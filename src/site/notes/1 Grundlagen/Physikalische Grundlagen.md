---
{"dg-publish":true,"permalink":"/1 Grundlagen/Physikalische Grundlagen/","tags":["computernetworks","grundlagen"],"updated":"2026-06-18T15:04:04.151+02:00","dg-note-properties":{"tags":["computernetworks","grundlagen"],"aliases":["Nachrichtentechnischer Kanal","Bandbreite","Datenrate","Latenz"]}}
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