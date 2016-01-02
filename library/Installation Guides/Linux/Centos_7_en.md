[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------

#Compiling and Installing on Centos 7

First off I made a Tutorial for Debian based distros specifically Ubuntu located [here](http://ubuntuforums.org/showthread.php?t=1964479). This guide is actually pretty old and with the new updates to the servers I thought it was time to re build my Tutorial. Now I can hear you saying "But the thread title says Centos 7", and indeed you would be correct. For this particular guide I will be using a Red Hat Variation namely CentOS. Before we get started lets run through the basics:

This guide I will be assuming you have the OS pre-installed and ready for the picking.

###PREREQUISITES
As a prerequisite you should understand the following:
+ Knowledge of BASH a Plus however not required
+ Knowledge of command line text editors (I will use nano in this guide however you are more then welcome to use vi or even vim) Debian users that are used to "pico" should probably use nano as its practically the same
+ Users should also be fairly familiar with the Yellowdog Updater, Modified (yum package manager)
+ Users should be knowledgeable with rudimentary git functionality we will need this for cloning repos
+ Usage of Putty is a bonus however if your doing this on the box its self you may not need these tools.
+ WinSCP or another similar piece of software for file transfer of data files to the server.

###PORTS
Because this is a Red Hat derivative firewalls are more prominently installed from the get-go I will give a list of ports that you will need in order to use the system as this is an EAQ (Excessively Asked Question)
+ 22 SSH - Remote Shell (Operating System not Mangos Console)
+ 8085 mangos - client to world connection
+ 3724 realmd - client to Authentication Server
+ 7878 SOAP - (OPTIONAL) Soap interface
+ 3443 Remote Access (OPTIONAL) - Remote Console Access (using PUTTY this needs a RAW connection)
+ 80 HTTP - (OPTIONAL) if you decide to use the GM Commands Script provided or if you have a web-page you want on your server
+ 3306 MySQL - (OPTIONAL) if you want to manage your MySQL or MariaDB with a remote host or you are setting up 2 servers

###PRE-INSTALLATION NOTES
Some things to keep in mind as we walk through the installation:
+ CentOS 7 X64
+ Default user on CentOS 7 is root, you may create a new user with out root privileges however for all the installs you will need root privileges. As I will be using root I will mark the areas you need to run commands with sudo for clarification.
+ I will be using the MASTER branch when I git clone if you would like to specifically choose the branch to clone I would suggest reading a bit of documentation about choosing branches on github before we get started.
+ I will be using MariaDB 10.0 as a replacement for MySQL


###PREINSTALL
Set up a YUM Repo to use the MariaDB official repositories

    # sudo if not root
    nano /etc/yum.repos.d/MariaDB.repo

Now in our newly created repo file we will set the following options

    # MariaDB 10.0 CentOS repository list - created 2015-01-19 02:15 UTC
    # http://mariadb.org/mariadb/repositories/
    [mariadb]
    name = MariaDB
    baseurl = http://yum.mariadb.org/10.0/centos7-amd64
    gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
    gpgcheck=1

Once we add the MariaDB repo lets also add the Repository for the ACE installs

    nano /etc/yum.repos.d/ace_micro.repo

and in this file we will add the following:

    [devel_libraries_ACE_micro]
    name=Latest ACE micro release (CentOS_7)
    type=rpm-md
    baseurl=http://download.opensuse.org/repositories/devel:/libraries:/ACE:/micro/CentOS_7/
    gpgcheck=1
    gpgkey=http://download.opensuse.org/repositories/devel:/libraries:/ACE:/micro/CentOS_7/repodata/repomd.xml.key
    enabled=1

After the files are in place, install MariaDB and ACE with:

    # sudo if not root
    yum install MariaDB-server MariaDB-client ace-6.3.1

You will be prompted to accept the GPG key after the packages have been downloaded.
Depending on your internet speed this next step might be a good time to get a cup of coffee during the creation of this tutorial I had about 7 hundred packages to install as well as updates. Once all of that is installed we can move on to the rest of the development tools and libraries with the command:

    # sudo if not root
    yum groupinstall "Development Tools" "Additional Development"

The above group installs might be a bit overkill for installing libraries and dependencies how ever it ensures all necessary libraries are installed.
At this point you should have a clean working environment ready to go. Now we can start to pull down the MaNGOS sources and set up our build environment.

###BUILDING MANGOS
At this time lets create our base directory tree from my home directory I'm going to create a SOURCES directory in which I will run all my git clones it is in this base directory where I keep all of my code.
I'm going to create all of these directories in order to keep all of my repositories organized in a somewhat orderly fashion.

    mkdir SOURCES
    cd SOURCES
    git clone https://github.com/mangosthree/server.git
    git clone https://github.com/mangosthree/database.git

Now you should have both the database and the server code ready to go however we need to add the scripts library in order to have that compile with our our core

    git clone https://github.com/mangosthree/scripts.git server/src/bindings/scripts

Now you will note I am placing the scripts into the `server/src/bindings/scripts` directory this is rather important as we will be setting this as one of our compile options later on. Its important to note here that this is a step that can be hard to understand for a first timer but we wont get into depth in this tutorial about it.
Once all of our downloads are done we can create a few more directories and kick off the compile.

    mkdir _build && cd _build

and here is the huge command of the day:

    cmake .. -DTBB_USE_EXTERNAL=1 -DCMAKE_BUILD_TYPE=release -DACE_USE_EXTERNAL=0 -DCMAKE_INSTALL_PREFIX=/opt/mangos -DINCLUDE_BINDINGS_DIR=scripts -DPCH=0 -DCMAKE_CXX_FLAGS="-O3 -march=native" -DCMAKE_C_FLAGS="-O3 -march=native"

Now at first this one line looks pretty scary, but lets take a closer look and break it down to understand what we're doing here

+ -DTBB_USE_EXTERNAL=1 this will instruct the compiler to locate and use the External TBB sources (should have been installed with the "Additional Development" group)
+ -DCMAKE_BUILD_TYPE=release for debugging purposes you may change this to debug
+ -DACE_USE_EXTERNAL=0 remember that ACE package we installed earlier? Yes this is where the compiler is told to use that If we wanted to install MaNGOS with an EXTERNAL ace package we would need to download the source tar-ball and compile ACE along side of mangos
+ -DCMAKE_INSTALL_PREFIX=/opt/mangos this is our installation directory feel free to change this to any location you want however I prefer to have it here as this is the "optional software directory"
+ -DINCLUDE_BINDINGS_DIR=scripts this is the scripts directory that we cloned before you must have the cloned directory inside of the src/bindings directory
+ -DPCH=0 Pre-compiled headers option (tends to speed compile up however I don't think pre-compiled headers ship with mangos if any one would like to clarify on that id be happy to add the information)

I found these next two off another wiki page for architecture optimization options essentially it stream-lines the code for your hardware

+ -DCMAKE_CXX_FLAGS="-O3 -march=native"
+ -DCMAKE_C_FLAGS="-O3 -march=native"

Now you should have a fully configured source directory and some output should appear on your terminal, as an example this is what mine looked like:

    -- Detected 64-bit platform.
    -- Using mysql-config: /usr/bin/mysql_config
    -- Found MySQL library: /usr/lib64/libmysqlclient_r.so
    -- Found MySQL headers: /usr/include/mysql
    -- Found OpenSSL: /usr/lib64/libssl.so;/usr/lib64/libcrypto.so (found version "1.0.1e")
    -- Found ZLIB: /usr/lib64/libz.so (found version "1.2.7")
    -- MaNGOS-Core revision  : a681260670a3afee4f7e986a4de6dcbb7308ec81
    -- Install server to     : /opt/mangos
    -- Build script library  : Yes (using scripts)
    -- Use PCH               : No
    -- Using Linux port
    -- Configuring done
    -- Generating done
    -- Build files have been written to: /root/SOURCES/server/_build

At this point we can safely run our make and then proceed to install our packages

    make -j`getconf _NPROCESSORS_ONLN`

The option `getconf _NPROCESSORS_ONLN` instructs the server to get the number of online CPUs and returns that value to the compiler (make). Some system comparisons:

+ Dell Poweredge R900 4 quad-cores (total of 16 cores at 1.6GHz) and the server compiled in just about 2 minutes. 
+ Dell Poweredge 2850 2 dual cores (total of 4 cores at 2.8GHz) compiled in roughly 30 minutes.

So depending on your system speed (and number of cores) this step could very well take a while to complete. Once the compile is done and you dont have any errors you can proceed to install it with

    # sudo if not root
    make install

This will install your server software in the `-DCMAKE_INSTALL_PREFIX` location that we specified during the cmake configuration step. Before we go on lets look at the directory structure

+ /opt/mangos - this is our root directory (if yours is different you can substitute this value for your location)
+ /opt/mangos/etc - will be all our configuration files
+ /opt/mangos/bin - binary directory containing the realmd and the mangosd programs

##DATABASE INSTALLATION
Lets get back to our sources directory and start with adding in the required databases. Up until just recently adding all the databases and there patches was very difficult and I had created a few scripts to manage that task however I will not be using them as Factionwars, Nemok, BrainDedd and Antz have done a great job on a bash script that does most of the heavy lifting for you.
We are going to run a few commands to perform the following tasks:

+ Set up root password (in the event it wasn't done during the yum install step)
+ import realmd.sql
+ import mangos.sql
+ import characters.sql
+ import scriptdev2 database (is this needed? I've heard some things around the wiki about moving all that into the core when will that take effect?)

now that we know what we are doing lets see how we are doing it:

+ MySQL root password:

    # In the even that you system didn't set a password at the time of install
    # you will need to set the password here in order to use the installer provided
    # the script will default to "root" as the password and will not accept a blank password
    # in the event that you had not set a password for root you will leave the field blank in the following command
    mysql --user=root --password= --host=localhost
    # you should be looking at the MariaDB prompt 
    # MariaDB [(none)]>

Now at this prompt we will issue a few commands in order to set our root password and secure the server.

    UPDATE mysql.user SET Password = PASSWORD('new_password_here') WHERE User = 'root';
    FLUSH PRIVILEGES;
    exit;

This will set the password of 'new_password_here' to the user root, it will effect every instance of the user root so all passwords for root are now 'new_password_here'. The FLUSH statement causes the server to reread the grant tables. Without it, the password change remains unnoticed by the server until you restart it.


    # /root/SOURCES is the location of all of my git cloned repositories
    cd /root/SOURCES/server/sql/
    mysql --user=root --host=localhost --password=pass realmd < realmd.sql
    mysql --user=root --host=localhost --password=pass < create_mysql.sql
    cd /root/SOURCES/server/src/bindings/scripts/sql
    # this should set up all the required scripts
    mysql --user=root --host=localhost --password=pass < scriptdev2_create_database.sql
    mysql --user=root --host=localhost --password=pass scriptdev2 < scriptdev2_create_structure_mysql.sql
    mysql --user=root --host=localhost --password=pass scriptdev2 < scriptdev2_script_full.sql
    cd /root/SOURCES/database/

At this point we can run the Linux Installer provided in the repository

    bash ./install_linux.sh

Follow the on screen instructions. You will eventually come to a part of the script

    Please enter the path to your Mangos Three repository:

At this point you will need to enter the path to the directory of your server code for example mine is:

    /root/SOURCES/server

That completes the database installation

###CONFIGURATION SETTINGS
Well if your still with me this far I think your doing pretty good. We will now set our configuration settings and even set up the AH-Bot. First off lets start with the realmd section as this is the easiest to get on-line with out any trouble.

#####NOTES

+ /opt/mangos/logs - we will create this directory for our log files
+ /opt/mangos/data - we will create this directory for our data files

I haven't used the client data extractors in quite some time I've been using a back up of my data for about a year and I've just been moving it around to different servers and new compiles, however I don't think the processes has changed all that much. If you need to get your data extracting I would go a head and do that now so you can work on your configuration settings.

Back to our shell (or putty through SSH):

    cd /opt/mangos
    mkdir /opt/mangos/logs
    mkdir /opt/mangos/data
    cd /opt/mangos/etc

Inside of the this directory you should see 3 files:

+ mangosd.conf.dist
+ realmd.conf.dist
+ scriptdev2.conf.dist

Before we start to change configuration settings lets grab our AHBot.conf file 

    cp /root/SOURCES/server/src/game/AuctionHouseBot/ahbot.conf.dist.in /opt/mangos/etc/ahbot.conf.dist

I copied ahbot.conf.dist.in to ahbot.conf.dist as I like to have the dist files around in case I need to look at the default settings. We will need to rename them (or simply copy) to reflect name.conf. A little bit of Bash-Fu and we can do all 4 renames in one line:

    # rename the files
    ls | sed -e "p;s/\.dist//" | xargs -n2 mv
    # to copy and leave the .dist files as a back up as I like to do
    ls | sed -e "p;s/\.dist//" | xargs -n2 cp

The ls output is piped to sed, then we use the p flag to print the argument without modifications, in other words, the original name of the file.
The next step is use the substitute command to change file extension.

**NOTE**: We’re using single quotes to enclose literal strings (the dot is a meta-character if using double quotes escape it with a backslash).
The result is a combined output that consists of a sequence of old_file_name -> new_file_name.
Finally we pipe the resulting feed through xargs to get the effective rename of the files.

Now that we have adjusted all the file names lets modify a few settings in the files to allow us to connect to the database and get our servers up.
First off lets edit the RealmD settings `realmd.conf`:

    # hostname;port;username;password;database
    LoginDatabaseInfo = "127.0.0.1;3306;mangos;mangos;realmd"
    ...
    LogsDir = "../logs" # the path is relative to the bin directory
    ...
    # Also because I like colourful readouts to identify problems we specify log colors here
    # Format "normal_color details_color debug_color error_color
    # The following color codes will be used "13 7 11 9"
    LogColors = "13 7 11 9"
    ...

That is the RealmD configuration settings and now for our mangosd configuration `mangosd.conf`:

    DataDir = "../data"
    LogsDir = "../logs"
    LoginDatabaseInfo     = "127.0.0.1;3306;mangos;mangos;realmd"
    WorldDatabaseInfo     = "127.0.0.1;3306;mangos;mangos;mangos"
    CharacterDatabaseInfo = "127.0.0.1;3306;mangos;mangos;characters"

    # the following are turned on my setup how ever they are not required to turn the server on
    WorldLogFile = "world.log"
    ...
    GmLogFile = "gms.log"
    ...
    RaLogFile = "remote_access.log"
    ...
    # Also because I like colourful readouts to identify problems we specify log colors here
    # Format "normal_color details_color debug_color error_color
    # The following color codes will be used "13 7 11 9"
    LogColors = "13 7 11 9"
    ...

    # Turn Remote Access On (I will be using it for connecting putty in order to run commands)
    Ra.Enable = 1
    ...
    # If you require SOAP you can turn that on here 
    SOAP.Enabled = 1

and `scriptdev2.conf`

    ScriptDev2DatabaseInfo     = "127.0.0.1;3306;mangos;mangos;scriptdev2"

    # Log File for SD2-Errors
    SD2ErrorLogFile = "../logs/SD2Errors.log" #there is no log directory option so you must specify path + file here

Finally the `AHBot.conf` I will be leaving all values in the AH-Bot at defaults, however I will show you which lines are needed to turn the AH-Bot on:

    AuctionHouseBot.Seller.Enabled = 1
    ...
    AuctionHouseBot.Buyer.Enabled = 1

Well that takes care of all of the configuration and a few other options that you might want to use. Now at this point we have the data directory to populate and then its run-time.

    # sudo if not root
    adduser --system --home-dir /opt/mangos --no-create-home --shell /usr/sbin/nologin --user-group mangos
    chown -R mangos:mangos /opt/mangos
    chmod -R 770 /opt/mangos

If you don't have a Black-Belt in Bash-Fu that's not a problem as we will now break that down into hopefully some thing a bit more understandable

+ --system = we want to create a system user
+ --home-dir /opt/mangos = this will be the home of the user we are going to create and should also reflect the base installation directory of your server core
+ --no-create-home = this lets the adduser program know not to create the home directory, we already did that during the install
+ --shell /usr/sbin/nologin = we also do not want this new user to be able to log-in as this is a system user not a human user
+ --user-group = this lets us create the group along side the user that way later on we can assign human users to that group and give out group permissions
+ mangos = finally the name of the user/group we are creating 

The chown sets mangos:mangos(user:group) as the full owner and group of that directory. And the chmod sets the permission to allow owner and group full access to the directory Recursively. We can add a user to our mangos group in order to upload files to the data directory:

    # sudo if not root
    usermod USERNAME -a -G mangos

This will add USERNAME to the group mangos

Once your data extraction utilities are done with there job you can move them over to the server using a tool like WinSCP. As long as you set your user in the mangos group you shouldnt run into any upload problems.

###SERVER BOOT
Lets boot the realmd server first and and see if its running fine

    cd /opt/mangos/bin
    ./realmd
    MaNGOS Three/ (* * Revision 12778 - *) for Linux_x64 (little-endian) [realm-daemon]
    <Ctrl-C> to stop.

    Using configuration file /opt/mangos/etc/realmd.conf.
    Login Database total connections: 2
    MySQL client library: 10.0.15-MariaDB
    MySQL server ver: 10.0.15-MariaDB
    MySQL client library: 10.0.15-MariaDB
    MySQL server ver: 10.0.15-MariaDB
    Added realm id 1, name 'MaNGOS'

At this point we know it loads with no issues so lets CTRL+C and set up the realm id 1 named MaNGOS. Back to our MySQL console we go:

    mysql --user=root --password=pass --host=localhost

and then lets set the IP address of our host so we can connect our game client to the server:

    UPDATE `realmd`.`realmlist` SET `address`='a.b.c.d' WHERE `id`=1;

now this line by its self will not work you need to replace `a.b.c.d` with a real ip address if you are on the same LAN you may specify the machines IP address found by running:

    ifconfig

if you are connecting across the internet then the ip address you want to use is going to be your ISP assigned address you can find that by running:

    curl -s 'http://checkip.dyndns.org' | sed 's/.*Current IP Address: \([0-9\.]*\).*/\1/g'

now lets boot mangosd and see the results of that

    cd /opt/mangos/bin
    ./mangosd
now at this point you should see a lot of loading and then if all goes well:

    Starting Remote access listener on port 3443 on 0.0.0.0
    MaNGOSsoap: bound to http://127.0.0.1:7878
    Max allowed socket connections 16384
    Network Thread Starting
    Network Thread Starting

And then your up and running. If you would like to get into your RA Console you will need to set up a RAW socket connection to port 3443. I use putty for this just set your ip address for the server and then select raw hit connect and login using your administrative account (default is ADMINISTRATOR)

###GM Commands
Here is a small script I wrote a while back to log into the mysql back end and grabs the gm commands and there permissions level from the database. For the sake of reference and documentation I will post it here for you:

    <?php
    
    $database = "mangos";
    $host = "localhost";
    $username = "mangos";
    $password = "mangos";
    
    ?>
    
    <html>
    <head>
       <title>Mangos Commands</title>
    </head>

    <body bgcolor="black">
    <font color="white">
    <center><h1>Commands</h1></center>

    <center>
        <table bordercolor="black" border="1">
            <tr>
                <th><FONT COLOR=WHITE>Name</FONT></th>
                <th><FONT COLOR=WHITE>GM Level</FONT></th>
                <th><FONT COLOR=WHITE>Description</FONT></th>
            </tr>

    <?php
    $view = 60;
    $db = mysql_connect($host, $username, $password) or die ("Unable to Connect ERROR" . mysql_error());
    mysql_select_db($database,$db) or die ("Cannot select Database ERROR: " . mysql_error());

    $query =  "SELECT name, security, help FROM mangos.command ORDER BY security";

    $result = mysql_query($query);
    while ($row = mysql_fetch_array($result))
    {
        $name = $row["name"];
        $security = $row["security"];
        $help = $row["help"];
        echo "\t<tr>\n";

        echo "\t\t<td><FONT COLOR=WHITE>$name</FONT></td>\n";
        echo "\t\t<td><FONT COLOR=WHITE>$security</FONT></td>\n";
        echo "\t\t<td><FONT COLOR=WHITE>$help</FONT></td>\n";
        echo "\t</tr>\n";
    }
    ?>

    </table>
    </center>
    </font>
    <br>

    </body>
    </html>

Pretty simple little page its just a black page with a white table of commands these commands are sorted by Account level you may change the sorting by any field by adjusting the SQL Query:

    SELECT name, security, help FROM mangos.command ORDER BY security;

###FIREWALL
The list of ports is located towards the top of this page with a full description the commands below will open each port on the firewall. For those ports 
In the event that your RPM Distro has a firewall installed here is a list of commands that will help you open your ports:

    iptables -A INPUT -p tcp --dport 3306 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    iptables -A INPUT -p tcp --dport 3443 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    iptables -A INPUT -p tcp --dport 22 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    iptables -A INPUT -p tcp --dport 8085 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    iptables -A INPUT -p tcp --dport 3724 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    iptables -A INPUT -p tcp --dport 80 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    iptables -A INPUT -p tcp --dport 7878 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
