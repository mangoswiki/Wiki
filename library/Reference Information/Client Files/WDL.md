[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

WDL files contain a low-resolution heightmap for a world. This is probably what the WoW client uses to draw the solid-colored mountain ranges in the background ('in front of' the sky, but 'behind' the fog and the rest of the scenery). It can also be conveniently used to construct a minimap - however, since no water level information is present, the best guess is 0 (sea level) - this results in some lower-than-sea-level areas being blue on the WoWmapview minimap. Oh well. :)

* ''Someone told me that the use of WDL files was actually to determine pathing (especially for NPCs). We still need a confirmation on what they're for though. -DG'' 

*Chunked structure.

##MWMO, MWID and MODF chunk

These chunks seem to have been added to every WDL and contain information about low resolution [[WMO]] used to create a silhouette.

###MWMO

    *'''Filenames for [[WMO]] that appear in the low resolution map.''' Zero terminated strings.

###MWID

    *'''List of indexes into the MWMO chunk.'''

###MODF

    *'''Placement information for the [[WMO]].''' Appears to be the same 64 byte structure used in the [[WDT]] and [[ADT]] MODF chunks.

###MAOF chunk

    *'''Map Area Offset.''' 

    Contains 64*64 = 4096 unsigned 32-bit integers, these are absolute offsets in the file to each map tile's MapAreaLow-array-entry. For unused tiles the value is 0.

     /*000h*/ UINT32 areaLowOffsets[4096];
     ''or''
     /*000h*/ UINT32 areaLowOffsets[64][64];

##MapAreaLow array
###MARE chunks
    *'''Map Area''' 

Heightmap for one map tile. Contains 17*17 + 16*16 = 545 signed 16-bit integers. So a 17 by 17 grid of height values is given, with additional height values in between grid points. Here, the "outer" 17x17 points are listed (in the usual row major order), followed by 16x16 "inner" points. The height values are on the same scale as those used in the regular height maps.

###MAHO chunks
After each MARE chunk there follows a MAHO (MapAreaHOles) chunk. It may be left out if the data is supposed to be 0 all the time.

Its an array of 16 shorts. Each short is a bitmask. If the bit is not set, there is a hole at this position.