---
{"dg-publish":true,"permalink":"/1 Grundlagen/Protokolle/","tags":["computernetworks","grundlagen"],"updated":"2026-06-18T22:32:42.790+02:00","dg-note-properties":{"permalink":"/1 Grundlagen/Protokolle/","tags":["computernetworks","grundlagen"],"updated":"2026-06-18T22:20:27.217+02:00"}}
---



# Protokolle

> [!abstract] Auf einen Blick
> Ein **Protokoll** legt **Form, Ordnung und Konventionen** der Kommunikation zwischen Partnern fest: Adressierung, Form der PDUs (z. B. Frames), Fehlerbehandlung, Richtung des Datenflusses und ggf. Flusskontrolle.

## Was ein Protokoll regeln muss
- **Identifikation und Adressierung** der Partner,
- **Form** der Protokoll-Atome (Frames, Pakete, Segmente),
- **Fehlerbehandlung**,
- optional **Verbindungsorientierung**,
- **Richtung** des Datenflusses (simplex, halbduplex, vollduplex),
- oft eine Form von **Multiplexing**,
- optional **Flusskontrolle** (Überlastvermeidung).

Beschrieben werden Protokolle über **zeitlichen Ablauf** (Sequenzdiagramme) und **logische Folge** (Zustände).

## Verbindungsorientiert vs. verbindungslos
| | verbindungsorientiert | verbindungslos |
|---|---|---|
| Aufbau | **Handshake** vor Datenaustausch | kein Handshake |
| Partner | dedizierte Instanzen, Verbindungs-ID | keine dedizierten Partner |
| Einheit | Datenstrom | einzelne **Datagramme** |
| oft gebündelt mit | Zuverlässigkeit, Überlastkontrolle | minimaler Overhead |
| Beispiel | [[6 Transportschicht/TCP\|TCP]] | [[6 Transportschicht/UDP\|UDP]], [[5 Vermittlungsschicht/IPv4-Paket\|IP]] |

## Verwandte Themen
[[1 Grundlagen/Schichtenmodell\|Schichtenmodell]] · [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/UDP\|UDP]] · [[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]] · [[2 Link Layer/Vermittlungsarten\|Vermittlungsarten]]

[[1 Grundlagen/1.0 Grundlagen (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[1 Grundlagen/Schichtenmodell\|⬅️ Schichtenmodell]]  ·  [[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte ➡️]]