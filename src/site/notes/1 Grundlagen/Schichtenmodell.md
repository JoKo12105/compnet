---
{"dg-publish":true,"permalink":"/1 Grundlagen/Schichtenmodell/","tags":["computernetworks","grundlagen"],"updated":"2026-06-18T18:01:53.295+02:00","dg-note-properties":{"tags":["computernetworks","grundlagen"],"aliases":["Schichten","OSI","Referenzmodell","Encapsulation","Tunneling","Dienst","Interface"]}}
---


# Schichtenmodell

> [!abstract] Auf einen Blick
> Die Komplexität von Netzwerken wird **zerlegt und delegiert**: Module werden nach „Hardware-Nähe“ vertikal in **Schichten** gestapelt. Jede Schicht **nutzt den Dienst der tieferen** und **stellt der höheren einen Dienst bereit**. Gleiche Schichten beider Seiten sprechen dasselbe **Protokoll** → ein **Protokoll-Stack**.

## Warum Schichten?
Ohne Schichtung müsste man die Anwendung für jedes neue Medium neu schreiben, alle Fehlerfälle in der Anwendung behandeln und sämtliche Netzwerk-Details kennen. Die Schichtung verbirgt die Implementierung und erlaubt die freie **Kombination** von Medien, Techniken und Standards.

## Drei zentrale Begriffe
- **Dienst** — Gruppe von Operationen, die eine Schicht der höheren bereitstellt (Implementierung bleibt verborgen).
- **Interface** — die Sicht auf den Dienst von oben (abstrahiert von der Implementierung).
- **Protokoll** — Form, Ordnung und Konventionen der Kommunikation zwischen **gleichen** Schichten der beiden Partner. → [[1 Grundlagen/Protokolle\|Protokolle]]

Logisch kommuniziert jede Schicht **nur mit der gleichen Schicht** der Gegenseite; physisch nur mit der höheren/tieferen Schicht der **eigenen** Seite. Als Referenz diente lange das **OSI-Modell**; praxisnäher ist das **Tanenbaum-Referenzmodell**, das die Struktur des heutigen Internets gut abbildet.

## Encapsulation
Beim Senden wird eine Dateneinheit der Ebene *n* in eine der Ebene *n−1* **verpackt** (Encapsulation), beim Empfangen wieder **entpackt**. Werden Dateneinheiten stattdessen in eine **gleich hohe oder höhere** Schicht verpackt, spricht man von **Tunneling** (häufig im Security-Umfeld). Genau dieser Vorgang Schritt für Schritt:

<!-- viz:schichtenmodell -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>Encapsulation im Schichtenmodell</title><style>
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
  background:radial-gradient(circle at top left,rgba(255,255,255,.9),transparent 32%),linear-gradient(180deg,rgb(248,244,236) 0%,var(--bg) 100%);
  box-shadow:var(--shadow)}
h1.viz-title{text-align:center;font-size:19px;margin:0 0 4px}
.viz-sub{text-align:center;color:var(--muted);font-size:13.5px;margin:0 0 18px}
.steps-nav{display:flex;gap:9px;justify-content:center;margin-bottom:16px;flex-wrap:wrap}
.step-dot{width:32px;height:32px;border-radius:999px;border:2px solid rgb(201,189,167);background:rgb(255,250,241);color:rgb(106,95,77);font-size:13px;font-weight:700;display:flex;align-items:center;justify-content:center;cursor:pointer;transition:transform .18s,background .18s,color .18s,border-color .18s;box-shadow:0 2px 8px rgba(90,70,40,.08)}
.step-dot:hover{transform:translateY(-1px)}
.step-dot.active{background:var(--accent);border-color:rgb(23,53,140);color:rgb(255,255,255);transform:scale(1.06)}
.step-dot.done{background:var(--success);border-color:rgb(23,99,56);color:rgb(255,255,255)}
.step-label{text-align:center;font-size:14px;color:var(--ink);margin-bottom:16px;min-height:20px;font-weight:700}
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
</style></head>
<body><div class=&quot;stepper&quot;>
<h1 class=&quot;viz-title&quot;>Encapsulation im Schichtenmodell</h1>
<p class=&quot;viz-sub&quot;>Wie eine Nachricht beim Senden Schicht für Schicht „eingepackt“ wird</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 418&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>Encapsulation im Schichtenmodell</title>
<defs>
  <marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;6&quot; markerHeight=&quot;6&quot; orient=&quot;auto-start-reverse&quot;>
    <path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/>
  </marker>
</defs>
<g id=&quot;lyr5&quot; class=&quot;c1 card&quot;><rect x=&quot;24&quot; y=&quot;20&quot; width=&quot;186&quot; height=&quot;44&quot; rx=&quot;11&quot;/>
  <text class=&quot;th&quot; x=&quot;117&quot; y=&quot;42&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>5 · Anwendung</text></g>
<g id=&quot;lyr4&quot; class=&quot;c2 card&quot;><rect x=&quot;24&quot; y=&quot;74&quot; width=&quot;186&quot; height=&quot;44&quot; rx=&quot;11&quot;/>
  <text class=&quot;th&quot; x=&quot;117&quot; y=&quot;96&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>4 · Transport</text></g>
<g id=&quot;lyr3&quot; class=&quot;c3 card&quot;><rect x=&quot;24&quot; y=&quot;128&quot; width=&quot;186&quot; height=&quot;44&quot; rx=&quot;11&quot;/>
  <text class=&quot;th&quot; x=&quot;117&quot; y=&quot;150&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>3 · Vermittlung</text></g>
<g id=&quot;lyr2&quot; class=&quot;c4 card&quot;><rect x=&quot;24&quot; y=&quot;182&quot; width=&quot;186&quot; height=&quot;44&quot; rx=&quot;11&quot;/>
  <text class=&quot;th&quot; x=&quot;117&quot; y=&quot;204&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>2 · Sicherung</text></g>
<g id=&quot;lyr1&quot; class=&quot;c5 card&quot;><rect x=&quot;24&quot; y=&quot;236&quot; width=&quot;186&quot; height=&quot;44&quot; rx=&quot;11&quot;/>
  <text class=&quot;th&quot; x=&quot;117&quot; y=&quot;258&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>1 · Bitübertragung</text></g>
<line x1=&quot;117&quot; y1=&quot;64&quot; x2=&quot;117&quot; y2=&quot;74&quot; stroke=&quot;rgb(138,122,94)&quot; stroke-width=&quot;2&quot; marker-end=&quot;url(#arrow)&quot;/>
<line x1=&quot;117&quot; y1=&quot;118&quot; x2=&quot;117&quot; y2=&quot;128&quot; stroke=&quot;rgb(138,122,94)&quot; stroke-width=&quot;2&quot; marker-end=&quot;url(#arrow)&quot;/>
<line x1=&quot;117&quot; y1=&quot;172&quot; x2=&quot;117&quot; y2=&quot;182&quot; stroke=&quot;rgb(138,122,94)&quot; stroke-width=&quot;2&quot; marker-end=&quot;url(#arrow)&quot;/>
<line x1=&quot;117&quot; y1=&quot;226&quot; x2=&quot;117&quot; y2=&quot;236&quot; stroke=&quot;rgb(138,122,94)&quot; stroke-width=&quot;2&quot; marker-end=&quot;url(#arrow)&quot;/>
<text id=&quot;pdu-name&quot; class=&quot;th&quot; x=&quot;455&quot; y=&quot;232&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(30,36,48)&quot;>Daten</text>
<g id=&quot;pdu-ethh&quot; class=&quot;c4 card&quot; opacity=&quot;0&quot;><rect x=&quot;250&quot; y=&quot;258&quot; width=&quot;56&quot; height=&quot;42&quot; rx=&quot;8&quot;/>
  <text class=&quot;tm&quot; x=&quot;278&quot; y=&quot;279&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>MAC</text></g>
<g id=&quot;pdu-ip&quot; class=&quot;c3 card&quot; opacity=&quot;0&quot;><rect x=&quot;307&quot; y=&quot;258&quot; width=&quot;56&quot; height=&quot;42&quot; rx=&quot;8&quot;/>
  <text class=&quot;tm&quot; x=&quot;335&quot; y=&quot;279&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>IP</text></g>
<g id=&quot;pdu-tcp&quot; class=&quot;c2 card&quot; opacity=&quot;0&quot;><rect x=&quot;364&quot; y=&quot;258&quot; width=&quot;56&quot; height=&quot;42&quot; rx=&quot;8&quot;/>
  <text class=&quot;tm&quot; x=&quot;392&quot; y=&quot;279&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>TCP</text></g>
<g id=&quot;pdu-data&quot; class=&quot;c1 card&quot; opacity=&quot;0&quot;><rect x=&quot;421&quot; y=&quot;258&quot; width=&quot;150&quot; height=&quot;42&quot; rx=&quot;8&quot;/>
  <text class=&quot;ts&quot; x=&quot;496&quot; y=&quot;279&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Nutzdaten</text></g>
<g id=&quot;pdu-etht&quot; class=&quot;c4 card&quot; opacity=&quot;0&quot;><rect x=&quot;572&quot; y=&quot;258&quot; width=&quot;50&quot; height=&quot;42&quot; rx=&quot;8&quot;/>
  <text class=&quot;tm&quot; x=&quot;597&quot; y=&quot;279&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>CRC</text></g>
<line id=&quot;line-down&quot; x1=&quot;455&quot; y1=&quot;300&quot; x2=&quot;455&quot; y2=&quot;330&quot; stroke=&quot;rgb(138,122,94)&quot; stroke-width=&quot;2&quot; stroke-dasharray=&quot;5 4&quot; marker-end=&quot;url(#arrow)&quot; opacity=&quot;0&quot;/>
<rect x=&quot;250&quot; y=&quot;334&quot; width=&quot;372&quot; height=&quot;34&quot; rx=&quot;9&quot; fill=&quot;rgb(238,231,216)&quot; stroke=&quot;rgb(207,197,180)&quot;/>
<text class=&quot;ts&quot; x=&quot;436&quot; y=&quot;351&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(95,107,122)&quot;>Übertragungsmedium</text>
<g id=&quot;pdu-bits&quot; opacity=&quot;0&quot;><text class=&quot;tm&quot; x=&quot;436&quot; y=&quot;351&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(22,147,127)&quot; font-family=&quot;monospace&quot;>0101 1100 1011 0100 1110 0011</text></g>
<g id=&quot;arrow-tx&quot; opacity=&quot;0&quot;><line x1=&quot;270&quot; y1=&quot;386&quot; x2=&quot;600&quot; y2=&quot;386&quot; class=&quot;arr&quot; stroke=&quot;rgb(22,147,127)&quot; marker-end=&quot;url(#arrow)&quot;/>
  <text class=&quot;ts&quot; x=&quot;435&quot; y=&quot;402&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(22,147,127)&quot;>Signal zum Empfänger</text></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Anwendung übergibt Nutzdaten&quot;, &quot;blink&quot;: [&quot;lyr5&quot;], &quot;show&quot;: [&quot;pdu-data&quot;], &quot;hide&quot;: [&quot;pdu-tcp&quot;, &quot;pdu-ip&quot;, &quot;pdu-ethh&quot;, &quot;pdu-etht&quot;, &quot;pdu-bits&quot;, &quot;line-down&quot;, &quot;arrow-tx&quot;], &quot;set&quot;: [[&quot;pdu-name&quot;, &quot;Daten (Nachricht)&quot;\|&quot;pdu-name&quot;, &quot;Daten (Nachricht)&quot;]], &quot;html&quot;: &quot;<b>Schritt 1 — Anwendung (L5):</b> Eine Anwendung (z. B. ein Browser) erzeugt Nutzdaten und übergibt sie an die Transportschicht.&quot;}, {&quot;label&quot;: &quot;Transport packt ein → Segment&quot;, &quot;blink&quot;: [&quot;lyr4&quot;], &quot;show&quot;: [&quot;pdu-data&quot;, &quot;pdu-tcp&quot;], &quot;hide&quot;: [&quot;pdu-ip&quot;, &quot;pdu-ethh&quot;, &quot;pdu-etht&quot;, &quot;pdu-bits&quot;, &quot;line-down&quot;, &quot;arrow-tx&quot;], &quot;set&quot;: [[&quot;pdu-name&quot;, &quot;Segment&quot;\|&quot;pdu-name&quot;, &quot;Segment&quot;]], &quot;html&quot;: &quot;<b>Schritt 2 — Transport (L4):</b> Es kommt ein <b>TCP-Header</b> davor (Quell-/Ziel-Port, SEQ/ACK). Aus den Daten wird ein <b>Segment</b>.&quot;}, {&quot;label&quot;: &quot;Vermittlung packt ein → Paket&quot;, &quot;blink&quot;: [&quot;lyr3&quot;], &quot;show&quot;: [&quot;pdu-data&quot;, &quot;pdu-tcp&quot;, &quot;pdu-ip&quot;], &quot;hide&quot;: [&quot;pdu-ethh&quot;, &quot;pdu-etht&quot;, &quot;pdu-bits&quot;, &quot;line-down&quot;, &quot;arrow-tx&quot;], &quot;set&quot;: [[&quot;pdu-name&quot;, &quot;Paket (Datagram)&quot;\|&quot;pdu-name&quot;, &quot;Paket (Datagram)&quot;]], &quot;html&quot;: &quot;<b>Schritt 3 — Vermittlung (L3):</b> Der <b>IP-Header</b> (Quell-/Ziel-IP, TTL) wird ergänzt. Das Ergebnis ist ein <b>Paket</b>, das über Netzgrenzen geroutet werden kann.&quot;}, {&quot;label&quot;: &quot;Sicherung packt ein → Frame&quot;, &quot;blink&quot;: [&quot;lyr2&quot;], &quot;show&quot;: [&quot;pdu-data&quot;, &quot;pdu-tcp&quot;, &quot;pdu-ip&quot;, &quot;pdu-ethh&quot;, &quot;pdu-etht&quot;], &quot;hide&quot;: [&quot;pdu-bits&quot;, &quot;line-down&quot;, &quot;arrow-tx&quot;], &quot;set&quot;: [[&quot;pdu-name&quot;, &quot;Frame&quot;\|&quot;pdu-name&quot;, &quot;Frame&quot;]], &quot;html&quot;: &quot;<b>Schritt 4 — Sicherung (L2):</b> Ein <b>MAC-Header</b> (Quell-/Ziel-MAC) und am Ende eine <b>CRC-Prüfsumme</b> umschließen das Paket. Das ist ein <b>Frame</b>.&quot;}, {&quot;label&quot;: &quot;Bitübertragung → Signal&quot;, &quot;blink&quot;: [&quot;lyr1&quot;], &quot;show&quot;: [&quot;pdu-data&quot;, &quot;pdu-tcp&quot;, &quot;pdu-ip&quot;, &quot;pdu-ethh&quot;, &quot;pdu-etht&quot;, &quot;line-down&quot;, &quot;pdu-bits&quot;], &quot;hide&quot;: [&quot;arrow-tx&quot;], &quot;set&quot;: [[&quot;pdu-name&quot;, &quot;Bitstrom / Signal&quot;\|&quot;pdu-name&quot;, &quot;Bitstrom / Signal&quot;]], &quot;html&quot;: &quot;<b>Schritt 5 — Bitübertragung (L1):</b> Das Frame wird in einen <b>Bitstrom</b> und schließlich in ein physikalisches <b>Signal</b> umgewandelt und auf das Medium gelegt.&quot;}, {&quot;label&quot;: &quot;Übertragung zum Empfänger&quot;, &quot;show&quot;: [&quot;pdu-bits&quot;, &quot;line-down&quot;, &quot;arrow-tx&quot;], &quot;blink&quot;: [&quot;arrow-tx&quot;], &quot;hide&quot;: [], &quot;set&quot;: [[&quot;pdu-name&quot;, &quot;Bitstrom / Signal&quot;\|&quot;pdu-name&quot;, &quot;Bitstrom / Signal&quot;]], &quot;html&quot;: &quot;<b>Schritt 6 — Übertragung:</b> Das Signal läuft über das Medium zum Empfänger (ggf. über mehrere Geräte und Teilnetze hinweg).&quot;}, {&quot;label&quot;: &quot;Decapsulation beim Empfänger&quot;, &quot;show&quot;: [&quot;pdu-data&quot;, &quot;pdu-tcp&quot;, &quot;pdu-ip&quot;, &quot;pdu-ethh&quot;, &quot;pdu-etht&quot;], &quot;hide&quot;: [&quot;pdu-bits&quot;, &quot;arrow-tx&quot;, &quot;line-down&quot;], &quot;blink&quot;: [&quot;lyr1&quot;, &quot;lyr5&quot;], &quot;set&quot;: [[&quot;pdu-name&quot;, &quot;Decapsulation (umgekehrt)&quot;\|&quot;pdu-name&quot;, &quot;Decapsulation (umgekehrt)&quot;]], &quot;html&quot;: &quot;<b>Schritt 7 — Decapsulation:</b> Beim Empfänger läuft alles <b>rückwärts</b>: Jede Schicht entfernt „ihren“ Header (L1→L2→L3→L4) und reicht den Rest nach oben — bis die Anwendung wieder die reinen Nutzdaten sieht. Logisch kommuniziert jede Schicht <b>nur mit der gleichen Schicht der Gegenseite</b>.&quot;}];
let current = 0;
function render(idx){
  const s = steps[idx];
  document.getElementById(&quot;step-label&quot;).textContent = (idx+1)+&quot; / &quot;+steps.length+&quot; — &quot;+s.label;
  document.getElementById(&quot;step-content&quot;).innerHTML = s.html;
  (s.hide||[]).forEach(id=>{const e=document.getElementById(id);if(e){e.style.opacity=&quot;0&quot;;e.classList.remove(&quot;blinking&quot;);}});
  (s.show||[]).forEach(id=>{const e=document.getElementById(id);if(e){e.style.opacity=&quot;1&quot;;e.classList.remove(&quot;blinking&quot;);}});
  (s.blink||[]).forEach(id=>{const e=document.getElementById(id);if(e){e.style.opacity=&quot;1&quot;;e.classList.add(&quot;blinking&quot;);}});
  (s.set||[]).forEach(p=>{const e=document.getElementById(p[0]);if(e){e.textContent=p[1];}});
  document.querySelectorAll(&quot;.step-dot&quot;).forEach((d,i)=>{d.className=&quot;step-dot&quot;+(i===idx?&quot; active&quot;:i<idx?&quot; done&quot;:&quot;&quot;);});
  document.getElementById(&quot;btn-prev&quot;).disabled = idx===0;
  document.getElementById(&quot;btn-next&quot;).disabled = idx===steps.length-1;
  document.getElementById(&quot;btn-next&quot;).textContent = idx===steps.length-1 ? &quot;Fertig&quot; : &quot;Weiter&quot;;
}
function changeStep(d){current=Math.max(0,Math.min(steps.length-1,current+d));render(current);}
const dotsEl=document.getElementById(&quot;dots&quot;);
steps.forEach((_,i)=>{const d=document.createElement(&quot;div&quot;);d.className=&quot;step-dot&quot;;d.textContent=i+1;d.onclick=()=>{current=i;render(i);};dotsEl.appendChild(d);});
render(0);
</script></body></html>" width="100%" height="720" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:schichtenmodell -->

> [!example] PDU-Namen je Schicht
> Transport → **Segment**, Vermittlung → **Paket/Datagram**, Sicherung → **Frame**, Bitübertragung → **Bitstrom/Signal**.

## Verwandte Notes
[[1 Grundlagen/Protokolle\|Protokolle]] · [[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte]] · [[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket]] · [[6 Transportschicht/TCP\|TCP]] · [[3 Access Networks/Ethernet\|Ethernet]]

[[1 Grundlagen/1.0 Grundlagen (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[1 Grundlagen/Übertragungsmedien & Frequenzen\|⬅️ Übertragungsmedien & Frequenzen]]  ·  [[1 Grundlagen/Protokolle\|Protokolle ➡️]]