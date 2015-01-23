[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

BLS specify specific instructions to the video card as to how to render parts of the world and how to do certain effects.

There are two major types of shaders: fragment shaders (also known as pixel shaders) and vertex shaders. Fragment shaders are executed on a per-pixel basis, thus can influence texture fetching and combining operations, whereas vertex shaders are executed on a per-vertex basis. These can change vertex positions to achieve mesh animation, particle systems, and texture animation.

BLS files can be found under Shaders\Pixel as well as Shaders\Vertex. They are refernced from [[WFX]] files as well as directly from WoW.exe, so there is no client database pointing to them.

There are different types of shaders. 

    *Vertex shaders:
    **arbvp1
    **arbvp1_cg12
    **vs_1_1
    **vs_2_0
    **vs_3_0
    *Pixel shaders:
    **arbfp1
    **nvrc
    **nvts
    **ps_1_1
    **ps_1_4
    **ps_2_0
    **ps_3_0

They are sorted in folders as of 3.*. Previously, there were no different folders but an additional header in the files defining the type.

###Header
    *Main header (0xC bytes)
    This header is in all files - pixel and vertex shaders in all profiles.
     struct BLSHeader {
     ''/*0x00*/''	char[4] magix;		// in reverse character order: "SVXG" in case of a vertex shader, "SPXG" in case of a fragment shader
     ''/*0x04*/''	uint32 version;		// Always 0x10003 - version 1.3 of format
     ''/*0x08*/''	uint32 permutationCount;
     ''/*0x0C*/''
     };

###Blocks
    There are permutationCount blocks of the following structure. They are padded to 0x*0, 0x*4, 0x*8 and 0x*C.
     struct BLSBlock {
     ''/*0x00*/''	DWORD flags0;		// seen: 0x3FE80 in pixel shaders; 0x1A0F in vertex shaders. there may be more ..
     ''/*0x04*/''	DWORD flags4;		// seen: 0x200 in pixel shaders; 0x3FEC1 in vertex shaders (there may be more ..)
     ''/*0x08*/''	DWORD unk8;		// Never seen anything in here.
     ''/*0x0C*/''	uint32 size;		// Tells you how large the block actually is.
     ''/*0x10*/''	char data[size];	// In whatever format defined.
     ''/*----*/''
     };