[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 
· Other Versions:  [**English**](/wiki/Installation%20Guides/Linux/Debianinstall.md) [**Español**](/wiki/Installation%20Guides/Linux/Debianinstall-spanish.md)

----------

Diese Anleitung ist für Debian-basierte Distributionen. Sie kann als Referenz für andere Distributionen verwendet werden, einzelne Schritte können abweichen. Der einzige Unterschied sollte allerdings der sein, die erforderlichen Pakete zusammen zu bekommen.

## Intro
Diese Anleitung ist für diejenigen, die es vorziehen, die überlegene Stabilität und das Ressourcenmanagement von Linux zu verwenden. Diese Anleitung ist für Anfänger geschrieben, es setzt keine MaNGOS Kenntnisse voraus, daher werden auch Schritte beschrieben die für fortgeschrittene Nutzer offensichtlich erscheinen.

### 1. Das Abholen der Abhängigkeiten.
Mangos benötigt einige Anwendungen um korrekt kompilieren und laufen zu können. Diese zu installieren ist dank dem Paketmanager apt einfach. Es muss nur folgende Zeile als super user ausgeführt werden:

    apt-get install build-essential gcc g++ automake git-core autoconf make patch libmysql++-dev mysql-server libtool libssl-dev grep binutils zlibc libc6 libbz2-dev cmake

Der mysql-server wird eine eigene kurze Installationsroutine starten in der man ein Passwort vergeben muss. Dieses unbedingt merken!

Falls das herunterladen der Paket fehlschlägt versuche **sudo apt-get update** um die lokalen Repositories auf den neuesten Stand zu bringen. Falls es dann immer noch nicht klappt, fehlt eines der Pakete oder trägt einen anderen Namen. Falls das der Fall ist sollte man versuchen es über den Befehl **apt-cache search** *Paketname* (funktioniert auch ohne Root-Privilegien) zu suchen, und unter dem aktuellen Namen installieren.

### 2. Der Mangos Benutzer (Optional)
Optional kann ein Benutzer angelegt werden unter dem Mangos läuft. Es wird nicht empfohlen, den Server (und viele andere Dinge) als root ausführen.

    adduser mangos

Und folgen Sie den Anweisungen. Ein schnellerer, und weniger ausführlicher Weg dies zu tun ist:

    useradd -m mangos
    passwd mangos

Dies schafft einen neuen Benutzer mit dem Namen Mangos der die vollen Besitzer-Berechtigungen des Verzeichnisses /home/mangos besitzt. Von diesem Verzeichnis wird der Server später ausgeführt. Falls der Server später in einem anderen Verzeichnis liegen soll, müssen dem neu angelegten Benutzer die Besitzrechte für diesen Ordner gegeben werden:

    chown /pfad/zum/anderen/ordner mangos

Sobald dies erledigt ist wird in den neu angelegten Benutzer gewechselt:

    su mangos


### 3. Herunterladen des MaNGOS Codes
Es gibt eine Menge von Mangos Varianten zur Auswahl.

Diese Anleitung verwendet die aktuellste MaNGOS Version (für Cataclysm), funktioniert aber auch für alle anderen MaNGOS Versionen. Für andere Versionen muss lediglich der github-Pfad angepasst werden, Bspl: Zero (WoW 1.12.x): http://github.com/mangoszero/[...].

Nach dem wechseln in den richtigen Order (Home-Verzeichnis oder dem eigens angelegt Ordner) wird der Server-, der Datenbank- und ScriptDev2-Code heruntergeladen. ScriptDev2 wird dabei in server/src/bindings geladen:

    git clone --recursive http://github.com/mangosthree/server.git
    git clone --recursive http://github.com/mangosthree/database.git

### 4. Kompilieren des Servers

Anschließend muss der Ordner erstellt werden in den das Projekt "erstellt" wird. _Bitte beachten: ~/ ist der relative Pfad zum aktuellen Benutzer-Verzeichnis._

    cd ~/server
    mkdir build
    cd build

Nun wird der Server kompiliert und installiert. Dies dauert in der Regel etwa 5 Minuten. _Beachten: dass ".." ist eine Konstante für das übergeordnete Verzeichnis. "cmake .." in /home/Mangos/server/build ist das selbe wie "cmake" in /home/Mangos/server._ Das -DPREFIX= Argument gibt an, wo der Server installiert werden soll. Es muss entsprechend geärndert werden.

    cmake .. -DPREFIX=/home/mangos/
    make
    make install

### 5. Extrahieren der Game-Elemente
Nun muss im Ausgangs-Verzeichnis (in diesem Fall /home/mangos/), einen Ordner für die Client-Dateien erstellt werden. Er kann frei benannt werden. Hier wird der Verzeichnisname "data" verwendet. Zusätzlich muss ein Verzeichnis für die logs erstellt werden (in diesem Fall "logs"):

    mkdir data
    mkdir logs

Anschließend werden die inhalte der .MPQ-Dateien des Orginal-Clients extrahiert.

#### Extrahieren unter Linux
---

_Eine deutsche Übersetzung ist in Arbeit, solange müssen sich deutsche Benutzer leider mit der englischen Anleitung begnügen:http://github.com/mangoswiki/Wiki/wiki/Extracting-Game-Assets_ 

#### Unter Windows
---
Verschiebe nun die Dateien aus dem Ordner server/contrib/extractor_binary in das WoW Client-Verzeichnis auf einem Windows-Rechner.

Rufe nun den ausführen Dialog mit der Tastenkombination Windows+R auf, gebe in das aufgegange Fenster cmd  ein und starte die Komandozeile mit Shift + Strg + Enter als Administrator. Navigieren in das WoW-Verzeichnis, und rufe dort die Programme:

    ad.exe
    vmapExtractor.exe
    vmap_assembler.exe buildings VMAPs

nacheinander auf.
Nun müssen die von den Programmen angelegten Verzeichnisse "dbc", "maps" und "vmaps" in das vorhin angelegte "data"-Verzeichnis auf dem Linux-System kopiert werden.

### 6. SQL-Batch magic
MaNGOS speichert millionen Dinge in der SQL-Datenbank. Um die dafür nötige Struktur in der Datenbank anzulegen werden einige SQL-Skripte mitgegeben. Dabei wird der Befehl "mysql -u root -p" einige Male verwendet. _Der Parameter -u root steht für die verwendung des DB-Benutzers "root", der Parameter -p gibt an das ein Passwort verwendet wird (es kann auch direkt mit -p[Passwort] angegeben werden)._

Die .sql-Dateien würde könnten auch mit grafischen Anwendung wie phpmyadmin oder Navicat importiert werden, in dieser Anleitung wird aber die Kommandozeile verwendet.

Begonnen wird mit den Dateien in server/sql. Damit werden die Tabellen-Strukturen der drei MaNGOS-Anwendungen erstellt.

    cd /home/mangos/server/sql
    mysql -u root -p < create_mysql.sql
    mysql -u root -p realmd < realmd.sql
    mysql -u root -p characters < characters.sql
    mysql -u root -p mangos < mangos.sql

ScriptDev2 benötigt seine eigene Datenbank:

    cd /home/mangos/server/src/bindings/scripts/sql
    mysql -u root -p < scriptdev2_create_database.sql
    mysql -u root -p scriptdev2 < scriptdev2_create_structure_mysql.sql
    mysql -u root -p scriptdev2 < scriptdev2_script_full.sql

Nun müssen die Datenbanken noch gefüllt werden (Quests, Dialoge, etc). Um die vielen kleinen SQL-Dateien zusammenzuführen muss ein Skript ausgeführt werden, die enstandene große SQL-Datei kann dann importiert werden:

    cd /home/mangos/database
    bash make_full_db.sh
    mysql -u root -p mangos < full_db.sql

Es kann sein dass zwischenzeitlich einige Veränderungen eingeführt wurden ohne die der world-server nicht läuft. Falls der Server später also nicht startet und SQL-Fehler meldet müssen vermutlich Updates eingespielt werden, dies geschieht mit den Befehlen:

    cd /home/mangos/server/sql/updates
    mysql -u root -p mangos < blahblahblah_mangos_whatever.sql

_Beachte "mangos" ist hier nicht das Passwort des root-Benutzers sondern der Datenbank-Name!_
Der Vorgang sollte für alle SQL-Dateien wiederholt werden die [...]_mangos_[...].sql benannt sind!

### 7. Konfiguration
Um den Server zu konfigurieren, müssen ein paar Textdateien und ein paar Datenbank-Einträge bearbeitet werden. Ich empfehle für letzteres einen grafischen SQL-Client wie phpmyadmin, Navicat(Windows) oder emma(Linux). Kopieren Sie zunächst die Standard-Konfigurationsdateien die erstellt wurden:

    cd /home/mangos/etc
    cp realmd.conf.dist realmd.conf
    cp mangosd.conf.dist mangosd.conf
    cp scriptdev2.conf.dist scriptdev2.conf

Der Minimal-Aufwand für einen lauffähigen Server ist, die folgenden Zeilen in der Datei mangosd.conf anzupassen:

    DataDir = "/home/mangos/data"
    LogsDir = "/home/mangos/logs"

Natürlich sollte man alle drei Konfigurationsdateien bearbeiten, sie sind kommentiert und meist selbsterklärend.

Nun muss mit einem SQL-Client die Tabelle "realmlist" in der Datenbank "realmd" angepasst werden. Das Feld "address" muss geändert werden und zwar in den Wert unter dem der Realm VON AUSSEN erreichbar ist (damit ist NICHT der localhost 127.0.0.1 gemeint, sondern die "echte" IP-Adresse.).

###8. Ausführen des Servers und erstellen eines Admin-Kontos
Die Binärdateien befinden sich im Verzeichnis "bin" ihres Root-Verzeichnisses. Es sind die Dateien mangosd und realmd.

mangosd ist die "Welt"-Server und realmd ist der Realm-Server. Normalerweise benötigt man nur eine Instanz von realmd, allerdings eine mangosd-Instanz für jeden Realm der sich in der Tabelle "realmlist" befindet.

Die Server können mit der Software "screen" ausgeführt werden um auch nach dem abmelden des Benutzers weiter zu funktionieren. Hierfür kann dieses Skript (mit freundlicher Genehmigung von Krampf) verwendet werden: _Falls sich screen nicht auf ihrem System befindet kann es mit dem Befehl apt-get install screen (als root) nachinstalliert werden._

    #!/bin/sh
    cd /home/mangos/bin
    screen -A -m -d -S mangosworld ./mangosd

    #!/bin/sh
    cd /home/mangos/bin
    screen -A -m -d -S mangosrealm ./realmd

Zu Begin muss mangosd allerdings einmal manuell ausgeführt werden (mit: ./mangosd) um einen ersten Account zu erstellen und diesem Administrator-Berechtigungen zu geben. Dafür gibt man nach ausführen von mangosd in der MaNGOS-Shell (mangos>) die Befehle:

    account create "username" "password"
    account set gmlevel "username" 3

ein. Anschließend kann der Server wieder mit Strg.+C beendet werden.

Nun ist es geschafft, ein fertiger Privatserver zum damit rumspielen ist erstellt! Viel Spaß damit!

Übersetztung der Orginal-Anleitung: http://github.com/mangoswiki/wiki/wiki/Debianinstall
