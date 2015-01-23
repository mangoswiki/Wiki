[![](/wiki/icons/home.gif)](/wiki/Home.md) 

----------

### Setting up User Accounts

From the Mangos command prompt:-

We need to create an account to use with the server.

    account create testuser mypassword

In order to use the expansions

for Classic only

    account set addon testuser 1

for TBC

    account set addon testuser 2

for WotLK

    account set addon testuser 3

for Cata

    account set addon testuser 4

This will set up a user called testuser with a password of mypassword

Setting up the client to access the server 1) Navigate to the location of the Warcraft Client installed on your local PC

2) Navigate to the “Data\enGB” folder (or other locale if not uk)

3) Open the file “realmlist.wtf” with WordPad

It will contain the following lines (actual detail may vary slightly) :-

    set realmlist eu.logon.worldofwarcraft.com
    set patchlist enGB.patch.battle.net:1119/patch 

Changed these values to the IP address of the server.

That’s it. We’re ready to roll....