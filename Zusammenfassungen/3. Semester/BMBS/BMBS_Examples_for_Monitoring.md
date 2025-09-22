Die Automatisierung von Aufgaben im **IT-Betrieb und -Monitoring** ist eine wesentliche Aufgabe, die durch Ansätze wie «Infrastructure as Code» immer wichtiger wird. Der Kurs BMBS.TA1A vermittelt Grundkenntnisse in der Script-Programmierung mit Bash, kombiniert mit typischen Linux-Kommandos zur Systemverwaltung.

Im Folgenden finden Sie eine Zusammenfassung gängiger Bash-Script-Elemente und Beispiele, die häufig im Linux-Monitoring eingesetzt werden:

### I. Grundlegende Funktionen für Monitoring-Skripte

Für die Erstellung robuster Monitoring-Skripte sind Funktionen zur Protokollierung und Fehlerbehandlung unerlässlich.

#### 1. Log-Einträge protokollieren (funcLog)
Die Funktion **`funcLog()`** wird verwendet, um formatierte Log-Einträge zu erstellen.

*   Sie verwendet eine lokale Variable `_logtime`, um den aktuellen Zeitstempel im Format `%Y.%m.%d-%H:%M:%S` zu speichern.
*   Die übergebene Nachricht (`_message`) wird zusammen mit dem Zeitstempel sowohl in eine Alert-Logdatei (`${_APPLI_FOLDER}/appli/log/alert.log`) geschrieben als auch auf der Standardausgabe ausgegeben.

**Beispiel-Script-Funktion für Logging:**
```bash
funcLog() {
local _logtime
local _message=${1}
_logtime=$(date +%Y.%m.%d-%H:%M:%S)
echo "${_logtime} ${_message}" >> ${_APPLI_FOLDER}/appli/log/alert.log
echo "${_logtime} ${_message}"
}
```

#### 2. Fehlerbehandlung und Exit-Codes (funcError)
Die Funktion **`funcError()`** dient der Überprüfung des Rückgabewertes eines Kommandos (Exit-Code), um im Fehlerfall das Skript abzubrechen.

*   Sie nimmt den Fehlerwert als Argument.
*   **Wenn der Fehlerwert nicht gleich "0" ist** (`if ! [ "${_error}" == "0" ]`), beendet das Skript die Ausführung mit dem Exit-Code 1 (`exit 1`).
*   Der Aufruf erfolgt typischerweise durch Übergabe der speziellen Shell-Variable `$?`, welche den Exit-Code des zuletzt ausgeführten Kommandos enthält, z.B.: `funcError $?`.

**Beispiel-Script-Funktion für Fehlerbehandlung:**
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

### II. Spezifische Anwendungsbeispiele für Monitoring

Typische Monitoring-Aufgaben in der Systemadministration, die mit Bash-Skripten gelöst werden, umfassen die Überwachung von Ressourcen.

#### 1. Überprüfung des Festplattenspeichers (chkdf)
Skripte wie **`chkdf1.sh`** dienen dazu, die Festplattenauslastung zu prüfen und Alarme auszugeben, wenn Schwellenwerte überschritten werden.

*   Ein solches Skript liest die **5. und 6. Spalte der `df`-Ausgabe**.
*   Es entfernt die Überschrift sowie alle `%`-Zeichen.
*   Es vergleicht den prozentualen Auslastungswert in Spalte 5 mit einem auf der Kommandozeile übergebenen Schwellenwert.
*   **Beispiel-Ausgabe bei Überschreitung des Schwellenwerts 20:**
    `mountpoint / ist zu mehr als 20% voll!`.

Das erweiterte Skript **`chkdf2.sh`** nutzt assoziative Arrays  oder Funktionen, um die Funktionalität zu erweitern:

*   Es kann eine Konfigurationsdatei (`-f dateiname`) lesen, die spezifische Mountpunkte und individuelle Schwellenwerte (z.B. `/=60`, `/var=80`) enthält.
*   Alternativ kann mit der Option `-t <Prozentzahl>` ein allgemeiner Schwellenwert für alle Dateisysteme geprüft werden, falls keine Konfigurationsdatei angegeben wird.

#### 2. Verarbeitung von Performance-Statistiken (vmstat Analyse)
Skripte können Systemstatistiken verarbeiten, die von Kommandos wie **`vmstat`** geliefert werden .

*   `vmstat` liefert unter anderem die *idle* CPU-Zeit (`id`), den freien Hauptspeicher (`free`) oder die Anzahl der Prozesse, die auf ihre Ausführung warten (`r`) .
*   Analyse-Skripte können spezifische Spalten zur Analyse auswählen (`-c <Spalte>`) .
*   Sie können prüfen, ob ein Wert über (`-g <Wert>`) oder unter (`-l <Wert>`) einem Schwellenwert liegt und dies über ein bestimmtes Zeitintervall (`-i <Sekunden>`) hinweg tun .

### III. Erweitertes Scripting für den IT-Betrieb

Für kontinuierliches Monitoring oder die Interaktion mit externen Systemen sind fortgeschrittene Bash-Konzepte relevant:

#### 1. Funktionen und Modularisierung
Grosse Skripte werden durch **Funktionen** übersichtlicher. Funktionen können in **Funktionsbibliotheken** gruppiert werden (z.B. `file_functions`, `util_functions`, `math_functions`) . Diese Bibliotheken können in das Hauptskript mit `source` oder `.` eingebunden werden.

Beispiele für nützliche Funktionen in Bibliotheken:

*   **`is_writable_dir()`** (in `file_functions`): Liefert den Rückgabecode 0, wenn der übergebene Eintrag ein Verzeichnis ist und der Benutzer Schreibrecht besitzt .
*   **`usage()`** (in `util_functions`): Gibt den Skriptnamen (`$0` des aufrufenden Skripts) und eine Beschreibung des korrekten Aufrufs auf *stderr* aus.

#### 2. Jobkontrolle und Signale
Monitoring-Prozesse werden oft im Hintergrund ausgeführt.

*   Der Aufruf mit **`&`** startet das Kommando im Hintergrund.
*   Das Kommando **`nohup`** wird verwendet, wenn das Kommando im Hintergrund laufen soll, **unabhängig davon, ob die Terminal-Sitzung beendet wird** .
*   Die Anweisung **`trap`** ermöglicht es, auf eintreffende Signale zu reagieren, was für Monitoring-Skripte essenziell ist .
    *   Zum Beispiel kann `trap` die Standardreaktion auf Signale (wie SIGHUP, SIGTERM oder SIGINT) unterdrücken oder durch die Ausführung einer *cleanup*-Funktion ersetzen, die vor der Beendigung aufräumt (z.B. temporäre Dateien oder Named Pipes löscht) .
    *   Signale wie SIGUSR1 (Signal Nr. 10) können verwendet werden, um ein dauerhaft laufendes Skript anzuweisen, **die Konfigurationsdatei neu einzulesen**.

#### 3. Interprozesskommunikation
Für die Kommunikation zwischen nicht verwandten Prozessen, wie sie im Monitoring-Umfeld oft vorkommt, können **Named Pipes** verwendet werden .

*   Eine Named Pipe wird wie eine Datei mit **`mkfifo myFIFO`** angelegt .
*   Sie ermöglicht es, die Ausgabe eines beliebigen schreibenden Prozesses an einen anderen lesenden Prozess weiterzuleiten .

#### 4. Synchronisierung
Um Konflikte zu vermeiden, wenn mehrere Skripte gleichzeitig auf dieselben Ressourcen (z.B. gemeinsame Logdateien) zugreifen, ist Synchronisierung erforderlich.

*   Dies kann über **Lock-Dateien** erreicht werden. Ein Skript kann beim Start prüfen, ob eine Lock-Datei existiert. Wenn nicht, legt es diese an (und schreibt z.B. seine PID hinein) und setzt die Berechtigung auf *readonly* für andere Benutzer, wodurch verhindert wird, dass zwei Instanzen gleichzeitig kritische Operationen durchführen.