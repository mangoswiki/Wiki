[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

##Introduction

ZMP Files - presumably for **Z**one **M**a**p** - link map data to location info from [AreaTable.dbc](dbc_AreaTable_MaNgosZero). There are 3 of those files in 1.12.2:

* Interface\WorldMap\Azeroth.zmp
* Interface\WorldMap\Expansion01.zmp (in patch.MPQ, no data present)
* Interface\WorldMap\Kalimdor.zmp

## Structure

The files are headerless. They contain 128 x 128 uint32 values (double resolution compared to WDT) which are area IDs from [AreaTable.dbc](dbc_AreaTable_MaNgosZero)

## Speculation

I think it is possible that this file is used by the client to display the name of the current area while moving in the World. -- shlainn

WowDev Wiki says:

>They are used on parsing WorldMapArea.dbc. The values get copied and then get overwritten with the WorldMapArea-id the areaid they referenced is in. It will hold a zero or the WMA-id depending on if the area and the map that's currently parsed match. This also takes the virtual map id into account.