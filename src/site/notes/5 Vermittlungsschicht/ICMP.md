---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/ICMP/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T22:32:42.863+02:00","dg-note-properties":{"permalink":"/5 Vermittlungsschicht/ICMP/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T22:20:29.931+02:00"}}
---



# ICMP

> [!abstract] Auf einen Blick
> Das **ICMP (Internet Control Message Protocol)** übermittelt **Status- und Fehlermeldungen** des IP-Betriebs. ICMP-Nachrichten reisen selbst als Nutzdaten **in einem IP-Paket** und werden v. a. von Routern verwendet.

## Typische Meldungen
- **NETWORK UNREACHABLE** — Paket nicht zustellbar.
- **TIME EXCEEDED** — die [[5 Vermittlungsschicht/IPv4-Paket\|TTL]] ist abgelaufen (Grundlage von **traceroute**).
- **ECHO REQUEST / REPLY** — „Lebt der Host noch?“ → das ist **ping**.

> [!note] Grenzen
> ICMP **reagiert nicht** auf ICMP-Fehler (sonst drohten Schleifen). [[5 Vermittlungsschicht/IPv4-Paket\|IP]] selbst dient nur der Paketübertragung; ICMP ergänzt die Diagnose.

## Verwandte Themen
[[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[5 Vermittlungsschicht/IPv6\|IPv6]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/DHCP\|⬅️ DHCP]]  ·  [[5 Vermittlungsschicht/IPv6\|IPv6 ➡️]]