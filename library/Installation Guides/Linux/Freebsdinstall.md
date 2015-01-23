[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------

For now this guide will be nothing more than a bare bones, only what you need to do, to get mangos up and running on FreeBSD.  See one of the other, more verbose, install guides to get the details of the install.

**Important**

This was tested on FreeBSD 9.1 amd64 but it should work on earlier versions; it however does not work on the i386 version.  Even though these steps should work on older versions, I will only help troubleshoot on version 9.0 and newer.  I just don't have the time to troubleshoot older versions.  If you do run into problems following this guide, don't hesitate to shoot me a PM on the mangos forums.

## Server Setup
**Installing Prerequisites**

I'm assuming this is a fresh box you're installing on.  If not, adjust accordingly.

    portsnap fetch extract
    cd /usr/ports/databases/mysql56-server && make install clean
    cd /usr/ports/devel/git && make install clean

**Add a user for mangos to run as**

Run `adduser` and follow the prompts

**Get the source**
Logout as root and login as the user you just created.  Run the following commands to download the latest source.

    mkdir mangos
    cd mangos
    git clone --recursive http://github.com/mangosthree/server.git server
    mkdir build
    cd server
    git clone --recursive http://github.com/mangosthree/scripts.git src/bindings/scripts

**Building the server**

You need to decide where to install mangos to.  I follow the linux way of doing this because right now it is easier with how mangos works.  As I have more time I'll work up directions/scripts to help keep mangos installed in a more FreeBSD way (ie. binaries go into /usr/local/bin).  So for now I choose to install mangos to /opt/mangos so this guide will give that as an example.  If you know enough to not follow that then you should be able to tweak these instructions to suit your needs.

Log in as root and create the directory for mangos

    mkdir -p /opt/mangos
    chown user:user /opt/mangos

Replace user:user with your username that you created earlier

    cd ../build
    cmake ../server -DCMAKE_INSTALL_PREFIX=/opt/mangos -DINCLUDE_BINDINGS_DIR=scripts
    gmake
    gmake install

Make and make install may work but I have not tested this.  I use gmake since most of the development for mangos is done on linux and is getting tested against that.

## Database Setup

**All of these steps will be performed as the user you created earlier in this guide, not root**

### Set root password for mysql

**If you choose to import and create the sql as a different user you are on your own. I'm only covering the easy way.**

    mysqladmin -u root password "set_your_password"

### Create database structure

    cd ~/mangos/server/sql
    mysql -u root -p < create_mysql.sql
    mysql -u root -p characters < characters.sql
    mysql -u root -p realmd < realmd.sql

### Import the world database

    cd ~/mangos
    git clone --recursive http://github.com/mangosthree/database database
    cd database/full_db
    unzip mangosthree_db_r3.zip \#the name of this file may change from time to time
    mysql -u root -p mangos < mangosthree_db_r3.sql

##Configuration
This step is documented at the page: [**Configuration Files**](Configuration-Files)

## Start the server

**Warning!!! This will fail this time. I mean for it to.**

    cd /opt/mangos/bin
    ./mangosd

When the server fails to start it will tell you at what level your database is at and what level it needs to be.  This is ok.  We will now go to the updates directory for the server and import them.

### Import the updates

**Update naming convention. Important to understand**

version#_increment_databasename_tablename.sql

**You will need to import each update after the one the error you just received states you need.**

    cd ~/mangos/server/sql/updates
    mysql -u root -p database < update_file.sql

Replace database and update_file with the correct information.  Once all of the updates have been imported past the one listed in the error you will be ready to start the server after going through the config files.  Warning! You need to go through each update in order or they will fail.

## Starting the server for real

You may want to start the server using screen (this is what I do) or daemonize it.  Your choice.  If you choose to go the screen route just install screen `cd /usr/ports/sysutils/screen && make install clean`.  Then run screen twice and in one session start realmd and the other start mangosd.  Example follows:

    screen
    cd /opt/mangos
    ./realmd

    screen
    cd /opt/mangos
    ./mangosd

That should do it.
