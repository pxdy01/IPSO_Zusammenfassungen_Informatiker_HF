Spicker & Prüfungsvorbereitung: Modulprüfung SIUS (System -Installation und -Störungsbehebung)

1. Microsoft Hyper-V & Virtualisierung

Architektur & Hypervisor-Modell

Hyper-V ist ein Type-1 Hypervisor (Bare-Metal). Er setzt direkt auf der physischen Server-Hardware auf und übernimmt die exklusive Steuerung aller Hardware-Virtualisierungsfunktionen.

* Ebene 0 (Level 0 – Hardware & Hypervisor): Physische CPU mit Virtualisierungserweiterungen (Intel VT / AMD-V) sowie der Hyper-V Hypervisor.
* Ebene 1 (Level 1 – Partitions-Schicht):
  * Parent Partition / Root Partition (Host OS): Führt das primäre Windows Server OS aus. Architektur-Grundsatz: Sämtliche physischen Hardware-Treiber laufen ausschließlich in dieser Host-Partition.
  * Child Partitions / Guest OS (VMs): Strikt isolierte virtuelle Maschinen. Gäste besitzen keinen direkten Hardwarezugriff; die Kommunikation erfolgt ausnahmslos über virtualisierte Hardwareschnittstellen (vCPU, vRAM, vNIC, vDisk).

Systemanforderungen (Host)

* CPU: 64-Bit-Prozessor mit Second-Level Address Translation (SLAT) und VM Monitor Mode Extensions.
* Virtualisierung im BIOS/UEFI: Aktiviertes Intel VT (Intel Virtualization Technology) oder AMD-V (AMD Virtualization).
* Sicherheitserweiterung: Hardwarebasierte Datenausführungsverhinderung (Hardware-DEP) via Intel XD Bit (Execute Disable) oder AMD NX Bit (No Execute).
* RAM: Ausreichend physischer Hauptspeicher für Host-Betriebssystem und kumulierte Gäste.

Management-Tools

Verwaltungswerkzeug	Haupteinsatzzweck & Enterprise-Kontext
Hyper-V Manager	MMC-basiertes Standard-GUI zur lokalen und einfachen Remote-Verwaltung einzelner Hosts und VMs.
System Center Virtual Machine Manager (SCVMM)	Enterprise-Plattform für zentrale Verwaltung großer, hochverfügbarer VM-Cluster und Software-Defined Data Centers (SDDC).
Windows Admin Center (WAC)	Modernes, browserbasiertes Management-Tool für Windows Server, HCI-Cluster und Hyper-V-Infrastrukturen.
PowerShell (Hyper-V Modul)	Vollständige CLI-Automatisierung via Skripte (Get-VM, Set-VM, Set-VMProcessor, New-VHD).

VM Configuration Version & Generationen

* VM Configuration Version: Bestimmt den verfügbaren Feature-Satz, das Konfigurationsformat und die Kompatibilität einer VM. Sie korrespondiert mit der Hyper-V-Host-Version, auf der die VM erstellt oder aktualisiert wurde.

Kriterium	Generation 1	Generation 2
Architektur	Legacy-BIOS-Emulation	UEFI-Firmware-Architektur
Betriebssysteme	Ältere OS & Legacy-Anwendungen (z. B. 32-Bit OS)	Moderne 64-Bit OS (Windows 11, Server 2022/2025, Linux)
Boot-Medien	IDE-Controller, emulierte Legacy-Netzwerkkarte	Synthetic SCSI-Controller, PXE via synthetic vNIC
Secure Boot Support	Nein (Nicht unterstützt)	Ja (Zwingende Voraussetzung für Secure Boot)
Performance	Langsamerer Boot-Vorgang durch Hardware-Emulation	Schnellerer Start, geringerer Overhead

Virtuelle Festplatten (VHD vs. VHDX) & Disktypen

* VHD Format: Limitierung auf max. 2 TB Kapazität. Anfällig für Datenbeschädigung bei Stromausfall.
* VHDX Format: Bis zu 64 TB Kapazität, höhere Performance, automatische Schutzmechanismen gegen Datenbeschädigung bei unerwarteten Stromausfällen.
* Disktypen:
  * Fixed Size (Feste Größe): Belegt den vollen Speicherplatz sofort bei Erstellung. Höchste E/A-Performance, keine Speicher-Overcommitment-Risiken.
  * Dynamically Expanding (Dynamisch): Belegt initial minimalen Speicher und wächst synchron mit der physischen Datennutzung der VM.
  * Differencing (Differenzierend): Untergeordnete Festplatte, die Änderungen isoliert gegenüber einer unveränderten Parent-VHD/VHDX speichert (Basis für Checkpoints und Golden Images).

Erweiterte Funktionen

* vSwitches: Virtuelle Switches (External, Internal, Private) zur Netzwerkanbindung und VLAN-Tagging.
* Checkpoints (Snapshots): Laufzeit- und Speicherzustandssicherung einer VM für Testzwecke (Produktions-Checkpoints nutzen VSS).
* Hyper-V Replica: Asynchrone VM-Replikation über IP-Netzwerke an Sekundärstandorte für Disaster Recovery.
* Live & Storage Migration: Unterbrechungsfreie Verschiebung von laufenden VMs (Live) oder deren Disks (Storage) zwischen Hosts/Datenspeichern.
* Integration Services: Host-Gast-Treiber und Hintergrunddienste (Zeitsynchronisation, Heartbeat, Shutdown, Data Exchange, VSS-Backup).
* Nested Virtualization: Verschachtelte Virtualisierung; ermöglicht das Ausführen von Hyper-V/Containern innerhalb einer Hyper-V-VM (erfordert Pass-Through der CPU-Virtualisierungsfunktionen via PowerShell: Set-VMProcessor -VMName <VM> -ExposeVirtualizationExtensions $true).

2. Container auf Windows-Systemen

Container bieten OS-Level-Virtualisierung und isolieren Anwendungen bei minimalem Ressourcen-Overhead im Vergleich zu Voll-VMs.

Isolierungsebenen

Merkmal	Prozess-Isolierung (Windows Server Container)	Hyper-V-Isolierung
Kernel-Architektur	Gemeinsamer Kernel mit dem Host (Shared Kernel)	Eigener Windows-Kernel pro Container
Laufzeit-Kapselung	Namensräume (Namespaces) & Control Groups auf Host	Container läuft in hochoptimierter Mini-VM
Ressourcenbedarf	Extrem gering, Millisekunden-Startzeiten	Geringfügig höher durch eigenen Kernel-Footprint
Sicherheitsniveau	Vertrauenswürdige Mandanten (Intra-Enterprise)	Strikte Mandantentrennung (Untrusted / Multi-Tenant Cloud)

Plattformen, Orchestrierung & Architektur

* Docker Engine: Container-Laufzeitumgebung zur Erstellung, Verwaltung und Paketierung von Container-Images.
* Kubernetes (K8s): Produktionsplattform für die automatisierte Skalierung, Bereitstellung, Deklaration und Vernetzung containerisierter Applikationen.
* Microservices vs. Monolith:

Kriterium	Monolithische Architektur	Microservices-Architektur
Entkopplung	Starke Kopplung aller Applikationskomponenten	Vollständige Entkopplung in eigenständige Services
Skalierbarkeit	Nur vertikal / gesamte Applikation replizierbar	Granulare, horizontale Skalierung einzelner Dienste
Wartbarkeit	Hohes Risiko bei Änderungen; komplexe Deployments	Unabhängige CI/CD-Pipelines pro Dienst

3. Microsoft Intune & Enterprise Endpoint Management

Microsoft Intune ist die cloudbasierte Unified Endpoint Management (UEM) Lösung für Gerätestuerung und Datensicherheit.

MDM vs. MAM

Kriterium	Mobile Device Management (MDM)	Mobile Application Management (MAM)
Fokus & Kontrolle	Vollständige Gerätekontrolle (Geräteregistrierung)	Schutz von Unternehmensdaten innerhalb spezifischer Apps
Einsatzbereich	Unternehmenseigene Geräte (Corporate-Owned)	Private Mitarbeitergeräte (BYOD – Bring Your Own Device)
Sicherheitsmechanismen	Remote-Wipe, BitLocker-Zwang, OS-Einschränkungen	App-Enkapsulierung, PIN-Schutz, Verhinderung von Copy-Paste

Co-Management, Provisionierung & Richtlinien

* Co-Management & Cloud Attach: Nahtlose Verbindung von Microsoft Endpoint Configuration Manager (MEC/SCCM) mit Intune. Erlaubt die schrittweise Verlagerung von Workloads (z. B. Compliance, Patching) in die Cloud.
* Windows Autopilot: Zero-Touch-Provisionierung. Geräte werden direkt vom Hersteller an den Endnutzer geliefert; Intune konfiguriert das Gerät automatisch beim ersten Anmelden.
* Compliance Policies & Settings Management: Definition von Richtlinien für den Gerätezustand (BitLocker, Antivirus, OS-Patchstand). Bei Nicht-Konformität greift der Bedingte Zugriff (Conditional Access).
* ADMX-Injektion: Gruppenrichtlinien-Vorlagen (ADMX) können direkt in Intune importiert werden, um klassische GPO-Einstellungen cloudbasiert auf Clients durchzusetzen.

4. Microsoft Defender & Windows Firewall

Microsoft Defender Antivirus

* Plattformunterstützung & Lizenzierung: Nativ in Windows 10/11 und Windows Server integriert. Für erweiterte Enterprise-Funktionen (EDR/XDR) ist eine Lizenzierung via Microsoft 365 E3/E5 oder Business Premium erforderlich.
* Scan-Typen im Vergleich:

Scan-Typ	Fokus & Abdeckung	Systemauslastung
Echtzeitschutz (Real-time)	Überprüft Dateien und Prozesse kontinuierlich beim Zugriff/Ausführung	Permanent im Hintergrund aktiv (minimal)
Quick Scan	Prüft kritische Systemordner, Registrierung und Speicherorte häufiger Malware	Sehr schnell (1–5 Min), vernachlässigbar
Full Scan	Tiefenprüfung aller Dateien auf allen Datenträgern und geladenen Speicherseiten	Hoch, beansprucht CPU & E/A über längeren Zeitraum

* Quarantäne: Passwortgeschützter, isolierter Systembereich des OS. Schadcode wird vom Dateisystem entkoppelt, verschlüsselt und an der Ausführung gehindert.
* Drittanbieter-AV: Die Installation einer Drittanbieter-Antivirensoftware versetzt Defender Antivirus automatisch in den Passiv-Modus (unter Windows Server) oder deaktiviert ihn (unter Windows Client), um Konflikte zu vermeiden.

Administration, Exclusions & Security Risks

* Verwaltungsschnittstellen: Windows Security App (lokal), PowerShell (Get-MpPreference, Add-MpPreference), Gruppenrichtlinien (GPO) sowie Microsoft Intune / Defender Portal.
* Exclusions (Ausnahmen): Gezielter Ausschluss von Pfaden, Dateitypen oder Prozessen.
  * Sicherheitsrisiko: Ausnahmen erzeugen blinde Flecken (Blind Spots). Angreifer nutzen bekannte Ausnahmepfade (z. B. Temp-Ordner von Business-Apps), um Schadcode unbemerkt vor dem Virenscanner auszuführen.

Windows Firewall & Security Design

* Kernfunktion: Hostbasierte Zustandsspeichernde Paketfilterung (Stateful Inspection).
* Sicherheitsnotwendigkeit neben Antivirus: Virenscanner agieren auf Datei- und Prozessebene. Die Firewall kontrolliert die Netzwerkschnittstelle, verhindert unautorisierten Netzwerkzugriff, blockiert Port-Scans und unterbindet das Ausbreiten von Angriffen (Lateral Movement) im Subnetz.
* Regelkomponenten: Richtung (Inbound / Outbound), Aktion (Allow / Block), Protokoll (TCP / UDP / ICMP), lokale/remote Ports, Quell-/Ziel-IP-Adressen und Profil (Domain, Private, Public).
* Least Privilege Prinzip: Netzwerktraffic ist standardmäßig eingehend zu blockieren (Default Deny). Freigaben erfolgen exklusiv für explizit zugelassene Quell-IPs, Systeme und benötigte Ports.

Enterprise Endpoint Security Ökosystem (Microsoft Defender XDR)

Defender-Komponente	Hauptschutzbereich & Enterprise-Fokus
Defender for Endpoint (MDE)	EPP & EDR: Verhaltensanalyse, Endpoint Detection and Response, Automated Investigation & Response (AIR) auf Client- & Server-Endpunkten.
Defender for Identity (MDI)	Identitätsschutz: Analysiert Active Directory / Entra ID Signale, erkennt Identity Attacks (Pass-the-Hash, Golden Ticket, Kerberoasting).
Defender for Cloud (MDC)	Cloud Security Posture Management (CSPM) und Workload-Schutz für Server-VMs, Container (K8s) und Datenbanken in Multi-Cloud-Umgebungen.
Defender for IoT	Agentenloser Schutz für Operational Technology (OT), Industrieanlagen und unmanaged IoT-Infrastrukturen.

5. GitHub & Git Workflow

Git Basics

* Repository (Repo): Der zentrale oder lokale Speicherort für Projektcode, Versionierungshistorie und Metadaten.
* Branch: Ein isolierter Entwicklungszweig zur getrennten Arbeit an Features oder Bugfixes, ohne den Hauptcode zu beeinträchtigen.
* Commit: Ein kryptografisch signierter Snapshot von Codeänderungen inklusive Autor und Änderungsbeschreibung.
* Pull Request (PR): Ein Antrag zur Überprüfung und Zusammenführung (Merge) von Code aus einem Feature-Branch in den Ziel-Branch.

GitHub Flow & Enterprise Safety

1. Main Branch: Repräsentiert produktionsbereiten, geschützten Code.
2. Feature Branch: Wird für jede Änderung neu vom main Branch abgezweigt.
3. Commits & Push: Änderungen werden lokal committet und in das GitHub-Remote-Repo hochgeladen.
4. Pull Request & Review: Automatisierte CI-Tests starten. Code-Review durch mindestens einen Peerexlusiv erfordert.
5. Merge into Main: Nach erfolgreichem Review und bestandenen Pipeline-Checks wird der Feature-Branch gemergt.

* Branch Protection Rules: Verhindern direkte Pushes auf den main Branch, erzwingen signierte Commits und machen bestandene CI-Statuschecks zur Voraussetzung.
* GitHub Actions & Gists: Actions bieten native CI/CD-Automatisierung für Tests und Infrastructure Deployments. Gists dienen dem Teilen von Code-Snippets.

6. Generative KI, Microsoft Foundry & Security Copilot

Grundlagen & Architektur

* Large Language Models (LLMs): Neuronale Netzwerke zur Text- und Code-Verarbeitung auf Basis der Transformer-Architektur.
* Prompts: Präzise formulierte Eingabeinstruktionen. Das Prompt Engineering bestimmt Qualität und Genauigkeit des KI-Outputs.
* Agents: Autonome KI-Instanzen, die Ziele analysieren, komplexe Aufgaben in Teilaktionen zerlegen und über APIs externe Tools steuern.

Microsoft Security Copilot & Ökosystem

Security Copilot nutzt generative KI, gekoppelt mit der weltweiten Threat Intelligence von Microsoft, zur Beschleunigung von SOC-Abläufen.

* Microsoft Entra: KI-gestützte Erkennung von anomalen Anmeldeversuchen, Risiko-Evaluierung von Identitäten und automatische Rechteminimierung.
* Microsoft Intune: Automatische Generierung von Konfigurationsprofilen und Compliance-Richtlinien via natürlicher Sprache sowie Auswirkungssimulation.
* Microsoft Defender: Automatisierte Incident-Zusammenfassung, Übersetzung von komplexen KQL-Abfragen (Kusto Query Language), Triage von Warnmeldungen und geführtes Threat Hunting.

7. Infrastructure as Code (IaC) & Azure Bicep

IaC-Paradigmen

Paradigma	Funktionsweise	Typische Werkzeuge
Deklarativ	Definiert den gewünschten Zielzustand (WAS gebaut werden soll). Engine berechnet Abhängigkeiten und Differenzen automatisch.	Azure Bicep, ARM-Templates, Terraform
Imperativ	Definiert Schritt-für-Schritt-Anweisungen (WIE gebaut werden soll). Skript steuert jeden Ausführungsschritt sequenziell.	PowerShell, Azure CLI, Bash

ARM vs. Bicep

Bicep ist eine domänenspezifische Sprache (DSL), die als transparente, lesbare Abstraktionsschicht über JSON-basierten Azure Resource Manager (ARM) Templates liegt. Bicep bietet eine schlanke Syntax, automatische Abhängigkeitsberechnung, First-Class-Typisierung und direkte Unterstüzung aller Azure-Ressourcen ab Tag 0.

Production-Grade Bicep Code-Beispiel

// Parameter mit Dekoratoren für Validierung und Dokumentation
@description('Azure-Region für den Deployment-Resource-Group-Kontext')
param location string = resourceGroup().location

@description('Umgebungstyp zur Festlegung des Tier-Skus')
@allowed([
  'dev'
  'prod'
])
param environmentType string = 'prod'

@description('Der Name des Storage Accounts (muss global eindeutig sein)')
@minLength(3)
@maxLength(24)
param storageAccountName string = 'st${uniqueString(resourceGroup().id)}'

// Variablenberechnung
var skuName = (environmentType == 'prod') ? 'Standard_GRS' : 'Standard_LRS'

// Ressourcendefinition nach Security Best Practices (TLS 1.2, HTTPS only)
resource storageAccount 'Microsoft.Storage/storageAccounts@2023-01-01' = {
  name: storageAccountName
  location: location
  sku: {
    name: skuName
  }
  kind: 'StorageV2'
  properties: {
    supportsHttpsTrafficOnly: true
    minimumTlsVersion: 'TLS1_2'
    allowBlobPublicAccess: false
  }
}

// Module: Einbindung wiederverwendbarer Infrastruktur-Bausteine
module networkModule 'modules/network.bicep' = {
  name: 'networkDeployment'
  params: {
    location: location
  }
}

// Output zur Rückgabe von Werten an nachgelagerte Pipeline-Schritte
@description('Die primäre Blob-Endpunkt-URL des erstellten Storage Accounts')
output storageEndpoint string = storageAccount.properties.primaryEndpoints.blob


Best Practices für Bicep

* Modularisierung: Aufteilung komplexer Vorlagen in wiederverwendbare, fokussierte Bicep-Module.
* Sicherheitskonfiguration: Niemals Secrets/Passwörter im Code hardcoden; Übergabe via Azure Key Vault Referenzen.
* Validierung: Parameter mittels Dekoratoren (@allowed, @minLength, @maxLength) strikt validieren.
* Namenskonventionen: Dynamische Namensgenerierung mit uniqueString(resourceGroup().id) zur Vermeidung von Namenskonflikten.

8. Dedizierter Schlussabschnitt: Vollständige Fragensammlung & Leitfragen-Antworten

8.1 Fragensammlung: Microsoft Hyper-V (Recherchefragen)

* Welche Funktionalitäten besitzt Microsoft Hyper-V?
  * Management: Hyper-V Manager GUI, Windows Admin Center, PowerShell-Modul (Hyper-V).
  * Portability: Live Migration (unterbrechungsfreie VM-Verschiebung), Storage Migration, Import/Export-Funktionen.
  * Disaster Recovery: Hyper-V Replica (asynchrone VM-Spiegelung an Sekundärstandort), Produktions-Checkpoints/Snapshots.
  * Security: Secure Boot, Shielded VMs (Hardware-TPM-Virtualisierung).
  * Optimization: Integration Services (Zeitsynchronisation, VSS-Backup, Guest Services, Heartbeat).
* Was ist ein Hypervisor?
  * Definition: Software-/Firmware-Schicht, die Hardware-Ressourcen abstrahiert und virtuelle Maschinen steuert.
  * Architektur-Details: Hyper-V ist ein Type-1 Hypervisor. Hardware-Treiber laufen nur im Host-OS (Parent Partition / Level 1). Gast-VMs (Child Partitions / Level 1) kommunizieren ausschließlich über den Hypervisor (Level 0) mit virtualisierter Hardware (vCPU, vRAM, vNIC, vDisk).
* Welche Gastbetriebssysteme werden von Hyper-V unterstützt (Stand Feb 2024)?
  * Windows: Alle unterstützten Client- und Server-Editionen (Windows 10/11, Server 2016–2022/2025).
  * Linux & BSD: Red Hat Enterprise Linux, CentOS, Debian, Ubuntu, SUSE Enterprise Linux, Oracle Linux sowie FreeBSD.
* Was sind die System Requirements für Hyper-V?
  * CPU: 64-Bit mit SLAT und VM Monitor Mode Extensions.
  * BIOS/UEFI: Intel VT / AMD-V aktiviert; Hardware-DEP aktiviert (Intel XD Bit / AMD NX Bit).
  * RAM: Physischer Hauptspeicher für Host-OS plus alle aktiven VMs.
* Mit welchen Tools kann man Hyper-V verwalten?
  * Hyper-V Manager: MMC-GUI für Einzel-Hosts.
  * SCVMM: Enterprise Cluster- und SDDC-Verwaltung.
  * Windows Admin Center: Browserbasiertes Management.
  * PowerShell: Skriptbasierte Voll-Automatisierung.
* Was sind mögliche Use Cases für Hyper-V?
  * Server-Konsolidierung: Reduzierung physischer Hardware durch Multiplexing mehrerer Server-Dienste auf einem Host.
  * Test- & Entwicklungsumgebungen: Schnelle Bereitstellung und Isolation von Test-Systemen via Checkpoints.
  * Legacy-App-Isolierung: Weiterbetrieb älterer Betriebssysteme isoliert von der physischen Hardware.
  * Multi-Tenant-Clouds: Strikte Mandantentrennung auf physischen Compute-Nodes.
* Wie können VM Settings gesetzt werden?
  * Verwaltungs-Interfaces: Hyper-V Manager (GUI via VM Settings), Windows Admin Center.
  * PowerShell CLI: Cmdlets wie Set-VM (RAM/Dynamic Memory), Set-VMProcessor (vCPU-Anzahl/Nested Virtualization), Set-VMNetsworkAdapter (VLAN-IDs).
* Was ist eine VM Configuration Version und wie wird sie bestimmt?
  * Definition: Kennzeichnung für das Feature-Set und Format der VM-Konfigurationsdatei.
  * Bestimmung: Entspricht der spezifischen Hyper-V-Host-Version, auf der die VM erstellt oder explizit hochgestuft wurde.
* Was ist eine VM Generation? Welche existieren und welche wird für Secure Boot benötigt?
  * Gen 1: Legacy-BIOS-Architektur, IDE-Controller, emulierte Hardware.
  * Gen 2: UEFI-Architektur, synthetic SCSI, schnellere Boot-Zeiten.
  * Secure Boot: Erfordert zwingend Generation 2.
* Was ist eine VHD? Welche VHD-Typen existieren?
  * VHD vs. VHDX: VHD (bis 2 TB), VHDX (bis 64 TB, stromausfallsicher).
  * Typen: Fixed (feste Größe reserviert), Dynamic (wachsend), Differencing (Änderungsspeicher zu Basis-Disk).

8.2 Fragensammlung: Gruppe 1 – Defender Antivirus: Schutz & Erkennung

* Was ist der Unterschied zwischen Echtzeitschutz, Quick Scan und Full Scan?
  * Echtzeitschutz: Permanent / Präventiv – Analysiert Systemaufrufe, Downloads und Prozessstarts im Millisekundenbereich beim Zugriff.
  * Quick Scan: Gezielt / Reaktiv – Scannt innerhalb weniger Minuten typische Malware-Einnistorte (Registry, Autostart, %AppData%, System32).
  * Full Scan: Umfassend / Reaktiv – Durchsucht sequenziell alle Dateien aller lokalen Laufwerke und den kompletten RAM.
* Was bedeutet Quarantäne?
  * Prozess: Das Betriebssystem isoliert die betroffene Datei in ein geschütztes Verzeichnis (C:\ProgramData\Microsoft\Windows Defender\Quarantine), verschlüsselt den Inhalt und entzieht die Ausführungsrechte.
* Welcher Prozess läuft bei einer Bedrohungserkennung ab?
  * Prozesskette: Bedrohung → Erkennung → Blockierung/Quarantäne → Information → Bereinigung → Kontrolle
* Reicht die Meldung „Threat removed“ in einem Unternehmen aus?
  * Bewertung: Nein, keinesfalls.
  * Erforderliche Enterprise-Folgeaktivitäten:
    * Root Cause Analysis (RCA): Wie gelangte die Malware auf den Endpunkt (Phishing, Drive-by, USB, Unpatched Vulnerability)?
    * Lateral Movement Check: Hat sich die Malware im Netzwerk weiterverbreitet oder Anmeldedaten abgegriffen?
    * EDR Telemetrie-Analyse: Untersuchung der Prozess-Abläufe vor der Blockierung im Defender Portal.
    * System Audit: Prüfung von Schattenkopien, Persistence-Mechanismen (Scheduled Tasks, Registry Keys) und Netzwerk-Logs.
* Ist Microsoft Defender Antivirus alleine ein ausreichender Schutz für ein Unternehmen?
  * Bewertung: Nein.
  * Begründung: Ein reiner Datei-Virenscanner schützt nicht vor fileless Attacks, Identity Theft oder neuartigen Zero-Day-Exploits. Unternehmen benötigen eine mehrschichtige Schutzarchitektur (Defense-in-Depth): EDR/XDR (Defender for Endpoint), Netzwerksicherheit (Firewall/Segmentation), Identity Protection (Entra ID / MFA) und ein zentrales SIEM/SOC.

8.3 Fragensammlung: Gruppe 2 – Defender Administration & Exclusions

* Ein Softwarehersteller verlangt das Ausschließen des kompletten Installationsordners von Microsoft Defender. Würdet ihr diese Ausnahme erstellen? Welches Risiko entsteht und wie sieht eine sicherere Lösung aus?
  * Entscheidung: Nein, die Ausnahme darf keinesfalls pauschal erstellt werden.
  * Risiko-Analyse: Der ausgeschlossene Ordner wird zum blinden Fleck (Blind Spot). Angreifer können Schadcode gezielt dort platzieren und unbemerkt ausführen.
  * Erforderliche Abklärungen: Analyse der Ursache (Echtzeit-Performance-Engpass oder False-Positive-Blockade?), Einfordern detaillierter Hersteller-Dokumentation.
  * Sicherere Alternative:
    1. Process Exclusion: Exklusiv die spezifischen, digital signierten Prozesse der Anwendung ausschließen statt des ganzen Pfads.
    2. Gezielte Datei-Ausnahme: Ausschluss nur auf spezifische Dateiendungen oder Unterordner begrenzen.
  * Überwachung & Auditing: Zentrale Vergabe der Ausnahmen via Intune/GPO, fortlaufende Überwachung via PowerShell (Get-MpPreference) und automatische Alarmierung bei Ausnahmespeicherung via EDR.
* Wie findet man ein sinnvolles Gleichgewicht zwischen Security und IT-Betrieb?
  * Ansatz: Risikobasierte Entscheidungsfindung (Least Privilege). Ausnahmen so eng wie möglich fassen, zeitlich befristen, lückenlos im Change Management dokumentieren und mit kompensierenden Sicherheitskontrollen (z. B. erhöhtes EDR-Monitoring für den Ausnahmepfad) versehen.

8.4 Fragensammlung: Gruppe 3 – Endpoint Security im KMU-Szenario

* Ausgangslage KMU: 100 Mitarbeitende | Windows 11 | Microsoft 365 | 2 IT-Mitarbeitende | begrenztes Security-Know-how.
* Begriffsabgrenzung:
  * Antivirus (AV): Reaktiv, signatur- und heuristikbasierte Blockierung bekannter Schadsoftware.
  * Endpoint Protection Platform (EPP): Integrierte Schutz-Suite (AV, Host-Firewall, Web-Schutz, Device Control).
  * Endpoint Detection and Response (EDR): Kontinuierliches Telemetrie-Monitoring, Verhaltensanalyse, Threat Hunting und automatisierte Response-Abläufe bei komplexen Incidents.
* Vergleichsauftrag: Microsoft Defender for Endpoint vs. Enterprise-Alternative (z. B. CrowdStrike / SentinelOne):

Vergleichskriterium	Microsoft Defender for Endpoint (M365 Business Premium)	Alternative Enterprise EDR (z. B. CrowdStrike / SentinelOne)
Schutzfunktionen & EDR	Erstklassig; KI-gestützte Verhaltensanalyse & Automated Remediation	Erstklassig; hochspezialisierte KI-Verhaltensanalyse
Zentrale Verwaltung	Integriertes Microsoft Defender Portal & Intune (Single Pane of Glass)	Eigenständige Konsole der jeweiligen Drittanbieter-Cloud
Integration	Nativ im Windows OS; nahtlos mit Entra ID, Conditional Access & M365	Erfordert separaten Agenten auf allen Endpunkten
Lizenzierung & Kosten	In M365 Business Premium enthalten (keine Zusatzlizenz nötig)	Zusätzliche Lizenzkosten pro Endpunkt / Jahr
Betriebsaufwand	Extrem gering; automatisierte Vorfallsbereinigung entlastet IT	Mittel bis hoch; erfordert dediziertes Know-how für Konsole
Skalierbarkeit	Nahtlos von KMU bis Enterprise skalierbar	Nahtlos skalierbar

* Managemententscheidung & Empfehlung für das KMU:
  * Konkrete Empfehlung: Microsoft Defender for Endpoint via Microsoft 365 Business Premium.
  * Strategische Begründung: Das KMU besitzt bereits Windows 11 und Microsoft 365. Die Lösung erfordert keine Installation von Drittanbieter-Agenten und keine zusätzliche Infrastruktur. Bei einer IT-Personalstärke von nur 2 Personen entlasten die automatisierten Vorfallsbereinigungen (Automated Investigation & Response) das Team massiv. Es entstehen keine zusätzlichen Software-Kosten, da Defender for Endpoint in der Business Premium Lizenz bereits enthalten ist.

8.5 Fragensammlung: Gruppe 4 – Firewall & Security Design

* Warum wird trotz Antivirus eine Firewall benötigt?
  * Antwort: Antivirus arbeitet inhalts- und prozessorientiert auf dem Host. Die Firewall arbeitet netzwerkorientiert an der Schnittstelle. Sie blockiert unautorisierte Netzwerkanfragen, verhindert Port-Scans und stopt Angreifer beim Versuch, sich innerhalb des Netzwerks weiterzubewegen (Lateral Movement).
* Spezialauftrag Firewall Designer – Regelmatrix nach dem Least Privilege Prinzip:

Dienst & Port	Quell-Entität (Wer)	Ziel-Entität (Wohin)	Aktion	Technische Begründung & Bedrohungsvektor
HTTPS (TCP 443)	Any / Internet	Webserver (DMZ)	ALLOW	Öffentlicher Webdienst. Server muss zwingend in einer DMZ isoliert sein.
RDP (TCP 3389)	Admin-Subnetz / VPN	Ziel-Server	ALLOW	Administrator-Zugriff nur aus verschlüsseltem Admin-Segment mit MFA.
RDP (TCP 3389)	Any / Internet	Alle Systeme	BLOCK	Strikte Sperre! Schutz vor automatisierten Brute-Force-Angriffen, Password Spraying und RDP-Exploits (z. B. BlueKeep).
SQL (TCP 1433)	Applikations-Server	Datenbank-Server	ALLOW	Exklusiver Datenbankzugriff nur für die dedizierte Anwendungs-IP.
SQL (TCP 1433)	Client-Netz / Internet	Datenbank-Server	BLOCK	Direkter Datenbankzugriff aus dem Nutzer-Netz oder Internet ist ein kritisches Sicherheitsrisiko.

* Warum ist „Port öffnen“ alleine noch keine gute Firewall-Strategie?
  * Antwort: Ein geöffneter Port ohne strikte Beschränkung der Quell- und Ziel-IP-Adressen ist eine offene Einladung für Angreifer. Eine effektive Firewall-Strategie schränkt die Quellen strikt ein (Least Privilege), nutzt stateful Inspection und kombiniert Port-Regeln mit IPS/IDS sowie Anwendungsprüfung.
