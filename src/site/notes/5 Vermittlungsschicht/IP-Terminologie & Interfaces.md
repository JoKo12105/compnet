---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/IP-Terminologie & Interfaces/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T23:46:01.975+02:00","dg-note-properties":{"tags":["computernetworks","vermittlung"],"aliases":["IP-Terminologie","Node","Host","Router","Link","Interface","Loopback","Virtuelle Interfaces","Namespaces","MTU"]}}
---


# IP-Terminologie & Interfaces

> [!abstract] Auf einen Blick
> IP führt eine eigene Terminologie ein: **Node**, **Router**, **Host**, **Link** und **Interface**. Wichtig: IP **erzeugt** keine Interfaces, sondern **konfiguriert** sie — und zwar physische *wie* virtuelle (z. B. Loopback oder VPN-Endpunkte).

## Die Begriffe
- **Node** — jedes Gerät, das IP implementiert.
- **(IP-)Router** — ein Node, der Pakete weiterleitet, die **nicht an ihn** adressiert sind. → [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]]
- **Host** — alle übrigen Nodes (Endgeräte), die nur eigene Pakete senden/empfangen.
- **Link** — ein Kommunikationskanal, über den Nodes direkt kommunizieren (z. B. ein [[3 Access Networks/Ethernet\|Ethernet]]-Segment).
- **Interface** — die Schnittstelle, über die ein Node an einen Link angeschlossen ist (die Netzwerkkarte / NIC).

## Attribute eines Interface
Jedes Interface trägt u. a.:
- eine **IP-Adresse** ([[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]]),
- eine **Netzmaske**,
- eine **MTU** (Maximum Transmission Unit) — die maximale Nutzlast,
- einen **Typ** (Point-to-Point oder Broadcast).

## Physische vs. virtuelle Interfaces
IP **konfiguriert** vorhandene Interfaces, statt sie zu erschaffen. Sie entstehen als:
- **physische Schnittstellen** — jedes aktive Gerät der Ebenen 1/2 wird vom Betriebssystem als Interface angelegt; die (De-)Aktivierung kann dynamisch geschehen.
- **virtuelle Schnittstellen** — IP-spezifisch, z. B. das **Loopback** (`127.0.0.1` bzw. `::1`) für Tests im eigenen Host, sowie **Pseudo-Geräte** wie **VPN-Endpunkte** oder **Bridges**. Diese Form ist v. a. im **Container**-Umfeld verbreitet.

> [!note] Namespaces
> Wie alle Betriebssystem-Ressourcen sind auch Interfaces **Namespaces** zugeordnet — die technische Grundlage dafür, dass Container voneinander isolierte Netzwerk-Stacks haben.

## Verwandte Themen
[[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]] · [[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte]] · [[3 Access Networks/Ethernet\|Ethernet]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/Routing-Protokolle\|⬅️ Routing-Protokolle]]  ·  [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR ➡️]]
