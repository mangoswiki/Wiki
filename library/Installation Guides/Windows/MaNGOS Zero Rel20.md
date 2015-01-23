[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md)

----------

##How to Setup a MaNGOS Zero Server from Scratch
 
(without using repacks)

# **PLEASE NOTE**<br /> - THIS IS ONLY FOR MANGOSZERO REL20

This document will explain how to setup a MaNGOS World of Warcraft Server on Windows from Scratch.

##Required Software

All the required software below (apart from the OS) is free software and there are various options from MS to get long evaluation versions of their Server OS’s

* **A Windows Server OS** - I normally use Windows Server 2008
* [**MySQL - Community Server**](http://dev.mysql.com/downloads/mysql/)
* [**SQLyog - Community Edition**](http://code.google.com/p/sqlyog/wiki/Downloads)
* [**Git**](http://msysgit.github.io/) 
* **World of Warcraft** - You will need the version for the expansion of your server
* **Visual Studio 2010, 2012 or 2013 (Express or otherwise)**

**Optional Software**

* [**Notepad ++**](http://notepad-plus-plus.org/download)

 
##Important Things to remember

These may sound obvious, but it amazes me how often people forget these details later

    1. Server Admin Password: INFO1=[             ] e.g. Pa55word
    2. Server IP Address:     INFO2=[  .          ] e.g. 192.168.10.20
    3. MySQL Root Password:   INFO3=[             ] e.g. mangos

##Server Installation

The following section details setting up the Server, installing an OS on it and Installing MySQL onto the server.

1)      Record the Server Admin password in the box ***INFO1*** above

##Installing the Server Applications

***MySQL***
-
1)      MySQL is the Database that MaNGOS runs on

2)       Select ‘Complete’, followed by ‘Install’ and ‘Finish’ to complete the installation

3)      Once the installation is complete, the ‘Instance Configuration Wizard’ will start

4)      Select ‘Standard Configuration’

5)      Tick ‘Include Bin Directory in Windows PATH’

6)      Enter a Root Password, store this password in the box ***INFO3*** above.

7)      Tick ‘Enable Root Access from remote machines’

8)      Continue through the screens then click ‘Execute’, followed by finish the setup

***SQLyog***
-
1)      SQLyog is a graphical front end for MySQL

2)      The install is straight forward with all the default options being fine

3)      After installation, SQLyog is started up

4)      After clicking ‘Continue’ on the nag screen, you will come to the ‘Connection’ screen

5)      Select ‘New’, set a name as ‘Mangos Server’ and click ok, then set the password to the value you recorded in ***INFO3***

6)      Then click ‘Connect’

7)      When you get to the treeview screen, then MySQL is set correctly and working.


##Data Applications

The following applications are required for getting the actual data and files required for the mangos server to run.

***Git***
-
Git is a package used by the MaNGOS team to control the source files for MaNGOS.

1)      Click through the screens of the install until this screen:-

2)      Click the option ‘Git Bash Here’ and continue on using the default values.

##Setting up the MaNGOS server Databases
1)      Open SQLyog and connect to the databases

2)      Right Click on “root@localhost” and select ‘Create Database’

3)      Type “Mangos” into the Database name field, then click “Create”

4)      Right Click on “root@localhost” and select ‘Create Database’

5)      Type “Characters” into the Database name field, then click “Create”

6)      Right Click on “root@localhost” and select ‘Create Database’

7)      Type “Realmd” into the Database name field, then click “Create”


##Downloading the MaNGOS Source Code

1)   Open ‘My Computer’ and open ‘Local Disk (C :)’

2)   Right click in an empty area and select ‘New => Folder’, name this folder “MangosSource”

3)   Right Click on “MangosSource” and select “Git Bash Here”

4)   The command prompt style window will open and wait with a prompt “$”

5)   Type: 

    git clone --recursive http://github.com/mangoszero/server.git
The **--recursive** in the above command is very important! Without it compiling will fail.

6)   .... This will take a while

**The source Code for MaNGOS is now located in the `server` folder**

##Downloading and Importing the Database Data
1)   Type: 

    git clone --recursive http://github.com/mangoszero/database.git

**.... This will take a while**

    cd server/sql
    Installer_DB.cmd

This will ask you to select the database options you want and then after asking for Server Name, Username & Password will set up the databases.

    cd ../..
    cd database/_tools
    MaNGOSdb_Installer.bat

2) You will be asked for the Server Name, Username and password for the mysql database.

The MaNGOS Databases have now been populated with data


##Extracting Game Data

1)      Click on “My computer”

2)      Navigate to the following path:

    C:\MangosSource\server\bin


3)      Copy all the files into your ‘Warcraft’ Folder (where Launcher.exe and WOW.exe are)

4) Run 'ExtractResources.sh' and follow the onscreen prompts, you should choose the option to extract everything.

5)   Once it is complete, select the DBC, Maps and VMaps folders and move them to “C:\Mangos\data”

6)   The “Buildings” folder can be deleted.


##Compiling the MaNGOS source code
1)      Navigate to `server\win` then Double Click on the following:-<br/>
        If you use Visual Studio 2010 then you open the file `BuildEverything_VC100.sln`<br/>
        If you use Visual Studio 2012 then you open the file `BuildEverything_VC110.sln`<br/>
        If you use Visual Studio 2013 then you open the file `BuildEverything_VC120.sln`<br/>

2)      Once Visual Studio has loaded, click on the build menu, then select ‘Configuration Manager’

3)      Change the ‘Active solution configuration’ to Release, then click close

4)      Once Visual Studio has loaded, then on the build menu, then select ‘Build’

5)      Then select ‘Rebuild solution’.

6)      ....This will take a while.

7)      Once complete, the following message will be shown:-

    “========== Rebuild All: 19 succeeded, 0 failed, 0 skipped ==========”

8)      Close Visual Studio.


9)      Navigate to “server\bin” and select all the files, copy them to “C:\Mangos\”


##Configuring MaNGOS

Once all the above steps have been completed, now it’s time to pull things together. This can be one of the most frustrating steps to do, but with a little patience it’s easy.

1)      Navigate to “C:\Mangos\”

2)      Open mangosd.conf with WordPad

3)      Find the following line:-

    DataDir = "."

Change this to:-

    DataDir = "C:\Mangos\Data"

 

4)      Find the following 3 lines:-

    LoginDatabaseInfo      = "127.0.0.1;3306;mangos;mangos;realmd"
    WorldDatabaseInfo      = "127.0.0.1;3306;mangos;mangos;mangos"
    ScriptDev2DatabaseInfo = "127.0.0.1;3306;mangos;mangos;mangos"
    CharacterDatabaseInfo  = "127.0.0.1;3306;mangos;mangos;characters"

Change these to:-

The ***INFO3*** values below should be replaced by the values you recorded earlier for ***INFO3***

    LoginDatabaseInfo      = "127.0.0.1;3306;root;INFO3;realmd"
    WorldDatabaseInfo      = "127.0.0.1;3306;root;INFO3;mangos"
    ScriptDev2DatabaseInfo = "127.0.0.1;3306;root;INFO3;mangos"
    CharacterDatabaseInfo  = "127.0.0.1;3306;root;INFO3;characters"

e.g.

    LoginDatabaseInfo      = "127.0.0.1;3306;root;mangos;realmd"
    WorldDatabaseInfo      = "127.0.0.1;3306;root;mangos;mangos"
    ScriptDev2DatabaseInfo = "127.0.0.1;3306;root;mangos;mangos"
    CharacterDatabaseInfo  = "127.0.0.1;3306;root;mangos;characters"

5)      Close WordPad

6)      Open realmd.conf with WordPad

7)      Find the following line:-

    LoginDatabaseInfo     = "127.0.0.1;3306;mangos;mangos;realmd"

Change this to:-

The ***INFO3*** values below should be replaced by the values you recorded earlier for ***INFO3***

    LoginDatabaseInfo     = "127.0.0.1;3306;root;INFO3;realmd"

e.g.

    LoginDatabaseInfo     = "127.0.0.1;3306;root;mangos;realmd"

8)      Close WordPad

9)      Open SQLyog and connect to the databases

10)   Click on the + beside realmd

11)   Right Click on realmlist and select ‘Open Table’

12)   Click on the Name column containing ‘MaNGOS’ and change this to ‘MyWow’ then click on the save button (a blue floppy disk icon).

13)   Close SQLyog

14)   Navigate to “C:\Mangos”

15)   Double click realmd.exe and you should get the following:-

    MaNGOS/0.20.0-DEV (* * Revision 20000 - *) for Win32 (little-endian) [realm-daemon]

    <Ctrl-C> to stop.

    Using configuration file realmd.conf.
    Database: 127.0.0.1;3306;root;mangos;realmd
    MySQL client library: 5.1.49
    MySQL server ver: 5.5.8
    Added realm "MyWoW"
    realmd process priority class set to HIGH

 
16)   Double click mangosd.exe and you will notice it immediately closes.

Hopefully this will generate hundreds of messages and end up with:-

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