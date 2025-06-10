# Shell Aufgaben Teil 1

## Aufgabenblock 1
1.  Erzeugt Benutzer anhand einer Liste von Benutzernamen in einer
     Textdatei (via Parameter angegebenen).
     Hinweis: Benutzen Sie `useradd` und `cat`.

2.  Fügt einen Benutzer anhand einer Liste von Gruppen in einer
     Textdatei (via Parameter angegebenen) den jeweiligen Gruppen
     hinzu.
     Hinweis: Benutzen Sie `groupadd` , `usermod` und `cat`. Achtung es gibt für jeden Benutzer jeweils eine `Initial login group` und mehrere `Supplementary groups`.

3.  Findet alle Dateien, welche einem (via Parameter angegebenen)
     Benutzer gehören und kopiert diese an den aktuellen Ort. Die
     kopierten Dateien werden zu einem `tar.gz` Archiv zusammengefasst
     und danach gelöscht. Die Archivdatei wird mit dem Benutzernamen
     und dem aktuellen Datum benannt.
     Hinweis: Benutzen Sie `find`, `tar`, `rm` und `date`.

4.  Ermittelt die eigene IP-Adresse und macht einen PING-Sweep für das
     Subnetz der eigenen IP. Gibt aus, welche Hosts up sind und
     speichert die IP-Adressen der Hosts in einer Textdatei.
     Hinweis: Benutzen Sie `ping` (oder `fping`), `ifconfig` und
     `grep`.

5.  Challenge für Profis: Ermittelt die Events der Stadt Zürich für das aktuellen Datum von
     [www.eventkalender.ch](https://www.eventkalender.ch).  Evtl. suchen Sie in einer bestimmten Kategorie: https://www.eventkalender.ch/konzerte-musicals-shows.cfm?kat=1 <br> Erweitern Sie das Skript danach auf beliebige Städte und die Angabe eines Datums (wenn kein
     Datum angegeben wird, wird das aktuelle angewendet).
     
     Hinweis: Benutzen Sie `curl`, `grep` und `cut`.

## Erklärung

## Lösung
### Aufgabe 1