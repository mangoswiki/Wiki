[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 
· Other Versions(old): [**Deutsch**](/wiki/Installation%20Guides/Linux/Debianinstall-German.md)  [**English**](/wiki/Installation%20Guides/Linux/Debianinstall.md)

----------

Esta guía es para todas las distribuciones basadas en Debian.

##Intro
Esta guía es para aquellos que prefiere usar la estabilidad superior y la gestión de los recursos de Linux, o simplemente no se puede usar Windows por varias razones.
Mientras que la actual guía pegajosa de Linux es una gran fuente de información, hay algunos matices no se menciona y el objetivo de este hilo es
Dirección aquellos. Esta guía será en gran medida similar, pero se espera que sea más actualizada con algunos de los cambios en los repositorios. Esta guía
está escrito con el principiante en mente y como tal podría decir lo obvio en la ocasión.

Nota: Si desea utilizar los submódulos con su servidor, puede activar o desactivar durante la etapa de cmake añadiendo lo siguiente antes de su prefijo:
(0 = deshabilitado 1 = habilitado)

    -DBUILDTOOLS = 1 - para construir las herramientas de extracción
    -DENABLE_LIB_SD2 = 1 - para habilitar SD2
    -DENABLE_LIB_ELUNA = 1 - para habilitar Eluna
    -DSOAP = 1 - para activar el jabón
    
###1. Buscar las dependencias.
Mangos necesita un número pequeño de paquetes para poder compilar y ejecutar correctamente. Ésos es fácil con una simple aplicación del gestor de paquetes apt. Simplemente ejecuta la siguiente línea como superusuario:

    sudo apt-get update
    sudo apt-get install cmake cmake-qt-gui git g++ gcc make libace-ssl-dev libace-dev libbz2-dev libmysql++-dev libmysqlclient-dev libssl-dev
    sudo apt-get install mysql-client mysql-common mysql-server zlib1g-dev vim autoconf libtool screen bash
    
MySQL-server ejecutará un demonio corto y simple instalación propia y solicitar una contraseña de root entre otras cosas. Asegúrese de recordar.

###2. El usuario de mangos (no opcional)
DEBE crear un nuevo usuario con el que ejecutar el servidor de mangos. No se recomienda como root para ejecutar el servidor (y un montón de otras cosas).
Vamos a utilizar el nombre de usuario 'Mango' para obtener un ejemplo, puede utilizar cualquier nombre de usuario que quieres pero necesitará reemplazar mangos con su nombre de usuario en todas las rutas.
    
    adduser mangos
    
Esto creará un nuevo usuario con los mangos de nombre bajo las /home/mangos de la carpeta por defecto.
Si usted prefiere su servidor privado para ejecutar en otra carpeta, asegúrese de darle los privilegios de usuario a esa carpeta.
Ejemplo:
    
    chown -R mangos:mangos /path/to/folder
    
Y cuando termines ajuste que, vas a cambiar al usuario, así que podemos comenzar el proceso de instalación.
    
    su - mangos
    
###3. Conseguir la fuente de Mangos
Existen varias versiones de mangos para elegir.

Esta guía servirá de MaNGOS Zero(classic) un ejemplo. Si usted decide usar otra versión, simplemente puede cambiar la URL de clonación a la versión que desea.
Este paso está documentado en la página: [** clonación del Repos**](/wiki/Installation%20Guides/General/Cloning%20the%20Repos.md)

Asegúrese de que está en la carpeta correcta y luego buscar el servidor, base de datos y extras.
    
    git clone --recursive https://github.com/mangoszero/server.git
    git clone --recursive https://github.com/mangoszero/database.git
    
###4. Compilando la fuente del servidor
Ahora crear el directorio en la carpeta del servidor. Tenga en cuenta que ~ es una ruta relativa al directorio home del usuario actual.
    
    cd ~/server
    mkdir build
    cd build
    
Construir el servidor, especificar donde se instalará para después de compilar. Esto puede tardar unos minutos. Tenga en cuenta que ".. / "es una constante para el directorio padre.
El argumento de prefijo especifica donde se instalará el servidor. Cambiar en consecuencia.

    cmake ../ -DCMAKE_INSTALL_PREFIX=/home/mangos/zero
	
Entonces empezamos a compilar. Si usted tiene más de 1 núcleo de CPU, podemos compilar más rápido mediante la adición de la cantidad de núcleos que desea utilizar en la compilación. Puedes hacer
esto añadiendo -j# para la marca comando. es decir: make -j 4
    
    make
    make install
    

###5. Extraer los juegos activos
Este paso está documentado en la página: [** Extraiga el juego Assets**](Extracting-Game-Assets)

###6. Importar la base de datos MySQL
Ahora podemos importar las bases de datos para realmd, mangos y personajes. Esto puede hacerse fácilmente a través de mysql utilizando la contraseña de ROOT que era la configuración anterior.
    
    mysql -u root -p realmd < /home/mangos/database/Realm/Setup/realmdCreateDB.sql
    mysql -u root -p realmd < /home/mangos/database/Realm/Setup/realmdLoadDB.sql
    mysql -u root -p characters < /home/mangos/database/Character/Setup/characterCreateDB.sql
    mysql -u root -p characters < /home/mangos/database/Character/Setup/characterLoadDB.sql
    mysql -u root -p mangos < /home/mangos/database/World/Setup/mangosdCreateDB.sql
    mysql -u root -p mangos < /home/mangos/database/World/Setup/mangosdLoadDB.sql
    
Asegurémonos de que se actualiza la base de datos mundial completamente:
    
    cat /home/mangos/database/World/Update/(current Release)/*.sql >> /home/mangos/all.sql
    mysql -u root -p mangos < /home/mangos/all.sql
	

Ahora tienes que rellenar las bases de datos. Esto incluye misiones, diálogo, etc.. Hay un script que compilará un número masivo de archivos de sql en un lote grande de sql que se pueden aplicar a la vez.

    cd /home/mangos/database
    bash make_full_WorldDB.sh
    mysql -u root -p mangos < full_db.sql
    
###7. Configuración
Este paso está documentado en la página: [** Files**](Configuration-Files) de configuración

###8. Ejecutando el servidor y crear una cuenta de administrador
Los binarios se ubicará en la carpeta bin del directorio raíz del servidor. Son mangosd realmd.
mangosd es el servidor del mundo y realmd es el servidor del Reino. Normalmente sólo se necesita una instancia de realmd corriendo y una instancia mangosd para cada reino que quieres en tu realmlist.

Si quieres que tu servidor se ejecute en scripts de reinicio automático, entonces usted necesitará copiar los scripts de reinicio de la fuente del servidor.
        
	mv /home/mangos/server/src/tools/restart-scripts/*.sh /home/mangos/zero/
	
Asegúrese de cambiar /home/mangos/zero con tu camino usado y chmod + x cada archivo. Entonces sólo correrán. / realmd y. / mangos en ese directorio.

Tienes que crear tu cuenta y darle privilegios de administrador. Así que si usted ha utilizado los scripts de reinicio automático, usted puede filtrar a mediante:
    
	screen -x mangos
	
Luego de ejecutar estos comandos en los mangos shell de comandos.
    
    account create "username" "password"
    account set gmlevel "username" 3
    
Cuando termines, usted puede separar de la pantalla usando CTRL A+D
Asegúrese de separar de él y no salir de la pantalla.

Eso es todo! Un servidor privado funcional, parcialmente con secuencias de comandos para que usted pueda jugar con. Que te diviertas.
Si usted encuentra cualquier problema con el tutorial, por favor Únete a nuestros foros y explicar el problema.
