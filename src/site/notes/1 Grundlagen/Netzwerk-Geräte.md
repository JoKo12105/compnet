---
{"dg-publish":true,"permalink":"/1 Grundlagen/Netzwerk-Geräte/","tags":["computernetworks","grundlagen"],"updated":"2026-06-18T18:28:31.400+02:00","dg-note-properties":{"tags":["computernetworks","grundlagen"],"aliases":["Geräte","Hub","Switch","Router","Gateway","Middlebox"]}}
---


# Netzwerk-Geräte

> [!abstract] Auf einen Blick
> Geräte werden nach der **höchsten Schicht** eingeordnet, deren Protokolle sie „verstehen“. Ein Gerät operiert auf **Ebene n**, wenn es die Protokolle bis Ebene n versteht.

## Geräte nach Ebenen
| Ebene | Gerät | Aufgabe |
|---|---|---|
| 1 | **Hub** | reine **Signalverstärkung** (alle Ports sehen alles) |
| 2 | **Switch** | verknüpft Netzwerk-Segmente, leitet anhand der **MAC-Adresse** gezielt weiter → [[3 Access Networks/Ethernet\|Ethernet]] |
| 3 | **Router** | findet den Weg zwischen **Subnetzen** anhand der **IP-Adresse** → [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] |
| 4+ | **Gateway / Middlebox** | diverse Funktionen, z. B. Sicherheit, Übersetzung (NAT, Firewall) |

Ein **Switch** vermeidet Kollisionen, indem er Frames nur an den Zielport schickt (dediziertes Medium statt Shared Medium). Ein **Router** arbeitet mit Paketen und entscheidet per [[5 Vermittlungsschicht/Longest Prefix Match\|Longest Prefix Match]], wohin ein Paket geht.

## Verwandte Themen
[[1 Grundlagen/Schichtenmodell\|Schichtenmodell]] · [[3 Access Networks/Ethernet\|Ethernet]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[1 Grundlagen/Aufbau des Internets\|Aufbau des Internets]]

[[1 Grundlagen/1.0 Grundlagen (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[1 Grundlagen/Protokolle\|⬅️ Protokolle]]  ·  [[1 Grundlagen/Aufbau des Internets\|Aufbau des Internets ➡️]]