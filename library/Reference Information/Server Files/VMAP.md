[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

VMAP stands for MaNGOS WoW Vertex Map Physics Info

##VMAPS
Vmaps are used to implement vertical clipping related issues. They are required for spells, which require the caster to have its target in line of sight and random movement generators (fear for example).

They are extracted from the client and will be stored in a MaNGOS own format.

##Generation

The generation takes place in two steps. 

First, all important WMO files are exported from the MPQ files and written to the `buildings` subdirectory. 

Additionally a file containing information about the positions of these WMOs in the world is generated from ADT files and will be written to the `buildings` folder.

In a second step, these information are assembled to .vmap and .vmdir file.

##Extracted WMO format
The extracted wmo files in the Buildings subdirectory have a special format - they are **not** to be mixed up with the client internal format of the same name.

    byte[8]         magic "VMAPxxx"
    uint32          nVectors
    uint32          nGroups
    nGroups         times:
	uint32          liqudflags
	uint32          "GRP "
	uint32          moba_size
	uint32          moba_batch
	uint32          mobaex
	uint32          "INDX"
	uint32          wsize
	uint32          nIndexes
	nIndexes        times:
	float[3]        movt
	uint32          "VERT"
	uint32          wsize
	uint32          nVertices
	nVertices       times:
	float[3]        vertice
	uint32          "LIQU"
	uint32          LiqExsize
	uint32          hlq_xverts
	uint32          hlq_yverts
	LiquidEx_size/4 times:
	float           LiquidEx
