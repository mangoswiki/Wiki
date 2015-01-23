[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md)  

### **Required Software**

* Windows 7 or Windows 8 (32-bit or 64-bit).
* [Microsoft Visual Studio C++ (desktop edition)](http://www.visualstudio.com/downloads/download-visual-studio-vs)
* [Git](http://git-scm.com/)
* [MySql server](http://dev.mysql.com/downloads/mysql/)

##Getting MaNGOS source

Open folder, in which you want to have mangos server. I will be using C:\Users\[username]\mangos. If you installed git right, right click and on popup menu and choose "Git Bash". When the Git Bash window appears, type this command:

    git clone --recursive http://github.com/mangosthree/server.git

####ScriptDev2 ~ C++ scripts

Next we will download the scripts for the server. The target folder needs to be \src\bindings\ScriptDev2 in the mangos source folder, so I will be using C:\Users\[username]\mangos\src\bindings\ScriptDev2.

    git clone --recursive http://github.com/scriptdev2/scriptdev2-cata.git src\bindings

##Compiling Mangos

You need to create a folder that contains the server after it has been built. I will be using C:\Users\[username]\Mangos Server as the server folder. 

Go to C:\Users\[username]\mangos\win and double click mangosdVC90.sln (mangosdVC90.sln is for Visual Studio 2008 and mangosdVC100.sln is for Visual Studio 2010). You should see "Build" at the top left of the window (on VS 2010 you need to go to Tools -> Settings -> Expert settings to see the "Build" at the top of the window). Click it and select Configuration Manager. You should set Active Solution Configuration to Release and Active Solution Platform should be Win32.

>Note! Free versions of the compilers do not have 64bit and the compiling will be skipped.

Now click Build again and then select Build solution to start the compiling. 

**Do not stop the compiling even though you think it has finished.**

The process is complete when you see something like: 

    ========== Build: 11 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========

If there are none failed you are good to go. Then just shut the window.

>Note! If you had an error or are having problems with the build you can select Build->Clean Solution to "reset" the compilation. 

####Compiling ScriptDev2

We're going to do the same thing to compile ScriptDev2. 

Go to: C:\Users\[username]\mangos\src\bindings\ScriptDev2 and double click scriptVC90.sln. Now you should see "Build" at the top left of the window. Click it and select Configuration Manager. You should set Active Solution Configuration to Release and Active Solution Platform should be Win32. 

Click Build again and then select Build solution to start the compiling. 

**Do not stop the compiling even though you think it has finished.**

The process is complete when you see something like: 

    ========== Build: 11 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========

If there are none failed you are good to go. Then just shut the window.

##7. Configuration
Go to C:\Users\[username]\mangos\bin\Win32_Release and copy the files to C:\Users\[username]\Mangos Server.

This step is documented at the page: [**Configuration Files**](Configuration-Files

##DBC's, Maps, and Vmaps
####DBC and Maps

>You need to have WoW to do this and it needs to be the same version as the version that MaNGOS supports at the time you downloaded the source!

Go to C:\Users\[username]\mangos\contrib\extractor and copy ad.exe to your WoW root folder (the folder with wow.exe and Launcher.exe). Start the ad.exe and wait until it has finished. Then move the new folders: maps and dbc to C:\Users\[username]\Mangos Server.

####Vmaps

These are not necessary, but without them you do not have Line of sight (Los).

>Note! The extractor tries to detect where your wow installation is, so if you have a wow installed with a higher patch it may cause errors. Usually this is what causes Vmap extracting problems. 

>To get over the errors, we need to create a shortcut to makevmaps_SIMPLE.bat. Then right-click on the shortcut and select Properties. Inside, find the Target box, and add `-d` plus the path to your WoW install.

>"C:\Users\Public\Games\World of Warcraft\makevmaps_SIMPLE.bat" -d "C:\Users\Public\Games\World of Warcraft"

Go to C:\Users\[username]\mangos\contrib\vmap_extract_assembler_bin and copy the files to WoW/Data/xxXX/.
Run makevmaps_SIMPLE.bat and let it finish.

Then move the Vmaps folder to C:\Users\[username]\Mangos Server.
The Buildings folder is unused and can be deleted.

##Database
Characters, Logon and scripts

I will be using Xampp here.
Go to your xampp installation folder and start the mysql server and apache by clicking mysql_start.bat and apache_start.bat.

Start up HeidiSQL, create a new connection and enter the information.

*Xampp
Hostname/IP: most often Localhost or 127.0.0.1 or the address of your host.
User: root by default
Password: Usually blank
Port: The default port usually works if you are using localhost (your host port)

Then click Open.

You should create a new user that has a username and password. (blank password will error later)
Go to Tools and select User manager, then Add user and fill in the username and password. Do not forget to apply all priviledges.

Now right click root@localhost at the up left and select Create new and then Database, then fill up the name and click Ok.
Create the following databases:
characters
mangos
realmd
scriptdev2

Go to C:\Users\[username]\mangos\sql and double click realmd.sql.
Select your user and then click on realmd database so that it becomes selected (yellow).
Then Execute the file (press F9 or the "play" button up center).

Execute characters.sql from C:\Users\[username]\mangos\sql to characters database,

scriptdev2_create_structure_mysql.sql from C:\Users\[username]\mangos\src\bindings\ScriptDev2\sql to scriptdev2 database and

scriptdev2_script_full.sql from C:\Users\[username]\mangos\src\bindings\ScriptDev2\sql to scriptdev2 database.


##World database

If you want a database, then you should apply it now.
OR
If you just want an empty world, execute mangos.sql from C:\Users\[username]\mangos\sql to mangos database.


##UDB (unified database)

    I will be showing how to apply UDB database.
    Create a new folder somewhere.
    I will create a folder called UDB to C:\Users\[username]\Mangos Server.

    Right click the folder and select SVN Checkout...
    Then write this to the Url of repository:

    https://unifieddb.svn.sourceforge.net/svnroot/unifieddb/trunk/


    and click Ok.

    Now let it download. If you encounter something that stops the download in the middle,
    just right click the folder again and select SVN Update and the download should start again.
    After the download has finished you can see the revision of the database (You might need it later, but not in this guide). Just close the window by clicking Ok.

    Then go to C:\Users\[username]\Mangos Server\UDB\Full_DB and unzip UDB_0.12.1.393_mangos_10545_SD2_1833.zip.
    Go to the unzipped folder and execute UDB_0.12.1.393_mangos_10545_SD2_1833.sql to your mangos database.

    Then go to C:\Users\[username]\Mangos Server\UDB\Updates\0.12.1_additions and execute these files in this order:
    394_corepatch_mangos_10546_to_10720.sql to mangos database,
    394_updatepack_mangos.sql to mangos database,
    395_corepatch_mangos_10721_to_10892.sql to mangos database,
    395_updatepack_mangos.sql to mangos database,
    396_updatepack_mangos.sql to mangos database,
    397_corepatch_mangos_10905_to_11064.sql to mangos database,
    397_updatepack_mangos.sql to mangos database,
    398_corepatch_mangos_11065_to_11156.sql to mangos database,
    398_updatepack_mangos.sql to mangos database.
    ([Incase there are more updates] first corepatch, then updatepack and so on..)


ACID, SD2 and updates to world DB
World DB updates

Now you must apply some patches to the database to make it work with your core.
Go to your database with HeidiSQL and select mangos database.
Go to db_version table, click Data tab and check the far right column name.
It should be like: required_[color=red]10551_01</font>_mangos_spell_proc_event where 10551_01 is the core version that your database currently supports.

Go to C:\Users\[username]\mangos\sql\updates folder and execute all the .sql's in numerical order (1,2,3,4,5,6) that start with a higher number than what you have in the database (I had 11117_01, so I need to execute from 11169_01 up) TO your mangos database.
Ignore all _realmd_ and _characters_ sql's as those are for realmd and characters databases, which are already up to date.


##ACID and SD2

Now you need to make a new folder named ACID to somewhere.
I am using the default folders in the guide:
C:\Users\[username]\Mangos Server\ACID
I will also use this folder as the server folder

Right click the folder and select SVN Checkout...
Then write this to the Url of repository:

https://sd2-acid.svn.sourceforge.net/svnroot/sd2-acid/trunk/wotlk/3.0.8/


and click Ok.

Now let it download. If you encounter something that stops the download in the middle, just right click the folder again and select SVN Update and the download should start again.
After the download has finished you can see the revision of the downloaded scripts (You might need it later, but not in this guide). Just close the window by clicking Ok.

Now execute:
3.0.8_acid.sql from C:\Users\[username]\Mangos Server\ACID to your mangos database and
mangos_scriptname_full.sql from C:\Users\[username]\mangos\src\bindings\ScriptDev2\sql to your mangos database.


##Configs

Go to C:\Users\[username]\Mangos Server, backup all .confs (if something goes wrong) and open up mangosd.conf with any text editor (like notepad ect.).

Scroll down to:

LoginDatabaseInfo     = "127.0.0.1;3306;root;mangos;realmd"
WorldDatabaseInfo     = "127.0.0.1;3306;root;mangos;mangos"
CharacterDatabaseInfo = "127.0.0.1;3306;root;mangos;characters"


And change 127.0.0.1 to the host address (local is 127.0.0.1),
3306 to the port (3306 is usually local)
root to your database username
mangos to your database password

Vmaps:
Scroll down to

vmap.enableLOS = 0
vmap.enableHeight = 0


If you do have Vmaps and want to use them, change the numbers to 1
If you do not have Vmaps or do not want to use them, make sure the numbers are 0

You may also want to tweak the server XP and drop rates in this file, just scroll down.
close the file and save it.

Then open up realmd.conf, scroll down to:

LoginDatabaseInfo = "127.0.0.1;3306;root;mangos;realmd"


And change 127.0.0.1 to the host address (local is 127.0.0.1),
3306 to the port (3306 is local)
root to your database username
mangos to your database password

Close and save it.

Then open up scriptdev2.conf, scroll down to:

ScriptDev2DatabaseInfo     = "127.0.0.1;3306;root;mangos;scriptdev2"


And change 127.0.0.1 to the host address (local is 127.0.0.1),
3306 to the port (3306 is local)
root to your database username
mangos to your database password

Close and save it.


##Starting up

First ensure that your SQL server is online (xampp or mysql).

Xampp can be started by:
Going to your xampp installation folder and starting the mysql server and apache by clicking mysql_start.bat and apache_start.bat.

Go to C:\Users\[username]\Mangos Server and start up realmd.exe and mangosd.exe
Wait for the server to load all the data.

To create a new user you must write these to the mangosd.exe window:

.account create [name] [password] (this will create the account with the desired user and password)
.account set addon [name] 2 (this will allow the account to connect to the server using WOTLK expansion, 2-wotlk, 1-tbc, 0-classic)
.account set gmlevel [name] 3 (this command will make the account a gm account, 3-admin, 2-gm, 1-mod, 0-player (default))

Then log in and enjoy.
