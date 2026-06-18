---
{"dg-publish":true,"permalink":"/5-vermittlungsschicht/routing-protokolle/","tags":["computernetworks","vermittlung"],"dg-note-properties":{"tags":["computernetworks","vermittlung"],"aliases":["Routing-Protokolle","IGP","EGP","OSPF","BGP","Distance Vector","Link State"]}}
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

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
