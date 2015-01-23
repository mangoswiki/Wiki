[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

## MPQ File Format

### Introduction

All of the game data for WoW are stored in MPQ Archives. The format's capabilities include compression, encryption, file segmentation, extensible file metadata, cryptographic signature and the ability to store multiple versions of the same file for internationalization and platform-specific differences. MPQ archives can use a variety of compression algorithms which may also be combined.

The definitive source for information on MPQ Files is <http://wiki.devklog.net/index.php?title=The_MoPaQ_Archive_Format>.

The following summary only includes facts relevant for 1.12.X Client versions

### Technical overview

All numbers in the MPQ format are in little endian byte order; signed numbers use the two's complement system. Data types are listed either as int (integer, the number of bits specified), byte (8 bits), or char (bytes which contain ASCII characters). All sizes and offsets are in bytes, unless specified otherwise. Structure members are listed in the following general form: 

    offset from the beginning of the structure: data type(array size) member name : member description

### General Archive Layout
The physical layout of the files looks like this

* Archive Header
* File Data
* Hash Table
* Block Table

In the following the components are discussed in the logical order of processing required to read and extract files from MPQ Archives

### Archive Header
Header size is 32 bytes, maximum archive size is 4 GB.

	00h: char(4) Magic             Indicates that the file is a MPQ archive. Must be ASCII "MPQ" 1Ah.
	04h: int32 HeaderSize          Size of the archive header.
	08h: int32 ArchiveSize         Size of the whole archive, including the header. 
	0Ch: int16 FormatVersion       MPQ format version. 0000h for Classic WoW.
	0Eh: int8 SectorSizeShift      Power of two exponent specifying the number of 512-byte disk sectors in each logical sector 
								   in the archive. The size of each logical sector in the archive is 512 * 2^SectorSizeShift. 
 								   Bugs in the Storm library dictate that this should always be 3 (4096 byte sectors).
	10h: int32 HashTableOffset     Offset to the beginning of the hash table, relative to the beginning of the archive.
	14h: int32 BlockTableOffset    Offset to the beginning of the block table, relative to the beginning of the archive.
	18h: int32 HashTableEntries    Number of entries in the hash table. Must be a power of two, and must be less than 2^16 
	1Ch: int32 BlockTableEntries   Number of entries in the block table.

### Hash Table

The Hash Table serves as a quick means of filename lookup without having to go through string comparisons. For each file in the archive, the full path is hashed using a proprietary algorithm (for source see <http://wiki.devklog.net/index.php?title=The_MoPaQ_Archive_Format#Algorithm_Source_Code>) resulting in three 32bit integers. The first of those hashes serves as primary lookup key for the Hash Table, the others are used for verification in case of a hash collision. In the case that two files have the same lookup key (hash collision), the first file is stored under that hash, and the second file is stored under the next free hash. So during lookup, if the second and third hash don't match, the algorithm goes down the list until it either finds a match of an empty entry.
Each entry in the Hash Table looks like this:

	00h: int32 FilePathHashA    The hash of the file path, using method A.
	04h: int32 FilePathHashB    The hash of the file path, using method B.
	08h: int16 Language         The language of the file. This is a Windows LANGID data type, and uses the same values. 
								0 indicates the default language (American English), or that the file is language-neutral.
	0Ah: int8 Platform          The platform the file is used for. 0 indicates the default platform. No other values 
								have been observed.
	0Ch: int32 FileBlockIndex   If the hash table entry is valid, this is the index into the block table of the file. 
								Otherwise, one of the following two values:
		FFFFFFFFh           	Hash table entry is empty, and has always been empty. Terminates searches for a given file.
		FFFFFFFEh           	Hash table entry is empty, but was valid at some point (in other words, the file was deleted). 
								Does not terminate searches for a given file

The Hash Table is encrypted using a proprietary encryption algorithm using "(hash table)" as key. The encryption algorithm is also documented at <http://wiki.devklog.net/index.php?title=The_MoPaQ_Archive_Format#Algorithm_Source_Code>

### Block Table

The Block Table contains offsets into the File Data block for each File in the Archive. It also stores file attributes like compression or encryption. Hash Table FileBlockIndex points to entries in the Block Table. Like the Hash Table it is encrypted, using "(block table)" as key.
Each Block Table entry looks like this:

	00h: int32 BlockOffset   Offset of the beginning of the block, relative to the beginning of the archive.
	04h: int32 BlockSize     Size of the block in the archive.
	08h: int32 FileSize      Size of the file data stored in the block. If the file is compressed, this is the size of the uncompressed file data.
	0Ch: int32 Flags         Bit mask of the flags for the block. 

Known flags are:

	Flag name				Value		Meaning
	MPQ_FILE_IMPLODE		0x00000100	File is compressed using PKWARE Data compression library
	MPQ_FILE_COMPRESS		0x00000200	File is compressed using combination of compression methods
	MPQ_FILE_ENCRYPTED		0x00010000	The file is encrypted
	MPQ_FILE_FIX_KEY		0x00020000	The decryption key for the file is altered according to the position of the file in the archive
	MPQ_FILE_PATCH_FILE		0x00100000	The file contains incremental patch for an existing file in base MPQ
	MPQ_FILE_SINGLE_UNIT	0x01000000	Instead of being divided to 0x1000-bytes blocks, the file is stored as single unit
	MPQ_FILE_DELETE_MARKER	0x02000000	File is a deletion marker, indicating that the file no longer exists. This is used to allow patch archives to delete files present in lower-priority archives in the search chain. The file usually has length of 0 or 1 byte and its name is a hash
	MPQ_FILE_SECTOR_CRC		0x04000000	File has checksums for each sector (explained in the File Data section). Ignored if file is not compressed or imploded.
	MPQ_FILE_EXISTS			0x80000000	Set if file exists, reset when the file was deleted

### File Data 

Block Table BlockOffset points to the beginning of a file data block. Each file data block has a header of nSectors+1 int32 values, indicating offsets to each sector start (relative to the beginning of the file data block). The final value of this list is the total (compressed) file size, including the header. The size of each block can easily be calculated from the difference between two offsets. If the block is compressed, the first byte of every sector indicates the compression method used

### Extracting a file
This is a step-by-step instruction.

1. Read the File Header, find the offsets to the Hash Table and Block Table
2. Read and Decrypt Hash Table and Block Table
3. Compute Hashes for the file (Full Path, all Slashes converted to Backslashes) => **Hash0, Hash1, Hash2**
4. **HashTableOffset** = **Hash0** & (**Header.HashTableEntries** -1)
5. Starting from **HashTableOffset**, go through the Hash Table and compare **Hash1** and **Hash2** to **HashTable.FilePathHashA** and **HashTable.FilePathHashB** respectively until either a match or an empty entry is found. In the latter case the file you are looking for does not exist.
6. Find the Block Table entry which corresponds to **HashTable.FileBlockIndex**
7. Go to the file offset specified in **BlockTable.BlockOffset**
8. Read int32 values until you reach a value that is equal to **BlockTable.BlockSize** => **SectorOffset[0] ... SectorOffset[n]**
9. For every entry of **SectorOffset[0]...SectorOffset[n-1]**, seek to **BlockTable.BlockOffset+SectorOffset[x]**
10. Read **SectorOffset[x+1]-SectorOffset[x]** bytes of data.
11. If **BlockTable.Flags** has a compressed flag set, the first byte of each sector indicates the compression method applied.
12. Decrypt and or decompress each sector as necessary, stitch them together, et voila, there is your file

### The Listfile

Each MPQ in WoW 1.12.X contains a "(listfile)". This file lists the full archive contents, one file path per line, in clear text. Hashing the file paths provides lookup keys into Hash Table. The file is provided for convenience, as it seems. It is not used by the client.
