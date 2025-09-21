
## Grundlagen von Bash-Scripting

Ein Bash-Skript ist eine Textdatei, die eine Sequenz von Befehlen enthält. Die Skripte werden vom **Bash-Interpreter** ausgeführt.

### Erstellen und Ausführen eines Skripts

1.  **Shebang:** Jedes Skript sollte mit der sogenannten **Shebang-Zeile** beginnen: `#!/bin/bash`. Dies teilt dem Betriebssystem mit, welchen Interpreter es für die Ausführung des Skripts verwenden soll.
    
2.  **Dateiendung:** Skripte haben oft die Endung `.sh`, dies ist jedoch nicht zwingend.
    
3.  **Ausführungsrechte:** Bevor Sie ein Skript ausführen können, müssen Sie ihm die nötigen Ausführungsrechte geben. Verwenden Sie dafür den Befehl `chmod +x skriptname.sh`.
    
4.  **Ausführung:** Führen Sie das Skript mit `./skriptname.sh` aus.
    

### Variablen

Variablen dienen zur Speicherung von Werten.

-   **Deklaration:** Weisen Sie einer Variable einen Wert zu, ohne Leerzeichen um das Gleichheitszeichen: `meine_variable="Hallo Welt"`.
    
-   **Zugriff:** Greifen Sie auf den Wert einer Variable zu, indem Sie ihr ein `$`-Zeichen voranstellen: `echo $meine_variable`. Verwenden Sie geschweifte Klammern, um Verwechslungen mit anderen Texten zu vermeiden: `echo "Der Wert ist ${meine_variable}!"`.
    

### Ein- und Ausgabe

-   **Standard-Ausgabe:** Verwenden Sie den Befehl `echo` um Text oder Variablenwerte auf der Konsole auszugeben. `echo "Dies ist eine Ausgabe."`.
    
-   **Standard-Eingabe:** Lesen Sie Benutzereingaben mit dem Befehl `read` ein.
    
    -   `read -p "Geben Sie Ihren Namen ein: " benutzername`
        
    -   `echo "Hallo, $benutzername"`
        

----------

## Kontrollstrukturen

Kontrollstrukturen ermöglichen es, den Programmfluss zu steuern.

### Bedingte Anweisungen (if-elif-else)

Bedingte Anweisungen werden verwendet, um verschiedene Befehle abhängig von einer Bedingung auszuführen.

**Syntax:**

Bash

```
if [ Bedingung ]; then
  # Befehle, wenn die Bedingung wahr ist
elif [ Zweite_Bedingung ]; then
  # Befehle, wenn die zweite Bedingung wahr ist
else
  # Befehle, wenn keine der Bedingungen wahr ist
fi

```

**Wichtige Test-Operatoren:**

-   **Numerische Vergleiche:**
    
    -   `-eq` (gleich)
        
    -   `-ne` (nicht gleich)
        
    -   `-gt` (grösser als)
        
    -   `-lt` (kleiner als)
        
    -   `-ge` (grösser oder gleich)
        
    -   `-le` (kleiner oder gleich)
        
-   **String-Vergleiche:**
    
    -   `==` (gleich)
        
    -   `!=` (nicht gleich)
        
    -   `-z "string"` (String ist leer)
        
    -   `-n "string"` (String ist nicht leer)
        
-   **Datei-Tests:**
    
    -   `-e datei` (Datei existiert)
        
    -   `-f datei` (Ist eine reguläre Datei)
        
    -   `-d verzeichnis` (Ist ein Verzeichnis)
        
    -   `-r datei` (Datei ist lesbar)
        
    -   `-w datei` (Datei ist schreibbar)
        
    -   `-x datei` (Datei ist ausführbar)
        

### Schleifen

Schleifen wiederholen eine Befehlssequenz.

**For-Schleife:** Iteriert über eine Liste von Elementen.

Bash

```
for datei in *.txt; do
  echo "Bearbeite Datei: $datei"
done

```

**While-Schleife:** Wiederholt, solange eine Bedingung wahr ist.

Bash

```
zahl=1
while [ $zahl -le 5 ]; do
  echo "Zahl: $zahl"
  zahl=$((zahl+1))
done

```

----------

## Funktionen und fortgeschrittene Konzepte

Funktionen fassen Befehle zu wiederverwendbaren Blöcken zusammen.

### Funktionen

-   **Deklaration:**
    
    Bash
    
    ```
    function meine_funktion {
      echo "Dies ist eine Funktion."
    }
    
    ```
    
    oder kurz:
    
    Bash
    
    ```
    meine_funktion() {
      echo "Dies ist eine Funktion."
    }
    
    ```
    
-   **Aufruf:** `meine_funktion`
    
-   **Parameter:** Auf Parameter wird mit `$1`, `$2`, etc. zugegriffen.
    
    -   `$#`: Anzahl der Parameter
        
    -   `$*` oder `$@`: Alle Parameter als eine Zeichenkette
        

### Exit-Codes und Fehlerbehandlung

-   **Exit-Code:** Jedes Kommando und Skript gibt einen **Exit-Code** zurück. Ein Wert von `0` bedeutet Erfolg, ein Wert ungleich `0` bedeutet Fehler.
    
-   **Abfrage:** Der Exit-Code des letzten Befehls wird in der Variable `$?` gespeichert.
    
    -   `cp datei1.txt datei2.txt`
        
    -   `if [ $? -eq 0 ]; then echo "Kopieren erfolgreich."; fi`
        

----------

## Best Practices

-   **Kommentare:** Fügen Sie Kommentare (`#`) hinzu, um Ihren Code verständlich zu machen.
    
-   **Fehlerbehandlung:** Verwenden Sie `set -e`, um das Skript bei einem Fehler sofort zu beenden.
    
-   **Debugging:** Führen Sie Ihr Skript mit `bash -x skriptname.sh` aus, um die Ausführung Schritt für Schritt zu verfolgen und die Befehle und Variablenwerte zu sehen.
    
-   **Globale Variablen vermeiden:** Verwenden Sie lokale Variablen in Funktionen mit dem Schlüsselwort `local`.
    
