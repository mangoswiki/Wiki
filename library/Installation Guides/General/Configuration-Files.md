[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------

When you install MaNGOS, a folder called etc is created in the install directory. Inside this folder there are two files: 

    realmd.conf.dist
    mangosd.conf.dist

These are used to configure each of the servers when they run. To edit them, first copy the two .dist files, and remove the .dist. The .conf files will be the files you edit in order to change the behavior of your local site, while the unedited .dist versions retain the unchanged original default settings so you can revert back any time you need to.

    cp realmd.conf.dist realmd.conf
    cp mangosd.conf.dist mangosd.conf

Then in each file you have to change the password for MySQL that you set earlier. The default is 'mangos' so if you didn't change the password in an earlier step, then the conf's will work right out of the box. If you did change the password, find a line that looks like
    
    LoginDatabaseInfo = "127.0.0.1;3306;mangos;mangos;realmd"
                             |       |     |      |> password for the MySQL account
                             |       |     |> username of the MySQL account
                             |       |> Port that the server is running on
                             |> address that the MySQL server is running on

Then just change the second mangos to the password that you set earlier.

You must change the password 1 time in realmd.conf and 3 times in mangosd.conf. The password must be changed where is says LoginDatabaseInfo, WorldDatabaseInfo, or CharacterDatabaseInfo.

After you have changed all the passwords, you must set the location of the server data (e.g. maps, vmaps, dbc's). In mangosd.conf, change
    
    DataDir = ""

to wherever you keep the server data.

Of course you should go over all of the .conf files and change what you want. Comments can tell you much more than I can.