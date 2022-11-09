---
title: Einstieg in Linux
theme:Nord
---

# Einstieg in Linux
### von Thomas Z. und Finn Lasse S.

---

## Dateisystem

---

### "Everything is a file"
"Alles ist eine Datei"
* /dev/cpu/X <!-- .element: class="fragment" data-fragment-index="1" -->
* /dev/sda <!-- .element: class="fragment" data-fragment-index="2" -->
* /dev/tty <!-- .element: class="fragment" data-fragment-index="3" -->
* /usr/bin/init <!-- .element: class="fragment" data-fragment-index="4" -->


---

### Symbolic links
Equivalent zu "Shortcuts" in Windows.
* /bin/sh <!-- .element: class="fragment" data-fragment-index="1" -->
* /usr/bin/shutdown <!-- .element: class="fragment" data-fragment-index="2" -->
* usr-merge <!-- .element: class="fragment" data-fragment-index="3" -->

---

### /tmp, /var, /etc, /opt
* /tmp sind temporäre Dateien, die beim neustarten gelöscht werden z.B. /tmp/systemd-* <!-- .element: class="fragment" data-fragment-index="1" -->
* /var sind variable dateien, die sich ändern können. z.B. /var/mail <!-- .element: class="fragment" data-fragment-index="2" -->
* /etc sind editierbare Dateien für konfigurationen z.B. /etc/fstab <!-- .element: class="fragment" data-fragment-index="3" -->

---

### /mnt, /root, /home
* auf /mnt werden manuell Partitionen eingebunden (mit dem mount-Programm) <!-- .element: class="fragment" data-fragment-index="1" -->
* in /root liegen Dateien, die nur für den root user wichtig sind. <!-- .element: class="fragment" data-fragment-index="2" -->
* in /home haben die Nutzer ihre persönlichen Verzeichnisse <!-- .element: class="fragment" data-fragment-index="3" -->

---

### /bin, /sbin, /lib, /lib64, /usr & usr-merge
* /in /bin liegen Programme, wie die, worüber wir später sprechen werden <!-- .element: class="fragment" data-fragment-index="1" -->
* in /sbin liegen systemwichtige Programme, z.B. (ehemalig) init <!-- .element: class="fragment" data-fragment-index="2" -->
* /lib und /lib64 sind verantwortlich für bibliotheken, meist in der Form von shared-objects. /lib64 für 64 bit <!-- .element: class="fragment" data-fragment-index="3" -->
* /usr war mal /home, weshalb dort Programme liegen, die von Nutzern ausgeführt werden sollen <!-- .element: class="fragment" data-fragment-index="4" -->
* usr-merge
    * mit Symbolic links
    * /lib64 -> /usr/lib <!-- .element: class="fragment" data-fragment-index="1" -->
    * /lib -> /usr/lib <!-- .element: class="fragment" data-fragment-index="2" -->
    * /bin -> /usr/bin <!-- .element: class="fragment" data-fragment-index="3" -->
    * /sbin -> /usr/bin <!-- .element: class="fragment" data-fragment-index="4" -->

---

### /boot, /sys, /proc
* /boot ist eine 2. Partition. Dort liegen Dateien zum hochfahren vom Rechner <!-- .element: class="fragment" data-fragment-index="1" -->
* /sys ist besetzt von low-level software, wie firmware von UEFI. <!-- .element: class="fragment" data-fragment-index="2" -->
* Dateien in /proc beschreiben die laufenden Prozesse. Aus diesen Dateien können informationen über diese gelesen weden. z.B. /proc/cpuinfo <!-- .element: class="fragment" data-fragment-index="3" -->

---

### /lost+found, /dev
* lost+found ist ein Teil von dem ext4-Dateisystem <!-- .element: class="fragment" data-fragment-index="1" -->
* /dev beinhaltet Physische Geräte, wie schon bei "Everything is a file" erklärt <!-- .element: class="fragment" data-fragment-index="2" -->

---

## Permissions
* Charakter-Reihe aus 4 Teilen
    * 1. Buchstabe bestimmt, was für eine Datei das ist.
        * d -> directory, Verzeichnis, Ordner
        * - -> Editierbare Datei
        * l -> Symlink
    * rwx
        * r -> read, lesen
        * w -> write, schreiben, bearbeiten
        * x -> execute, ausführen
        * s/t -> sticky, es kann hinzugefügt werden, aber nicht weggenommen werden (dir)
    * Teil 1 bestimmt was der Besitzer mit der Datei machen kann
    * Teil 2 bestimmt was die Gruppe des Besitzers machen kann
    * Teil 3 bestimmt was der Rest der Nutzer damit machen kann.
    
    * Besonderheiten bei Ordnern
        * x -> der Ordner kann zum working-directory gemacht werden        
        * das x kann mit s oder t ersetzt werden (sticky -> dateien hinzufügen, nicht wegnehmen)
                
---

## Pipes & Trennungen


