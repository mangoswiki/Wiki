[![](/wiki/icons/home.gif)](/wiki/Home.md) 

----------

###Frequently Asked Questions about MaNGOS

#### Not sure how to Install?

See our [**Installation Instructions**](Installation%20Instructions)

#### I cannot login onto my server
* realmd started?
* mangosd started?
* realmd database, table `realmlist` set to match the values in your **mangosd.conf** ?
* realmlist set to your localhost ? (**set realmlist 127.0.0.1**)
* User account created? (Did you follow [**Installation Instructions**](Installation%20Instructions) correctly)

#### I play TBC, WotLK, Cata or MOP and cannot access the Blood Elves, Draenei, Worgen, Goblins or Pandaran
* You need to set you account for the required expansion as below :-

<pre>
    1 for TBC for Blood Elves, Draenei
    2 for WotLK for Deathknight, plus all TBC
    3 for Worgen and Goblins, plus all WoTLK and TBC
    4 for Pandaran, plus all Cata, WotLK and TBC
</pre>

#### MaNGOSd or/and Realmd quit instantly when I start them !
* Run mangos in command line instead, if you have git bash that's also fine. Then you will see the onscreen error output and be able to continue from there.

#### I play WotLK/Cata/MOP and cannot access the Death Knight
- You need to the expansion of your account to 2, 3 or 4 (2 for WotLK, 3 for Cata, 4 for MOP)
- You need to level a character to level 50 OR
- Change the config option "MinLevelForHeroicCharacterCreating" in your **mangosd.conf** OR
- Set your account to be a GM Account (see below)

#### How do I use GM commands?
* You need to set your GM-Level. See the [**Installation Instructions**](Installation%20Instructions)

#### Typical Compiling Problems

#### ACE-Error while compiling vmap_assembler on a linux system
If you get an error like:
    
    [...]
    ../../dep/ACE_wrappers/ace/config-lite.h:24,
                 from ../../dep/ACE_wrappers/ace/Basic_Types.h:46,
                 from ../../src/framework/Platform/Define.h:25,
                 from ../../src/game/vmap/ModelInstance.h:28,
                 from ../../src/game/vmap/TileAssembler.h:28,
                 from vmap_assembler.cpp:23:
    ../../dep/ACE_wrappers/ace/config-macros.h:28:26: error: ace/config.h: No such file or directory
    [...]

create the file **config.h** in the directory **[server]/dep/ACE_wrappers/ace/** and fill it with the content: 

    #include "config-linux.h"

to do so just run the following on the shell:

    echo '#include "config-linux.h"' > /path/to/source/server/dep/ACE_wrappers/ace/config.h


####Time Out error when pushing updates and sometimes when cloning repo's.

#####After loads of research I found the solution (for windows anyway)...

Here's what to do:-

1) Open a command prompt with admin priviledges<br/>
2) Type <pre>tracert git.com</pre>

   I got the response... <pre>Tracing route to git.com [75.101.142.70]</pre>
   - remember that number

3) Type <pre>ipconfig</pre>
   I got the response... <pre>Default Gateway . . . . . . . . . : 192.168.10.254</pre>
   - remember that number too

4) Type <pre>route add [number from step 2] [number from step 3]</pre>
   i.e. <pre>route add 75.101.142.70 192.168.10.254</pre>

The above resolved the timeout issues for me.

###Where would I find and modify the list of unacceptable names?
####You tried to create a character with the name Baroni and the system said that it was an invalid name. So you had to go with Barani. How do I get WoW/Mangos to accept Baroni with an O?

If you modify the characters name directly in the database this will bypass the reserved names file. Log back in and you have got Baroni instead of Barani now.
