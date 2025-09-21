# Kontrollstrukturen: If, Else, Elif und Case (Bash Scripting)

In der Programmierung, insbesondere beim Bash Scripting, dienen Kontrollstrukturen dazu, den Ablauf eines Programms zu steuern. Die **Selektion** (oder **Verzweigung**) ist eine dieser grundlegenden Kontrollstrukturen und erlaubt es, unterschiedliche Anweisungen auszuführen, abhängig davon, ob eine Bedingung erfüllt ist oder nicht.

## 1. Die If-Anweisung

Die `if`-Anweisung führt eine Reihe von Anweisungen nur dann aus, wenn ein **Kommando** erfolgreich war, d.h., wenn es den **Exit-Code 0** (steht für "Wahr" oder Erfolg) zurückgibt.

### Syntax (Grundform)

Die Basisstruktur der `if`-Anweisung sieht wie folgt aus:

```bash
if Kommando
then
  Anweisung 1
  Anweisung 2
fi
```

Wenn das `Kommando` den Exit Code 0 zurückgibt, werden die Anweisungen im `then`-Block ausgeführt; andernfalls wird der `then`-Block übersprungen.

### Beispiel: Einfache If-Prüfung

Im Bash Scripting werden Bedingungen oft mithilfe des eingebauten Kommandos `test` oder der äquivalenten Schreibweise `[ ]` geprüft. Diese Kommandos liefern einen Exit-Code von 0 ("Wahr"), wenn die Bedingung erfüllt ist, und einen Wert un-Code (`$_error`) **nicht** gleich "0" ist.

## 2. If...then...else...fi (Alternative)

Mit `else` kann eine Alternative zur `if`-Bedingung angegeben werden. Die Anweisungen im `else`-Block werden ausgeführt, **nur wenn** der Exit-Code des initialen Kommandos **ungleich 0** ist (d.h., die Bedingung war "Falsch").

### Syntax (mit else)

```bash
if Kommando
then
  Anweisung 1  # Wird ausgeführt, wenn Exit Code = 0
else
  Anweisung 2  # Wird ausgeführt, wenn Exit Code ≠ 0
fi
```

### Beispiel: Zahlen vergleichen

Angenommen, Sie möchten prüfen, ob eine Zahl positiv ist.

```bash
ZAHL=10

if [ $ZAHL -gt 0 ]; then
  echo "Die Zahl ist grösser als 0."
else
  echo "Die Zahl ist 0 oder kleiner."
fi
```

## 3. Elif (Mehrfache Alternative)

Wenn mehr als zwei Alternativen unterschieden werden müssen, kann die `if...then...else...fi`-Struktur mehrfach verschachtelt werden. Eine übersichtlichere Schreibweise dafür ist die Verwendung von `elif` (Else If).

### Syntax (mit elif)

```bash
if Ausdruck1
then
  Kommando1
elif Ausdruck2
then
  Kommando2
else
  Kommando3
fi
Kommando4
```

Wenn der erste Ausdruck (`Ausdruck1`) falsch ist, wird der zweite Ausdruck (`Ausdruck2`) geprüft, und so weiter. Wenn keiner der Ausdrücke wahr ist, wird der Code im optionalen `else`-Block ausgeführt.

### Beispiel: Zwei Zahlen vergleichen

Ein Skript könnte prüfen, ob die erste Zahl kleiner, grösser oder gleich der zweiten Zahl ist:

```bash
ZAHL1=10
ZAHL2=20

if [ $ZAHL1 -lt $ZAHL2 ]; then
  echo "$ZAHL1 ist kleiner als $ZAHL2"
elif [ $ZAHL1 -gt $ZAHL2 ]; then
  echo "$ZAHL1 ist grösser als $ZAHL2"
else
  echo "$ZAHL1 ist gleich $ZAHL2"
fi
```

## 4. Case (Mehrfach-Fallunterscheidung)

Die `case`-Anweisung ist eine weitere Kontrollstruktur, die sich ideal für **Mehrfachauswahlen** eignet, insbesondere wenn verschachtelte `if`-Anweisungen schnell unübersichtlich werden würden. Sie vergleicht den Inhalt einer Variablen mit verschiedenen Mustern (`Muster`).

### Syntax

```bash
case $variable in
  *Muster 1)
    Aktionen 1
    ;;
  *Muster 2)
    Aktionen 2
    ;;
  *)
    Default-Aktionen
    ;;
esac
```

Wenn der Inhalt der Variablen mit einem der Muster übereinstimmt, werden die entsprechenden Aktionen ausgeführt. Anschließend springt der Programmfluss zu den Anweisungen nach `esac`.

Wichtig:
*   Jeder Fall endet mit doppelten Semikolons (`;;`).
*   Das Muster `*)` fängt alle Fälle ab, bei denen keines der vorhergehenden Muster gepasst hat (Default-Aktionen).
*   Es können auch Alternativen innerhalb eines Falls formuliert werden (z.B. `a|-a|--all)`).

### Beispiel: Optionenauswertung

Dieses Beispiel zeigt, wie mit `case` eine Kommandozeilenoption (hier: `$opt`) verarbeitet werden kann, wobei auch alternative Schreibweisen für die Option akzeptiert werden können:

```bash
opt=$1

case "$opt" in
  a|-a|--all)
    echo Alle Dateien werden verarbeitet
    ;;
  n|-n|--new)
    echo Nur neue Dateien werden verarbeitet
    ;;
  *)
    echo "$opt: ungültige Option"
    ;;
esac
```
Hier werden für den Fall "alle Dateien" die Optionen `a`, `-a` oder `--all` akzeptiert.

Ein weiteres Beispiel zeigt die Verarbeitung von Benutzereingaben, wobei Groß- und Kleinschreibung berücksichtigt wird:

```bash
# Beispiel: Antwort auswerten
antwort="Ja"
case "$antwort" in
  [jJ] | [jJ][aA])         # Prüft auf 'j' oder 'J', sowie 'ja' oder 'JA'
    echo "JA!"
    ;;
  [nN] | [nN][eE][iI][nN]) # Prüft auf 'n' oder 'N', sowie 'nein' oder 'NEIN'
    echo "Nein!"
    ;;
  *)
    echo "[ja] oder [nein] eingeben"
esac
```
In diesem Beispiel wurden Alternativen für die Muster in den `case`-Anweisungen verwendet.