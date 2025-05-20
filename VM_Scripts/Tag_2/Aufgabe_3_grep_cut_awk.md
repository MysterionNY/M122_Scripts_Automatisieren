# Bash Grundlagen VM scripts

## Übung 4 - grep/cut/awk

## Erklärung
### grep
`grep` (Global Regular Expression Print) durchsucht Zeilen einer Datei oder Eingabe nach einem definierten Muster (Pattern) und gibt diejenigen Zeilen aus, die (bzw. nicht) übereinstimmen. Mit Optionen wie `-v` (invert match), `-E` (erweiterte Regex) oder `--color=auto` kann man das Verhalten und die Ausgabedarstellung feinkörnig steuern.

### cut
`cut` teilt jede Eingabezeile anhand eines Trennzeichens (Default Tabulator) in Felder und druckt ausgewählte Feldnummern. Mit `-d` kann man das Delimiter-Zeichen (z. B. `:` oder `,`) einstellen, und mit `-f` legt man fest, welche Felder ausgegeben werden sollen. So lassen sich etwa Spalten aus Protokollen oder CSV-Dateien extrahieren.

### awk
`awk` ist eine kleine Programmiersprache für zeilenweise Text­verarbeitung. Standardmässig trennt `awk` Felder anhand von whitespace, kann aber mit `-F` auf beliebige Delimiter umgestellt werden. Über eingebaute Variablen wie `NF` (Anzahl der Felder) und Positionen (`$1`, `$2`, …, `$NF`) lassen sich komplexe Extraktionen und Berechnungen dynamisch realisieren – z. B. das Auslesen des zweitletzten Felds unabhängig von der Gesamt­anzahl der Separatoren.


### a) Erzeugen Sie eine Textdatei mit folgendem Inhalt
```bash
cat << 'EOF' > datei.txt
alpha1:1alpha1:alp1ha
beta2:2beta:be2ta
gamma3:3gamma:gam3ma
obelix:belixo:xobeli
asterix:sterixa:xasteri
idefix:defixi:ixidef
EOF
```

#### a.1 Alle Zeilen, welche **obelix** enthalten
```bash
grep --color=auto 'obelix' datei.txt
```

#### a.2 Alle Zeilen, welche **2** enthalten
```bash
grep --color=auto '2' datei.txt
```

#### a.3 Alle Zeilen, welche ein **e** enthalten
```bash
grep --color=auto 'e' datei.txt
```

#### a.4 Alle Zeilen, welche **nicht** gamma enthalten
```bash
grep --color=auto -v 'gamma' datei.txt
```

#### a.5 Alle Zeilen, welche **1, 2 oder 3** enthalten (mit `-E`)
```bash
grep --color=auto -E '1|2|3' datei.txt
```

---

### b) Mit `cut` nur bestimmte Felder anzeigen

#### b.1 Alle Begriffe **vor** dem ersten `:`
```bash
cut -d':' -f1 datei.txt
```

#### b.2 Alle Begriffe **zwischen** den beiden `:`
```bash
cut -d':' -f2 datei.txt
```

#### b.3 Alle Begriffe **rechts** des letzten `:`
```bash
cut -d':' -f3 datei.txt
```

---

### c) Mit `awk` das Feld zwischen letztem und zweitletztem `:` dynamisch ausgeben
```bash
awk -F':' '{ print $(NF-1) }' datei.txt
```
