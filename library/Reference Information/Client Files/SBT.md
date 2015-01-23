[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

### Introduction

For each cinematic there is one SBT (**S**u**BT**itle) file found in Interface\Cinematics (interface.MPQ). It contains localized subtitles for movies.

### File Structure
At the beginning are 3 bytes 0xEF BB BF. Some kind of ID/Magic bytes/unknown stuff.

Each entry is made of a timestamp and a text. The entries are divided by an empty line.

    00:00:04:06 - 00:00:13:01
    Four years have passed since the mortal races banded together and stood united against the might of the Burning Legion. 
    
    00:00:14:00 - 00:00:22:05
    Though Azeroth was saved, the tenuous pact between the Horde and the Alliance has all but evaporated. 
    
    00:00:24:06 - 00:00:28:21
    The drums of war thunder once again. 

The timestamp is hr:min:sec:msec.
