---
{"dg-publish":true,"permalink":"/1 Grundlagen/Aufbau des Internets/","tags":["computernetworks","grundlagen"],"updated":"2026-06-18T22:32:42.742+02:00","dg-note-properties":{"permalink":"/1 Grundlagen/Aufbau des Internets/","tags":["computernetworks","grundlagen"],"updated":"2026-06-18T22:20:27.297+02:00"}}
---



# Aufbau des Internets

> [!abstract] Auf einen Blick
> Das Internet ist hierarchisch aus **Autonomen Systemen (AS)**, **Netzen** und **Nodes** (Router, Hosts) aufgebaut. Auf oberster Ebene stehen die AS — administrative Einheiten mit eigener Verwaltung und eigenen [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Richtlinien]].

## Autonome Systeme (AS)
Mehr als 60.000 AS bilden die oberste Stufe. Ein AS hat **gleiche Verwaltung** und **gleiche Routing-Protokolle**, identifiziert durch eine **16/32-Bit-ASN**. Zwischen AS bestehen Geschäftsbeziehungen:
- **Tier 1** — kauft keinen Transit, betreibt kostenneutrales **Peering** mit Gleichgroßen.
- **Tier 3** — kauft Transit/Peering von größeren Partnern.
- **Tier 2** — dazwischen.

**Peering** findet oft an Internet-Knoten statt (z. B. DE-CIX Frankfurt).

## Access vs. Backbone
Bei den kleineren Einheiten (Netzen) unterscheidet man zwei Formen, die sich vor allem auf **Ebene 1 und 2** unterscheiden — ab **Ebene 3** werden sie zu einem großen „Netz“ zusammengeschlossen:
| | [[3 Access Networks/3.0 Access Networks (Übersicht)\|Access]] | [[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|Backbone]] |
|---|---|---|
| Zugänge | viele | wenige |
| Entfernungen | kurz | groß |
| Technologien | viele, heterogen | wenige, einheitlich |
| Last | sehr unterschiedlich | gleichmäßiger |

## Verwandte Themen
[[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte]] · [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Protokolle]] · [[3 Access Networks/3.0 Access Networks (Übersicht)\|3.0 Access Networks (Übersicht)]] · [[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|4.0 Backbone Networks (Übersicht)]]

[[1 Grundlagen/1.0 Grundlagen (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[1 Grundlagen/Netzwerk-Geräte\|⬅️ Netzwerk-Geräte]]  ·  [[2 Link Layer/2.0 Link Layer (Übersicht)\|Kapitel 2: Link Layer ➡️]]