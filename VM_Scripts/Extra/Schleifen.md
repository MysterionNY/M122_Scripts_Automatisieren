# Schleifen

## foreach
```bash
#!/usr/bin/env bash
# Für jedes Wort in der Liste …
for w in Apfel Banane Kirsche; do
  echo "Frucht: $w"
done
```

## for
```bash
#!/usr/bin/env bash
# Zähle i von 1 bis 5
for (( i=1; i<=5; i++ )); do
  echo "Durchlauf $i"
done
```

## while
```bash
#!/usr/bin/env bash
# Zähle solange hoch, bis count 3 erreicht
count=1
while [ $count -le 3 ]; do
  echo "Count ist $count"
  ((count++))
done
```