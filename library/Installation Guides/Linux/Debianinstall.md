[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 
· Other Versions: [**Deutsch**](/wiki/Installation%20Guides/Linux/Debianinstall-German.md)  [**Español**](/wiki/Installation%20Guides/Linux/Debianinstall-spanish.md)

----------

This guide is for ALL Debian-based distributions.

##Intro
This guide is for those who would prefer to use the superior stability and resource management of Linux, or simply cannot use Windows for various reasons.
While the current Linux sticky guide is a great source of information, there are a few nuances it fails to mentions and the aim of this thread is to
address those. This guide will be largely similar, but will hopefully be more up to date with a few of the changes in the repositories. This guide
is written with the complete beginner in mind, and as such might state the obvious on occasion.

###1. Fetching the dependencies.
Mangos needs a small number of packages to be able to compile and run properly. Getting those is easy with a simple application of the apt package manager. Just run the following line as super user:
    sudo apt-get update
    sudo apt-get install cmake cmake-qt-gui git g++ gcc make libace-ssl-dev libace-dev libbz2-dev libmysql++-dev libmysqlclient-dev libssl-dev
    sudo apt-get install mysql-client mysql-common mysql-server zlib1g-dev vim autoconf libtool screen

mysql-server will run a short and simple installation daemon of its own and ask for a root password among other things. Make sure to remember it.

###2. The mangos user (NOT optional)
You MUST create a new user with which to run your mangos server on. It is not advised to run the server (and a lot of other things) as root.
We are going to use the username 'mangos' for an example, you can use any username you want but you will need to replace mangos with your username in all paths.
    adduser mangos

This will create a new user with the name mangos under the folder /home/mangos by default.
If you would prefer your private server to run in another folder, make sure to give your user privileges to that folder.
Example:
    chown -R mangos:mangos /path/to/folder

And when you're done setting that up, you're going to switch to the user so we can begin the install process.
    su - mangos


###3. Getting the Mangos source
There are several mangos versions to choose from.

This guide will use MaNGOS Zero(classic) as an example. If you choose to use another version, you can simply just change the cloning URL to the version you would like.
This step is documented at the page: [**Cloning the Repos**](Cloning-the-Repos)

Make sure you're in the right folder and then fetch the server, database and ScriptDev2 sources. ScriptDev2 needs to be in server/src/bindings
    git clone --recursive https://github.com/mangoszero/server.git
    git clone --recursive https://github.com/mangoszero/database.git

###4. Compiling the server source
Now create the build directory in your server folder. Note that ~/ is a relative path to the current user's home directory.
    cd ~/server
    mkdir build
    cd build

Build the server, specifying where it will be installed to after compiling. This may take a few minutes. Note that "../" is a constant for the parent directory.
The -DPREFIX= argument specifies where the server will be installed. Change it accordingly.
    cmake ../ -DPREFIX=/home/mangos/
    or 
    cmake ../ -DCMAKE_INSTALL_PREFIX=/home/mangos/
    make
    make install


###5. Extracting the game assets
This step is documented at the page: [**Extract Game Assets**](Extracting-Game-Assets)

###6. Importing the MySQL Database
First, we are going to create the databases and user for each database. Here you can familiarize yourself with mysql operations.
To enter mysql, we will need to login as root:
    mysql -u root -p

After you login there should be a mysql> prompt, here we will enter the following:
    create database realmd;
    create database mangos;
    create database characters;
    GRANT ALL PRIVILEGES ON realmd.* TO mangos@'127.0.0.1' IDENTIFIED BY 'mangos';
    GRANT ALL PRIVILEGES ON mangos.* TO mangos@'127.0.0.1' IDENTIFIED BY 'mangos';
    GRANT ALL PRIVILEGES ON characters.* TO mangos@'127.0.0.1' IDENTIFIED BY 'mangos';
    flush privileges;

When finished, just type in 'quit'. Please note there needs to be ; after each line entered for MySQL to recognize the command.

Now we can import the databases for realmd, mangos and characters. This can be done easily through mysql using the ROOT password that was setup earlier.
    mysql -u root -p realmd < /home/mangos/database/Realm/Setup/realmdCreateDB.sql
    mysql -u root -p realmd < /home/mangos/database/Realm/Setup/realmdLoadDB.sql
    mysql -u root -p characters < /home/mangos/database/Character/Setup/characterCreateDB.sql
    mysql -u root -p characters < /home/mangos/database/Character/Setup/characterLoadDB.sql
    mysql -u root -p mangos < /home/mangos/database/World/Setup/mangosdCreateDB.sql
    mysql -u root -p mangos < /home/mangos/database/World/Setup/mangosdLoadDB.sql

Let's make sure the world database is updated fully:
    cat /home/mangos/database/World/Update/(current Release)/*.sql >> /home/mangos/all.sql
    mysql -u root -p mangos < /home/mangos/all.sql

Now you need to populate the databases. This includes quests, dialog, etc. There is a script that will compile a massive number of sql files into one big sql batch you can apply at once.
    cd /home/mangos/database
    bash make_full_WorldDB.sh
    mysql -u root -p mangos < full_db.sql

###7. Configuration
This step is documented at the page: [**Configuration Files**](Configuration-Files)

###8. Running the server and creating an Admin account
Your binaries will be located in the bin folder of your server's root directory. Those are mangosd realmd.
mangosd is the world server and realmd is the realm server. Typically you only need one instance of realmd running, and one mangosd instance for every realm you want in your realmlist.

If you would lke your server to run on auto restart scripts, add the following to each individual file in your server root directory.
Make this file: mangos_check.sh
    while true; do
    cd /home/mangos/server/bin
    ./realmd
    wait
    done
Make this file: realmd_check.sh
    while true; do
    cd /home/mangos/server/bin
    ./mangos
    wait
    done
Make this file: realmd.sh
    SESSION="realmd"
    DAEMON="screen -d -m -S $SESSION /home/mangos/server/realmd_check.sh"
    screen -r $SESSION -ls -q 2>&1 >/dev/null
    echo -e ""
    echo "Realmd has been launched into the background."
    echo -e ""
    if [ $? -le 10 ]; then
    echo "Restarting $DAEMON"
    $DAEMON
    fi
    wait
Make this file: mangosd.sh
    SESSION="mangos"
    DAEMON="screen -d -m -S $SESSION /home/mangos/server/mangos_check.sh"
    screen -r $SESSION -ls -q 2>&1 >/dev/null
    echo -e ""
    echo "Mangos World has been launched into the background."
    echo -e ""
    if [ $? -le 10 ]; then
    echo "Restarting $DAEMON"
    $DAEMON
    fi
    wait

Be sure to chmod +x each file, then you will just run ./realmd and ./mangosd in your server directory.

Also make sure to run ./mangosd in server/bin/ normally once, so you can create your account and give it admin privileges.
Run these commands in the mangos command shell.
    account create "username" "password"
    account set gmlevel "username" 3


That's it! A functional, partially scripted private server for you to mess around with. Have fun.
If you encounter any issues with the tutorial, please join our forums and explain the problem.
