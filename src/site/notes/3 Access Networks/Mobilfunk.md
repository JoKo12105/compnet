---
{"dg-publish":true,"permalink":"/3-access-networks/mobilfunk/","tags":["computernetworks","access"],"dg-note-properties":{"tags":["computernetworks","access"],"aliases":["Mobilfunk","GSM","UMTS","LTE","5G","Zelle","Handover"]}}
---


# Mobilfunk

> [!abstract] Auf einen Blick
> **Mobilfunk**-Netze sind in **Zellen** strukturiert und nutzen zentrales **Multiplexing** (Zeit/Frequenz/Code), das jedem Teilnehmer fest zugeteilt wird. Sie durchliefen die Generationen **1G → 5G** mit steigender Datenrate und sinkender Latenz.

## Zellstruktur, Reuse & Handover
<!-- viz:mobilfunk-zellen -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>Mobilfunk – Zellstruktur, Reuse &amp; Handover</title><style>
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
</style></head>
<body><div class=&quot;stepper&quot;>
<h1 class=&quot;viz-title&quot;>Mobilfunk – Zellstruktur, Reuse &amp; Handover</h1>
<p class=&quot;viz-sub&quot;>Warum Zellen? Frequenz-Wiederverwendung und Zellwechsel</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 400&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>Mobilfunk – Zellstruktur, Reuse &amp; Handover</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs><g id=&quot;hex-C&quot; class=&quot;c1&quot;><polygon points=&quot;406.0,200.0 378.0,248.5 322.0,248.5 294.0,200.0 322.0,151.5 378.0,151.5&quot; fill=&quot;var(--c1)&quot; stroke=&quot;var(--c1b)&quot; stroke-width=&quot;2&quot; opacity=&quot;0.9&quot;/></g><g id=&quot;hex-E&quot; class=&quot;c3&quot;><polygon points=&quot;490.0,151.5 462.0,200.0 406.0,200.0 378.0,151.5 406.0,103.0 462.0,103.0&quot; fill=&quot;var(--c3)&quot; stroke=&quot;var(--c3b)&quot; stroke-width=&quot;2&quot; opacity=&quot;0.9&quot;/></g><g id=&quot;hex-F&quot; class=&quot;c2&quot;><polygon points=&quot;490.0,248.5 462.0,297.0 406.0,297.0 378.0,248.5 406.0,200.0 462.0,200.0&quot; fill=&quot;var(--c2)&quot; stroke=&quot;var(--c2b)&quot; stroke-width=&quot;2&quot; opacity=&quot;0.9&quot;/></g><g id=&quot;hex-B&quot; class=&quot;c2&quot;><polygon points=&quot;322.0,151.5 294.0,200.0 238.0,200.0 210.0,151.5 238.0,103.0 294.0,103.0&quot; fill=&quot;var(--c2)&quot; stroke=&quot;var(--c2b)&quot; stroke-width=&quot;2&quot; opacity=&quot;0.9&quot;/></g><g id=&quot;hex-A&quot; class=&quot;c3&quot;><polygon points=&quot;322.0,248.5 294.0,297.0 238.0,297.0 210.0,248.5 238.0,200.0 294.0,200.0&quot; fill=&quot;var(--c3)&quot; stroke=&quot;var(--c3b)&quot; stroke-width=&quot;2&quot; opacity=&quot;0.9&quot;/></g><g id=&quot;hex-T&quot; class=&quot;c2&quot;><polygon points=&quot;406.0,103.0 378.0,151.5 322.0,151.5 294.0,103.0 322.0,54.5 378.0,54.5&quot; fill=&quot;var(--c2)&quot; stroke=&quot;var(--c2b)&quot; stroke-width=&quot;2&quot; opacity=&quot;0.9&quot;/></g><g id=&quot;hex-D&quot; class=&quot;c3&quot;><polygon points=&quot;406.0,297.0 378.0,345.5 322.0,345.5 294.0,297.0 322.0,248.5 378.0,248.5&quot; fill=&quot;var(--c3)&quot; stroke=&quot;var(--c3b)&quot; stroke-width=&quot;2&quot; opacity=&quot;0.9&quot;/></g><g id=&quot;bts&quot;><rect x=&quot;340&quot; y=&quot;166&quot; width=&quot;20&quot; height=&quot;26&quot; rx=&quot;3&quot; fill=&quot;#444&quot; /><line x1=&quot;350&quot; y1=&quot;166&quot; x2=&quot;350&quot; y2=&quot;148&quot; stroke=&quot;#444&quot; stroke-width=&quot;2&quot;/><circle cx=&quot;350&quot; cy=&quot;146&quot; r=&quot;4&quot; fill=&quot;#cc5a42&quot;/></g><g id=&quot;reuse&quot; opacity=&quot;0&quot;><text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;206&quot; text-anchor=&quot;middle&quot;>f1</text><text class=&quot;tm&quot; x=&quot;434.0&quot; y=&quot;157.50257738807144&quot; text-anchor=&quot;middle&quot;>f3</text><text class=&quot;tm&quot; x=&quot;434.0&quot; y=&quot;254.49742261192856&quot; text-anchor=&quot;middle&quot;>f2</text><text class=&quot;tm&quot; x=&quot;266.0&quot; y=&quot;157.50257738807144&quot; text-anchor=&quot;middle&quot;>f2</text><text class=&quot;tm&quot; x=&quot;266.0&quot; y=&quot;254.49742261192856&quot; text-anchor=&quot;middle&quot;>f3</text><text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;109.00515477614287&quot; text-anchor=&quot;middle&quot;>f2</text><text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;302.9948452238571&quot; text-anchor=&quot;middle&quot;>f3</text></g><g id=&quot;ph1&quot; opacity=&quot;0&quot;><circle cx=&quot;350&quot; cy=&quot;220&quot; r=&quot;9&quot; fill=&quot;#2549b8&quot;/><text x=&quot;350&quot; y=&quot;220&quot; font-size=&quot;9&quot; fill=&quot;#fff&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>📱</text></g><g id=&quot;ph2&quot; opacity=&quot;0&quot;><circle cx=&quot;434.0&quot; cy=&quot;248.49742261192856&quot; r=&quot;9&quot; fill=&quot;#2549b8&quot;/><text x=&quot;434.0&quot; y=&quot;248.49742261192856&quot; font-size=&quot;9&quot; fill=&quot;#fff&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>📱</text></g><g id=&quot;ho&quot; opacity=&quot;0&quot;><line x1=&quot;362&quot; y1=&quot;218&quot; x2=&quot;422.0&quot; y2=&quot;242.49742261192856&quot; class=&quot;arr&quot; stroke=&quot;#cc5a42&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;402.0&quot; y=&quot;208&quot; text-anchor=&quot;middle&quot; fill=&quot;#cc5a42&quot;>Handover</text></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Eine Zelle mit Basisstation&quot;, &quot;show&quot;: [&quot;hex-C&quot;, &quot;bts&quot;], &quot;hide&quot;: [&quot;reuse&quot;, &quot;ph1&quot;, &quot;ph2&quot;, &quot;ho&quot;], &quot;html&quot;: &quot;<b>Zelle:</b> Eine <b>Basisstation</b> (bei LTE: eNodeB) versorgt einen räumlichen Bereich — die <b>Zelle</b>. Mobilfunknetze sind in solche Zellen strukturiert.&quot;}, {&quot;label&quot;: &quot;Warum überhaupt Zellen?&quot;, &quot;show&quot;: [&quot;hex-C&quot;, &quot;hex-A&quot;, &quot;hex-B&quot;, &quot;hex-D&quot;, &quot;hex-E&quot;, &quot;hex-F&quot;, &quot;hex-T&quot;, &quot;bts&quot;], &quot;hide&quot;: [&quot;reuse&quot;, &quot;ph1&quot;, &quot;ph2&quot;, &quot;ho&quot;], &quot;blink&quot;: [&quot;hex-C&quot;], &quot;html&quot;: &quot;<b>Begründung:</b> Wegen der starken Abstrahl-Dämpfung (≈ 1/r⁴) dürfen Sender und Empfänger nicht zu weit auseinanderliegen. Viele kleine Zellen bedeuten: <b>geringe Sendeleistung</b>, lange Akkulaufzeit und <b>viele Teilnehmer</b> — aber hohe Aufbaukosten.&quot;}, {&quot;label&quot;: &quot;Frequenz-Wiederverwendung (Reuse)&quot;, &quot;show&quot;: [&quot;hex-C&quot;, &quot;hex-A&quot;, &quot;hex-B&quot;, &quot;hex-D&quot;, &quot;hex-E&quot;, &quot;hex-F&quot;, &quot;hex-T&quot;, &quot;bts&quot;, &quot;reuse&quot;], &quot;blink&quot;: [&quot;reuse&quot;], &quot;hide&quot;: [&quot;ph1&quot;, &quot;ph2&quot;, &quot;ho&quot;], &quot;html&quot;: &quot;<b>Reuse:</b> Die begrenzten Frequenzen werden in <b>Gruppen</b> aufgeteilt. Dieselbe Frequenzgruppe (z. B. <b>f2</b>) wird in <b>nicht benachbarten</b> Zellen wiederverwendet — so steigt die Gesamtkapazität ohne Interferenz.&quot;}, {&quot;label&quot;: &quot;Handover beim Zellwechsel&quot;, &quot;show&quot;: [&quot;hex-C&quot;, &quot;hex-A&quot;, &quot;hex-B&quot;, &quot;hex-D&quot;, &quot;hex-E&quot;, &quot;hex-F&quot;, &quot;hex-T&quot;, &quot;bts&quot;, &quot;ph1&quot;, &quot;ho&quot;, &quot;ph2&quot;], &quot;blink&quot;: [&quot;ho&quot;], &quot;hide&quot;: [&quot;reuse&quot;], &quot;html&quot;: &quot;<b>Handover:</b> Bewegt sich ein Gerät aus einer Zelle in die nächste, wird die Verbindung im <b>Vermittlungs-Subsystem</b> nahtlos übergeben. Mobilfunk durchlief die Generationen <b>1G → 5G</b> (GSM, UMTS, LTE, 5G) mit stetig steigender Datenrate und sinkender Latenz.&quot;}];
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
</script></body></html>" width="100%" height="700" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:mobilfunk-zellen -->

## Die Generationen
| Gen | Technik | Merkmal |
|---|---|---|
| 1G | analog | A/B/C-Netze |
| 2G | digital, **GSM** | Sprache; Erweiterungen GPRS (paketvermittelt), EDGE |
| 3G | **UMTS**/HSPA | Daten + Telefonie, WCDMA |
| 4G | **LTE**(-Advanced) | IP-basiert, MIMO, bis ~300 Mbit/s |
| 5G | — | hohe Verfügbarkeit, ~1 ms Latenz, viele Teilnehmer, Gbit/s |

## Subsysteme & Identifikation
Drei Subsysteme: **Funk** (Over The Air, Ebene 1), **Vermittlung** (Weiterleitung, Handover, Backbone), **Verwaltung** (Nutzer, Roaming). Zugang nur mit Kennung: **IMSI** (SIM-Karte) und **IMEI** (Gerät). Multiplexing per Zeit/Frequenz/Code, fest pro Teilnehmer.

## Verwandte Notes
[[3 Access Networks/WLAN\|WLAN]] · [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]] · [[3 Access Networks/IoT & Bluetooth\|IoT & Bluetooth]] · [[1 Grundlagen/Übertragungsmedien & Frequenzen\|Übertragungsmedien & Frequenzen]]

[[3 Access Networks/3.0 Access Networks (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[3 Access Networks/WLAN\|⬅️ WLAN]]  ·  [[3 Access Networks/IoT & Bluetooth\|IoT & Bluetooth ➡️]]