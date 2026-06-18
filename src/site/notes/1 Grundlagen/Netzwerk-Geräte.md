---
{"dg-publish":true,"permalink":"/1-grundlagen/netzwerk-geraete/","tags":["computernetworks","grundlagen"],"dg-note-properties":{"tags":["computernetworks","grundlagen"],"aliases":["Geräte","Hub","Switch","Router","Gateway","Middlebox"]}}
---


# Netzwerk-Geräte

> [!abstract] Auf einen Blick
> Geräte werden nach der **höchsten Schicht** eingeordnet, deren Protokolle sie „verstehen“. Ein Gerät operiert auf **Ebene n**, wenn es die Protokolle bis Ebene n versteht.

## Geräte nach Ebenen
| Ebene | Gerät | Aufgabe |
|---|---|---|
| 1 | **Hub** | reine **Signalverstärkung** (alle Ports sehen alles) |
| 2 | **Switch** | verknüpft Netzwerk-Segmente, leitet anhand der **MAC-Adresse** gezielt weiter → [[3 Access Networks/Ethernet\|Ethernet]] |
| 3 | **Router** | findet den Weg zwischen **Subnetzen** anhand der **IP-Adresse** → [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] |
| 4+ | **Gateway / Middlebox** | diverse Funktionen, z. B. Sicherheit, Übersetzung (NAT, Firewall) |

Ein **Switch** vermeidet Kollisionen, indem er Frames nur an den Zielport schickt (dediziertes Medium statt Shared Medium). Ein **Router** arbeitet mit Paketen und entscheidet per [[5 Vermittlungsschicht/Longest Prefix Match\|Longest Prefix Match]], wohin ein Paket geht.

## Verwandte Notes
[[1 Grundlagen/Schichtenmodell\|Schichtenmodell]] · [[3 Access Networks/Ethernet\|Ethernet]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[1 Grundlagen/Aufbau des Internets\|Aufbau des Internets]]

[[1 Grundlagen/1.0 Grundlagen (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[1 Grundlagen/Protokolle\|⬅️ Protokolle]]  ·  [[1 Grundlagen/Aufbau des Internets\|Aufbau des Internets ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
