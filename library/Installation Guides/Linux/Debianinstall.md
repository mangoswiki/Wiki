[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 
· Other Versions(old): [**Deutsch**](/wiki/Installation%20Guides/Linux/Debianinstall-German.md)  [**Español**](/wiki/Installation%20Guides/Linux/Debianinstall-spanish.md)

----------

This guide is for ALL Debian-based distributions.

##Intro
This guide is for those who would prefer to use the superior stability and resource management of Linux, or simply cannot use Windows for various reasons.
While the current Linux sticky guide is a great source of information, there are a few nuances it fails to mentions and the aim of this thread is to
address those. This guide will be largely similar, but will hopefully be more up to date with a few of the changes in the repositories. This guide
is written with the complete beginner in mind, and as such might state the obvious on occasion.

NOTE: If you wish to use submodules with your server, you can enable or disable them during the cmake step by adding the following before your PREFIX:
(0=disabled 1=enabled)
    
    -DBUILDTOOLS=1 - to build the Extraction Tools
    -DENABLE_LIB_SD2=1 - to Enable SD2
    -DENABLE_LIB_ELUNA=1 - to Enable Eluna
    -DSOAP=1 - to Enable SOAP
    
###1. Fetching the dependencies.
Mangos needs a small number of packages to be able to compile and run properly. Getting those is easy with a simple application of the apt package manager. Just run the following line as super user:
    
    sudo apt-get update
    sudo apt-get install cmake cmake-qt-gui git g++ gcc make libace-ssl-dev libace-dev libbz2-dev libmysql++-dev libmysqlclient-dev libssl-dev
    sudo apt-get install mysql-client mysql-common mysql-server zlib1g-dev vim autoconf libtool screen bash
    
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
This step is documented at the page: [**Cloning the Repos**](/wiki/Installation%20Guides/General/Cloning%20the%20Repos.md)

Make sure you're in the right folder and then fetch the server, database and extras.
    
    git clone --recursive https://github.com/mangoszero/server.git
    git clone --recursive https://github.com/mangoszero/database.git
    
###4. Compiling the server source
Now create the build directory in your server folder. Note that ~/ is a relative path to the current user's home directory.
    
    cd ~/server
    mkdir build
    cd build
    
Build the server, specifying where it will be installed to after compiling. This may take a few minutes. Note that "../" is a constant for the parent directory.
The PREFIX argument specifies where the server will be installed. Change it accordingly.

    cmake ../ -DCMAKE_INSTALL_PREFIX=/home/mangos/zero
	
Then we start compiling. If you have more than 1 CPU core, you can compile quicker by adding the amount of cores you want to use in the compile. You can do
this by adding -j # to the make command. ie: make -j 4
    
    make
    make install
    

###5. Extracting the game assets
This step is documented at the page: [**Extract Game Assets**](Extracting-Game-Assets)

###6. Importing the MySQL Database
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

If you would like your server to run on auto restart scripts, then you will need to copy the restart scripts from the server source.
        
	mv /home/mangos/server/src/tools/restart-scripts/*.sh /home/mangos/zero/
	
Be sure to change /home/mangos/zero with your used path and chmod +x each file. Then you will just run ./realmd and ./mangos in that directory.

You need to create your account and give it admin privileges. So if you used the auto restart scripts, you can screen back to it using:
    
	screen -x mangos
	
Then run these commands in the mangos command shell.
    
    account create "username" "password"
    account set gmlevel "username" 3
    
After you're done, you can detach from the screen using CTRL A+D
Be sure you detach from it and not exit the screen.

That's it! A functional, partially scripted private server for you to mess around with. Have fun.
If you encounter any issues with the tutorial, please join our forums and explain the problem.
