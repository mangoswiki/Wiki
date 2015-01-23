[![](/wiki/icons/home.gif)](/wiki/Home.md) 

----------

### Generic Resources about Git

[All about Git - official page](http://git-scm.com)

#### Some good video talks about http:

* [Linus Torvalds: History&Concepts](http://goo.gl/z72s)
* [Scott Chacon: Git basics, live examples](http://goo.gl/R9H2q)
* [Randal Schwartz: Git basics, descriptional](http://vimeo.com/35778382)
* [Jesica Kerr: Git basics, descriptional](http://vimeo.com/46010208)

#### A good book of the subject:

* [Pro-Git](http://git-scm.com/book)

### Install Git

#### On Windows
Install [MySysGit](http://code.google.com/p/msysgit/downloads/list)

Be sure to check the install with ["Git bash here" support](http://i49.tinypic.com/v45smh.jpg)

#### On Linux
Use your package manager to install git.

### Basic Functions

#### Cloning a repo to your harddrive

The most basic form of this command is:
<pre>git clone --recursive http://github.com/{username}/{reponame}</pre>

A slightly better form is to specify the folder name of the local repo:
<pre>git clone --recursive http://github.com/{username}/{reponame} {localreponame}</pre>

Due to the introduction of submodules in mangos, we is propberbly safer to use the following variant:
<pre>git clone --recursive http://github.com/{username}/{reponame} {localreponame}</pre>

In the case of mangosZero this would be a valid command to clone it correctly to a folder called 0server
<pre>git clone --recursive http://github.com/mangoszero/server 0server</pre>

#### Updating an existing repo with the latest source

From the folder containing the source, type:

<pre>git pull --recurse-submodules</pre>

This will will pull in all updated files, you can then proceed to build using Visual Studio or cmake/make on Linux.

