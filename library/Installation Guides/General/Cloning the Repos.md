[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md)

----------

##How to Clone the MaNGOS repos
 
##Important Things to remember

There are Five MaNGOS cores, each designed to support a specific version of WOW

* MangosZero - Vanilla
* MangosOne - The Burning Crusade
* MangosTwo - Wrath of the Lich King
* MangosThree - Cataclysm
* MangosFour - Mists of Pandaria

The default branch of all the repos is always the latest released version, however between releases other branches contain the ongoing development work.

##Cloning the default branch of the repos

Server Sourcecode

    git clone https://github.com/mangoszero/server.git --recursive

Database

    git clone https://github.com/mangoszero/database.git --recursive

The server and database folders then contain the contents of each repo.

##Cloning a specific branch of the repos

If you want the try out the latest development work in progress, they are available. In these examples I will use a branch called develop21

Server Sourcecode

    git clone https://github.com/mangoszero/server.git --recursive -b develop21

Database

    git clone https://github.com/mangoszero/database.git --recursive -b develop21

The server and database folders then contain the contents of each repo for this branch.
