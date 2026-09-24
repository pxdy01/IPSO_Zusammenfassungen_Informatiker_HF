# PRÜFUNGSSPICKER: BACKUP & RESTORE

## KAPITEL 1: RISIKOMANAGEMENT & RISIKOANALYSE

### 1.1 Grundlagen & Schutzziele (CIA-Triade)
* **Confidentiality (Vertraulichkeit):** Schutz vor unbefugter Offenlegung. Massnahmen: Verschlüsselung (AES-256), Zugriffssteuerung (RBAC, Need-to-Know).
* **Integrity (Integrität):** Schutz vor unbefugter oder unbeabsichtigter Veränderung/Löschung. Massnahmen: Hash-Prüfsummen, Digitales Signieren, Write-Once-Read-Many (WORM).
* **Availability (Verfügbarkeit):** Gewährleistung des rechtzeitigen Zugriffs auf Daten und Systeme. Massnahmen: Redundanz, RAID, Backup & Restore, Disaster Recovery.

### 1.2 Das Risikoanalyse-Modell nach Polat
Eine Risikoanalyse dient als Filter- und Steuerungsinstrument zwischen technischer Notwendigkeit und finanzieller Machbarkeit:
1. **Asset-Inventarisierung:** Erfassung aller Datenlandschaften (strukturierte Datenbanken, unstrukturierte Fileserver/E-Mails).
2. **Bedrohungsmodellierung:** Identifikation möglicher Gefahrenquellen (Ransomware, Hardwareausfall, Brand, menschlicher Fehler).
3. **Risikobewertung:** Mathematische Formel:
   $$\text{Risikowert } (R) = \text{Eintrittswahrscheinlichkeit } (E) \times \text{Schadensausmass } (S)$$

### 1.3 Die 5×5-Risikomatrix & Klassifizierung

| Stufe | Eintrittswahrscheinlichkeit ($E$) | Schadensausmass ($S$) |
| :---: | :--- | :--- |
| **1** | **Sehr unwahrscheinlich** (Selten als 1x in 10 Jahren) | **Geringfügig** (Vernachlässigbarer finanzieller/operativer Schaden) |
| **2** | **Unwahrscheinlich** (1x in 3 bis 10 Jahren) | **Moderat** (Spürbarer Schaden, durch Tagesgeschäft kompensierbar) |
| **3** | **Möglich** (1x in 1 bis 3 Jahren) | **Erheblich** (Signifikanter finanzieller Schaden, Erlösausfall) |
| **4** | **Wahrscheinlich** (Mehrmals pro Geschäftsjahr) | **Kritisch** (Schwerer operativer Stillstand, Reputationsverlust) |
| **5** | **Sehr wahrscheinlich** (Kontinuierlich / Monatlich) | **Existenzbedrohend** (Insolvenzrisiko, massiver rechtlicher Verstoß) |

#### Risikoklassifizierung (Ampelsystem):
* **Grün (Niedrig: 1–4):** Akzeptables Risiko. Massnahme: Überwachung (Monitoring).
* **Gelb (Mittel: 5–9):** Aufmerksamkeit erforderlich. Massnahme: Einplanung im ordentlichen IT-Budget.
* **Orange (Hoch: 10–15):** Erhöhtes Risiko. Massnahme: Erarbeitung von Schutzmassnahmen innerhalb von 3–6 Monaten.
* **Rot (Kritisch: 16–25):** Inakzeptables Risiko. Massnahme: Sofortige Intervention / Stop-Go-Entscheid der Geschäftsleitung.

### 1.4 Die 4 Strategien der Risikosteuerung
1. **Risikovermeidung (Avoidance):** Verzicht auf risikobehaftete Prozesse/Technologien (z. B. Abschalten veralteter Server).
2. **Risikominderung (Mitigation):** Technische/organisatorische Reduktion von $E$ oder $S$ (z. B. Backup, Verschlüsselung, MFA).
3. **Risikotransfer (Transfer):** Übertragung des finanziellen Restrisikos auf Dritte (z. B. Cyberversicherung, SLA mit Cloud-Provider).
4. **Risikoakzeptanz (Acceptance):** Bewusste Übernahme von Kleinst-Risiken ("Parkschäden"), wenn Schutzkosten den Schaden übersteigen.

---

## KAPITEL 2: DATENKLASSIFIZIERUNG, SCHUTZBEDARF & GOVERNANCE

### 2.1 Das 5-Stufen-Klassifizierungsmodell

| Klasse | Bezeichnung | Schutzbedarf | Beispiel-Daten | Massnahmen & Vorgaben |
| :---: | :--- | :--- | :--- | :--- |
| **K1** | **Öffentlich** | Kein Schutzbedarf | Marketingmaterial, Stelleninserate | Freie Zugänglichkeit |
| **K2** | **Intern** | Normal | Organigramme, interne Richtlinien | Zugriff für alle Mitarbeitenden |
| **K3** | **Vertraulich** | Hoch | Projektpläne, Bilanzen, Verträge | Need-to-Know, RBAC, Transportverschlüsselung (TLS) |
| **K4** | **Streng vertraulich** | Sehr hoch | Geschäftsgeheimnisse, Patente, M&A | Strikte Freigabe durch Data Owner, AES-256 (At-Rest & In-Transit) |
| **K5** | **Personendaten** | Gesetzlich geregelt | Patientendaten, Lohnabrechnungen | nDSG-Konformität, MFA, lückenloses Audit-Trail, Anonymisierung |

### 2.2 Klassifizierungskriterien für Applikationen & Daten
* **Datenvolumen:** Auswirkung auf Backup-Dauer, Bandbreite und Speicherkapazität.
* **Periodizität:** Änderungsrate (Change Rate) der Daten pro Zeiteinheit (steuert Sicherungsfrequenz).
* **Zugriffssicherheit:** Anforderungen an Vertraulichkeit, Integrität und Verfügbarkeit.

### 2.3 Rollen & Verantwortlichkeiten (Governance)
* **Data Owner (Dateneigentümer / Fachverantwortlicher):** 
  * Fachliche Verantwortung für Daten.
  * Legt Klassifizierungsstufe fest und erteilt Zugriffsberechtigungen.
  * *Haftung:* Haftet für die fachliche und rechtliche Rechtmässigkeit der Datenerfassung.
* **Data Custodian (Datenverwalter / IT-Infrastruktur-Leiter):**
  * Technische Umsetzung der Schutzvorgaben des Data Owners.
  * *Haftung:* Haftet für technische Sicherheitsmängel (z. B. fehlendes Patch-Management, unzureichende Verschlüsselung trotz Vorgabe).
* **Management / Geschäftsleitung:** Genehmigung der Sicherheitsrichtlinien, Budgetbereitstellung, Stop-Go-Entscheidungen.
* **Mitarbeitende:** Pflicht zur Einhaltung der Klassifizierungsvorgaben im Arbeitsalltag.
* **Revision / DPO:** Unabhängige Auditierung der Prozesse und Einhaltung von nDSG/Compliance.

### 2.4 Schweizer Legal & Compliance Rahmenbedingungen
* **revidiertes Datenschutzgesetz (nDSG):** Verlangt risikobasierte Technische und Organisatorische Massnahmen (TOM).
  * *Meldepflicht:* Pflicht zur unverzüglichen Meldung von Datenschutzverletzungen mit hohem Risiko an den EDÖB.
  * *Strafbestimmungen:* Bussen bis zu CHF 250'000.- direkt gegen die verantwortliche natürliche Person bei vorsätzlicher Pflichtverletzung.
* **Obligationenrecht (OR Art. 958f):** Gesetzliche Aufbewahrungspflicht von 10 Jahren für Geschäftsbücher, Buchungsbelege und Korrespondenz.
* **FINMA-Rundschreiben:** Strenge Vorgaben für Finanzinstitute bzgl. Operational Resilience, BCM und Cloud-Outsourcing.

---

## KAPITEL 3: DIE 3-2-1-1-0 BACKUP-STRATEGIE & RAID-VERGLEICH

### 3.1 Das Mantra: "Ein RAID ist kein Backup!"
Ein RAID (Redundant Array of Independent Disks) bietet ausschliesslich **Hardware-Hochverfügbarkeit** (Schutz vor Diskausfällen). 
* **Was RAID KANN:** Das System läuft weiter, wenn 1 oder 2 Festplatten physisch ausfallen.
* **Was RAID NICHT KANN:** Schutz vor versehentlichem Löschen, Softwarefehlern, Ransomware-Verschlüsselung, Brand oder Überschwemmung (Löschbefehle werden sofort auf alle Platten gespiegelt!).

### 3.2 RAID-Level Übersicht & Vergleich

| RAID-Level | Funktionsweise | Min. Disks | Kapazitätsausnutzung | Lese-Perf. | Schreib-Perf. | Ausfallsicherheit | Rebuild-Risiko |
| :--- | :--- | :---: | :---: | :---: | :---: | :--- | :--- |
| **RAID 0** | Striping (ohne Parität) | 2 | 100% | Sehr hoch | Sehr hoch | **Keine** (1 Disk Defekt = Totalschaden) | N/A |
| **RAID 1** | Mirroring (Spiegelung) | 2 | 50% | Hoch | Normal | Ausfall von 1 Disk pro Paar | Niedrig |
| **RAID 5** | Striping mit verteilter Parität | 3 | $(n-1)/n$ | Hoch | Langsamer (Parity-Penalty) | Ausfall von max. 1 Disk | **Hoch** (URE-Fehler beim Rebuild) |
| **RAID 6** | Striping mit doppelter Parität | 4 | $(n-2)/n$ | Hoch | Langsam | Ausfall von max. 2 Disks | Moderat |
| **RAID 10** | Combination (RAID 1 + RAID 0) | 4 | 50% | Sehr hoch | Hoch | Ausfall von 1 Disk pro Spiegelsatz | Sehr schnell & sicher |

### 3.3 Die erweiterte 3-2-1-1-0 Backup-Regel

$$\text{3-2-1-1-0 Strategie} = \text{Redundanz (3)} + \text{Medienvielfalt (2)} + \text{Offsite (1)} + \text{Air-Gap/Immutable (1)} + \text{Zero Errors (0)}$$

1. **3 Kopien der Daten:** 1x Produktionsdaten + 2x Backup-Kopien.
2. **2 unterschiedliche Medien:** Speicherung auf verschiedenen Speichertypen (z. B. Disk + Tape oder Disk + Cloud Storage).
3. **1 Offsite-Kopie:** Mindestens ein Backup lagert an einem physisch getrennten Standort (Schutz vor Elementarschäden).
4. **1 Offline / Air-Gapped / Immutable Kopie:** 
   * *Physisches Air-Gap:* LTO-Tape im Tresor (keine Netzwerkanbindung).
   * *Logisches Air-Gap / Immutability:* S3 Object Lock (WORM-Prinzip auf Cloud-/Object-Storage).
5. **0 Fehler (Zero Errors):** Automatische, regelmässige Prüfungen (Verifikation) und automatisierte Restore-Tests.

### 3.4 Air-Gap vs. Immutable Storage (WORM)
* **Physischer Air-Gap (Tape):** Physisch getrennter Datenträger. Schutzfaktor: 100% immun gegen Cyberangriffe über Netzwerke. Stromverbrauch bei Lagerung: **0 Watt**.
* **Immutable Storage (S3 Object Lock):** Daten werden auf API-Ebene für einen definierten Zeitraum (Retention Time) gegen Löschen/Überschreiben gesperrt.
  * **Governance Mode:** Administrative Benutzer mit Sonderrechten können die Sperre aufheben.
  * **Compliance Mode:** Selbst der Root-Administrator oder Cloud-Provider kann die Sperre VOR Ablauf der Frist nicht aufheben!

---

## KAPITEL 4: BACKUP VS. DISASTER RECOVERY (DR)

### 4.1 Abgrenzung: Backup vs. Disaster Recovery

| Kriterium | Backup (Datensicherung) | Disaster Recovery (DR / Notfallwiederherstellung) |
| :--- | :--- | :--- |
| **Fokus** | Schutz von Datenbeständen & historische Integrität | Wiederherstellung der operativen Betriebsfähigkeit der IT |
| **Ziel** | Wiederherstellung einzelner Dateien, Tabellen oder VMs | Bereitstellung kompletter Rechenzentrumsinfrastrukturen |
| **Auslöser** | Versehentliches Löschen, Dateikorruption, Audit-Anfragen | Katastrophen, Ausfall von RZ/Standorten, Ransomware-Totalschaden |
| **Metrik** | RPO (Recovery Point Objective) | RTO (Recovery Time Objective) |
| **Technik** | Snapshots, Inkremente, Tapes, S3 Repositories | Replikation, Failover-Cluster, Standby-Rechenzentren |

### 4.2 Die Schlüsselmetriken: RPO und RTO

$$\text{RPO } (\text{Recovery Point Objective}) = \text{Maximal tolerierbarer Datenverlust in der Zeit (letzter Sicherungspunkt)}$$
$$\text{RTO } (\text{Recovery Time Objective}) = \text{Maximal tolerierbare Ausfallzeit bis zur Betriebsbereitschaft}$$

```
[Letztes Backup] <----- RPO -----> [SYSTEMAUSFALL] <----- RTO -----> [System wieder online]
                          (Datenverlust)                     (Ausfallzeit)
```

### 4.3 System-Verfügbarkeitsklassen

| Klasse | Kritikalität | RTO-Vorgabe | RPO-Vorgabe | Technische Lösung |
| :---: | :--- | :---: | :---: | :--- |
| **Klasse 1** | **Sehr hoch (Platin)** | $< 1 \text{ Stunde}$ | Near Zero / CDP | Hot-Standby, synchrone Replikation, Active-Active Cluster |
| **Klasse 2** | **Wichtig (Gold)** | wenige Stunden | $\le 1 \text{ Stunde}$ | Warm-Standby, asynchrone Replikation, Instant Recovery |
| **Klasse 3** | **Moderat (Silber)** | $\le 24 \text{ Stunden}$ | $\le 24 \text{ Stunden}$ | Cold-Standby, tägliches Backup (Disk-to-Disk) |
| **Klasse 4** | **Gering (Bronze)** | mehrere Tage | 1 Woche | Wöchentliches Backup (Tape/Cloud Archive) |

### 4.4 DR-Standby-Modelle im Vergleich
* **Cold Standby:** Bereitstellung von Räumlichkeiten/Strom. Hardware muss im Krisenfall erst bestellt und konfiguriert werden. RTO: Tage bis Wochen. Kriterien: Geringste Kosten.
* **Warm Standby:** Ersatz-Hardware steht am DR-Standort bereit. Daten werden asynchron repliziert. RTO: Einige Stunden. Kriterien: Ausgewogenes Kosten/Nutzen-Verhältnis.
* **Hot Standby:** Vollkommen redundante Infrastruktur am Zweitstandort. Synchrone Spiegelung der Daten. Automatisches Failover. RTO: Sekunden bis Minuten. Kriterien: Sehr hohe Kosten.

---

## KAPITEL 5: SPEICHERARCHITEKTUREN & MEDIENEVALUIERUNG

### 5.1 Storage Tiering (Mehrstufige Speicherarchitektur)
* **Tier 0 (Ultra Performance / Hot Data):** NVMe-SSDs / All-Flash. Für aktive Datenbanken und primäre Instant-Recovery-Ziele.
* **Tier 1 (Capacity / Warm Data):** SAS/SATA HDDs. Für Backup-Repositories der letzten 7–30 Tage.
* **Tier 2 (Archive / Cold Data):** LTO-Tape / Cloud Object Storage (Cold/Glacier). Für Langzeitarchivierung (10+ Jahre).

### 5.2 Anbindungstypen im Vergleich: DAS vs. SAN vs. NAS vs. Object

| Speichertyp | Zugriffsart | Protokolle | Typischer Einsatzbereich | Vor- & Nachteile |
| :--- | :--- | :--- | :--- | :--- |
| **DAS** (Direct Attached) | Blockbasiert | PCIe, SAS, SATA | Lokaler Server-Speicher, kleine Backup-Target-Disks | **+** Höchste Perf., tiefste Latenz<br>**-** Keine Skalierbarkeit, Single Point of Failure |
| **SAN** (Storage Area Net) | Blockbasiert | Fibre Channel, iSCSI | High-Performance Datenbanken, Hypervisor-Cluster | **+** Maximale Perf., Hochverfügbarkeit<br>**-** Hohe Kosten, komplexe FC-Infrastruktur |
| **NAS** (Network Attached) | Dateibasiert | SMB / CIFS, NFS | File-Sharing, allgemeines Backup-Ziel | **+** Einfache Integration, kosteneffizient<br>**-** Netzlatenz, Overhead bei Mio. Kleindateien |
| **Object Storage** | Objektbasiert | REST-API (HTTP/S3) | Cloud-Backup, Archiving, Immutability | **+** Unbegrenzte Skalierbarkeit, WORM-Support<br>**-** Höhere Latenz bei wahlfreiem Zugriff |

### 5.3 Magnetband-Technologie (LTO-Tape)
* **Status:** Absolut hochrelevant als ultimativer Ransomware-Schutz und für TCO-optimierte Langzeitarchivierung.
* **Kapazität (LTO-9):** 18 TB unkomprimiert / bis zu 45 TB komprimiert pro Kassette.
* **Lebensdauer:** Über **30 Jahre** bei korrekter Lagerung.
* **Stromverbrauch:** **0 Watt** bei passiver Lagerung im Tresor (Green IT).
* **LTFS (Linear Tape File System):** Bänder lassen sich wie ein gewöhnlicher USB-Stick im Dateimanager ansprechen.

---

## KAPITEL 6: DATENSICHERUNGSTECHNOLOGIEN & -VERFAHREN

### 6.1 Die drei klassischen Sicherungsarten

```
Vollbackup (Sonntag):          [================ 100% ================]
Inkrementell (Montag):        [Δ Mo] (Nur Änderungen seit So)
Inkrementell (Dienstag):      [Δ Di] (Nur Änderungen seit Mo)
Differentiell (Dienstag):     [Δ Mo + Δ Di] (Alle Änderungen seit So)
```

| Verfahren | Gesicherte Daten | Speicherbedarf | Backup-Geschwindigkeit | Restore-Komplexität |
| :--- | :--- | :---: | :---: | :--- |
| **Vollbackup (Full)** | Alle Daten des Systems | **Sehr hoch** | Langsam | **Sehr einfach** (Nur 1 Stand nötig) |
| **Inkrementell** | Änderungen seit der *letzten* Sicherung (egal ob Full/Inkrementell) | **Minimale** | Sehr schnell | **Komplex** (Full + ALLE Inkremente nacheinander) |
| **Differentiell** | Änderungen seit dem *letzten Vollbackup* | Wächst täglich an | Moderat | **Einfach** (Full + letztes Differentielles Backup) |
| **Synthetisches Vollbackup** | Software baut aus Full + Inkrementen ein neues Vollbackup | Gering (auf Target) | Extrem schnell | **Einfach** (Wird als echtes Full bereitgestellt) |

### 6.2 Generationenprinzip (Großvater-Vater-Sohn / GVS)
* **Sohn (Tages-Backup):** Inkrementell / Differentiell, Aufbewahrung: 6–7 Tage.
* **Vater (Wochen-Backup):** Vollbackup am Wochenende, Aufbewahrung: 4 Wochen.
* **Großvater (Monats-Backup):** Vollbackup Ende Monat, Aufbewahrung: 12 Monate oder Jahre (Retention Policy).

### 6.3 Agenten-basierte vs. Agentless Sicherung

#### 1. Agenten-basierte Sicherung
* **Funktionsweise:** Eine Software (Agent) wird direkt im Gast-Betriebssystem installiert.
* **Vorteile:** Transaktionskonsistente Sicherung komplexer Applikationen (MS SQL, Oracle, Exchange via VSS), granulare Wiederherstellung einzelner Objekte (E-Mail, Tabelle), Quell-Deduplizierung.
* **Nachteile:** Hoher Wartungsaufwand (Patching der Agenten auf hunderten Systemen), Ressource-Overhead im Host.

#### 2. Agentless Sicherung (Hypervisor-API)
* **Funktionsweise:** Sicherung erfolgt direkt über die API des Hypervisors (VMware VADP / Hyper-V RCT) auf Image-Ebene.
* **Vorteile:** Keine Softwareinstallation in der VM erforderlich, zentrale Steuerung, volle VM-Sicherung inklusive Konfiguration.
* **Technologien:**
  * **CBT (Changed Block Tracking) / RCT:** Der Hypervisor führt Buch darüber, welche Blöcke sich geändert haben. Es werden nur die geänderten Blöcke übertragen.
  * **Instant Recovery:** Die gesicherte VM wird direkt aus dem Backup-Storage heraus gestartet (RTO $< 5$ Minuten).

---

## KAPITEL 7: EFFIZIENZ, DATENREDUKTION & KAPAZITÄTSPLANUNG

### 7.1 Daten-Deduplizierung
Deduplizierung eliminiert redundante Datenblöcke. Anstelle mehrfacher Speicherung wird ein eindeutiger **Hash-Wert** (digitaler Fingerabdruck, z. B. SHA-256) berechnet. Existiert der Hash in der zentralen Index-Datenbank bereits, wird nur ein winziger **Pointer (Zeiger)** gespeichert.

### 7.2 Verfahrensvergleiche der Deduplizierung

| Kriterium | Inline-Deduplizierung | Post-Process-Deduplizierung |
| :--- | :--- | :--- |
| **Ablauf** | Verarbeitungsprüfung im RAM *vor* dem Schreiben auf Disk | Schreiben unkomprimiert auf Landing Zone, Deduplizierung über Nacht |
| **Speicherbedarf** | **Sehr gering** (Keine Landing Zone nötig) | **Hoch** (Benötigt temporäre Speicherkapazität) |
| **CPU-Belastung** | Hoch während des Backup-Fensters | Hoch während der Nachtstunden |

| Kriterium | Source-Deduplizierung | Target-Deduplizierung |
| :--- | :--- | :--- |
| **Ort** | Auf dem Quellserver (Backup-Client / Agent) | Auf der zentralen Backup-Appliance |
| **Netzwerk-Entlastung**| **Extrem hoch** (Nur neue Blöcke reisen übers Netz) | Keine (Alle Daten reisen unkomprimiert übers Netz) |
| **Quellserver-Load** | Höhere CPU-Last auf dem Quellsystem | Keine CPU-Belastung der Quellsysteme |

### 7.3 Rehydrierung
* **Definition:** Das Wiederzusammensetzen deduplizierter Blöcke und Zeiger zu einer vollständigen, lesbaren Datei während des Restores.
* **RTO-Warnung:** Rehydrierung erfordert massive CPU-Leistung und I/O-Zugriffe. Bei großflächigen Restores kann die Rehydrierungszeit die RTO drastisch verlängern!

### 7.4 Formeln & Kapazitätsberechnung

#### 1. Kombinierter Reduktionsfaktor ($RF$):
$$RF = \text{Deduplizierungsrate} \times \text{Komprimierungsrate}$$
*Beispiel:* Deduplizierung 3:1, Komprimierung 1,5:1 $\implies RF = 3 \times 1,5 = 4,5:1$.

#### 2. Berechnung des Gesamtrohbedarfs ($V_{\text{roh}}$):
$$V_{\text{roh}} = (V_{\text{full}} \times N_{\text{full}}) + (V_{\text{primär}} \times C_{\text{daily}} \times N_{\text{inkrement}})$$
* $V_{\text{full}}$: Volumengrösse Vollbackup
* $N_{\text{full}}$: Anzahl vorzuhaltender Vollbackups
* $C_{\text{daily}}$: Tägliche Änderungsrate (Change Rate in %)
* $N_{\text{inkrement}}$: Anzahl Inkremente

#### 3. Effektiver physischer Speicherbedarf ($V_{\text{effektiv}}$):
$$V_{\text{effektiv}} = \left( \frac{V_{\text{roh}}}{RF} \right) \times P_{\text{puffer}}$$
* $P_{\text{puffer}}$: Sicherheitspuffer (Branchenstandard = $1,25$, entspricht 25% Puffer).

#### Musterberechnung (Prüfungsbeispiel):
* Primärdaten: **10 TB**, Change Rate: **5% (0.5 TB/Tag)**.
* Strategie: **4 Wochen Retention**, 1x Vollbackup/Woche (4x), 6x Inkremente/Woche (24x).
* Effizienz: Deduplizierung 3:1, Kompression 1.5:1 ($RF = 4,5$). Puffer: **25% (1.25)**.
1. Vollbackups: $10 \text{ TB} \times 4 = 40 \text{ TB}$.
2. Inkremente: $0,5 \text{ TB} \times 24 = 12 \text{ TB}$.
3. Gesamtrohbedarf: $40 + 12 = 52 \text{ TB}$.
4. Nach Effizienzfaktoren: $52 \text{ TB} / 4,5 = 11,55 \text{ TB}$.
5. Mit Puffer ($1,25$): $11,55 \text{ TB} \times 1,25 = \mathbf{14,44 \text{ TB}}$ effektiv zu beschaffender Speicher!

---

## KAPITEL 8: RANSOMWARE-RESILIENZ, COMPLIANCE & SCHWEIZER PRAXISFÄLLE

### 8.1 Anatomie von Ransomware-Angriffen auf Backups
Moderne Ransomware (Double Extortion) geht gezielt in Phasen vor:
1. **Initial Access & Reconnaissance:** Einbruch ins Netz, Ausspionieren der Admin-Zugangsdaten.
2. **Backup-Destruktion:** Gezieltes Löschen der VSS-Schattenkopien (`vssadmin delete shadows /all /quiet`), Löschen von Backup-Repositories und Aufheben von Retention Policies.
3. **Exfiltration & Verschlüsselung:** Diebstahl sensibler Daten (Erpressung mit Veröffentlichung) + Verschlüsselung der Produktivdaten.

### 8.2 Schutzarchitekturen & Cyber-Resilienz
* **Zero Trust & Network Microsegmentation:** Das Backup-System liegt in einer isolierten Sicherheitszone (DMZ), getrennt von der regulären Domain.
* **MFA (Multi-Faktor-Authentifizierung):** Pflicht für alle Zugriffe auf Backup-Konsolen.
* **Hardened Repository:** Ein gehärtetes Linux-Server-Repository ohne SSH-Zugang, auf dem der Backup-Dienst als Nicht-Root läuft.

### 8.3 Zusammenfassung aller Schweizer Praxisfälle (ABRL)

#### 1. SwissData AG (Musterfall 1)
* *Problem:* Unregelmässige Backup-Fehler seit 6 Monaten, wechselnde Symptome (Timeouts, Speichermangel).
* *Ursache:* Mangelndes Monitoring, fehlendes zentrales Alerting, unzureichende Kapazitätsplanung.
* *Lösung:* Einführung von automatischem Log-Monitoring, täglicher Alert-Auswertung und systematischem Change-Rate-Tracking.

#### 2. AlpinTech GmbH (Musterfall 2)
* *Problem:* Unklare Risikostruktur bei der Datensicherung eines Industrieunternehmens.
* *Lösung:* Erstellung einer 5×5-Risikomatrix. Priorisierung von 2 roten Risiken (Ransomware & unvollständige Backups) durch Zuweisung von RTO/RPO-Klassen (Produktion RTO 1h / RPO 15min; Buchhaltung RTO 24h / RPO 4h).

#### 3. HelvetiaMed AG / SwissMediCare AG (Musterfall 3)
* *Problem:* Totaler Ausfall des Patientendaten-Servers. Das Backup war seit 14 Tagen unbemerkt voll- und abgebrochen.
* *Auswirkung:* Verlust von 3'500 Patienteneinträgen. Massiver Reputations- und Finanzschaden.
* *Lösung:* Einführung der 3-2-1-1-0 Strategie, tägliches Monitoring der Speicherkapazitäten, automatische Alarmierung und monatliche automatisierte Restore-Tests.

#### 4. FinSecure AG (Musterfall 4)
* *Problem:* Ransomware-Angriff am Wochenende; Server, E-Mail und Backup-Server verschlüsselt. Lösegeldforderung: 50 Bitcoins.
* *Lösung:* Kein Lösegeld zahlen. Notfallplan mit Air-Gapped Tapes und Immutable Cloud Storage (S3 Object Lock in Compliance Mode) zur sauberen Wiederherstellung.

#### 5. MediCare Bern AG (Musterfall 5)
* *Problem:* 18 Stunden Backup-Fenster und akuter Platzmangel bei 300 Windows-VMs.
* *Lösung:* Einsatz einer Deduplication-Appliance mit **Inline-Deduplizierung** (kein Platz für Landing Zone vorhanden) und **Source-Side Deduplication** (reduziert Übertragungszeit über das LAN/WAN drastisch). Datenreduktion um 90%.

#### 6. Mobirama / Mobiliar (Musterfall 6)
* *Problem:* Verschlüsselungstrojaner im Dezember 2017. Geschäftsführer verweigerte Lösegeldzahlung.
* *Ergebnis:* Wiederherstellung dauerte 3 Tage aus internen Backups. Schaden im mittleren 5-stelligen Bereich. Konsequenz: Grundlegende Überarbeitung der Backup-Strategie und Abschluss einer Cyber-Versicherung.

---

## SCHNELL-REFERENZ FÜR DIE PRÜFUNG (FORMELN & CHECKLISTEN)

### Formel-Sammlung auf einen Blick
1. **Risikowert:** $R = E \times S$
2. **Kombinierter Reduktionsfaktor:** $RF = \text{Deduplizierungsrate} \times \text{Komprimierungsrate}$
3. **Effektive Kapazität:** $V_{\text{effektiv}} = (V_{\text{roh}} / RF) \times 1,25$
4. **RAID 5 Kapazität:** $(n-1) \times \text{Disk-Grösse}$
5. **RAID 6 Kapazität:** $(n-2) \times \text{Disk-Grösse}$
6. **RAID 10 Kapazität:** $(n / 2) \times \text{Disk-Grösse}$

### Prüfungs-Checkliste zur Bewertung von Backup-Konzepten
- [ ] Werden **3 Kopien** gehalten?
- [ ] Werden **2 verschiedene Medien** genutzt?
- [ ] Ist **1 Kopie Offsite** (extern)?
- [ ] Ist **1 Kopie Offline/Air-Gapped oder Immutable**?
- [ ] Gibt es automatisierte **Restore-Tests (0 Fehler)**?
- [ ] Sind **RPO** und **RTO** pro Applikation klar definiert?
- [ ] Ist die Rolle des **Data Owners** und **Data Custodians** zugewiesen?
- [ ] Werden gesetzliche Fristen (**OR 958f = 10 Jahre**, **nDSG = TOM**) eingehalten?
