---
{"dg-publish":true,"permalink":"/3-access-networks/io-t-and-bluetooth/","tags":["computernetworks","access"],"dg-note-properties":{"tags":["computernetworks","access"],"aliases":["IoT","Internet of Things","Bluetooth","BLE","Zigbee","LoRaWAN"]}}
---


# IoT & Bluetooth

> [!abstract] Auf einen Blick
> **IoT**-Umgebungen bestehen aus **vielen, kleinen, energiearmen** Systemen, oft als **ad-hoc / Mesh**-Netze ohne zentrale Struktur. Ziel: hohe Flexibilität und leichte Inbetriebnahme — Interoperabilität war lange zweitrangig.

## Typische Protokolle
- **Kabelgebunden:** SmartHome (BACnet, KNX), Industrie (Profibus, CANBUS, Industrial Ethernet).
- **Funk:** WiFi/[[3 Access Networks/WLAN\|WLAN]], LoRaWAN, [[3 Access Networks/Mobilfunk\|NB-IoT (LTE/5G)]]; SmartHome: **Bluetooth/BLE**, EnOcean, Thread, Zigbee, Z-Wave.

> [!note] Matter
> **Matter** liegt im [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]] höher (Layer 5) und setzt auf darunterliegende Funktechniken auf.

## Spezialfall Bluetooth
Funk-Protokoll für kurze Reichweiten (< 40 m) im lizenzfreien 2,4-GHz-Band:
- Punkt-zu-Punkt und vermaschte Ad-hoc-Netze,
- feste 48-Bit-Geräte-ID (MAC-Adresse),
- dynamisches **Master-Slave**: 1 Master, max. 7 Slaves; der Master vergibt Zeitschlitze (TDM),
- verbindungslos (**BLE**) oder verbindungsorientiert,
- Störungsbehandlung durch schnellen **Frequenzwechsel**.

## Verwandte Notes
[[3 Access Networks/Mobilfunk\|Mobilfunk]] · [[3 Access Networks/WLAN\|WLAN]] · [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]]

[[3 Access Networks/3.0 Access Networks (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[3 Access Networks/Mobilfunk\|⬅️ Mobilfunk]]  ·  [[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|Kapitel 4: Backbone ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
