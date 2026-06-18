---
{"dg-publish":true,"permalink":"/6 Transportschicht/QUIC/","tags":["computernetworks","transport"],"updated":"2026-06-18T15:04:05.793+02:00","dg-note-properties":{"tags":["computernetworks","transport"],"aliases":["QUIC","Quick UDP Internet Connections"]}}
---


# QUIC

> [!abstract] Auf einen Blick
> **QUIC** will [[6 Transportschicht/TCP\|TCP]] dort ablösen, wo es zu langsam ist. Es basiert auf [[6 Transportschicht/UDP\|UDP]] + TLS, bringt **schnellen Verbindungsaufbau inklusive Verschlüsselung** und liegt als Protokoll der **Ebene 5** — unabhängig von OS und Middleboxes.

## Warum QUIC?
TCP genügt vielen Performance-Anforderungen nicht mehr (Verbindungsaufbau, Latenz, Fehlerkorrektur). QUIC:
- **schneller Verbindungsaufbau** inkl. Austausch der Security-Informationen,
- **eingebaute Verschlüsselung**,
- **Zuverlässigkeit pro Stream** (ein blockierter Stream bremst die anderen nicht),
- Optimierung für **HTTPS**: parallele, unabhängige Ströme pro Anfrage,
- **Multipath** (wie MPTCP).

Weil QUIC auf Layer 5 sitzt, kann es **unabhängig vom Betriebssystem** weiterentwickelt werden.

## Verwandte Notes
[[6 Transportschicht/UDP\|UDP]] · [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle bei TCP]] · [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/UDP\|⬅️ UDP]]  ·  [[6 Transportschicht/Socket-API\|Socket-API ➡️]]