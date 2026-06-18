---
{"dg-publish":true,"permalink":"/0-uebersicht-and-glossar/glossar/","tags":["computernetworks","glossar"],"dg-note-properties":{"tags":["computernetworks","glossar"]}}
---


# 📖 Glossar

Alphabetisches Nachschlagewerk der zentralen Begriffe. Jeder Eintrag verweist auf die ausführliche Note.

## A
- **AS (Autonomes System)** — administrative Einheit mit eigener Verwaltung und Routing-Politik, durch eine ASN identifiziert. → [[1 Grundlagen/Aufbau des Internets\|Aufbau des Internets]]
- **ACK** — Bestätigung des Empfangs (Acknowledgement); zentral bei [[2 Link Layer/LLC – Sicherung\|ARQ]] und [[6 Transportschicht/TCP\|TCP]].
- **ARP** — Address Resolution Protocol: bildet eine IP- auf eine MAC-Adresse ab. → [[5 Vermittlungsschicht/ARP\|ARP]]
- **ARQ** — Automatic Repeat Request: Fehlerbehandlung durch erneutes Senden. → [[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]]

## B
- **Bandbreite** — Frequenzbereich eines Mediums (physikalisch). → [[1 Grundlagen/Physikalische Grundlagen\|Physikalische Grundlagen]]
- **Backbone** — auf Skalierbarkeit ausgelegtes Kernnetz großer Reichweite. → [[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|4.0 Backbone Networks (Übersicht)]]
- **BGP** — Border Gateway Protocol, das Exterior-Routing-Protokoll zwischen AS. → [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Protokolle]]

## C
- **CIDR** — Classless Inter-Domain Routing: Netz/Host-Grenze per Präfixlänge. → [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]]
- **CSMA/CD** — Carrier Sense Multiple Access / Collision Detection (klassisches Ethernet). → [[3 Access Networks/Ethernet\|Ethernet]]
- **CSMA/CA** — Collision Avoidance (WLAN). → [[3 Access Networks/WLAN\|WLAN]]
- **Circuit Switching** — Leitungsvermittlung mit reserviertem Weg. → [[2 Link Layer/Vermittlungsarten\|Vermittlungsarten]]

## D
- **Datenrate** — übertragene Bits pro Sekunde (Sicht der Informatik). → [[1 Grundlagen/Physikalische Grundlagen\|Physikalische Grundlagen]]
- **DHCP** — dynamische Vergabe von IP-Konfiguration beim Booten. → [[5 Vermittlungsschicht/DHCP\|DHCP]]
- **DWDM** — Dense Wavelength Division Multiplexing im Backbone. → [[4 Backbone Networks/SONET, SDH & DWDM\|SONET, SDH & DWDM]]
- **DSL** — Digital Subscriber Line über die Telefonleitung. → [[3 Access Networks/DSL\|DSL]]

## E
- **Encapsulation** — Verpacken einer Dateneinheit der Ebene n in eine der Ebene n−1. → [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]]
- **Ethernet** — wichtigstes LAN-Protokoll, IEEE 802.3. → [[3 Access Networks/Ethernet\|Ethernet]]

## F
- **FEC** — Forward Error Correction: Fehlerkorrektur durch redundante Daten. → [[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]]
- **Forwarding** — Weiterleiten eines Pakets vom Eingang zum passenden Ausgang (data plane). → [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]]
- **Frame** — Dateneinheit (PDU) des Link Layers. → [[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]]

## I
- **ICMP** — Internet Control Message Protocol (Fehlermeldungen, ping). → [[5 Vermittlungsschicht/ICMP\|ICMP]]
- **IP-Adresse** — 32-Bit- (IPv4) bzw. 128-Bit-Größe (IPv6) zur Identifikation eines Interface. → [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]]
- **IPv6** — Nachfolger von IPv4 mit 128-Bit-Adressen. → [[5 Vermittlungsschicht/IPv6\|IPv6]]

## L
- **Latenz** — Verzögerung der Übertragung. → [[1 Grundlagen/Physikalische Grundlagen\|Physikalische Grundlagen]]
- **LLC** — Logical Link Control (Datensicherung). → [[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]]
- **LPM** — Longest Prefix Match: beste Route = längstes passendes Präfix. → [[5 Vermittlungsschicht/Longest Prefix Match\|Longest Prefix Match]]

## M
- **MAC** — Media Access Control (Medienzugang) bzw. die 6-Byte-Hardwareadresse. → [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]] · [[3 Access Networks/Ethernet\|Ethernet]]
- **Mobilfunk** — zellulare Funknetze (GSM, UMTS, LTE, 5G). → [[3 Access Networks/Mobilfunk\|Mobilfunk]]
- **MTU** — Maximum Transmission Unit (max. Nutzlast eines Mediums). → [[3 Access Networks/Ethernet\|Ethernet]]

## P
- **Packet Switching** — Paketvermittlung: jedes Paket einzeln. → [[2 Link Layer/Vermittlungsarten\|Vermittlungsarten]]
- **Paket / Datagram** — PDU der Vermittlungsschicht. → [[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket]]
- **Port** — nummerierter Kommunikationsendpunkt im OS. → [[6 Transportschicht/Ports & Sockets\|Ports & Sockets]]
- **Protokoll** — Vorgabe von Form, Ordnung und Konventionen der Kommunikation. → [[1 Grundlagen/Protokolle\|Protokolle]]

## R
- **Router** — Gerät der Ebene 3, das Pakete zwischen Netzen weiterleitet. → [[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]]
- **Routing** — Bereitstellen der Forwarding-Informationen (control plane). → [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]]
- **RTT** — Round Trip Time. → [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle bei TCP]]

## S
- **Schichtenmodell** — vertikale Zerlegung der Netzaufgaben in Schichten. → [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]]
- **Socket** — prozess-interner Kommunikationsendpunkt (≈ Datei). → [[6 Transportschicht/Ports & Sockets\|Ports & Sockets]]
- **Switch** — Gerät der Ebene 2, verbindet Netzwerk-Segmente. → [[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte]]
- **Subnetz** — feinere, intern sichtbare Unterteilung eines Netzes. → [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]]

## T
- **TCP** — zuverlässiges, verbindungsorientiertes Transportprotokoll. → [[6 Transportschicht/TCP\|TCP]]
- **TTL** — Time To Live (Hop-Zähler im IP-Paket). → [[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket]]

## U
- **UDP** — verbindungsloses, unzuverlässiges Transportprotokoll. → [[6 Transportschicht/UDP\|UDP]]

## W
- **WLAN** — drahtloses LAN nach IEEE 802.11. → [[3 Access Networks/WLAN\|WLAN]]

[[0 Übersicht & Glossar/Übersicht\|← Zur Übersicht]]
---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">BUY ME A COFFEE ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Websites zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
