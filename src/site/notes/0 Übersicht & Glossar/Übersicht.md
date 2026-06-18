---
{"dg-publish":true,"permalink":"/0-uebersicht-and-glossar/uebersicht/","tags":["computernetworks","moc","start","gardenEntry"],"dg-note-properties":{"tags":["computernetworks","moc","start","gardenEntry"]}}
---


# 🌐 Computer Networks — Kurs & Nachschlagewerk

Dieser Vault ist **Kurs** und **Nachschlagewerk** zugleich. Jedes Konzept hat seine eigene Note, Querverweise sind als `[[Links]]` eingebunden, und zentrale Abläufe werden über **interaktive Visualisierungen** Schritt für Schritt erklärbar gemacht.

> [!tip] Bedienung
> Klicke in der Roadmap eine Karte an, um die Unterthemen zu sehen. In den interaktiven Elementen führen **„Weiter / Zurück"** durch die Schritte.

<!-- viz:roadmap -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>🌐 Computer Networks — Roadmap</title><style>
*{box-sizing:border-box}
body{margin:0;padding:26px 14px;background:transparent;font-family:&quot;Segoe UI&quot;,&quot;Trebuchet MS&quot;,sans-serif;color:#1e2430}
.stepper,.widget{
  --bg:#f4efe6; --panel:#fffdf8; --ink:#1e2430; --muted:#5f6b7a; --line:#cfc5b4;
  --accent:#2549b8; --success:#22814b;
  --c1:#d9ecff; --c1b:#1d5fa7; --c1t:#123a63;
  --c2:#d8f5df; --c2b:#2f8f4e; --c2t:#1d5d32;
  --c3:#ffe4b8; --c3b:#c67a00; --c3t:#6e4300;
  --c4:#e8ddff; --c4b:#7452c7; --c4t:#442b7f;
  --c5:#d9faf4; --c5b:#16937f; --c5t:#0d5a4d;
  --c6:#ffd9d2; --c6b:#cc5a42; --c6t:#7a2e20;
  --shadow:0 10px 28px rgba(58,40,18,.10);
  max-width:920px;margin:0 auto;padding:24px 18px;border-radius:24px;
  background:radial-gradient(circle at top left,rgba(255,255,255,.9),transparent 32%),linear-gradient(180deg,#f8f4ec 0%,var(--bg) 100%);
  box-shadow:var(--shadow)}
h1.viz-title{text-align:center;font-size:19px;margin:0 0 4px}
.viz-sub{text-align:center;color:var(--muted);font-size:13.5px;margin:0 0 18px}
.steps-nav{display:flex;gap:9px;justify-content:center;margin-bottom:16px;flex-wrap:wrap}
.step-dot{width:32px;height:32px;border-radius:999px;border:2px solid #c9bda7;background:#fffaf1;color:#6a5f4d;font-size:13px;font-weight:700;display:flex;align-items:center;justify-content:center;cursor:pointer;transition:transform .18s,background .18s,color .18s,border-color .18s;box-shadow:0 2px 8px rgba(90,70,40,.08)}
.step-dot:hover{transform:translateY(-1px)}
.step-dot.active{background:var(--accent);border-color:#17358c;color:#fff;transform:scale(1.06)}
.step-dot.done{background:var(--success);border-color:#176338;color:#fff}
.step-label{text-align:center;font-size:14px;color:var(--ink);margin-bottom:16px;min-height:20px;font-weight:700}
.diagram-frame{max-width:780px;margin:0 auto;padding:16px;border-radius:22px;background:var(--panel);border:1px solid #e8dece;box-shadow:inset 0 1px 0 rgba(255,255,255,.8)}
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
.step-description{max-width:780px;margin:16px auto 0;padding:16px 20px;border-radius:18px;background:linear-gradient(180deg,#fff9ef 0%,#fff5e3 100%);border:1px solid #efd6a8;color:var(--ink);font-size:14.5px;line-height:1.6;box-shadow:0 8px 24px rgba(115,82,20,.08);animation:slide-in .28s ease}
.step-description b{color:#7c4a00}
.btn-row{display:flex;justify-content:center;gap:12px;margin-top:16px}
.btn{padding:10px 22px;border-radius:999px;border:1.5px solid #d2c3aa;background:#fff9ef;color:var(--ink);font-size:13px;font-weight:700;cursor:pointer;transition:transform .15s,background .15s,border-color .15s}
.btn:hover:not(:disabled){background:#fff1d3;transform:translateY(-1px)}
.btn.primary{background:var(--accent);color:#fff;border-color:#17358c}
.btn.primary:hover:not(:disabled){background:#1f3e9d}
.btn:disabled{opacity:.45;cursor:not-allowed}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.6;transform:scale(1.02)}}
@keyframes slide-in{from{transform:translateY(8px);opacity:0}to{transform:translateY(0);opacity:1}}
.blinking{animation:pulse 1.15s ease-in-out infinite;transform-origin:center}

.rm-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:14px}
.rm-card{border-radius:18px;padding:16px 18px;border:2px solid;cursor:pointer;transition:transform .18s,box-shadow .18s;box-shadow:0 6px 18px rgba(60,45,20,.08)}
.rm-card:hover{transform:translateY(-3px);box-shadow:0 12px 28px rgba(60,45,20,.16)}
.rm-card h2{margin:0 0 6px;font-size:16px;display:flex;align-items:center;gap:8px}
.rm-num{display:inline-flex;width:26px;height:26px;border-radius:50%;align-items:center;justify-content:center;font-size:13px;font-weight:800;color:#fff}
.rm-card p{margin:0;font-size:12.5px;color:#5f6b7a;line-height:1.5}
.rm-tags{margin-top:10px;display:none;flex-wrap:wrap;gap:6px}
.rm-card.open .rm-tags{display:flex}
.rm-tag{font-size:11px;font-weight:600;background:rgba(255,255,255,.65);border:1px solid #cfc5b4;border-radius:999px;padding:3px 9px}
.k1{background:var(--c1);border-color:var(--c1b)} .k1 .rm-num{background:var(--c1b)}
.k2{background:var(--c2);border-color:var(--c2b)} .k2 .rm-num{background:var(--c2b)}
.k3{background:var(--c3);border-color:var(--c3b)} .k3 .rm-num{background:var(--c3b)}
.k4{background:var(--c4);border-color:var(--c4b)} .k4 .rm-num{background:var(--c4b)}
.k5{background:var(--c5);border-color:var(--c5b)} .k5 .rm-num{background:var(--c5b)}
.k6{background:var(--c6);border-color:var(--c6b)} .k6 .rm-num{background:var(--c6b)}
.rm-hint{text-align:center;color:#5f6b7a;font-size:12.5px;margin-top:18px}
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
</script></body></html>" width="100%" height="560" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
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

## 📖 Wie lese ich diesen Vault?

Für die **Klausurvorbereitung** empfiehlt sich der Weg von oben nach unten (Kapitel 1 → 6) entlang des **Schichtenmodells** — von unten (Bits & Medien) nach oben (Anwendungen). Als **Nachschlagewerk** kannst du über den Schnellzugriff oder das [[0 Übersicht & Glossar/Glossar\|Glossar]] direkt zu einem Begriff springen.
Jede Note beginnt mit einer Kurzdefinition („Auf einen Blick"), gefolgt von Details und — wo sinnvoll — einer interaktiven Visualisierung.

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
