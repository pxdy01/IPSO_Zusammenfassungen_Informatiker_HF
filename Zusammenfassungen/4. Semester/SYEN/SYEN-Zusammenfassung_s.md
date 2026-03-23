### Systems Engineering: Kompakter Spicker für die Fachprüfung

#### 1\. Block 1: Grundlagen, Systemdefinition und Systemdenken

##### 1.1 Gegenüberstellung der Disziplinen

| Merkmale    | Systems Engineering                          | System Engineering                                           | Projektmanagement                                          |
| ----------- | -------------------------------------------- | ------------------------------------------------------------ | ---------------------------------------------------------- |
| Definition  | Domänenübergreifende Disziplin (Methodik)    | Konkrete Anwendung von Systems Engineering auf ein Projekt.  | Organisation und Koordination des Problemlösungsprozesses. |
| Schwerpunkt | Denkweisen, Methoden, Prozesse, Vorgehen     | Entwicklung eines konkreten Systems; konstruktive Lösungsfindung. | Überwachung der Projektziele (Zeit, Kosten, Qualität)      |
| Kompetenzen | Fachwissen technischer Domänen ist sekundär. | Unverzichtbar: Fachwissen über die spezifische Domäne.       | Unverzichtbar: Zuteilung von Kompetenzen auf Teilaufgaben. |

(Quelle: Block 1, Folie 12)

##### 1.2 Systemdefinition und Eigenschaften

**Systemdefinition:** Ein System ist ein dynamisches Ganzes mit spezifischen Eigenschaften und Verhaltensweisen. Es besteht aus Teilen, die so verknüpft sind, dass kein Teil unabhängig ist und das Verhalten des Ganzen durch das Zusammenwirken aller Teile bestimmt wird.

**Wesentliche Eigenschaften:**

* **Teile:** Besteht aus mehreren, verschiedenen Komponenten.  

* **Vernetzung:** Teile stehen durch einen strukturierten Aufbau in Beziehung (keine wahllose Anordnung).  

* **Ganzheitlichkeit:** Das System stellt ein Ganzes dar, das mehr ist als die Summe seiner Teile (Synergie/Emergenz).  

(Quelle: Block 1, Folie 16 & 25\)

##### 1.3 Das SE-Männchen (Daenzer 1976\)

Das Modell visualisiert die Hierarchie der Disziplin:

1. **SE-Philosophie (Kopf):** Übergeordnetes Fundament aus **Systemdenken** (Begriffe/Modelle) und **Vorgehensmodellen**.  

2. **Problemlösungsprozess (Körper):** Die operative Ebene, bestehend aus **Systemgestaltung** (inhaltliche Lösung) und **Projektmanagement** (formale Abwicklung).  

3. **Hilfsmittel (Füße):** Spezifische **Techniken** zur Systemgestaltung und zum Projektmanagement (Methoden-Werkzeugkasten).  

(Quelle: Block 1, Folie 19; Block 3, Folie 5\)

##### 1.4 Systemelemente und Umfeld

* **Untersuchungsbereich:** Der Bereich, in dem Optimierungen oder Veränderungen geplant sind.  

* **Systemgrenze:** Trennlinie zwischen System und Umwelt; definiert den Handlungsspielraum.  

* **Umsystem:** Ein dem betrachteten System übergeordnetes System (Supersystem).  

* **Subsystem (Untersystem):** Ein in sich geschlossener, funktionaler Teil eines größeren Systems.  

* **Element:** Die kleinste, innerhalb der Betrachtung nicht weiter unterteilte Komponente. 

(Quelle: Block 1, Folie 14, 15 & 25\)

##### 1.5 Offene vs. Geschlossene Systeme

* **Offene Systeme:** Interagieren über Wechselwirkungen mit der Umwelt.  

* **Geschlossene Systeme:** Keine Interaktion mit der Umwelt (theoretisches Modell).  

* **Realität:** In der Praxis sind **alle Systeme offen**. Geschlossene Systeme existieren real nicht (außer ggf. das Universum).  

(Quelle: Block 1, Folie 21; Block 3, Folie 6\)

##### 1.6 Systemgrenzen und Schnittstellen

**Vier Dimensionen der Abgrenzung:** 

- **Geographisch (Räumlich/Standort):** Hier geht es um physische Standorte.

  *Beispiel:* Du planst ein neues WLAN-Netzwerk. Zieht man die Grenze geographisch nur um das Hauptgebäude in Zürich, oder schliesst das System auch die Filiale in Bern und das Homeoffice der Mitarbeitenden ein?

- **Politisch:** Hier geht es um Machtstrukturen, Einflussbereiche oder politische Zuständigkeiten.

  *Beispiel:* Bei einem E-Voting-System für die Schweiz verläuft die politische Grenze bei den Kantonen, da jeder Kanton eigene Abstimmungsgesetze und Zuständigkeiten hat

- **Juristisch (Rechtlich):** Diese Grenze wird durch Verträge, Gesetze oder Rechtsformen vorgegeben.

  *Beispiel:* Ein HR-System wird für die "Firma AG" entwickelt. Die juristische Grenze schliesst die Tochtergesellschaft "Firma GmbH" aus, da sie rechtlich gesehen ein anderes Unternehmen mit eigener Buchhaltung ist. Auch Datenschutzrichtlinien (z. B. Daten dürfen die Schweiz nicht verlassen) bilden juristische Systemgrenzen.

- **Betriebs-organisatorisch:** Diese Grenze richtet sich nach dem Organigramm oder den internen Strukturen eines Unternehmens.

  *Beispiel:* Ein neues Zeiterfassungssystem wird eingeführt. Die Systemgrenze wird so gezogen, dass das System nur für die Abteilung "Support" gilt, während die Abteilung "Entwicklung" ihr bestehendes System behält.

Das Verständnis dieser Dimensionen hilft dir dabei, im "Trade-off" (Kompromiss) die Grenze weder zu eng noch zu weit zu ziehen, damit der Analyseaufwand machbar bleibt, du dir aber keine innovativen Lösungswege verbaust.

**Prinzipien der Grenzziehung:**

* **Übergewicht der inneren Bindung:** Die Teile (Elemente) *innerhalb* deines Systems müssen viel stärker miteinander vernetzt sein und mehr miteinander interagieren, als sie es mit Dingen *ausserhalb* des Systems tun. Wenn dies nicht so ist, wäre das System extrem abhängig von seiner Umwelt und unglaublich fehleranfällig. 
  * **Schnittstellenminimierung:** Schnittstellen zur Umwelt müssen so gering und einfach wie möglich gehalten werden. Geht hand in Hand mit dem ersten Prinzip.

* **Trade-off:** Eine zu weite Abgrenzung erhöht den Analyseaufwand massiv; eine zu enge Grenze schränkt den Lösungsraum ein und verhindert Innovation.

(Quelle: Block 1, Folie 26-28, Ergänzungen mit Recherchen)

##### 1.7 Black-Box-Betrachtung

Das Black-Box-Prinzip ist rein **wirkungsorientiert** (Input/Output). Der interne Aufbau wird ausgeblendet, um Komplexität zu reduzieren.

* **Hierarchisches Systemkonzept:** Die Black-Box ermöglicht es, komplexe Systeme als einfaches Element innerhalb eines übergeordneten Systems (Supersystem) zu behandeln.

(Quelle: Block 1, Folie 29; Block 3, Folie 10\)

#### 2\. Block 2: Vorgehensmodelle, PLZ und Risikomanagement

##### 2.1 Grundprinzipien des SE-Vorgehensmodells

* **Vom Groben zum Detail (Top-Down):** Erst den Rahmen (generelle Ziele) festlegen, dann schrittweise konkretisieren und einengen.  

* **Variantenbildung:** Grundsätzliches Denken in Alternativen, um Fehlentscheidungen zu vermeiden.  

* **Phasengliederung:** Zeitliche Strukturierung in überschaubare Etappen (Meilensteine).

(Quelle: Block 2, Folie 4-5)

##### 2.2 Der Problemlösungszyklus (PLZ) \- Mikrostrategie

Der PLZ wird in jeder Phase des Projekts erneut durchlaufen:

* **Zielsuche**  

  * **Situationsanalyse** (Aufgaben-, IST-Zustands-, Zukunftsanalyse, Zusammenfassende Problemdefinition).  
  * **Zielformulierung** (Entwurf, Analyse, **Genehmigung**).  

* **Lösungssuche**

  * **Konzeptsynthese** (Entwurf von Varianten).  
  * **Konzeptanalyse** (Prüfung der Varianten).  

* **Auswahl**  

  * **Beurteilung** (Vergleich anhand Kriterien).  

  * **Entscheidung** (Festlegung auf eine Variante). 

Quelle: Block 2, Folie 10\)


##### 2.3 Situationsanalyse und Schwachstellen

**Zweck:** Systematisches Durchleuchten einer Situation (Diagnose), um das Problem begreifbar zu machen.

**Ursachen-/Wirkungs-Graph:** Visualisiert die **Vernetzung und Interkonnektivität** verschiedener Schwachstellen und deren Hintergründe.

*Beispiele:* 

- *(Ursache)* Dozent will zwingend Beamer nutzen ➔ *(Wirkung/Ursache)* Unterricht findet in einem anderen Raum statt ➔ *(Wirkung/Ursache)* Längerer Weg zum Bahnhof ➔ **(Hauptsymptom) Zug verpasst**.
- *(Ursache)* Dozent macht langweilige "Folienschlacht" ➔ *(Wirkung/Ursache)* Müdigkeit ➔ *(Wirkung/Ursache)* Drang, unterwegs einen Kaffee zu kaufen ➔ *(Wirkung/Ursache)* Zeitverlust ➔ **(Hauptsymptom) Zug verpasst**.
- *(Ursache)* Keine klaren Anweisungen zur Pausendauer ➔ *(Wirkung/Ursache)* Klasse überzieht die Pause ➔ *(Wirkung/Ursache)* Unterricht endet zu spät ➔ **(Hauptsymptom) Zug verpasst**.

**Inhalt eines Schwachstellenkatalogs (Checkliste):**  

- [ ] ID-Nummer & Bezeichnung (Stichwort)  

- [ ] Kurzbeschreibung der Schwachstelle  

- [ ] Mögliche Ursachen & Auswirkungen (Wichtigkeit)  

- [ ] Chancenbeurteilung der Beseitigung  

- [ ] Grobe Lösungsidee

*Beispiel:*

| ID   | Bezeichnung (Stichwort)     | Kurzbeschreibung                                             | Ursache(n)                                                   | Auswirkung (Wichtigkeit)                                     | Chancenbeurteilung                                    | Grobe Lösungsidee                                            |
| ---- | --------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ----------------------------------------------------- | ------------------------------------------------------------ |
| 1    | Verspätetes Unterrichtsende | Der Unterricht wurde zu spät beendet, was zur Verknappung der Zeit führt | Dozent gab keine genauen Anweisungen zur Pausendauer; Klasse überzog die Pause | Die Zeit reicht nicht mehr für den pünktlichen Zuganschluss (Hohe Wichtigkeit) | Sehr gut (sofort und einfach behebbar)                | Klare Pausenzeiten definieren; Dozent hört in Zukunft generell etwas früher auf |
| 2    | Monotoner Unterricht        | Der Unterricht war langweilig und einschläfernd              | Reine "Folienschlacht" mittels Beamer durch den Dozenten     | Studierende müssen Kaffee kaufen gehen, um wach zu werden, was zusätzlich Zeit kostet | Mittel (braucht etwas Vorbereitungszeit des Dozenten) | Interaktivere Unterrichtsgestaltung ohne reinen Beamer-Fokus. |
| 3    | Ungünstige Raumwahl         | Der Weg zum Bahnhof hat sich erheblich verlängert            | Dozent wollte in einem anderen Raum mit Beamer unterrichten  | Längere Gehdistanz zum Bahnhof frisst den Zeitpuffer auf     | Gut                                                   | Auf Beamer verzichten oder Schulzeiten besser an Zugabfahrten anpassen |

(Quelle: Block 2, Folie 12-16)

##### 2.4 Risikomanagement

**Prozess:**  1\. Identifikation  ➔  2\. Bewertung  ➔  3\. Verringerung.

**Risikomatrix:** Achsen: **Eintrittswahrscheinlichkeit** (E) vs. **Schadensausmass** (A).

|                                |              | Schandenausmass | Schandenausmass | Schandenausmass  |
| ------------------------------ | ------------ | --------------- | --------------- | ---------------- |
|                                |              | Gering          | Mittel          | Hoch             |
| **Eintritswahrscheinlichkeit** | Häufig       | Mitleres Risiko | Hohes Risiko    | Hohes Risiko     |
| **Eintritswahrscheinlichkeit** | Gelegentlich | Geringes Risiko | Mitleres Risiko | Hohes Risiko     |
| **Eintritswahrscheinlichkeit** | Selten       | Geringes Risiko | Geringes Risiko | Mittleres Risiko |

* **Risikowert (R) Kalkulation:** R = E * A (Shorthand für die Einstufung Gering/Mittel/Hoch).

**Struktur Risikokatalog:**  

| Nr.  | Kategorie | Risiko         | Auswirkung   | E    | A    | **R** | Maßnahme        | E    | A    | R    | Restrisiko       |
| ---- | --------- | -------------- | ------------ | ---- | ---- | ----- | --------------- | ---- | ---- | ---- | ---------------- |
| 1    | Personal  | Krankheitsfall | Projektstopp | s    | h    | m     | Stellvertretung | s    | g    | g    | Know-how Verlust |

*Legende: s=selten, g=gelegentlich, h=häufig / g=gering, m=mittel, h=hoch*

(Quelle: Block 2, Folie 18-20)

##### 2.5 Zielbeziehungen

* **Unterstützung:**  Ziel A begünstigt B (Bsp.: Hohe Performance  ➔  Benutzerzufriedenheit).  

* **Unabhängigkeit:**  Keine Beeinflussung (Bsp.: Farbwahl Gehäuse vs. Verschlüsselungsalgorithmus).  

* **Konkurrenz:**  Ziele behindern sich (Bsp.: Maximale Sicherheit vs. minimale Kosten).  

* **Widerspruch:**  Ziele schließen sich aus (Bsp.: Absolute Standardisierung vs. Individualsoftware).

(Quelle: Block 2, Folie 28\)

#### 3\. Block 3: Phasenmodell, Lösungssuche und Zielformulierung

##### 3.1 Lebensphasen eines Systems (Makrostrategie)

1. **Anstoss**: Start

2. **Vorstudie** (Synonym:  *Vorabklärung* ): Machbarkeit, Problemdefinition, Systemabgrenzung.  

3. **Hauptstudie** (Synonym:  *Grobkonzept* ): Systemarchitektur, HW/SW-Zusammenspiel, Funktionsanalyse.  

4. **Detailstudie** (Synonym:  *Detailkonzept* ): Definitive Teilsystemgrenzen, Pflichtenhefte, Baustein-Konzepte.  

5. **Systembau** (Realisierung)

6. **Einführung**

7. **Nutzung/Entsorgung** 

Quelle: Block 2, Folie 7; Block 3, Folie 12-20)

##### 3.2 Problemdefinition und Zielformulierung

* **Problem:** Diskrepanz zwischen **IST-Zustand** und **SOLL-Vorstellung** für die es noch keine Lösung gibt.  

* **SMART-Prinzip:** **S**pezifisch, **M**essbar, **A**ttraktiv (akzeptiert), **R**ealistisch, **T**erminiert.  

* **Grundsätze:** Lösungsneutralität (beschreibe das "Was"), Vollständigkeit, Operationalisierung (messbar machen).

**Ziele (Das WAS) vs. Anforderungen (Das WIE):**

| Ziele (Erwünschte Wirkung) | Anforderungen (Der Weg/Forderung) |
| -------------------------- | --------------------------------- |
| Senkung der Personalkosten | Automatisierung des Mahnlaufs     |
| Erhöhung der Transparenz   | Einführung täglicher Reports      |

(Quelle: Block 2, Folie 21-24; Block 3, Folie 11, 25\)

##### 3.3 Lösungssuche: Synthese und Analyse

**Synthese (Kreativer Schritt):** Modellhaftes Zusammenfügen zu einem Ganzen.

1. **Erahnung:** Intuition des gesamten Lösungskonzepts.  

2. **Finden:** Identifikation der notwendigen Lösungselemente.  

3. **Zusammenfügen:** Modellausbau und Verbindung der Elemente.  

4. **Regeln:** Modularität \+ minimale Schnittstellen, **Infragestellen von Randbedingungen**, Denken in echten Varianten.  

5. **Merke:** Wunschziele (Kann-Ziele) dienen hier als wichtige Rahmenbedingungen.

**Analyse (Kritischer Schritt):** Prüfung der Varianten (noch keine Bewertung).  

* **Regeln:** Prüfung auf Muss-Ziel-Einhaltung, Funktionstüchtigkeit, Sicherheit, Zuverlässigkeit.

(Quelle: Block 3, Folie 28-35)

#### 4\. Block 4: Evaluation und Entscheidungsmethoden

##### 4.1 Zielgewichtung

* **Muss-Ziele:** Keine Gewichtung erforderlich, da sie zu 100% erfüllt sein müssen (K.O.-Kriterien).  

* **Kann-Ziele (Wunschziele):** Werden gewichtet, um ihre relative Bedeutung für die Auswahlentscheidung abzubilden.

(Quelle: Block 4, Folie 28\)

Für die Gewichtung der Kann-Ziele gibt es drei wesentliche Verfahren:

**Stufenweise Vergabe von Gewichtungspunkten (Zielhierarchie):** 
Ausgehend von einem Hauptziel (welches z. B. 100 Punkte erhält) werden die Punkte stufenweise auf die darunterliegenden Unterziele und Feinziele verteilt.

**Vorteile:** 
Das Vorgehen ist einfach und die grafische Darstellung für jeden leicht verständlich.

**Nachteile:** 
Bei einer grossen Anzahl an Zielen ist das Urteilsvermögen schnell überfordert und es besteht das Risiko, dass bestimmte Zielgruppen frühzeitig bevorzugt werden.

(Quelle: Block 4, Folie 31)

**Einfaches Gewichtungsverfahren:**
Die Ziele werden pauschal in vier Kategorien eingeteilt: nicht sehr wichtig, durchschnittlich, wichtig und sehr wichtig (Muss-Ziel ohne KO-Eigenschaft).

**Vorteile:** 
Sehr simple und schnelle Handhabung.

**Nachteile:** 
Wegen der fehlenden Differenzierung ist dieses Verfahren nur für kleinere Projekte anwendbar.

(Quelle: Block 4, Folie 33)

**Präferenzmatrix:**
Dies ist ein "wissenschaftlicher" Paar-Vergleich, bei dem alle Ziele systematisch einander gegenübergestellt und miteinander verglichen werden.

**Vorteile:** 
Die vielen Einzelvergleiche verhindern, dass das Endergebnis einfach manipuliert werden kann.

**Nachteile:** 
Die Technik ist aufwendig, benötigt Zeit und ist erklärungsbedürftig.

(Quelle: Block 4, Folie 45)

Die **Nutzwertanalyse** baut direkt auf diesen gewichteten Zielen auf und dient der vergleichenden Bewertung der ausgearbeiteten Lösungsvarianten. Der Ablauf ist wie folgt strukturiert:

**Muss-Ziele prüfen:** 
Es wird pro Variante (z. B. "Bingo", "Bongo", "Quark") kontrolliert, ob die Muss-Ziele erfüllt sind.

**Punkte vergeben:** 
Für die einzelnen Kann-Ziele wird beurteilt, wie gut die Variante das Ziel erfüllt, und entsprechend Punkte verteilt.

**Gewichtung anwenden:** 
Die vergebenen Punkte werden mit dem zuvor definierten Gewicht des jeweiligen Ziels multipliziert. Das Ergebnis ist das "Produkt".

**Summieren:** 
Die Summe aller Produkte ergibt den Gesamtnutzwert (die Gesamtpunktzahl) für die jeweilige Variante.

Die **Kosten/Wirksamkeitsanalyse** (häufig gleichbedeutend mit Kosten/Nutzenanalyse verwendet) setzt abschliessend den soeben errechneten Nutzwert ins Verhältnis zu den finanziellen Kosten einer Variante. Dabei teilt man die Gesamtkosten der Variante durch die erreichten Punkte aus der Nutzwertanalyse, um die **Kosten pro Punkt** zu berechnen.

*Beispiel:* Wenn Variante A 2000 CHF kostet und in der Nutzwertanalyse 450 Punkte erreicht hat, betragen die Kosten 4.44 pro Punkt. Erreicht Variante D zwar 470 Punkte, kostet aber 2500 CHF, liegen die Kosten hier bei 5.32 pro Punkt – Variante A bietet somit das bessere Kosten-Nutzen-Verhältnis.

(Quelle: Block 4, Folien 51 und 52)

##### 4.3 Wasserfallmodell

Das **Wasserfallmodell** ist ein klassisches Vorgehensmodell, das vom Grundsatz her **sequentiell und konstruktivistisch** aufgebaut ist. Im Gegensatz zu agilen Methoden durchläuft es die verschiedenen Projektphasen streng nacheinander.

Nach dem Wasserfallmodell von **Götz Schmidt** lassen sich den einzelnen Phasen typische **Zeithorizonte** zuordnen, die aufzeigen, wie viel Zeit in der Regel in die jeweiligen Schritte investiert wird:

- **Anstoss:** Tage / Wochen
- **Vorstudie:** Wochen / Monate
- **Hauptstudie (Konzept):** mehrere Monate
- **Detailstudie (Detailkonzept):** wenige Monate (pro Detailstudie)
- **Systembau (Realisierung):** wenige Monate (pro Teil)
- **Einführung:** Wochen / Monate
- **Erhaltung (Wartung):** Zeitlos... (läuft solange, bis das System irgendwann abgelöst wird)

In der Praxis wird neben der reinen sequentiellen Form häufig das **Wasserfallmodell mit Rückkopplung** verwendet, welches Korrekturschleifen (Iterationen) zu vorherigen Phasen zulässt.

*(Hinweis: Als weitere Ausprägungen von Vorgehensmodellen werden auf diesen Folien auch das V-Modell, das Spiralmodell und RUP – Rational Unified Process – aufgeführt).*

(Quelle: Block 4, Folien 37 bis 39)