 # dateisystem
* `ls -la /`
* everything is a file
* symlinks
* /tmp => temporäre dateien, werden nach dem neustarten resettet.
* /mnt => verzeichnis, wo USB-Sticks eingehängt werden.
* /etc => optionen / einstellungsdateien
* /var => variable dateien wie logs und warteschlangen für z.B. drucker 
* /bin => binäre / ausführbare dateien
* /sbin => auch ausführbare dateien
* /usr => tools, bibliotheken und installierten programme, damals gab es kein /home, da war alles in /usr.
* /lib => bibliotheken
* /lib64 => auch bibliotheken
* usr-merge
* /boot => dateien & programme, die zum hochfahren gebraucht werden. z.B. grub, grub.cfg
* /sys => low-level software, z.b. firmware, kernel info
* /run => 
* /proc => laufende prozesse
* /opt => optionale programme, hier können vom nutzer installierte programme hin getan werden.
* /lost+found
* /root => home-verzeichniss für den root user. falls die /home partition ausfällt, kann hierrauf zurückgewiesen werden, um es zu reparieren.
* /home => verzeichnis, wo die nutzer ihre unterverzeichnisse haben, wo sie ihre dateien speichern können.
* /dev => hardware wird hier gelistet, wie partitionen, cpu, ram, aber auch etwas wie:
  * /dev/null
  * /dev/random
* . => das jetzige verzeichnis, in dem sich der user befindet
* .. => das darüberliegende verzeichnis vom nutzer aus
* . am anfang eines dateinamens oder verzeichnisses. => versteckt, wird nur angezeigt, wenn es der nutzer auch will.

# Pipes und andere Operatoren
* "|": output von einem programm in ein anderes übertragen
    * z.b.: `lsblk | grep nvme`
* ">": output eines Programmes in eine datei oder anderes Program legen.
    * z.B.: `echo $RANDOM > /tmp/test` 
* ">>": output eines Programmes an eine datei oder den output eines anderen Programmes anhängen
    * z.B.: `genfstab -U /mnt >> /mnt/etc/fstab`
* ">>>": appendiert output eines Programmes an eine Datei oder den Output eines anderen Programmes. Hier auch Errors und Warnungen, die bei ">>" in stdout gelegt werden.
    * z.B.: `grub-mkconfig >>> /boot/grub.cfg`
* ";": abtrennung, dass 2 Programme in einer Zeile ausgeführt werden können
    * z.B.: `mkdir /tmp/testdir ; cd /tmp/testdir`
* "&&": das gleiche wie ";".
    * z.B.: `mkdir /tmp/testdir2 && cd /tmp/testdir`
* "&": verschiebt das ausgeführte Programm in den Hintergrund.
  * z.B.: `firefox &`
    
# Permissions

* besteht aus 4 teilen
    * drwxrwxrwx
    * r steht für read (lesen)
    * w steht für write (schreiben)
    * x steht für execute (ausführen)

* erstes zeichen
    * d => kurz für directory, also verzeichnis  
    * - => einfache datei
    * l => ein symlink z.b.: /bin/sh
        
* die anderen teile
    * wenn es eine datei ist
        * teil 1 ist für den besitzer der datei
        * teil 2 ist für die Gruppe des besitzers der datei
        * teli 3 ist für alle anderen (auch others oder world genannt)
    * wenn es ein dir ist
        * x bedeutet dann, dass der user das verzeichnis zum working-dir machen kann
