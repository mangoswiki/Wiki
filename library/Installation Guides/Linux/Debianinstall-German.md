[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 
· Other Versions(old): [**English**](/wiki/Installation%20Guides/Linux/Debianinstall.md)  [**Español**](/wiki/Installation%20Guides/Linux/Debianinstall-spanish.md)

----------

Dieses Handbuch richtet sich an alle Debian-basierten Distributionen.

##Intro
Diese Anleitung ist für diejenigen, die würde es vorziehen, die hervorragende Stabilität und Ressourcen-Management von Linux zu verwenden, oder kann nicht benutzen Sie einfach Windows aus verschiedenen Gründen.
Während im aktuelle Linux-klebrige-Handbuch eine große Quelle der Informationen ist, gibt es einige Nuancen, die es zu Erwähnungen auftritt und dieses Threads soll
die Adresse. In diesem Handbuch werden weitgehend ähneln, aber werden hoffentlich mehr up to date mit ein paar Änderungen in den Repositories. In diesem Handbuch
ist mit der Anfänger im Auge, und als solche kann das offensichtliche gelegentlich besagen.

Hinweis: Wenn Sie Teilmodule mit Ihrem Server verwenden möchten, können Sie aktivieren oder deaktivieren sie während der Cmake-Schritt durch Hinzufügen des folgenden bevor Sie das Präfix:
(0 = deaktiviert 1 = aktiviert)
    
    -DBUILDTOOLS = 1 - auf die Extraktion Buildtools
    -DENABLE_LIB_SD2 = 1 - SD2 aktivieren
    -DENABLE_LIB_ELUNA = 1 - Eluna aktivieren
    -DSOAP = 1 - SOAP aktivieren
    
###1. Holen die Abhängigkeiten.
Mangos braucht eine kleine Anzahl von Paketen zu kompilieren und die ordnungsgemäß ausgeführt. Diese ist leicht mit einer einfachen Anwendung von apt Paketmanager. Führen Sie einfach die folgende Zeile als super User:

    sudo apt-get update
    sudo apt-get install cmake cmake-qt-gui git g++ gcc make libace-ssl-dev libace-dev libbz2-dev libmysql++-dev libmysqlclient-dev libssl-dev
    sudo apt-get install mysql-client mysql-common mysql-server zlib1g-dev vim autoconf libtool screen bash
    
MySQL-Server läuft einen kurze und einfache Installation-Daemon für sich und fordern Sie ein Root-Passwort unter anderem. Achten Sie darauf, es zu merken.

###2. Die Mangos-Benutzer (nicht optional)
Sie müssen einen neuen Benutzer mit dem Ihr Mangos Server ausgeführt, auf erstellen. Es wird nicht empfohlen, führen Sie den Server (und eine Menge anderer Dinge) als Root.
Wir werden verwenden Sie den Benutzernamen "Mangos" ein Beispiel, können Sie den gewünschten Benutzernamen, aber du brauchst Mangos mit Ihrem Benutzernamen in allen Pfaden zu ersetzen.
    
    adduser mangos
    
Dies erstellt einen neuen Benutzer mit dem Namen Mangos unter dem Ordner /home/mangos standardmäßig.
Wenn Sie Ihre private Server in einem anderen Ordner ausführen möchten, stellen Sie sicher, Ihre Benutzerberechtigungen für diesen Ordner geben.
Beispiel:
    
    chown -R mangos:mangos /path/to/folder
    
Und wenn Sie fertig sind festlegen, dass auf, du wirst an den Benutzer zu wechseln, so dass wir den Installationsvorgang zu starten können.
    
    su - mangos
    
###3. Erste Mangos-Quelle
Es gibt mehrere Mangos-Versionen zur Auswahl.

Dieses Handbuch wird MaNGOS Zero(classic) als Beispiel verwenden. Wenn Sie eine andere Version verwenden, können Sie einfach nur die Klonen URL auf die Version ändern möchten.
Dieser Schritt ist auf der Seite dokumentiert: [** Klonen der Repos**](/wiki/Installation%20Guides/General/Cloning%20the%20Repos.md)

Stellen Sie sicher, dass Sie in den richtigen Ordner und dann zu holen, die Server, die Datenbank und die Extras.
    
    git clone --recursive https://github.com/mangoszero/server.git
    git clone --recursive https://github.com/mangoszero/database.git
    
###4. Kompilieren die Server-Datenquelle
Jetzt erstellen Sie das Build-Verzeichnis im Serverordner. Beachten Sie, dass ~ / ist ein relativer Pfad zum home-Verzeichnis des aktuellen Benutzers.
    
    cd ~/server
    mkdir build
    cd build
    
Bauen Sie den Server angeben, wo es um nach dem Kompilieren installiert wird. Dies kann einige Minuten dauern. Beachten Sie, dass "... / "ist eine Konstante für das übergeordnete Verzeichnis.
Das Präfix-Argument gibt an, in dem der Server installiert wird. Ändern Sie es entsprechend.

    cmake ../ -DCMAKE_INSTALL_PREFIX=/home/mangos/zero
	
Dann fangen wir kompilieren. Wenn Sie mehr als 1 CPU-Kern haben, kompilieren Sie schneller durch die Zugabe von Kernen in die Kompilierung verwenden möchten. Sie können tun
Dies indem Sie hinzufügen -j# auf die Fabrikmarke Befehl. IE: make -j 4
    
    make
    make install
    

###5. Die game-Elemente extrahieren
Dieser Schritt ist auf der Seite dokumentiert: [** extrahieren Spiel Assets**](Extracting-Game-Assets)

###6. Importieren der MySQL-Datenbank
Jetzt können wir die Datenbanken für Mangos, Realmd und Zeichen importieren. Dies kann leicht durch Mysql über das ROOT-Passwort, das zuvor eingerichtet wurde.
    
    mysql -u root -p realmd < /home/mangos/database/Realm/Setup/realmdCreateDB.sql
    mysql -u root -p realmd < /home/mangos/database/Realm/Setup/realmdLoadDB.sql
    mysql -u root -p characters < /home/mangos/database/Character/Setup/characterCreateDB.sql
    mysql -u root -p characters < /home/mangos/database/Character/Setup/characterLoadDB.sql
    mysql -u root -p mangos < /home/mangos/database/World/Setup/mangosdCreateDB.sql
    mysql -u root -p mangos < /home/mangos/database/World/Setup/mangosdLoadDB.sql
    
Wir stellen sicher, dass die Welt-Datenbank vollständig aktualisiert wird:
    
    cat /home/mangos/database/World/Update/(current Release)/*.sql >> /home/mangos/all.sql
    mysql -u root -p mangos < /home/mangos/all.sql
	

Jetzt müssen Sie die Datenbanken zu füllen. Dazu gehören, Charaktere, Dialog, etc.. Es gibt eine Skript, die eine massive Anzahl von Sql-Dateien in eine große Sql-Batch kompiliert wird, die Sie sofort anwenden können.
    cd /home/mangos/database
    bash make_full_WorldDB.sh
    mysql -u root -p mangos < full_db.sql
    
###7. Konfiguration
Dieser Schritt ist auf der Seite dokumentiert: [** Konfiguration Files**](Configuration-Files)

###8. Der Server ausgeführt wird und ein Administratorkonto erstellen
Ihre Binärdateien werden im Binärordner des Root-Verzeichnis des Servers befinden. Das sind die Mangosd Realmd.
Mangosd ist der Welt-Server und Realmd ist der Realm-Server. In der Regel brauchen Sie nur eine Instanz des Realmd ausgeführt, und eine Mangosd-Instanz für jeden Bereich in Ihre Realmlist gewünschte.

Wenn Sie Ihren Server auf Auto-Neustart-Skripts ausführen möchten, müssen Sie den Neustart-Skripts aus dem Server-Datenquelle zu kopieren.
        
	mv /home/mangos/server/src/tools/restart-scripts/*.sh /home/mangos/zero/
	
Achten Sie darauf, dass Sie /home/mangos/zero mit Ihrem verwendeten Pfad und Chmod + x jede Datei zu ändern. Dann Sie einfach läuft. / Realmd und. / Mangos in diesem Verzeichnis.

Sie müssen Ihr Konto zu erstellen und geben sie Admin-Privilegien. Also wenn Sie die Auto-Restart-Skripts verwendet, können Sie es mit Bildschirm:
    
	screen -x mangos
	
Führen Sie diese Befehle in die Mangos-Befehlsshell.
    
    account create "username" "password"
    account set gmlevel "username" 3
    
Nachdem Sie fertig sind, können Sie den Bildschirm mit STRG A + D trennen
Achten Sie Sie getrennt von ihm und verlassen Sie nicht die.

Das ist es! Eine funktionelle, teilweise skriptgesteuerte Privatserver für Sie mit. Viel Spass.
Wenn Sie irgendwelche Probleme mit dem Tutorial stoßen, bitte Foren Sie unsere und erklären Sie das Problem.
