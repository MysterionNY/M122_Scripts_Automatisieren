# Bash Grundlagen VM scripts

## Übung 3 - Tilde Extension

## Erklärung
Der Sinn hinter der Tilde '~' liegt darin eine abgekürzte Variante zu schaffen, welche zum Home Verzeichnis des Benutzers führt, also: /home/benutzer. Dabei hat sie unterschiedliche Verwendungsmöglichkeiten und entspricht dann für unterschiedliche Verwendungen.

### ~ --- ohne nichts (Bringt dich ins Home Verzeichnis zurück)
```bash
cd ~
```

### ~/... --- Wechselt ins Docs file relativ zum Pfad des Home Verzeichnis, also: /home/benutzer/Docs
```bash
cd ~/Docs
```

### ~username --- Gibt die Inhaltsverzeichnise vom Home Pfad eines anderen users aus
```bash
ls ~root
```

## Anwendungsbeispiel um zu sehen wie Tilde funktioniert
```bash
mert@m122:~$ cd /
mert@m122:/$ pwd
/
mert@m122:/$ cd ~
mert@m122:~$ pwd
/home/mert
mert@m122:~$
```