# Zusammenfassung für die Prüfung: IT-Betrieb und -Monitoring mit Bash Scripting (BMBS.TA1A)

Das Fach "IT-Betrieb und -Monitoring mit Bash Scripting (BMBS.TA1A)" vermittelt grundlegende Kenntnisse der Shell-Programmierung zur **Automatisierung von Aufgaben im IT-Betrieb und -Monitoring**. Dies ist eine wesentliche Aufgabe im Arbeitsfeld und wird durch Ansätze wie «Infrastructure as Code» in Zukunft immer wichtiger. Der Kurs konzentriert sich auf die Nutzung der Scriptmöglichkeiten der Bash, kombiniert mit typischen Linux-Kommandos zur Systemverwaltung. Das Ziel ist es, von der Anforderung zum Entwurf und vom Entwurf zum getesteten Programm zu gelangen.

Das Fach setzt Kenntnisse aus "IT-System-Grundlagen (ITGL)" voraus und wird auf dem **Kompetenzniveau 3 ("Advanced", professionelles Handeln)** unterrichtet, wobei die Absolventen in der Lage sein sollen, komplexe Aufgaben in einem unvorhersehbaren Arbeitskontext autonom zu bearbeiten.

## 1. Kursstruktur und Ablauf

Der Kurs ist in **acht Blöcke** gegliedert, die jeweils Präsenzunterricht (40 Lektionen) und Selbststudium (50 Lektionen für Selfstudy und Transfer) umfassen. Die Blöcke decken folgende Hauptthemen ab:

*   **Block 1: Grundlagen "Handwerkszeug"** – Prozesse, Variablen, Parameter, Shell-I/O.
*   **Block 2: Kontrollstrukturen 1, Algorithmen, Versionierung** – if-Anweisung, `test`, Berechnungen.
*   **Block 3: Kontrollstrukturen 2, Algorithmen, Test, Debugging** – Schleifen (`while`, `for`, `until`), `read`, `printf`.
*   **Block 4: Kontrollstrukturen 4, Datenstrukturen, Funktionen** – `case`, `getopts`, `select`, Funktionen.
*   **Block 5: Modularisierung, Test-Automatisierung** – Arrays (indiziert, assoziativ), Fallstudie.
*   **Block 6: Fallstudie Anwendung (Gruppenarbeit)** – Grundlagen des Testens, Testautomatisierung.
*   **Block 7: Fortgeschrittene Techniken** – Prozesse, Pipes, Signale, dynamische Anweisungen (`eval`).
*   **Block 8: Fallstudie Anwendung (Gruppenarbeit)** – Prüfungsvorbereitung, fortgeschrittene Themen.

Als **Lehrmittel** wird "Shell-Programmierung Das umfassende Handbuch von Stefan Kania, Jürgen Wolf" (6. Auflage 2019, Rheinwerk Verlag) empfohlen. Aufgaben und Lösungsvorschläge sind auf einem **GitHub-Repository** verfügbar. Ein eigenes Notebook mit VMs ist als Hilfsmittel notwendig.

## 2. Modulprüfung

Die Modulprüfung dauert **120 Minuten** und erfordert das **Lösen praktischer Aufgabenstellungen**, deren Lösungen als Scripte abzugeben sind. Die Bewertung erfolgt nach folgenden Kriterien:

*   **Lösung funktioniert**: Volle Punktzahl.
*   **Lösung funktioniert nicht oder nur teilweise**: Teilpunkte können bei richtigem Lösungsansatz erzielt werden.
*   **Lösung funktioniert nicht und kein richtiger Lösungsansatz erkennbar**: Keine Punkte.

Die Prüfung umfasst Kompetenzen aus den Fächern ITGL (IT-System-Grundlagen) und BMBS.

## 3. Kernkonzepte der Bash-Script-Programmierung

### Scriptausführung

*   Ein Script beginnt oft mit einem speziellen Kommentar, dem **Shebang** (`#!/bin/bash`), der angibt, welcher Interpreter für die Ausführung verwendet werden soll. Hier könnte auch etwas anderes stehen, z.B. `#!/bin/sh` oder `#!/usr/bin/python3`.
*   **Vier Arten der Ausführung**:
    1.  `bash scriptname.sh`: Eine neue `/bin/bash` wird gestartet.
    2.  `chmod +x scriptname.sh` und dann `./scriptname.sh`: Das Script wird direkt ausgeführt, ebenfalls in einer neuen `/bin/bash`.
    3.  `source scriptname.sh`: Die bestehende Shell liest die Kommandos und führt sie aus. Variablen, die im Script gesetzt werden, bleiben in der aufrufenden Shell gültig.
    4.  `. scriptname.sh`: Ist äquivalent zu `source`.

### Variablen

*   Definition: `Name=Wert`. Zugriff mit `$Name`.
    ```bash
    erster_name=Jochen
    echo $erster_name # Gibt "Jochen" aus
    ```
*   **Variablen-Expansion**:
    *   **Parameter-Expansion**: Zuweisen von **Default-Werten** (`${Variable:-Default-Wert}`, `${Variable:=Default-Wert}`) oder Extrahieren von Substrings.
        *   Beispiel: `${VAR1#*:}` entfernt den längsten passenden Substring vom Anfang.
        *   Beispiel: `${VAR1%:*} `entfernt den längsten passenden Substring vom Ende.
    *   **Kommando-Substitution**: Zuweisen der Ausgabe eines Kommandos an eine Variable (z.B. `Today=$(date "+%Y-%m-%d")` oder `Today=`date "+%Y-%m-%d"``).
        ```bash
        Today=$(date "+%Y-%m-%d")
        echo $Today # Gibt z.B. "2019-09-06" aus
        ```
*   **Quoting und Escaping**:
    *   `"` (Double Quotes): Schützen Leerzeichen, erlauben aber Variablen-Expansion.
    *   `'` (Single Quotes): Schützen alles, auch Variablen, verhindern Expansion.
    *   `\` (Backslash): Schützt das nächste Zeichen.
*   **Gültigkeit (Scope)**: Variablen sind standardmässig lokal zur Shell. Mit `export` werden sie an Subshells vererbt und sind dort gültig. `local` deklariert Variablen innerhalb von Funktionen als lokal .
*   **Spezielle Parameter**: `$0` (Scriptname), `$1-$9` (Positionsparameter), `$#` (Anzahl der Argumente). `shift` verschiebt Positionsparameter.

### I/O-Umlenkung

*   **Standard-I/O-Kanäle**: `stdin` (0), `stdout` (1), `stderr` (2).
*   **Umlenkung von stdout**: `Kommando > datei.log` (überschreibt), `Kommando >> datei.log` (hängt an).
*   **Umlenkung von stderr**: `Kommando 2> fehler.log`, `Kommando 2>> fehler.log`.
*   **Merge von stdout und stderr**: `Kommando > all.log 2>&1`.
*   **Alle Ausgaben unterdrücken**: `Kommando > /dev/null 2>&1`.
*   **Eingabe umleiten**: `Kommando < input.txt`.
*   **Pipelines**: `Kommando1 | Kommando2` leitet stdout von Kommando1 zu stdin von Kommando2. Jedes Programm in einer Pipeline läuft in einer Subshell.
*   **`tee`**: Dupliziert Ausgaben auf stdout und in eine Datei. Kann mit `2>&1` auch stderr umleiten.
*   **`exec`**: Kann die Dateideskriptoren des laufenden Prozesses ändern, z.B. für eine einmalige Umleitung aller zukünftigen Ausgaben im Script (`exec 1> out.log`, `exec 2> err.log`).

### Kontrollstrukturen

*   **Selektion (if/else/elif)**: Steuerung des Programmflusses basierend auf Bedingungen. Der **Exit-Code** (`$?`) eines Kommandos ist entscheidend (0 für Erfolg, ungleich 0 für Misserfolg).
    *   **`test` und `[ ]`**: Builtin-Kommandos zur Prüfung von Bedingungen.
        *   Ganze Zahlen: `-eq`, `-ne`, `-lt`, `-gt`, `-le`, `-ge`.
        *   Zeichenketten: `=`, `!=`, `-z` (leer), `-n` (nicht leer).
        *   Dateiattribute: `-e` (existiert), `-f` (normale Datei), `-d` (Verzeichnis), `-x` (ausführbar), `-w` (schreibbar), `-r` (lesbar).
    *   **`[[ ]]`**: Erweiterte Alternative zu `[ ]` in Bash, Zsh, Ksh. Ermöglicht Muster (Globbing), reguläre Ausdrücke (`=~`), und logische Operatoren (`&&`, `||`) direkt in den Klammern.
    *   **Logische Operatoren**: `!` (Negation), `-a` oder `&&` (UND), `-o` oder `||` (ODER).
    *   **`case`**: Für Mehrfach-Fallunterscheidungen basierend auf Mustern (`case $variable in Muster1) Aktionen ;; Muster2) Aktionen ;; *) Default ;; esac`).
*   **Iteration (Schleifen)**:
    *   **`while`**: Führt Anweisungen aus, solange eine Bedingung WAHR ist (Exit-Code 0). In der Schleife muss das Kriterium der Bedingung geändert werden, sonst läuft die Schleife endlos.
    *   **`for` (1. Form)**: Iteriert über eine Liste von Werten (`for var in list; do ... done`). Nützlich für Script-Parameter (`$*`, `$@`) oder Kommandoausgaben (`$(ls)`).
    *   **`for` (2. Form, C-ähnlich)**: Zählergesteuerte Schleife (`for ((init; condition; increment)); do ... done`).
    *   **`until`**: Führt Anweisungen aus, bis eine Bedingung WAHR ist (Exit-Code 0). Kann immer durch eine `while`-Schleife ersetzt werden.
    *   **Steuerung der Schleifen**:
        *   **`break`**: Bricht die aktuelle Schleife ab.
        *   **`continue`**: Springt zum nächsten Schleifendurchlauf (überspringt den Rest des aktuellen Durchlaufs).

### Input/Output (Interaktiv & Formatiert)

*   **`read`**: Liest Benutzereingaben interaktiv (`read var`, mit Prompt: `-p`, verdeckt: `-s`), oder Zeile für Zeile aus Dateien oder Pipes.
    ```bash
    read -p "Geben Sie Ihren Namen ein: " name
    ```
*   **`printf`**: Für formatierte Ausgaben (Tabellen), mit Platzhaltern (`%s`, `%d`, `%f`) für Feldbreite, Ausrichtung und Nachkommastellen.
    ```bash
    printf "%-20s %6d %10.2f\n" "Shirt" 5 29.75
    ```

### Rechnen in der Bash

*   **`(( ))`**: Für Ganzzahl-Berechnungen und logische Vergleiche.
    ```bash
    (( z = 5 + 10 ))
    ```
*   **`let`**: Alternative für Ganzzahl-Berechnungen. Bei `let` muss das `$`-Zeichen vor Variablen-Namen stehen.
*   **`typeset -i` / `declare -i`**: Deklariert Variablen als Ganzzahlen, wodurch Berechnungen einfacher werden.

### Funktionen

*   **Definition**: `name() { Anweisungen }` oder `function name { Anweisungen }`.
*   **Aufruf**: Einfach den Namen der Funktion verwenden, Argumente werden wie Positionsparameter (`$1`, `$2`, `$@`) behandelt.
*   **Rückgabewerte**:
    *   Mit `return <Ganzzahl>` (0-255, in `$?` verfügbar) für Statusmeldungen.
    *   Für andere Werte `echo` verwenden und im aufrufenden Programm per Kommando-Substitution abfangen.
    *   `exit` in einer Funktion beendet das gesamte Skript.
*   **Scope**: Variablen sind global, es sei denn, sie werden mit `local` innerhalb der Funktion deklariert. Eine lokale und eine globale Variable können den gleichen Namen haben, wobei in der Funktion die lokale Variable Vorrang hat.
*   **Funktionsbibliotheken**: Funktionen können in separaten Dateien gespeichert und mit `source` oder `.` in Scripte eingebunden werden.
*   **Vorrang**: Alias > Funktion > Builtin > Externes Kommando.
*   **Beispiel Log- und Fehlerfunktionen**:
    *   `funcLog()`: Schreibt Zeitstempel und Nachricht in eine Logdatei (`alert.log`) und auf stdout.
        ```bash
        funcLog() {
          local _logtime
          local _message=${1}
          _logtime=$(date +%Y.%m.%d-%H:%M:%S)
          echo "${_logtime} ${_message}" >> ${_APPLI_FOLDER}/appli/log/alert.log
          echo "${_logtime} ${_message}"
        }
        ```
    *   `funcError()`: Prüft, ob der übergebene Fehlercode ungleich 0 ist, und beendet das Skript dann mit Exit-Code 1.
        ```bash
        funcError() {
          local _error=${1}
          if ! [ "${_error}" == "0" ]; then
            exit 1
          fi
        }
        #Aufruf
        funcError $?
        ```

### Arrays

*   **Indizierte Arrays**: Werte werden über numerische Indizes (beginnend bei 0) angesprochen (`arr=(A B C)`, `${arr}`). Elemente hinzufügen (`arr+=(value)`).
*   **Assoziative Arrays**: Werte werden über Zeichenketten (Keys) angesprochen (`declare -A arr`, `arr[Key]=Wert`, `${arr[Key]}`).
*   **Operationen**: Alle Elemente (`${arr[@]}`), Anzahl Elemente (`${#arr[@]}`), Keys (`${!arr[@]}`), Hinzufügen (`arr+=(value)`), Löschen (`unset`).
*   Arrays in Funktionen sind standardmässig lokal, können aber mit `declare -g` global gemacht werden. `IFS` kann zur Manipulation von Feldtrennern beim Befüllen von Arrays genutzt werden.

### Erweiterte Themen

*   **Prozesse**:
    *   **`fork()`**: Erzeugt eine exakte Kopie des aktuellen Prozesses.
    *   **`exec()`**: Ersetzt das Programm im *laufenden Prozess* durch ein neues Programm, ohne einen neuen Prozess zu starten.
    *   **`wait()`**: Wartet auf die Beendigung eines Kindprozesses.
    *   **Hintergrundausführung**: Mit `&` wird ein Kommando im Hintergrund gestartet (`fork()` ohne `wait()`).
*   **Jobkontrolle**: Kommandos wie `jobs` (listet Jobs), `fg` (Vordergrund), `bg` (Hintergrund), `kill`, `disown` (entkoppelt Job von der Shell-Sitzung).
*   **`nohup`**: Stellt sicher, dass ein im Hintergrund gestartetes Kommando auch nach Beendigung der Terminal-Sitzung weiterläuft.
*   **Signale**: Mechanismus zur Kommunikation zwischen Prozessen. Beispiele: `SIGHUP` (1, Terminal beendet), `SIGINT` (2, Ctrl+C), `SIGTERM` (15, kill), `SIGKILL` (9, nicht abfangbar). `trap` ermöglicht das Abfangen und Behandeln von Signalen in Scripts.
*   **Interprozesskommunikation (IPC)**:
    *   **Named Pipes (`mkfifo`)**: Ermöglichen die Kommunikation zwischen nicht verwandten Prozessen, indem sie wie Dateien angelegt und von Prozessen gelesen/geschrieben werden können.
    *   **Synchronisierung mit Lock-Dateien**: Verhindert gleichzeitigen Zugriff auf Ressourcen (z.B. durch Prüfung und Schreiben der PID in eine Lock-Datei).
*   **Dynamische Anweisungen und `eval`**: Kommandos können in Variablen gespeichert werden. `eval` führt einen String als Kommando aus, was nützlich für komplexe dynamisch generierte Kommandos (z.B. mit Pipes) ist.

### Testen von Scripts

*   **Test-Arten**:
    *   **Unit-Test**: Prüfung einer Funktion oder eines Scripts mit aussagekräftigen Testfällen, die automatisch durchlaufen werden.
    *   **Integrations-Test**: Prüfung der Zusammenarbeit mehrerer Funktionen oder Scripts, insbesondere der Schnittstellen.
    *   **System-Test**: Test des gesamten Systems, um zu prüfen, ob alle Anforderungen erfüllt werden.
*   **Was kann getestet werden?**:
    *   **Direkte Wirkungen**: Rückgabewerte (Exit-Code), Terminal-Ausgaben (stdout, stderr).
    *   **Seiteneffekte**: Änderungen am Systemzustand (Variablen, Dateien), Änderungen am Systemverhalten.
*   **Testpfade**:
    *   **Positivtest ("Happy Path")**: Überprüfung des Verhaltens, wenn das Script wie geplant genutzt wird und korrekt abläuft.
    *   **Negativtest ("Sad Path")**: Überprüfung des Verhaltens, wenn das Script fehlerhaft ausgeführt wird oder andere Fehler auftreten.
    *   **Destruktiver Test ("Monkey Test")**: Willkürliche Versuche, das Skript zum Absturz zu bringen.
*   **Testumgebung**: Muss reproduzierbar sein (z.B. VM-Snapshots). Verwendung von "Stubs" oder "Mocks" für nicht fertige oder externe Komponenten.
*   **Testdaten**: Auswahl von Repräsentanten aus **Äquivalenzklassen**. Beispiel für Zahlenbereich 1-100: Werte im Bereich (1, 50, 100), unterhalb (0, -1), oberhalb (101), keine Zahl ("ABC").
*   **Testscript-Struktur**:
    *   `setup`: Vorbereitung des Testfalls.
    *   Ausführung des Tests.
    *   `report`: Ausgabe der Testergebnisse (Output, Return-Code, Dateizustand).
    *   `teardown`: Aufräumen nach dem Test.

### Textverarbeitungstools (Anhänge)

*   Kurze Einführung in **`sed`** (Stream Editor) für Suchen und Ersetzen (`s/Suchmuster/Ersatztext/g`) und **`awk`** für zeilen- und spaltenweise Textverarbeitung (`awk '[Muster] {Aktionen}' datei`).
*   **Reguläre Ausdrücke (Regex)** sind dabei wichtig und umfassen Zeichen wie `^`, `$`, `.`, `[]`, `*`, `+`, `\`.

```
