---
{"dg-publish":true,"permalink":"/6 Transportschicht/Transportschicht Grundlagen/","tags":["computernetworks","transport"],"updated":"2026-06-18T22:32:42.917+02:00","dg-note-properties":{"permalink":"/6 Transportschicht/Transportschicht Grundlagen/","tags":["computernetworks","transport"],"updated":"2026-06-18T22:20:30.613+02:00"}}
---



# Transportschicht Grundlagen

> [!abstract] Auf einen Blick
> Die Transportschicht **gehört zum Netz-Nutzer** (nicht zum Netzbetreiber): Sie fängt die Fehler der unsicheren [[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|dritten Schicht]] auf und stellt den Anwendungen erstmals eine **Prozess-zu-Prozess**-Verbindung bereit — bei [[6 Transportschicht/TCP\|TCP]] sogar einen verlässlichen Byte-Strom.

## Dienste
- **Schnittstelle** zur Anwendung (Adressierung über [[6 Transportschicht/Ports & Sockets\|Ports]]),
- **Multiplexing** von einer IP zu mehreren Anwendungen,
- **Fehlerkorrektur** bei unzuverlässiger Netzschicht,
- bessere **Quality of Service (QoS)**.

## Aufgaben (wie die Sicherungsschicht — nur Ende-zu-Ende)
Fehlererkennung (Checksummen, Bestätigungen), Verbindungskontrolle, Daten-Pufferung, Schutz der Daten, **Flusskontrolle**. Weil die Protokolle hier den Fehlern der Netzschicht begegnen, ähneln sie denen der [[2 Link Layer/LLC – Sicherung\|Sicherungsschicht]] — nur eben **Ende-zu-Ende** statt Hop-zu-Hop.

## Verwandte Themen
[[6 Transportschicht/Ports & Sockets\|Ports & Sockets]] · [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/UDP\|UDP]] · [[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]] · [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|⬅️ Übersicht]]  ·  [[6 Transportschicht/Ports & Sockets\|Ports & Sockets ➡️]]