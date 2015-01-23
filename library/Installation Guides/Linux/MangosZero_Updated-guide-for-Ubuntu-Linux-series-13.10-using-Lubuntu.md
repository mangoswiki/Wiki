[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------

## Linux Mangos Installation Guide
This guide should work well for any of the Ubuntu Linux flavors. Further testing will come later but I choose Lubuntu 13.10 based upon its lightweight GUI and wide Ubuntu base support. Debian users may find this guide works fine with only a few small adjustments.


If you come from a Microsoft Windows background, it is incredibly easy to install any Ubuntu Linux onto a flash drive and boot the PC (or Mac and possibly Arm mini PCs!) into Linux. From there, you can decide whether or not the OS will meet your server needs. Most servers around the world run Linux or something very similar.


I choose Lubuntu 13.10 for the following reasons:

* Very lightweight GUI
* Updated GCC compiler
* Updated hardware support
* Fast repositories allowing downloads to finish quickly
* Part of the Ubuntu family allowing the server to have widest support

## This guide uses the following configuration
Remember to replace user with your Linux login name. If your Linux username is jennifer, your mangoscode would be in /home/jennifer/mangoscode.

**All sources:** /home/user/mangoscode

**Database with mangosdb.sh installer:** /home/user/mangoscode/database

**Extract event database:** /home/user/mangoscode/EventAI

**Mangos server code:** /home/user/mangoscode/server

**Mangos base SQL files to create structure:** /home/user/mangoscode/server/sql

**Build directory that you will create using mkdir:** /home/user/mangoscode/build

**Mangos binaries requiring sudo and chown to access:** /home/mangosserver

**Two binaries and the vmaps, maps, mmaps, Buildings and dbc go here:** /home/mangosserver/bin

**Two files here, mangosd.conf, realmd.conf:** /home/mangosserver/etc

## Adding all of the necessary apps, libraries and dependency files with one command
The Ubuntu family of Linux distros have repositories where the official software downloads from, very similar to what we see on Android and Iphones. In fact, your phone devs may have gotten the idea first from the Linux community. Your Android phone is, in fact, a form of Linux!

Copy and paste the following command:

`sudo apt-get install apache2 cmake cmake-qt-gui git g++ libace-ssl-dev libace-dev libapache2-mod-php5 libbz2-dev libmysql++-dev libmysqlclient-dev libssl-dev libtbb-dev make mysql-client mysql-common mysql-server php5-mysql libtbb-dev libtbb2 zlib1g-dev vim libtbb-dev`

You will be asked to provide a Mysql password. Make sure you use one that you will remember! That same password is used later in this guide to configure the mangosd.conf and realmd.conf along with the database installation script that I wrote for Mangos!

**NOTE:** If an error is returned that a file can not be found, do not worry! Use the following command to search for the proper file name and then edit the above command: `apt-cache search <filename>`


Using Git to download, or clone, the Mangos source code
First, decide where your Mangos server source code will clone to and compile from. The most obvious choice may be /home/user/source. The user is your user name that you used during the installation. Old school Linux users may use /usr/src/ but I would argue that you will want to have easy access through your home directory and user folder.


To clone, or rather download, the Mangos source code, use the following commands:

`git clone --recursive http://github.com/mangoszero/server.git`

`git clone --recursive http://github.com/mangoszero/database.git`

As long as everything downloaded cleanly with no errors, proceed with the following commands:

 `cd ../..`

 `mkdir build` 

 `cd build` 


## Using Cmake or Cmake GUI to configure the compiling options
You can configure the compiler options using Cmake GUI if you prefer the easy of point and click. This method is very easy and allows users to see all of the options and add more of their own, which I will discuss in this guide. However, I will show the command line interface (CLI) method as well. Please do not use both methods!


## Using Cmake GUI (Skip this section if you use CLI Cmake!)
Click on the Ubuntu app menu and go to Development. This folder should show the Cmake tool with a triangle icon. Open that app. 

Fill in the following Cmake GUI windows:

**Where is the source code:** \<browse to where the Mangos source code is\>

**Where to build the binary:** \<browse to where the Mangos build directory is that we created\>

Below, select Advanced to see more options. Then click the following from the lower window:

**ACE_USE_EXTERNAL:** \<Ubuntu 13.10 all use a very recent version of ACE. Check this\>

**CMAKE_BUILD_TYPE:** \<Add into this field the word Release. Debug is for devs!\>

**CMAKE_INSTALL_PREFIX:** \<Very important! This is where your server binaries will install to!\>

**NOTE:** The default CMAKE_INSTALL_PREFIX is /opt/mangos. I used /home/mangosserver but to install anywhere outside of /opt or /home/<user> will require root access during the make install step!

Now, you are done with that unless you want to add some advanced optimizations! As with all of Linux, there are many options to make your server faster based on the specific hardware optimizations and options provided by the Linux devs.

Look under the many options for the following options:

CMAKE_CXX_FLAGS:

CMAKE_C_FLAGS:

GCC recognizes just about any CPU core that you could imagine and it does very well with optimizing the code for them all so it benefits you to use that to your advantage. The best optimization option that you could use for CMAKE_CXX_FLAGS and CMAKE_C_FLAGS may be: -O3 -march=native

Take a moment and type the following into the CLI window:

 `cc -march=native -E -v - </dev/null 2>&1 | grep cc1`

On my AMD 6-Core Zambezi, this is what GCC returned:

/usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -E -quiet -v -imultiarch x86_64-linux-gnu - -march=bdver1 -mcx16 -msahf -mno-movbe -maes -mpclmul -mpopcnt -mabm -mlwp -mno-fma -mfma4 -mxop -mno-bmi -mno-bmi2 -mno-tbm -mavx -mno-avx2 -msse4.2 -msse4.1 -mlzcnt -mno-rtm -mno-hle -mno-rdrnd -mno-f16c -mno-fsgsbase -mno-rdseed -mprfchw -mno-adx -mfxsr -mxsave -mno-xsaveopt --param l1-cache-size=16 --param l1-cache-line-size=64 --param l2-cache-size=2048 -mtune=bdver1 -fstack-protector -Wformat -Wformat-security 

On my Intel Atom netbook, which is what runs my Mangos server, it returns:

/usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -E -quiet -v -imultiarch x86_64-linux-gnu - -march=atom -mcx16 -msahf -mmovbe -mno-aes -mno-pclmul -mno-popcnt -mno-abm -mno-lwp -mno-fma -mno-fma4 -mno-xop -mno-bmi -mno-bmi2 -mno-tbm -mno-avx -mno-avx2 -mno-sse4.2 -mno-sse4.1 -mno-lzcnt -mno-rtm -mno-hle -mno-rdrnd -mno-f16c -mno-fsgsbase -mno-rdseed -mno-prfchw -mno-adx -mfxsr -mno-xsave -mno-xsaveopt --param l1-cache-size=24 --param l1-cache-line-size=64 --param l2-cache-size=512 -mtune=atom -fstack-protector -Wformat -Wformat-security


Many of these GCC switches are used on other CPU cores but bdver1 is specific to my family of AMD processors. So GCC is ready to produce very specific optimizations for my CPU but that means the binary won't run well on an Intel. This awesome feature allows you to compile the source specifically for your system and run it better.

By default, Mangos compiles with -O2 (Cap o, not zero!). There are -O1, -O2 and -O3 with -O3 being the most optimal settings that produces the quickest possible binary. So again, type setting CMAKE_CXX_FLAGS and CMAKE_C_FLAGS in the Cmake GUI to -O3 -march=native


## Using the Command Line Interface (CLI) Cmake
If you simply want to cut and paste without having to fool around with a pesky GUI, that is alright too and here are the details.

You should already be in the /server/build/ directory. Use the following command to configure the Cmake options file (CMakeLists.txt and CMakeCache.txt):

 `cmake .. -DCMAKE_INSTALL_PREFIX=/home/mangosserver -DTBB_USE_EXTERNAL=1 -DACE_USE_EXTERNAL=1 -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_FLAGS="-O3 -march=native" -DCMAKE_C_FLAGS="-O3 -march=native" -DINCLUDE_BINDINGS_DIR=ScriptDev2 -DDEBUG=0 -DTBB_USE_EXTERNAL=1`

Briefly, I will explain some of these options so that you can tailor your build to however it meets your needs best.

*  -DCMAKE_INSTALL_PREFIX, `this is where your server binaries will be installed to. The default is /opt/mangos but you may want these to go somewhere else. I prefer to have them under /home/mangosserver but remember that installing outside of your /home/<user> directory means you will need Super User access for the `make install command.
*  -DACE_USE_EXTERNAL=1, Since Ubuntu uses really new files and the repositories are very fast for updates, I used 1 here but you could use 0 to compile your own. Especially good if you used the GCC optimizations but it may also increase the chances of an error. 
*  -DTBB_USE_EXTERNAL=1, parallelism library for C++, which we add through the Ubuntu repositories. We will use the one that Ubuntu provides. Like ACE, we can save time and have fewer errors by using the updated one that Ubuntu provides.
*  -DCMAKE_BUILD_TYPE, We use Release here. There is an option to create a Debug binary that will add debug features and more overhead. We do not want more overhead on our server!
*  -DCMAKE_CXX_FLAGS and -DCMAKE_C_FLAGS, These you use the same optimization options. I have suggested using -O3 -march=native.
*  -DDEBUG=0, This is probably not used anymore and should be removed from this guide after testing!

## Building the source code
This could take a long time depending on your system so after copying and pasting the following command, you may want to go make a sandwich. 

 make -j\`getconf _NPROCESSORS_ONLN\`

**WARNING: **If you are using a laptop as your server or any PC that is prone to over-heating, this command will be a problem! The -j option tells the compiler to use more than one core. The `getconf _NPROCESSORS_ONLN` tells -j to use all of the detected cores, which will make your PC work very hard. My laptop would shut down from heat under this command but my netbook and main PC are fine. Be aware and be prepared otherwise!

If you have an error, any Ubuntu Linux will allow quick resolution. You can copy and paste the error to Google and see who solved that problem already or look for a possible clue in the CLI window as to what dependancy is missing. You can use apt-cache search, for example, to find libraries that may be missing and satisfy the compiling process.

Finally, after everything is done and you had no errors, use the following command to install the binaries into the directory you used in -DCMAKE_INSTALL_PREFIX.

 `make install`

**NOTE:** An error can occur if you do not have file permission to the destination directory. You can install using sudo make install. Furthermore, you can change the user permissions of the destination folder and all of its files by using `sudo chown user:user /<destination directory>/**`

So if you receive an error about directory permissions, use:

 `sudo make install`

## Adding the 4 Mangos databases and using Mysql
Mangos uses the Mysql database server software for all of the databases. It is fast and efficient with wide support. Although you installed the Mysql software, there is a chance that it is not running. To verify that it is running on the system at this time, use:

 `service mysqld status`

Now enter your Mysql database password that you choose at the start of this guide when you ran the first apt-get install command! Another command to use to verify our Mysql is running:

`ps -A | grep mysql` 

If for some reason it is not running, use the following command to start Mysql:

`sudo /etc/init.d/mysql start`


Change directory to your Mangos source. We will go to where the sql files are located.

`cd /home/<mangos source code>/server/sql`

Although many Mangos guides tell users to use create_mysql.sql, I always have an error. So instead, I simply login to the Mysql server CLI and paste the commands there. It is very simple!

 `mysql -u root -h localhost -p` 

Type your Mysql password and you have entered the Mysql console where commands can be issued directly to the Mysql interface. Use the following commands to create the databases needed by Mangos. Notice that each command is ends with a semicolon (;)!

 `CREATE DATABASE `mangos` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci; `
 `CREATE DATABASE `characters` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci; `
 `CREATE DATABASE `realmd` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;`
 `CREATE DATABASE `scriptdev2` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;`

 After each command, Mysql should return: Query OK, 1 row affected (0.00 sec) 

You can verify the creation of the databases by using this command: `show databases;`
Now type exit to leave the Mysql console.

To fill the datebases with the base structures, use these commands from the /<mangos source>/sql/ directory, entering your Mysql password each time.

 `mysql -u root -h localhost -p realmd < realmd.sql `
 `mysql -u root -h localhost -p characters < characters.sql `
 `mysql -u root -h localhost -p mangos < mangos.sql`

The scriptdev2.conf.dist.in must be copied to your Mangos binary etc directory. 

`cp scriptdev2.conf.dist.in /<whatever you put for -DCMAKE_INSTALL_PREFIX>/etc/scriptdev2.conf`


Finally, the last database involves filling up the world and adding the necessary updates!

`cd /home/`<mangos source code>/`database`

You will be using the install_linux.sh tool or the one that I wrote called mangosdb.sh. My tool may not yet be available in the github but you can find it easily on the forums! Both of these tools requires you to edit them and add your specific Mysql username and password. Use vim install_linux.sh to edit, or use your favorite Linux CLI text editor, so that your variables match your system. That is, your Mysql username and password. 

First, make the install_linux.sh or mangosdb.sh file executable.

 `chmod +x install_linux.sh`
 Now, execute the script: `./install_linux.sh`

If all goes well, all of the world database items will fill up the mangosd database! However, you may need to add more files from the /home/`<mangos source code>/`sql/updates directory! You find that out when you first run the mangos server.

## Editing the mangosd.conf, realmd.conf and scriptdev2.conf files
Before the last step of running the server and determining which updates to add, the mangosd.conf, realmd.conf and scriptdev2.conf files must be edited to match your system and use the options of your choosing. These files are located in the directory that you choose under the -DCMAKE_INSTALL_PREFIX option in a subdirectory called etc.

In each file, look for:

`LoginDatabaseInfo = "127.0.0.1;3306;mangos;mangos;realmd"`

Edit these to look like:

`LoginDatabaseInfo = "127.0.0.1;3306;<mysql username>;<mysql password>;realmd"`

## Running the server and checking for updates
 `Change directory to the mangos server binaries under <mangos binaries>/bin and first type:`
 `./realmd &`
 `./mangosd`

 You may have an error similar to this:
<pre>
[A] You have: --> 12738_01_mangos_spell_template.sql

[B] You need: --> 12752_01_mangos_reputation_spillover_template.sql
</pre>

Simply go back to your source directory where the sql file updates are located:

`cd /<mangos source files>/sql/updates`

My mangosdb.sh tool allows you to copy the specific updates to its update directory or you can simply use the following commands to update each file:

`mysql -u root -h localhost -p mangos < 12741_01_mangos.sql `

`mysql -u root -h localhost -p mangos < 12751_01_mangos_phase.sql `

`mysql -u root -h localhost -p mangos < 12752_01_mangos_reputation_spillover_template.sql `

Notice, the error said we need 12752_01_mangos*? But we have 11785_01_mangos*, so that means we need to add every update from 11785_01_mangos on up to 12752_01_mangos*.

To see if your Mangosd and Realmd servers are running, use:
`ps -A | grep mangos;ps -A | grep realm`

## Edit your WoW client realm.wtf reflecting your server IP
After this, your server should run without errors and the only thing you need to do is edit your WoW client's realms.wtf to point to your server IP address and you are good to go!

set realmlist 192.168.0.110:8085
set patchlist localhost

**NOTE:** Mangostwo is on port 8084. Check your WorldServerPort in mangosd.conf

**WARNING:** You will not be able to connect to your Mangos server from any other computer unless you modify the realmlist IP address! This will be an easy fix. Simply log into your Mysql, as we did in other parts of this guide, and perform the following commands.

To log into Mysql and the realmd database specifically, use:
`mysql -u root -h localhost -p realmd`
`Enter password: `

Now, paste this one command but replace 192.168.0.100 with your Mangos server's LAN address. Not 0.0.0.0 or 127.0.0.1! This is the address where people connect from the outside world.

UPDATE `realmd`.`realmlist` SET `address`='192.168.0.100' WHERE `id`='1';

The output that you will see looks something like this:
`mysql> UPDATE `realmd\`.\`realmlist\` SET \`address\`='192.168.0.110\' WHERE \`id\`='1'; `

`Query OK, 1 row affected (0.00 sec)`
`Rows matched: 1  Changed: 1  Warnings: 0`



Now type exit and you are good to go. Make sure you change 192.168.0.100 to your server's LAN IP address!
