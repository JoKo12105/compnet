---
{"dg-publish":true,"permalink":"/6 Transportschicht/TCP/","tags":["computernetworks","transport"],"updated":"2026-06-18T15:04:05.710+02:00","dg-note-properties":{"tags":["computernetworks","transport"],"aliases":["TCP","Transmission Control Protocol","Segment"]}}
---


# TCP

> [!abstract] Auf einen Blick
> **TCP (Transmission Control Protocol)** ist **zuverlässig**, **verbindungsorientiert**, **unicast**, **vollduplex** und **byte-orientiert**. Es ist das Protokoll der meisten Internet-Anwendungen und gleicht die Unzuverlässigkeit von [[5 Vermittlungsschicht/IPv4-Paket\|IP]] aus.

## Eigenschaften
- **byte-orientiert:** TCP ignoriert Nachrichtengrenzen und teilt den Strom in **Segmente** (max. ~64 KB), die es an [[5 Vermittlungsschicht/IPv4-Paket\|IP]] übergibt.
- **zuverlässig:** dank SEQ/ACK, Timern und [[6 Transportschicht/Flusskontrolle bei TCP\|Fenstertechnik]].
- **verbindungsorientiert:** mit Auf- und Abbau ([[6 Transportschicht/TCP-Verbindung\|TCP-Verbindung]]).

## Das TCP-Segment (wichtige Felder)
- **Quell-/Ziel-Port** → identifiziert mit den IPs die Verbindung ([[6 Transportschicht/Ports & Sockets\|Ports & Sockets]]).
- **Sequence Number** — Nummer des ersten Bytes des Segments.
- **Acknowledgement Number** — nächstes erwartetes Byte (gültig bei gesetztem ACK-Flag).
- **Flags** — SYN, ACK, FIN, RST (Verbindung), PSH, URG.
- **Window Size** — Empfangsfenster für die [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle]].
- **Checksum** und **Daten** (max. Länge = MSS).

## Verwandte Notes
[[6 Transportschicht/TCP-Verbindung\|TCP-Verbindung]] · [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle bei TCP]] · [[6 Transportschicht/UDP\|UDP]] · [[6 Transportschicht/Ports & Sockets\|Ports & Sockets]] · [[6 Transportschicht/QUIC\|QUIC]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/Ports & Sockets\|⬅️ Ports & Sockets]]  ·  [[6 Transportschicht/TCP-Verbindung\|TCP-Verbindung ➡️]]