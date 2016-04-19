[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------

This Ubuntu Install Guide is thanks to Krampf and his MaNGOS Community Article.  The following steps assume you are at a Console in your Home Directory. Tested and working on Ubuntu Server 15.04 64 bit, I assume is the same for other Debian-like systems. For different distros the main difference is in the preparation section, since you will have to track correspondents packages in other repos.

## Preparation  
The following packages are probably needed to compile and run MaNGOS-zero:  

> gcc g++ automake git-core autoconf make patch libmysql++-dev mysql-server libtool libssl-dev grep binutils zlibc libc6 libbz2-dev cmake

When mysql-server is installed a password for the root users will be requested. DON'T FORGET IT.

You will also need a WoW-client to extract map files, dbc files and some other stuff.

### Fetching Source  
Get the source code of MaNGOS and patch ScriptDev2 in.  Create a directory called mangos rather than dumping it in your home directory. Depending on the core you want to download, you should replace mangoszero (classic) to mangosone (burning crusade) or mangostwo (lich king), etc.

    mkdir mangos  
    cd mangos  
    git clone --recursive http://github.com/mangoszero/server.git 

This command will clone code from the master repo. If you are interested in most up to date code, you will have to clone branch develop21

	git clone --recursive http://github.com/mangoszero/server.git -b develop21

### Compile MaNGOS  
Compiling (with an install dir of /opt/mangos-server)  Note:  If /opt/mangos-server does not exist, create it and chown to the user you compile your code with:

    chown my_user:users /opt/mangos-server

Now lets create an object-dir and compile inside it

    mkdir obj
    cd obj
    cmake .. -DCMAKE_INSTALL_PREFIX=/opt/mangos-server
    make  
    make install  

cmake can use any of the following options, but the one in the example above is recommended. Each option must be prefixed with `-D`:
 * `CMAKE_INSTALL_PREFIX` - decides where mangos will be installed
 * `CONF_DIR` - Path to the configuration files, can be absolute or relative
 * `PCH` - if this is used precompiled headers will be used
 * `DEBUG` - build in debug mode, easier to make use of data when it crashes etc
 * `USE_STD_MALLOC` - use the `malloc` given by the std libs instead of the TBB library
 * `ACE_USE_EXTERNAL` - use external ACE library instead of the one given, use version around 6.0.3 for it
 to be compatible
 * `BUILD_TOOLS` - enabling this will build the software needed for the extraction of game assets
 * `SOAP` - enabling remote access via SOAP
 * `SCRIPT_LIB_ELUNA` - will compile with support for Eluna scripting
 * `SCRIPT_LIB_SD2` - will compile with support for ScriptDev2 scripts
On develop21 branch there are 2 more options:
 * `SCRIPT_LIB_SD3` - replacing SCRIPT_LIB_SD2
 * `PLAYERBOTS` - enable playerbotsAI, more information on this project @ https://github.com/playerbot/mangos/wiki

## Database

### Create Databases  Grabbing the database.

    cd ~/mangos  
    git clone --recursive http://github.com/mangoszero/database.git  

### Add users and create the actual database. 

Here you can either choose to create your own user, it will need the following privileges in that case: 
`SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, ALTER TABLES`

If not you'll need to go into the folder where you cloned your server:

    cd ~/mangos/server/sql

and then open the file `create_mysql.sql` in a text editor, ie:

    emacs -nw create_mysql.sql

Well there you'll need to edit the line that looks like this:

    CREATE USER 'mangos'@'localhost' IDENTIFIED BY 'mangos';

Change the last mangos to a more secure password as this is what we mangosd will be connecting with to the 
database, an example:

    CREATE USER 'mangos'@'localhost' IDENTIFIED BY 'MYUBERpASssWORD';

**Remember this password, it will be used in the config file later**

With this change done we can save the file, close it and import it into mysql. It will now create three 
databases: mangos, characters, realmd. If you want to have multiple installations (ie, different cores) 
you will have to edit the `create_mysql.sql` to create different tables. To import it into mysql we run:

    mysql -u root -p < create_mysql.sql

A prompt will come up asking for you password, just type it in and hit enter. Once this is done we need to 
import the structures into each of the three databases, this we will do like so:

    mysql -u root -p mangos < mangos.sql
    mysql -u root -p characters < characters.sql
    mysql -u root -p realmd < realmd.sql

ScriptDev2 also needs its own database if you're including that in your server.

    mysql -u root -p < scriptdev2_create_database.sql
    mysql -u root -p scriptdev2 < scriptdev2_create_structure_mysql.sql
    mysql -u root -p scriptdev2 < scriptdev2_script_full.sql

After this we will need to fill the mangos database with some real data, ie mobs and all that nice stuff.
For that we'll need our database repo:

    cd ~/mangos/
    git clone --recursive http://github.com:mangoszero/database
    cd database/_tools
    ./make_full_db.sh

If you get a 'permission denied' error when running make_full_db.sh, make sure the executable bit is set on the file:

    chmod u+x make_full_db.sh

or explicitly run the file contents

    bash make_full_db.sh

The script will create a file name full_db.sql which we will import to our database with the same command as earlier:

    mysql -u root -p mangos < full_db.sql

And we're set!

### Setup realmd database to accept connections from others than localhost
To let other players than the same computer that you are running the realmd/mangosd on you need to change a row in the `realmd` database, this can be done this way (connect to mysql using: `mysql -u USER -p`:

    use realmd;
    update realmlist set address = 'your local/external ip' where id = 1;

An example of how it would look with a real address:

    use realmd;
    update realmlist set address = '192.168.1.10' where id = 1;

This will change the first realm that you have to listen for connections on more than just **localhost**, if you're on a LAN and want to play with your friends this should be changed to the local ip of the computer that is running the server, this can be acquired by running `ifconfig` or `ip addr` depending on your distro. On the other hand, if you want your friends around the globe to connect you would have to open some ports and set the address to your external ip which can be found by for example going to http://whatismyip.com

## Extracting data from the client
This step is documented at the page: [**Extract Game Assets**](Extracting-Game-Assets)

## Configuration Files
This step is documented at the page: [**Configuration Files**](Configuration-Files)

## Updating  
To update source code and database. This is not needed if you are installing for the first time. This is what you do if you are updating an existing server to have the latest changes in the git repository.

    cd ~/mangos/server  
    git pull  
    cd src/bindings/ScriptDev2  
    git pull  
    cd ~/mangos/database  
    git pull  

After pulling the most recent code from git, you will need to compile the source code again as described in the 'Compile MaNGOS' section and restart mangosd and realmd before the changes will be reflected in your server.

### Starting mangosd and realmd  
This example requires additional editing to allow running the server using screen.  Create the following two files and make them +x  `chmod +x {filename}` and place them in /usr/local/bin

mangos-world:

    \#!/bin/sh  
    cd /opt/mangos-server/bin  
    screen -A -m -d -S mangosworld ./mangosd  

mangos-realm:

    \#!/bin/sh  
    cd /opt/mangos-server/bin  
    screen -A -m -d -S mangosrealm ./realmd  
