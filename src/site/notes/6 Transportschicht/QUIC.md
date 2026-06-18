---
{"dg-publish":true,"permalink":"/6-transportschicht/quic/","tags":["computernetworks","transport"],"dg-note-properties":{"tags":["computernetworks","transport"],"aliases":["QUIC","Quick UDP Internet Connections"]}}
---


# QUIC

> [!abstract] Auf einen Blick
> **QUIC** will [[6 Transportschicht/TCP\|TCP]] dort ablösen, wo es zu langsam ist. Es basiert auf [[6 Transportschicht/UDP\|UDP]] + TLS, bringt **schnellen Verbindungsaufbau inklusive Verschlüsselung** und liegt als Protokoll der **Ebene 5** — unabhängig von OS und Middleboxes.

## Warum QUIC?
TCP genügt vielen Performance-Anforderungen nicht mehr (Verbindungsaufbau, Latenz, Fehlerkorrektur). QUIC:
- **schneller Verbindungsaufbau** inkl. Austausch der Security-Informationen,
- **eingebaute Verschlüsselung**,
- **Zuverlässigkeit pro Stream** (ein blockierter Stream bremst die anderen nicht),
- Optimierung für **HTTPS**: parallele, unabhängige Ströme pro Anfrage,
- **Multipath** (wie MPTCP).

Weil QUIC auf Layer 5 sitzt, kann es **unabhängig vom Betriebssystem** weiterentwickelt werden.

## Verwandte Notes
[[6 Transportschicht/UDP\|UDP]] · [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle bei TCP]] · [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/UDP\|⬅️ UDP]]  ·  [[6 Transportschicht/Socket-API\|Socket-API ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
