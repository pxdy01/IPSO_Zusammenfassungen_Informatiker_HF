# Zusammenfassung für das Fach SLAE

## 1. Grundlagen Service Level Management (SLM)

### 1.1 Definitionen und Konzepte

| Begriff | Definition | 
| :--- | :--- | 
| **Service Management** | Eine Menge von spezialisierten organisatorischen Fähigkeiten, die einen Mehrwert für den Kunden erzeugen und in Form einer Dienstleistung (Service) angeboten werden. | |
| **Ziele SM** | Ausrichten der IT-Services auf gegenwärtige und zukünftige Anforderungen des Business; Optimierung der Service-Qualität; Reduzieren der (langfristigen) Kosten der Serviceerbringung. | |
| **Service** | Eine Methode, einen Mehrwert für die Kunden zu generieren, orientiert an den Ergebnissen, die Kunden erzielen wollen, ohne dass diese die Kosten und Risiken der Erzeugung tragen. | |
| **IT Service Management (ITSM)** | Die Gesamtheit von Massnahmen und Methoden, die nötig sind, um die bestmögliche Unterstützung von Geschäftsprozessen durch die IT-Organisation zu erreichen. | |
| **ITIL®** | *Information Technology Infrastructure Library*. Eine Sammlung von "Best Practices", die sich zum De-Facto Standard für die Lieferung von Services entwickelt hat. | |

### 1.2 Service vs. Produkt

Services unterscheiden sich wesentlich von Produkten:

*   **Zusammenfall von Konsum und Produktion** (*Uno Actu*-Prinzip).
*   **Fehlende Lagerfähigkeit** und Vergänglichkeit (können nicht gelagert werden).
*   **Kein Eigentumstransfer**.
*   **Unvorhersehbare Qualität**, direkt wirksam beim Kunden.
*   Das **Verhalten der Mitarbeitenden** ist ein zentrales Element bei der Erbringung von Services.

### 1.3 Stakeholder

*   **Kunden:** Beauftragen den Service Provider, bezahlen für den Service und definieren/vereinbaren die Service Level Ziele.
*   **User (Anwender):** Nutzen den erbrachten Service.
*   **Supplier (Lieferanten):** Dritte, die Waren oder Services liefern, die für die Bereitstellung des Services erforderlich sind (Underpinning Contract Partner).

## 2. Das SOUSIS-Modell

Das SOUSIS-Modell dient als SLA-Framework, um IT-Services transparent zu beschreiben und belastbare Vereinbarungen zu erstellen.

| Element | Akronym | Beschreibung |
| :--- | :--- | :--- |
| **SLA** | Service Level Agreement | Alle Serviceverpflichtungen gegenüber Kunden. Vereinbart die zugesicherte Leistung. | |
| **OLA** | Operational Level Agreement | Interne Vereinbarung zwischen internen IT-Fachbereichen zur Erfüllung eines SLA. Hat keinen juristischen Anteil. | |
| **UC** | Underpinning Contract | Extern gerichtete Vereinbarung mit Dritten/Lieferanten zur Teilleistungserbringung eines SLA. Hat einen rechtswirksamen Anteil. | |
| **Servicekatalog** | | Bereitstellung einer zentralen und konsistenten Informationsquelle zu allen Services. Enthält kundengerichtete und unterstützende Services. | |
| **IT-Rahmenvertrag** | | Regelt die juristische Geschäftsbeziehung und generelle, serviceübergreifende Rahmenbedingungen (z.B. Haftung, Kündigung, Datenschutz). | |
| **Service Level Kalkulator** | | Dient zur Durchführung von Verfügbarkeitskalkulationen und zur Ausweisung der End-to-End-Dienstleistung im SLA, basierend auf OLA/UC Werten. | |

### 2.1 Servicekatalog Attribute (Die Servicebeschreibung)

Ein Servicekatalog wird typischerweise durch folgende Attribute beschrieben:

*   Nummer, Bezeichnung, Servicekategorie.
*   Kurzbeschreibung (Text).
*   Enthalten/Nicht enthalten (Aufzählung).
*   Service Level (Kennzahle/n).
*   Betrieb (Störungspriorität/Kritikalität).
*   Preis.

### 2.2 SLA-Strukturen

*   **Servicebasiertes SLA:** Deckt einen Service ab, der für jeden Kunden identisch erbracht wird.
*   **Kundenbasiertes SLA:** Deckt alle Anforderungen eines Kunden oder einer Kundengruppe ab.
*   **Multi-Level-SLA:** Kombiniert verschiedene Anforderungen aus Unternehmenssicht mit den bereitgestellten Services.

## 3. Service Design und Anforderungen

### 3.1 Service Design Phase

Die Service Design Phase befasst sich mit der **Ermittlung der Kundenanforderungen** und deren **Überführung in Service- und Service-Management-Lösungen**.

**Ziele des Service Designs:** Verbesserung TCO, Verbesserung der Service Qualität, Sicherstellung der Konsistenz der Services, bessere Erfüllung der Businessanforderungen.

**Prozesse im Service Design (ITIL):**

1.  Design Coordination.
2.  Service Catalogue Management.
3.  **Service Level Management**.
4.  Capacity Management (definiert und überwacht Kapazitäten).
5.  Availability Management (definiert und überwacht Verfügbarkeit).
6.  IT Service Continuity Management (Bewältigung von Katastrophen).
7.  Information Security Management (Richtlinien zu Vertraulichkeit, Integrität, Verfügbarkeit).
8.  Supplier Management (Verwaltung von Lieferanten/Verträgen).

### 3.2 Service Anforderungen

Anforderungen an einen Service lassen sich in drei Hauptkategorien unterteilen:

1.  **Funktionale Anforderungen:** Beschreiben Aufgaben oder Funktionen, die ein Service erfüllen muss.
2.  **Management und operationelle Anforderungen** (Nicht-Funktionale): Umfassen Qualitätsaspekte und unterstützen die Realisierbarkeit des Services. Beispiele:
    *   Verfügbarkeit und Zuverlässigkeit.
    *   Sicherheit.
    *   Wartbarkeit und Betriebsfähigkeit.
    *   Messbarkeit und Rapportierbarkeit.
3.  **Usability Anforderungen:** Stellen sicher, dass die Services die Erwartungen des Benutzers bezüglich einfacher Benutzung und Bedienerfreundlichkeit erfüllen.

## 4. Metriken, Kalkulation und Überwachung

### 4.1 Metriken und Kenngrössen

Metriken sollen Service Management-Prozesse unterstützen, verständlich sein, ohne großen Overhead erhoben werden und die Grundlage für Planung, Berechnung und Verrechnung bilden.

**Wichtige Kennzahlen:**

*   **MTTF** (Mean Time to Failure): Mittlere erwartete Zeit bis zum nächsten Ausfall.
*   **MTBF** (Mean Time between Failure): Mittlere Betriebszeit bis zum nächsten Ausfall.
*   **MTTR** (Mean Time to Recover): Mittlere Zeit der Servicewiederherstellung.

**Leistungsziele** sollten dem **SMART**-Prinzip unterliegen: **S**pecific, **M**easurable, **A**chievable, **R**elevant and **T**imely.

### 4.2 Verfügbarkeitskalkulation

Die **Gesamtverfügbarkeit** eines Services, der aus mehreren Komponenten ohne Redundanz besteht (End-to-End), wird durch die **Multiplikation der Verfügbarkeitswerte** der einzelnen Technologiebereiche berechnet.

*Beispiel:* Verfügbarkeit End2End = System 1 Verfügbarkeit \* System 2 Verfügbarkeit \* ....

### 4.3 Überwachung und Reporting

Das Berichtswesen muss Richtlinien folgen, die festlegen:

*   Wer welche Berichte erhält.
*   Was gemessen und worüber berichtet wird.
*   Die zu benutzenden Begriffe und Grenzwerte.
*   Die Berechnungsgrundlagen und die Periodizität der Berichte.

Kunden benötigen Informationen über **Verfügbarkeit, Zuverlässigkeit und Leistung** des Services.

## 5. Risiken, Kosten und Sourcing

### 5.1 Risikomanagement und Bonus/Malus

*   **Risiko:** Ein unsicheres Ergebnis, eine positive Gelegenheit oder eine negative Bedrohung.
*   **Risikoteilung:** Services reduzieren die Risiken für das Geschäft des Kunden, erhöhen aber gleichzeitig jene des Service Providers.

**Bonus/Malus (Penalty):** Spezifiziert die Konsequenzen bei Abweichungen von den vereinbarten Service-Levels.

*   **Malus (Penalty):** Konsequenzen bei Verletzung eines Service-Levels (z.B. finanzielle Entschädigung).
*   **Bonus:** Konsequenzen bei Übererfüllung eines Service-Levels (z.B. Kostensenkung).

### 5.2 Sourcing-Modelle

| Modell | Beschreibung |
| :--- | :--- |
| **Insourcing** | Die Produktion der Services wird im eigenen IT-Betrieb durchgeführt. |
| **Outsourcing** | Die Produktion wird von einer Drittpartei übernommen. | 
| **Co-Sourcing** | Services werden zusammen mit einer Partnerfirma kooperativ unterstützt. | 
| **Multi-Sourcing** | Ein Service wird von mehreren externen Partnern produziert. | 
| **BPO (Business Process Outsourcing)** | Ein ganzer Geschäftsprozess wird durch eine Drittpartei übernommen. | 
| **KPO (Knowledge Process Outsourcing)** | Wissen eines ganzen Arbeitsbereichs wird ausgelagert. | 

### 5.3 Cloud Servicemodelle

*   **IaaS (Infrastructure as a Service):** Nutzungszugang von virtualisierten Computerhardware-Ressourcen (Rechner, Netze, Speicher). Nutzer sind für die Installation und den Betrieb ihrer Software verantwortlich.
*   **SaaS (Software as a Service):** Nutzungszugang von Software-Sammlungen und Anwendungsprogrammen. Wird auch als *Software on demand* bezeichnet.
*   **PaaS (Platform as a Service):** Nutzungszugang von Programmierungs- oder Laufzeitumgebungen. Nutzer entwickeln oder lassen ihre eigenen Anwendungen innerhalb einer vom Dienstanbieter bereitgestellten Softwareumgebung ausführen.
*   **BPaaS (Business Process as a Service):** Outsourcing von Geschäftsprozessen in eine Cloud.

## 6. Verwandte Modelle und Frameworks

### 6.1 ISO/IEC 20000:2018

*   International anerkannter **Qualitätsstandard für IT Service Management (Norm)**.
*   Gibt die Mindestanforderungen vor, die ein IT-Service-Provider erfüllen sollte, um kunden- und businessorientierte Dienstleistungen anzubieten.

### 6.2 CMMI® (Capability Maturity Model Integrated)

Referenzmodell, das bewährte Praktiken zusammenfasst, um eine kontinuierliche Prozessverbesserung zu unterstützen.

**Die 5 Reifegrade:**

1.  **Initial (1):** Prozesse sind unvorhersehbar, schlecht kontrolliert und reaktiv.
2.  **Managed (2):** Prozesse sind geplant und ausgeführt, grundlegende Projektmanagementprozesse sind etabliert.
3.  **Defined (3):** Prozesse sind proaktiv, gut dokumentiert und standardisiert; Konsistenz über alle Projekte hinweg.
4.  **Quantitatively Managed (4):** Prozesse sind quantitativ verstanden und gesteuert, Metriken werden zur Steuerung verwendet.
5.  **Optimizing (5):** Fokus liegt auf kontinuierlicher Prozessverbesserung und Innovation.

### 6.3 COBIT® (Control Objectives for Information and related Technology)

*   Framework für die Umsetzung von **IT Governance** (Steuerung und Kontrolle der IT).
*   Basiert auf international anerkannten Standards und Frameworks (z.B. ITIL®).
*   Konzentriert sich darauf, **was** zur Erreichung einer angemessenen Steuerung erforderlich ist, nicht primär auf das **wie**.

**Wichtige Information Criteria (Ziele):**

*   **Confidentiality** (Vertraulichkeit von Daten).
*   **Integrity** (Integrität, Vollständigkeit und Richtigkeit von Daten).
*   **Availability** (Verfügbarkeit von Daten).
*   Effektivität, Effizienz, Verlässlichkeit, Einhaltung (Compliance).
