# Zusammenfassung Block 1: IT-Sicherheits- und Risikomanagement (SIRI)

Dieses Dokument ist Teil des Moduls "IT-Sicherheits- und Risikomanagement SIRI" und zielt darauf ab, den Teilnehmern praxisorientierte Fähigkeiten in diesem Bereich zu vermitteln.

**Kernziele des Moduls:**

* Die Notwendigkeit der Verantwortungsübernahme durch die höchste Leitungsebene im Bereich Informationssicherheit begründen.
* Die primären Schutzziele wie Verfügbarkeit, Vertraulichkeit und Integrität nach ISO-27000 erklären, ebenso wie weitere Ziele wie Authentizität und Verbindlichkeit.
* Angreifertypen und deren Motive im unternehmerischen Kontext interpretieren.
* Wichtige Quellen zur Informationsbeschaffung gegenüberstellen.
* Bedrohungen erheben und dem Management verständlich darlegen.

**Grundlagen der Informationssicherheit:**

* Informationssicherheit ist keine alleinige Aufgabe der IT-Abteilung, sondern betrifft die gesamte Firma.
* Die Gesamtverantwortung liegt beim obersten Organ (Geschäftsleitung/Verwaltungsrat) und ist nicht delegierbar.
* Die Einbettung der Informationssicherheit in das gesamte Unternehmen erfordert die Berücksichtigung von Strategie, Prozessen, Organisation, Applikation/Software, Hardware, Datenmanagement und Telekommunikation.
* Compliance aus Sicht des Unternehmens erfordert die Berücksichtigung geltender Gesetze und Verträge sowie ein gesetzes- und vertragskonformes Verhalten, das im ISMS zwingend berücksichtigt werden muss (z.B. DSG, OR, BSI 100-X, ISO 2700X).

**Risikomanagement und Schutzobjekte:**

* Risikomanagement (IKS) umfasst die IT-Sicherheit und das ISMS.
* Schutzobjekte sind materielle Vermögenswerte (Immobilien, Maschinen, Informatikmittel etc.) und immaterielle Vermögenswerte (Guter Ruf, Firmenwert, Wissen, Patente etc.).
* Die primären Schutzziele sind Vertraulichkeit, Integrität und Verfügbarkeit (CIA-Modell). ISO/IEC 27000 erweitert dies um Authentizität, Zurechenbarkeit, Nicht-Abstreitbarkeit und Zugriffskontrolle.
* Der Schutzbedarf wird aus Sicht der Prozesse (Kritikalität, Sensitivität) bestimmt.
* Datenschutz fokussiert auf Vertraulichkeit und Integrität, während Datensicherheit Vertraulichkeit, Integrität und Verfügbarkeit umfasst.

**Gefährdungen und Angreifer:**

* Gefährdungskategorien umfassen höhere Gewalt, organisatorische Mängel, menschliche Fehlhandlungen, technisches Versagen und vorsätzliche Handlungen.
* Angreifertypen und deren Motive:
  * **(Ethical) Hacker (White Hat):** Setzen sich aktiv für bessere Sicherheit ein.
  * **Cracker (Black Hat):** Cyberkriminelle, die Geld wollen.
  * **Skriptkiddie:** Jugendliche mit Geltungsdrang.
  * **Hacktivisten:** Gruppierungen mit eigenen Interessen.
* Typische Angriffsformen können aktiv/passiv (Wie?), gezielt/ungezielt (An wen?) und intern/extern (Von Wo?) sein.
* Erfolgreiche Malware-Angriffe erfordern oft Benutzeraktionen (Anklicken von Links, Öffnen von Anhängen), erhöhte Rechte des Schadcodes, oder veraltete Software/Systeme. Massnahmen sind Awareness-Schulungen, Content-Filter, eingeschränkte Benutzerrechte, UAC, Applikations-Allowlisting, zeitnahe Updates und Exploit-Schutz.
* Das Hacking Vorgehensmodell umfasst: Auskundschaften/Footprinting, Scanning, Angriff/Hacking, Festsetzen und Zugriff verschleiern.

**Aktuelle Informationen und Quellen:**

* Es ist wichtig, aktuell zu bleiben und Informationen zu beschaffen (Lageberichte, News, Security Newsletter).
* Nützliche Quellen sind u.a. cybercrimepolice.ch, ncsc.admin.ch, bsi.de, heisec.de und allianz-fuer-cybersicherheit.de.

**Implementierung von Informationssicherheit:**

* Informationssicherheit sollte ganzheitlich umgesetzt werden (Technische, Organisatorische, Rechtliche, Menschliche Sicherheit).
* Ein geeignetes Management-System (ISMS) sollte etabliert und Prozesse umgesetzt werden. Das Management muss eine aktive Rolle übernehmen und Verantwortung tragen.
* Der PDCA-Zyklus (Plan-Do-Check-Act) ist ein Beispiel für die Sicherheitsarchitektur und das ISMS (BSI Grundschutz Methode). Die Schutzbedarfsfeststellung beginnt bei den primären Assets (Werte).


# Zusammenfassung Block 2: IT-Sicherheit und Risikomanagement (Vertiefung und Anwendung)

Dieser Block baut auf den Grundlagen auf und konzentriert sich auf die praktische Anwendung und Analyse von IT-Sicherheitsmassnahmen.

**Lernziele des Blocks:**
*   Einfache Expositionsanalysen mittels Internetanwendungen durchführen.
*   Den Schweregrad von Schwachstellen interpretieren und mittels CVE und CVSS einordnen.
*   Den Einfluss von Social Engineering Szenarien verstehen.
*   Den Unterschied zwischen einem Ereignis und einem Vorfall begründen.
*   Ein Sicherheits-Assessment für ein Unternehmen oder einen Unternehmensteil planen und durchführen.

**Vertiefung der Themen (basierend auf den Folien):**

*   **Schwachstellen-Management:**
    *   **Schwachstellen-Typen und ihre Einstufung:** Angriffe werden nach Erkennbarkeit, Wert des Angriffsziels, Kosten/Ausdauer für einen Angriff und Schadenhöhe eingestuft. APT-Angriffe werden als besonders unauffällig beschrieben.
    *   **Ausnutzung von Schwachstellen:** Schwachstellen (Lücken) sind zentrale Risiken. Cyberkriminelle nutzen diese mittels Exploits (Malware) aus, um Zugriff auf Systeme und persönliche Daten zu erlangen.
    *   **Hacking Vorgehensmodell:** Umfasst Auskundschaften/Footprinting, Scanning, Angriff/Hacking, Festsetzen und Zugriff verschleiern.
    *   **Schwachstellen-Analyse-Tools:** Tools wie NMAP/Zenmap (Netzwerk-Scanning), OpenVAS (Vulnerability-Scanning) und CVE (Common Vulnerabilities and Exposures) helfen bei der Identifizierung und Bewertung von Schwachstellen.
    *   **Penetration Testing:** Eine praktische Überprüfung von Sicherheitsmassnahmen durch Blackbox, Whitebox oder Graybox Tests. Dies erfordert hohe Skills, einen klaren Auftrag, Plan und absolute Verschwiegenheit.

*   **Malware und Angriffsformen:**
    *   **Schadsoftware (Malware):** Bedroht Organisationen massiv. Quellen sind Internet, E-Mail, SMS/IM, soziale Netzwerke und USB-Speichermedien.
    *   **Gängige Angriffsformen:** Client-Site-Attacken über "getarnte" Malware (Trojaner, die ins RAM geladen werden).
    *   **Massnahmen gegen Malware:** Awareness-Schulungen, Content-Filter, eingeschränkte Benutzerrechte (UAC, App-Locker), Smart-Screen Filter, zeitnahe Updates, Exploit-Schutz, Einschränkung von Downloadmöglichkeiten, Sperrung von CMD/PowerShell etc.
    *   **Werkzeuge für gezielte Angriffe:** Manipulation von USB-Geräten (Rubber Ducky, Bash Bunny), Maus-Dongles, Ladekabeln und Netzwerkadaptern kann zur Kompromittierung genutzt werden.

*   **Schwachstelle Mensch (Social Engineering):**
    *   Social Engineering nutzt menschliche Schwächen (Neugier, Vertrauenswürdigkeit, Dringlichkeit, Druck, Autorität).
    *   Gefälschte Mailadressen und Phishing-Links sind gängige Methoden.
    *   Neue Angriffsmöglichkeiten wie Deepfake Hacks entstehen durch KI.

*   **IKT Security Assessment:**
    *   **IKT-Minimalstandard (CH):** Ziel ist es, mit geringem Aufwand ein akzeptables Sicherheitsniveau zu erreichen. Dies umfasst die Identifizierung von kritischen Infrastrukturen und die Bewertung des IST-Zustandes.
    *   **Werkzeuge und Methoden:** Es werden Werkzeuge und Methoden für Security-Scanning und Penetration Testing vorgestellt (z.B. NMAP, OpenVAS, CVE-Datenbank, VPN-Lösungen wie ProtonVPN, Webseiten-Prüftools wie dnslytics.com, securityheaders.com, haveibeenpwned.com).
    *   **Konkrete Massnahmen:** Regelmässiges Security-Scanning, Reduktion der Exposition, Sicherung von Diensten, Nutzung von VPN und 2-Faktor-Authentifizierung, Analyse von Schwachstellenberichten und die Erarbeitung von Behebungsmassnahmen.

Dieser Block betont die Bedeutung eines proaktiven und umfassenden Ansatzes zur IT-Sicherheit, der technische Massnahmen mit menschlichen Faktoren und analytischen Fähigkeiten kombiniert.

# Zusammenfassung: Informationssicherheits- und Risikomanagement (Block 3)

Die folgende Zusammenfassung gibt einen umfassenden Überblick über die Themen des Blocks 3 ("IT-Sicherheits- und Risikomanagement") basierend auf den bereitgestellten Unterlagen aus dem Verzeichnis 'Quelldateien/Block 3'.

---

## 1. Kerninhalte von 'Block 3' (SIRI_LD2023_V1_0_SV1_B3)
Der Fokus liegt auf der Etablierung eines ganzheitlichen Informationssicherheits-Managementsystems (ISMS).
*   **Ganzheitlicher Ansatz:** Informationssicherheit wird als Zusammenspiel von Technik (T), Organisation (O), Recht (R) und Mensch (M) betrachtet.
*   **Management-Aufgabe:** Ein ISMS muss zwingend von der Geschäftsleitung getragen werden. Es ist ein kontinuierlicher Prozess (PDCA-Zyklus), der mit ausreichenden Ressourcen ausgestattet werden muss.
*   **Strategische Ausrichtung:** Die Sicherheitsstrategie orientiert sich an der Geschäfts- und IT-Strategie. Zentrale Säulen sind die Sicherheitspolitik (Security Policy), die Sicherheitsstrategie sowie die konkreten Sicherheitskonzepte und die Sicherheitsorganisation.
*   **Wichtige Funktionen:** Rollen wie der Chief Information Security Officer (CISO/ISB), der Datenschutzbeauftragte und der Notfallbeauftragte (Business Continuity) sind für die Steuerung essenziell.
*   **Methodik:** Einsatz von Standards wie ISO 2700x und BSI IT-Grundschutz zur Analyse von Schwachstellen, Risikobehandlung und Planung von Maßnahmen.

## 2. Kernpunkte der ISO/IEC 27001:2013
Die ISO 27001 ist der internationale Standard für die Einführung, den Betrieb und die kontinuierliche Verbesserung eines ISMS.
*   **Anforderungen:** Umfasst den Kontext der Organisation, Führung (Leadership), Planung, Unterstützung, Betrieb, Leistungsbewertung und Verbesserung.
*   **Risikomanagement:** Ein zentraler Aspekt ist der risikobasierte Ansatz bei der Auswahl und Implementierung von Sicherheitsmaßnahmen.
*   **Annex A:** Enthält eine Referenzliste von 114 Maßnahmen (Controls) in 14 Kategorien (z. B. Zugangskontrolle, Kryptographie, physische Sicherheit), die als Grundlage für die Auswahl geeigneter Sicherheitsmaßnahmen dienen.
*   **PDCA-Modell:** Auch wenn nicht explizit genannt, folgt die Norm dem Plan-Do-Check-Act-Prinzip zur stetigen Qualitätsverbesserung.

## 3. Gemeinsamkeiten und Unterschiede der Sicherheitsleitlinien und -strategien
Die Analyse der Gruppenarbeit-Dateien (TU Graz, FH Flensburg, EGK, Kommunalverwaltungen, HWK, BSI) zeigt deutliche Muster:
*   **Gemeinsamkeiten:**
    *   **Grundwerte:** Alle Dokumente basieren auf den drei Schutzzielen Vertraulichkeit, Integrität und Verfügbarkeit.
    *   **Verantwortung:** Die oberste Leitung (Rektorat, Geschäftsführung, Behördenleitung) trägt immer die Gesamtverantwortung.
    *   **Compliance:** Rechtliche Vorgaben (DSGVO, KVG, landesspezifische Gesetze) sind zentrale Compliance-Treiber.
    *   **Rollenmodell:** Die Benennung eines ISB oder CISO als zentrale Instanz ist universell.
*   **Unterschiede:**
    *   **Detaillierungsgrad:** Dokumente für den akademischen Bereich (z. B. TU Graz) sind oft sehr detailliert in Bezug auf technische Richtlinien (z. B. Passwortkomplexität, IDM). Vorlagen für KMUs (HWK) oder kirchliche Einrichtungen sind eher auf grundlegende Leitlinien und Sensibilisierung fokussiert.
    *   **Klassifizierung:** Die Methoden zur Einstufung der Vertraulichkeit variieren (z. B. Traffic Light Protocol (TLP) bei Uni Mannheim vs. Stufen V1-V4 bei der EGK).
    *   **Kontext:** Während Behörden die Aufrechterhaltung des Gemeinwohls betonen, fokussieren private Unternehmen stärker auf Wettbewerbsvorteile und die Vermeidung von Reputationsschäden.

## 4. Struktur und Bedeutung von Sicherheitskonzepten und -organisationen
*   **Bedeutung des Sicherheitskonzepts:** Es dient als operatives Hilfsmittel zur Umsetzung der Sicherheitsstrategie. Es dokumentiert den Ist-Zustand, den Schutzbedarf und die daraus abgeleiteten Maßnahmen.
*   **Struktur eines Konzepts (nach BSI/ISO):**
    1.  **Geltungsbereich:** Festlegung des Informationsverbunds.
    2.  **Strukturanalyse:** Inventarisierung von IT-Systemen, Netzen und Anwendungen.
    3.  **Schutzbedarfsfeststellung:** Bewertung der Schadensauswirkungen (Normal, Hoch, Sehr Hoch).
    4.  **Modellierung:** Auswahl geeigneter Sicherheitsmaßnahmen basierend auf Bausteinen.
    5.  **Basis-Check:** Vergleich von Soll-Maßnahmen mit dem Ist-Zustand.
*   **Bedeutung der Sicherheitsorganisation:** Sie definiert die Strukturen, Prozesse und Verantwortlichkeiten. Eine starke Organisation (z. B. Lenkungsausschüsse, Einbindung der IT-Leitung) ist notwendig, um Informationssicherheit dauerhaft im Alltag zu verankern und nicht nur als rein technisches Projekt zu behandeln. Sie stellt sicher, dass Sicherheitsziele messbar sind und regelmäßig überprüft werden.

--- 
*Diese Zusammenfassung verdeutlicht, dass Informationssicherheit ein systematischer, managementgesteuerter Prozess ist, der über technische Lösungen hinausgeht und eine klare organisatorische Struktur erfordert.*

# Zusammenfassung Block 4: IT-Sicherheits- und Risikomanagement

Dieser Block, betitelt mit "IT-Sicherheits- und Risikomanagement", greift das Zitat von Sun Tzu auf: „Wenn du den Feind und dich kennst, brauchst du den Ausgang von hundert Schlachten nicht zu fürchten.“ Dies unterstreicht die Bedeutung von Wissen über Bedrohungen und die eigene Organisation im Bereich der IT-Sicherheit.

Die Agenda für diesen Block deutet auf eine Vertiefung und praktische Anwendung der gelernten Konzepte hin, mit einem Fokus auf "Repetitionstest" und "Zielüberprüfung M3". Die Inhalte umfassen:

*   **Grundlagen Informationssicherheit:** Auffrischung und Festigung der Kernkonzepte.
*   **Analyse von Schwachstellen und Vorfällen:** Techniken zur Identifizierung und Bewertung von Schwachstellen sowie zum Umgang mit Sicherheitsvorfällen.
*   **Grundlagen eines ISMS:** Vertiefung des Verständnisses für Informationssicherheits-Managementsysteme.
*   **Compliance und DSG:** Behandlung von regulatorischen Anforderungen, insbesondere im Hinblick auf den Datenschutz.
*   **BSI IT-Grundschutz-Methodik:** Vertiefung der Anwendung der Methodik des Bundesamtes für Sicherheit in der Informationstechnik.
*   **Risikomanagement und Risikobewertung:** Vertiefte Anwendung von Methoden zur Identifizierung, Analyse und Bewertung von Risiken.
*   **Maßnahmenplanung und Überprüfung:** Praktische Aspekte der Planung, Umsetzung und Überprüfung von Sicherheitsmaßnahmen.

Dieser Modulblock dient somit der Festigung des Wissens und der Vorbereitung auf die praxisorientierte Anwendung der erlernten Konzepte im Bereich IT-Sicherheit und Risikomanagement.

# Zusammenfassung Block 5: IT-Sicherheits- und Risikomanagement

Dieser Block behandelt die methodische Einführung und den Betrieb eines Information Security Management Systems (ISMS) nach nationalen und internationalen Standards, insbesondere dem BSI IT-Grundschutz, basierend auf dem Dokument `SIRI_LD2023_V1_0_SV1_B5.pdf`.

---

## 1. Kernthemen von 'Block 5'
Der Fokus liegt auf der Professionalisierung der Informationssicherheit in Unternehmen. Die zentralen Themen umfassen:
*   **Grundlagen der Informationssicherheit:** Definition von Schutzzielen und Identifikation von Assets.
*   **ISMS-Einführung:** Strategische Planung und Initialisierung eines Managementsystems für Informationssicherheit.
*   **BSI IT-Grundschutz-Methodik:** Anwendung der Standards der BSI 200-X Reihe.
*   **Risikomanagement:** Identifikation, Analyse und Behandlung von IT-Risiken.
*   **Compliance und Recht:** Berücksichtigung von Gesetzen wie dem Datenschutzgesetz (DSG) und anderen regulatorischen Anforderungen.
*   **Organisation der Sicherheit:** Rollenverteilung (z. B. CISO/ISB) und Verantwortlichkeiten der Geschäftsleitung.

## 2. Schlüsselkonzepte
Das Dokument führt mehrere fundamentale Konzepte ein, die für eine strukturierte Sicherheit essenziell sind:

### BSI-Standards und Schichtenmodell (200-X)
*   **BSI 200-1:** Allgemeine Anforderungen an ein ISMS.
*   **BSI 200-2:** IT-Grundschutz-Methodik (Basis-, Kern- und Standard-Absicherung).
*   **BSI 200-3:** Leitfaden zum Risikomanagement.
*   **Schichtenmodell:** Strukturierung in Prozess-Bausteine (Management), System-Bausteine (IT-Komponenten) und Infrastruktur (Räume, Netze).

### Schutzziele (CIA-Triade)
Die Bewertung von Informationen und Systemen erfolgt anhand der drei primären Schutzziele:
1.  **Vertraulichkeit (Confidentiality):** Schutz vor unbefugter Preisgabe.
2.  **Integrität (Integrity):** Schutz vor unbefugter Änderung oder Manipulation.
3.  **Verfügbarkeit (Availability):** Sicherstellung des Zugriffs bei Bedarf.

### Sicherheitsstufen und Schutzbedarf
Die Einstufung des Schutzbedarfs erfolgt in drei Kategorien:
*   **Normal:** Begrenzter Schaden bei Verletzung der Schutzziele.
*   **Hoch:** Beträchtlicher Schaden (z. B. Verstöße gegen Gesetze, erhebliche finanzielle Einbußen).
*   **Sehr hoch:** Existenzieller Schaden, der die Institution gefährdet oder Leib und Leben bedroht.

### Reifegradmodell des ISMS
Die Qualität des Sicherheitsprozesses wird in Stufen von 0 bis 5 gemessen, wobei Stufe 3 ein voll etabliertes und dokumentiertes System darstellt und Stufe 5 die kontinuierliche Optimierung beschreibt.

## 3. Umsetzungsprozess (Planung, Umsetzung, Prüfung)
Die Umsetzung folgt dem klassischen **PDCA-Zyklus** (Plan-Do-Check-Act):

### Planung (PLAN)
*   **Initiierung:** Die Geschäftsleitung übernimmt die Gesamtverantwortung und stellt Ressourcen bereit.
*   **Strukturanalyse:** Erfassung aller relevanten Geschäftsprozesse, Anwendungen und IT-Systeme.
*   **Schutzbedarfsfeststellung:** Bewertung der Assets nach der CIA-Triade.
*   **Modellierung:** Auswahl passender BSI-Bausteine und Durchführung von Risikoanalysen (insb. bei erhöhtem Schutzbedarf).

### Umsetzung (DO)
*   **Massnahmenplanung:** Festlegung technischer (z. B. Firewall), organisatorischer (z. B. Richtlinien), personeller und infrastruktureller Maßnahmen.
*   **Realisierungsplan:** Festlegung von Prioritäten, Terminen und Verantwortlichkeiten für die Implementierung.

### Prüfung und Verbesserung (CHECK & ACT)
*   **Überprüfung:** Einsatz von Audits, Logfile-Analysen und Tests zur Kontrolle der Wirksamkeit.
*   **Fortentwicklung:** Korrektur von Mängeln und kontinuierliche Anpassung des ISMS an neue Bedrohungslagen.

## 4. Zusammenfassung der wichtigsten Erkenntnisse
*   **Managementaufgabe:** Informationssicherheit ist keine reine IT-Aufgabe, sondern eine strategische Verantwortung der Geschäftsleitung. Ohne ein offizielles Sicherheitsleitbild (Policy) fehlt die notwendige Verbindlichkeit.
*   **Ganzheitlicher Ansatz:** Sicherheit umfasst nicht nur Technik, sondern auch Prozesse, Personal und physische Infrastruktur.
*   **Effizienz durch Standards:** Die Nutzung von BSI-Bausteinen spart Zeit, da auf bewährte Maßnahmenkataloge zurückgegriffen werden kann und aufwendige Risikoanalysen nur für kritische Bereiche ("Kronjuwelen") nötig sind.
*   **Werte-Fokus:** Ein effektives ISMS schützt sowohl materielle Werte (Hardware, Gebäude) als auch immaterielle Werte (Reputation, Know-how, Daten).

---
*Diese Zusammenfassung dient als Leitfaden für die Umsetzung von Sicherheitsstandards in der Praxis.*

# Zusammenfassung Block 6: IT-Sicherheits- und Risikomanagement

## 1. Kerninhalte von Block 6 (Operative Umsetzung & BSI 200-X)
Block 6 widmet sich der praktischen Implementierung von Informationssicherheit durch ein strukturiertes Managementsystem (ISMS). Zentrales Element ist die Anwendung der deutschen BSI-Standards, die als praxiserprobte Methodik für den deutschsprachigen Raum gelten.

*   **BSI-Standard-Absicherung:** Der Fokus liegt auf der **Standard-Absicherung nach BSI 200-2**, welche ein angemessenes Sicherheitsniveau für normale und hohe Schutzbedarfe bietet.
*   **Komponenten des ISMS:** Ein ISMS besteht laut Unterlagen aus Sicherheitsprozessen, Ressourcen (Mitarbeiter/Technik) und Managementprinzipien (Leitlinien).
*   **Informationssicherheit als Prozess:** Es wird betont, dass Sicherheit kein Zustand, sondern ein kontinuierlicher Kreislauf nach dem **PDCA-Modell** (Plan-Do-Check-Act) ist.
*   **Abgrenzung zum Handbuch:** Neben dem BSI-Ansatz wird auf das "Informationssicherheitshandbuch für die Praxis" und das 10-Punkte-Programm von InfoSurance verwiesen, die einen vereinfachten Einstieg ermöglichen.

## 2. Key Points der Gruppenarbeit (Fallstudie SwissMedTech AG)
Die Fallstudie zur **SwissMedTech AG (SMTAG)** diente der Anwendung der Theorie auf ein Cloud-basiertes Dienstleistungsunternehmen.

*   **Szenario:** SMTAG betreibt die medizinische Plattform *MediView* mit 80 Mitarbeitern und nutzt zwei Rechenzentren. Das Ziel ist der Aufbau eines ISMS nach BSI 200-2.
*   **Methodische Schritte in der Gruppe:**
    *   **Business Model Canvas (BMC):** Identifikation kritischer Werte aus Geschäftssicht.
    *   **Schutzbedarfsfeststellung:** Bewertung von Patientendaten und Systemen nach den **CIA-Kriterien** (Vertraulichkeit, Integrität, Verfügbarkeit).
    *   **IS-Organisation:** Aufbau einer Rollenstruktur (z.B. ISB, IT-Sicherheitsbeauftragte).
    *   **Strukturanalyse:** Erstellung eines Netzplans und Inventarisierung von Anwendungen und IT-Systemen.
    *   **Bausteinauswahl:** Zuordnung konkreter Module aus dem IT-Grundschutz-Kompendium (z.B. Cloud-Nutzung, Serverräume, Clients).

## 3. Deep Dive: Risikomanagement (BSI 200-3) und Methodik (BSI 200-2)

### BSI 200-2: IT-Grundschutz-Methodik
Die Methodik bietet einen Fahrplan in 9 Schritten:
1.  **Strukturanalyse:** Erfassung aller relevanten Assets (Prozesse, IT, Räume).
2.  **Schutzbedarfsfeststellung:** Kategorisierung in *normal*, *hoch* oder *sehr hoch*. Wichtig sind hier die **Vererbungsprinzipien**:
    *   **Maximumprinzip:** Ein System übernimmt den höchsten Schutzbedarf der Anwendungen.
    *   **Kumulationseffekt:** Häufung von Anwendungen kann den Bedarf des Systems erhöhen.
    *   **Verteilungseffekt:** Redundanz kann den Schutzbedarf eines Einzelsystems senken.
3.  **Modellierung:** Auswahl der Anforderungen aus den Bausteinen des Kompendiums.
4.  **IT-Grundschutz-Check:** Ein Soll-Ist-Vergleich (Status: ja, nein, teilweise, entbehrlich).
5.  **Realisierungsplan:** Planung der Maßnahmenumsetzung.

### BSI 200-3: Risikoanalyse
Die Risikoanalyse ergänzt den Grundschutz, wenn Standardmaßnahmen nicht ausreichen.
*   **Wann nötig?** Bei hohem Schutzbedarf, fehlenden Bausteinen oder untypischen Einsatzszenarien.
*   **Prozess:** Identifikation von **elementaren Gefährdungen** (47 Typen laut BSI), Bewertung von Eintrittshäufigkeit und Schadensausmaß.
*   **Risikomatrix:** Visualisierung der Risiken zur Entscheidungsfindung.
*   **Risikobehandlung:** Optionen sind Vermeidung, Reduktion (Zusatzmaßnahmen), Transfer (Versicherung) oder Akzeptanz (Managemententscheidung).

## 4. Zusammenfassung der praktischen Umsetzungsschritte
Die Umsetzung folgt einem klaren Pfad von der Strategie zur Kontrolle:

1.  **Vorbereitung:** Management-Commitment einholen, ISB benennen, Leitlinie verabschieden.
2.  **Analysephase:** Geltungsbereich definieren, Strukturanalyse durchführen, Schutzbedarf festlegen.
3.  **Konzeptionsphase:** Bausteine zuordnen, IT-Grundschutz-Check durchführen, Lücken identifizieren.
4.  **Risikophase:** Risikoanalyse für kritische Assets nach BSI 200-3 durchführen.
5.  **Umsetzungsphase:** Maßnahmen konsolidieren, Kosten schätzen, Realisierungsplan abarbeiten.
6.  **Betrieb & Verbesserung:** Überwachung durch Kennzahlen, interne Audits und Reifegradmodelle zur Vorbereitung einer möglichen ISO 27001-Zertifizierung auf Basis von IT-Grundschutz.

---
*Zusammenfassung erstellt auf Basis der Modulunterlagen von Block 6.*

# Zusammenfassung Block 7: IT-Sicherheits- und Risikomanagement

Dieser Block behandelt die strategische und operative Bewältigung von IT-Risiken, die Sicherstellung des Geschäftsbetriebs (Business Continuity) und spezifische Maßnahmenkataloge für Unternehmen, basierend auf den Unterlagen zu Modulblock 7 sowie den Programmen von InfoSurance und SwissBanking.

---

## 1. Kerninhalte von Block 7
Das Hauptziel von Block 7 ist die Beherrschung von Risiken durch einen systematischen Managementprozess (orientiert an ISO 27001/27005).

*   **Risikomanagement-Prozess:**
    *   **Identifikation:** Erkennen von Bedrohungen (z. B. Hackerangriffe, technisches Versagen) und Schwachstellen (z. B. fehlende Firewall).
    *   **Analyse:** Bewertung nach Eintrittswahrscheinlichkeit ($E$) und Auswirkung ($A$). Formel: $E \times A = R$ (Risikowert).
    *   **Bewertung:** Abgleich mit Akzeptanzkriterien. Ist das Restrisiko tragbar?
    *   **Behandlung:** Vier Strategien: *Vermeiden* (Eliminierung), *Vermindern* (Massnahmen), *Übertragen* (Versicherung) oder *Akzeptieren* (Restrisiko).
*   **Business Continuity Management (BCM) & Notfallplanung:**
    *   BCM zielt darauf ab, die Geschäftstätigkeit nach einem Ereignis aufrechtzuerhalten.
    *   **Business Impact Analyse (BIA):** Identifiziert kritische Prozesse und Ressourcen. Sie bestimmt die Prioritäten für den Wiederanlauf und liefert Kenngrößen für die Kosten-Nutzen-Analyse von Sicherheitsmaßnahmen.
    *   Unterscheidung zwischen **Notfallplan** (Wiederbetriebnahme kritischer Systeme / Disaster Recovery) und **Kontinuitätsplan** (Aufrechterhaltung der Geschäftstätigkeit).

## 2. Kernpunkte des InfoSurance 10-Punkte-Programms
Das Programm bietet einen pragmatischen Leitfaden für KMU, unterteilt in Basisschutz, Vertraulichkeit und Verfügbarkeit (insgesamt 20 Punkte).

**Zehn Maßnahmen für den wirkungsvollen Grundschutz:**
1.  **Pflichtenheft für IT-Verantwortliche:** Klare Definition von Aufgaben und Zuständigkeiten.
2.  **Regelmäßige Backups:** Sicherung auf getrennten Medien, inklusive regelmäßiger Rückspieltests.
3.  **Aktueller Virenschutz:** Installation und tägliche Aktualisierung auf allen Systemen.
4.  **Firewall:** Schutz des Internetzugangs und Absicherung von WLAN-Verbindungen.
5.  **Software-Updates (Patch-Management):** Zeitnahe Installation von Sicherheitsupdates.
6.  **Starke Passwörter:** Mindestens 8 Zeichen, Mix aus Groß-/Kleinschreibung, Zahlen und Sonderzeichen.
7.  **Schutz mobiler Geräte:** Verschlüsselung und PIN-Schutz für Notebooks und Smartphones.
8.  **IT-Benutzerrichtlinien:** Schriftliche Regeln für die erlaubte Nutzung von Internet und E-Mail.
9.  **Infrastrukturschutz:** Physische Sicherung von Serverräumen (Zutrittskontrolle, Brandschutz).
10. **Ordnung bei Dokumenten:** Sicherer Verschluss vertraulicher Unterlagen und saubere Entsorgung.

**Zusatzpunkte für Vertraulichkeit & Verfügbarkeit:**
*   Verschlüsselung sensibler Daten und Datenträger.
*   Sensibilisierung der Mitarbeitenden (Awareness).
*   Einsatz von unterbrechungsfreier Stromversorgung (USV).
*   Redundante Auslegung kritischer Komponenten (z. B. Server-Spiegelung).

## 3. Praktische Ratschläge aus der 'Checkliste Notfall'
Die Checkliste (Empfehlungen der SwissBanking) fokussiert sich auf die operative Krisenbewältigung und Wiederherstellungsstrategien.

*   **Wiederherstellungsziele definieren:**
    *   **RTO (Recovery Time Objective):** Wie lange darf ein Systemausfall maximal dauern?
    *   **RPO (Recovery Point Objective):** Wie viel Datenverlust ist akzeptabel (Zeitspanne seit dem letzten Backup)?
*   **Ressourcenplanung:** Identifikation kritischer Abhängigkeiten in den Bereichen Personal (Schlüsselpersonen), Gebäude, IT/Daten und externe Zulieferer.
*   **Krisenmanagement-Organisation:**
    *   Vorbereitung von Kommunikationsplänen (intern/extern).
    *   Einrichtung von Alarmierungswegen, die auch bei IT-Ausfall funktionieren.
*   **Testen und Üben:** Notfallpläne sind wertlos, wenn sie nicht regelmäßig auf ihre Wirksamkeit geprüft und durch Übungen (Simulationsläufe) verifiziert werden.

## 4. Rollen und Verantwortlichkeiten in Krisensituationen
Eine klare Zuweisung von Verantwortlichkeiten ist essenziell für ein funktionierendes Sicherheitsmanagement.

*   **Verwaltungsrat / Geschäftsleitung:** Trägt die Gesamtverantwortung. Sie muss die Strategie genehmigen, Ressourcen (Budget) bereitstellen und die Akzeptanz von Restrisiken absegnen.
*   **Risk Owner:** Verantwortlich für die Überwachung und Bewirtschaftung spezifischer, ihm zugewiesener Risiken.
*   **Krisenstab:** Ein im Notfall einberufenes Team zur Koordination der Bewältigung. Ziel ist die Schadensminimierung und die Wiederaufnahme des Normalbetriebs.
*   **IT-Verantwortliche:** Setzen technische Maßnahmen um, verantworten das Backup-Wesen und führen die Disaster-Recovery-Pläne aus.
*   **Mitarbeitende:** Sind der zentrale Erfolgsfaktor. Sie sind verantwortlich für die Einhaltung der Richtlinien, die Meldung von Vorfällen und die Wahrnehmung der Sicherheits-Awareness (z. B. Erkennen von Phishing).

---
*Diese Zusammenfassung basiert auf den Unterlagen zu Modulblock 7 sowie den spezifischen Programmen von InfoSurance und SwissBanking.*


# Zusammenfassung Block 8: IT-Sicherheits- und Risikomanagement

Dieser abschließende Modulblock konzentriert sich auf die praktische Umsetzung von Sicherheitsmaßnahmen, die Überprüfung der Effektivität (Auditing) sowie spezifische technische und organisatorische Konzepte zur Absicherung eines Unternehmens, basierend auf den Unterlagen zu Block 8 und der zugehörigen Fallstudie.

---

## 1. Kernthemen von Block 8
Der Block deckt ein breites Spektrum an Sicherheitsdisziplinen ab, die für den Abschluss des Moduls entscheidend sind:

*   **Identity & Access Management (IAM):** Fokus auf den Schutz von Identitäten durch Mehrfaktor-Authentifizierung (MFA), Single-Sign-On (SSO) und die Erstellung von Zugriffskontrollmatrizen (ACLs).
*   **Organisatorische Richtlinien:**
    *   **Clear Desk Policy:** Regeln zur Sauberkeit am Arbeitsplatz (Bildschirm sperren, Dokumente wegschließen).
    *   **Passwort-Richtlinien:** Mindestanforderungen (12+ Zeichen, Komplexität) und Einsatz von Passwort-Managern (z.B. KeePass, Proton Pass).
    *   **Nutzungsreglemente:** Rechtliche Grundlagen des Arbeitgebers zur Überwachung von Internet und E-Mail am Arbeitsplatz (unter Berücksichtigung des schweizerischen Obligationenrechts).
*   **Technische Schutzmaßnahmen:**
    *   **Sicherheitsgateways (Firewalls):** Einsatz von UTM-Lösungen (Unified Threat Management) und Zonenkonzepten (DMZ).
    *   **Netzwerksicherheit:** Absicherung von WLAN (WPA2/3, Deaktivierung von WPS) und Bluetooth.
    *   **Sicherer Remotezugriff:** VPN-Technologien (IPSec, SSL-VPN) für Standortverbindungen und Fernzugriff.
*   **System- und Datensicherheit:**
    *   **Härtung (Hardening):** Deaktivierung nicht benötigter Schnittstellen und Dienste.
    *   **Datensicherung:** Strategien (Full, Inkrementell, Differenziell) und das Generationenprinzip (Grossvater-Vater-Sohn).
    *   **Verfügbarkeitsmanagement:** Konzepte wie RAID-Systeme, Clustering und Loadbalancing zur Vermeidung von Ausfällen.
*   **Kontrolle und Revision:**
    *   **IS-Revision (Auditing):** Systematische Prüfung der Sicherheitsorganisation nach BSI-Standards.
    *   **IT-Forensik:** Grundlagen zur Aufklärung von Vorfällen unter Berücksichtigung des schweizerischen Strafrechts (z.B. Art. 143bis StGB - Unbefugtes Eindringen in ein Datenverarbeitungssystem).

## 2. Kernpunkte der 'Aufgabe' (Fallstudie SimpleTech AG)
Die praktische Übung beschreibt die Ausgangslage der **SimpleTech AG**, eines Produktionsbetriebs mit 50 Mitarbeitenden, und fordert eine Risikoanalyse:

*   **Szenario:**
    *   Zentraler Server steuert die gesamte Produktion (Stillstand bei Ausfall).
    *   Mangelhafte Infrastruktur: USV reicht nur für 5 Minuten, kein IT-Notfallplan vorhanden.
    *   Historie: Ein Ransomware-Vorfall vor sechs Monaten führte zu zwei Tagen Produktionsstopp.
    *   Organisatorische Mängel: Passwort-Sharing (IT-Leiter kennt alle Passwörter), unregelmäßige Schulungen, "On-the-job" Einarbeitung neuer Mitarbeiter ohne formale Prozesse.
*   **Aufgabenstellung:**
    1.  Nennung von zwei **technischen Risiken** inklusive einer **quantitativen Risikoanalyse** (finanzieller Impact).
    2.  Nennung von zwei **organisatorischen Risiken** inklusive einer **qualitativen Risikoanalyse**.
    3.  Erarbeitung jeweils einer geeigneten **Maßnahme zur Verbesserung** für jedes identifizierte Risiko.

## 3. Praktische Checklisten und Zusammenfassungen
Ein Highlight von Block 8 ist die finale Checkliste der wichtigsten Maßnahmen:

### "Meine Massnahmen Top 10 + 2"
1.  **Revisionssaugliche Datensicherung:** Erfüllung der Archivierungspflichten.
2.  **Nutzungs- & Überwachungsreglement:** Erstellung klarer Richtlinien.
3.  **Mitarbeiterschulung:** Sensibilisierung für Informationssicherheit.
4.  **Keine Admin-Rechte:** Arbeiten am PC mit eingeschränkten Rechten.
5.  **Passwort-Sicherheit:** Verwendung komplexer Passwörter (min. 12 Zeichen).
6.  **Update-Management:** Zeitnahe Aktualisierung von Software und Hardware.
7.  **Endpoint Protection:** Umfassende Virenschutzlösungen.
8.  **UTM-Firewall:** Professionell eingerichtete Netzwerksicherheit.
9.  **Physischer Schutz:** Sicherung der Computeranlagen vor Ort.
10. **Verschlüsselung:** Schutz vertraulicher Daten auf mobilen Geräten.
11. **App-Allowlisting:** Explizite Freigabe von Anwendungen (z.B. AppLocker).
12. **Exploit-Schutz:** Einsatz erweiterter Sicherheitsfunktionen (z.B. Windows Exploit-Schutz).

### Physische Sicherheit (Ergänzungen)
*   **Zutrittsschutz:** Zonenplanung (Öffentlich -> Intern -> Sicherheitszone).
*   **Brandschutz:** Installation von Rauchmeldern und Feuerlöschern.
*   **Wasserschutz:** Keine Wasserleitungen über Serverräumen.

## 4. Abschließende Erkenntnisse für den gesamten Kurs
Das Dokument schließt mit einer zentralen Botschaft ab, die den Erfolg aller Sicherheitsbemühungen zusammenfasst:

> *"Alle Bemühungen zur regelmässigen und sauberen Datensicherung nützen wenig, wenn die Mitarbeitenden die Daten auf lokale nicht gesicherte Medien speichern. Erstellen Sie daher Weisungen und schulen Sie die Mitarbeitenden!"*

**Zentrales Fazit:** Technik allein reicht nicht aus. Informationssicherheit ist ein Zusammenspiel aus **Technik, Organisation und Mensch**. Nur durch kontinuierliche Schulung, klare Richtlinien und regelmäßige Überprüfung (Revision) kann ein angemessenes Schutzniveau langfristig gehalten werden.


