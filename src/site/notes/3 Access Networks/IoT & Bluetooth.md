---
{"dg-publish":true,"permalink":"/3 Access Networks/IoT & Bluetooth/","tags":["computernetworks","access"],"updated":"2026-06-18T23:37:19.464+02:00","dg-note-properties":{"permalink":"/3 Access Networks/IoT & Bluetooth/","tags":["computernetworks","access"],"updated":"2026-06-18T22:20:28.669+02:00"}}
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
- Punkt-zu-Punkt und vermaschte Ad-hoc-Netze
- feste 48-Bit-Geräte-ID (MAC-Adresse)
- dynamisches **Master-Slave**: 1 Master, max. 7 Slaves; der Master vergibt Zeitschlitze (TDM)
- verbindungslos (**BLE**) oder verbindungsorientiert
- Störungsbehandlung durch schnellen **Frequenzwechsel**

## Verwandte Themen
[[3 Access Networks/Mobilfunk\|Mobilfunk]] · [[3 Access Networks/WLAN\|WLAN]] · [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]]

[[3 Access Networks/3.0 Access Networks (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[3 Access Networks/Mobilfunk\|⬅️ Mobilfunk]]  ·  [[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|Kapitel 4: Backbone ➡️]]