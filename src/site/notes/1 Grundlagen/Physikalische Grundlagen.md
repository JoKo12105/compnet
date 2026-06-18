---
{"dg-publish":true,"permalink":"/1-grundlagen/physikalische-grundlagen/","tags":["computernetworks","grundlagen"],"dg-note-properties":{"tags":["computernetworks","grundlagen"],"aliases":["Nachrichtentechnischer Kanal","Bandbreite","Datenrate","Latenz"]}}
---


# Physikalische Grundlagen

> [!abstract] Auf einen Blick
> Jede Datenübertragung folgt dem Modell **Quelle → (Codierung) → Medium → Ziel**. Das Medium hat physikalische Grenzen: **Bandbreite** und **Übertragungsgeschwindigkeit**. Für die Informatik zählen daraus abgeleitet **Datenrate** (Bit/s) und **Latenz** (Verzögerung).

## Der nachrichtentechnische Kanal
Die Nachricht liegt im Rechner **digital** vor, das übertragene **Signal** ist faktisch immer **analog**. Dazwischen steht ein **Umformer (Codierung)** und das **Übertragungsmedium**.

## Kenngrößen
| Sicht | Kenngröße | Bedeutung |
|---|---|---|
| Physik | **Bandbreite** | nutzbarer Frequenzbereich des Mediums |
| Physik | **Übertragungsgeschwindigkeit** | Ausbreitungsgeschwindigkeit des Signals |
| Informatik | **Datenrate** | übertragene **Bits pro Sekunde** |
| Informatik | **Latenz** | Verzögerung / Verzögerungszeit |

Faustregeln: Die **Datenrate** steigt mit höherer Bandbreite, besserer Codierung und weniger Störungen. Die **Latenz** sinkt mit höherer Übertragungsgeschwindigkeit und weniger Verzögerung an Zwischenstationen.

## Störungen
Signale unterliegen **Dämpfung**, **Verzerrung (Dispersion)** und **Rauschen**. Diese begrenzen Reichweite und Datenrate eines [[1 Grundlagen/Übertragungsmedien & Frequenzen\|Mediums]].

## Verwandte Notes
[[1 Grundlagen/Übertragungsmedien & Frequenzen\|Übertragungsmedien & Frequenzen]] · [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]] · [[3 Access Networks/DSL\|DSL]]

[[1 Grundlagen/1.0 Grundlagen (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[1 Grundlagen/Was sind Netzwerke\|⬅️ Was sind Netzwerke]]  ·  [[1 Grundlagen/Übertragungsmedien & Frequenzen\|Übertragungsmedien & Frequenzen ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
