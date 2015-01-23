[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 
· Other Versions:  [**English**](/wiki/Installation%20Guides/Linux/Debianinstall.md)  [**Deutsch**](/wiki/Installation%20Guides/Linux/Debianinstall-German.md)

----------

Esta guía es para distribuciones basadas en Debian. Puede ser utilizada como referencia para otras distros, pero debes tú mismo completar el resto. La única diferencia es conocer los paquetes necesarios a instalar.

##Intro
Wiki en español traducida de la versión inglesa, y con resumen de acciones a seguir para poner en marcha tu servidor MaNGOS, todo bajo Linux que como sabes rinde mejor el servidor que si fuese sobre Windows.

###1. Consiguiendo las dependencias.
Mangos Necesita un número de aplicaciones para compilar y ejecutar correctamente. Se pueden instalar con cualquier gestor de paquetes apt por ejemplo. Simplemente ejecuta esto como super usuario o root:

    apt-get install build-essential gcc g++ automake git-core autoconf make patch libmysql++-dev mysql-server libtool libssl-dev grep binutils zlibc libc6 libbz2-dev cmake

mysql-server se ejecutará como un pequeño demonio y te preguntará por una clave de root y otras cosas, no olvides las contraseñas.

Si no puedes descargar algunos de estos paquetes prueba con **sudo apt-get update** para actualizar los repositorios. Si aún así falla es posible que algunos paquetes estén perdidos por alguna causa. Puedes probar **apt-cache search** *package* (apt-cache no requiere privilegios de superusuario o root.

###2. El usuario mangos (Opcional)
Deberías crear un nuevo usuario para ejecutar tu servidor MaNGOS, no es recomendable ejecutar nada como root por temas de seguridad.

    adduser mangos

Y sigue los pasos. Otra manera de hacer más rápido esto:

    useradd mangos
    passwd mangos

Esto creará un nuevo usuario con el nombre de mangos y con sus permisos en /home/mangos por defecto. Esto es donde ejecuto mi servidor, por que esta cuenta es solo para esto, nada más. Si prefieres ejecutar tu servidor en otra carpeta aseguraté de que tienes permisos correctos en esa carpeta.

    chown /your/folder/here mangos

Y cuando hayas hecho eso, cambia al usuarior

    su mangos


###3. Consiguiendo el código fuente
Hay más de una versión de MaNGOS la cual escojer.

Esta guía usa el proyecto master que en este caso es Cataclysm y si estás buscando hospedar algún xpac, simplemente cambia los links de github para que reflejen eso.

Aseguraté de que estás en la carpeta correcta y después baja el código del servidor, base de datos y fuentes de ScriptDev2. ScriptDev2 necesita estar en server/src/bindings

    git clone --recursive http://github.com/mangosthree/server.git
    git clone --recursive http://github.com/mangosthree/database.git

###4. Compilando el código fuente del servidor.

    cd ~/server
    mkdir build
    cd build

Compila el servidor, especifica en donde será instalado el servidor después de la compilación. Esto puede tardar unos cinco minutos. Date cuenta que ".." es una constante al directorio padre. Haciendo "cmake .." en /home/mangos/server/build es lo mismo que hacer "cmake /home/mangos/server". El -DPREFIX= argumento especifíca donde será instalado el servidor. Cambialó según te convenga.

    cmake .. -DPREFIX=/home/mangos/
    make
    make install

###5. Extracting the game assets
This step is documented at the page: [**Extract Game Assets**](Extracting-Game-Assets)

###6. SQL batch magic
Mangos uses SQL databases to store just about a million things. It also comes with a number of batch scripts to build the required databases for you. You will be using the "mysql -u root -p" command a lot. This command essentially lets you run mysql queries from the command line. The -u parameter specifies which user to apply the query as (in this case, root), and the -p parameter is necessary if your user has a password. Keep in mind -p by itself works and you don't need to do "mysql -u root -p qwerty123" or whatever your password is!

Note that these .sql files would probably work with a gui mysql application such as phpmyadmin or navicat. 

Start with the files in server/sql. This will create the three databases Mangos uses and build the table structures.

    cd /home/mangos/server/sql
    mysql -u root -p < create_mysql.sql
    mysql -u root -p realmd < realmd.sql
    mysql -u root -p characters < characters.sql
    mysql -u root -p mangos < mangos.sql

ScriptDev2 also needs its own database.

    cd /home/mangos/server/src/bindings/scripts/sql
    mysql -u root -p < scriptdev2_create_database.sql
    mysql -u root -p scriptdev2 < scriptdev2_create_structure_mysql.sql
    mysql -u root -p scriptdev2 < scriptdev2_script_full.sql

Now you need to populate the databases. This includes quests, dialog, etc. There is a script that will compile a massive number of sql files into one big sql batch you can apply at once.

    cd /home/mangos/database
    bash make_full_db.sh
    mysql -u root -p mangos < full_db.sql

Depending on when you are reading this, the server might need a few "updates" applied to it without which the world server will refuse to run. I needed to do this with mangoszero but not mangostwo. Do this step if you get an error at runtime. 

    cd /home/mangos/server/sql/updates
    mysql -u root -p mangos < blahblahblah_mangos_whatever.sql

Repeat for every similar .sql file in the folder. Mangos might not be the appropriate database for this every time.

###7. Configuration
To configure your server you will need to edit a few text files, and edit a few entries in your SQL databases. I recommend you use a graphical SQL client such as phpmyadmin if your computer runs apache2, navicat for windows or squirrel sql for linux. First, copy the default configuration files created by your server and edit them as necessary.

    cd /home/mangos/etc
    cp realmd.conf.dist realmd.conf
    cp mangosd.conf.dist mangosd.conf
    cp scriptdev2.conf.dist scriptdev2.conf

The minimal effort required run a function server is to edit the following lines in mangosd.conf

    DataDir = "/home/mangos/data"
    LogsDir = "/home/mangos/logs"

Of course you should go over all three .conf files and change what you want. Comments can tell you much more than I can.

Now, point your SQL client to your SQL server and select the realmd database. Then select the realmlist table. There should already be an entry there. Edit the name, address and port fields as necessary. The reason why 127.0.0.1 doesn't work is because that address is what the CLIENT will try to connect to, and thus will try to probe itself.

###8. Running the server and creating an Admin account
Your binaries will be located in the bin folder of your server's root directory. Those are mangosd realmd.

mangosd is the world server and realmd is the realm server. Typically you only need one instance of realmd running, and one mangosd instance for every realm you want in your realmlist.

If you want to run these servers using screen, use these scripts, courtesy of krampf. Make sure to chmod +x them.

    #!/bin/sh
    cd /home/mangos/bin
    screen -A -m -d -S mangosworld ./mangosd

    #!/bin/sh
    cd /home/mangos/bin
    screen -A -m -d -S mangosrealm ./realmd

Make sure to run ./mangosd normally once, because you'll need to create your account and give it admin privileges. Run these commands in the mangos command shell.

    account create "username" "password"
    account set gmlevel "username" 3

And here you go! A functional, partially scripted private server for you to mess around with. Have fun.
