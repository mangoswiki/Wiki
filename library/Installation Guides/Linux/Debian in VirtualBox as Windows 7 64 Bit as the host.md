####This how to will be on how to get MangosZero running on Debian in VirtualBox as Windows 7 64 Bit as the host

### Installing VirtualBox
This part should be self-explanatory, I may recap on certain settings like BIOS and other default settings

### Starting up Virtual box and Installing the base operating system

Create a new virtual machine, I'm going with a 64-bit install with Debian 7.2.0 ISOs. 512MB ram, create a 20GB dynamic partition.  After the new virtual machine has been set up, give the server 12MB of video ram which is more than enough to run a server.

Start the server, and select your settings as you wish.

When installing packages, only install what you need because we want this server to be as trim as possible.  No Desktop, XWindow or gui, just a straight server.

On the Software Selection screen, Unselect Everything but the standard system utilities.

Install the Grub boot loader

### Setting up Build Environment for Mangos

Login as root, we need to install a few things first.  After looking at top, I only have 58 processes total running and about 56k of RAM used.  not bad at all.  We want the OS to be as trim as possible, that is one of the goals for this article.

As root, type in:
<pre>
apt-get install sudo ssh
</pre>

After install of sudo, Add the user mangos and edit the /etc/sudoers file and add the mangos username

<pre>
adduser mangos

edit /etc/sudoers

Add under 'User Privilege Section' underneath root
mangos    ALL=(ALL:ALL) ALL

Exit and save
</pre>

Now type in exit and login as mangos username.  You should have sudo rights now.

Type in these commands to establish a build environment
<pre>
sudo apt-get install -y autoconf automake clang cmake gcc g++ libtool make patch
sudo apt-get install -y cmake-curses-gui git-core
</pre>

I had an issue with these commands not being found so I had to add the default repos in /etc/apt/sources.list

<pre>
deb http://http.debian.net/debian wheezy main
deb-src http://http.debian.net/debian wheezy main

deb http://http.debian.net/debian wheezy-updates main
deb-src http://http.debian.net/debian wheezy-updates main

deb http://security.debian.org/ wheezy/updates main
deb-src http://security.debian.org/ wheezy/updates main
</pre>

### Installing the Development headers

<pre>
sudo apt-get install apache2 cmake cmake-qt-gui git g++ libace-ssl-dev libace-dev libapache2-mod-php5 libbz2-dev libmysql++-dev libmysqlclient-dev libssl-dev libtbb-dev make mysql-client mysql-common mysql-server php5-mysql libtbb-dev libtbb2 zlib1g-dev vim libtbb-dev
</pre>

### Map Extraction

I chose the lazy way and extracted the maps in Windows 7 and then copied them to my Linux VM and it works great.

I'll work on a Debian map extraction very soon.

### Installing the Database Server (MySQL)

<pre>
sudo apt-get install -y libace-dev libbz2-dev libmysqlclient-dev libncurses5-dev libreadline-dev libssl-dev zlib1g-dev
</pre>

Set the root password for the MySQL server

### Creating and Setting Permissions for MySQL User

<pre>
mysql -u root -p

CREATE USER 'mangos'@'localhost' IDENTIFIED BY 'password';
</pre>
for Password, use whatever you want and for user mangos, use whatever you want.

<pre>
GRANT ALL PRIVILEGES ON `mangos\_%` . * TO 'mangos'@'localhost';
GRANT USAGE ON * . * TO 'mangos'@'localhost' IDENTIFIED BY 'password' WITH MAX_QUERIES_PER_HOUR 0 MAX_CONNECTIONS_PER_HOUR 0 MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0 ;
</pre>
again for username and password, use whatever you want, just ensure they match

### Creating the Mangos Databases

<pre>
mysql -u root -p

CREATE DATABASE `mZero_characters` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
CREATE DATABASE `mZero_realm` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
CREATE DATABASE `mZero_scripts` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
CREATE DATABASE `mZero_world` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
FLUSH PRIVILEGES ;
</pre>

### Downloading the Mangos-Zero Source from github and compiling

While you are in user mode and not root, create the mangos source directory
<pre>
cd ~
mkdir mangos-source
cd mangos-source
git clone --recursive https://github.com/mangoszero/server
git clone --recursive https://github.com/mangoszero/database
</pre>

Be sure to use the '''--recursive''' so git will pull in everything, without this your compile will fail

### Compiling Mangos
create the directories needed for build
<pre>
sudo mkdir -p /opt/mZero/
sudo mkdir -p /opt/mZero/logs/mangos-zero/
sudo mkdir -p /opt/mZero/share/mangos-zero/
sudo chown -R mangos:mangos mZero
</pre>

<pre>
cd server
mkdir _build
cd _build
cmake -DCMAKE_INSTALL_PREFIX=/opt/mZero -DCMAKE_BUILD_TYPE=Debug -DWITH_MOD_LUA=0 -DWITH_MOD_SCRIPTDEV2=1 ..
</pre>

Now in the ~/mangos-source/server/_build directory

<pre>
make
</pre>

After a successful compile run this.

<pre>
make install
</pre>

### Configuration of Mangos

<pre>
cd /opt/mZero/etc
cp ahbot.conf.dist ahbot.conf
cp mangosd.conf.dist mangosd.conf
cp realmd.conf.dist realmd.conf
</pre>

<pre>
nano realmd.conf
</pre>

The **LoginDatabaseInfo** Variable looks like this
<pre>
LoginDatabaseInfo      = "127.0.0.1;3306;mangos;mangos;realmd"
</pre>

Change to
<pre>
LoginDatabaseInfo      = "127.0.0.1;3306;mangos;password;mZero_realm"
</pre>


then for mangosd.conf

<pre>
nano mangosd.conf
</pre>

The lines that need to be changed are:
<pre>
LoginDatabaseInfo      = "127.0.0.1;3306;mangos;mangos;realmd"
WorldDatabaseInfo      = "127.0.0.1;3306;mangos;mangos;mangos"
CharacterDatabaseInfo      = "127.0.0.1;3306;mangos;mangos;characters"
ScriptDev2DatabaseInfo      = "127.0.0.1;3306;mangos;mangos;mangos"
</pre>

These lines should be changed to:
<pre>
LoginDatabaseInfo      = "127.0.0.1;3306;mangos;password;mZero_realm"
WorldDatabaseInfo      = "127.0.0.1;3306;mangos;password;mZero_world"
CharacterDatabaseInfo      = "127.0.0.1;3306;mangos;password;mZero_characters"
ScriptDev2DatabaseInfo      = "127.0.0.1;3306;mangos;password;mZero_scripts"
</pre>

### Inserting Database Information

<pre>
cd ~/mangos-source/database/Realm/Setup
mysql -u root -p mZero_realm < realmdLoadDB.sql
cd ~/mangos-source/database/Character/Setup
mysql -u root -p mZero_characters < characterLoadDB.sql
cd ~/mangos-source/database/World/Setup
mysql -u root -p mZero_world < mangosdLoadDB.sql
</pre>

### Inserting Table Information and Full DB

<pre>
cd ~/mangos-source/database/
nano make_full_WorldDB.sh

Change the last line to look like this:

for i in /home/mangos/mangos-source/database/World/Setup/FullDB/*.sql; do tail -n +18 $i >> full_db.sql; done

Save the file

bash make_full_WorldDB.sh
mysql -u root -p mZero_world < full_db.sql
</pre>

### Running the Server

### Realmd (Realm Server)

go to /opt/mZero/bin and run the realmd server

<pre>
cd /opt/mZero/bin
./realmd
</pre>

If after running realmd and you get an error

<pre>
cd ~/mangos-source/database/Realm/Updates/Rel20
mysql -u root -p mZero_realm < update_the_SQL_file_it_was_screaming_for.sql
</pre>

You should get realmd listening for connections at this time.

### Mangos (World Server)
go to /opt/mZero/bin and run the mangosd server

<pre>
cd /opt/mZero/bin
./mangosd
</pre>

If after running mangosd and you get an error

<pre>
cd ~/mangos-source/database/World/Updates/Rel20
mysql -u root -p mZero_world < update_the_SQL_file_it_was_screaming_for.sql
</pre>

You should get mangosd listening for connections at this time.

### Finalizing running the server

I use Screen so you'll have to install this

<pre>
sudo apt-get install screen
</pre>

Then, in the /opt/mZero/bin directory, create a file called runserver.sh

<pre>
#!/bin/sh
cd /opt/mZero/bin
screen -A -m -d -S mangosworld ./mangosd

#!/bin/sh
cd /opt/mZero/bin
screen -A -m -d -S mangosrealm ./realmd
</pre>

Save it and then chmod +x runserver.sh

### Credits

If you have any issues with this, please feel free to email me at **me@chrisfaulkner.org** or contact the **getMangos.eu** team
