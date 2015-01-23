[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 
· Other Versions: [**Deutsch**](/wiki/Installation%20Guides/Linux/Debianinstall-German.md)  [**Español**](/wiki/Installation%20Guides/Linux/Debianinstall-spanish.md)

----------

This guide is for Debian-based distributions. It can be used as a reference for other distros but you need to go the extra mile yourself. The only difference should be how you get the required packages.

##Intro
This guide is for those who would prefer to use the superior stability and resource management of Linux, or simply cannot use Windows for various reasons. While the current Linux sticky guide is a great source of information, there are a few nuances it fails to mentions and the aim of this thread is to address those. This guide will be largely similar, but will hopefully be more up to date with a few of the changes in the repositories. This guide is written with the complete beginner in mind, and as such might state the obvious on occasion.

###1. Fetching the dependencies.
Mangos needs a number of applications to be able to compile and run properly. Getting those is easy with a simple application of the apt package manager. Just run the following line as super user:

    apt-get install build-essential gcc g++ automake git-core autoconf make patch libmysql++-dev mysql-server libtool libssl-dev grep binutils zlibc libc6 libbz2-dev cmake

mysql-server will run a short and simple installation daemon of its own and ask for a root password among other things. Make sure to remember it.

If you are unable to download some of these packages, try **sudo apt-get update** to bring aptitude's repositories up to date. If it still fails after that, it is possible that one of these packages is missing for a variety of reasons. You can try **apt-cache search** *package* (note that apt-cache does not require super user privileges) and look for those packages by name.

###2. The mangos user (Optional)
You might want to create a  new user with which to run your mangos server. It is not advised to run the server (and a lot of other things) as root.

    adduser mangos

And follow the prompts. A quicker, less verbose way to do this is

    useradd mangos
    passwd mangos

This will create a new user with the name mangos and with owner privileges on /home/mangos by default. This is where I run my server, because the account is not used for anything else. If you would prefer your private server to run in another folder, make sure to give your mangos user owner privileges to that folder.

    chown /your/folder/here mangos

And when you're done setting that up, switch to the user

    su mangos


###3. Getting the Mangos source
There's a lot of mangos versions to choose from. 

This guide will use the master mangos project (Cataclysm) and if you're looking to host another xpac, simply change the github links to reflect that.

Make sure you're in the right folder and then fetch the server, database and ScriptDev2 sources. ScriptDev2 needs to be in server/src/bindings

    git clone --recursive http://github.com/mangosthree/server.git
    git clone --recursive http://github.com/mangosthree/database.git

###4. Compiling the server source

Go to your server folder, create a new directory in which to build the project, and navigate to that. Note that ~/ is a relative path to the current user's home directory. 

    cd ~/server
    mkdir build
    cd build

Build the server, specifying where it will be installed to after compiling. This can take about 5 minutes. Note that ".." is a constant for the parent directory. Doing "cmake .." in /home/mangos/server/build is the same as doing "cmake /home/mangos/server". The -DPREFIX= argument specifies where the server will be installed. Change it accordingly.

    cmake .. -DPREFIX=/home/mangos/
    or 
    cmake .. -DCMAKE_INSTALL_PREFIX=/home/mangos/
    make
    make install

###5. Extracting the game assets
This step is documented at the page: [**Extract Game Assets**](Extracting-Game-Assets)

###6. SQL batch magic
Mangos uses SQL databases to store just about a million things. It also comes with a number of batch scripts to build the required databases for you. You will be using the "mysql -u root -p" command a lot. This command essentially lets you run mysql queries from the command line. The -u parameter specifies which user to apply the query as (in this case, root), and the -p parameter is necessary if your user has a password. Keep in mind -p by itself works and you don't need to do "mysql -u root -p qwerty123" or whatever your password is!

Note that these .sql files would probably work with a gui mysql application such as phpmyadmin or navicat. 

Start with the files in server/sql. This will create the three databases Mangos uses and build the table structures.

    cd /home/mangos/server/sql
    mysql -u root -p < create_mysql.sql
    mysql -u root -p realmd < realmd.sql
    mysql -u root -p characters < characters.sql
    mysql -u root -p mangos < mangos.sql

ScriptDev2 also needs its own database.

    cd /home/mangos/server/src/bindings/scripts/sql
    mysql -u root -p < scriptdev2_create_database.sql
    mysql -u root -p scriptdev2 < scriptdev2_create_structure_mysql.sql
    mysql -u root -p scriptdev2 < scriptdev2_script_full.sql

Now you need to populate the databases. This includes quests, dialog, etc. There is a script that will compile a massive number of sql files into one big sql batch you can apply at once.

    cd /home/mangos/database
    bash make_full_db.sh
    mysql -u root -p mangos < full_db.sql

Depending on when you are reading this, the server might need a few "updates" applied to it without which the world server will refuse to run. I needed to do this with mangoszero but not mangostwo. Do this step if you get an error at runtime. 

    cd /home/mangos/server/sql/updates
    mysql -u root -p mangos < blahblahblah_mangos_whatever.sql

Repeat for every similar .sql file in the folder. Mangos might not be the appropriate database for this every time.

###7. Configuration
This step is documented at the page: [**Configuration Files**](Configuration-Files)

###8. Running the server and creating an Admin account
Your binaries will be located in the bin folder of your server's root directory. Those are mangosd realmd.

mangosd is the world server and realmd is the realm server. Typically you only need one instance of realmd running, and one mangosd instance for every realm you want in your realmlist.

If you want to run these servers using screen, use these scripts, courtesy of krampf. Make sure to chmod +x them.

    #!/bin/sh
    cd /home/mangos/bin
    screen -A -m -d -S mangosworld ./mangosd

    #!/bin/sh
    cd /home/mangos/bin
    screen -A -m -d -S mangosrealm ./realmd

Make sure to run ./mangosd normally once, because you'll need to create your account and give it admin privileges. Run these commands in the mangos command shell.

    account create "username" "password"
    account set gmlevel "username" 3

And here you go! A functional, partially scripted private server for you to mess around with. Have fun.
