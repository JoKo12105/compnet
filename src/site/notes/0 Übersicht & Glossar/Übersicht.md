---
{"dg-publish":true,"permalink":"/0 Übersicht & Glossar/Übersicht/","tags":["computernetworks","moc","start","gardenEntry"],"updated":"2026-06-18T21:42:03.358+02:00","dg-note-properties":{"tags":["computernetworks","moc","start","gardenEntry"]}}
---

> [!warning] WIP
> Die Webseite ist aktuell noch Work-In-Progress!
> 
> Daher kann es sein, dass Dinge fehlen, nicht alle Erklärung etc. optimiert sind, 
> HTML-Elemente nicht funktionieren oder nicht richtig eingebunden/formatiert sind 
> und beliebige sonstige Makel!
> 
> >[!info] Tipp
> >Gerne mal ab und zu die Seite neu laden, da ständig Updates hinzu kommen können.

# 🌐 Computer Networks — Kurs & Nachschlagewerk

Diese Website ist **Kurs** und **Nachschlagewerk** zugleich. Jedes Konzept hat seinen eigenen Artikel, Querverweise sind direkt verlinkt, und zentrale Abläufe werden über **interaktive Visualisierungen** Schritt für Schritt erklär- und erfahrbar gemacht.

> [!tip] Bedienung
> Klicke in der Roadmap eine Karte an, um die Unterthemen zu sehen. In den interaktiven Elementen führen **„Weiter / Zurück"** durch die Schritte.

<!-- viz:roadmap -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>🌐 Computer Networks — Roadmap</title><style>
*{box-sizing:border-box}
body{margin:0;padding:26px 14px;background:transparent;font-family:&quot;Segoe UI&quot;,&quot;Trebuchet MS&quot;,sans-serif;color:rgb(30,36,48)}
.stepper,.widget{
  --bg:rgb(244,239,230); --panel:rgb(255,253,248); --ink:rgb(30,36,48); --muted:rgb(95,107,122); --line:rgb(207,197,180);
  --accent:rgb(37,73,184); --success:rgb(34,129,75);
  --c1:rgb(217,236,255); --c1b:rgb(29,95,167); --c1t:rgb(18,58,99);
  --c2:rgb(216,245,223); --c2b:rgb(47,143,78); --c2t:rgb(29,93,50);
  --c3:rgb(255,228,184); --c3b:rgb(198,122,0); --c3t:rgb(110,67,0);
  --c4:rgb(232,221,255); --c4b:rgb(116,82,199); --c4t:rgb(68,43,127);
  --c5:rgb(217,250,244); --c5b:rgb(22,147,127); --c5t:rgb(13,90,77);
  --c6:rgb(255,217,210); --c6b:rgb(204,90,66); --c6t:rgb(122,46,32);
  --shadow:0 10px 28px rgba(58,40,18,.10);
  max-width:920px;margin:0 auto;padding:24px 18px;border-radius:24px;
  background:transparent;
  box-shadow:none}
h1.viz-title{text-align:center;font-size:19px;margin:0 0 4px;color:rgb(238,242,248)}
.viz-sub{text-align:center;color:rgb(170,182,200);font-size:13.5px;margin:0 0 18px}
.steps-nav{display:flex;gap:9px;justify-content:center;margin-bottom:16px;flex-wrap:wrap}
.step-dot{width:32px;height:32px;border-radius:999px;border:2px solid rgb(201,189,167);background:rgb(255,250,241);color:rgb(106,95,77);font-size:13px;font-weight:700;display:flex;align-items:center;justify-content:center;cursor:pointer;transition:transform .18s,background .18s,color .18s,border-color .18s;box-shadow:0 2px 8px rgba(90,70,40,.08)}
.step-dot:hover{transform:translateY(-1px)}
.step-dot.active{background:var(--accent);border-color:rgb(23,53,140);color:rgb(255,255,255);transform:scale(1.06)}
.step-dot.done{background:var(--success);border-color:rgb(23,99,56);color:rgb(255,255,255)}
.step-label{text-align:center;font-size:14px;color:rgb(227,233,242);margin-bottom:16px;min-height:20px;font-weight:700}
.diagram-frame{max-width:780px;margin:0 auto;padding:16px;border-radius:22px;background:var(--panel);border:1px solid rgb(232,222,206);box-shadow:inset 0 1px 0 rgba(255,255,255,.8)}
svg{display:block;width:100%;height:auto}
.th{font-size:15px;font-weight:800}
.ts{font-size:12px;font-weight:600}
.tm{font-size:11px;font-weight:600}
.arr{stroke-width:2.2;fill:none}
.card rect{stroke-width:2}
.c1 rect,rect.c1{fill:var(--c1);stroke:var(--c1b)} .c1 text,text.c1{fill:var(--c1t)}
.c2 rect,rect.c2{fill:var(--c2);stroke:var(--c2b)} .c2 text,text.c2{fill:var(--c2t)}
.c3 rect,rect.c3{fill:var(--c3);stroke:var(--c3b)} .c3 text,text.c3{fill:var(--c3t)}
.c4 rect,rect.c4{fill:var(--c4);stroke:var(--c4b)} .c4 text,text.c4{fill:var(--c4t)}
.c5 rect,rect.c5{fill:var(--c5);stroke:var(--c5b)} .c5 text,text.c5{fill:var(--c5t)}
.c6 rect,rect.c6{fill:var(--c6);stroke:var(--c6b)} .c6 text,text.c6{fill:var(--c6t)}
.step-description{max-width:780px;margin:16px auto 0;padding:16px 20px;border-radius:18px;background:linear-gradient(180deg,rgb(255,249,239) 0%,rgb(255,245,227) 100%);border:1px solid rgb(239,214,168);color:var(--ink);font-size:14.5px;line-height:1.6;box-shadow:0 8px 24px rgba(115,82,20,.08);animation:slide-in .28s ease}
.step-description b{color:rgb(124,74,0)}
.btn-row{display:flex;justify-content:center;gap:12px;margin-top:16px}
.btn{padding:10px 22px;border-radius:999px;border:1.5px solid rgb(210,195,170);background:rgb(255,249,239);color:var(--ink);font-size:13px;font-weight:700;cursor:pointer;transition:transform .15s,background .15s,border-color .15s}
.btn:hover:not(:disabled){background:rgb(255,241,211);transform:translateY(-1px)}
.btn.primary{background:var(--accent);color:rgb(255,255,255);border-color:rgb(23,53,140)}
.btn.primary:hover:not(:disabled){background:rgb(31,62,157)}
.btn:disabled{opacity:.45;cursor:not-allowed}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.6;transform:scale(1.02)}}
@keyframes slide-in{from{transform:translateY(8px);opacity:0}to{transform:translateY(0);opacity:1}}
.blinking{animation:pulse 1.15s ease-in-out infinite;transform-origin:center}
.rm-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:14px}
.rm-card{border-radius:18px;padding:16px 18px;border:2px solid;cursor:pointer;transition:transform .18s,box-shadow .18s;box-shadow:0 6px 18px rgba(60,45,20,.08)}
.rm-card:hover{transform:translateY(-3px);box-shadow:0 12px 28px rgba(60,45,20,.16)}
.rm-card h2{margin:0 0 6px;font-size:16px;display:flex;align-items:center;gap:8px}
.rm-num{display:inline-flex;width:26px;height:26px;border-radius:50%;align-items:center;justify-content:center;font-size:13px;font-weight:800;color:rgb(255,255,255)}
.rm-card p{margin:0;font-size:12.5px;color:rgb(95,107,122);line-height:1.5}
.rm-tags{margin-top:10px;display:none;flex-wrap:wrap;gap:6px}
.rm-card.open .rm-tags{display:flex}
.rm-tag{font-size:11px;font-weight:600;background:rgba(255,255,255,.65);border:1px solid rgb(207,197,180);border-radius:999px;padding:3px 9px}
.k1{background:var(--c1);border-color:var(--c1b)} .k1 .rm-num{background:var(--c1b)}
.k2{background:var(--c2);border-color:var(--c2b)} .k2 .rm-num{background:var(--c2b)}
.k3{background:var(--c3);border-color:var(--c3b)} .k3 .rm-num{background:var(--c3b)}
.k4{background:var(--c4);border-color:var(--c4b)} .k4 .rm-num{background:var(--c4b)}
.k5{background:var(--c5);border-color:var(--c5b)} .k5 .rm-num{background:var(--c5b)}
.k6{background:var(--c6);border-color:var(--c6b)} .k6 .rm-num{background:var(--c6b)}
.rm-hint{text-align:center;color:rgb(170,182,200);font-size:12.5px;margin-top:18px}
</style></head>
<body><div class=&quot;widget&quot;>
<h1 class=&quot;viz-title&quot;>🌐 Computer Networks — Roadmap</h1>
<p class=&quot;viz-sub&quot;>Klicke eine Karte, um die Unterthemen einzublenden</p>
<div class=&quot;rm-grid&quot; id=&quot;grid&quot;></div>
<p class=&quot;rm-hint&quot;>Teil I: Grundlagen (1–2) · Teil II: Netz-Typen (3–4) · Teil III: Übergreifende Infrastruktur (5–6)</p>
</div>
<script>
const topics=[
 {n:1,c:&quot;k1&quot;,t:&quot;Grundlagen&quot;,d:&quot;Was Netzwerke leisten: Medien &amp; Signale, das Schichtenmodell, Protokolle, Geräte, Aufbau des Internets.&quot;,tags:[&quot;Netzwerk-Begriff&quot;,&quot;Medien &amp; Bandbreite&quot;,&quot;Schichtenmodell&quot;,&quot;Encapsulation&quot;,&quot;Protokolle&quot;,&quot;AS &amp; Tiers&quot;]},
 {n:2,c:&quot;k2&quot;,t:&quot;Link Layer&quot;,d:&quot;Die Sicherungsschicht: Frames, Fehlerbehandlung (ARQ/FEC) und der Medienzugang (MAC).&quot;,tags:[&quot;LLC &amp; Frames&quot;,&quot;ARQ / FEC&quot;,&quot;MAC&quot;,&quot;Multiplexing&quot;,&quot;Random Access&quot;,&quot;Switching&quot;]},
 {n:3,c:&quot;k3&quot;,t:&quot;Access Networks&quot;,d:&quot;Der Zugang vieler Teilnehmer: DSL, Ethernet, WLAN, Mobilfunk (1G–5G), IoT &amp; Bluetooth.&quot;,tags:[&quot;DSL&quot;,&quot;Ethernet / CSMA/CD&quot;,&quot;WLAN / CSMA/CA&quot;,&quot;Mobilfunk&quot;,&quot;IoT&quot;,&quot;Bluetooth&quot;]},
 {n:4,c:&quot;k4&quot;,t:&quot;Backbone Networks&quot;,d:&quot;Das Rückgrat: Glasfaser, SONET/SDH, DWDM (Wellenlängen-Multiplexing), Überseekabel, DOCSIS.&quot;,tags:[&quot;Glasfaser&quot;,&quot;SONET/SDH&quot;,&quot;DWDM&quot;,&quot;Überseekabel&quot;,&quot;DOCSIS&quot;]},
 {n:5,c:&quot;k5&quot;,t:&quot;Vermittlungsschicht (L3)&quot;,d:&quot;Weg-Finden über Netze hinweg: Routing &amp; Forwarding, IP-Adressen/CIDR, IPv4-Paket, ARP, DHCP, IPv6.&quot;,tags:[&quot;Routing/Forwarding&quot;,&quot;IP &amp; CIDR&quot;,&quot;Subnetze&quot;,&quot;Longest Prefix Match&quot;,&quot;ARP / DHCP&quot;,&quot;IPv6&quot;]},
 {n:6,c:&quot;k6&quot;,t:&quot;Transportschicht (L4)&quot;,d:&quot;Prozess-zu-Prozess: Ports &amp; Sockets, TCP (Handshake, Flusskontrolle), UDP, QUIC.&quot;,tags:[&quot;Ports &amp; Sockets&quot;,&quot;TCP-Handshake&quot;,&quot;Flusskontrolle&quot;,&quot;UDP&quot;,&quot;QUIC&quot;,&quot;Socket-API&quot;]}
];
const grid=document.getElementById(&quot;grid&quot;);
topics.forEach(o=>{const div=document.createElement(&quot;div&quot;);div.className=&quot;rm-card &quot;+o.c;
 div.innerHTML=`<h2><span class=&quot;rm-num&quot;>${o.n}</span>${o.t}</h2><p>${o.d}</p><div class=&quot;rm-tags&quot;>${o.tags.map(t=>`<span class=&quot;rm-tag&quot;>${t}</span>`).join(&quot;&quot;)}</div>`;
 div.onclick=()=>div.classList.toggle(&quot;open&quot;);grid.appendChild(div);});
</script></body></html>" width="100%" height="820" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:roadmap -->

## 🧭 Die drei Teile der Vorlesung

### Teil I — Die Grundlagen
1. [[1 Grundlagen/1.0 Grundlagen (Übersicht)\|Grundlagen]] — Medien & Signale, Schichtenmodell, Protokolle, Geräte, Aufbau des Internets
2. [[2 Link Layer/2.0 Link Layer (Übersicht)\|Link Layer]] — Frames, Fehlerbehandlung (ARQ/FEC), Medienzugang (MAC)

### Teil II — Typen von Netzwerken
3. [[3 Access Networks/3.0 Access Networks (Übersicht)\|Access Networks]] — DSL, Ethernet, WLAN, Mobilfunk, IoT
4. [[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|Backbone Networks]] — Glasfaser, SONET/SDH, DWDM, DOCSIS

### Teil III — Übergreifende Infrastruktur
5. [[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|Vermittlungsschicht (Layer 3)]] — Routing, IP-Adressen, CIDR, ARP, DHCP, IPv6
6. [[6 Transportschicht/6.0 Transportschicht (Übersicht)\|Transportschicht (Layer 4)]] — Ports & Sockets, TCP, UDP, QUIC

## 🔑 Schnellzugriff: zentrale Konzepte

Grundlagen: [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]] · [[1 Grundlagen/Protokolle\|Protokolle]] · [[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte]] · [[1 Grundlagen/Aufbau des Internets\|Aufbau des Internets]]
Zugang: [[3 Access Networks/Ethernet\|Ethernet]] · [[3 Access Networks/WLAN\|WLAN]] · [[3 Access Networks/Mobilfunk\|Mobilfunk]]
Internet (L3): [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[5 Vermittlungsschicht/Longest Prefix Match\|Longest Prefix Match]] · [[5 Vermittlungsschicht/ARP\|ARP]] · [[5 Vermittlungsschicht/DHCP\|DHCP]] · [[5 Vermittlungsschicht/IPv6\|IPv6]]
Transport (L4): [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/TCP-Verbindung\|TCP-Verbindung]] · [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle bei TCP]] · [[6 Transportschicht/UDP\|UDP]]

## 📖 Wie lese ich diese Website?

Für die **Klausurvorbereitung** empfiehlt sich der Weg von oben nach unten (Kapitel 1 → 6) entlang des **Schichtenmodells** — von unten (Bits & Medien) nach oben (Anwendungen). Als **Nachschlagewerk** kannst du über den Schnellzugriff oder das [[0 Übersicht & Glossar/Glossar\|Glossar]] direkt zu einem Begriff springen.
Jeder Artikel beginnt mit einer Kurzdefinition („Auf einen Blick"), gefolgt von Details und — wo sinnvoll — einer interaktiven Visualisierung.

## 🔗 Links to visit
+ [YouTube / Computer Networking (Deepdive)](https://youtu.be/6G14NrjekLQ?si=-qRlUVpDmNXeRP35)
	+ Nicht wirklich ein „Deepdive“ (es sind 15 min) hat aber gute Erklärungen
+ [YouTube / Five Layers Model - part 1](https://www.youtube.com/watch?v=Q3qqd6Y2FbQ)
  [YouTube / Five Layers Model - part 2](https://www.youtube.com/watch?v=LYH4DwydVAM&t=194s)
	+ Basierend auf Marias Empfehlung
	  > "Großartige Videos imo zum Fünf Layer Model"
+ [YouTube / screw it... let's rebuild the ENTIRE Internet](https://youtu.be/HRa31C7zfzk?si=2R2cmH1cTccsnOk8) 
	+ **⚠️Content Warning⚠️:** französisch 😡

+ [Betriebssysteme-Website](https://betriebssysteme.vercel.app)
	+ Meine andere Website zum Thema *Betriebssysteme*, falls sich jemand nochmal darüber informieren möchte

---

<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid rgb(198,122,0);background:linear-gradient(180deg,rgb(255,224,138),rgb(255,206,71));color:rgb(90,61,0);text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">BUY ME A COFFEE ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Websites zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
