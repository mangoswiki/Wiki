[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------
The server needs certain files from the client to run. The extraction process on windows is different from the one on unix systems.

**The extracted files are identical on all systems, once extracted they can be used on every operating system.**

## Extracting the game assets

### Preparation
Create folders for your data and log files inside your MaNGOS root directory (e.g. C:\Mangos or /opt/mangos). In this example they are named "data" and "logs".
* On a Linux Shell run:
    `mkdir data && mkdir logs`


* On Windows cmd run: `md data & md logs`

And then extract the data files from Blizzard's mpq archives. Make sure your the client's version matches your server's.

###On Linux

---

_**Depending on your distribution you may need to install cmake!**_

In the first step you have to compile the tools for extracting.  The source files of the tools are in the directory **contrib**:
#### Compiling

There are four needed binarys for extracting all the Client-Data that we need: 

* **map-extractor** is for extracting dbcs (Database files of the client) and the maps.
* **vmap-extractor** is for extracting model data out of the clients archives.
* **vmap-assembler** creates the correct "vmap" files MaNGOS needs.
* **MoveMap-Generator** creates a movement map to have mobs not walk through walls etc, not necessary to have.

First compile libmpq which is needed, _skip this step when you're with mangos-three (Cataclysm)_ :

    cd ~/server/dep/libmpq 
    ./autogen.sh
    ./configure
    make

Then compile "ad":

    cd ~/server/contrib/extractor
    cmake .
    make

then copy the binary **map-extractor** from the current directory to your WoW-Folder:

    cp ad /path/to/wow

Next, you'll need to compile stormlib:

    cd ~/build-dir/mangos/server/dep/StormLib/
    cmake .
    make

After that, compile the **vmap-extractor** with the commands:

    cd ~/server/contrib/vmap_extractor
    cmake .
    make

then copy the file **vmap-extractor** from the directory **vmap-extract** into your WoW-Folder:

    cp vmapextract/vmapextractor /path/to/wow

As last step do the same thing with the vmap-assembler:

    cd ~/server/contrib/vmap_assembler
    cmake .
    make

after compiling copy the binary **vmap-assembler** to your WoW-Folder:

    cp vmap_assembler /path/to/wow

Now lets compile and copy **MoveMap-Generator** to the same folder:

    cd ~/src/contrib/mmap/
    cmake .
    make
    cp MoveMapGen /path/to/wow

If you run into trouble when running make you could refer to http://getmangos.eu/wiki/Tutorials/Frequently%20Asked%20Questions.md under the heading typical compile problems.

### Running the tools
After you copied the compiled tools to your WoW base Directory you can run them in this order:

    cd /path/to/wow 
    ./ad
    ./vmapextractor
    mkdir vmaps
    ./vmap_assembler Buildings vmaps

If you want the movement maps aswell you should run something along these lines:

    cp ~/server/contrib/extractor_binary/MoveMapGen.sh /path/to/wow
    cd /path/to/wow
    mkdir mmaps
    ./MoveMapGen.sh 1

_**If the script doesn't seem to work and just outputs garbage please don't run it as root as this seems to be the problem for people.**_
Run it without arguments to find all the possible things you can change.

Now you just need to copy the folders dbc, maps, and vmaps to the data directory (in our example /home/mangos/data) of your server:

    cp dbc -R /home/mangos/data
    cp maps -R /home/mangos/data
    cp vmaps -R /home/mangos/data

And if you ran .MoveMapGen.sh:

    cp mmaps -R/home/mangos/data

And you're done with the extraction process!

###On Windows

---
Move the files in server/contrib/extractor_binary to your WoW client's location on your Windows filesystem.

Click start, type cmd in the search bar and do shift+ctrl+enter to run it as administrator. Navigate to your WoW client's location and do the following.

    ad.exe
    vmapExtractor.exe

    mkdir vmaps
    vmap_assembler.exe Buildings vmaps

Move the dbc, maps and vmaps folders to your server's data folder. Find mangosd.conf, edit DataDir to your current data folder's path (where dbc, maps and vmaps are located).

Note that this does NOT extract the movement maps like is described in the Linux section. The MoveMapGen.sh script is supposed to be run on Linux under the bash shell, but works on a windows machine if run from a cygwin terminal. If you're not even vaguely a programmer, the script runs MoveMapGen.exe once for each of the integer map ids stored within the script as MAP_LIST_A, MAP_LIST_B, MAP_LIST_C, MAP_LIST_D in the script. This could be done manually, but you'd be insane to try it.

If you run into an runtime error regarding msvcp110.dll while extracting movement maps, you likely need to install a code library contained within Visual C++ Redistributable for Visual Studio 2012 Update 3, which can be downloaded from [www.microsoft.com/en-us/download/details.aspx?id=30679](www.microsoft.com/en-us/download/details.aspx?id=30679).
