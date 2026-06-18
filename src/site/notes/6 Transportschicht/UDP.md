---
{"dg-publish":true,"permalink":"/6 Transportschicht/UDP/","tags":["computernetworks","transport"],"updated":"2026-06-18T18:28:33.254+02:00","dg-note-properties":{"tags":["computernetworks","transport"],"aliases":["UDP","User Datagram Protocol"]}}
---


# UDP

> [!abstract] Auf einen Blick
> **UDP (User Datagram Protocol)** ist **verbindungslos**, **unzuverlässig** und hat **keine Flusskontrolle**. Es erweitert ein [[5 Vermittlungsschicht/IPv4-Paket\|IP-Paket]] nur um Quell-/Ziel-Port, Länge und Checksumme — minimaler Overhead.

## Wann UDP?
Für kurze **Statusmeldungen** und **Abfrage-Situationen**, bei denen ein Verbindungsaufbau zu teuer wäre oder Verzögerung schlimmer ist als Verlust — z. B. [[5 Vermittlungsschicht/DHCP\|DHCP]], DNS, Streaming, Spiele.

Bei UDP genügt das **2-Tupel** (Ziel-IP, Ziel-Port) zur Identifikation eines Sockets ([[6 Transportschicht/Ports & Sockets\|Ports & Sockets]]). Anders als [[6 Transportschicht/TCP\|TCP]] gibt es keinen Handshake, keine Reihenfolgegarantie und keine Wiederholung.

> [!info] Weitere Transportprotokolle
> Neben TCP und UDP gibt es SCTP, RTP (Echtzeit) und – besonders relevant – [[6 Transportschicht/QUIC\|QUIC]].

## Verwandte Themen
[[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/QUIC\|QUIC]] · [[6 Transportschicht/Ports & Sockets\|Ports & Sockets]] · [[5 Vermittlungsschicht/DHCP\|DHCP]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/Flusskontrolle bei TCP\|⬅️ Flusskontrolle bei TCP]]  ·  [[6 Transportschicht/QUIC\|QUIC ➡️]]