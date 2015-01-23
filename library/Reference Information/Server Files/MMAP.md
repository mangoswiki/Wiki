[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

MMaps Information
----

This page contains information on MMaps which are now included in the MaNGOS Core

###What are MMaps?

"MMaps" is an abbreviation for "Movement Maps."
They essentially handle the movement of creature path-finding and paths on a particular map.

###What do they do to improve things ?

In simple terms, they will prevent creatures and npcs from passing through the map (I.E. running through a hill, a tree, or a wall).

###How do they manage that ?

* MMaps load individual tiles for individual areas of each map. By doing so, it forces the creature movement on the maps to obey a set of rules.
* By establishing these "rules", it prevents creatures from passing through these "tiles", which creates the effect of creatures understanding their environmental surroundings.
* This also enforces LOS (Line of Sight) when a creature is in combat.

As you can see, this is a very important addition to the Core, as they enhance many aspects of overall game-play.

For more information, see: [navmesh](http://code.google.com/p/recastnavigation)
