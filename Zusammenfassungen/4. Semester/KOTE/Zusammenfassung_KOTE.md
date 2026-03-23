# Detaillierte Zusammenfassung: Kommunikationstechnik (KOTE) - Networking Part 1

Basierend auf den Schulungsunterlagen (V1.0) von Mathias Gut.

> **⚠️ PRÜFUNGS-FOKUS (Tipps des Dozenten)**
> Diese Themen wurden explizit als prüfungsrelevant genannt:
> 1.  **Begriffe erklären:** Offene Fragen & Multiple Choice (siehe Kap. 1 & 2).
> 2.  **3-Way-Handshake:** Den Prozess im Detail kennen (siehe Kap. 5).
> 3.  **Subnetting:** Ein gegebenes Netz unterteilen können (siehe Beispiel in Kap. 4).
> 4.  **LAN-Design:** Technologien für Redundanz (STP, EtherChannel) und Segmentierung (VLANs) unterscheiden.
> 5.  **CLI-Konfiguration:** VLANs anlegen, Ports zuweisen und **Router-on-a-Stick (RoaS)** konfigurieren.

---

## 1. Einführung & Netzwerk-Grundlagen

### Einbettung in die IT-Strategie
Netzwerkmanagement ist Teil der IT-Strategie und ordnet sich in das Business Model ein:
*   **Business:** Ziele, Prozesse.
*   **IT:** Strategie -> Servicemanagement -> Anwendungen -> Systeme -> Datenmanagement -> **Telekommunikation**.

### Elementare Netzwerkelemente & Begriffe
*   **Nachricht:** Die eigentliche Information (Payload).
*   **Medium:** Physikalischer Übertragungsweg (Kupfer, LWL, Luft).
*   **Gerät:**
    *   *Endgeräte (Hosts):* PC, Server, IoT.
    *   *Netzwerkgeräte (Nodes):* Router, Switches, Firewalls.
*   **Regel (Protokoll):** Syntax, Semantik und Timing der Kommunikation (z. B. TCP/IP).

### Kommunikationstypen (Casting)
*   **Unicast:** 1 zu 1 (Punkt-zu-Punkt).
*   **Multicast:** 1 zu Gruppe (z. B. IPTV, Routing-Updates).
*   **Broadcast:** 1 zu Alle (im lokalen Netz, z. B. ARP, DHCP).
*   **Anycast:** 1 zu "Nächstgelegenem" einer Gruppe (Lastverteilung, DNS Root Server).

### Übertragungsarten (Richtung)
*   **Simplex:** Einseitig (z. B. Radio, Maussignal zum PC).
*   **Halbduplex (Half-Duplex):** Wechselseitig, nicht gleichzeitig (z. B. Funkgerät, alte Hub-Netzwerke, WLAN).
*   **Vollduplex (Full-Duplex):** Gleichzeitig Senden und Empfangen (heutige Switched Networks, Telefonie).

### Netzwerkausdehnung (Topologien)
*   **PAN:** Personal Area Network (Bluetooth, NFC).
*   **LAN:** Local Area Network (Ethernet, WLAN).
*   **MAN:** Metropolitan Area Network (Stadtnetze).
*   **WAN:** Wide Area Network (Internet, Standortvernetzung).
*   **GAN:** Global Area Network.

### Physikalische vs. Logische Topologie
*   **Physikalisch:** Die Verkabelung (Stern, Bus, Ring, Mesh).
*   **Logisch:** Der Datenfluss (z. B. Token Ring ist physikalisch ein Stern, logisch ein Ring).

---

## 2. Referenzmodelle: OSI & TCP/IP

### Das ISO/OSI-Schichtenmodell (7 Layer)
Jede Schicht bietet Dienste für die darüberliegende Schicht an.

| Schicht | Name (DE/EN) | PDU (Protocol Data Unit) | Funktion | Hardware/Protokolle |
| :--- | :--- | :--- | :--- | :--- |
| **7** | **Anwendung** (Application) | Daten | Netzzugang für Anwendungen | HTTP, FTP, SMTP, DNS |
| **6** | **Darstellung** (Presentation) | Daten | Formatierung, Verschlüsselung, Kompression | ASCII, JPEG, SSL/TLS |
| **5** | **Sitzung** (Session) | Daten | Dialogkontrolle, logische Verbindungen | RPC, SQL, NetBIOS |
| **4** | **Transport** (Transport) | Segment | Ende-zu-Ende Verbindung, Fehlerkorrektur, Flow Control | TCP, UDP, Ports |
| **3** | **Vermittlung** (Network) | Paket | Logische Adressierung, Routing (Wegwahl) | IP, ICMP, Router, L3-Switch |
| **2** | **Sicherung** (Data Link) | Frame | Phys. Adressierung (MAC), Medienzugriff | Ethernet, ARP, Switch, Bridge |
| **1** | **Bitübertragung** (Physical) | Bit | Übertragung von Rohbits über Medium | Kabel, Hub, Repeater |

**Kapselung (Encapsulation):**
Beim Senden fügt jede Schicht ihren **Header** hinzu (L4 Header + L3 Header + L2 Header + Daten + L2 Trailer).
Beim Empfangen ("Entkapselung") werden diese Schicht für Schicht entfernt.

### TCP/IP-Modell (DoD-Modell)
Reduziert auf 4 Schichten, praxisorientierter:
1.  **Anwendung:** (OSI 5-7) - HTTP, Telnet, FTP.
2.  **Transport:** (OSI 4) - TCP, UDP.
3.  **Internet:** (OSI 3) - IP, ICMP, IGMP.
4.  **Netzzugang:** (OSI 1-2) - Ethernet, Token Ring, Frame Relay.

---

## 3. Layer 1 & 2: Ethernet & Medien

### Übertragungsmedien
*   **Twisted Pair (Kupfer):**
    *   Aufbau: 4 Adernpaare, verdrillt zum Schutz vor EMI (Elektromagnetischer Interferenz).
    *   Typen: **UTP** (Unshielded), **STP** (Shielded).
    *   Stecker: RJ45.
    *   Kabel: Straight-Through (PC zu Switch) vs. Crossover (Switch zu Switch / PC zu PC - dank Auto-MDIX heute oft egal).
*   **Lichtwellenleiter (LWL / Fiber):**
    *   **Multimode:** Dickerer Kern, LED-Licht, kürzere Distanzen (z. B. im Gebäude), günstiger.
    *   **Singlemode:** Sehr dünner Kern (9µm), Laser-Licht, enorme Distanzen (WAN), teurer.
    *   Stecker: LC, SC, ST.
*   **WLAN (IEEE 802.11):** Geteiltes Medium (Shared Medium), Halbduplex.

### Ethernet (IEEE 802.3)
*   **CSMA/CD:** Carrier Sense Multiple Access / Collision Detection. (Bei Hubs/Halbduplex: Hören, ob frei ist -> Senden -> Bei Kollision Jam-Signal senden und warten).
*   **MAC-Adresse:** 48 Bit (6 Byte), hexadezimal (z. B. `00:0b:a9:6a:7d:d8`).
    *   Erste 24 Bit: **OUI** (Organizationally Unique Identifier) - Herstellerkennung.
    *   Letzte 24 Bit: Fortlaufende Nummer des Herstellers (NIC Specific).
    *   Besondere MAC: `ff:ff:ff:ff:ff:ff` = Broadcast.

### Ethernet Frame Aufbau
Ein Ethernet-Frame transportiert das IP-Paket.
*   **Präambel (7 Byte) + SFD (1 Byte):** Synchronisation (101010...11).
*   **Destination MAC (6 Byte):** Zieladresse.
*   **Source MAC (6 Byte):** Quelladresse.
*   **VLAN Tag (optional 4 Byte):** 802.1Q Tag (TPID, TCI).
*   **Type/Length (2 Byte):** Gibt das L3-Protokoll an (z. B. 0x0800 für IPv4, 0x0806 für ARP).
*   **Payload (Data):** 46 - 1500 Byte (MTU - Maximum Transmission Unit).
*   **FCS (Frame Check Sequence):** CRC-Prüfsumme zur Fehlererkennung am Ende.

---

## 4. Layer 3: IP & Routing

### IPv4 Header (Wichtige Felder)
*   **Version:** 4 (für IPv4).
*   **IHL (Internet Header Length):** Länge des Headers.
*   **TOS (Type of Service):** Priorisierung (QoS).
*   **Total Length:** Gesamtlänge des Pakets.
*   **TTL (Time To Live):** Lebensdauer (Hops). Wird von jedem Router um 1 dekrementiert. Bei 0 wird das Paket verworfen (Schutz vor Loops).
*   **Protocol:** Welches L4 Protokoll folgt? (6=TCP, 17=UDP, 1=ICMP).
*   **Source IP & Destination IP:** 32-Bit Adressen.

### IP-Adressierung
*   **Aufbau:** 32 Bit, 4 Oktette (z. B. 192.168.1.1).
*   **Netzklassen (Classful Routing - veraltet, aber Grundlagen):**
    *   **Class A:** `0.0.0.0` - `127.255.255.255` (Subnet /8). Erstes Bit 0.
    *   **Class B:** `128.0.0.0` - `191.255.255.255` (Subnet /16). Erste Bits 10.
    *   **Class C:** `192.0.0.0` - `223.255.255.255` (Subnet /24). Erste Bits 110.
*   **Private Adressen (RFC 1918):** Nicht im Internet routbar.
    *   `10.0.0.0/8`
    *   `172.16.0.0/12`
    *   `192.168.0.0/16`
*   **APIPA (Link-Local):** `169.254.x.x` (wenn kein DHCP verfügbar).

### Subnetting & CIDR (WICHTIG!)
*   **Subnetzmaske:** Trennt IP in Netzanteil (Einsen) und Hostanteil (Nullen).
*   **CIDR (Classless Inter-Domain Routing):** Suffix-Notation (z. B. /24).
*   **Berechnung:** Anzahl Hosts = 2^(Hostbits) - 2.

#### 🧮 Beispiel-Rechnung: Unterteilung eines Subnetzes
Gegeben: Netz `192.168.1.0/24`.
Aufgabe: Erstelle 4 Subnetze.

1.  **Benötigte Bits:** Um 4 Subnetze zu erhalten, brauchen wir 2 Bits (2² = 4).
2.  **Neue Maske:** Alte Maske (/24) + 2 Bits = **/26**.
    *   Binär: `11111111.11111111.11111111.11000000`
    *   Dezimal: `255.255.255.192` (Das letzte Oktett: 128 + 64 = 192)
3.  **Schrittweite (Magic Number):** 256 - 192 = **64**.
4.  **Die Subnetze:**
    *   **Netz 1:** `192.168.1.0` bis `.63` (Netz: .0, Broadcast: .63, Hosts: .1 - .62)
    *   **Netz 2:** `192.168.1.64` bis `.127` (Netz: .64, Broadcast: .127, Hosts: .65 - .126)
    *   **Netz 3:** `192.168.1.128` bis `.191` (Netz: .128, Broadcast: .191, Hosts: .129 - .190)
    *   **Netz 4:** `192.168.1.192` bis `.255` (Netz: .192, Broadcast: .255, Hosts: .193 - .254)

### ARP (Address Resolution Protocol)
*   Verbindet L3 (IP) mit L2 (MAC).
*   **ARP Request:** "Wer hat IP x.x.x.x?" (Broadcast: `ff:ff:ff:ff:ff:ff`).
*   **ARP Reply:** "Ich (MAC y:y:y) habe IP x.x.x.x" (Unicast).
*   `arp -a`: Zeigt ARP-Cache (Tabelle) am Client an.

### ICMP (Internet Control Message Protocol)
*   Dient Diagnose und Fehlermeldung.
*   Wichtige Typen:
    *   **Echo Request (8) / Echo Reply (0):** Ping.
    *   **Destination Unreachable (3):** Ziel nicht erreichbar.
    *   **Time Exceeded (11):** TTL abgelaufen (nutzt Traceroute).

---

## 5. Layer 4: Transport (TCP vs. UDP)

### Ports
Adressieren die Anwendung auf dem Host (Multiplexing).
*   **Well Known Ports (0-1023):** Systemdienste (80=HTTP, 443=HTTPS, 22=SSH, 53=DNS).
*   **Registered Ports (1024-49151).**
*   **Dynamic/Private Ports (49152-65535).**

### TCP (Transmission Control Protocol)
*   **Eigenschaften:** Verbindungsorientiert, zuverlässig, geordnete Reihenfolge, Flusskontrolle.
*   **Header Flags:**
    *   **SYN:** Synchronize (Verbindungsaufbau).
    *   **ACK:** Acknowledgment (Bestätigung).
    *   **FIN:** Finish (Verbindungsabbau).
    *   **RST:** Reset (Abbruch).
*   **3-Way-Handshake (Verbindungsaufbau) - WICHTIG!:**
    1.  Client -> Server: **SYN** (Ich will verbinden, Sequenz=X)
    2.  Server -> Client: **SYN, ACK** (OK, ich auch. Sequenz=Y, Acknowledge=X+1)
    3.  Client -> Server: **ACK** (Verbindung steht. Acknowledge=Y+1)
*   **Flow Control:** "Window Size" teilt dem Sender mit, wie viele Daten der Empfänger gerade puffern kann.

### UDP (User Datagram Protocol)
*   **Eigenschaften:** Verbindungslos, unzuverlässig (kein ACK), schnell, geringer Overhead (8 Byte Header).
*   **Einsatz:** Streaming, VoIP, DNS-Abfragen, DHCP.

---

## 6. Anwendungsschicht & Dienste

*   **DNS (Domain Name System):** UDP/53.
    *   Hierarchischer Namensraum (Root `.` -> Top Level Domain `.ch` -> Second Level `google` -> Host `www`).
    *   **Record Types:**
        *   **A:** IPv4 Adresse.
        *   **AAAA:** IPv6 Adresse.
        *   **CNAME:** Alias (Verweis auf anderen Namen).
        *   **MX:** Mail Exchange (Mailserver).
        *   **NS:** Nameserver.
        *   **PTR:** Pointer (Reverse Lookup: IP -> Name).
*   **DHCP (Dynamic Host Configuration Protocol):** UDP 67/68.
    *   Prozess: DORA (Discover, Offer, Request, Acknowledge).
    *   Verteilt: IP, Subnetzmaske, Gateway, DNS-Server.

---

## 7. Switching & VLANs (Technologien)

### Segmentierung vs. Redundanz
*   **Segmentierung (Trennung):**
    *   **VLAN (Virtual LAN):** Unterteilt ein physikalisches Netz in mehrere logische Netze. Reduziert die Broadcast-Domäne und erhöht die Sicherheit.
    *   **Tagging (802.1Q):** Markiert Frames auf Trunk-Leitungen mit einer VLAN-ID.
*   **Redundanz (Ausfallsicherheit):**
    *   **STP (Spanning Tree Protocol):** Verhindert Schleifen (Loops) in Ethernet-Netzwerken, wenn redundante Kabel gezogen werden. Blockiert automatisch redundante Pfade.
    *   **EtherChannel (Link Aggregation):** Fasst mehrere Kabel logisch zu einem zusammen (höhere Bandbreite + Redundanz).

### Router-on-a-Stick (RoaS)
Um zwischen verschiedenen VLANs zu kommunizieren, wird ein Router benötigt.
*   Der Switch-Port zum Router ist ein **Trunk**.
*   Der Router nutzt **Sub-Interfaces** (z. B. `g0/0.10`), die jeweils ein VLAN taggen.

---

## 8. CLI & Troubleshooting (Cisco IOS)

### Wichtige CLI-Befehle (Konfiguration & Prüfung)

#### VLANs und Ports am Switch
```cisco
Switch(config)# vlan 10                     ! VLAN erstellen
Switch(config-vlan)# name Sales             ! Name vergeben
Switch(config-vlan)# exit

Switch(config)# interface range fa0/1 - 10  ! Ports auswählen
Switch(config-if-range)# switchport mode access        ! Als Endgeräte-Port
Switch(config-if-range)# switchport access vlan 10     ! VLAN zuweisen

Switch(config)# interface gi0/1             ! Uplink-Port zum Router/Switch
Switch(config-if)# switchport mode trunk    ! Als Trunk konfigurieren
```

#### Router-on-a-Stick (RoaS) am Router
**Wichtig für die Prüfung:** Inter-VLAN-Routing konfigurieren.
```cisco
Router(config)# interface gi0/0             ! Physisches Interface
Router(config-if)# no shutdown              ! Aktivieren (wichtig!)
Router(config-if)# exit

Router(config)# interface gi0/0.10          ! Subinterface für VLAN 10 erstellen
Router(config-subif)# encapsulation dot1q 10 ! 802.1Q Tagging für VLAN 10 aktivieren
Router(config-subif)# ip address 192.168.10.1 255.255.255.0 ! Gateway-IP setzen

Router(config)# interface gi0/0.20          ! Subinterface für VLAN 20
Router(config-subif)# encapsulation dot1q 20
Router(config-subif)# ip address 192.168.20.1 255.255.255.0
```

#### Diagnose-Befehle
| Befehl | Funktion |
| :--- | :--- |
| `show running-config` | Zeigt aktuelle Konfiguration (RAM). |
| `copy run start` | Speichert Konfiguration (NVRAM). |
| `show ip interface brief` | Schneller Überblick über Interfaces und IPs (Layer 1/2/3 Status). |
| `show ip route` | Zeigt Routing-Tabelle (L3). |
| `show vlan brief` | Zeigt VLANs und zugewiesene Ports. |
| `show interfaces trunk` | Zeigt Trunk-Ports und erlaubte VLANs. |
| `ping <ip>` | Testet Verbindung (L3). |

### Wireshark Filter
*   `ip.addr == 192.168.1.5`: Nur Pakete dieser IP.
*   `tcp.port == 80`: Nur HTTP Traffic.
*   `http`: Nur HTTP Protokoll.
*   `!arp`: Alles außer ARP.
*   **Follow TCP Stream:** Zeigt den kompletten Datenaustausch einer Session.
