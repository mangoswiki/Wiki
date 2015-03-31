[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md)

----------

##How to Update your local repos
 
Change directory to your Server Source code folder

    git pull --recurse-submodules
    git submodule init
    git submodule update

and repeat for the Database

    git pull --recurse-submodules
    git submodule init
    git submodule update

The server and database folders then contain the update contents of each repo for this branch.
