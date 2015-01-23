[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------
This Ubuntu Install Guide is thanks to Krampf and his MaNGOS Community Article.  The following steps assume you are at a Console in your Home Directory.  The Following Code blocks can be pasted directly into the Console.

Note that if retrieving an expansion-specific repository (at least as of 2013), the urls need to be http://github.com/mangoszero/, http://github.com/mangosone/, http://github.com/mangostwo/, etc, not http://github.com/mangos/ as listed in the instructions below.

### Preparation  
Installing necessary packages to compile and run MaNGOS:  

> sudo apt-get install build-essential gcc g++ automake git-core autoconf make patch libmysql++-dev \  
mysql-server libtool libssl-dev grep binutils zlibc libc6 libbz2-dev cmake

### Fetching Source  
Get the source code of MaNGOS and patch ScriptDev2 in.  Create a directory called mangos rather than dumping it in your home directory:

> mkdir mangos  
cd mangos  
git clone --recursive http://github.com/mangosthree/server.git  
cd server  
git clone --recursive http://github.com/mangosthree/scripts.git src/bindings/scripts  
git apply src/bindings/scripts/patches/MaNGOS-*-ScriptDev2.patch

If you receive an error while applying the patch, just open `src/bindings/CMakeList.txt` with `nano` (or any other text editor) and comment out the line `add_subdirectory(universal)` and uncomment/add the line `add_subdirectory(scripts)`.

### Compile MaNGOS  
Compiling (with an install dir of /opt/mangos-server)  Note:  If /opt/mangos-server does not exist, create it and chown to the user you compile your code with

> mkdir objdir  
cd objdir  
cmake .. -DCMAKE_INSTALL_PREFIX=/opt/mangos-server  
make  
make install  

In older versions of cmake, you might have to use `DPREFIX` instead of `DCMAKE_INSTALL_PREFIX`.

### Extract Game Assets
This step is documented at the page: [**Extract Game Assets**](Extracting-Game-Assets)

### Create Databases  Grabbing the database.

> cd ~/mangos  
git clone --recursive http://github.com/mangosthree/database.git  

### Updating  
To update source code and database

> cd ~/mangos/server  
git pull  
cd src/bindings/ScriptDev2  
git pull  
cd ~/mangos/database  
git pull  

### Starting mangosd and realmd  
mangosd and realmd can be started from the terminal from the /opt/mangos-server/bin directory by typing

    ./realmd  

and

    ./mangosd  

You'll have to run these in separate terminals, since once you start one process, you won't be able to run additional shell commands until that process ends, and you want both processes running at the same time. Once you can manually start realmd and mangosd from the terminal without any errors (mysql connection problems, missing data problems, database out of date problems), you will probably want to set up scripts to start your servers more elegantly. The 'screen' command is an excellent tool that will allow your servers to run persistently in the background even when the terminal from which they are started gets closed.
This example requires additional editing to allow running the server using screen.  Create the following two files and make them +x  (chmod +x {filename}) and place them in /usr/local/bin. These two script files will start two detached screen windows, one named 'mangosworld' that runs /opt/mangos-server/bin/mangosd and another 'mangosrealm' that runs /opt/mangos-server/bin/realmd. They will run behind the scenes, very much like a background job, and can be viewed through any terminal when you so desire.

mangos-world:

> \#!/bin/sh  
cd /opt/mangos-server/bin  
screen -A -m -d -S mangosworld ./mangosd  

mangos-realm:

> \#!/bin/sh  
cd /opt/mangos-server/bin  
screen -A -m -d -S mangosrealm ./realmd  
