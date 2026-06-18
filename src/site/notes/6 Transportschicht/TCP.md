---
{"dg-publish":true,"permalink":"/6-transportschicht/tcp/","tags":["computernetworks","transport"],"dg-note-properties":{"tags":["computernetworks","transport"],"aliases":["TCP","Transmission Control Protocol","Segment"]}}
---


# TCP

> [!abstract] Auf einen Blick
> **TCP (Transmission Control Protocol)** ist **zuverlässig**, **verbindungsorientiert**, **unicast**, **vollduplex** und **byte-orientiert**. Es ist das Protokoll der meisten Internet-Anwendungen und gleicht die Unzuverlässigkeit von [[5 Vermittlungsschicht/IPv4-Paket\|IP]] aus.

## Eigenschaften
- **byte-orientiert:** TCP ignoriert Nachrichtengrenzen und teilt den Strom in **Segmente** (max. ~64 KB), die es an [[5 Vermittlungsschicht/IPv4-Paket\|IP]] übergibt.
- **zuverlässig:** dank SEQ/ACK, Timern und [[6 Transportschicht/Flusskontrolle bei TCP\|Fenstertechnik]].
- **verbindungsorientiert:** mit Auf- und Abbau ([[6 Transportschicht/TCP-Verbindung\|TCP-Verbindung]]).

## Das TCP-Segment (wichtige Felder)
- **Quell-/Ziel-Port** → identifiziert mit den IPs die Verbindung ([[6 Transportschicht/Ports & Sockets\|Ports & Sockets]]).
- **Sequence Number** — Nummer des ersten Bytes des Segments.
- **Acknowledgement Number** — nächstes erwartetes Byte (gültig bei gesetztem ACK-Flag).
- **Flags** — SYN, ACK, FIN, RST (Verbindung), PSH, URG.
- **Window Size** — Empfangsfenster für die [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle]].
- **Checksum** und **Daten** (max. Länge = MSS).

## Verwandte Notes
[[6 Transportschicht/TCP-Verbindung\|TCP-Verbindung]] · [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle bei TCP]] · [[6 Transportschicht/UDP\|UDP]] · [[6 Transportschicht/Ports & Sockets\|Ports & Sockets]] · [[6 Transportschicht/QUIC\|QUIC]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/Ports & Sockets\|⬅️ Ports & Sockets]]  ·  [[6 Transportschicht/TCP-Verbindung\|TCP-Verbindung ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
