[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

[[WMO/v17|WMO]] files contain world map objects. They, too, have a [[Chunk|chunked]] structure just like the [[WDT]] files.

There are two types of [[WMO/v17]] files, actually:

*[[WMO/v17#WMO_root_file|WMO root file]] - lists textures ([[BLP]] Files), doodads ([[M2]] or [[MDX]] Files), etc., and orientation for the [[WMO/v17]] groups
*[[WMO/v17#WMO_group_file|WMO group file]] - 3d model data for one unit in the world map object 

The root file and the groups are stored with the following filenames:

*World\wmo\path\WMOName.wmo
*World\wmo\path\WMOName_NNN.wmo

There is a hardcoded maximum of 512 group files per root object.

= WMO root file =

The root file lists the following:

* textures ([[BLP]] File references)
* materials
* models ([[M2|MDX / M2]] File references)
* groups
* visibility information
* more data

==  MOHD chunk ==

*'''Header for the map object. 64 bytes.'''

 '''Offset 	Type 		Description'''
 0x00 	uint32 		nMaterials - number of materials
 0x04 	uint32 		nGroups - number of [[WMO/v17]] groups
 0x08 	uint32 		nPortals - number of portals
 0x0C 	uint32 		nLights - number of lights
 0x10 	uint32 		nModels - number of [[M2]] models imported
 0x14 	uint32 		nDoodads - number of dedicated files (*see below this table!) 
 0x18 	uint32 		nSets - number of doodad sets
 0x1C 	uint32 		ambient color?
 0x20 	uint32 		[[WMO/v17]] ID (column 2 in [[WMOAreaTable.dbc]])
 0x24 	float[3] 	Bounding box corner 1
 0x30 	float[3] 	Bounding box corner 2
 0x3C 	uint32 		LiquidType related, see below in the MLIQ chunk.

*(*[[M2]] instances + all groupfiles belonging to this wmo including groupfiles of dedicated rootfiles(ie StormwindHarbor.wmo to Stormwind.wmo))

 struct SMOHeader ''// 03-29-2005 By ObscuR''
 {
 /*000h*/  UINT32 nTextures;		
 /*004h*/  UINT32 nGroups;		
 /*008h*/  UINT32 nPortals;		
 /*00Ch*/  UINT32 nLights;		
 /*010h*/  UINT32 nDoodadNames;		
 /*014h*/  UINT32 nDoodadDefs;		
 /*018h*/  UINT32 nDoodadSets;		
 /*01Ch*/  float ambColor[6];		
 /*020h*/ 
 /*024h*/  	
 /*028h*/  		
 /*02Ch*/ 	
 /*030h*/  float pos[2];		
 /*034h*/  		
 /*038h*/  		
 /*03Ch*/   UINT32 wmoID;		
 /*040h*/ 
 };

 struct MOHD // --[[User:Schlumpf|Schlumpf]] 20:53, 30 July 2007 (CEST)
 {
 /*000h*/  UINT32 nTextures;		
 /*004h*/  UINT32 nGroups;		
 /*008h*/  UINT32 nPortals;		
 /*00Ch*/  UINT32 nLights;		
 /*010h*/  UINT32 nModels;		
 /*014h*/  UINT32 nDoodads;		
 /*018h*/  UINT32 nSets;		
 /*01Ch*/  UINT8  colR;		
 /*01Dh*/  UINT8  colG;	
 /*01Eh*/  UINT8  colB;		
 /*01Fh*/  UINT8  colX;			
 /*020h*/  UINT32 wmoID;
 /*024h*/  float  bb1[3];
 /*030h*/  float  bb2[3];		
 /*03Ch*/  UINT32 nullish;	
 };

==  MOTX chunk ==

*'''List of textures ([[BLP]] Files) used in this map object. <del>There are nTextures entries in this chunk.</del>''' 

A block of <del>zero-padded, zero-terminated strings,</del> that are complete filenames with paths. There will be further material information for each texture in the next chunk. The gaps between the filenames are padded with extra zeroes, but the material chunk does have some positional information for these strings.

The beginning of a string is always aligned to a 4Byte Adress. (0, 4, 8, C). The end of the string is Zero terminated and filled with zeros until the next aligment.
Sometimes there also empty aligtments for no (it seems like no) real reason.

==  MOMT chunk ==

*'''Materials used in this map object, 64 bytes per texture ([[BLP]] file), nMaterials entries.'''

 struct SMOMaterial ''// based on: 03-29-2005 By ObscuR'' // --[[User:Schlumpf|schlumpf_]] 18:36, 5 August 2009 (CEST)
 {
 /*000h*/  UINT32 flags1;		
 /*004h*/  UINT32 shader;		// Index into CMapObj::s_wmoShaderMetaData. See below (shader types).
 /*008h*/  UINT32 blendMode;		// Blending: 0 for opaque, 1 for transparent
 /*00Ch*/  UINT32 texture_1;		// Start position for the first texture filename in the [[WMO/v17#MOTX_chunk|MOTX]] data block. Defaults to "createcrappygreentexture.blp".
 /*010h*/  UINT32 color_1; 
 /*014h*/  UINT32 flags_1;
 /*018h*/  UINT32 texture_2;		// Start position for the second texture filename in the [[WMO/v17#MOTX_chunk|MOTX]] data block	
 /*01Ch*/  UINT32 color_2; 		// diffuse (CWorldView::GatherMapObjDefGroupLiquids():  geomFactory->SetDiffuseColor((CImVector*)(smo+7)); )
 /*020h*/  UINT32 flags_2;
 /*024h*/  UINT32 texture_3; 	
 /*028h*/  UINT32 color_3;
 /*02Ch*/  UINT32 unk[3];  		//float diffColor[3] 		
 /*030h*/  uint32_t runTimeData[4];	// This data is explicitly nulled upon loading. Contains textures or similar stuff.
 /*034h*/  		
 /*038h*/
 /*03Ch*/ 
 /*040h*/ 
 }

The flags might used to tweak alpha testing values, I'm not sure about it, but some grates and flags in IF seem to require an alpha testing threshold of 0, at other places this is greater than 0.
 '''flag2 		Meaning'''
 0x01 		?(I'm not sure atm I tend to use lightmap or something like this)
 0x04 		Two-sided (disable backface culling)
 0x08 		Darkned ?, the intern face of windows are flagged 0x08
 0x10 		Bright at night (unshaded) (used on windows and lamps in Stormwind, for example) -ProFeT: i think that is Unshaded becase external face of windows are flagged like this.
 0x20 		?
 0x40 		looks like GL_CLAMP
 0x80 		looks like GL_REPEAT
===shader types===
Depending on the shader, a different amount of textures is required. If there aren't enough filenames given, it defaults to Opaque (with one filename). More filenames than required are just ignored.

Data is from 15464.
{| style="background:#FCFCFC; color:black"
|- 
! value 
! name
! textures without shader
! textures with shader 
! ?1
! ?2
|-
| 0 || Diffuse || 1 || 1 || 1 || 1
|-style="background:#F0F8FF;"
| 1 || Specular || 1 || 1 || 1 || 1
|-
| 2 || Metal || 1 || 1 || 1 || 1
|-style="background:#F0F8FF;"
| 3 || Env || 1 || 2 || 1 || 1
|-
| 4 || Opaque || 1 || 1 || 1 || 1
|-style="background:#F0F8FF;"
| 5 || EnvMetal || 1 || 2 || 1 || 1
|-
| 6 || TwoLayerDiffuse || 1 || 2 || 2 || 2
|-style="background:#F0F8FF;"
| 7 || TwoLayerEnvMetal || 1 || 3 || 2 || 2
|-
| 8 || TwoLayerTerrain || 1 || 2 || 1 || 2
|-style="background:#F0F8FF;"
| 9 || DiffuseEmissive || 1 || 2 || 2 || 2
|-
| 10 || Unknown || 1 || 1 || 1 || 1 || Seems to be invalid. Does something with MOTA (tangents).
|-style="background:#F0F8FF;"
| 11 || MaskedEnvMetal || 1 || 3 || 2 || 2
|-
| 12 || EnvMetalEmissive || 1 || 3 || 2 || 2
|-style="background:#F0F8FF;"
| 13 || TwoLayerDiffuseOpaque || 1 || 2 || 2 || 2
|-
| 14 || TwoLayerDiffuseEmissive || 1 || 1 || 1 || 1 || Seems to be invalid. Does something with MOTA (tangents).
|-style="background:#F0F8FF;"
| 15 || || 1 || 2 || 2 || 2
|-
| 16 || Diffuse || 1 || 1 || 1 || 1 || Not sure if valid or just wrapping. Exists twice.
|}
 if (?1 == 2)
 {
   if (?2 == 2)
     vertexBufferFormat = 19;
   else
     vertexBufferFormat = 7;
 }
 else if (?2 == 2)
   vertexBufferFormat = 17;
 else
   vertexBufferFormat = 4;

== MOGN chunk ==

*'''List of group names for the groups in this map object. There are nGroups entries in this chunk.''' Should be four-byte aligned entries. 

A contiguous block of zero-terminated strings. The names are purely informational except for "antiportal". The names are referenced from MOGI or somewhere in the group object, IIRC. --[[User:Schlumpf|Schlumpf]] 11:18, 27 July 2011 (UTC)

i think think that his realy is zero terminated and just a name list .. but so far im not sure _what_ else it could be - tharo

==  MOGI chunk ==

*'''Group information for WMO groups, 32 bytes per group, nGroups entries.'''

 '''Offset 	Type 		Description'''
 0x00 	uint32 		Flags
 0x04 	3 * float 	Bounding box corner 1
 0x10 	3 * float 	Bounding box corner 2
 0x1C 	int32 		name in [[WMO/v17#MOGN_chunk|MOGN]] chunk (or -1 for no name?)

 struct WMOGroup // --[[User:Schlumpf|Schlumpf]] 21:06, 30 July 2007 (CEST)
 {
 /*000h*/  UINT32 flags;  		
 /*004h*/  float  bb1[3];  		
 /*010h*/  float  bb2[3];		
 /*01Ch*/  UINT32 nameoffset;
 }

Groups don't have placement or orientation information, because the coordinates for the vertices in the additional .[[WMO/v17]] files are already correctly transformed relative to (0,0,0) which is the entire [[WMO/v17]]'s base position in model space.

The name offsets seem to be incorrect (or something else entirely?). The correct name offsets are in the [[WMO/v17#WMO_group_file|WMO group file]] headers. (along with more descriptive names for some groups)
* It is just the index. You have to find the offsets by yourself. --[[User:Schlumpf|Schlumpf]] 10:17, 31 July 2007 (CEST)

The flags for the groups seem to specify whether it is indoors/outdoors, probably to choose what kind of lighting to use. Not fully understood. "Indoors" and "Outdoors" are flags used to tell the client whether certain spells can be cast and abilities used. (Example: Entangling Roots cannot be used indoors).

 '''Flag		Meaning'''
 0x8 		Outdoor (use global lights?)
 0x40		?
 0x80 		?
 0x2000		Indoor (use local lights?)
 0x8000		Unknown, but frequently used
 0x10000 	Used in Stormwind?
 0x40000		Show skybox if the player is "inside" the group (this is cleared for all groups if MOSB has no content)

==  MOSB chunk ==

*'''Skybox.''' Contains an zero-terminated filename for a skybox. (padded to 4 byte alignment if "empty"). If the first byte is 0, the skybox flag in all MOGI entries are cleared and there is no skybox.

==  MOPV chunk ==

*'''Portal vertices, one entry is a float[3], 4 * 3 * float per portal, nPortals entries.'''

Portals are (always?) rectangles that specify where doors or entrances are in a [[WMO/v17]]. They could be used for visibility, but I currently have no idea what relations they have to each other or how they work.

Since when "playing" WoW, you're confined to the ground, checking for passing through these portals would be enough to toggle visibility for indoors or outdoors areas, however, when randomly flying around, this is not necessarily the case.

So.... What happens when you're flying around on a gryphon, and you fly into that arch-shaped portal into Ironforge? How is that portal calculated? It's all cool as long as you're inside "legal" areas, I suppose. 

It's fun, you can actually map out the topology of the [[WMO/v17]] using this and the [[WMO/v17#MOPR_chunk|MOPR]] chunk. This could be used to speed up the rendering once/if I figure out how.

==  MOPT chunk ==
*'''Portal information. 20 bytes per portal, nPortals entries.'''

 '''Offset	Type 		Description'''
 0x00 	uint16 		Base vertex index?
 0x02 	uint16 		Number of vertices (?), always 4 (?)
 0x04 	3*float 	a normal vector maybe? haven't checked.
 0x10 	float 		unknown  - if this is NAN, the three floats will be (0,0,1)

==  MOPR chunk ==
*'''Portal <> group relationship? 2*nPortals entries of 8 bytes.'''
I think this might specify the two [[WMO/v17]] groups that a portal connects.

''It's not correct that there's 2*nPortals of 8 bytes in all cases. For example in WOTLK data, Stormwind.wmo has 319 portals but only 627 portal relationships before MOVV chunk starts. Maybe some portals are unused or something, I haven't analyzed further - but there are many models where this is the case.    ---[[User:Relaxok|Relaxok]], 09-06-2012
''

 '''Offset 	Type 		Description'''
 0x0 	uint16 		Portal index
 0x2 	uint16 		WMO group index
 0x4 	int16 		1 or -1
 0x6 	uint16 		always 0

 struct SMOPortalRef'' // 04-29-2005 By ObscuR''
 {
   /*000h*/  UINT16 portalIndex;
   /*000h*/  UINT16 groupIndex;
   /*004h*/  UINT16 side;
   /*006h*/  UINT16 filler;
   /*008h*/
 };

==  MOVV chunk ==

*'''Visible block vertices''', 0xC byte per entry.

Just a list of vertices that corresponds to the visible block list.

==  MOVB chunk ==

*'''Visible block list'''

 unsigned short firstVertex;
 unsigned short count;

==  MOLT chunk ==

*'''Lighting information. 48 bytes per light, nLights entries'''

 '''Offset 	Type 		Description'''
 0x00 	4 * uint8 	Flags or something? Mostly (0,1,1,1)
 0x04 	4 * uint8 	Color (B,G,R,A)
 0x08 	3 * float 	Position (X,Z,-Y)
 0x14 	7 * float 	Unknown (light properties?)

 enum LightType 
 {
 	OMNI_LGT,
 	SPOT_LGT,
 	DIRECT_LGT,
 	AMBIENT_LGT
 };

 struct SMOLight ''// 04-29-2005 By ObscuR''
 {
   /*000h*/  UINT8 LightType; 	
   /*001h*/  UINT8 type;
   /*002h*/  UINT8 useAtten;
   /*003h*/  UINT8 pad;
   /*004h*/  UINT8 color[4];  
   /*008h*/  float position[3];
   /*014h*/  float intensity;
   /*018h*/  float attenStart;
   /*01Ch*/  float attenEnd;
   /*020h*/  float unk1;
   /*024h*/  float unk2;
   /*028h*/  float unk3;
   /*02Ch*/  float unk4;
   /*030h*/  
 };

I haven't quite figured out how WoW actually does lighting, as it seems much smoother than the regular vertex lighting in my screenshots. The light paramters might be range or attenuation information, or something else entirely. Some [[WMO/v17]] groups reference a lot of lights at once.

The WoW client (at least on my system) uses only one light, which is always directional. Attenuation is always (0, 0.7, 0.03). So I suppose for models/doodads (both are [[M2]] files anyway) it selects an appropriate light to turn on. Global light is handled similarly. Some [[WMO/v17]] textures ([[BLP]] files) have specular maps in the alpha channel, the pixel shader renderpath uses these. Still don't know how to determine direction/color for either the outdoor light or [[WMO/v17]] local lights... :)

==  MODS chunk ==
*'''This chunk defines doodad sets.''' 

Doodads in WoW are [[M2]] model files. There are 32 bytes per doodad set, and nSets entries. Doodad sets specify several versions of "interior decoration" for a [[WMO/v17]]. Like, a small house might have tables and a bed laid out neatly in one set called "Set_$DefaultGlobal", and have a horrible mess of abandoned broken things in another set called "Set_Abandoned01". The names are only informative.

The doodad set number for every WMO instance is specified in the [[ADT]] files.

 '''Offset 	Type 		Description'''
 0x00 	20 * char 	Set name
 0x14 	uint32 		index of first doodad instance in this set (this is not the name index,
                         but the actual order the doodads come in the MODD chunk in the WMO -MaiN)
 0x18 	uint32 		number of doodad instances in this set
 0x1C 	uint32 		unused? (always 0)

 struct SMODoodadSet // --[[User:Schlumpf|Schlumpf]] 17:03, 31 July 2007 (CEST)
 {
 /*000h*/  char   name[20];
 /*014h*/  UINT32 firstinstanceindex;
 /*018h*/  UINT32 numDoodads;
 /*01Ch*/  UINT32 nulls;
 }

==  MODN chunk ==

*'''List of filenames for [[M2]] ([[MDX|mdx]]) models that appear in this [[WMO/v17]].''' 
A block of zero-padded, zero-terminated strings. There are nModels file names in this list. They have to be .[[MDX]]!

==  MODD chunk ==

*'''Information for doodad instances. 40 bytes per doodad instance, nDoodads entries.''' 

-- There are not nDoodads entries here! Divide the chunk length by 40 to get the correct amount.

While [[WMO/v17]]s and models ([[M2]]s) in a map tile are rotated along the axes, doodads within a [[WMO/v17]] are oriented using quaternions! Hooray for consistency!

I had to do some tinkering and mirroring to orient the doodads correctly using the quaternion, see model.cpp in the WoWmapview source code for the exact transform matrix. It's probably because I'm using another coordinate system, as a lot of other coordinates in [[WMO/v17]]s and models also have to be read as (X,Z,-Y) to work in my system. But then again, the [[ADT]] files have the "correct" order of coordinates. Weird.

 '''Offset 	Type 		Description'''
 0x00 	uint24 		Offset to the start of the model's filename in the [[WMO/v17#MODN_chunk|MODN]] chunk.
 0x03	uint8		Flags (known: 1: CMapBaseObj::flags |= 0x800, 2: MapStaticEntity::field_34 |= 1).
 0x04 	3 * float 	Position (X,Z,-Y)
 0x10 	3 * float 	X, Y, Z components of the orientaton quaternion
 0x1C 	float 		W component of the orientation quaternion
 0x20 	float 		Scale factor
 0x24 	4 * uint8 	(B,G,R,A) Lightning-color. 

 struct SMODoodadDef ''// 03-29-2005 By ObscuR''
 {
   /*000h*/  UINT32 nameIndex
   /*004h*/  float pos[3];
   /*010h*/  float rot[4];
   /*020h*/  float scale;
   /*024h*/  UINT8 color[4];
   /*028h*/
 };

(nameIndex & 0xFFFFFF) is used as reference offset into modn. The upper byte seems to be some kind of flag (0,1,2 are checked for) and the doodad def adds some flags for them, see CWorldMap::CreateDoodadDef. The SMODoodadDef is the 3rd parameter. --[[User:Bananenbrot|Bananenbrot]] 16:01, 29 August 2012 (UTC)

==  MFOG chunk ==

*'''Fog information. Made up of blocks of 48 bytes.'''

 '''Offset 	Type 		Description'''
 0x00 	uint32 		Flags -- &1: Ignore radius (infinite radius) in CWorldView::QueryCameraFog 
 0x04 	float[3]	Position
 0x10 	float 		Smaller radius
 0x14 	float 		Larger radius
 0x18 	float 		Fog end
 0x1C 	float 		Fog start multiplier (0..1)
 0x20 	uint32 		Fog color                         //The back buffer is also cleared to this colour 
 0x24 	float 		Unknown (almost always 222.222)
 0x28 	float 		Unknown (-1 or -0.5)
 0x2C 	uint32 		Color 2

 struct SMOFog ''// 03-29-2005 By ObscuR''
 {
   /*000h*/  UINT32 flags;		
   /*004h*/  float pos[3];		
   /*008h*/ 	
   /*00Ch*/  		
   /*010h*/  float start[3];		
   /*014h*/  		
   /*018h*/ 		
   /*01Ch*/  float end[3];			
   /*020h*/  	
   /*024h*/   	
   /*028h*/  float fogs[2];
   /*02Ch*/  	
   /*030h*/		
 }
 
*Fog end: This is the distance at which all visibility ceases, and you see no objects or terrain except for the fog color.
*Fog start: This is where the fog starts. Obtained by multiplying the fog end value by the fog start multiplier.

== MCVP chunk (optional) ==

*'''Convex Volume Planes. Contains blocks of floating-point numbers.''' 0x10 bytes (4 floats) per entry.

= WMO group file =

WMO group files contain the actual polygon soup for a particular section of the entire [[WMO/v17]].

Every group file has one top-level [[WMO/v17#MOGP_chunk|MOGP]] chunk, that has a 68-byte header followed by more subchunks. So it can be effectively treated as a file with a header at 0x14 and chunks starting at 0x58. 

The subchunks are not always present. Some are fixed and needed while others are only checked for if some flags in the header are set. The chunks '''need''' to be in the right order if you want WoW to read it.

The following chunks are always present in the following order:
*[[WMO/v17#MOGP_chunk|MOGP]]
*[[WMO/v17#MOPY_chunk|MOPY]]
*[[WMO/v17#MOVI_chunk|MOVI]]
*[[WMO/v17#MOVT_chunk|MOVT]]
*[[WMO/v17#MONR_chunk|MONR]]
*[[WMO/v17#MOTV_chunk|MOTV]]
*[[WMO/v17#MOBA_chunk|MOBA]]

These chunks are only present if a flag in the header is set. See the list below for the flags.
*Cataclysm introduced a new optional MOBS chunk, I guess it's related to [[WMO/v17#MOBA_chunk|MOBA]]. ---[[User:Bananenbrot|Bananenbrot]], 12-18-2010
*[[WMO/v17#MOLR_chunk|MOLR]]
*[[WMO/v17#MODR_chunk|MODR]]
*[[WMO/v17#MOBN_chunk|MOBN]]
*[[WMO/v17#MOBR_chunk|MOBR]]
*MPBV
*MPBP
*MPBI
*MPBG
*[[WMO/v17#MOCV_chunk|MOCV]]
*[[WMO/v17#MLIQ_chunk|MLIQ]]
*MORI
*MORB


== MOGP chunk ==

Note: In its header is given a wrong size. Just use 0x44. -eLaps
*Actually, the size is correct, the other chunks are just subchunks of MOGP :) ---[[User:Tigurius|Tigurius]]

 '''Offset	Type		Description'''
 0x00 	uint32 		Group name (offset into [[WMO/v17#MOGN_chunk|MOGN]] chunk)
 0x04 	uint32 		Descriptive group name (offset into [[WMO/v17#MOGN_chunk|MOGN]] chunk)
 0x08 	uint32 		Flags
 0x0C 	float[3] 	Bounding box corner 1 (same as in [[WMO/v17#MOGI_chunk|MOGI]])
 0x18 	float[3] 	Bounding box corner 2
 0x24 	uint16 		Index into the [[WMO/v17#MOPR_chunk|MOPR]] chunk
 0x26 	uint16 		Number of items used from the [[WMO/v17#MOPR_chunk|MOPR]] chunk
 0x28 	uint16 		Number of batches A
 0x2A 	uint16 		Number of batches B
 0x2C 	uint32 		Number of batches C
 0x30 	uint8[4] 	Up to four indices into the WMO fog list
 0x34 	uint32 		LiquidType related, see below in the MLIQ chunk.
 0x38 	uint32 		WMO group ID (column 4 in [[WMOAreaTable.dbc]])
 0x3C 	uint32 		Always 0?
 0x40 	uint32 		Always 0?

*'''Struct from WoWModelViewer 0.6'''
 struct WMOGroupHeader {
     int nameStart, nameStart2, flags; 
 	float box1[3], box2[3]; 
 	short portalStart, portalCount;
 	short batches[4];
 	uint8 fogs[4];
 	int32 unk1, id, unk2, unk3;
 };

The fields referenced from the [[WMO/v17#MOPR_chunk|MOPR]] chunk indicate portals leading out of the [[WMO/v17]] group in question.

For the "Number of batches" fields, A + B + C == the total number of batches in the [[WMO/v17]] group (in the [[WMO/v17#MOBA_chunk|MOBA]] chunk). This might be some kind of LOD thing, or just separating the batches into different types/groups...?

Flags: always contain more information than flags in [[WMO/v17#MOGI_chunk|MOGI]]. I suppose [[WMO/v17#MOGI_chunk|MOGI]] only deals with topology/culling, while flags here also include rendering info.

 '''Flag		Meaning'''
 0x1		Has [[WMO/v17#MOBN_chunk|MOBN]] and [[WMO/v17#MOBR_chunk|MOBR]] chunk.
 0x2
 0x4 		Has vertex colors ([[WMO/v17#MOCV_chunk|MOCV]] chunk).
 0x8 		Outdoor
 0x10
 0x20
 0x40
 0x80
 0x100
 0x200 		Has lights  ([[WMO/v17#MOLR_chunk|MOLR]] chunk)
 0x400		Has MPBV, MPBP, MPBI, MPBG chunks. Yes, such chunks seem to exist.
 0x800 		Has doodads ([[WMO/v17#MODR_chunk|MODR]] chunk)
 0x1000		Has water   ([[WMO/v17#MLIQ_chunk|MLIQ]] chunk)
 0x2000		Indoor
 0x8000
 0x10000
 0x20000		Has MORI and MORB chunks.
 0x40000		Show skybox
 0x80000		isNotOcean, LiquidType related, see below in the MLIQ chunk.
 0x100000
 0x200000
 0x400000
 0x800000
 0x1000000	SMOGroup::CVERTS2: Has two MOCV chunks: Just add two or don't set 0x4 to only use cverts2.
 0x2000000	SMOGroup::TVERTS2: Has two MOTV chunks: Just add two.

==  MOPY chunk ==

*'''Material info for triangles, two bytes per triangle. So size of this chunk in bytes is twice the number of triangles in the WMO group.'''

 '''Offset	Type 	Description'''
 0x00 	uint8 	Flags?
 0x01 	uint8 	Material ID

 struct SMOPoly ''// 03-29-2005 By ObscuR''
 {
 	enum  
 	{
 		F_NOCAMCOLLIDE,
 		F_DETAIL,
  		F_COLLISION,
 		F_HINT,
 		F_RENDER,
 		F_COLLIDE_HIT,
 	};
 /*000h*/  uint8 flags;
 /*001h*/  uint8 mtlId;
 };
 
 // are you sure it's 3 bytes? wowmapview uses groups of 2 :)  - Z.
 // look like the lightmapTex byte is no longer present, this struct come from Alpha :) - Obs

Frequently used flags are 0x20 and 0x40, but I have no idea what they do.

 '''Flag	Description'''
 0x00 	?
 0x01 	?
 0x02 	NOCAMCOLLIDE
 0x04 	no collision
 0x08 	?
 0x20 	?
 0x40 	?

From 15464:
 bool isNoCamCollide (uint8 flags) { return flags & 2; }
 bool isDetailFace (uint8 flags) { return flags & 4; }
 bool isCollisionFace (uint8 flags) { return flags & 8; }
 bool isColor (uint8 flags) { return !(flags & 8); }
 bool isRenderFace (uint8 flags) { return (flags & 0x24) == 0x20; }
 bool isTransFace (uint8 flags) { return (flags & 1) && (flags & 0x24); }
 bool isCollidable (uint8 flags) { return isCollisionFace (flags) || isRenderFace (flags); }

Material ID specifies an index into the material table in the root [[WMO/v17]] file's [[WMO/v17#MOMT_chunk|MOMT]] chunk. Some of the triangles have 0xFF for the material ID, I skip these. (but there might very well be a use for them?)

The triangles with 0xFF Material ID seem to be a simplified mesh. Like for collision detection or something like that. At least stairs are flattened to ramps if you only display these polys. --[[User:shlainn|shlainn]] 7 Jun 2009

0xFF representing -1 is used for collision-only triangles. They aren't rendered but have collision. Problem with it: WoW seems to cast and reflect light on them. Its a bug in the engine. --[[User:Schlumpf|schlumpf_]] 20:40, 7 June 2009 (CEST)

Triangles stored here are more-or-less pre-sorted by texture, so it's ok to draw them sequentially.

== MOVI chunk ==

*'''Vertex indices for triangles.''', count = size / sizeof(unsigned short). Three 16-bit integers per triangle, that are indices into the vertex list. The numbers specify the 3 vertices for each triangle, their order makes it possible to do backface culling.

== MOVT chunk ==

*'''Vertices chunk.''', count = size / (sizeof(float) * 3). 3 floats per vertex, the coordinates are in (X,Z,-Y) order. It's likely that [[WMO/v17]]s and models ([[M2]]s) were created in a coordinate system with the Z axis pointing up and the Y axis into the screen, whereas in OpenGL, the coordinate system used in WoWmapview the Z axis points toward the viewer and the Y axis points up. Hence the juggling around with coordinates.

==  MONR chunk ==

*'''Normals.''' count = size / (sizeof(float) * 3). 3 floats per vertex normal, in (X,Z,-Y) order.

== MOTV chunk ==

*'''Texture coordinates, 2 floats per vertex in (X,Y) order.''' The values range from 0.0 to 1.0. Vertices, normals and texture coordinates are in corresponding order, of course.

== MOBA chunk ==
 
*'''Render batches. Records of 24 bytes.'''

 struct SMOBatch'' // 03-29-2005 By ObscuR''
 {
 	enum
 	{
 		F_RENDERED
 	};
 	?? lightMap;
 	?? texture;
 	?? bx;
 	?? by;
 	?? bz;
 	?? tx;
 	?? ty;
 	?? tz;
 	?? startIndex;
 	?? count;
 	?? minIndex;
 	?? maxIndex;
 	?? flags;
 };

For the enUS, enGB versions, it seems to be different from the preceding struct:
 '''Offset	Type 		Description'''
 0x00 	uint32 		Some color?
 0x04 	uint32 		Some color?
 0x08 	uint32 		Some color?
 0x0C 	uint32 		Start index
 0x10 	uint16 		Number of indices
 0x12 	uint16 		Start vertex
 0x14 	uint16 		End vertex
 0x16 	uint8 		0?
 0x17 	uint8 		Texture

In my eyes, looks more like:
 struct
 {
 /*0x00*/ int16_t a[2*3]; // indices? a box? (-2,-2,-1,2,2,3 in cameron)
 /*0x0C*/ uint32_t start?;
 /*0x10*/ uint16_t num?;
 /*0x12*/ uint16_t[2];
 /*0x16*/ uint8_t;
 /*0x17*/ uint8_t materialId; // index into MOMT
 }
--[[User:Schlumpf|Schlumpf]] 22:16, 4 March 2011 (UTC)

==  MOLR chunk ==

*'''Light references, one 16-bit integer per light reference.'''

This is basically a list of lights used in this [[WMO/v17]] group, the numbers are indices into the [[WMO/v17]] root file's [[WMO/v17#MOLT_chunk|MOLT]] table.

For some [[WMO/v17]] groups there is a large number of lights specified here, more than what a typical video card will handle at once. I wonder how they do lighting properly. Currently, I just turn on the first GL_MAX_LIGHTS and hope for the best. :(

== MODR chunk ==

*'''Doodad references, one 16-bit integer per doodad.'''
The numbers are indices into the doodad instance table ([[WMO/v17#MODD_chunk|MODD]] chunk) of the [[WMO/v17]] root file. These have to be filtered to the doodad set being used in any given [[WMO/v17]] instance.

== MOBN chunk ==

*'''Array of t_BSP_NODE. / CAaBspNode.''' 0x10 bytes.
 
 struct t_BSP_NODE
 {	
 	short planetype;          // 4: leaf, 0 for YZ-plane, 1 for XZ-plane, 2 for XY-plane?
 	short children[2];        // index of bsp child node(right in this array)   
 	unsigned short numfaces;  // num of triangle faces in [[WMO/v17#MOBR_chunk|MOBR]]. May not be more than 300.
 	unsigned int firstface;   // index of the first triangle index(in [[WMO/v17#MOBR_chunk|MOBR]])
 	float fDist;    
 };
 // The numfaces and firstface define a polygon plane.
                                         ''2005-4-4 by linghuye''

This+BoundingBox(in wmo_root.MOGI) is used for Collision --[[User:Tigurius|Tigurius]]

How? A plane can only be defined by a minimum of three points, two points is a line. How is collision done? --[[User:omni123|omni123]]


 #define epsilon 0.01F
 void MergeBox(CVect3 (&result)[2], float  *box1, float  *box2)'''
 {
  result[0][0] = box1[0];
  result[0][1] = box1[1];
  result[0][2] = box1[2];
  result[1][0] = box2[0];
  result[1][1] = box2[1];
  result[1][2] = box2[2];
 }
 void   AjustDelta(CVect3 (&src)[2], float *dst, float coef)'''
 {
  float d1 = (src[1][0]- src[0][0]) * coef;// delta x
  float d2 = (src[1][1]- src[0][1]) * coef;// delta y
  float d3 = (src[1][2]- src[0][2]) * coef;// delta z
  dst[1] = d1 + src[0][1];
  dst[0] = d2 + src[0][0];
  dst[2] = d3 + src[0][2];
 }
 void TraverseBsp(int iNode, CVect3 (&pEyes)[2] , CVect3 (&pBox)[2],void *(pAction)(T_BSP_NODE *,void *param),void *param)'''
  {
  int plane;
  float eyesmin_boxmin;
  float boxmax_eyesmax;
  float eyesmin_fdist;
  float eyes_max_fdist;
  float eyesmin_div_deltadist;
  CVect3 tBox1[2];
  CVect3 tBox2[2];
  CVect3 newEyes[2];
  CVect3 ajusted;
  T_BSP_NODE *pNode = &m_tNode[iNode];
  if ( pNode)
  {
   if (pNode->planetype & 4 )
   {
    if(pAction == 0)
    {
     RenderGeometry(GetEngine3DInstance(),pNode);
     return;
    }
    else
    {
     pAction(pNode,param);
    }
   }
   plane =pNode->planetype  & 3;
   eyesmin_boxmin = pEyes[0][plane] - pBox[0][plane];
   if ( ( -epsilon < eyesmin_boxmin) | (-epsilon == eyesmin_boxmin) || (pEyes[1][plane]- pBox[0][plane])  >= -epsilon )
   {
    boxmax_eyesmax = pBox[1][plane] - pEyes[1][plane];
    if ( (epsilon < boxmax_eyesmax) | (epsilon == boxmax_eyesmax) || (pBox[1][plane] -  pEyes[0][plane]) >= epsilon )
    {
     memmove(tBox1,pBox,sizeof(pBox));
     tBox1[0][plane] = pNode->fDist;
     memmove(tBox2,pBox,sizeof(pBox));
     tBox2[1][plane] = pNode->fDist;
     eyesmin_fdist = pEyes[0][plane] - pNode->fDist;
     eyes_max_fdist = (pEyes[1][plane]) - pNode->fDist;
     if ( eyesmin_fdist >= -epsilon && eyesmin_fdist <= epsilon|| (eyes_max_fdist >= -epsilon) && eyes_max_fdist <= epsilon )
     {
      if ( pNode->children[1] != (short)-1 ) TraverseBsp(pNode->children[1],  pEyes,  tBox1,pAction,param);
      if ( pNode->children[0] != (short)-1 ) TraverseBsp(pNode->children[0] , pEyes, tBox2,pAction,param);
      return;
     }
     if ( eyesmin_fdist > epsilon && eyes_max_fdist < epsilon)
     {
       if ( pNode->children[1] != (short)-1 ) TraverseBsp(pNode->children[1], pEyes, tBox1,pAction,param);
       return;
     }
     if ( eyesmin_fdist < -epsilon && eyes_max_fdist < -epsilon)
     {
       if ( pNode->children[0] != (short)-1 ) TraverseBsp(pNode->children[0] , pEyes, tBox2,pAction,param);
       return;
     }
     eyesmin_div_deltadist = (float)(eyesmin_fdist / (eyesmin_fdist - eyes_max_fdist));
     AjustDelta(pEyes, ajusted, eyesmin_div_deltadist);
     if ( eyesmin_fdist <= 0.0 )
     {
      if ( pNode->children[0]  != (short)-1 )
      {
       MergeBox(newEyes, &pEyes[0][0], ajusted);
       TraverseBsp(pNode->children[0] , newEyes, tBox2,pAction,param);
      }
      if (pNode->children[1]  != (short)-1 )
      {
       MergeBox(newEyes, ajusted, &pEyes[1][0]);
       TraverseBsp(pNode->children[1] , newEyes, tBox1,pAction,param);
      }
     }
     else
     {
      if ( pNode->children[1]  != (short)-1 )
      {
       MergeBox(newEyes, &pEyes[0][0], ajusted);
       TraverseBsp(pNode->children[1] , newEyes, tBox1,pAction,param);
      }
      if (pNode->children[0]  != (short)-1 )
      {
       MergeBox(newEyes, ajusted, &pEyes[1][0]);
       TraverseBsp(pNode->children[0] , newEyes, tBox2,pAction,param);
      }
     }
    }
   }
  }
 }


 CheckFromEyes(CVect3 (&pEyes)[2],void *(pAction)(T_BSP_NODE *,void *param),void *param )
 {
 /*CVect3 eyes[2];
 instance_mat.invert();
 eyes[0] = _fixCoordSystemInv((instance_mat*p->m_pCameraViewport->GetCameraTarget())+CVect3(0,-10,0) );
 eyes[1] = _fixCoordSystemInv((instance_mat*p->m_pCameraViewport->GetCameraTarget())+CVect3(0,60,0) ); 
  // make vector down
 */
 /* eyes[0] = CVect3(-1.474797e+001F, -1.195053e+001F,  5.416779e+000F); // Debug absolute position from WP  Azaroth 1164,58,-10645.83
 eyes[1] = CVect3(-1.474797e+001F, -1.195053e+001F, -1.754583e+003F);
 */
 TraverseBsp(0,pEyes,m_bbox,pAction);
 }


This BSP seems to be used for collision purpose only.  

An object could have has 2 collision system. The first one is encoded in a simplified Geometry (when MOPY. MaterialID=0xFF) the second one is encoded in T_BSP_NODE.
Some object has collision method 1 only, some other uses method 2 only. Some object have both collision systems (some polygons are missing in the BSP but are present in the simplified geometry). how  to use these 2 system remains unclear. 

For the time being, I check first the simplified geometry, and then if there is no collision, I apply a second pass using the BSP. It is sub-optimum, but it seems to work.
Probably there is somewhere a flag telling us with which method we should use for the object.

The  code attached seems to work fine for BSP method--[[peter-pan|peter-pan]].




planetype might be 0 for YZ-plane, 1 for XZ-plane, 2 for XY-plane, 4 for BSP leaf. fDist is where split plane locates based on planetype, ex, you have a planetype 0 and fDist 15, so the split plane is located at offset ( 15, 0, 0 ) with Normal as ( 1, 0, 0 ), I think the offset is relative to current node's bounding box center. The BSP root ( ie. node 0 )'s bounding box is the WMO's boundingbox, then you subdivide it with plane and fdist, then you got two children with two bounding box, and so on. you got the whole BSP tree. As the bsp leaf might overlapping the dividing plane, i think you might have two same face exist on two different bsp leaf. I'll make further tests to prove this. --[[mobius|mobius]].

==  MOBR chunk ==
*'''Face indices''' for CAaBsp (MOBN). Unsigned shorts.
*'''Triangle indices (in [[WMO/v17#MOVI_chunk|MOVI]] which define triangles) to describe polygon planes defined by [[WMO/v17#MOBN_chunk|MOBN]] BSP nodes.'''

== MOCV chunk ==

*'''Vertex colors, 4 bytes per vertex (BGRA), for [[WMO/v17]] groups using indoor lighting.''' 
I don't know if this is supposed to work together with, or replace, the lights referenced in [[WMO/v17#MOLR_chunk|MOLR]]. But it sure is the only way for the ground around the goblin smelting pot to turn red in the Deadmines. (but some corridors are, in turn, too dark - how the hell does lighting work anyway, are there lightmaps hidden somewhere?)

- I'm pretty sure WoW does not use lightmaps in it's [[WMO/v17]]s...

After further inspection, this is it, actual pre-lit vertex colors for [[WMO/v17]]s - vertex lighting is turned off. This is used if flag 0x2000 in the [[WMO/v17#MOGI_chunk|MOGI]] chunk is on for this group. This pretty much fixes indoor lighting in Ironforge and Undercity. The "light" lights are used only for [[M2]] models (doodads and characters). (The "too dark" corridors seemed like that because I was looking at it in a window - in full screen it looks pretty much the same as in the game) Now THAT's progress!!!

''Yes, 0x2000 (INDOOR) flagged WMO groups use _only_ MOCV for lighting, however this chunk is also used to light outdoor groups as well like lantern glow on buildings, etc.  If 0x8 (OUTDOOR) flag is set, you start out with normal world lighting (like with light dbc params) and then you multiply these vertex colors by the texture color and add it to the world lighting.  This makes many models look much better.  See the Forsaken buildings in Howling Fjord for an example of some that make use of this a lot for glowing windows and lamps. [[User:Relaxok|Relaxok]] 18:29, 20 March 2013 (UTC)''

==  MLIQ chunk ==

*'''Specifies liquids inside WMOs.''' 
This is where the water from Stormwind and BFD etc. is hidden. (slime in Undercity, pool water in the Darnassus temple, some lava in IF)

Chunk header:
 '''Offset	Type 		Description'''
 0x00 	uint32 		number of X vertices (xverts)
 0x04 	uint32 		number of Y vertices (yverts)
 0x08 	uint32 		number of X tiles (xtiles = xverts-1)
 0x0C 	uint32 		number of Y tiles (ytiles = yverts-1)
 0x10 	float[3] 	base coordinates for X and Y
 0x1C 	uint16 		material ID
 0x1E 	c2vector[xtiles*ytiles]
 ?????? 	types[xtiles*ytiles]	Unsure, if really types. (0 - 20)

The liquid data contains the vertex height map (xverts * yverts * 8 bytes) and the tile flags (xtiles * ytiles bytes) as descripbed in [[ADT]] files ([[ADT#MCLQ_chunk|MCLQ]] chunk). The length and width of a liquid tile is the same as on the map, that is, 1/8th of the length of a map chunk. (which is in turn 1/16th the length of a map tile).

Note that although I could read Mh2o's heightmap and existstable in row major order (like reading a book), I had to read this one in column major order to compensate for a 90° misrotation. --[[User:Bananenbrot|Bananenbrot]] 22:02, 1 August 2012 (UTC)

*the real deal
The LiquidType in the DBC is determined as follows: 

If var_0x3C in the root's MOHD has the 4 bit (&4), it will take the variable in MOGP's var_0x34. If not, it checks var_0x34 for 15 (green lava). If that is set, it will take 0, else it will take var_0x34 + 1.

The result of this (0,var_0x34 or var_0x34+1) will be checked if above 21 (naxxramas slime). If yes, the entry is stored as given. Else, it will be checked for the type (ocean, water, magma, slime). Ocean might be overwritten by MOGP flags being & 0x80000.

*tl;dr
MOGP.var_0x34 is LiquidType. This will be overwritten with the "WMO *" liquid types in case, this is below 21 (naxxramas slime). Additionally, it will be taken +1 if the flag in the root's header is not set.

*old:
''The material ID often refers to what seems to be a "special" material in the root [[WMO/v17]] file (special because it often has a solid color/placeholder texture, or a texture from XTextures\*) - but sometimes the material referenced seems to be not special at all, so I'm not really sure how the liquid material is obtained - such as water/slime/lava.''

== Unknown Chunk ==
''(Yes, I don't even know the identifier. But it is there. Might be one of the following.)''

There are size>>1 entries in it. It modifies the vertices indexes or something.

== MORI ==
* shorts.
== MORB==
* ignored if !CMap::enableTriangleStrips
* modifies MOBA, therefore has same count.
* size is not checked, but 2 * sizeof(int), even though it is only (int, short).
 struct MORB_entry
 {
   uint32_t start_index;
   uint16_t index_count;
   uint16_t padding;
 }
* overwrites 0xC and 0x10 of MOBA (start, count).

== MOTA==
* unsure, which size / data types.
* separated in two parts:
** [0 .. moba_count * 2[
** [moba_count * 2 .. ?]
== MOBS==
* size = 0x18
 struct MOBS_entry
 {
   char unk[0x18];
 };