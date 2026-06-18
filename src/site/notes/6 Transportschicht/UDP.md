---
{"dg-publish":true,"permalink":"/6-transportschicht/udp/","tags":["computernetworks","transport"],"dg-note-properties":{"tags":["computernetworks","transport"],"aliases":["UDP","User Datagram Protocol"]}}
---


# UDP

> [!abstract] Auf einen Blick
> **UDP (User Datagram Protocol)** ist **verbindungslos**, **unzuverlässig** und hat **keine Flusskontrolle**. Es erweitert ein [[5 Vermittlungsschicht/IPv4-Paket\|IP-Paket]] nur um Quell-/Ziel-Port, Länge und Checksumme — minimaler Overhead.

## Wann UDP?
Für kurze **Statusmeldungen** und **Abfrage-Situationen**, bei denen ein Verbindungsaufbau zu teuer wäre oder Verzögerung schlimmer ist als Verlust — z. B. [[5 Vermittlungsschicht/DHCP\|DHCP]], DNS, Streaming, Spiele.

Bei UDP genügt das **2-Tupel** (Ziel-IP, Ziel-Port) zur Identifikation eines Sockets ([[6 Transportschicht/Ports & Sockets\|Ports & Sockets]]). Anders als [[6 Transportschicht/TCP\|TCP]] gibt es keinen Handshake, keine Reihenfolgegarantie und keine Wiederholung.

> [!info] Weitere Transportprotokolle
> Neben TCP und UDP gibt es SCTP, RTP (Echtzeit) und – besonders relevant – [[6 Transportschicht/QUIC\|QUIC]].

## Verwandte Notes
[[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/QUIC\|QUIC]] · [[6 Transportschicht/Ports & Sockets\|Ports & Sockets]] · [[5 Vermittlungsschicht/DHCP\|DHCP]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/Flusskontrolle bei TCP\|⬅️ Flusskontrolle bei TCP]]  ·  [[6 Transportschicht/QUIC\|QUIC ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
