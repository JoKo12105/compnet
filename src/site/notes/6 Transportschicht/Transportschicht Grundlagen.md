---
{"dg-publish":true,"permalink":"/6-transportschicht/transportschicht-grundlagen/","tags":["computernetworks","transport"],"dg-note-properties":{"tags":["computernetworks","transport"],"aliases":["Transportschicht","QoS","Ende-zu-Ende"]}}
---


# Transportschicht Grundlagen

> [!abstract] Auf einen Blick
> Die Transportschicht **gehört zum Netz-Nutzer** (nicht zum Netzbetreiber): Sie fängt die Fehler der unsicheren [[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|dritten Schicht]] auf und stellt den Anwendungen erstmals eine **Prozess-zu-Prozess**-Verbindung bereit — bei [[6 Transportschicht/TCP\|TCP]] sogar einen verlässlichen Byte-Strom.

## Dienste
- **Schnittstelle** zur Anwendung (Adressierung über [[6 Transportschicht/Ports & Sockets\|Ports]]),
- **Multiplexing** von einer IP zu mehreren Anwendungen,
- **Fehlerkorrektur** bei unzuverlässiger Netzschicht,
- bessere **Quality of Service (QoS)**.

## Aufgaben (wie die Sicherungsschicht — nur Ende-zu-Ende)
Fehlererkennung (Checksummen, Bestätigungen), Verbindungskontrolle, Daten-Pufferung, Schutz der Daten, **Flusskontrolle**. Weil die Protokolle hier den Fehlern der Netzschicht begegnen, ähneln sie denen der [[2 Link Layer/LLC – Sicherung\|Sicherungsschicht]] — nur eben **Ende-zu-Ende** statt Hop-zu-Hop.

## Verwandte Notes
[[6 Transportschicht/Ports & Sockets\|Ports & Sockets]] · [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/UDP\|UDP]] · [[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]] · [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|⬅️ Übersicht]]  ·  [[6 Transportschicht/Ports & Sockets\|Ports & Sockets ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
