[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md)

----------

##How to Setup a MaNGOS Server from Scratch
 
(without using repacks)

This document will explain how to setup a MaNGOS World of Warcraft Server on Windows from Scratch

###Required Software

----

All the required software below (apart from the OS) is free software and there are various options from MS to get long evaluation versions of their Server OS’s

* **A Windows Server OS** - I normally use Windows Server 2008
* [**MySQL - Community Server**](http://dev.mysql.com/downloads/mysql/)
* [**SQLyog - Community Edition**](http://code.google.com/p/sqlyog/wiki/Downloads)
* [**Git**](http://msysgit.github.io/) 
* **World of Warcraft** - You will need the version for the expansion of your server
* **Visual Studio 2010 or 2012 (Express or otherwise)**

####Optional Software

----
* [**Notepad ++**](http://notepad-plus-plus.org/download)
* [**CCleaner**](http://www.piriform.com/ccleaner/download)

 
###Important Things to remember

---
These may sound obvious, but it amazes me how often people forget these details later

    1. Server Admin Password: INFO1=[             ] e.g. Pa55word
    2. Server IP Address:     INFO2=[  .          ] e.g. 192.168.10.20
    3. MySQL Root Password:   INFO3=[             ] e.g. mangos

###Server Installation

----
The following section details setting up the Server, installing an OS on it and Installing MySQL onto the server.

####Installing the Server OS
1)      Install the Operating System as normal.

2)      Install any Windows Updates that may be required

3)      Record the password used in the under ***INFO1*** on the page 3

####Installing the Server Applications
***MySQL***

1)      MySQL is the Database that MaNGOS runs on

2)       Select ‘Complete’, followed by ‘Install’ and ‘Finish’ to complete the installation

3)      Once the installation is complete, the ‘Instance Configuration Wizard’ will start

4)      Select ‘Standard Configuration’

5)      Tick ‘Include Bin Directory in Windows PATH’

6)      Enter a Root Password, store this password as ***INFO3*** page 3

7)      Tick ‘Enable Root Access from remote machines’

8)      Continue through the screens then click ‘Execute’, followed by finish the setup

***SQLyog***

1)      SQLyog is a graphical front end for MySQL

2)      The install is straight forward with all the default options being fine

3)      After installation, SQLyog is started up

4)      After clicking ‘Continue’ on the nag screen, you will come to the ‘Connection’ screen

5)      Select ‘New’, set a name as ‘Mangos Server’ and click ok, then set the password to the value you recorded in ***INFO3***

6)      Then click ‘Connect’

7)      When you get to the treeview screen, then MySQL is set correctly and working:-


####Data Applications
The following applications are required for getting the actual data and files required for the mangos server to run.

***Git***

Git is a package used by the MaNGOS team to control the source files for MaNGOS.

1)      Click through the screens of the install until this screen:-

2)      Click the option ‘Git Bash Here’ and continue on using the default values.

####Setting up the MaNGOS server Databases
1)      Open SQLyog and connect to the databases

2)      Right Click on “root@localhost” and select ‘Create Database’

3)      Type “Mangos” into the Database name field, then click “Create”

4)      Right Click on “root@localhost” and select ‘Create Database’

5)      Type “Characters” into the Database name field, then click “Create”

6)      Right Click on “root@localhost” and select ‘Create Database’

7)      Type “Realmd” into the Database name field, then click “Create”

**FOLLOWING STEP NOT REQUIRED FOR MANGOS ZERO**

8)      Right Click on “root@localhost” and select ‘Create Database’

**FOLLOWING STEP NOT REQUIRED FOR MANGOS ZERO**

9)      Type “ScriptDev2” into the Database name field, then click “Create”

####Downloading the MaNGOS Source Code

1)   Open ‘My Computer’ and open ‘Local Disk (C :)’

2)   Right click in an empty area and select ‘New => Folder’, name this folder “MangosSource”

3)   Right Click on “MangosSource” and select “Git Bash Here”

4)   The command prompt style window will open and wait with a prompt “$”

5)   Type: 

   for MaNGOS Zero (Vanilla)
    
    git clone --recursive http://github.com/mangoszero/server
The **--recursive** in the above command is very important! Without it compiling will fail.

   for MaNGOS One (TBC)
    
    git clone --recursive http://github.com/mangosone/server
    cd mangos/src/bindings
    git clone --recursive http://github.com/mangosone/scripts
    
   for MaNGOS Two (WoTLK)
    
    git clone --recursive http://github.com/mangostwo/server
    cd mangos/src/bindings
    git clone --recursive http://github.com/mangostwo/scripts

   for MaNGOS Three (Cata)

    git clone --recursive http://github.com/mangosthree/server
    cd mangos/src/bindings
    git clone --recursive http://github.com/mangosthree/scripts

   for MaNGOS Four (Mop)

    git clone --recursive http://github.com/mangosfour/server

6)   .... This will take a while

**The source Code for MaNGOS is now located in the `server` folder**

######We now need to modify the mangos build process to load in the script library

**THIS STEP IS NOT REQUIRED FOR MANGOS ZERO**

7) edit **CMakeLists.txt** in this folder

change

    # add_subdirectory(scripts)

to

    add_subdirectory(scripts)


###Downloading and Importing the Database Data
1)   Type: 

   for MaNGOS Zero (Vanilla)

    git clone --recursive http://github.com/mangoszero/database

   for MaNGOS One (TBC)

    git clone --recursive http://github.com/mangosone/database
    
   for MaNGOS Two (WoTLK)

    git clone --recursive http://github.com/mangostwo/database

   for MaNGOS Three (Cata)

    git clone --recursive http://github.com/mangosthree/database

   for MaNGOS Four (Mop)

    git clone --recursive http://github.com/mangosfour/database

2)      .... This will take a while

**The Database SQL Files are located in this folder**

    cd database/_tools
    make_full_db.sh
    mysql -u root -p mangos < full_db.sql

** should this fail with unknown command, see below**

You will need to add the path of MySQL.exe to the command, something like:-

    "C:\Program Files\MySQL\MySQL Server 5.6\bin\MySQL" -u root -p mangos < full_db.sql

The MaNGOS Databases have now been populated with data

**Once complete the scripts database entries need to be added

**THIS STEP IS NOT REQUIRED FOR MANGOS ZERO**

3) Now load scripts database entries

    cd ../..
    cd server/src/bindings/scripts/sql
    mysql -u root -p mangos < mangos_scriptname_clear.sql
    mysql -u root -p mangos < mangos_scriptname_full.sql
    mysql -u root -p scriptdev2 < scriptdev2_create_structure_mysql.sql
    mysql -u root -p scriptdev2 < scriptdev2_script_full.sql

**should this fail with unknown command, see below**

You will need to add the path of MySQL.exe to the command, something like:-

    "C:\Program Files\MySQL\MySQL Server 5.6\bin\MySQL" -u root -p mangos < mangos_scriptname_clear.sql
    "C:\Program Files\MySQL\MySQL Server 5.6\bin\MySQL" -u root -p mangos < mangos_scriptname_full.sql
    "C:\Program Files\MySQL\MySQL Server 5.6\bin\MySQL" -u root -p scriptdev2 < scriptdev2_create_structure_mysql.sql
    "C:\Program Files\MySQL\MySQL Server 5.6\bin\MySQL" -u root -p scriptdev2 < scriptdev2_script_full.sql

The MaNGOS Databases have been update and the scripts database has now been populated with data


##Extracting Game Data
_This step is also documented at the page [**Extract Game Assets**](Extracting-Game-Assets) (Windows and Linux)_

1)      Click on “My computer”

2)      Navigate to the following path:

**FOR MANGOS ZERO**

 “C:\MangosSource\server\bin”

**FOR ALL OTHERS**

 “C:\MangosSource\server\contrib\extractor_binary”

3)      Copy all the files into your ‘Warcraft’ Folder (where Launcher.exe and WOW.exe are)

**STEPS 4 THROUGH 9 ARE NOT REQUIRED FOR MANGOS ZERO**

4)      Navigate to the path “C:\MangosSource \server\contrib\extractor”

5)      Copy the file `ad.exe` into your ‘Warcraft’ Folder (where Launcher.exe and WOW.exe are)

6)      Run `ad.exe` and let it do its stuff.

It should look something like the following:-

    Map & DBC Extractor
    ===================
    Detected locale: enGB
    Opening ./Data/enGB/locale-enGB.MPQ
    Opening ./Data/enGB/patch-enGB.MPQ
    Opening ./Data/enGB/patch-enGB-2.MPQ
    Opening ./Data/enGB/patch-enGB-3.MPQ
    Detected client build: 12340
    Extracting dbc files...
    Extracted 246 DBC files

    Using locale: enGB
    Opening ./Data/enGB/locale-enGB.MPQ
    Opening ./Data/enGB/patch-enGB.MPQ
    Opening ./Data/enGB/patch-enGB-2.MPQ
    Opening ./Data/enGB/patch-enGB-3.MPQ
    Opening ./Data/common.MPQ
    Opening ./Data/common-2.MPQ
    Opening ./Data/lichking.MPQ
    Opening ./Data/expansion.MPQ
    Opening ./Data/patch.MPQ
    Opening ./Data/patch-2.MPQ
    Opening ./Data/patch-3.MPQ

    Extracting maps...

    Read Map.dbc file... Done! (135 maps loaded)
    Read AreaTable.dbc file...Done! (2307 areas loaded)
    Read LiquidType.dbc file...Done! (26 LiqTypes loaded)

    Convert map files
    Extract Azeroth (1/135)
    Extract Kalimdor (2/135)

    ..... ETC .....

7)      Run `make_vmaps.bat` and let it do its stuff.

Sample Output:-

    E:\World of Warcraft>vmapExtractor.exe

    Extract V3.00 2010_07. Beginning work ....
    Game path: E:\World of Warcraft\Data\
    Found locale 'enGB'
    Adding data files from locale directories.
    Scanning patch levels from data directory.
    Scanning patch levels from locale directories.
    Locale: enGB
    Opening E:\World of Warcraft\Data\enGB/locale-enGB.MPQ
    Opening E:\World of Warcraft\Data\enGB/expansion-locale-enGB.MPQ
    Opening E:\World of Warcraft\Data\enGB/lichking-locale-enGB.MPQ
    Opening E:\World of Warcraft\Data\common.MPQ
    Opening E:\World of Warcraft\Data\common-2.MPQ
    Opening E:\World of Warcraft\Data\expansion.MPQ
    Opening E:\World of Warcraft\Data\lichking.MPQ
    Opening E:\World of Warcraft\Data\patch.MPQ
    Opening E:\World of Warcraft\Data\patch-2.MPQ
    Opening E:\World of Warcraft\Data\patch-3.MPQ
    Opening E:\World of Warcraft\Data\enGB/patch-enGB.MPQ
    Opening E:\World of Warcraft\Data\enGB/patch-enGB-2.MPQ
    Opening E:\World of Warcraft\Data\enGB/patch-enGB-3.MPQ
    Read LiquidType.dbc file...Done! (26 LiqTypes loaded)
    Extracting World\wmo\Dungeon\Azjol_Lowercity\Azjol_Lowercity.wmo
    Extracting World\wmo\Dungeon\IceCrown_dungeon\Icecrown_Dungeon_exteriorMicro.wmo
    Extracting World\wmo\Dungeon\IceCrownRaid\IceCrownRaid.wmo

    ...... ETC .....

TIP: Did this fail ? – See ‘Resolving Issues Section’ (Near the End)

8)      ... after a while it will change to:-

    Extract wmo complete (No (fatal) errors)

    Map – Azeroth
    Map – Kalimdor

    ...... ETC .....

9)      ... after a while it will change to:-

    Processing Map 0
    [################################################################]

    Processing Map 1
    [#################################

    ...... ETC .....

**THIS STEP IS FOR MANGOS ZERO ONLY**

10) Run 'ExtractResources.sh' and follow the onscreen prompts, you should choose the option to extract everything.

11)   Once it is complete, select the DBC, Maps and VMaps folders and move them to “C:\Mangos\data”

12)   The “Buildings” folder can be deleted.


##Compiling the MaNGOS source code
1)      Navigate to `server\win` then Double Click on the following:-
        If you use Visual Studio 2010 then you open the file `mangosdVC100.sln`
        If you use Visual Studio 2012 then you open the file `mangosdVC110.sln`
        If you use Visual Studio 2013 then you open the file `mangosdVC120.sln`

2)      Once Visual Studio has loaded, then on the build menu, then select ‘Configuration Manager’

3)      Change the ‘Active solution configuration’ to Release, then click close

4)      Once Visual Studio has loaded, then on the build menu, then select ‘Build’

5)      Then select ‘Rebuild solution’.

6)      ....This will take a while.

7)      Once complete, the following message will be shown:-

    “========== Rebuild All: 11 succeeded, 0 failed, 0 skipped ==========”

8)      Close the solution.

9)      In the folder `server\src\bindings\scripts\` open one of the following solutions:-
        If you use Visual Studio 2010 then you open the file `scriptVC100.sln`
        If you use Visual Studio 2012 then you open the file `scriptVC110.sln`
        If you use Visual Studio 2013 then you open the file `scriptVC120.sln`

10)      Once Visual Studio has loaded, then on the build menu, then select ‘Configuration Manager’

11)      Change the ‘Active solution configuration’ to Release, then clock close

12)      Once Visual Studio has loaded, then on the build menu, then select ‘Build’

13)      Then select ‘Rebuild solution’.

14)      ....This will take a while.

15)      Once complete, the following message will be shown:-

    “========== Rebuild All: 1 succeeded, 0 failed, 0 skipped ==========”

16)      Close Visual Studio.


17)      Navigate to “server\bin” and select all the files, copy them to “C:\Mangos\”

18)   Navigate to  “server\src\mangosd” and copy the file “mangosd.conf.dist.in” to “C:\Mangos\”

19)   Rename file “mangosd.conf.dist.in” as “mangosd.conf”

20)   Navigate to  “server\src\realmd” and copy the file “realmd.conf.dist.in” to “C:\Mangos\”

21)   Rename file “realmd.conf.dist.in” as “realmd.conf”

22)   Navigate to  "server\src\bindings\scripts" and copy the file "scriptdev2.conf.dist.in" "C:\Mangos\" 

23)   Rename file "scriptdev2.conf.dist.in" as "scriptdev2.conf" 

##Configuring MaNGOS
Once all the above steps have been completed, now it’s time to pull things together. This can be one of the most frustrating steps to do, but with a little patience it’s easy.

1)      Navigate to “C:\Mangos\”

2)      Open mangosd.conf with WordPad

3)      Find the following line:-

    DataDir = "."

Change this to:-

    DataDir = "C:\Mangos\Data"

 

4)      Find the following 3 lines:-

    LoginDatabaseInfo     = "127.0.0.1;3306;mangos;mangos;realmd"

    WorldDatabaseInfo     = "127.0.0.1;3306;mangos;mangos;mangos"

    CharacterDatabaseInfo = "127.0.0.1;3306;mangos;mangos;characters"

Change these to:-

The ***INFO3*** values below should be replaced by the values you recorded on page 3 for ***INFO3***

    LoginDatabaseInfo     = "127.0.0.1;3306;root;INFO3;realmd"

    WorldDatabaseInfo     = "127.0.0.1;3306;root;INFO3;mangos"

    CharacterDatabaseInfo = "127.0.0.1;3306;root;INFO3;characters"

e.g.

    LoginDatabaseInfo     = "127.0.0.1;3306;root;mangos;realmd"

    WorldDatabaseInfo     = "127.0.0.1;3306;root;mangos;mangos"

    CharacterDatabaseInfo = "127.0.0.1;3306;root;mangos;characters"

5)      Close WordPad

6)      Open realmd.conf with WordPad

7)      Find the following line:-

    LoginDatabaseInfo     = "127.0.0.1;3306;mangos;mangos;realmd"

Change this to:-

The ***INFO3*** values below should be replaced by the values you recorded on page 3 for ***INFO3***

    LoginDatabaseInfo     = "127.0.0.1;3306;root;INFO3;realmd"

e.g.

    LoginDatabaseInfo     = "127.0.0.1;3306;root;mangos;realmd"

8)      Close WordPad

9)      Open scriptdev2.conf with WordPad

10)      Find the following line:-

    ScriptDev2DatabaseInfo     = "127.0.0.1;3306;mangos;mangos;scriptdev2"

Change this to:-

The ***INFO3*** values below should be replaced by the values you recorded on page 3 for ***INFO3***

    ScriptDev2DatabaseInfo     = "127.0.0.1;3306;root;INFO3;scriptdev2"

e.g.

    ScriptDev2DatabaseInfo     = "127.0.0.1;3306;root;mangos;scriptdev2"

11)      Close WordPad

12)      Open SQLyog and connect to the databases

13)   Click on the + beside realmd

14)   Right Click on realmlist and select ‘Open Table’

15)   Click on the Name column containing ‘MaNGOS’ and change this to ‘MyWow’ then click on the save button (a blue floppy disk icon).

16)   Close SQLyog

17)   Navigate to “C:\Mangos”

18)   Double click realmd.exe and you should get the following:-

    MaNGOS/0.17.0-DEV (* * Revision 11000 - *) for Win32 (little-endian) [realm-daemon]

    <Ctrl-C> to stop.

    Using configuration file realmd.conf.
    Database: 127.0.0.1;3306;root;mangos;realmd
    MySQL client library: 5.1.49
    MySQL server ver: 5.5.8
    Added realm "MyWoW"
    realmd process priority class set to HIGH

 
19)   Double click mangosd.exe and you will notice it immediately closes.

20)   Click the ‘START’ button and type CMD followed by enter.

21)   A Command Prompt will open

22)   Type `CD C:\Mangos` then press enter

23)   Now type `Mangosd.exe` and you should get the following:-

E:\Mangos>mangosd.exe

   MaNGOS/0.17.0-DEV (* * Revision 11000 - *) for Win32 (little-endian) [world-daemon]

    <Ctrl-C> to stop.

    MM   MM         MM   MM  MMMMM   MMMM   MMMMM
    MM   MM         MM   MM MMM MMM MM  MM MMM MMM
    MMM MMM         MMM  MM MMM MMM MM  MM MMM
    MM M MM         MMMM MM MMM     MM  MM  MMM
    MM M MM  MMMMM  MM MMMM MMM     MM  MM   MMM
    MM M MM M   MMM MM  MMM MMMMMMM MM  MM    MMM
    MM   MM     MMM MM   MM MM  MMM MM  MM     MMM
    MM   MM MMMMMMM MM   MM MMM MMM MM  MM MMM MMM
    MM   MM MM  MMM MM   MM  MMMMMM  MMMM   MMMMM
            MM  MMM https://getmangos.eu
            MMMMMM

    Using configuration file mangosd.conf.
    OpenSSL 1.0.0 29 Mar 2010 (Library: OpenSSL 1.0.0 29 Mar 2010)
    Using ACE: 5.8.3
    World Database: 127.0.0.1;3306;root;mangos;mangos
    Connected to MySQL database at 127.0.0.1
    MySQL client library: 5.1.49
    MySQL server ver: 5.5.8
    AUTOCOMMIT SUCCESSFULLY SET TO 1
    SQL: SELECT required_10998_01_mangos_spell_proc_event FROM db_version LIMIT 1
    query ERROR: Unknown column 'required_10998_01_mangos_spell_proc_event' in 'field list'
    [0 ms] SQL: SELECT * FROM db_version LIMIT 1
    The table `db_version` in your [WORLD] database indicates that this database is out of date!

    [A] You have: --> `10973_01_mangos_game_event_mail.sql`
    [B] You need: --> `10998_01_mangos_spell_proc_event.sql`

    You must apply all updates after [A] to [B] to use mangos with this database.

    These updates are included in the sql/updates folder.[0 ms] SQL: SET NAMES `utf8`

    Please read the included [README] in sql/updates for instructions on updating.

    [10 ms] SQL: SET CHARACTER SET `utf8`

The Version of the Database MaNGOS expects is not the same as we have installed, so we need to update it

24)   Navigate to “C:\MangosSource\mangos\sql\updates” and leave this window open

25)   Open SQLyog and connect to the databases

26)   Click on mangos, then click into the ‘Query’ window to the right

27)   Switch back to the explorer window

28)   From the messages in Yellow above, we need to update the MaNGOS database from 10973_01 to 10998_01

These updates are shown below:-


29)   Open the first file with WordPad.

30)   Select ‘Edit’, then ‘Select All’

31)   Followed by ‘Edit’, then ‘Copy’

32)   Click back to the SQLyog, then Right click on the Query window, and select ‘Paste’

33)   Select ‘Edit’, then ‘Select All’

34)   Then Press Shift+F9 (The shortcut for Execute all queries)

35)   Repeat this for all the updates required

36)   Click back to the Command Prompt and Type “mangosd.exe”

Hopefully this will generate hundreds to messages and end up with:-

    $mangos

##Setting Up MaNGOS Users
This step is documented at the page: [**Setting Up MaNGOS Users**](Setting-Up-MaNGOS-Users)

##Starting the Game
1)      Start World of Warcraft, Use Wow.exe rather than launcher.exe

2)      The Login screen should appear, login with the username/password specified above (testuser/testuser)

3)      The Realm selection screen should appear:-

4)      Sometimes you may get asked to select a Language and Realm type, just Select English and Normal

5)      Select ‘MyWow’ and click ‘Okay’

6)      Now create a character is normal, I created a Draenei Shaman

7)      Click Enter to Enter the Realm.
 

#Resolving Issues
 

“make_vmaps.bat” fails with error ‘Could not read dir_bin file!’
 

1)      Does the batch file fail with the following message ?

    C:\World of Warcraft>vmap_assembler.exe buildings vmaps

    Could not read dir_bin file!

    exit with errors

2)      Right Click “makevmaps_SIMPLE.bat” and select Edit

3)      Change the first line from:-

    vmapExtractor.exe

To

    vmapExtractor.exe –d data

 
4)      Select ‘File’, followed by ‘Save’ – then close down the editor

5)      Now run the file “make_vmaps.bat” again