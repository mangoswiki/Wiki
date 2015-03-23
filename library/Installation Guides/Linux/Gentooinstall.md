[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------
##How to compile/install mangos under Gentoo linux

### Get needed dependencies
You will need gcc cmake and make

I also installed my own ace library (dev-libs/ace-5.7.2)
So I have cmake with -DACE_USE_EXTERNAL

It seems that mangos use an old tbb library version (2.2), so I dont try to use the tbb curently available in gentoo


### check out sources
MaNGOSZero for Classic

    git clone --recursive http://github.com/mangoszero/server.git
    cd server
    git clone --recursive http://github.com/mangoszero/database.git database    

MaNGOSOne for TBC

    git clone --recursive http://github.com/mangosone/server.git
    cd server
    git clone --recursive http://github.com/mangosone/database.git database    

MaNGOSTwo for WoTLK

    git clone --recursive http://github.com/mangostwo/server.git
    cd server
    git clone --recursive http://github.com/mangostwo/database.git database    

MaNGOSThree for Cataclysm

    git clone --recursive http://github.com/mangosthree/server.git
    cd server
    git clone --recursive http://github.com/mangosthree/database.git database    
    cd src/bindings
    git clone --recursive http://github.com/mangosthree/scripts.git


### configure/compiling
First edit src/bindings/CMakeLists.txt and uncomment this line:

    #add_subdirectory(scripts)

to look like this:

    add_subdirectory(scripts)

Go to to mangos sources and do:
<pre>cmake . -DCMAKE_INSTALL_PREFIX=/opt
make
make install
</pre>
that's not enough, some extract tools need libmpq
<pre>cd dep/libmpq
./autogen.sh
./configure
make
</pre>

No need to make install because tools statically use this library.

For each of the following directories:-
<pre>contrib/extractor 
contrib/mmap 
contrib/vmap_assembler 
contrib/vmap_extractor_v3

do cmake . and make
</pre>

Now you have compiled all needed stuffs

### SQL
Now time to fill your mysql database

    mysql -pPASSWORD < sql/create_mysql.sql

    mysql -pPASSWORD mangos < sql/mangos.sql
    mysql -pPASSWORD characters < sql/characters.sql
    mysql -pPASSWORD realmd < sql/realmd.sql

this creates 3 databases and a default mangos SQL user.

Now that the table structures are created, its time to populate it

Now you need to populate the databases. This includes quests, dialog, etc. There is a script that will compile a massive number of sql files into one big sql batch you can apply at once.

    cd /home/mangos/database
    bash make_full_db.sh
    mysql -u root -p mangos < full_db.sql

    mysql -pPASSWORD mangos < full_db.sql

Depending on when you are reading this, the server might need a few "updates" applied to it without which the world server will refuse to run. I needed to do this with mangoszero but not mangostwo. Do this step if you get an error at runtime. 

    cd /home/mangos/server/sql/updates
    mysql -u root -p mangos < blahblahblah_mangos_whatever.sql

Repeat for every similar .sql file in the folder. Mangos might not be the appropriate database for this every time.

### Extracting the data 
Now it's time to extract data from your WoW game directory.
Basically look at contrib/extractor_binary/ExtractResources.sh for seeing what to be done
So do:
<pre>contrib/extractor/ad
contrib/vmap_extractor_v3/vmapextract/vmapextractor
contrib/vmap_assembler/vmap_assembler
</pre>

####NOTE
Some tools segfault, but works the second time I launched it:)

###Creating final directory
<pre>Create /opt/mangos
mkdir /opt/mangos</pre>
I have copied in realmd and mangos binary and all libs produced by the build

    libtbbmalloc_proxy.so
    libtbbmalloc.so
    libtbb.so
    realmd
    mangosd

Copy mangosd.conf.dist as mangosd.conf and realmd.conf.dist as realmd.conf
These need to be edited with the correct username / password details.

Copy in it also all the directories produced by the extractor (dbc, maps, vmaps, mmaps)

###Configuration
This step is documented at the page: [**Configuration Files**](Configuration-Files)

###Starting servers
I start at hand the servers with

    ./realmd
    ./mangosd

In the console of mangos do:

    account create accountname password
    account set addon 2
