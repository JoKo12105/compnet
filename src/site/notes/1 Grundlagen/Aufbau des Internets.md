---
{"dg-publish":true,"permalink":"/1-grundlagen/aufbau-des-internets/","tags":["computernetworks","grundlagen"],"dg-note-properties":{"tags":["computernetworks","grundlagen"],"aliases":["Internet","Autonome Systeme","AS","Tiers","Peering","Access","Backbone"]}}
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

## Verwandte Notes
[[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte]] · [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Protokolle]] · [[3 Access Networks/3.0 Access Networks (Übersicht)\|3.0 Access Networks (Übersicht)]] · [[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|4.0 Backbone Networks (Übersicht)]]

[[1 Grundlagen/1.0 Grundlagen (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[1 Grundlagen/Netzwerk-Geräte\|⬅️ Netzwerk-Geräte]]  ·  [[2 Link Layer/2.0 Link Layer (Übersicht)\|Kapitel 2: Link Layer ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
