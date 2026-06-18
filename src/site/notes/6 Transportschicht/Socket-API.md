---
{"dg-publish":true,"permalink":"/6 Transportschicht/Socket-API/","tags":["computernetworks","transport"],"updated":"2026-06-18T22:32:42.907+02:00","dg-note-properties":{"permalink":"/6 Transportschicht/Socket-API/","tags":["computernetworks","transport"],"updated":"2026-06-18T22:20:30.917+02:00"}}
---



# Socket-API

> [!abstract] Auf einen Blick
> Nahezu alle Netz-Anwendungen werden über die **Socket-API** programmiert — die Schnittstelle zwischen [[6 Transportschicht/6.0 Transportschicht (Übersicht)\|Ebene 4]] und der Anwendung (Ebene 5). Ein **Socket** ist ein prozess-interner Kommunikationsendpunkt (≈ Datei) und basiert auf dem [[6 Transportschicht/TCP-Verbindung\|Zustandsmodell von TCP]].

## Die zentralen Aufrufe
| Aufruf | Bedeutung |
|---|---|
| `socket()` | neuen Endpunkt erzeugen |
| `bind()` | lokale Adresse (IP:Port) zuordnen (v. a. Server) |
| `listen()` | in Empfangsmodus schalten |
| `accept()` | blockierend auf Verbindung warten |
| `connect()` | aktiver Verbindungsaufbau (Client) |
| `send()` / `recv()` | Daten senden/empfangen |
| `close()` | Verbindung beenden |

Typischer **Server**: `socket → bind → listen → accept → recv/send → close`. Typischer **Client**: `socket → connect → send/recv → close`.

> [!note] Vertiefung
> Die konkrete C-Programmierung (Adress-Strukturen wie `sockaddr_in`, `getaddrinfo`, `inet_pton/ntop`, protokoll-unabhängige Entwicklung) ist Stoff von **Teil IV** der Vorlesung und hier bewusst nur als Brücke skizziert.

## Verwandte Themen
[[6 Transportschicht/Ports & Sockets\|Ports & Sockets]] · [[6 Transportschicht/TCP-Verbindung\|TCP-Verbindung]] · [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/UDP\|UDP]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/QUIC\|⬅️ QUIC]]  ·  [[0 Übersicht & Glossar/Übersicht\|Zur Startseite ➡️]]