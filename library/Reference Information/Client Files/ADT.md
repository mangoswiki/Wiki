[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------
## Introduction

ADT Files contain the actual terrain information (height maps, texturing, WMOs, doodads, etc) required by the client to render the static parts of the terrain. They use a [[chunked file structure]] like [[WDT Files]]. Each ADT File contains 256 (16x16) map tiles (or map chunks).
Each map tile is 33.3333 yards on each side, making the size of the map block in an ADT file 533.3333 yards on each side in total. 
As every WDT File can reference 64x64 ADT map blocks, the whole map is approximately 34133.33 yards on each side. 
So there will be a few initial data chunks to specify textures, objects, models, etc. followed by 256 MCNK (mapchunk) chunks :) Each MCNK chunk has a small header of its own, and additional chunks within its data block

## ADT files and blocks 

There is an .adt file for each existing block. If a block is unused it won't have an .adt file. The file will be: **World/Maps/{InternalMapName}/<{nternalMapName}_{BlockY}_{BlockX}.adt.**

    {InternalMapName} - The second field in Map.dbc
    {BlockY} - obtained with the following formula: floor((32 - (y / 533.33333))) 
    {BlockX} - obtained with the following formula: floor((32 - (x / 533.33333)))`


## Chunk Definitions

### MVER - Version

<table>
<tr><th>Identifier</th><td>MVER</td></tr>
<tr><th>Length</th><td>4 bytes</td></tr>
</table>

This chunk specifies the format version. All ADT Files in 1.12.X have Version 18.
***
### MHDR - Header

<table>
<tr><th>Identifier</th><td>MHDR</td></tr>
<tr><th>Length</th><td>64 bytes</td></tr>
</table>

The Header chunk contains offsets to various other chunks. All offsets are relative to the start of the MHDR data block

    00h      uint32          flags;     //Known Values: 1 = contains MFBO
    04h      uint32          offsMCIN;
    08h      uint32          offsMTEX;
    0Ch      uint32          offsMMDX;
    10h      uint32          offsMMID;
    14h      uint32          offsMWMO;
    18h      uint32          offsMWID;
    1Ch      uint32          offsMDDF;
    20h      uint32          offsMODF;
    24h      uint32          offsMFBO;  // this is only set if flags &1.
    28h      uint32          offsMH2O;
    2Ch      uint32          offsMTFX;
    30h      uint32[4]       unused;

***
### MCIN - Chunk Index

<table>
<tr><th>Identifier</th><td>MCIN</td></tr>
<tr><th>Length</th><td>4096 bytes</td></tr>
</table>

This is a lookup table containing absolute offsets and sizes for every map tile in the file. There are 16x16 = 256 entries of 16 bytes each:

    00h    uint32 offsMCNK            // absolute offset.
    04h    uint32 size                // the size of the MCNK chunk, this is refering to.
    08h    uint32 flags               // these two are always 0. only set in the client.
    0Ch    uint32 asyncId

***
### MTEX - Texture File Names

<table>
<tr><th>Identifier</th><td>MTEX</td></tr>
<tr><th>Length</th><td>variable</td></tr>
</table>

A list of zero-terminated file names for the textures used in this map.

***
### MMDX - Doodad File Names

<table>
<tr><th>Identifier</th><td>MMDX</td></tr>
<tr><th>Length</th><td>variable</td></tr>
</table>

A list of zero-terminated file names for the doodads / models used in this map.

***
### MMID - Doodad File Name Lookup

<table>
<tr><th>Identifier</th><td>MMID</td></tr>
<tr><th>Length</th><td>variable</td></tr>
</table>

uint32 offsets into the MMDX chunk for every doodad.

***
### MWMO - WMO File Names

<table>
<tr><th>Identifier</th><td>MWMO</td></tr>
<tr><th>Length</th><td>variable</td></tr>
</table>

A list of zero-terminated file names for the WMOs used in this map.
***
### MWID - WMO File Name Lookup

<table>
<tr><th>Identifier</th><td>MWID</td></tr>
<tr><th>Length</th><td>variable</tr>
</table>

uint32 offsets into the MWMO chunk for every doodad.

***
### MDDF - Doodad Definition

<table>
<tr><th>Identifier</th><td>MDDF</td></tr>
<tr><th>Length</th><td>nDoodad * 36 bytes</td></tr>
</table>

Placement Information for Doodads

    00h      uint32          mmidEntry;           // references an entry in the MMID chunk, specifying the model to use.
    04h      uint32          uniqueId;            // this ID should be unique for all ADTs currently loaded. Blizzard has these unique for the whole game.
    08h      float[3]        position;
    14h      float[3]        rotation;            // degrees.
    20h      uint16          scale;               // 1024 is the default size equaling 1.0f.
    22h      uint16          flags;               // values from enum MDDFFlags.

***
### MODF - WMO Definition

<table>
<tr><th>Identifier</th><td>MODF</td></tr>
<tr><th>Length</th><td>nWMO * 64 bytes</td></tr>
</table>

Placement Information for World Map Objects

    00h      uint32          mwidEntry;           // references an entry in the MWID chunk, specifying the model to use.
    04h      uint32          uniqueId;            // unique ID for the whole map.
    08h      float[3]        position;
    14h      float[3]        rotation;            // same as in MDDF.
    20h      float[3]        lowerBounds;         // these two are position plus the wmo bounding box.
    2Ch      float[3]        upperBounds;         // they are used for defining when if they are rendered as well as collision.
    38h      uint16          flags;
    3Ah      uint16          doodadSet;           // which WMO doodad set is used.
    3Ch      uint16          nameSet;             // which WMO name set is used. Used for renaming goldshire inn to northshire inn while using the same model.
    3Eh      uint16          padding;
        
***
### MCNK - Map Chunk Data

<table>
<tr><th>Identifier</th><td>MCNK</td></tr>
<tr><th>Length</th><td>128 byte header + variable data</td></tr>
</table>

After the general information above 256 MCNK chunks follow. Each of these has a header followed by subchunks. Subchunks mostly behave like normal file chunks, except for some flakyness in their chunk size values. The header looks like this:

    00h      uint32          flags;        // 1h=has MCSH, 2h=impassible, 4h=River, 8h=Ocean, 10h=Magma, 20h=Slime, 40h=has MCCV
    04h      uint32          IndexX;
    08h      uint32          IndexY;
    0Ch      uint32          nLayers;      // maximum 4
    10h      uint32          nDoodadRefs;
    14h      uint32          ofsMCVT;      // offsets to various chunks. Relative to the beginning of the MCNK Chunk
    18h      uint32          ofsMCNR;
    1Ch      uint32          ofsMCLY;
    20h      uint32          ofsMCRF;
    24h      uint32          ofsMCAL;
    28h      uint32          sizeAlpha;
    2Ch      uint32          ofsMCSH;                           // only with flags&0x1
    30h      uint32          sizeShadow;
    34h      uint32          areaid;
    38h      uint32          nMapObjRefs;
    3Ch      uint32          holes;
    40h      uint2[8][8]     ReallyLowQualityTextureingMap;     // the content is the layer being on top, I guess.
    50h      uint32          predTex;                           // ???
    54h      uint32          noEffectDoodad;                            // ???
    58h      uint32          ofsMCSE;
    5Ch      uint32          nSndEmitters;                              //will be set to 0 in the client if ofsSndEmitters doesn't point to MCSE!
    60h      uint32          ofsMCLQ;
    64h      uint32          sizeLiquid;                                // 8 when not used; only read if >8.
    68h      float[3]        position;
    74h      uint32          ofsMCCV;                           // only with flags&0x20, had uint32 textureId;
    78h      uint32          ofsMCLV;                           // introduced in Cataclysm
    7Ch      uint32          unused;                            // currently unused

About the holes in the terrain: This is a bitmapped field, the least significant 16 bits are used row-wise in the following arrangement with a 1 bit meaning that the map chunk has a hole in that part of its area:
	0x1	0x2	0x4	0x8
	0x10	0x20	0x40	0x80
	0x100	0x200	0x400	0x800
	0x1000	0x2000	0x4000	0x8000
***
### MCVT Subchunk

<table>
<tr><th>Identifier</th><td>MCVT</td></tr>
<tr><th>Length</th><td>580 bytes</td></tr>
</table>

These are the actual height values for the 9x9+8x8 vertices. 145 floats in the following order/arrangement:. The values in here are only relative to the position given in the corresponding MCNK chunk.

      1    2    3    4    5    6    7    8    9
       10   11   12   13   14   15   16   17
     18   19   20   21   22   23   24   25   26
       27   28   29   30   31   32   33   34
     35   36   37   38   39   40   41   42   43
       44   45   46   47   48   49   50   51
     52   53   54   55   56   57   58   59   60
       61   62   63   64   65   66   67   68
     69   70   71   72   73   74   75   76   77
       78   79   80   81   82   83   84   85
     86   87   88   89   90   91   92   93   94
       95   96   97   98  99  100  101  102
    103  104  105  106  107  108  109  110  111
      112  113  114  115  116  117  118  119
    120  121  122  123  124  125  126  127  128
      129  130  131  132  133  134  135  136
    137  138  139  140  141  142  143  144  145

WoW uses Squares out of 4 of the Outer(called NoLoD)-Vertices with one of the Inner(called LoD)-Vertices in the Center:

      1    2
        10
     18   19
***
### MCNR Subchunk - Normals

<table>
<tr><th>Identifier</th><td>MCNR</td></tr>
<tr><th>Length</th><td>435 bytes + 13 bytes of unknown data</td></tr>
</table>

9x9 + 8x8 surface normals, laid out as in the MCVT chunk.

   int8[3] normal;         // normalized. X, Y, Z. 127 == 1.0, -127 == -1.0.

This chunk has 13 bytes of unknown data at the end. The chunk size only covers the normals, though.

***
### MCLY Subchunk - Texture Layers

<table>
<tr><th>Identifier</th><td>MCLY</td></tr>
<tr><th>Length</th><td>1-4 layers * 16 bytes</td></tr>
</table>

These are texture layer definitions for this map chunk. 16 bytes per layer, up to 4 layers. Every texture layer other than the first will have an alpha map to specify blending amounts. The first layer is rendered with full opacity. To know which alphamap is used, there is an offset into the MCAL chunk. That one is relative to MCAL.
You can animate these by setting the flags. Only simple linear animations are possible. You can specify the direction in 45° steps and the speed.
The textureId is just the array index of the filename array in the MTEX chunk.
The effectId links to GroundEffectTexture.dbc. It defines the little detaildoodads as well as the footstep sounds and if footprints are visible. 

    00h      uint32          textureId;
    04h      uint32          flags;
    08h      uint32          offsetInMCAL;
    0Ch      int32           effectId;    // (actually int16 and padding)

**Flags**

    Flag     Description
    ---------------------------------------------------------------------------------
    0x001    Animation: Rotate 45° clockwise.
    0x002    Animation: Rotate 90° clockwise.
    0x004    Animation: Rotate 180° clockwise.
    0x008    Animation: Make this faster.
    0x010    Animation: Faster!!
    0x020    Animation: Faster!!!!
    0x040    Animation: Animate this texture as told in the other bits.
    0x080    This will make the texture way brighter. Used for lava to make it "glow".
    0x100    Use alpha map - set for every layer after the first
    0x200    Alpha map is compressed

***
### MCRF Subchunk

<table>
<tr><th>Identifier</th><td>MCRF</td></tr>
<tr><th>Length</th><td>variable</td></tr>
</table>

A uint32 list of with MCNK.nDoodadRefs + MCNK.nMapObjRefs indices into the file's MDDF and MODF chunks, saying which MCNK subchunk those particular doodads and objects are drawn within. This MCRF list contains duplicates for map doodads that overlap areas.
As both, WMOs and M2s are referenced here, they get doodad indices first, then WMOs. If you have a doodad and a WMO in the ADT as well as the MCNK, you will have a {0,0} in MCRF with nDoodadRefs and MCNK.nMapObjRefs being 1.

***
### MCSH Subchunk - Shadows

<table>
<tr><th>Identifier</th><td>MCSH</td></tr>
<tr><th>Length</th><td>512 bytes</td></tr>
</table>

Shadow map for static shadows on the terrain. Can be left out with the chunk&1 flag not set.
The shadow maps work as follows: the shadows are stored per bit as 0 or 1 (off or on) so we have 8 bytes (which equates to 64 values) X 64 bytes (64 values in this case) which ends up as a square 64x64 shadowmap with either white or black. Note that the shadow values come LSB first.

***
### MCAL Subchunk - Alpha maps

<table>
<tr><th>Identifier</th><td>MCAL</td></tr>
<tr><th>Length</th><td>0-3 layers * 2048 bytes</td></tr>
</table>


These are alpha maps for additional texture layers beside the base layer. Each layer contains a 64x64 alpha map. There are 2 alpha values per byte, first 4 bits and second 4 bits. Results in 2048 bytes per layer.

***
### MCLQ Subchunk - Liquids

<table>
<tr><th>Identifier</th><td>MCLQ</td></tr>
<tr><th>Length</th><td>???</td></tr>
</table>

The size of the chunk is in the mapchunk header. The type of liquid is given in the mapchunk flags, also in the header.
**This information is old and incomplete as well as maybe wrong.**
The first two floats specify the minimum and maximum liquid height level. After them comes a 9x9 height map for the water with the following format per vertex:

    0x00     int16    ?
    0x02     int16    ?
    0x04     float    height value

The unknown int values might be color or transparency info, or something entirely different... Most frequently they are 0.
Followed by 8x8 bytes of flags for every liquid "tile" between the 9x9 vertex grid. The value 0x0F means do not render. (the specific flag for this seems to be 8 but I'm not sure - but it fixes some places where there was extra "water" sticking into the rest of the scenery)
Finally, 0x54 bytes of additional data, no idea what it's used for.

***
### MCSE Subchunk - Sound emitters

<table>
<tr><th>Identifier</th><td>MCSE</td></tr>
<tr><th>Length</th><td>???</td></tr>
</table>

This is not well understood. Struct from WoWDev Wiki:

    00h      uint32          soundPointID;
    04h      uint32          soundNameID;
    08h      float[3]        pos;
    0Ch
    10h
    14h      float           minDistance;
    18h      float           maxDistance;
    1Ch      float           cutoffDistance;
    20h      uint16          startTime;
    22h      uint16          endTime;
    24h      uint16          groupSilenceMin;
    26h      uint16          groupSilenceMax;
    28h      uint16          playInstancesMin;
    2Ah      uint16          playInstancesMax;
    2Ch      uint16          loopCountMin;
    2Eh      uint16          loopCountMax;
    30h      uint16          interSoundGapMin;
    32h      uint16          interSoundGapMax;

