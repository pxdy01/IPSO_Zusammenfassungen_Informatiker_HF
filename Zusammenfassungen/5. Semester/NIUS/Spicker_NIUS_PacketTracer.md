# Spicker Netzwerk-Troubleshooting

Sep 28, 2026 · @Patrik

Alle Fehler aus den Labs im Ordner, je mit Symptom, Diagnose, Behebung und Test. Die Fehler der Labs 01–03 stammen aus den Musterlösungen, die der Troubleshooting Challenge aus dem Vergleich Ausgangs- vs. Soll-Konfiguration in der .pka-Datei.

## Vorgehen (immer gleich)

Vom Client aus Schicht für Schicht eingrenzen, dann erst die Config lesen.

1. **Client prüfen:** `ipconfig /all` → IP, Maske, Gateway, DNS mit der Adresstabelle vergleichen.
2. **Gateway pingen:** geht nicht → Fehler lokal (IP/Maske/VLAN/Switchport/Router-Interface).
3. **Ziel per IP pingen:** `ping 198.51.100.100` bzw. Webserver-IP.
4. **Traceroute:** `tracert <Ziel>` → der letzte antwortende Hop zeigt, WO es hängt.
5. **Name testen:** Ping per IP geht, per Name nicht → DNS (Server, ACL, Client-DNS-Eintrag).
6. **Auf dem verdächtigen Gerät:** `show ip int brief`, `show ip route`, `show run`, `show access-lists`, `show vlan brief`.
7. **Beheben, dann exakt den Test vom Anfang wiederholen** und mit `copy run start` speichern.

Für die Doku an der Prüfung: *Wie herangegangen → wie eingegrenzt → wie gelöst* (so steht es auf dem Aufgabenblatt).

## LAB 01 – Keine Default-Route ins Internet (R4)

**Symptom:** GL1 und Verwaltung erreichen ifa.ch nicht. Interne Netze funktionieren.

**Ursache:** R4 (Internet-Router mit NAT) hat keine Default-Route zum Provider-Router R5 (192.0.2.10) und gibt sie nicht per OSPF an R1–R3 weiter.

**Herausfinden:**

- `tracert` vom Laptop → endet intern, bzw. „Destination host unreachable“.
- Auf R1/R2/R3: `show ip route` → **kein** Eintrag `O*E2 0.0.0.0/0` (Gateway of last resort is not set).
- Auf R4: `show run | section ospf` → `default-information originate` fehlt; `show ip route` → keine `S* 0.0.0.0/0`.

**Beheben:**

```
R4(config)# ip route 0.0.0.0 0.0.0.0 192.0.2.10
R4(config)# router ospf 1
R4(config-router)# default-information originate
```

**Testen:** Auf R1: `show ip route` → `O*E2 0.0.0.0/0 via …` erscheint. Vom Laptop `ping`/`tracert` zum Webserver 198.51.100.100 und im Browser ifa.ch öffnen.

**Merke:** `default-information originate` verteilt nur eine Default-Route, die der Router selbst schon in der Routing-Tabelle hat. Beides zusammen nötig.

## LAB 02 – Access-Switch S11: STP und VLAN 20

**Symptom:** GL1 hat nach dem Einstecken/Starten ca. 30–50 s keine Verbindung und erreicht www.ifa.ch gar nicht.

**Ursache (3 Fehler auf S11):**

1. `spanning-tree mode pvst` statt `rapid-pvst` (alle anderen Switches laufen RSTP).
2. Access-Ports Fa0/1–20 haben `spanning-tree portfast disable`, kein BPDU Guard → Port durchläuft Listening/Learning, darum die Wartezeit.
3. **VLAN 20 existiert nicht** in der VLAN-Datenbank. Fa0/1–10 sind zwar `switchport access vlan 20`, aber der Port ist dann inaktiv → GL1 (an Fa0/1) hat gar kein Netz.

**Herausfinden:**

- `show vlan brief` → nur VLAN 1 und 21, **VLAN 20 fehlt**, Fa0/1–10 tauchen nirgends auf.
- `show interfaces fa0/1 switchport` → `Access Mode VLAN: 20 (Inactive)`.
- `show spanning-tree` → `Spanning tree enabled protocol ieee` (= PVST, nicht rstp).
- `show run` → `spanning-tree portfast disable` auf den Access-Ports.

**Beheben:**

```
S11(config)# spanning-tree mode rapid-pvst
S11(config)# interface range f0/1-20
S11(config-if-range)# spanning-tree portfast
S11(config-if-range)# spanning-tree bpduguard enable
S11(config-if-range)# exit
S11(config)# vlan 20
S11(config-vlan)# name GL
```

**Testen:** `show vlan brief` → Fa0/1–10 in VLAN 20. `show spanning-tree` → `protocol rstp`, Access-Ports als `Edge`. Kabel an GL1 ziehen/stecken → Link sofort grün. Ping 192.168.20.1, dann ifa.ch.

**Merke:** PortFast und BPDU Guard nur auf Endgeräte-Ports, nie auf Trunks (Gi0/1, Gi0/2). BPDU Guard setzt einen Port err-disabled, wenn dort ein Switch angeschlossen wird.

## LAB 03 – ACL auf R2 blockiert DNS für die Verwaltung

**Symptom:** Nur der Laptop Verwaltung (VLAN 21, 192.168.21.0/24) erreicht ifa.ch nicht. GL1 (VLAN 20) geht.

**Ursache:** Auf R2 hängt die Extended-ACL `acl` inbound an Gi0/0 (Link von R1). Sie erlaubt DNS (UDP 53) zum DNS-Server 172.20.20.100 nur aus 192.168.**20**.0/24. Der Eintrag für 192.168.**21**.0/24 fehlt → implizites `deny any` am Ende verwirft die DNS-Anfrage.

**Herausfinden:**

- Browser mit IP (`http://198.51.100.100`) geht, mit Name nicht → Namensauflösung ist das Problem.
- `nslookup ifa.ch` auf Verwaltung → Timeout.
- Unterschied GL1 vs. Verwaltung = anderes Subnetz → nach ACLs suchen: `show ip interface gi0/0` („Inbound access list is acl“), dann `show access-lists` → Trefferzähler (`matches`) ansehen, nur 192.168.20.0 hat einen DNS-Eintrag.
- Achtung: Die ACL erlaubt kein ICMP. Ein Ping durch R2 kann darum scheitern, obwohl das Routing stimmt.

**Beheben:**

```
R2(config)# ip access-list extended acl
R2(config-ext-nacl)# permit udp 192.168.21.0 0.0.0.255 host 172.20.20.100 eq 53
```

**Testen:** `nslookup ifa.ch` auf Verwaltung liefert eine IP. Browser mit ifa.ch öffnen. `show access-lists` → der neue Eintrag zählt `matches` hoch.

**Merke:** Neue Zeilen in einer benannten ACL kommen ans Ende, aber **vor** das implizite deny. Reihenfolge prüfen: Ein früheres `deny` würde zuerst greifen (dann mit Sequenznummer einfügen, z. B. `15 permit …`).

## Troubleshooting Challenge (.pka) – 6 Fehler

Ziel: Alle PCs erreichen Webserver, R1 und Switches (IPv4 + IPv6) und kommen per SSH auf R1. Netze: IT 172.16.1.0/26, Marketing 172.16.1.64/26, R&D 172.16.1.128/25. Logins: enable `Ciscoenpa55`, SSH `Admin1` / `Admin1pa55`.

| # | Gerät | Fehler (Ist → Soll) | So findest du ihn | Fix |
| --- | --- | --- | --- | --- |
| 1 | PC IT | IPv4 192.168.1.1, GW 192.168.1.62 → **172.16.1.1 /26, GW 172.16.1.62** | `ipconfig` vs. Adresstabelle; Ping aufs Gateway scheitert | Desktop → IP Configuration anpassen |
| 2 | PC R&D | IPv6 2001:db8:cafe::2 (= Duplikat von IT) → **2001:db8:cafe:2::2/64** | `ipconfig` → Präfix passt nicht zu R1 G0/2 (cafe:2::/64) | IPv6-Adresse korrigieren, GW fe80::1 |
| 3 | S2 | VLAN1 172.16.1.125 **/27** → **/26** (255.255.255.192) | `show ip int brief` / `show run int vlan1`; Maske ≠ Adresstabelle und ≠ R1 G0/1 (/26); mit /27 liegt Marketing (.65–.95) nicht mehr im selben Subnetz wie S2 | `int vlan 1` → `ip address 172.16.1.125 255.255.255.192` |
| 4 | R1 | G0/1 IP 192.168.1.126 → **172.16.1.126 /26** | `show ip int brief`; Marketing erreicht Gateway nicht | `int g0/1` → `ip address 172.16.1.126 255.255.255.192` |
| 5 | R1 | SSH-User fehlt | `show run \| include username` → leer | `username Admin1 secret Admin1pa55` |
| 6 | R1 | VTY nur Telnet → **SSH** | `show run \| section line vty` → `transport input telnet` | `line vty 0 4` → `transport input ssh` + `login local` |

**Testen:**

- Von jedem PC: `ping 64.100.0.3` (Web) und `ping 2001:db8:acad::3`, dazu Ping auf das eigene Gateway und auf den Switch im eigenen Netz.
- Von jedem PC: `ssh -l Admin1 172.16.1.62` → Login klappt. Auf R1 `show ip ssh` → „SSH Enabled“ (sonst `crypto key generate rsa`, 1024 Bit, Domain `CCNA-lab.com` ist gesetzt).
- Auf S2: `ping 172.16.1.126`.

**Hinweis zu deiner gespeicherten Datei:** Dort hat R1 zusätzlich auf S0/0/0 die IP 209.165.200.226 – das ist die IP von Main (Duplikat). Im Soll ist R1 S0/0/0 ungenutzt und `shutdown`.

## Weitere Labs: IPv4/IPv6-Interfaces und WLAN

**Lab 1.1.3.5 (IPv4/IPv6-Schnittstellen):** Kein Fehler-Lab, sondern Konfiguration. Die Stolpersteine sind trotzdem prüfungsrelevant: LAN-Interfaces haben keine Adresse und sind `shutdown`.

```
R1(config)# int g0/0
R1(config-if)# ip address 172.16.20.1 255.255.255.128
R1(config-if)# no shutdown
R2(config)# ipv6 unicast-routing
R2(config)# int g0/0
R2(config-if)# ipv6 address 2001:db8:c0de:12::1/64
R2(config-if)# ipv6 address fe80::2 link-local
R2(config-if)# no shutdown
```

Test: `show ip int brief` / `show ipv6 int brief` → up/up. PCs: IPv4-GW = Router-IP im LAN, IPv6-GW = **fe80::2** (Link-Local!). Ping PC↔PC und zum Dual-Stack-Server.

**WLAN mit Wireless Controller (WLC 2504 + 3702i):**

- APs finden den Controller nicht → im DHCP-Pool fehlt `option 150 ip 192.168.1.254` (WLC-Adresse), oder AP steht nicht auf DHCP.
- IP-Konflikt → WLC-Management-IP zuerst setzen und `ip dhcp excluded-address 192.168.1.1 192.168.1.9` auf dem Switch.
- APs ohne Strom → PoE vom Multilayer-Switch.
- Test: `show ip dhcp binding` auf dem Switch (APs haben Adressen), im WLC-Web-GUI die APs als verbunden sehen, Laptop verbindet mit SSID.

**WLAN-Störungen (Theorie):** Kanalüberlappung (2,4 GHz nur 1/5/9/13), fremde WLANs, Mikrowellen/Bluetooth, Wände/Funklöcher, fehlerhaftes Handover. Handover = AP-Wechsel im eigenen Netz, Roaming = Wechsel in anderes Netz/Medium.

## Befehls-Toolbox nach Fehlerart

| Verdacht | Befehl | Worauf achten |
| --- | --- | --- |
| Interface / IP | `show ip int brief`, `show ipv6 int brief` | up/up? richtige IP? `administratively down` → `no shutdown` |
| Maske / Subnetz | `show run int <if>` | Maske = Adresstabelle, Gateway im selben Subnetz |
| Routing | `show ip route`, `show ipv6 route` | Route zum Ziel? `Gateway of last resort` gesetzt? |
| OSPF | `show ip ospf neighbor`, `show run \| section ospf` | Nachbarn FULL, `network`-Statements, `passive-interface`, `default-information originate` |
| ACL | `show access-lists`, `show ip int <if>` | Welche ACL, welche Richtung, `matches`-Zähler, implizites deny |
| VLAN | `show vlan brief`, `show int <if> switchport` | VLAN existiert? Port im richtigen VLAN? `(Inactive)` |
| Trunk | `show interfaces trunk` | Allowed VLANs enthalten 20/21? native VLAN gleich? |
| STP | `show spanning-tree` | `rstp` vs. `ieee`, Root Bridge, Port `Edge` (PortFast), err-disabled |
| NAT | `show ip nat translations`, `show run \| include nat` | inside/outside richtig, ACL 1 deckt Quellnetze ab |
| DNS | `nslookup <name>` am Client | Per IP ok, per Name nicht → DNS-Server/ACL/Client-DNS |
| SSH | `show ip ssh`, `show run \| section line vty` | `transport input ssh`, `login local`, Username, RSA-Key |
| Client | `ipconfig /all`, `ping`, `tracert` | IP/Maske/GW/DNS, letzter Hop im tracert |

Nach jeder Änderung: gleichen Test wiederholen, dann `copy running-config startup-config`.
