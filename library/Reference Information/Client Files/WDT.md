[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

## Introduction

WDT files specify exactly which map tiles are present in a world, if any, and can also reference a "global" WMO. They have a [[Chunked File Structure]].

## Chunks

### MVER - **M**ap **Ver**sion

<table>
<tr><th>Identifier</th><td>MVER</td></tr>
<tr><th>Length</th><td>4 bytes</tr>
</table>

This chunk specifies the format version. All WDT Files in 1.12.X have Version 18.

***

### MPHD - **M**a**p** **H**ea**d**er

<table>
<tr><th>Identifier</th><td>MPHD</td></tr>
<tr><th>Length</th><td>32 bytes</tr>
</table>

This chunk is the Map header. It contains 8 int32 Values.

    00h      uint32          flags;
    04h      uint32          something;
    08h      uint32          unused[6];

Flags values are not well understood. From Wowdev:

    Flag     Description
    --------------------------------------------------------------------------------------------------------
    0x01     Use global map object definition.
    0x02     CMapRenderChunk::SetVertexFormat( 2 ); (else: 1) -- Use vertex shading (ADT.MCNK.MCCV)
    0x04     Decides whether to use _env terrain shaders or not: funky and if MCAL has 4096 instead of 2048(?)
    0x08     Disables something. No idea what. Another rendering thing. Someone may check all them in wild life..
    0x10     if( flags & 0x02 && CMap::enableTerrainShaderVertex ) CMapRenderChunk::SetVertexFormat( 16 ); // cataclysm?

The second integer is not ignored but stores something too. This is even less well understood.

***

### MAIN Chunk

<table>
<tr><th>Identifier</th><td>MAIN</td></tr>
<tr><th>Length</th><td>32768 bytes</tr>
</table>


This is the map table data. It contains 64x64 8 byte entries. 

    00h      uint32          m_flags;
    04h      void*           m_area;       // only set during runtime.

Flags:

    Flag     Description
    -----------------------------------------------------------------
    0x01     There is an ADT File for this position
    0x02     Set by the client during runtime if the chunk was loaded

We just need to know the 0x01 flag. The corresponding ADT File is found in World\Maps\\<MAPNAME>\\<MAPNAME>_XX_YY.adt

***

### MWMO - **M**ap **W**orld **M**ap **O**bject

<table>
<tr><th>Identifier</th><td>MWMO</td></tr>
<tr><th>Length</th><td>varies</tr>
</table>


If there is no terrain in a map (e.g. Deeprun Tram), all entries in the MAIN Chunk are 0. In this, and ONLY in this case, the MWMO Chunk contains exactly one WMO File Name (Zero Terminated).

***

### MODF Chunk

<table>
<tr><th>Identifier</th><td>MODF</td></tr>
<tr><th>Length</th><td>64 bytes</tr>
</table>

If the MWMO Chunk is not empty, MODF contains placement information for the WMO.

    00h      uint32          ID (index in the MWID list)
    04h      uint32          unique identifier for this instance
    08h      float[3]        Position (X,Y,Z)
    14h      float[3]        Orientation (A,B,C)
    20h      float[6]        Bounding Box
    38h      uint16          Flags
    3Ah      uint16          Doodad set index
    3Ch      uint16          Name set?
    3Eh      uint16          Padding
