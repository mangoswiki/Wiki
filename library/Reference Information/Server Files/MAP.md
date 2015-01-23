[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

The .Map files contain the basic map tiles information, including height maps and liquid maps

> The information below has been reverse engineered from the .Map files for all five cores, research into the exact format for each of the chunks contained in the file is ongoing. 

Each map is made up of a grid of 64 x 64. The map filename is built up via the following formula:-

For Each of the maps contained in Maps.dbc, the MapID is used (padded by zeros), followed by the Y and X cords in the grid.

So 0002035.map is made up of the following:- 

<pre>000 ( Map ID 0 = Azeroth)
20 (Tile 20 on the Y Axis)
35 (Tile 35 on te X Axis)
</pre>

  Antz (getMangos.eu)


##Header

      Identifier: 4 Bytes		=	4d 41 50 53 (MAPS)
     Map Version: 4 Bytes		=	This changes for each core version (see table below)
    Build Number: 4 Bytes		=	34 30 00 00 (12340) - **MaNGOSTwo**,**MaNGOSThree** and **MaNGOSFour** Only
     AREA Offset: 4 Bytes		=	28 00 00 00 (40 Bytes)
       AREA Size: 4 Bytes		=	08 02 00 00 (520 Bytes)
     MHGT Offset: 4 Bytes		=	30 02 00 00 (560 Bytes)
       MHGT Size: 4 Bytes		=	10 00 00 00 (16 Bytes)
     MLIQ Offset: 4 Bytes		=	40 02 00 00 (576 Bytes)
       MLIQ Size: 4 Bytes		=	10 00 00 00 (16 Bytes)
     Hole Offset: 4 Bytes		=	50 02 00 00 (591 Bytes)
       Hole Size: 4 Bytes		=	00 02 00 00 (512 Bytes)

###Map Version
    4 Bytes		        =	7a 31 2e 33 (z1.3) - **MaNGOSZero**
    4 Bytes		        =	73 31 2e 33 (s1.3) - **MaNGOSOne**
    4 Bytes		        =	73 31 2e 33 (v1.3) - **MaNGOSTwo**
    4 Bytes		        =	73 31 2e 32 (v1.2) - **MaNGOSThree**
    4 Bytes		        =	73 31 2e 32 (p1.3) - **MaNGOSFour**

##AREA Chunk

    Identifier:	4 Bytes		=	41 52 45 41 (AREA)
          Data:	Area Size - 4

##MHGT Chunk
This chunk contains the height map information for the tile

    Identifier:	4 Bytes		=	4d 48 47 54 (MHGT)
          Data:	MHGT Size - 4

##MLIQ Chunk
This chunk contains the liquid map information for the tile

    Identifier:	4 Bytes		=	4d 4c 49 51 (MLIQ)
          Data:	MLIQ Size - 4

##Hole Chunk
This chunk is current unknown, although in educated guess is that these are defined holes in the terrain - possibly for areas like tunnels that lead onto another tile.

         Data:	Hole Size	=	Define flags for chunks with holes
