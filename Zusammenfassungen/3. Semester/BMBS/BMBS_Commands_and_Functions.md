### I. Systemüberwachung und -Statistiken (Monitoring-Tools)

Im Rahmen des Monitorings sind folgende spezifische Linux-Kommandos relevant, deren Ausgaben oft in Bash-Skripten verarbeitet werden:

| Kommando | Zweck im Monitoring-Kontext | Relevante Details aus den Quellen |
| :--- | :--- | :--- |
| **`vmstat`** | Dient zur Lieferung von **Performance-Statistiken** über die Systemauslastung. | Liefert unter anderem die *idle* CPU-Zeit (`id`), den freien Hauptspeicher (`free`) oder die Anzahl der Prozesse, die auf ihre Ausführung warten (`r`) . Skripte können Spalten wie `id` oder `free` analysieren, um festzustellen, ob Werte über oder unter einem Schwellenwert liegen. |
| **`df`** | Wird zur Überwachung der **Festplattenauslastung** verwendet. | Skripte wie `chkdf1.sh` analysieren die Ausgabe, um prozentuale Auslastungswerte (z.B. in der 5. und 6. Spalte) zu prüfen und bei Überschreitung eines Schwellenwerts einen Alarm auszugeben. |
| **`ps`** | Dient zur Anzeige von Prozessinformationen. | Die Ausgabe kann in Arrays gespeichert und zeilenweise verarbeitet werden, z.B. um die PID, TTY, Zeit und das Kommando von Prozessen zu überprüfen. |
| **`date`** | Dient zur Erfassung des aktuellen Zeitstempels. | Wird häufig für die Protokollierung verwendet, um formatierte Zeitstempel (z.B. `%Y.%m.%d-%H:%M:%S`) in Log-Einträgen zu speichern. |
| **`ls`** | Wird zur Anzeige von Dateinamen verwendet. | Die Ausgabe dient dazu, Listen von Werten (Dateien) zu generieren, die in Schleifen (z.B. `for datei in $(ls)`) verarbeitet werden können. |
| **`find`** | Dient zum Suchen von Dateien. | Wird in komplexeren Skripten verwendet, um Dateien mit bestimmten Mustern oder Endungen zu lokalisieren, z.B. in Skripten wie `collect.sh`. |

### II. Textverarbeitung und Filterung (Filter Tools)

Da Monitoring oft die Analyse von Log-Dateien und Kommandoausgaben beinhaltet, sind Textverarbeitungstools essenziell :

*   **`grep`** / **`egrep`**: Wird zum Suchen von Mustern in Texten verwendet.
*   **`sed`**: Ein mächtiges Tool zur **Textverarbeitung**, insbesondere zum Suchen und Ersetzen in Log-Dateien oder Kommandoausgaben .
*   **`awk`**: Ein mächtiges Tool zur **strukturierten Textverarbeitung**, ideal für die Verarbeitung von Spalten und Zeilen (z.B. in `vmstat`- oder `df`-Ausgaben).

### III. Bash-Steuerung und -Kontrollstrukturen

Für das Management des Skript-Ablaufs und des Systemzustands sind folgende interne Bash-Anweisungen zentral:

| Anweisung | Zweck im Monitoring-Kontext | Relevante Details aus den Quellen |
| :--- | :--- | :--- |
| **`exit`** | Beendet das Skript und gibt einen Exit-Code zurück. | Wichtig für die Fehlerbehandlung, um bei Fehlschlägen das Skript mit einem Fehlercode (`exit 1` oder `exit 2`) abzubrechen. |
| **`if / test / [ ]`** | Steuert den Kontrollfluss basierend auf Bedingungen (Selektion). | Unerlässlich für die **Auswertung des Exit-Codes** und für Vergleiche von Zahlen, Zeichenketten oder die **Prüfung von Dateiattributen** (z.B. `[ -f $name ]` für eine reguläre Datei oder `[ -w $name ]` für Schreibrechte). |
| **`while`** | Führt Anweisungen wiederholt aus (Iteration), solange eine Bedingung WAHR ist. | Wird verwendet, um Logiken in Endlosschleifen auszuführen (z.B. `while true; do ... done` für dauerhaftes Monitoring) oder um Dateien zeilenweise zu lesen (`while read zeile do ... done < $datei`). |
| **`for`** | Iteriert über eine Liste von Werten. | Wird oft genutzt, um über alle Skript-Argumente (`for argument in "$@"`), alle Dateinamen (`for datei in *`) oder die Elemente eines Arrays zu iterieren. |
| **`trap`** | Ermöglicht das **Abfangen und Behandeln von Signalen** . | Kritisch für langlebige Monitoring-Skripte, um auf externe Anweisungen (z.B. `SIGTERM` zum Beenden oder `SIGUSR1` zum Neuladen der Konfiguration) zu reagieren und Aufräumarbeiten durchzuführen . |
| **`exec`** | Ersetzt das laufende Programm im Prozess oder ändert Dateideskriptoren. | Kann zur einmaligen Umleitung aller Standard-I/O-Kanäle für das gesamte Skript an dessen Anfang verwendet werden, z.B. `exec 2> err.log` zur globalen Umleitung aller Fehlermeldungen. |
| **`getopts`** | Dient zur **Auswertung von Kommandozeilen-Optionen**. | Wird genutzt, um Monitoring-Skripten flexible Parameter zu übergeben (z.B. `-f <Dateiname>` oder `-t <Prozentzahl>` für `chkdf2.sh`). |
| **`shift`** | Verschiebt Positionsparameter. | Hilfreich, um nach der Verarbeitung von Optionen durch `getopts` die verbleibenden Argumente effizient zu verarbeiten. |
| **`read`** | Liest Benutzereingaben oder Zeilen aus Dateien/Pipes. | Wird zur interaktiven Eingabe in Hilfsskripten und vor allem zum **zeilenweisen Lesen von Konfigurationsdateien** oder den Ausgaben anderer Kommandos über Pipes verwendet. |
| **`printf`** | Ermöglicht **formatierte Ausgabe**. | Wichtig für die Erstellung strukturierter Log-Einträge oder Berichte (Tabellen), da es Feldbreiten und Formatierungen unterstützt. |

### IV. Prozess- und Jobkontrolle (Hintergrund-Management)

*   **`&`**: Startet ein Kommando im Hintergrund.
*   **`wait`**: Lässt das Hauptskript auf die Beendigung eines oder mehrerer Hintergrundprozesse warten.
*   **`jobs`**: Zeigt die im Hintergrund laufenden Jobs an.
*   **`fg` / `bg`**: Holt einen Job in den Vordergrund (`fg`) oder startet ihn im Hintergrund (`bg`).
*   **`kill`**: Sendet Signale an Prozesse, um sie zu beenden oder zu steuern.
*   **`nohup`**: Stellt sicher, dass ein im Hintergrund laufendes Kommando **weiterläuft, nachdem die Shell-Sitzung beendet wurde** – entscheidend für permanente Monitoring-Prozesse.