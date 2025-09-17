
# Zusammenfassung für die Prüfung: Grundlagen der Client- und Server-Installation & Cloud-Technologien

Diese Zusammenfassung deckt die Kernkonzepte der Units 1 bis 8 ab, einschliesslich Windows Clients, Windows Server, PowerShell, Active Directory, DNS, DHCP, Azure und Entra ID.

---

### **Unit 1: Grundlagen Windows Client Betriebssystem**

*   **Windows Clients Funktionen & Unterschiede:** Techniker HF können die Hauptunterschiede und -merkmale zwischen **Windows 10 und Windows 11** detailliert beschreiben, einschliesslich Benutzeroberfläche, neuer Funktionen, Systemanforderungen, verfügbaren Editionen und Verbesserungen gegenüber früheren Versionen. Präsentationen können zu Themen wie Funktionen, Unterschiede, Systemanforderungen, Editionen, Benutzeroberfläche und Management von Windows 11 erstellt werden.
*   **Installation von Windows Clients:** Es gibt verschiedene Optionen für die Installation eines Windows-Clients, einschliesslich des Installationsprozesses von Windows 10, des Upgradeprozesses von Windows 10 und verschiedener Methoden der automatischen Client-Installationen.
*   **Windows Clients Servicing:**
    *   Der **General Availability Channel** bietet stabile und breit verfügbare Windows-Updates für Endbenutzer.
    *   Der **Long-Term Servicing Channel** bietet Unternehmen langfristige Unterstützung und Stabilität durch weniger häufige, aber langfristig unterstützte Updates.
    *   Das **Windows Insider Program** ermöglicht es Benutzern, Vorabversionen zu testen und Feedback zu geben.
*   **Windows Clients Editionen:** Es existieren verschiedene Editionen, die sich in Funktionen und Zielgruppen unterscheiden. Beispiele für Windows 10 Editionen sind:
    *   **Home:** Für den Heimgebrauch mit grundlegenden Funktionen.
    *   **Pro:** Erweiterte Funktionen für kleine Unternehmen und professionelle Anwender (Domänensupport, erweiterte Sicherheit, Remote-Desktop).
    *   **Enterprise:** Für größere Unternehmen mit erweiterten Sicherheits- und Verwaltungsfunktionen und Volumenlizenzierungsoptionen.
    *   **Education:** Speziell für Bildungsein:** Es existieren verschiedene Editionen, die sich in Funktionen und Zielgruppen unterscheiden. Beispiele für Windows 10 Editionen sind:
    *   **Home:** Für den Heimgebrauch mit grundlegenden Funktionen.
    *   **Pro:** Erweiterte Funktionen für kleine Unternehmen und professionelle Anwender (Domänensupport, erweiterte Sicherheit, Remote-Desktop).
    *   **Enterprise:** Für größere Unternehmen mit erweiterten Sicherheits- und Verwaltungsfunktionen und Volumenlizenzierungsoptionen.
    *   **Education:** Speziell für Bildungseinrichtungen.
    *   Spezifische Funktionen wie **BitLocker-Verschlüsselung, Domänenbeitritt, Gruppenrichtlinienverwaltung, Windows Sandbox** (Pro und Enterprise) und **Windows Update for Business** sind nur in Pro und höheren Editionen verfügbar.
*   **Hardwareanforderungen:** Die Anforderungen variieren je nach Windows-Version (Prozessor, RAM, Festplattenspeicher, Grafikkarte, Anzeige). Eine grosse Diskussion gab es bezüglich der Änderungen zwischen Windows 10 und Windows 11, insbesondere die Notwendigkeit von **TPM 2.0 (Trusted Platform Module) und Secure Boot** für Windows 11, um die Sicherheit und Integrität zu verbessern.
*   **Windows Clients Upgrade:** Unternehmen wechseln zu Windows 11 wegen verbesserter Sicherheit (TPM 2.0, Secure Boot), neuen Funktionen (Snap Layouts, virtuelle Desktops), besserer Leistung, Unterstützung für neue Technologien und langfristiger Kompatibilität.
*   **Upgrade vs. Migration:** Ein **Upgrade** ist der direkte Versionswechsel auf demselben Gerät, während eine **Migration** den Umzug von Benutzer- und Systemdaten auf ein neues Gerät oder in eine neue Umgebung meint.
*   **Windows Clients Imaging:**
    *   **Imaging** ist der Prozess des Erstellens einer genauen Kopie eines Computersystems oder einer Festplatte, einschliesslich des Betriebssystems, der Anwendungen und Benutzerdaten.
    *   **Vorteile:** Schnelle Bereitstellung, konsistente Konfigurationen, einfache Wiederherstellung nach einem Fehler oder Datenverlust.
    *   **Nachteile:** Grosser Speicherplatzbedarf, zeitaufwändige Updates, mögliche Inkompatibilitäten mit unterschiedlicher Hardware.
    *   **Online Servicing** bezieht Updates direkt aus dem Internet, während **Offline Servicing** Updates von lokal gespeicherten Quellen bezieht.
    *   **Szenarien:** Rollout neuer Arbeitsplatzrechner, Systemaktualisierungen, Wiederherstellung nach Systemausfall oder schnelle Bereitstellung identischer Systemkonfigurationen.
    *   **Tools:** Microsoft Deployment Toolkit (MDT), Windows Deployment Services (WDS), System Center Configuration Manager (SCCM), Clonezilla, Acronis True Image, Symantec Ghost.
*   **Windows PE (Preinstallation Environment):** Eine minimale Betriebssystemumgebung von Microsoft für die Bereitstellung und Wiederherstellung von Windows-Betriebssystemen. Um Windows PE auf einem physischen Gerät zu verwenden, müssen die entsprechenden **Treiber für die Zielhardware** hinzugefügt werden.

---

### **Unit 2: Grundlagen Windows Server Betriebssystem**

*   **Lernziele:** Absolventen können Windows Server detailliert beschreiben (Benutzeroberfläche, Funktionen, Systemanforderungen, Editionen), Installations- und Upgrade-Optionen umfassend erklären und Kenntnisse über Lizenzierungsoptionen und Aktivierungsmethoden erlangen.
*   **Windows Server Editionen:** Es gibt verschiedene Editionen von Windows Server, die sich in Funktionen und Zielgruppen unterscheiden. Die Quellen erwähnen, dass neue Editionen mit Windows Server 2022 existieren und fragen nach minimalen Hardwareanforderungen (RAM, CPU, Disk) sowie nach LTSC oder Semi Annual Channels.
*   **Windows Server Funktionen:** Techniker sollen neue Features von Windows Server 2022 und 2019 nennen können. Ein "deprecated Feature" ist ein Feature, das nicht mehr weiterentwickelt wird oder durch neuere Technologien ersetzt wurde.
*   **Server Core vs. Server with Desktop Experience:**
    *   **Server Core** bietet eine minimale Installation ohne grafische Benutzeroberfläche.
    *   **Server with Desktop Experience** beinhaltet die vollständige grafische Benutzeroberfläche.
    *   Beide haben Vor- und Nachteile hinsichtlich Ressourcenverbrauch, Sicherheit und Verwaltungsaufwand.
*   **Windows Server Updates:** Updates können auf einem Windows Server installiert werden, und es gibt unterstützte Versionen und **Extended Security Updates (ESU)**, die über das normale Supportende hinaus Sicherheitsupdates bereitstellen.
*   **Windows Server Upgrade:** Es gibt verschiedene Migrationsmöglichkeiten. Ein Inplace Upgrade von Windows Server 2012 auf Windows Server 2019 ist oft nicht direkt unterstützt.
*   **Windows Server Aktivierung:**
    *   **KMS (Key Management Service):** Ein Dienst von Microsoft zur Aktivierung von Volumenlizenzversionen von Microsoft-Produkten in einer Unternehmensumgebung; Clients werden aktiviert, wenn die Anzahl höher als 25 ist.
    *   **MAK Key (Multiple Activation Key):** Ein Schlüssel zur Aktivierung von Volumenlizenzen, der eine Verbindung zu Microsofts Aktivierungsservern benötigt.
    *   **VAMT (Volume Activation Management Tool):** Verwaltungstool von Microsoft zur Verwaltung von Volumenaktivierungsschlüsseln, Überwachung von Produktaktivierungen und Erstellung von Berichten.
    *   **AVMA (Automatic Virtual Machine Activation):** Ermöglicht die automatische Aktivierung virtueller Windows Server-Instanzen auf Hyper-V-Hosts ohne separate Produktaktivierung, indem der Hypervisor und der KMS-Host des Hosts genutzt werden.
*   **Windows Server Lizenzierung (Core/CAL):**
    *   Windows Server Standard und Datacenter werden nach **Core oder Core/CAL** lizenziert.
    *   Bei der Core-Lizenzierung muss jeder physische Core lizenziert werden (mindestens 8 Cores pro Prozessor und im Gesamtvertrag mindestens 16 Cores). Alternativ kann nach individuellen virtuellen Maschinen lizenziert werden (jeder virtuelle Core lizenziert, 16 Cores im Gesamtvertrag).
    *   Zusätzlich zu Core Licenses können **CALs (Client Access Licenses)** für jedes Gerät oder jeden Benutzer erforderlich sein, der direkt oder indirekt auf den Server zugreift.
    *   SQL Server und Biztalk Server werden nur nach Core lizenziert.

---

### **Unit 3: Grundlagen Windows PowerShell**

*   **Lernziele:** Techniker können die Grundlagen von Windows PowerShell präzise beschreiben, Commandlets erläutern, mit Variablen und Pipelines arbeiten, Skripte erstellen/ausführen, Parameter definieren, If-, Else-, Elseif-Abfragen nutzen und einfaches Error-Handling (Try/Catch) durchführen.
*   **Was ist PowerShell?** Eine plattformübergreifende Lösung zur Aufgabenautomatisierung, bestehend aus einer Befehlszeilen-Shell, einer Skriptsprache und einem Konfigurationsmanagement-Framework. PowerShell läuft unter Windows, Linux und macOS. Sie wird als Skript- und Automatisierungssprache und damit auch als Programmiersprache betrachtet.
*   **Einsatzbereich:**
    *   Standardmäßig auf Windows-Systemen installiert und die Standard-Command-Line-Shell.
    *   Kann für Systemverwaltung, Automatisierung, Konfigurationsmanagement und Skripterstellung verwendet werden.
    *   Verwendbar für viele Microsoft-Produkte (Windows Server, Exchange Server, SharePoint, Azure) und Drittanbieterprodukte (VMware, Citrix, AWS).
    *   **PowerShell DSC (Desired State Configuration)** verwendet eine deklarative Syntax, um Systemkonfigurationen zu definieren und aufrechtzuerhalten.
*   **PowerShell Versionen:** Es wird zwischen PowerShell 5.1 (basiert auf .NET Framework 4.5) und PowerShell 7.x und höher (basiert auf .NET Core 2.0, plattformübergreifend) unterschieden.
*   **Arbeitsumgebungen:** VSCode, Windows Terminal, Standard PowerShell.
*   **PowerShell Commands (Cmdlets):** Befehle in PowerShell werden als **Cmdlets** bezeichnet und bestehen immer aus einem Verb und einem Nomen.
*   **Tipps und Tricks:** TAB-Taste für Autovervollständigung, `Get-Help` für Hilfe, Pfeil Oben für den letzten Befehl.
*   **PowerShell Pipeline:** Eine Verkettung mehrerer PowerShell-Befehle mit dem Pipeline Operator "**|**".
*   **Variablen:** PowerShell ermöglicht das Speichern von Informationen in Variablen, die für spätere Zwecke aufgerufen werden können. Es gibt User Created Variables, Preference Variables und Automatic Variables. Jedes Objekt (Integer, String, Arrays, Hash Tables, Prozesse, Services, Event Logs oder Computer) kann als Variable gespeichert werden.
*   **PowerShell Skriptausführung:**
    *   Die **Ausführungsrichtlinie (Execution Policy)** ist eine Sicherheitsfunktion, die das Laden von Konfigurationsdateien und die Ausführung von Skripten steuert.
    *   Die Ausführung von Skripten ist in aktuellen Client- und Serverbetriebssystemen standardmässig deaktiviert.
    *   Die Sicherheitsrichtlinien sind "Restricted", "AllSigned", "RemoteSigned", "Unrestricted" und "Bypass".
    *   Gültigkeitsbereiche sind "Machine", "User" und "Process".
    *   Ein PowerShell-Skript kann mit `Set-AuthenticodeSignature` digital signiert werden.
*   **PowerShell Remoting:** Erlaubt die Ausführung von PowerShell auf mehreren Rechnern und unterstützt WMI, WS-Management und SSH Remoting.

---

### **Unit 4: Grundlagen Active Directory**

*   **Lernziele:** Techniker HF können Active Directory Domain Services (AD DS) erklären, Benutzer-, Gruppen- und Computerobjekte erstellen/verwalten, fortgeschrittene Konzepte (Forest, Domänen, Trust Relationships, OUs, AD DS Rollen) verstehen und Gruppenrichtlinienobjekte (GPOs) erstellen/verteilen. Sie können Active Directory effektiv mit PowerShell verwalten.
*   **Active Directory Domain Services (AD DS) Grundlagen:**
    *   **AD DS** ist ein Verzeichnisdienst von Microsoft zur Verwaltung von Netzwerkressourcen wie Benutzern, Computern und anderen Objekten in einer strukturierten Form.
    *   **Objekte** in AD DS können Benutzer, Gruppen, Computer, Drucker usw. sein.
    *   Ein **Active Directory Forest** ist eine Sammlung von einer oder mehreren Domänen, die eine gemeinsame Schemadefinition, Konfiguration und einen globalen Katalog teilen.
    *   Eine **Active Directory Domain** ist eine logische Gruppierung von Objekten.
    *   Eine **Organizational Unit (OU)** ist ein Container innerhalb einer Domäne zur Organisation von Objekten und zur Anwendung von Gruppenrichtlinien.
    *   Das **AD DS Schema** definiert die Objekte und Attribute, die in AD gespeichert werden können. Änderungen am Schema sind kritisch und sollten von erfahrenen Administratoren mit Tools wie ADSI Edit vorgenommen werden.
*   **Domain Controller (DC):**
    *   Ein DC ist ein Server, der die Active Directory-Datenbank hostet und Authentifizierungs- und Autorisierungsdienste bereitstellt.
    *   Der **Global Catalog Server** enthält eine partielle Replikation aller Objekte im Forest und dient der schnellen Suche.
    *   Es gibt **fünf FSMO-Rollen (Flexible Single Master Operations)**: Schema Master (einmal pro Forest), Domain Naming Master (einmal pro Forest), RID Master (einmal pro Domäne), PDC Emulator (einmal pro Domäne), Infrastructure Master (einmal pro Domäne).
*   **Benutzer, Gruppen und Computer:**
    *   **Benutzer** sind Anmeldekonten. Bei der Erstellung sind Attribute zwingend. Der **UPN (User Principal Name)** ist eine eindeutige Kennung.
    *   **Gruppen** dienen der Bündelung von Benutzern für die Verwaltung von Berechtigungen. Es gibt verschiedene Gruppen-Typen und Anwendungsfälle. Das **IGDLA (oder AGDLP) Prinzip** (Users in Global Groups, Global Groups in Domain Local Groups, Domain Local Groups get Access to Resources) ist ein Best Practice für die Berechtigungsvergabe.
    *   **Computer** können einer Domäne hinzugefügt werden. Es gibt ein Computer Machine Password.
*   **ADDS Replikation:** Der Prozess, bei dem Änderungen an AD DS-Daten zwischen Domaincontrollern repliziert werden, um Konsistenz und Verfügbarkeit zu gewährleisten. Die **Multimaster-Replikation** erlaubt es mehreren DCs, gleichzeitig Änderungen vorzunehmen.
*   **Active Directory Trust:**
    *   Ein Trust ermöglicht es einer Domäne, Ressourcen (Dateien, Ordner, Drucker) in einer anderen Domäne zu verwenden und Benutzern Zugriff ohne erneute Anmeldung zu gewähren.
    *   **Trust-Typen:** Einweg-Trust (Ressourcenzugriff nur in eine Richtung), Zweiweg-Trust (Ressourcenzugriff in beide Richtungen), Transitiver Trust (Vertrauen wird über eine Kette von Domänen weitergegeben).
    *   **Trust-Richtungen:** Eingehender Trust (Zugriff auf Ressourcen erhalten), Ausgehender Trust (Ressourcen bereitstellen).
    *   **Protokolle:** Kerberos ist das primäre Authentifizierungsprotokoll; **NTLM** ist ein älteres, weniger sicheres Protokoll, das nicht mehr verwendet werden sollte.
*   **Management Tools:**
    *   **Active Directory Administrative Center** ist ein grafisches Tool für die Verwaltung von AD-Objekten.
    *   Die **Active Directory MMC (Microsoft Management Console)** bietet Snap-Ins zur Verwaltung.
    *   **Active Directory-Benutzer und -Computer (ADUC)** ist ein grundlegendes Werkzeug für die tägliche Verwaltung.
    *   Das **PowerShell-Modul** für Active Directory ermöglicht automatisierte Verwaltungsaufgaben über Cmdlets.
*   **Gruppenrichtlinien (GPOs):**
    *   GPOs ermöglichen die zentrale Verwaltung und Durchsetzung von Einstellungen und Konfigurationen für Benutzer und Computer in einer AD-Umgebung.
    *   Sie können für Sicherheitseinstellungen, Desktop-Einstellungen, Softwareinstallationen und Skripte verwendet werden.
    *   Anwendungsebenen: Standort, Domäne, OU, Site.
    *   **Verarbeitungsreihenfolge:** Lokale Gruppenrichtlinien, Standortrichtlinien, Domänenrichtlinien, OU-Richtlinien.
    *   **Administrative Templates** sind Vorlagen für GPOs.
    *   Berechtigte Personen sind Domain-Administratoren oder Benutzer mit entsprechenden Berechtigungen.
*   **Active Directory PowerShell Cmdlets:** Zum Beispiel `New-ADUser` (Benutzer erstellen), `Get-ADOrganizationalUnit` (OU abrufen), `Remove-ADGroupMember` (Benutzer aus Gruppe entfernen), `Remove-ADGroup` (Gruppe löschen), `Reset-ComputerMachinePassword` (Computerpasswort wiederherstellen).

---

### **Unit 5: Grundlagen Windows Server DNS**

*   **Lernziele:** Techniker HF können DNS-Grundlagen, Funktionsweise und DNS-Zonen beschreiben, DNS-Server installieren/konfigurieren, DNS-Records verwalten, DNS-Forwarding einrichten, iterative/rekursive Anfragen verstehen und Debugging-Tools verwenden.
*   **Aufgabe von DNS (Domain Name System):** Die Hauptaufgabe ist die Übersetzung von menschenlesbaren Domainnamen in maschinenlesbare IP-Adressen und umgekehrt. DNS dient als verteilte Datenbank, die das Internet durchsucht, um die IP-Adresse eines Hosts zu ermitteln.
*   **DNS Zonen:**
    *   **Forward Lookup Zone:** Ordnet Domainnamen IP-Adressen zu.
    *   **Reverse Lookup Zone:** Ordnet IP-Adressen Domainnamen zu.
    *   **Primary Zone:** Die Master-Kopie der Zone, die direkt bearbeitet werden kann.
    *   **Secondary Zone:** Eine schreibgeschützte Kopie der Primary Zone zur Redundanz und Lastverteilung.
    *   **Stub Zone:** Enthält nur die Nameserver- und SOA-Einträge einer Domäne, um Namensauflösung effizienter zu gestalten.
*   **DNS Records:**
    *   **Start of Authority (SOA):** Enthält administrative Informationen über die Zone (z.B. primärer Nameserver, Kontaktperson, Seriennummer, Timings).
    *   Ein **DNS Record** ist ein Eintrag in einer DNS-Zone, der spezifische Informationen enthält.
    *   **Typen:** A (Host), AAAA (IPv6 Host), CNAME (Alias), MX (Mail Exchange), PTR (Pointer für Reverse Lookup), SRV (Service Location).
    *   **TTL (Time To Live):** Gibt an, wie lange ein DNS-Resolver einen Eintrag zwischenspeichern darf.
*   **DNS Query:**
    *   **Iterative DNS Query:** Der Resolver fragt den Nameserver, der dann auf einen anderen Nameserver verweist, bis die endgültige Antwort gefunden ist.
    *   **Rekursive DNS Query:** Der Resolver fragt einen Nameserver, der die gesamte Auflösungskette bis zur endgültigen Antwort selbst durchführt.
*   **DNS Management:** Aktivierung des Loggings auf einem DNS Server.
    *   **Aging:** Der Prozess, bei dem DNS-Einträge, die seit einer bestimmten Zeit nicht aktualisiert wurden, identifiziert und markiert werden.
    *   **Scavenging:** Der Prozess, bei dem als "gealtert" markierte DNS-Einträge entfernt werden, um die DNS-Datenbank sauber zu halten.
    *   Sicherung von DNS-Servern ist wichtig.
*   **DNS Debugging:** Befehle wie `nslookup` können verwendet werden, um DNS-Abfragen zu überprüfen und die Funktionalität eines DNS-Servers zu verifizieren.
*   **DNS Zonen Replication:**
    *   Eine **Active Directory Integrierte DNS Zone** speichert die DNS-Zonendaten in Active Directory, wodurch die Replikation über die AD-Replikation erfolgt.
    *   Ein **authoritativer DNS Server** ist für eine bestimmte Zone zuständig und liefert definitive Informationen.
*   **DNS Forwarding:**
    *   **DNS Forwarding** leitet DNS-Anfragen an externe DNS-Server weiter, wenn der lokale Server die Anfrage nicht selbst auflösen kann.
    *   **Root Server** sind die Top-Level-DNS-Server. DNS Forwarding kann die direkte Anfrage an Root-Server umgehen.
    *   **Split DNS** wird verwendet, um internen und externen Clients unterschiedliche DNS-Antworten für dieselbe Domain zu geben.

---

### **Unit 6: Grundlagen Windows Server DHCP**

*   **Lernziele:** Techniker HF beherrschen die Grundlagen von IP-Netzwerken (öffentliche/private IP-Adressen, Subnetze, Broadcasts), können DHCP verstehen/erklären, DHCP-Server installieren/konfigurieren (Scopes, Optionen) und Hochverfügbarkeitsoptionen (DHCP-Failover) erläutern.
*   **DHCP (Dynamic Host Configuration Protocol):** Ein Netzwerkprotokoll, das IP-Adressen und andere Netzwerkkonfigurationen automatisch an Geräte in einem Netzwerk verteilt.
    *   Ein **DHCP-Server** verteilt IP-Adressen und Netzwerkkonfigurationen.
    *   Ein **DHCP-Client** fordert IP-Adressen an und empfängt sie.
    *   **Vorteil:** Automatische und dynamische Zuweisung von IP-Adressen, reduziert manuellen Aufwand.
    *   Eine **DHCP-Lease** ist die zeitlich begrenzte Zuweisung einer IP-Adresse durch den DHCP-Server an einen Client.
*   **IP-Adressen:**
    *   Eine **private IP-Adresse** wird innerhalb eines privaten Netzwerks verwendet und ist nicht direkt über das Internet erreichbar. Man unterscheidet die Klassen A, B und C.
    *   Eine **öffentliche IP-Adresse** ist direkt über das Internet erreichbar.
    *   Eine **reservierte IP-Adresse** ist einem bestimmten Gerät dauerhaft zugewiesen.
*   **DHCP Relay vs. IP Helper:**
    *   Ein **DHCP-Relay** ist ein Netzwerkgerät oder eine Software, die DHCP-Nachrichten zwischen Clients und Servern über verschiedene Netzwerksegmente hinweg weiterleitet, wenn diese in unterschiedlichen Subnetzen sind.
    *   Ein **IP-Helper** ist ähnlich, kann aber auch andere netzwerkrelevante Informationen (z.B. Bootp-Anfragen, DNS-Abfragen) weiterleiten.
*   **DHCP Optionen:** Zusätzliche Konfigurationseinstellungen, die ein DHCP-Server an Clients verteilen kann (z.B. Standard-Gateway, DNS-Server, Domainname).
    *   Optionen können auf globaler Ebene, bereichsbasiert (für bestimmte IP-Bereiche) oder reservierungsbasiert (für einzelne Clients) gesetzt werden.
    *   Der **Default Gateway** wird üblicherweise mit DHCP-Option 3 gesetzt.
    *   Die **DNS-Server** werden üblicherweise mit DHCP-Option 6 gesetzt.
*   **DHCP Authorization:** Stellt sicher, dass nur autorisierte DHCP-Server in einem Active Directory-Domänenumfeld IP-Adressen verteilen dürfen. Dies verhindert Netzwerkfehler und Sicherheitsprobleme durch nicht autorisierte Server. Der PowerShell-Befehl `Add-DhcpServerInDC` autorisiert einen DHCP-Server.
*   **DHCP Hochverfügbarkeit:** Methoden zur Erreichung von Hochverfügbarkeit in DHCP sind:
    *   **DHCP-Clustering:** Einrichten eines Clusters von DHCP-Servern.
    *   **DNS Round-Robin:** Konfiguration mehrerer DHCP-Server und Weiterleitung von Anfragen durch DNS.
    *   **Virtuelle IP-Adressen:** Verwendung von Lastausgleichstechniken.
    *   **DHCP-Server-Redundanz:** Mehrere DHCP-Server unterstützen sich gegenseitig.
    *   **DHCP-Failover:** Zwei DHCP-Server synchronisieren ihre Konfiguration und IP-Adress-Pools für eine nahtlose Übernahme im Falle eines Ausfalls.
*   **Netzwerkberechnungen:**
    *   Eine **IP-Adresse** ist eine numerische Kennung für ein Gerät in einem Netzwerk.
    *   **Subnetting** ist der Prozess der Aufteilung eines größeren IP-Adressbereichs in kleinere Subnetze, um die Effizienz der Netzwerkressourcennutzung zu verbessern, die Verwaltung zu vereinfachen und die Leistung zu optimieren.
    *   Ein Subnetz wird anhand der benötigten Hosts, Netzwerkgröße und Sicherheitsanforderungen erstellt.
    *   Tools wie IP Calculator und Subnet Calculator können verwendet werden.

---

### **Unit 7: Grundlagen Azure**

*   **Lernziele:** Techniker HF verstehen die Rollen von Cloud-Anbietern und -Nutzern im Shared Responsibility Model, können Vor- und Nachteile von Cloud-Diensten identifizieren, verschiedene Cloud-Service-Kategorien (SaaS, PaaS, IaaS) erläutern, Microsoft Azure beschreiben und Ressourcen in der Azure Cloud erstellen.
*   **Cloud Computing:**
    *   Die **Cloud** bezieht sich auf die Bereitstellung von Computing-Ressourcen (Rechenleistung, Speicher, Datenbanken, Netzwerke, Anwendungen) über das Internet durch Cloud-Anbieter, ohne eigene physische Infrastruktur.
    *   Andere Cloud-Lösungen sind AWS, Google Cloud Platform (GCP) und Alibaba Cloud.
    *   **Vorteile:** Skalierbarkeit, Kosteneffizienz (Pay-as-you-go), Flexibilität, Zugänglichkeit, Automatisierung und vereinfachte Verwaltung.
    *   **Nachteile:** Sicherheits- und Datenschutzbedenken, Abhängigkeit von Internetverbindung und Anbieterverfügbarkeit, mögliche Compliance- und Regulierungsprobleme, potenzielle Einschränkungen bei Anpassung und Kontrolle.
*   **Cloud vs. On-Premise:**
    *   **Generell:** Cloud-Ressourcen werden von externen Anbietern über das Internet bereitgestellt, On-Premise-Ressourcen werden lokal in der Organisation bereitgestellt und verwaltet.
    *   **Kosten:** Cloud nutzt ein Pay-as-you-go-Modell; On-Premise erfordert Kapitalkosten für Hardware/Software und laufende Betriebskosten.
    *   **Sicherheit:** In der Cloud wird die Sicherheitsverantwortung zwischen Anbieter und Kunde geteilt (Shared Responsibility Model); On-Premise hat die Organisation die volle Kontrolle und Verantwortung.
    *   **Verfügbarkeit:** Cloud-Anbieter bieten hohe Verfügbarkeit durch SLAs und Redundanz; On-Premise hängt von der internen Infrastruktur und Wartung ab.
*   **Cloud Service Types:**
    *   **SaaS (Software as a Service):** Anwendungen werden über das Internet bereitgestellt und gehostet; Benutzer greifen über einen Webbrowser oder eine API darauf zu, ohne die zugrunde liegende Infrastruktur zu verwalten (z.B. Microsoft Office 365).
    *   **PaaS (Platform as a Service):** Bietet eine Plattform für Entwicklung, Bereitstellung und Verwaltung von Anwendungen; Entwickler kümmern sich nicht um die Infrastruktur (z.B. Microsoft Azure App Service).
    *   **IaaS (Infrastructure as a Service):** Stellt virtuelle Computing-Ressourcen wie Rechenleistung, Speicher und Netzwerke über das Internet bereit; Benutzer mieten und nutzen diese Ressourcen (z.B. Azure Virtual Machines).
*   **Cloud Models:**
    *   **Public Cloud:** Ressourcen werden von einem Cloud-Anbieter über das Internet bereitgestellt und von mehreren Kunden gemeinsam genutzt (z.B. Azure).
    *   **Private Cloud:** Cloud-Ressourcen werden innerhalb eines Unternehmens bereitgestellt und verwaltet; die Nutzung ist auf eine einzelne Organisation beschränkt.
    *   **Hybrid Cloud:** Kombiniert Elemente der Public und Private Cloud und ermöglicht die nahtlose Integration und den Datenaustausch.
    *   **Multi-Cloud:** Bezieht sich auf die Nutzung mehrerer Cloud-Plattformen und -Anbieter für Anwendungen und Workloads zur Redundanz, Ausfallsicherheit, Kostenoptimierung und Flexibilität.
*   **Scalability:**
    *   **Vertikales Scaling (Skalierung nach oben):** Erhöhung der Leistung einer einzelnen Maschine durch Hinzufügen von Ressourcen (CPU, RAM, Festplattenspeicher).
    *   **Horizontales Scaling (Skalierung nach aussen):** Erweiterung der Leistungsfähigkeit des Systems durch Hinzufügen von weiteren Instanzen oder Knoten (Servercluster).
*   **High Availability:**
    *   Ein **SLA (Service Level Agreement)** ist ein Vertrag, der Leistung und Erwartungen zwischen Dienstleister und Kunde festlegt.
    *   **Uptime** bezieht sich auf die Zeitdauer, in der ein System oder eine Dienstleistung ordnungsgemäss funktioniert und verfügbar ist. Die Downtime bei verschiedenen Uptime-Prozentsätzen kann berechnet werden (z.B. 99.99% Uptime bedeutet 0.876 Stunden Downtime pro Jahr).
*   **Azure Infrastructure:**
    *   Eine **Azure Region** ist ein geografisches Gebiet, das aus einem oder mehreren Azure-Rechenzentren besteht, die geografisch nahe beieinander liegen und über ein dediziertes, hochverfügbares Netzwerk verbunden sind. Nicht jede Azure-Ressource ist in jeder Region verfügbar.
    *   **Availability Zones** sind physisch getrennte Rechenzentren innerhalb einer Azure-Region, die eine hohe Verfügbarkeit und Redundanz bieten.
*   **Azure Resource Management:**
    *   **Azure Management Groups:** Container zur Organisation und Verwaltung von Azure-Abonnements in einer hierarchischen Struktur.
    *   **Azure Subscriptions:** Abonnements, die Benutzern die Nutzung von Azure-Diensten und -Ressourcen ermöglichen und mit Abrechnungsinformationen verbunden sind.
    *   **Azure Resource Groups:** Logische Container zur Organisation und Verwaltung von Azure-Ressourcen, die dieselben Lebenszyklusrichtlinien, Berechtigungen und Tags teilen.
    *   **Azure-Ressourcen** sind Dienste oder Elemente, die in Microsoft Azure bereitgestellt werden (z.B. virtuelle Maschinen, Datenbanken).

---

### **Unit 8: Grundlagen Microsoft Entra ID**

*   **Lernziele:** Absolventen können Entra ID (Azure Active Directory) verstehen, Benutzer-, Computer- und Gruppenobjekte erstellen, die Unterschiede zu Active Directory kennen, einen "Custom Domain Name" erstellen und dessen Funktionen erklären.
*   **Was ist Microsoft Entra ID?** (früher Azure Active Directory) ist ein Identitäts- und Zugriffsverwaltungsdienst von Microsoft in der Cloud, der eine zentrale Benutzerverwaltung und Authentifizierung für Cloud-basierte Anwendungen ermöglicht.
*   **Unterschiede zwischen Entra ID und Active Directory (On-Premise):**
    *   **Bereitstellungsart:** Microsoft Entra ID ist eine **Cloud-basierte Lösung**, während das traditionelle Active Directory **lokal vor Ort** bereitgestellt wird.
    *   **Funktionalität:** Microsoft Entra ID bietet spezielle Funktionen und Integrationen für Cloud-basierte Anwendungen und Dienste; das traditionelle Active Directory wird hauptsächlich für lokale Authentifizierung und Verwaltung von Windows-Domänenumgebungen verwendet.
*   **Lizenzierungstypen Entra ID:**
    *   **Entra ID Free:** Bietet grundlegende Identitäts- und Zugriffsverwaltungsfunktionen.
    *   **Entra ID Premium P1:** Enthält erweiterte Funktionen und zusätzliche Sicherheitsfunktionen.
    *   **Entra ID Premium P2:** Bietet alle Funktionen von P1 sowie erweiterte Sicherheits- und Compliance-Funktionen wie Identity Protection und Privileged Identity Management.
*   **Benutzer und Gruppen:** Die Erstellung und Verwaltung von Benutzern und Gruppen ist eine Kernfunktion in Entra ID.
*   **Custom Domain Name:** Es ist möglich, einen benutzerdefinierten Domainnamen zu Entra ID hinzuzufügen, um die Markenidentität zu wahren und die Benutzerfreundlichkeit zu verbessern.
