---
{"dg-publish":true,"permalink":"/2-link-layer/vermittlungsarten/","tags":["computernetworks","linklayer"],"dg-note-properties":{"tags":["computernetworks","linklayer"],"aliases":["Circuit Switching","Packet Switching","Leitungsvermittlung","Paketvermittlung","Vermittlung"]}}
---


# Vermittlungsarten

> [!abstract] Auf einen Blick
> Datenströme können auf zwei Arten transportiert werden: **circuit switched** (ein fester, reservierter Weg) oder **packet switched** (jedes Frame/Paket einzeln). Das **Internet ist paketvermittelt**.

## Die zwei Prinzipien
- **Circuit Switching (Leitungsvermittlung):** Weg und Ressourcen werden **vorab reserviert**. Danach keine Einzelentscheidung mehr → Router werden entlastet (Switching statt Forwarding spart bis zu ~80 % Last). Beispiele: POTS (Telefon), MPLS.
- **Packet Switching (Paketvermittlung):** jedes Paket wird **einzeln** entschieden — verbindungslos (per Adresse) oder verbindungsorientiert (per Verbindungs-ID). **Flexibel und ausfallsicher**, bringt Router aber energetisch an Grenzen.

## Interaktiv: der Vergleich
<!-- viz:switching -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>Circuit vs. Packet Switching</title><style>
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
<h1 class=&quot;viz-title&quot;>Circuit vs. Packet Switching</h1>
<p class=&quot;viz-sub&quot;>Leitungsvermittlung (fester Weg) vs. Paketvermittlung (jedes Paket einzeln)</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 710 400&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>Circuit vs. Packet Switching</title>
<defs>
  <marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;6&quot; markerHeight=&quot;6&quot; orient=&quot;auto-start-reverse&quot;>
    <path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/>
  </marker>
</defs>
<!-- edges -->
<g id=&quot;edges&quot; stroke=&quot;#c2b6a0&quot; stroke-width=&quot;6&quot; stroke-linecap=&quot;round&quot;>
  <line x1=&quot;80&quot; y1=&quot;210&quot; x2=&quot;210&quot; y2=&quot;210&quot;/>
  <line x1=&quot;210&quot; y1=&quot;210&quot; x2=&quot;350&quot; y2=&quot;120&quot;/>
  <line x1=&quot;350&quot; y1=&quot;120&quot; x2=&quot;500&quot; y2=&quot;210&quot;/>
  <line x1=&quot;500&quot; y1=&quot;210&quot; x2=&quot;630&quot; y2=&quot;210&quot;/>
  <line x1=&quot;210&quot; y1=&quot;210&quot; x2=&quot;350&quot; y2=&quot;300&quot;/>
  <line x1=&quot;350&quot; y1=&quot;300&quot; x2=&quot;500&quot; y2=&quot;210&quot;/>
</g>
<!-- highlighted circuit path -->
<g id=&quot;cpath&quot; opacity=&quot;0&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;6&quot; stroke-linecap=&quot;round&quot;>
  <line x1=&quot;80&quot; y1=&quot;210&quot; x2=&quot;210&quot; y2=&quot;210&quot;/>
  <line x1=&quot;210&quot; y1=&quot;210&quot; x2=&quot;350&quot; y2=&quot;120&quot;/>
  <line x1=&quot;350&quot; y1=&quot;120&quot; x2=&quot;500&quot; y2=&quot;210&quot;/>
  <line x1=&quot;500&quot; y1=&quot;210&quot; x2=&quot;630&quot; y2=&quot;210&quot;/>
</g>
<g class=&quot;c1 card&quot;><circle cx=&quot;80&quot; cy=&quot;210&quot; r=&quot;24&quot; fill=&quot;var(--c1)&quot; stroke=&quot;var(--c1b)&quot; stroke-width=&quot;2&quot;/>
  <text class=&quot;th&quot; x=&quot;80&quot; y=&quot;210&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>A</text></g>
<g class=&quot;c2 card&quot;><circle cx=&quot;630&quot; cy=&quot;210&quot; r=&quot;24&quot; fill=&quot;var(--c2)&quot; stroke=&quot;var(--c2b)&quot; stroke-width=&quot;2&quot;/>
  <text class=&quot;th&quot; x=&quot;630&quot; y=&quot;210&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>B</text></g>
<g class=&quot;c4&quot;><circle cx=&quot;210&quot; cy=&quot;210&quot; r=&quot;20&quot; fill=&quot;var(--c4)&quot; stroke=&quot;var(--c4b)&quot; stroke-width=&quot;2&quot;/><text class=&quot;tm&quot; x=&quot;210&quot; y=&quot;210&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>R1</text></g>
<g class=&quot;c4&quot;><circle cx=&quot;350&quot; cy=&quot;120&quot; r=&quot;20&quot; fill=&quot;var(--c4)&quot; stroke=&quot;var(--c4b)&quot; stroke-width=&quot;2&quot;/><text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;120&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>R2</text></g>
<g class=&quot;c4&quot;><circle cx=&quot;500&quot; cy=&quot;210&quot; r=&quot;20&quot; fill=&quot;var(--c4)&quot; stroke=&quot;var(--c4b)&quot; stroke-width=&quot;2&quot;/><text class=&quot;tm&quot; x=&quot;500&quot; y=&quot;210&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>R3</text></g>
<g class=&quot;c4&quot;><circle cx=&quot;350&quot; cy=&quot;300&quot; r=&quot;20&quot; fill=&quot;var(--c4)&quot; stroke=&quot;var(--c4b)&quot; stroke-width=&quot;2&quot;/><text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;300&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>R4</text></g>
<!-- packets -->
<g id=&quot;pkt1&quot; opacity=&quot;0&quot;><circle cx=&quot;280&quot; cy=&quot;165&quot; r=&quot;11&quot; fill=&quot;#1d5fa7&quot;/><text x=&quot;280&quot; y=&quot;165&quot; font-size=&quot;10&quot; fill=&quot;#fff&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>1</text></g>
<g id=&quot;pkt2&quot; opacity=&quot;0&quot;><circle cx=&quot;280&quot; cy=&quot;255&quot; r=&quot;11&quot; fill=&quot;#2f8f4e&quot;/><text x=&quot;280&quot; y=&quot;255&quot; font-size=&quot;10&quot; fill=&quot;#fff&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>2</text></g>
<text id=&quot;mode&quot; class=&quot;th&quot; x=&quot;355&quot; y=&quot;380&quot; text-anchor=&quot;middle&quot; fill=&quot;#1e2430&quot;></text>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Ausgangslage: A will an B senden&quot;, &quot;hide&quot;: [&quot;cpath&quot;, &quot;pkt1&quot;, &quot;pkt2&quot;], &quot;show&quot;: [], &quot;set&quot;: [[&quot;mode&quot;, &quot;A → B über ein Netz aus Routern&quot;\|&quot;mode&quot;, &quot;A → B über ein Netz aus Routern&quot;]], &quot;html&quot;: &quot;<b>Ausgangslage:</b> Zwischen A und B liegen mehrere Router mit alternativen Wegen. Es gibt zwei grundsätzliche Arten, die Daten zu transportieren.&quot;}, {&quot;label&quot;: &quot;Leitungsvermittlung: Weg reservieren&quot;, &quot;show&quot;: [&quot;cpath&quot;], &quot;blink&quot;: [&quot;cpath&quot;], &quot;hide&quot;: [&quot;pkt1&quot;, &quot;pkt2&quot;], &quot;set&quot;: [[&quot;mode&quot;, &quot;① Circuit Switching – Reservierung&quot;\|&quot;mode&quot;, &quot;① Circuit Switching – Reservierung&quot;]], &quot;html&quot;: &quot;<b>Circuit Switching (Leitungsvermittlung):</b> Vor dem Senden wird per <b>Handshake</b> ein fester Weg A–R1–R2–R3–B aufgebaut und die Ressourcen entlang des Weges <b>reserviert</b>.&quot;}, {&quot;label&quot;: &quot;Leitungsvermittlung: Strom fließt&quot;, &quot;show&quot;: [&quot;cpath&quot;], &quot;blink&quot;: [&quot;cpath&quot;], &quot;hide&quot;: [&quot;pkt1&quot;, &quot;pkt2&quot;], &quot;set&quot;: [[&quot;mode&quot;, &quot;① Circuit Switching – Datenstrom&quot;\|&quot;mode&quot;, &quot;① Circuit Switching – Datenstrom&quot;]], &quot;html&quot;: &quot;<b>Vorteil:</b> Während des kontinuierlichen Datenstroms ist <b>keine Einzelentscheidung</b> mehr nötig (Switching statt Forwarding) — das entlastet die Router. <b>Nachteil:</b> Reservierte, aber ungenutzte Kapazität wird verschwendet. Beispiel: klassisches Telefon (POTS), MPLS.&quot;}, {&quot;label&quot;: &quot;Paketvermittlung: Paket 1&quot;, &quot;show&quot;: [&quot;pkt1&quot;], &quot;blink&quot;: [&quot;pkt1&quot;], &quot;hide&quot;: [&quot;cpath&quot;, &quot;pkt2&quot;], &quot;set&quot;: [[&quot;mode&quot;, &quot;② Packet Switching&quot;\|&quot;mode&quot;, &quot;② Packet Switching&quot;]], &quot;html&quot;: &quot;<b>Packet Switching (Paketvermittlung):</b> Die Daten werden in <b>Pakete</b> zerlegt. <b>Paket 1</b> wird an jedem Router <b>einzeln</b> weitergeleitet — hier über R2 (oben).&quot;}, {&quot;label&quot;: &quot;Paketvermittlung: Paket 2 anderer Weg&quot;, &quot;show&quot;: [&quot;pkt1&quot;, &quot;pkt2&quot;], &quot;blink&quot;: [&quot;pkt2&quot;], &quot;hide&quot;: [&quot;cpath&quot;], &quot;set&quot;: [[&quot;mode&quot;, &quot;② Packet Switching – flexibel&quot;\|&quot;mode&quot;, &quot;② Packet Switching – flexibel&quot;]], &quot;html&quot;: &quot;<b>Paket 2</b> kann einen <b>anderen Weg</b> nehmen (über R4, unten) — z. B. weil der erste überlastet ist. Das ist <b>flexibel und ausfallsicher</b>, bringt Router aber an ihre Grenzen. <b>Das Internet ist paketvermittelt.</b>&quot;}];
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
<!-- /viz:switching -->

> [!note] Bezug zu höheren Schichten
> Die Paketvermittlung ist die Grundlage für [[5 Vermittlungsschicht/Routing & Forwarding\|Forwarding]] auf [[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|Ebene 3]]. Verbindungsorientierung vs. Verbindungslosigkeit taucht dort als [[6 Transportschicht/TCP\|TCP]] vs. [[6 Transportschicht/UDP\|UDP]] wieder auf.

## Verwandte Notes
[[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[1 Grundlagen/Protokolle\|Protokolle]] · [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/UDP\|UDP]]

[[2 Link Layer/2.0 Link Layer (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[2 Link Layer/MAC – Medienzugang\|⬅️ MAC – Medienzugang]]  ·  [[3 Access Networks/3.0 Access Networks (Übersicht)\|Kapitel 3: Access Networks ➡️]]