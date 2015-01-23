[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------

So you are looking to upgrade your server to the latest and greatest release....

1) Open up a Git Shell

2) Change directory to the folder where you cloned the server sourcecode

3) type `git pull`

4) Change directory to the folder where you cloned the scripts sourcecode

5) type `git pull`

6) Compile the server sourcecode and copy the files to your server

7) Compile the scripts sourcecode and copy the files to your server

8) Change directory to the folder where you cloned the database

9) type `git pull`

10) run the server and an error similar to the following will be shown:-

    MaNGOS/0.17.0-DEV (* * Revision 11000 - *) for Win32 (little-endian) [world-daemon]

    <Ctrl-C> to stop.

    MM   MM         MM   MM  MMMMM   MMMM   MMMMM
    MM   MM         MM   MM MMM MMM MM  MM MMM MMM
    MMM MMM         MMM  MM MMM MMM MM  MM MMM
    MM M MM         MMMM MM MMM     MM  MM  MMM
    MM M MM  MMMMM  MM MMMM MMM     MM  MM   MMM
    MM M MM M   MMM MM  MMM MMMMMMM MM  MM    MMM
    MM   MM     MMM MM   MM MM  MMM MM  MM     MMM
    MM   MM MMMMMMM MM   MM MMM MMM MM  MM MMM MMM
    MM   MM MM  MMM MM   MM  MMMMMM  MMMM   MMMMM
            MM  MMM https://getmangos.eu
            MMMMMM

    Using configuration file mangosd.conf.
    OpenSSL 1.0.0 29 Mar 2010 (Library: OpenSSL 1.0.0 29 Mar 2010)
    Using ACE: 5.8.3
    World Database: 127.0.0.1;3306;root;mangos;mangos
    Connected to MySQL database at 127.0.0.1
    MySQL client library: 5.1.49
    MySQL server ver: 5.5.8
    AUTOCOMMIT SUCCESSFULLY SET TO 1
    SQL: SELECT required_10998_01_mangos_spell_proc_event FROM db_version LIMIT 1
    query ERROR: Unknown column 'required_10998_01_mangos_spell_proc_event' in 'field list'
    [0 ms] SQL: SELECT * FROM db_version LIMIT 1
    The table `db_version` in your [WORLD] database indicates that this database is out of date!

    [A] You have: --> `10973_01_mangos_game_event_mail.sql`
    [B] You need: --> `10998_01_mangos_spell_proc_event.sql`

    You must apply all updates after [A] to [B] to use mangos with this database.

    These updates are included in the sql/updates folder.[0 ms] SQL: SET NAMES `utf8`

    Please read the included [README] in sql/updates for instructions on updating.

The Version of the Database MaNGOS expects is not the same as we have installed, so we need to update it

11) change folder to server\sql\updates and apply the updates from the version mentioned in [A], up to the version mentioned in [B]. Should there be extra ones, **DO NO APPLY THEM** !!
