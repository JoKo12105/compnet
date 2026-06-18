---
{"dg-publish":true,"permalink":"/2 Link Layer/MAC – Medienzugang/","tags":["computernetworks","linklayer"],"updated":"2026-06-18T15:04:04.362+02:00","dg-note-properties":{"tags":["computernetworks","linklayer"],"aliases":["MAC","Medienzugang","Multiplexing","Token","Random Access","Carrier Sense"]}}
---


# MAC – Medienzugang

> [!abstract] Auf einen Blick
> **MAC (Media Access Control)** regelt den Zugang **mehrerer** Stationen zu einem **gemeinsamen Kanal** (Broadcast-Medium). Hauptziel: **Kollisionen** verschiedener Frames verhindern. Drei Verfahrensklassen: **Multiplexing**, **Token**, **Random Access**.

## Multiplexing (zentrale Vergabe)
- **FDM** — feste **Frequenz**-Bänder pro Station (nur bei Breitband).
- **TDM** — feste **Zeitschlitze** pro Station.
- **CDM/CDMA** — **Codes**, v. a. im [[3 Access Networks/Mobilfunk\|Mobilfunk]].

Nachteil von FDM/TDM: Bandbreite wird **verschenkt**, wenn nur wenige Stationen senden.

## Token-Verfahren
Ein spezielles Bitmuster (**Token**) kreist; nur wer das Token besitzt, darf senden (z. B. Token Ring, FDDI). Gut **berechenbar**, aber wegen Durchsatz- und Stabilitätsproblemen heute selten.

## Random Access
Jede Station sendet, **wenn** sie Daten hat — keine zentrale Steuerung nötig. Problem: **Kollisionen**. Zwei einfache Optimierungen:
1. **Carrier Sensing** — nur senden, wenn das Medium frei ist.
2. **Collision Detection** — Senden abbrechen, wenn eine Kollision auftritt.

> [!warning] Wer erkennt Kollisionen?
> Der **Empfänger** sieht stets zerstörte Daten. Der **Sender** nicht immer: bei **Kabel** ja (→ [[3 Access Networks/Ethernet\|CSMA/CD]]), bei **Funk** nein (Fading, Hidden Stations) → dort **Collision Avoidance** ([[3 Access Networks/WLAN\|CSMA/CA]]).

## Verwandte Notes
[[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]] · [[3 Access Networks/Ethernet\|Ethernet]] · [[3 Access Networks/WLAN\|WLAN]] · [[3 Access Networks/Mobilfunk\|Mobilfunk]] · [[2 Link Layer/Vermittlungsarten\|Vermittlungsarten]]

[[2 Link Layer/2.0 Link Layer (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[2 Link Layer/LLC – Sicherung\|⬅️ LLC – Sicherung]]  ·  [[2 Link Layer/Vermittlungsarten\|Vermittlungsarten ➡️]]