### Spickzettel: Fachprüfung Kommunikationstechnik

#### 1\. Schichtenmodelle & Datenfluss (OSI vs. TCP/IP)

Drei Modelle im Fokus: OSI (Referenz), TCP/IP (Standard), RFC 1122 (Host-Anforderung).

##### Vergleich der Schichtenmodelle

| OSI (Schichten) | TCP/IP Common (5) | TCO/IP RFC 1122 (4) | PDU-Bezeichnung                  | Adressierung  |
| --------------- | ----------------- | ------------------- | -------------------------------- | ------------- |
| 7. Application  | 5. Application    | 4. Application      | Daten                            | Port / Socket |
| 6. Presentation | 5. Application    | 4. Application      | Daten                            | Port / Socket |
| 5. Session      | 5. Application    | 4. Application      | Daten                            | Port / Socket |
| 4. Transport    | 4. Transport      | 3. Transport        | Segmente (TCP) / Datagramme (UDP | Port / Socket |
| 3. Network      | 3. Network        | 2. Internet         | Pakete (IP-Datagramme)           | IP-Adresse    |
| 2. Data Link    | 2. Data Link      | 1. Link             | Rahmen (Frames)                  | MAC-Adresse   |
| 1. Physical     | 1. Physical       | 1. Link             | Bits (Signale)                   | Keine         |

* **Merksatz für OSI (L7 bis L1):**  **A**lle **P**riester **s**aufen **T**equila **n**ach **d**er **P**redigt.  
* **Kapselung (Encapsulation):** Sender fügt Schicht für Schicht Header (und L2-Trailer) hinzu. Das Paket wächst nach unten.  
* **Fragmentierung (De-encapsulation):** Empfänger analysiert und entfernt Header von unten nach oben.  
  * *Hinweis:*  Der Begriff "Fragmentierung" wird hier gemäss Modul-Präsentation für das Parsing/Entpacken genutzt (nicht zu verwechseln mit IP-Fragmentierung bei MTU-Überschreitung).  

(Quelle: Block 2, Folie 10-24)

#### 2\. Grundlagen der technischen Kommunikation

**Begriffe:**

- **QoS (Quality of Service):** Dienstgüte, definiert durch Parameter wie Übertragungsrate, Latenz (Verzögerung), Varianz (Jitter) und Paketverlustrate. Sie dient der Priorisierung wichtiger zeitkritischer Anwendungen wie VoIP-Telefonie.
- **Multiplexing:** Mehrere Signale oder Informationsströme werden zusammengefasst, um sie gleichzeitig über eine einzige physische Leitung zu übertragen.

##### Verbindungsarten

* **Simplex:** Einweg-Kommunikation (Beispiel: Radio, TV).  
* **Halbduplex:** Wechselseitig, aber nicht gleichzeitig (Beispiel: Funkgerät, Hub-Umgebungen).  
* **Vollduplex:** Gleichzeitiges Senden und Empfangen (Beispiel: Switch-Netzwerk).

##### Kommunikationsarten

* **Point-to-Point:** Verbindung zwischen exakt zwei Endpunkten (Beispiel: IP-Unicast, Telefon).  
* **Multicast:** Von einem Punkt an eine definierte Gruppe (Beispiel: Routing-Updates, Pay-TV).  
* **Broadcast:** Von einem Punkt an alle Teilnehmer im Segment (Beispiel: ARP-Request).

##### Übertragungsmodi

* **Basisband:** Gesamte Bandbreite für ein Signal (Standard im LAN/Ethernet).  
* **Breitband:** Bandbreite in Kanäle unterteilt für simultane Signale (WAN/TV-Kabel).

(Quelle: Block 1, Folie 38-54 / Block 2, Folie 44)

#### 3\. Ethernet & Physical Layer (Layer 1 & 2\)

##### Physische Medien

* **Kupfer (Twisted Pair):**  
  * **UTP:** Ungeschirmt.  **STP/S-STP:**  Geschirmt zur EMI-Reduktion.  

* **SF/STP:** Höchster Schutz durch Kombination aus Geflecht und Folie.  
* **Lichtwellenleiter (LWL):**  
  * **Multimode:** Großer Kern, Distanzen bis ca. 500m.  
  * **Monomode (Singlemode):** Dünner Kern, Reichweite bis 50km @ 1Gbit/s.


##### Zugriff & Verkabelung

* **CSMA/CD:** Medienzugriffsverfahren für Halbduplex/Hubs zur Kollisionserkennung.  
* **Straight-Through:** PC-zu-Switch.
* **Crossover:** Switch-zu-Switch oder PC-zu-PC.  
* **Auto-MDIX:** Automatische Erkennung und Korrektur der Kontaktbelegung durch den Switch.

(Quelle: Block 1, Folie 56-60)

#### 4\. LAN-Segmentierung & Redundanz (VLAN, STP, EtherChannel)

- **VLANs (Virtual Local Area Network) zur Segmentierung:** Unterteilen das physische Netzwerk in getrennte logische Einheiten (Broadcast-Domänen). VLANs erhöhen die Sicherheit und separieren z.B. VoIP vom Datennetz. Über Switch-Grenzen hinweg werden Frames mit dem Standard **IEEE 802.1Q** markiert ("Tagged"), indem ein VLAN-Tag in den Frame eingefügt wird.
  - **Access-Port:** Ein VLAN.
  - **Trunk-Port:** Mehrere VLANs via Tagging.
  - **Natives VLAN:** Ungetaggte Frames auf einem Trunk (Sicherheitsrisiko, falls Default VLAN 1)

- **Spanning-Tree Protocol (STP):** Ein Standard (IEEE 802.1d), der verwendet wird, um Redundanzen (mehrere physische Wege) zwischen Switches zu betreiben, ohne dass Endlosschleifen (Loops) im Netzwerk entstehen. Ein Switch agiert als "Rootbridge", während das Protokoll alle redundanten Pfade blockiert und nur bei Ausfall des Hauptpfads wieder freigibt.
  - *Cisco-Flavor:*  **PVST+** (Per VLAN Spanning Tree)
  - *Cisco-Flavor:* **RPVST+** (Rapid PVST+).  
- **EtherChannel / Link Aggregation:** Bündelt bis zu 8 physische Ports (z.B. über PAgP von Cisco oder nach Standard LACP) zu einem logischen "Trunk" oder "Port Channel". Das Resultat ist Load Balancing (Lastausgleich) und Ausfallsicherheit (Redundanz), ohne vom Spanning Tree als Schleife blockiert zu werden.

* **Port Security:**  
  * **Modi:** Statisch, Dynamisch, Sticky (speichert MAC in Running-Config).  
  * **Violation:** Protect (Drop), Restrict (Log), **Shutdown** (Default-Aktion, Port geht in  *err-disable* ).

(Quelle: Block 6, Folie 12-28 / Block 7, Folie 18-22)


#### 5\. IPv4-Adressierung, Subnetting & CIDR

##### Referenztabelle der Zweierpotenzen

| 2^1^ | 2^2^ | 2^3^ | 2^4^ | 2^5^ | 2^6^ | 2^7^ | 2^8^ | 2^9^ | 2^10^ | 2^11^ | 2^12^ | 2^13^ | 2^14^ | 2^15^ | 2^16^ |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 2    | 4    | 8    | 16   | 32   | 64   | 128  | 256  | 512  | 1024  | 2048  | 4096  | 81292 | 16384 | 32768 | 65536 |

##### Subnetting-Mathematik

- **Formeln:** Subnetze = 2^S^ ( S = Anzahl *geliehener* Subnetzbits); Hosts = 2^H^-2 (H = Anzahl restlichen Hostbits).
- **Interessantes Oktett:** Das erste Oktett von links, das in der Maske weder 0 noch 255 ist.  
- **Magic Number Methode:**  
  1. Maskenwert des interessanten Oktetts ermitteln.  
  2. **Magic Number = 256 - Maskenwert**  
  3. Subnetz-IDs sind Vielfache der Magic Number im interessanten Oktett.

*Beispiel 1:*
**Netzadresse:** 192.168.128.0/18
**Subnetzmaske:** 255.255.192.0 
**Interessantes Oktett:** 192
**Magic Number:** 256 - 192 = 64
**Bits (Subnetz/Host):** 
	255.255.255.255 --> 32Bits / 4 = 8 --> Subnetzbits von 255.255.192.0 = 8 + 8 + 2(Geliehene Host-Bits) --> 2^2^ = 4 Subnetze
	Host-Bits = 32 - Subnetzbits(18) = 14 --> 2^14^ = 16384 - 2 = 16382 Hosts pro Subnetz

Daraus resultieren folgende Subnetze:

| Netzadresse      | Subnetzmaske  | Hosts                                                        | Broadcast       |
| ---------------- | ------------- | ------------------------------------------------------------ | --------------- |
| 192.168.0.0/18   | 255.255.192.0 | 14 Host-Bits = 2^14^ - 2 = 16382<br />192.168.0.1 - 192.168.63.254 | 192.168.63.255  |
| 192.168.64.0/18  | 255.255.192.0 | 14 Host-Bits = 2^14^ - 2 = 16382<br />192.168.64.1 - 192.168.127.254 | 192.168.127.255 |
| 192.168.128.0/18 | 255.255.192.0 | 14 Host-Bits = 2^14^ - 2 = 16382<br />192.168.128.1 - 192.168.191.254 | 192.168.191.255 |
| 192.168.192.0/18 | 255.255.192.0 | 14 Host-Bits = 2^14^ - 2 = 16382<br />192.168.192.1 - 192.168.255.254 | 192.168.255.255 |

*Beispiel 2:*
**IP-Adresse:** 10.100.18.18
**Subnetzmaske:** 255.240.0.0
**Magic Number:** 256 - 240 = 16
**Subnetz-ID:** Vielfaches der Magic Number --> 0 16 32 48 64 80 96 112 ... --> Nun nimmt man den Wert der am nächsten (Tiefer) am Wert im interessanten Oktett kommt (IP-Adresse); I⁄n diesem Fall mit 100 ist es 96 --> IP-Adresse ist im Subnetz 10.96.0.0/12

##### CIDR & IP-Bereiche

* **CIDR (RFC 4632):** Klassenloses Routing via Präfix (/X). Vergabe durch IANA \-\> RIR (z.B. RIPE) \-\> ISP.  
* **RFC 1918 (Private Adressen):**  
  * **A:**  10.0.0.0/8  
  * **B:**  172.16.0.0 \- 172.31.255.255 (Präfix /12)  
  * **C:**  192.168.0.0/16


(Quelle: Block 4, Folie 29-58)

#### 6\. Layer 4: TCP (Transmission Control Protocol) Three-Way-Handshake

Verbindungsaufbau beim TCP-Protokoll wird als 3-Wege-Handschlag (Three-Way-Handshake) bezeichnet, um eine zuverlässige Kommunikation zu gewährleisten:

1. **SYN:** Der Sender initiiert die Verbindung und schickt ein Synchronisations-Segment (z.B. SEQ=100, CTL=SYN).
1. **SYN-ACK:** Der Empfänger bestätigt den Erhalt und synchronisiert sich mit dem Absender (SEQ=300, ACK=101, CTL=SYN, ACK).
1. **ACK:** Der Sender bestätigt den Empfang der Antwort (SEQ=101, ACK=301, CTL=ACK). Die Verbindung steht. *(Zusatzinfo: Der Verbindungsabbau "Teardown" nutzt die Flags FIN/ACK, ACK, ACK, FIN/ACK**).*

**Eigenschaften:** Verbindungsorientiert, zuverlässig (Error Recovery), Segmente.

(Quelle: Block 3, Folie 43-63)

#### 7. Layer 4: UDP (User Datagram Protocol)

Beim UDP-Protokoll gibt es **keinen Verbindungsaufbau** (keinen Handshake), da es verbindungslos arbeitet. Es wird genutzt, um Daten schnell und mit wenig Overhead zu übertragen:

1. **Senden:** Der Sender übermittelt die Daten direkt an die Ziel-IP und den Ziel-Port des Empfängers, ohne vorherige Aushandlung einer Sitzung oder Verbindung.
2. **Keine Bestätigung:** Der Paketempfang wird vom Empfänger nicht bestätigt (es gibt kein ACK). Die Übermittlung der Daten wird vom Protokoll nicht garantiert.

*Zusatzinfo: Da UDP keine Sequenznummern überwacht, setzt es die empfangenen Daten auch nicht selbstständig in die richtige Reihenfolge zusammen**. Eine eventuelle Fehlerkorrektur oder Sortierung muss zwingend von der jeweiligen Anwendung selbst übernommen werden**. Durch den geringeren Overhead eignet es sich besonders für zeitkritische Anwendungen wie VoIP oder einfache Request-Dienste wie DNS und DHCP**.*

**Eigenschaften:** Verbindungslos, schnell, keine Garantie, Datagramme.

(Quelle: Block 3, Folie 46-52)

#### 8\. Essentielle CLI-Befehle (Cisco IOS)

**Grundlegende Navigation und Speichern:**

Um ein Cisco-Gerät zu konfigurieren, musst du dich durch verschiedene CLI-Modi bewegen und deine Arbeit am Ende speichern:

````
## Wechselt vom User-Modus (>) in den Enable-Modus / Privileged-EXEC-Modus (#)
en

## Wechselt vom Enable-Modus in den globalen Konfigurationsmodus ((config)#)
conf t 

## Bringt dich genau eine Ebene zurück (z.B. vom Interface-Modus zurück in den globalen Konfigurationsmodus)
exit 

## Bringt dich aus jedem beliebigen Unter-Konfigurationsmodus direkt zurück in den Enable-Modus
end 

## Speichert die aktuelle Konfiguration (Running-Config) dauerhaft im NVRAM (Startup-Config), damit sie nach einem Neustart nicht verloren geht
wr

````

**VLAN definieren und Port-Zuweisung:**

Zuerst erstellst du das VLAN und gibst ihm optional einen Namen. Danach wählst du den Port aus, versetzt ihn zwingend in den Access-Modus und weist ihm das VLAN zu:

```
## Navigation
S1> en
S1# conf t

## VLAN erstellen und benennen
S1(config)# vlan 20
S1(config-vlan)# name Buchhaltung
S1(config-vlan)# exit

## Einzelnen Port konfigurieren und dem VLAN zuweisen
S1(config)# interface fastethernet 0/2
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 20
S1(config-if)# no sh 
S1(config-if)# end
S1# write
```

*Tipp: Wenn du mehrere Ports gleichzeitig zuweisen möchtest, kannst du*

```
S1(config)# interface range fastethernet 0/2 - 4
```

*nutzen.*

**Router on a Stick (RoaS) – Subinterfaces konfigurieren:**

Damit der Router zwischen verschiedenen VLANs routen kann, wird auf dem Router ein virtuelles Subinterface pro VLAN erstellt. Diesem Subinterface wird der 802.1Q-Tagging-Standard sowie das Default-Gateway (die IP-Adresse) des jeweiligen VLANs zugewiesen.

```
R1> en
R1# conf t

## Physisches Interface aktivieren (darf keine eigene IP haben)
R1(config)# interface gigabitethernet 0/0
R1(config-if)# no sh
R1(config-if)# exit

## Erstes Subinterface für VLAN 10 konfigurieren
R1(config)# interface gigabitethernet 0/0.10
R1(config-subif)# encapsulation dot1Q 10
R1(config-subif)# ip address 10.1.1.254 255.255.255.0
R1(config-subif)# exit

## Zweites Subinterface für VLAN 20 konfigurieren
R1(config)# interface gigabitethernet 0/0.20
R1(config-subif)# encapsulation dot1Q 20
R1(config-subif)# ip address 10.2.1.254 255.255.255.0
R1(config-subif)# end
R1# write
```

**Rückgängigmachen von Konfigurationen:**

Um eine getätigte Einstellung zu löschen oder auf den Standardwert zurückzusetzen, setzt du auf Cisco-Geräten im Regelfall einfach das Wort **no** vor den ursprünglichen Konfigurationsbefehl.

*Beispiele:*

````
R1(config-subif)# ip address 10.1.1.1 255.255.255.0 -> R1(config-subif)# no ip address 10.1.1.1 255.255.255.0
S1(config)# vlan 20 -> S1(config)# no vlan 20
````

(Quelle: Block 5, Folie 47-64 / Block 6, Folie 29-38)

#### 9\. Wireshark

- **Funktionsweise:** Wireshark ist ein Netzwerksniffer, der den Datenverkehr aufzeichnet. Um alle Pakete im Netzwerksegment (und nicht nur die an den eigenen Rechner adressierten) mitzuschneiden, muss sich die Netzwerkkarte im **"promiscuous mode"** befinden.
- **Ansicht:** Das Hauptfenster gliedert sich in drei Bereiche: 
  - **Packet List** (Paketübersicht)
  - **Packet Details** (Header-Informationen je Schicht)
  - **Packet Bytes** (die Rohdaten).
- **Wichtige Einstellungen (Preferences):**
  - Um die echten Portnummern zu sehen, sollte man die Option **"Enable transport name resolution" deaktivieren**.
  - Für Troubleshooting empfiehlt es sich, die Spalten **Cumulative Bytes** und **Delta time displayed** hinzuzufügen, da man mit Delta-Zeiten sofort sieht, wo eine Antwort zu lange gedauert hat.
  - **Follow TCP-Stream:** Eine der nützlichsten Funktionen, um den kompletten Inhalt einer Sitzung (Stream) geordnet anzeigen zu lassen. Erreichbar via **Rechtsklick auf ein TCP-Paket -> "Follow TCP-Stream"**.

**Wireshark Filter-Zusammensetzung:**

Display-Filter (Anzeigefilter) dienen dazu, die riesige Menge an aufgezeichneten Paketen gezielt einzugrenzen.

**Schnelle Filter-Erstellung (Maus-Methode):**

Du musst nicht jeden Filter auswendig kennen. Klicke im *Packet Details*-Bereich einfach mit der **rechten Maustaste** auf das gewünschte Feld (z.B. eine IP-Adresse oder einen Port), wähle **"Apply as Filter"** und dann **"Selected"**.

**Einfache Protokoll-Filter:** 

Die einfachste Art zu filtern ist die direkte Eingabe des Protokollnamens.

````
http, dns, ip, ipv6, arp, bootp, icmp, tcp, udp
````

**Host-, IP- und MAC-Filter:**

````
## Zeigt den gesamten Traffic an oder von dieser IP-Adresse
ip.addr == 192.168.1.2

## Zeigt nur Traffic an, bei dem diese IP der Absender ist
src host 192.168.1.2

## Zeigt nur Traffic an, bei dem diese IP das Ziel ist
dst host 192.168.1.2

## Filtert gezielt nach einer physikalischen MAC-Adresse auf Layer 2
ether host 00-02-a3-bb-00-01
````

**Port-Filter:**

````
## Zeigt jeglichen Traffic über Port 80, z. B. HTTP
port 80

## Zeigt nur Traffic an, der an den Ziel-Port 80 gerichtet ist
dst port 80
````

**Operatoren zur Filter-Zusammensetzung (Ausschlussverfahren):** 

Durch logische Operatoren (`!`, `not`, `and`, `or`) können Filter kombiniert werden, um irrelevanten Traffic – sogenanntes "Rauschen" – auszublenden.

````
## Ausschluss (! oder not) - Jeder Traffic, außer Traffic auf Port 80
!port 80

## Blendet den oft störenden IPv6-Traffic komplett aus
!ip6

## Blendet sämtlichen ARP-Traffic aus
!arp
````

**Verkettung von Bedingungen**

Wenn du nur "guten Netzwerkverkehr" analysieren willst und störende Standard-Anfragen ausblenden möchtest, verknüpfst du Filter mit `and` und `not()`.

Beispiel für eine komplexe Filter-Zusammensetzung:

``` 
## Dieser Filter blendet den gesamten normalen Traffic auf Port 80/8080 sowie DNS-Anfragen auf Port 53 aus
not(tcp.port==80) and not (tcp.port==8080) and not(udp.srcport==53 and udp.dstport==53)
```

(Quelle: Block 2, Folie 27-42 / Block 5, Folie 13-17 / Block 8, Folie 4-7)
