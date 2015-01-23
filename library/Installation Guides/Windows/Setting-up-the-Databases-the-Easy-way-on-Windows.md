[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------

This is intended for users who just want to get mangos running. If you are an experienced developer you know what do do.

## Required software ##

Download MySQLCommunity edition 5.5
Use the 32bit version

[http://dev.mysql.com/downloads/mysql/5.5.html#downloads](http://dev.mysql.com/downloads/mysql/5.5.html#downloads)

----------

A MySQL GUI
free and easy to use.

Use 64 or 32 bit whatever you like

[http://code.google.com/p/sqlyog/downloads/list](http://code.google.com/p/sqlyog/downloads/list)

----------

The database

[http://github.com/mangoszero/database](http://github.com/mangoszero/database)

You will find a download link for the database in .zip format on the right side.

----------


## 1- Installing Mysql ##

Just choose - next next next.

When its asks for Standard Character set choose UTF8, not essential but maybe you will become a developer and this will make your life easier then.

When it asks for a root password enter a password and **NOTE** it.

## 2- Installing SQLyog ##

Nothing special here.
Next Next Next and you are fine.

## 3- Unzipping the database and prepare it for an easy install ##

extract the database to a folder of your choice

**EXAMPLE: C:\MANGOSDB**

Start up the command prompt by clicking on START / the WINbutton on 7

WIN7 type cmd in the search field and press enter on XP you have to click the **RUN** button

If you are 30+ and know what good old DOS commands are just go to your database folder\_full_db and continue at **COPY**

**If not read here:**

Type

cd\

cd mychosenfolder\database\_full_db

In my EXAMPLE this would be 

cd\

cd MANGOSDB\database\_full_db

**- COPY**

then type

copy *.sql complete.sql

You should see something like (x) files copied.

type

exit

and you are back in windows.

## 4- Installing the database ##
Start MySQLyog

You will start on the connect screen.

MySQL Host Adress will be 127.0.0.1
if this does not work for some reason try localhost

Username is: root

Password is: The one you should have noted under step 1

port: 3306

Sometimes compressed protocol causes errors so uncheck it.

Click connect

Now you seen a tree structure on the left
right-click on the root@localhost
and choose create database

type in realmd and click create

repeat this step and create:

mangos
characters
scriptdev2

## 5- Filling the DB with life ##

right-click on realmd

choose import -> import SQL script

choose your previously downloaded mangos source folder and navigate to:
MANGOSSOURCEFOLDER\Server\SQL\
and select realmd.sql
click execute

As you probably guessed

right-click on characters

choose import -> import SQL script

choose your previously downloaded mangos source folder and navigate to:
MANGOSSOURCEFOLDER\Server\SQL\
and select charaters.sql
click execute

**BUT NOW**

right-click on mangos

choose import -> import SQL script

choose your previously downloaded **Database** folder

EXAMPLE:
MANGOSDB\database\_full_db
and select complete.sql
click execute

**NOW - Installing Scripdev2**

right-click on scriptdev2

choose import -> import SQL script

choose your previously downloaded mangos source folder and navigate to:
MANGOSSOURCEFOLDER\Server\src\bindings\scripts\sql
and select scriptvdev2_create_database.sql
click execute

then

right-click on scriptdev2

choose import -> import SQL script

choose your previously downloaded mangos source folder and navigate to:
MANGOSSOURCEFOLDER\Server\src\bindings\scripts\sql
and select scriptvdev2_script_full.sql
click execute

**and finally**

right-click on mangos

choose import -> import SQL script

choose your previously downloaded mangos source folder and navigate to:
MANGOSSOURCEFOLDER\Server\src\bindings\scripts\sql
and select mangos_scriptname_full.sql
click execute

## **Congratulations you are done** ##
