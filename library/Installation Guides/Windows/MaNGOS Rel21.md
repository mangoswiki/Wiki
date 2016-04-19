[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md)

----------

##How to Setup a MaNGOS Rel21 Server from Scratch
 
(without using repacks)

### **  This guide is currently a work in progress **

This document will explain how to setup a MaNGOS World of Warcraft Server on Windows from Scratch.

##Required Software

All the required software below (apart from the OS) is free software and there are various options from MS to get long evaluation versions of their Server OS’s

* **A Windows Server OS** - I normally use Windows Server 2008
* [**MySQL - Community Server**](http://dev.mysql.com/downloads/mysql/) - **Please avoid version 5.7**
* [**SQLyog - Community Edition**](http://code.google.com/p/sqlyog/wiki/Downloads)
* [**Git**](http://msysgit.github.io/) 
* **World of Warcraft** - You will need the version for the expansion of your server
* **Visual Studio 2010, 2012, 2013 or 2015 (Express or otherwise)**

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

2)       Select **‘Complete’**, followed by **‘Install’** and **‘Finish’** to complete the installation

3)      Once the installation is complete, the **‘Instance Configuration Wizard’** will start

4)      Select **‘Standard Configuration’**

5)      Tick **‘Include Bin Directory in Windows PATH’**

6)      Enter a Root Password, store this password in the box ***INFO3*** above.

7)      Tick **‘Enable Root Access from remote machines’**

8)      Continue through the screens then click **‘Execute’**, followed by finish the setup

***SQLyog***
-
1)      SQLyog is a graphical front end for MySQL

2)      The install is straight forward with all the default options being fine

3)      After installation, SQLyog is started up

4)      After clicking **‘Continue’** on the nag screen, you will come to the **‘Connection’** screen

5)      Select **‘New’**, set a name as **‘Mangos Server’** and click ok, then set the password to the value you recorded in ***INFO3***

6)      Then click **‘Connect’**

7)      When you get to the treeview screen, then MySQL is set correctly and working.


##Data Applications

The following applications are required for getting the actual data and files required for the mangos server to run.

***Git***
-
Git is a package used by the MaNGOS team to control the source files for MaNGOS.

1)      Click through the screens of the install until this screen:-

2)      Click the option ‘Git Bash Here’ and continue on using the default values.

##Downloading the MaNGOS Source Code

1)   Open **‘My Computer’** and open **‘Local Disk (C :)’** (or another drive)

2)   Right click in an empty area and select **‘New => Folder’**, name this folder `MangosSource`

3)   Right Click on `MangosSource` and select **“Git Bash Here”**

4)   Now follow the cloning guide from here:

[Cloning the Repos](/wiki/Installation%20Guides/General/Cloning%20the%20Repos.md)

**The source Code for MaNGOS is now located in the `MangosSource` folder**

##Downloading and Importing the Database Data
1)   Type: 

    git clone --recursive http://github.com/mangoszero/database.git -b develop21

**.... This will take a while**

    cd ..
    cd database
    InstallDatabases.bat


By Default the Installer will Create and Populate the Realm, Character and World databases. Will it also load a fully populated world Database, these options can be changed using the on-screen options.

Press N to move onto the next step.

2) You will be asked for the Server Name, Username and password for the mysql database, plus the names of the databases and ports for mysql.
- The defaults for all of theses are shown in brackets.

Once complete, the MaNGOS Databases will have been populated with data


##Extracting Game Data

1)      Click on **“My computer”**

2)      Navigate to the following path:

    C:\MangosSource\server\bin


3)      Copy all the files into your ‘Warcraft’ Folder (where Launcher.exe and WOW.exe are)

4) Run 'ExtractResources.sh' and follow the onscreen prompts, you should choose the option to extract everything.

5)   Once it is complete, select the DBC, Maps and VMaps folders and move them to “C:\Mangos\data”

6)   The “Buildings” folder can be deleted.


##Compiling the MaNGOS source code
1)      Navigate to `MangosSource\win` then Double Click on the following:-<br/>
        `MaNGOS_EasyBuild.exe`
        
2)      Click on **‘Check Now’**

3)      Any missing required libraries will be highlighted, click on the links to download and install then from the source.

**NOTE** Due to a restriction of MySQL, you can either install the 32Bit OR 64Bit libraries but not both. Install the version you intend to run on your server.   

4)      Once all the requisite libraries are installed, the **‘Build Options’** button will become available.

5)      From the next screen, select the required options:

**OS Version Build**      - The destination OS Build.<br/>
**Build Type**            - Whether you wish to build a Release or Debug version.<br/>
**Visual Studio Version** - If you have multiple versions of visual studio installed, you can pick the version you wish to build with.<br/>
**Server Build Options**  - Build the optional components.<br/>
**Scripting Engines**     - Choose which scripting engines to use.<br/> 

6)      Click **‘Generate Project’**, once complete visual studio will open  

7)      Click the **‘Build’** Menu, then select **‘Rebuild Solution’**

8)      Once complete, the following message will be shown:-

    “========== Rebuild All: 24 succeeded, 0 failed, 1 skipped ==========”

9)      Close Visual Studio.

10)     Navigate to the folder `MangosSource_build\bin` and select all the files, copy them to `C:\Mangos\`


##Configuring MaNGOS

Once all the above steps have been completed, now it’s time to pull things together. This can be one of the most frustrating steps to do, but with a little patience it’s easy.

1)      Navigate to `C:\Mangos\`

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

14)   Navigate to `C:\Mangos`

15)   Double click `realmd.exe` and you should get the following:-

    MaNGOS/0.21.0-DEV (* * Revision 21000 - *) for Win32 (little-endian) [realm-daemon]

    <Ctrl-C> to stop.

    Using configuration file realmd.conf.
    Database: 127.0.0.1;3306;root;mangos;realmd
    MySQL client library: 5.1.49
    MySQL server ver: 5.5.8
    Added realm "MyWoW"
    realmd process priority class set to HIGH

 
16)   Double click `mangosd.exe` and you will notice it immediately closes.

Hopefully this will generate hundreds of messages and end up with:-

    $mangos

##Setting Up MaNGOS Users
This step is documented at the page: [**Setting Up MaNGOS Users**](Setting-Up-MaNGOS-Users)

##Starting the Game
1)      Start World of Warcraft, Use `Wow.exe` rather than launcher.exe

2)      The Login screen should appear, login with the username/password specified above (testuser/testuser)

3)      The Realm selection screen should appear:-

4)      Sometimes you may get asked to select a Language and Realm type, just Select English and Normal

5)      Select ‘MyWow’ and click ‘Okay’

6)      Now create a character as normal, I created a Draenei Shaman :D

7)      Click Enter to Enter the Realm.