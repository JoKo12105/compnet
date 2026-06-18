---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/Routing-Protokolle/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T15:04:05.168+02:00","dg-note-properties":{"tags":["computernetworks","vermittlung"],"aliases":["Routing-Protokolle","IGP","EGP","OSPF","BGP","Distance Vector","Link State"]}}
---


# Routing-Protokolle

> [!abstract] Auf einen Blick
> Routing-Protokolle ermitteln die **beste Route** und halten die [[5 Vermittlungsschicht/Routing & Forwarding\|Forwarding-Tabellen]] aktuell. Man unterscheidet **innerhalb** eines [[1 Grundlagen/Aufbau des Internets\|AS]] (**IGP**) und **zwischen** AS (**EGP**).

## Interior vs. Exterior
| | **IGP** (innerhalb AS) | **EGP** (zwischen AS) |
|---|---|---|
| Beispiele | OSPF, IS-IS, RIPv2 | **BGPv4** |
| Nachbarerkennung | automatisch (z. B. Flooding) | direkte Kommunikation der Partner |
| Algorithmus | **Distance Vector** oder **Link State** | **Path Vector** (Pfad-Attribute) |

## Distance Vector vs. Link State
- **Distance Vector:** Jeder Router kennt nur **Distanzen zu Nachbarn** und tauscht seine Tabelle mit ihnen aus (à la „Sag mir, was du weißt“). Einfach, aber langsame Konvergenz.
- **Link State:** Jeder Router kennt die **gesamte Topologie** (geflutete Link-Zustände) und berechnet selbst kürzeste Wege (Dijkstra). Schnellere Konvergenz, mehr Aufwand. → **OSPF**.

> [!note] BGP – das Protokoll zwischen den AS
> **BGP** entscheidet nicht nur nach „kürzestem Weg“, sondern nach **Richtlinien** (Geschäftsbeziehungen, Tier-Struktur). Es hält das globale Internet zusammen.

## Verwandte Notes
[[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[5 Vermittlungsschicht/Longest Prefix Match\|Longest Prefix Match]] · [[1 Grundlagen/Aufbau des Internets\|Aufbau des Internets]] · [[5 Vermittlungsschicht/IPv6\|IPv6]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/Routing & Forwarding\|⬅️ Routing & Forwarding]]  ·  [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR ➡️]]