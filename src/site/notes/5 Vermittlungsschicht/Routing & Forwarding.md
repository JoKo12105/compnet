---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/Routing & Forwarding/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T18:01:54.996+02:00","dg-note-properties":{"tags":["computernetworks","vermittlung"],"aliases":["Forwarding","Routing","Router","Store and Forward","data plane","control plane"]}}
---


# Routing & Forwarding

> [!abstract] Auf einen Blick
> Im Internet werden Daten in **Paketen** übertragen; ihr Weg heißt **Route**. Zwei Aufgaben: **Forwarding** = Paket vom Eingang zum passenden Ausgang reichen (lokal, *data plane*); **Routing** = die nötigen Informationen netzweit bereitstellen (*control plane*).

## Forwarding (data plane)
Ein [[1 Grundlagen/Netzwerk-Geräte\|Router]] arbeitet nach **Store and Forward**: Paket zwischenspeichern, in der **Forwarding-Tabelle** die zur Ziel-IP best passende Zeile suchen ([[5 Vermittlungsschicht/Longest Prefix Match\|Longest Prefix Match]]), an das zugehörige Ausgangs-Interface übergeben. Router arbeiten **best effort** — ohne Garantien.

<!-- viz:forwarding -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>Forwarding in einem Router</title><style>
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
<h1 class=&quot;viz-title&quot;>Forwarding in einem Router</h1>
<p class=&quot;viz-sub&quot;>Store &amp; Forward, Tabellen-Lookup und Weiterleitung (data plane)</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 300&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>Forwarding in einem Router</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<g class=&quot;c1 card&quot;><rect x=&quot;20&quot; y=&quot;170&quot; width=&quot;110&quot; height=&quot;40&quot; rx=&quot;10&quot;/><text class=&quot;ts&quot; x=&quot;75&quot; y=&quot;190&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Eingang</text></g>
<g class=&quot;c4 card&quot;><rect x=&quot;250&quot; y=&quot;60&quot; width=&quot;200&quot; height=&quot;220&quot; rx=&quot;16&quot;/><text class=&quot;th&quot; x=&quot;350&quot; y=&quot;84&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Router</text></g>
<g class=&quot;c3 card&quot;><rect x=&quot;280&quot; y=&quot;110&quot; width=&quot;140&quot; height=&quot;120&quot; rx=&quot;10&quot;/>
 <text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;126&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Forwarding-Tabelle</text>
 <text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;150&quot; text-anchor=&quot;middle&quot;>Netz-ID → IF</text>
 <text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;172&quot; text-anchor=&quot;middle&quot;>10.1.0.0/16 → A</text>
 <text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;192&quot; text-anchor=&quot;middle&quot;>10.2.0.0/16 → B</text>
 <text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;212&quot; text-anchor=&quot;middle&quot;>default → C</text></g>
<g class=&quot;c2 card&quot;><rect x=&quot;570&quot; y=&quot;80&quot; width=&quot;110&quot; height=&quot;36&quot; rx=&quot;9&quot;/><text class=&quot;tm&quot; x=&quot;625&quot; y=&quot;98&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ausgang A</text></g>
<g class=&quot;c2 card&quot;><rect x=&quot;570&quot; y=&quot;172&quot; width=&quot;110&quot; height=&quot;36&quot; rx=&quot;9&quot;/><text class=&quot;tm&quot; x=&quot;625&quot; y=&quot;190&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ausgang B</text></g>
<g class=&quot;c2 card&quot;><rect x=&quot;570&quot; y=&quot;244&quot; width=&quot;110&quot; height=&quot;36&quot; rx=&quot;9&quot;/><text class=&quot;tm&quot; x=&quot;625&quot; y=&quot;262&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ausgang C</text></g>
<g id=&quot;pkt&quot; opacity=&quot;0&quot;><rect id=&quot;pktrect&quot; x=&quot;60&quot; y=&quot;150&quot; width=&quot;60&quot; height=&quot;22&quot; rx=&quot;5&quot; fill=&quot;rgb(37,73,184)&quot;/><text id=&quot;pkttext&quot; x=&quot;90&quot; y=&quot;161&quot; font-size=&quot;9&quot; fill=&quot;rgb(255,255,255)&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>→ 10.2.x</text></g>
<g id=&quot;ain&quot; opacity=&quot;0&quot;><line x1=&quot;130&quot; y1=&quot;190&quot; x2=&quot;248&quot; y2=&quot;190&quot; class=&quot;arr&quot; stroke=&quot;rgb(37,73,184)&quot; marker-end=&quot;url(#arrow)&quot;/></g>
<g id=&quot;aout&quot; opacity=&quot;0&quot;><line x1=&quot;452&quot; y1=&quot;190&quot; x2=&quot;568&quot; y2=&quot;190&quot; class=&quot;arr&quot; stroke=&quot;rgb(47,143,78)&quot; marker-end=&quot;url(#arrow)&quot;/></g>
<g id=&quot;lookup&quot; opacity=&quot;0&quot;><rect x=&quot;280&quot; y=&quot;186&quot; width=&quot;140&quot; height=&quot;20&quot; rx=&quot;4&quot; fill=&quot;none&quot; stroke=&quot;rgb(204,90,66)&quot; stroke-width=&quot;2.5&quot;/></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Paket trifft am Eingang ein&quot;, &quot;show&quot;: [&quot;pkt&quot;, &quot;ain&quot;], &quot;blink&quot;: [&quot;pkt&quot;], &quot;hide&quot;: [&quot;aout&quot;, &quot;lookup&quot;], &quot;html&quot;: &quot;<b>Schritt 1:</b> Ein Paket kommt an einem Eingangs-Interface an. Im Header steht die <b>Ziel-IP</b> (hier 10.2.x.x).&quot;}, {&quot;label&quot;: &quot;Store &amp; Forward&quot;, &quot;show&quot;: [&quot;pkt&quot;, &quot;ain&quot;], &quot;blink&quot;: [&quot;ain&quot;], &quot;hide&quot;: [&quot;aout&quot;, &quot;lookup&quot;], &quot;html&quot;: &quot;<b>Schritt 2 — Store &amp; Forward:</b> Der Router speichert das Paket zunächst vollständig zwischen, bis es ganz vorliegt.&quot;}, {&quot;label&quot;: &quot;Lookup in der Forwarding-Tabelle&quot;, &quot;show&quot;: [&quot;pkt&quot;, &quot;ain&quot;, &quot;lookup&quot;], &quot;blink&quot;: [&quot;lookup&quot;], &quot;hide&quot;: [&quot;aout&quot;], &quot;html&quot;: &quot;<b>Schritt 3:</b> Anhand der Ziel-IP wird die <b>am besten passende Zeile</b> der Forwarding-Tabelle gesucht (siehe Longest Prefix Match). Treffer: 10.2.0.0/16 → Ausgang B.&quot;}, {&quot;label&quot;: &quot;Weiterleiten an den Ausgang&quot;, &quot;show&quot;: [&quot;pkt&quot;, &quot;ain&quot;, &quot;lookup&quot;, &quot;aout&quot;], &quot;blink&quot;: [&quot;aout&quot;], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Schritt 4:</b> Das Paket wird an das passende <b>Ausgangs-Interface</b> übergeben. Router arbeiten nach <b>best effort</b> — keine Garantie für Vollständigkeit, Reihenfolge oder Zeit.&quot;}];
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
</script></body></html>" width="100%" height="600" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:forwarding -->

## Routing (control plane)
Die [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Protokolle]] halten die Forwarding-Tabellen aktuell und „optimal“ (bezogen auf eine Route: schnell/billig/sicher — oder auf das ganze Netz).

## Aufbau eines Routers
- **Forwarding Engine** — Lookup in der Forwarding-Tabelle,
- **Queue/Traffic Manager** — Queues, Prioritäten, Verwerfen überschüssiger Pakete,
- **Route Control Processor** — führt die Routing-Protokolle aus,
- **Backplane** — verbindet die Interfaces.

Optimierungen: **Adress-Aggregierung** (z. B. /24-Netze außen zu /22 zusammenfassen) und nach Präfixlänge sortierte Tabellen.

## Verwandte Notes
[[5 Vermittlungsschicht/Longest Prefix Match\|Longest Prefix Match]] · [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Protokolle]] · [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]] · [[2 Link Layer/Vermittlungsarten\|Vermittlungsarten]] · [[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|⬅️ Übersicht]]  ·  [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Protokolle ➡️]]