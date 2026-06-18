---
{"dg-publish":true,"permalink":"/1-grundlagen/protokolle/","tags":["computernetworks","grundlagen"],"dg-note-properties":{"tags":["computernetworks","grundlagen"],"aliases":["Protokoll","verbindungsorientiert","verbindungslos","Multiplexing","Flusskontrolle"]}}
---


# Protokolle

> [!abstract] Auf einen Blick
> Ein **Protokoll** legt **Form, Ordnung und Konventionen** der Kommunikation zwischen Partnern fest: Adressierung, Form der PDUs (z. B. Frames), Fehlerbehandlung, Richtung des Datenflusses und ggf. Flusskontrolle.

## Was ein Protokoll regeln muss
- **Identifikation und Adressierung** der Partner,
- **Form** der Protokoll-Atome (Frames, Pakete, Segmente),
- **Fehlerbehandlung**,
- optional **Verbindungsorientierung**,
- **Richtung** des Datenflusses (simplex, halbduplex, vollduplex),
- oft eine Form von **Multiplexing**,
- optional **Flusskontrolle** (Überlastvermeidung).

Beschrieben werden Protokolle über **zeitlichen Ablauf** (Sequenzdiagramme) und **logische Folge** (Zustände).

## Verbindungsorientiert vs. verbindungslos
| | verbindungsorientiert | verbindungslos |
|---|---|---|
| Aufbau | **Handshake** vor Datenaustausch | kein Handshake |
| Partner | dedizierte Instanzen, Verbindungs-ID | keine dedizierten Partner |
| Einheit | Datenstrom | einzelne **Datagramme** |
| oft gebündelt mit | Zuverlässigkeit, Überlastkontrolle | minimaler Overhead |
| Beispiel | [[6 Transportschicht/TCP\|TCP]] | [[6 Transportschicht/UDP\|UDP]], [[5 Vermittlungsschicht/IPv4-Paket\|IP]] |

## Verwandte Notes
[[1 Grundlagen/Schichtenmodell\|Schichtenmodell]] · [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/UDP\|UDP]] · [[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]] · [[2 Link Layer/Vermittlungsarten\|Vermittlungsarten]]

[[1 Grundlagen/1.0 Grundlagen (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[1 Grundlagen/Schichtenmodell\|⬅️ Schichtenmodell]]  ·  [[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
