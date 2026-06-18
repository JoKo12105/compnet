---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/Longest Prefix Match/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T15:26:19.674+02:00","dg-note-properties":{"tags":["computernetworks","vermittlung"],"aliases":["Longest Prefix Match","LPM","Forwarding-Regel"]}}
---


# Longest Prefix Match

> [!abstract] Auf einen Blick
> Beim [[5 Vermittlungsschicht/Routing & Forwarding\|Forwarding]] können **mehrere** Tabellenzeilen zur Ziel-IP passen. Es gewinnt die mit den **meisten übereinstimmenden Präfix-Bits** — der **Longest Prefix Match**. Längere Präfixe beschreiben kleinere (spezifischere) Netze.

## Die Regel
1. Zunächst sind alle Zeilen mögliche Treffer.
2. Ein Treffer liegt vor, wenn die Netz-ID der Zeile mit der Ziel-IP übereinstimmt (bitweises UND mit der Maske).
3. Der **beste** Treffer hat die **längste** übereinstimmende Netz-ID (LPM).
4. Kein Treffer übrig → Routing-Fehler. Die Tabelle wird nach **abnehmender Präfixlänge** sortiert.

## Interaktiv: Beispiel durchspielen
<!-- viz:lpm -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>Longest Prefix Match</title><style>
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
<h1 class=&quot;viz-title&quot;>Longest Prefix Match</h1>
<p class=&quot;viz-sub&quot;>Die beste Route ist das längste passende Präfix</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 280&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>Longest Prefix Match</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<g class=&quot;c1 card&quot;><rect x=&quot;180&quot; y=&quot;14&quot; width=&quot;340&quot; height=&quot;36&quot; rx=&quot;9&quot;/><text class=&quot;th&quot; x=&quot;350&quot; y=&quot;32&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ziel-IP: 142.143.144.4</text></g>
<g id=&quot;row1&quot;><rect x=&quot;120&quot; y=&quot;70&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;#fffdf8&quot; stroke=&quot;#cfc5b4&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;87&quot; dominant-baseline=&quot;central&quot;>142.143.144.0 /16</text><text class=&quot;ts&quot; x=&quot;430&quot; y=&quot;87&quot; dominant-baseline=&quot;central&quot;>→ Router Q</text></g><g id=&quot;mark1&quot; opacity=&quot;0&quot;><rect x=&quot;120&quot; y=&quot;70&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;none&quot; stroke=&quot;#2f8f4e&quot; stroke-width=&quot;3&quot;/></g><g id=&quot;row2&quot;><rect x=&quot;120&quot; y=&quot;112&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;#fffdf8&quot; stroke=&quot;#cfc5b4&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;129&quot; dominant-baseline=&quot;central&quot;>142.143.144.0 /24</text><text class=&quot;ts&quot; x=&quot;430&quot; y=&quot;129&quot; dominant-baseline=&quot;central&quot;>→ Router R</text></g><g id=&quot;mark2&quot; opacity=&quot;0&quot;><rect x=&quot;120&quot; y=&quot;112&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;none&quot; stroke=&quot;#2f8f4e&quot; stroke-width=&quot;3&quot;/></g><g id=&quot;row3&quot;><rect x=&quot;120&quot; y=&quot;154&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;#fffdf8&quot; stroke=&quot;#cfc5b4&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;171&quot; dominant-baseline=&quot;central&quot;>142.143.144.128 /25</text><text class=&quot;ts&quot; x=&quot;430&quot; y=&quot;171&quot; dominant-baseline=&quot;central&quot;>→ Router S</text></g><g id=&quot;mark3&quot; opacity=&quot;0&quot;><rect x=&quot;120&quot; y=&quot;154&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;none&quot; stroke=&quot;#cc3b2a&quot; stroke-width=&quot;3&quot;/></g><g id=&quot;row4&quot;><rect x=&quot;120&quot; y=&quot;196&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;#fffdf8&quot; stroke=&quot;#cfc5b4&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;213&quot; dominant-baseline=&quot;central&quot;>default /0</text><text class=&quot;ts&quot; x=&quot;430&quot; y=&quot;213&quot; dominant-baseline=&quot;central&quot;>→ Router Z</text></g><g id=&quot;mark4&quot; opacity=&quot;0&quot;><rect x=&quot;120&quot; y=&quot;196&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;none&quot; stroke=&quot;#2f8f4e&quot; stroke-width=&quot;3&quot;/></g>
<text id=&quot;verdict&quot; class=&quot;th&quot; x=&quot;350&quot; y=&quot;258&quot; text-anchor=&quot;middle&quot; fill=&quot;#22814b&quot;></text>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Aufgabe: beste Route für 142.143.144.4&quot;, &quot;hide&quot;: [&quot;mark1&quot;, &quot;mark2&quot;, &quot;mark3&quot;, &quot;mark4&quot;], &quot;show&quot;: [], &quot;set&quot;: [[&quot;verdict&quot;, &quot;&quot;\|&quot;verdict&quot;, &quot;&quot;]], &quot;html&quot;: &quot;<b>Aufgabe:</b> Welche Zeile der Routing-Tabelle nimmt der Router für das Ziel <b>142.143.144.4</b>? Es gilt: <b>Longest Prefix Match</b> — die Zeile mit den <b>meisten übereinstimmenden Präfix-Bits</b> gewinnt.&quot;}, {&quot;label&quot;: &quot;default /0 passt immer (schlechtester)&quot;, &quot;show&quot;: [&quot;mark4&quot;], &quot;blink&quot;: [&quot;mark4&quot;], &quot;hide&quot;: [&quot;mark1&quot;, &quot;mark2&quot;, &quot;mark3&quot;], &quot;set&quot;: [[&quot;verdict&quot;, &quot;&quot;\|&quot;verdict&quot;, &quot;&quot;]], &quot;html&quot;: &quot;<b>default /0:</b> passt auf <b>alles</b> (0 Bits Präfix) — also auch hier. Aber es ist der <b>kürzeste</b> Match, somit nur Notnagel.&quot;}, {&quot;label&quot;: &quot;/16 passt&quot;, &quot;show&quot;: [&quot;mark4&quot;, &quot;mark1&quot;], &quot;blink&quot;: [&quot;mark1&quot;], &quot;hide&quot;: [&quot;mark2&quot;, &quot;mark3&quot;], &quot;set&quot;: [[&quot;verdict&quot;, &quot;&quot;\|&quot;verdict&quot;, &quot;&quot;]], &quot;html&quot;: &quot;<b>/16:</b> Die ersten 16 Bit (142.143) stimmen → <b>passt</b>, mit 16 Bit Präfix.&quot;}, {&quot;label&quot;: &quot;/24 passt — und ist länger&quot;, &quot;show&quot;: [&quot;mark4&quot;, &quot;mark1&quot;, &quot;mark2&quot;], &quot;blink&quot;: [&quot;mark2&quot;], &quot;hide&quot;: [&quot;mark3&quot;], &quot;set&quot;: [[&quot;verdict&quot;, &quot;&quot;\|&quot;verdict&quot;, &quot;&quot;]], &quot;html&quot;: &quot;<b>/24:</b> Auch 142.143.144 stimmt → <b>passt</b> mit 24 Bit. Das ist <b>länger</b> als /16, also bisher der beste Treffer.&quot;}, {&quot;label&quot;: &quot;/25 passt NICHT&quot;, &quot;show&quot;: [&quot;mark4&quot;, &quot;mark1&quot;, &quot;mark2&quot;, &quot;mark3&quot;], &quot;blink&quot;: [&quot;mark3&quot;], &quot;hide&quot;: [], &quot;set&quot;: [[&quot;verdict&quot;, &quot;&quot;\|&quot;verdict&quot;, &quot;&quot;]], &quot;html&quot;: &quot;<b>/25 (142.143.144.128):</b> Das 25. Bit verlangt Host-Teil ≥ 128 — unsere .4 liegt darunter. <b>Kein Treffer.</b>&quot;}, {&quot;label&quot;: &quot;Gewinner: /24 → Router R&quot;, &quot;show&quot;: [&quot;mark2&quot;], &quot;blink&quot;: [&quot;mark2&quot;], &quot;hide&quot;: [&quot;mark1&quot;, &quot;mark3&quot;, &quot;mark4&quot;], &quot;set&quot;: [[&quot;verdict&quot;, &quot;Längstes passendes Präfix = /24  →  Router R&quot;\|&quot;verdict&quot;, &quot;Längstes passendes Präfix = /24  →  Router R&quot;]], &quot;html&quot;: &quot;<b>Ergebnis:</b> Unter allen Treffern (/0, /16, /24) hat <b>/24</b> das längste Präfix → das Paket geht an <b>Router R</b>. Die Tabelle wird genau deshalb nach <b>abnehmender Präfixlänge</b> sortiert.&quot;}];
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
<!-- /viz:lpm -->

> [!example] Sender-Seite
> Bei `z-netz = ziel-IP & netmask` wird verglichen: gleich dem eigenen Netz → **direct routing** (lokal); sonst an den passenden Router (**indirect**) oder an den **Default-Router**.

## Verwandte Notes
[[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]] · [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Protokolle]] · [[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/IPv4-Paket\|⬅️ IPv4-Paket]]  ·  [[5 Vermittlungsschicht/ARP\|ARP ➡️]]