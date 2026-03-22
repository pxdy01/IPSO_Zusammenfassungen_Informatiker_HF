### Prüfungsspicker: IT-Sicherheit und Risikomanagement (BSI 200-x & ISO 27001\)

#### 1\. Grundlagen und Definitionen (Block 1\)

* **Informationssicherheit:** Schutz von Informationen jeglicher Art (Papier, Köpfe, IT). Ziel ist die Absicherung der Grundwerte.  
* **IT-Sicherheit:** Teilmenge der Informationssicherheit; Fokus auf Schutz elektronisch gespeicherter Informationen und deren Verarbeitung.  
* **Cyber-Sicherheit:** Ausweitung der IT-Sicherheit auf den **Cyber-Raum**. Umfasst sämtliche mit dem Internet und vergleichbaren Netzen verbundene IT sowie darauf basierende Kommunikation, Prozesse und Informationen.  
* **Klassische Schutzziele (CIA-Triade):**
  * **Vertraulichkeit (Confidentiality):** Schutz vor unbefugter Preisgabe.  
  * **Integrität (Integrity):** Sicherstellung der Korrektheit von Daten und Systemfunktionen.  
  * **Verfügbarkeit (Availability):** Dienste und Informationen sind wie vorgesehen nutzbar.  

* **Erweiterte Grundwerte (generische Oberbegriffe):** Authentizität, Verbindlichkeit, Zuverlässigkeit, Resilienz und Nichtabstreitbarkeit.  
* **Gefährdungskategorien:**
  * *Höhere Gewalt:* Feuer, Wasser, Erdbeben, Sturm.  
  * *Fehlhandlungen:* Versehentliche Weitergabe, mangelnde Kenntnis, Ausfall von Schlüsselpersonen.  
  * *Technisches Versagen:* Missglückte Software-Updates, Hardware-Defekte.  
  * *Vorsätzliche Handlungen:* Schadsoftware, Abhören, Diebstahl, Social Engineering.


#### 2\. Normen und Standards (Block 2\)

| Standard      | Zweck und Inhalt (laut BSI 200-1)                            |
| ------------- | ------------------------------------------------------------ |
| ISO/IEC 27000 | Überblick über die ISMS-Familie, Zusammenhänge und zentrales Vokabular. |
| ISO/IEC 27001 | Normative Anforderungen an Einführung, Betrieb und Zertifizierung eines ISMS. Enthält den  Annex A  mit über 100 Controls (Maßnahmen). |
| ISO/IEC 27002 | Leitfaden für die Management-Ebene; Empfehlungen zur Auswahl und Umsetzung der Controls aus 27001. |
| ISO/IEC 27004 | Methoden zur Bewertung der Wirksamkeit des ISMS mittels Monitoring, Messung und Analyse (Kennzahlen). |
| ISO/IEC 27005 | Rahmenempfehlungen zum Risikomanagement für Informationssicherheit (basiert auf ISO 31000). |

**Nationale und sonstige Standards:**

* **BSI 200-1 bis 200-3:** Grundlegende Standards zum ISMS-Aufbau, zur Grundschutz-Methodik und zur Risikoanalyse (ISO 27001 kompatibel).  
* **BSI 100-4:** Methodik zur Etablierung eines behörden- oder unternehmensweiten Notfallmanagements.  
* **NIST SP 800-Serie:** US-Standards (besonders SP 800-53) mit weitreichendem Einfluss auf globale Sicherheits-Controls.  
* **COBIT 5:** Framework zur Governance und zum Management der Unternehmens-IT zur Erreichung von Geschäftszielen.  
* **ITIL:** Best Practices für IT-Service-Management; ein stabiler IT-Betrieb ist essenzieller Stützpfeiler für das ISMS.  
* **PCI DSS:** Spezifische Sicherheitsanforderungen für die Verarbeitung von Kreditkartentransaktionen.

#### 3\. Das Managementsystem für Informationssicherheit (ISMS) (Block 3\)

**ISMS-Komponenten (nach BSI 200-1, Abb. 2):**

1. **Managementprinzipien:** Vorgaben für Führung, Verantwortung und Integration.  
2. **Ressourcen:** Bereitstellung von Zeit, Personal und finanziellen Mitteln.  
3. **Mitarbeiter:** Einbindung durch Sensibilisierung, Schulung und Motivation.  
4. **Sicherheitsprozess:** Kernstück bestehend aus *Leitlinie*,  *Sicherheitsorganisation* und *Sicherheitskonzept*.

**Der PDCA-Zyklus im Sicherheitsprozess:**

* **Plan (Planung):** *Rahmenbedingungen identifizieren, Sicherheitsziele bestimmen, Sicherheitsstrategie ausarbeiten, Sicherheitskonzept und \-organisation planen.*  
* **Do (Umsetzung):** *Sicherheitskonzept und \-organisation umsetzen, Maßnahmen realisieren, Mitarbeiter schulen.*  
* **Check (Erfolgskontrolle):** *Wirksamkeit der Maßnahmen prüfen, interne Audits durchführen, Managementberichte erstellen, Zielerreichung überwachen.*  
* **Act (Optimierung):** *Mängel beseitigen, Prozesse verbessern, Strategie und Konzepte an geänderte Bedingungen anpassen.*

#### 4\. Management-Prinzipien und Ressourcen (Block 4\)

**Checkliste: Zentrale Management-Pflichten (BSI 200-1, Kap. 4.1)**

- [ ] **Gesamtverantwortung:** Übernahme der Verantwortung für das ordnungsgemäße Funktionieren (Chefsache).  

- [ ] **Steuerung:** Sicherheitsprozess initiieren, Strategie verabschieden und Risikoverantwortung tragen.  

- [ ] **Integration:** Einbindung der Sicherheit in alle Prozesse (Projektmanagement, Management).  

- [ ] **Zielsetzung:** Festlegung realistischer, messbarer und erreichbarer Sicherheitsziele.  

- [ ] **Wirtschaftlichkeit:** Kosten-Nutzen-Abwägung und Priorisierung effektiver Maßnahmen.  

- [ ] **Vorbildfunktion:** Einhaltung der Regeln und Teilnahme an Schulungen durch die Leitung.

**Verbindliche Dokumentationsaufgaben DOK (nach BSI 200-1):**

| Kapitel / Anforderung | Dokumentationsinhalt                                         |
| --------------------- | ------------------------------------------------------------ |
| 7.1 Planung           | Informationssicherheitsziele und die Sicherheitsleitlinie (Policy). |
| 7.1 Geltungsbereich   | Definition des Geltungsbereichs (Scope / Informationsverbund). |
| 7.2 Organisation      | Aufbau der Sicherheitsorganisation, Rollen und Verantwortlichkeiten. |
| 8.1 Methodik          | Auswahl der Risikoanalysemethode und Definition der Risikokategorien. |
| 8.1 Risikoanalyse     | Identifizierte Risiken, Bedrohungen, Schwachstellen und Schadenspotenziale. |
| 8.1 Risikobehandlung  | Gewählte Behandlungsstrategie pro Risiko inklusive Genehmigung der Leitung. |
| 8.1 Maßnahmen         | Auswahl der Sicherheitsmaßnahmen und Begründung der Eignung. |
| 8.2 Realisierung      | Realisierungsplan mit Prioritäten, Terminen und Verantwortlichen. |
| 8.3 Kontrolle         | Ergebnisse von Audits, Wirksamkeitsprüfungen und Managementbewertungen. |

**Ressourcen und Mitarbeiter:**

*   Investitionen in Personal und Know-how sind oft effektiver als reine Technik-Investitionen.  
*   Awareness und kontinuierliche Schulung aller Mitarbeiter sind Grundvoraussetzungen für den Erfolg.  
*   Ein strukturierter, stabiler IT-Betrieb bildet das notwendige Fundament für wirksame Sicherheit.

#### 5\. Sicherheitsleitlinie und Organisation (Block 5\)

**Inhalte der Sicherheitsleitlinie (Policy):**

| Kapitel                      | Inhalt / Zweck                                               |
| ---------------------------- | ------------------------------------------------------------ |
| Stellenwert & Ziele          | Warum ist Sicherheit wichtig? (Schutz der Geschäftsgeheimnisse, Vertrauen der Kunden). Bezug zu den allgemeinen Unternehmenszielen. |
| Sicherheitsstrategie         | Festlegung des angestrebten Sicherheitsniveaus (z.B. „Schutz der Kronjuwelen nach dem Stand der Technik“). |
| Geltungsbereich (Scope)      | Für wen und was gilt die Policy? (Alle Mitarbeiter, Standorte, IT-Systeme, auch Externe/Dienstleister). |
| Bekenntnis der Leitung       | Explizite Aussage, dass die Geschäftsführung hinter den Maßnahmen steht und die Ressourcen bereitstellt. |
| Sicherheitsorganisation      | Wer trägt die Verantwortung? (Benennung des CISO/ISB, Aufgaben der Mitarbeiter, Rolle des IS-Boards). |
| Compliance & Sanktionen      | Hinweis auf Gesetze (DSGVO) und interne Regelungen. Konsequenzen bei vorsätzlichen Verstößen. |
| Kontinuierliche Verbesserung | Verpflichtung zur regelmäßigen Überprüfung und Aktualisierung (PDCA-Zyklus). |

**Rollenmodell (Referenz Universität Mannheim):**

| Rolle             | Verantwortlichkeit                                           |
| ----------------- | ------------------------------------------------------------ |
| Rektorat          | Gesamtverantwortung, Freigabe der Leitlinie/Strategie, Ressourcenbereitstellung. |
| CISO / ISB        | Leitung der Stabsstelle, Steuerung des ISMS, Beratung, Berichtswesen an Leitung. |
| Lenkungsausschuss | Strategische Steuerung, Priorisierung von Maßnahmen, Entscheidungsvorbereitung. |
| Universitäts-IT   | Absicherung der **zentralen IT-Infrastruktur**, technische Realisierung. |

**Rollenmodell (Referenz B4)**

| Rolle                                      | Verantwortlichkeit                                           |
| ------------------------------------------ | ------------------------------------------------------------ |
| IS-Management Team (IS-Board)              | Strategische Steuerung des ISMS, Priorisierung von Sicherheitsmaßnahmen, Ressourcenallokation und Entscheidung über die Akzeptanz von Restrisiken. |
| Chief Information Security Officier (CISO) | Gesamtverantwortung für den Sicherheitsprozess, Beratung der Geschäftsleitung, Berichterstattung zum Status der Informationssicherheit und Pflege des ISMS. |
| IT-Sicherheitsbeauftragter                 | Fokus auf die operative und technische Umsetzung von Sicherheitsmaßnahmen innerhalb der IT-Infrastruktur (Server, Netze, Clients) sowie Überwachung des sicheren IT-Betriebs. |
| Datenschutzbeauftragter                    | Überwachung der Einhaltung von Datenschutzvorschriften (z.B. DSGVO), Beratung bei der Verarbeitung personenbezogener Daten und Durchführung von Datenschutz-Folgenabschätzungen. |
| Notfallbeauftragter (BCM                   | Sicherstellung der Business Continuity (Betriebskontinuität), Erstellung von Notfallplänen und Koordination von Maßnahmen zur Wiederherstellung kritischer Geschäftsprozesse. |
| Interne Revision                           | Unabhängige und objektive Prüfung der Wirksamkeit der Sicherheitskontrollen und Prozesse innerhalb der Organisation zur Identifikation von Schwachstellen. |
| Kontrolle (IKS)                            | Durchführung prozessintegrierter Kontrollen (Internes Kontrollsystem) zur Absicherung der Geschäftsprozesse und Sicherstellung der Regelkonformität (Compliance). |
| Externe Revision                           | Unabhängige Prüfung durch externe Dritte (z.B. Auditoren für Zertifizierungen), um die Konformität des ISMS mit Standards wie ISO 27001 oder BSI Grundschutz zu bestätigen. |

**Traffic Light Protocol (TLP) zur Informationsweitergabe:**

* ⚪  **WHITE (öffentlich):** Keine Vertraulichkeit; uneingeschränkte Weitergabe möglich.  
* 🟢  **GREEN (intern):** Für dienstlichen Gebrauch/Partner; keine Veröffentlichung.  
* 🟡  **AMBER (vertraulich):** Nur definierter Personenkreis; Weitergabe an Dritte nur bei Notwendigkeit.  
* 🔴  **RED (streng vertraulich):** Nur für konkreten Teilnehmerkreis (z.B. Sitzung); Weitergabe untersagt.

#### 6\. IT-Grundschutz-Methodik nach BSI 200-2 (Block 6\)

**Absicherungsvarianten:**

Der BSI-Standard 200-2 (IT-Grundschutz-Methodik) bietet drei verschiedene Absicherungsvarianten an. Die Institutionen können je nach eigenen personellen und finanziellen Ressourcen sowie dem individuellen Schutzbedarf zwischen den folgenden drei Vorgehensweisen wählen:

**1. Basis-Absicherung** *(Behandelt in Block 6, Folie "Wahl der Vorgehensweise Basis Absicherung")*

- **Fokus und Ziel:** Die Basis-Absicherung bietet einen schnellen und einfachen Einstieg in das Informationssicherheitsmanagement. Das Ziel ist es, das Sicherheitsniveau zunächst "in der Breite" anzuheben und die größten Gefahren schnellstmöglich zu senken.
- **Umfang:** Der Geltungsbereich umfasst hierbei häufig die gesamte Institution. Es werden bei der Überprüfung jedoch ausschließlich die elementaren Basis-Anforderungen des IT-Grundschutz-Kompendiums herangezogen. Aufwändige, tiefergehende Risikoanalysen entfallen bei diesem Ansatz komplett.
- **Ergebnis:** Es entsteht ein sehr schlankes Managementsystem, das vom BSI oft auch als "Bonsai-ISMS" bezeichnet wird. Dies ist besonders für kleine und mittelständische Kommunen oder Betriebe geeignet.
- **Wichtige Eigenschaft (laut Vorlesung):** Die Basis-Absicherung ist in dieser Form **nicht zertifizierbar**.

**2. Kern-Absicherung** *(Behandelt in Block 6, Folie "Wahl der Vorgehensweise Kern Absicherung")*

- **Fokus und Ziel:** Im Gegensatz zur breiten Basis-Absicherung geht die Kern-Absicherung in die Tiefe, ist aber in der Fläche stark eingeschränkt. Sie konzentriert sich ausschließlich auf den Schutz der elementaren, besonders geschäftskritischen Prozesse, Ressourcen und Werte – die sogenannten **"Kronjuwelen"**.
- **Umfang:** Der Geltungsbereich ist auf diesen herausragenden, kleinen Bereich beschränkt. Für diesen ausgewählten Kernbereich werden jedoch alle tiefergehenden Schritte der Absicherung (inklusive Basis- und Standard-Anforderungen) vollständig durchlaufen.
- **Wichtige Eigenschaft (laut Vorlesung):** Da sie einen in sich geschlossenen, tiefgehenden Schutz für die identifizierten Assets bietet, ist die Kern-Absicherung – im Gegensatz zur Basis-Absicherung – **zertifizierbar**.

**3. Standard-Absicherung** *(Behandelt in Block 6, Folie "Wahl der Vorgehensweise Standard Absicherung")*

- **Fokus und Ziel:** Dies ist die vom BSI empfohlene, vollständige Vorgehensweise. Das Ziel ist es, einen umfassenden und ganzheitlichen Schutz für alle Prozesse, IT-Systeme und Bereiche einer Institution zu erreichen.
- **Umfang:** Der Geltungsbereich umfasst die gesamte Institution oder einen sehr großen Informationsverbund. Bei der Standard-Absicherung werden neben den Basis-Anforderungen verpflichtend auch alle Standard-Anforderungen geprüft und umgesetzt. Wenn Bereiche identifiziert werden, die einen sehr hohen Schutzbedarf aufweisen oder für die es keine passenden BSI-Bausteine gibt, werden diese zusätzlich durch detaillierte Risikoanalysen (gemäß BSI-Standard 200-3) abgesichert.
- **Wichtige Eigenschaft:** Diese Variante wird von Beginn an im gesamten Informationsverbund umgesetzt. Sie bildet die Anforderungen der Norm ISO/IEC 27001 vollumfänglich ab und ist somit die Basis für eine reguläre "ISO 27001-Zertifizierung auf der Basis von IT-Grundschutz".

**Zusammenfassung und Strategie:** 
Oftmals stellen die Basis- sowie die Kern-Absicherung lediglich den ersten Einstieg dar. Institutionen können mit einer dieser beiden methodischen Varianten starten und ihr Sicherheitskonzept zu einem späteren Zeitpunkt nahtlos erweitern, um schlussendlich die vollumfängliche Standard-Absicherung zu erreichen.

**Der iterative Prozess (9 Schritte nach B6):**

1. Strukturanalyse (Identifikation von Anwendungen, Systemen, Netzen).  

2. Schutzbedarfsfeststellung (Kategorien: Normal, Hoch, Sehr Hoch).  

3. Modellierung (Auswahl der Bausteine).  

4. Auswahl Maßnahmen & IT-Grundschutz-Check 1 (Soll-Ist-Vergleich).  

5. Realisierungsplan (Umsetzungsplanung).  

6. Risikoanalyse (für Bereiche mit hohem Schutzbedarf oder Lücken).  

7. Maßnahmen konsolidieren & ergänzende Sicherheitsanalyse.  

8. **Akzeptanz/Behandlung** (Managemententscheidung über Restrisiken).  

9. IT-Grundschutz-Check 2 (Prüfung der Umsetzung).

**Modellierung (Schichtenmodell des Kompendiums):**

* **Prozess-Bausteine:** 
  * ISMS (Management): Befasst sich mit dem generellen Management der Informationssicherheit.
  * ORP (Organisation/Personal): Beinhaltet Anforderungen an die Organisation, das Personal sowie Sensibilisierung, Schulung und das Berechtigungsmanagement.
  * CON (Konzepte): Umfasst übergreifende Konzepte wie Kryptokonzepte, Datensicherungskonzepte oder Richtlinien zum Löschen und Vernichten von Daten. 
  * OPS (Betrieb): Regelt den sicheren IT-Betrieb, inklusive Outsourcing, Patch-Management und dem Schutz vor Schadprogrammen.
  * DER (Detektion/Reaktion): Behandelt das Erkennen von Sicherheitsvorfällen und das Notfallmanagement.

* **System-Bausteine:** 
  * INF (Infrastruktur): Behandelt physische Aspekte wie allgemeine Gebäude, Serverräume, Rechenzentren oder die IT-Verkabelung.
  * SYS (IT-Systeme): Umfasst Endgeräte und Server, vom "Allgemeinen Client" über spezielle Betriebssysteme (wie Windows oder Unix) bis hin zu Laptops und Smartphones.
  * NET (Netze): Regelt die Netzarchitektur, Router, Switches, Firewalls und WLAN-Netze.
  * APP (Anwendungen): Deckt konkrete Softwareanwendungen ab, beispielsweise Office-Produkte, Webserver, Groupware oder relationale Datenbanksysteme.
  * IND (Industrielle IT/IoT): Widmet sich speziellen industriellen Systemen wie Betriebs- und Steuerungstechnik oder Sensoren.


**Das Vorgehen bei der Modellierung:** 
Jedem Zielobjekt des betrachteten Bereichs werden die relevanten Bausteine aus diesen Schichten zugeordnet. Eine Besonderheit hierbei ist, dass **oft mehrere Bausteine für ein einzelnes technisches System kombiniert** werden müssen, um alle Sicherheitsanforderungen abzudecken. *Beispiel:* Für einen Webserver, der unter einem Unix-Betriebssystem läuft, müssen die Bausteine "Allgemeiner Server", "Server unter Unix" und "Webserver" parallel angewendet werden.

Sollte es für ein spezielles Zielobjekt – etwa eine völlig neue Technologie oder eine spezifische "Bare Metal Server"-Hardware – keinen passenden Baustein im Kompendium geben, kann dieses Objekt nicht hinreichend modelliert werden. Solche Zielobjekte müssen für eine **individuelle Risikoanalyse** vorgemerkt werden, woraus dann im Bedarfsfall ein benutzerdefinierter Baustein abgeleitet wird.

#### 7\. Risikomanagement und Risikoanalyse (Block 7\)

**Schutzbedarfsfeststellung (BSI 200-1):**

1. **Normal:** Schadensauswirkungen begrenzt und überschaubar.

2. **Hoch:** Auswirkungen beträchtlich, aber nicht existenzbedrohend.

3. **Sehr Hoch:** Existenzbedrohendes oder katastrophales Ausmaß.

4. *Vorgehen:* Schadensanalyse bzgl. CIA-Verlust für jeden Geschäftsprozess.

**Risikoanalyse nach BSI 200-3:**

1. *Qualitatives Verfahren:* Bewertung von Eintrittswahrscheinlichkeit (selten bis sehr häufig) vs. Schadenshöhe (vernachlässigbar bis existenzbedrohend).  

2. **Risikobehandlungsoptionen (Entscheidung durch Leitungsebene):**
   1. **Risikovermeidung:** Ursache ausschließen (z.B. Prozess einstellen).  
   2. **Risikoreduktion:**  Maßnahmen zur Senkung des Risikos umsetzen.  
   3. **Risikotransfer:**  Übertragung an Dritte (z.B. Versicherung, Outsourcing).  
   4. **Risikoübernahme (Akzeptanz):**  Bewusstes Tragen des Restrisikos auf Basis von Fakten.

#### 8\. Aufrechterhaltung, Zertifizierung und Revision (Block 8\)

* **Erfolgskontrolle:** Regelmäßige interne Audits, Nutzung von **Kennzahlen** (nach ISO 27004\) und Erstellung von **Managementberichten** zur Steuerungsunterstützung.  
* **Zertifizierung:** "ISO 27001-Zertifizierung auf der Basis von IT-Grundschutz". Externes Audit durch BSI-zertifizierte Auditoren; Zertifikatserteilung durch das BSI.  
* **IS-Revision:** Leitfaden des BSI zur Statusfeststellung und Identifikation von Schwachstellen; dient als Werkzeug der Erfolgskontrolle.

