[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

###These files are obsolete!

LIT files have stored lighting-information until some patch. Today, lightning is stored in the following DBC files:

* [**Light.dbc**](dbc_Light_MaNGOSZero)
* [**LightFloatBand.dbc**](dbc_LightFloatBand_MaNGOSZero)
* [**LightIntBand.dbc**](dbc_LightIntBand_MaNGOSZero)
* [**LightParams.dbc**](dbc_LightParams_MaNGOSZero)
* [**LightSkybox.dbc**](dbc_LightSkybox_MaNGOSZero)

For worlds that have terrain data, a corresponding LIT file includes information about the sky color, and possibly lighting conditions. They are stored in World\name\lights.lit

##Header

    Offset 	Type 	Description
    0x00 	uint32 	Always 05 00 00 80
    0x04 	uint32 	nSkies - number of skies defined in this file

64 bytes per sky:

    Offset 	Type 		Description
    0x00 	3 * int32 	(-1,-1,-1) for the 'default' first record, (0,0,0) otherwise
    0x0C 	3 * float 	Coordinates (X,Y,Z)
    0x18 	float 		Smaller radius for area (?)
    0x1C 	float 		Larger radius
    0x20 	char[32] 	Sky name

The float values seem to be multiplied by 36. Dividing by 36 gives back the original scale (I think) In the case of "I think", I think that the game client uses the floats to perform some kind of Cube-Mapped LightMapping (hence the X, Y, Z, -X, -Y, -Z values). -DG

##Sky data

    4 * 0x15F0 bytes per sky.

The first block of the four seems to have the sky colors, the second and fourth are usually all black, the third might be lighting colors or something else entirely.
    Offset 	Type 		Description
    0x0000 	18 * int32 	Lengths
    0x0048 	18 * 64 * int32	Color + time records
    0x1248 	32 * float 	Float values A
    0x12C8 	32 * float 	Float values B
    0x1348 	uint32 		Int value I
    0x134C 	32 * float 	Float values C
    0x13CC 	32 * float 	Float values D
    0x144C 	32 * float 	Float values E
    0x14CC 	32 * float 	Float values F
    0x154C 	uint32 		Int value J
    0x1550 	32 * float 	Float values G
    0x15D0 	8 * uint32 	Padding (all 0)

The color and time records are in the following format:

Each row of 64 integers contains 32 pairs of integers: the first value is the time in half-minutes (on a scale of 0 to 2880 from midnight to midnight), the second value is a BGRX color. The i-th row contains Lengths[ i ] records like that. I think the color values for intermediate times are interpolated based on the times given in this list.

So there are 18 time-based color rows described here, for the first block these are always the sky colors (well, the first 8 at least). WoWmapview is currently only drawing a very crude, fake sky globe - the colors may or may not match up ;)

The 7 sets of floating-point values have to describe the arrangement of the sky colors somehow, but they're pretty difficult to interpret. They usually contain at most 8 values, the rest being 0.

So today I experimented with a custom .LIT file (red and blue skies are hilarious), so here are the meanings for the various color tracks:

    Number 	Description
    0 	    Global diffuse light
    1 	    Global ambient light
    2 	    Sky color 0 (top)
    3 	    Sky color 1 (middle)
    4 	    Sky color 2 (middle to horizon)
    5 	    Sky color 3 (above horizon)
    6 	    Sky color 4 (horizon)
    7 	    Fog color / background mountains color
    8 	    ?
    9 	    Sun color + sun halo color
    10 	    Sun larger halo color
    11 	    ?
    12 	    Cloud color
    13 	    ?
    14 	    ?
    15 	    Ground shadow color
    16 	    Water color [light]
    17 	    Water color [dark]

The different skies are interpolated based on distance.

The four sets of data are completely different. 

    Number    Description
    0         The default look. 
    1 and 3   are usually all black. 
    2         might be the 'ghost view' lighting for when you're dead, but I'm not sure.
