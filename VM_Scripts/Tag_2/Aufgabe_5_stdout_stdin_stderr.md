# Bash Grundlagen VM scripts

## Übung 6 - stdout/stdin/stderr

## Erklärung
### Here-Document (`<<`)
* Mit `<< WORD` leitet man eine feste Zeilenfolge (bis zum Schlusswort `WORD`) über **stdin** an einen Befehl weiter. Hier verwenden wir das, um mit einem einzigen Befehl mehrere Zeilen in eine Datei zu schreiben.
### Standardausgabe (`>`, `>>`)
* `> datei` schreibt die **stdout** eines Befehls in „datei“ und **überschreibt** sie. `>> datei` hängt die **stdout** an das Ende von „datei“ (append), ohne vorhandenen Inhalt zu löschen.
### Standardfehler (`2>`)
* `2> datei` schreibt nur die **stderr** eines Befehls in „datei“.  
### Standard­eingabe
* `wc -w < datei` liest **stdin** aus „datei“ und zählt mit `wc -w` die Wörter.
### Truncation beim gleichen Ziel 
* Wenn man z. B. `cat a.txt > a.txt` schreibt, wird `a.txt` **vor** dem Lesen geleert, sodass am Ende eine leere Datei übrig bleibt.


## a) Textdatei mit Here-Document erzeugen
```bash
cat << 'END' > datei.txt
a
b
c
d
e
END
```

## b) Fehler von `ls -z` in eine Datei umleiten
```bash
ls -z 2> /root/errorsLs.log
```

## c) Ausgabe mit `>` versus `>>` untersuchen
```bash
# 1. Kleine Textdatei erstellen und befüllen
cat << 'EOF' > small.txt
Zeile1
Zeile2
EOF

# 2. Ausgabe nach out.txt mit '>' (überschreibt)
cat small.txt > out.txt
echo "--- Inhalt von out.txt nach '>' ---"
cat out.txt

# 3. Ausgabe nach out.txt mit '>>' (hängt an)
cat small.txt >> out.txt
echo "--- Inhalt von out.txt nach einmal '>>' ---"
cat out.txt

# 4. Nochmals mit '>>' anhängen
cat small.txt >> out.txt
echo "--- Inhalt von out.txt nach zweimal '>>' ---"
cat out.txt

# 5. Umleitung in dieselbe Datei führt zu Leeren (Shell truncates vor Lesen)
cat small.txt > small.txt
echo "--- Inhalt von small.txt nach 'cat small.txt > small.txt' ---"
cat small.txt
```

## d) Ausgabe von `whoami` umleiten
```bash
whoami > info.txt
```

## e) Ausgabe von `id` anhängen
```bash
id >> info.txt
```

## f) Wörter in info.txt zählen mit `wc`
```bash
wc -w < info.txt
```
