---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/Longest Prefix Match/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T23:33:42.149+02:00","dg-note-properties":{"permalink":"/5 Vermittlungsschicht/Longest Prefix Match/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T22:20:29.829+02:00"}}
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
<g id=&quot;row1&quot;><rect x=&quot;120&quot; y=&quot;70&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;87&quot; dominant-baseline=&quot;central&quot;>142.143.144.0 /16</text><text class=&quot;ts&quot; x=&quot;430&quot; y=&quot;87&quot; dominant-baseline=&quot;central&quot;>→ Router Q</text></g><g id=&quot;mark1&quot; opacity=&quot;0&quot;><rect x=&quot;120&quot; y=&quot;70&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;none&quot; stroke=&quot;rgb(47,143,78)&quot; stroke-width=&quot;3&quot;/></g><g id=&quot;row2&quot;><rect x=&quot;120&quot; y=&quot;112&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;129&quot; dominant-baseline=&quot;central&quot;>142.143.144.0 /24</text><text class=&quot;ts&quot; x=&quot;430&quot; y=&quot;129&quot; dominant-baseline=&quot;central&quot;>→ Router R</text></g><g id=&quot;mark2&quot; opacity=&quot;0&quot;><rect x=&quot;120&quot; y=&quot;112&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;none&quot; stroke=&quot;rgb(47,143,78)&quot; stroke-width=&quot;3&quot;/></g><g id=&quot;row3&quot;><rect x=&quot;120&quot; y=&quot;154&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;171&quot; dominant-baseline=&quot;central&quot;>142.143.144.128 /25</text><text class=&quot;ts&quot; x=&quot;430&quot; y=&quot;171&quot; dominant-baseline=&quot;central&quot;>→ Router S</text></g><g id=&quot;mark3&quot; opacity=&quot;0&quot;><rect x=&quot;120&quot; y=&quot;154&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;none&quot; stroke=&quot;rgb(204,59,42)&quot; stroke-width=&quot;3&quot;/></g><g id=&quot;row4&quot;><rect x=&quot;120&quot; y=&quot;196&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;213&quot; dominant-baseline=&quot;central&quot;>default /0</text><text class=&quot;ts&quot; x=&quot;430&quot; y=&quot;213&quot; dominant-baseline=&quot;central&quot;>→ Router Z</text></g><g id=&quot;mark4&quot; opacity=&quot;0&quot;><rect x=&quot;120&quot; y=&quot;196&quot; width=&quot;460&quot; height=&quot;34&quot; rx=&quot;7&quot; fill=&quot;none&quot; stroke=&quot;rgb(47,143,78)&quot; stroke-width=&quot;3&quot;/></g>
<text id=&quot;verdict&quot; class=&quot;th&quot; x=&quot;350&quot; y=&quot;258&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(34,129,75)&quot;></text>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Aufgabe: beste Route für 142.143.144.4&quot;, &quot;hide&quot;: [&quot;mark1&quot;, &quot;mark2&quot;, &quot;mark3&quot;, &quot;mark4&quot;], &quot;show&quot;: [], &quot;set&quot;: [{&quot;el&quot;: &quot;verdict&quot;, &quot;tx&quot;: &quot;&quot;}], &quot;html&quot;: &quot;<b>Aufgabe:</b> Welche Zeile der Routing-Tabelle nimmt der Router für das Ziel <b>142.143.144.4</b>? Es gilt: <b>Longest Prefix Match</b> — die Zeile mit den <b>meisten übereinstimmenden Präfix-Bits</b> gewinnt.&quot;}, {&quot;label&quot;: &quot;default /0 passt immer (schlechtester)&quot;, &quot;show&quot;: [&quot;mark4&quot;], &quot;blink&quot;: [&quot;mark4&quot;], &quot;hide&quot;: [&quot;mark1&quot;, &quot;mark2&quot;, &quot;mark3&quot;], &quot;set&quot;: [{&quot;el&quot;: &quot;verdict&quot;, &quot;tx&quot;: &quot;&quot;}], &quot;html&quot;: &quot;<b>default /0:</b> passt auf <b>alles</b> (0 Bits Präfix) — also auch hier. Aber es ist der <b>kürzeste</b> Match, somit nur Notnagel.&quot;}, {&quot;label&quot;: &quot;/16 passt&quot;, &quot;show&quot;: [&quot;mark4&quot;, &quot;mark1&quot;], &quot;blink&quot;: [&quot;mark1&quot;], &quot;hide&quot;: [&quot;mark2&quot;, &quot;mark3&quot;], &quot;set&quot;: [{&quot;el&quot;: &quot;verdict&quot;, &quot;tx&quot;: &quot;&quot;}], &quot;html&quot;: &quot;<b>/16:</b> Die ersten 16 Bit (142.143) stimmen → <b>passt</b>, mit 16 Bit Präfix.&quot;}, {&quot;label&quot;: &quot;/24 passt — und ist länger&quot;, &quot;show&quot;: [&quot;mark4&quot;, &quot;mark1&quot;, &quot;mark2&quot;], &quot;blink&quot;: [&quot;mark2&quot;], &quot;hide&quot;: [&quot;mark3&quot;], &quot;set&quot;: [{&quot;el&quot;: &quot;verdict&quot;, &quot;tx&quot;: &quot;&quot;}], &quot;html&quot;: &quot;<b>/24:</b> Auch 142.143.144 stimmt → <b>passt</b> mit 24 Bit. Das ist <b>länger</b> als /16, also bisher der beste Treffer.&quot;}, {&quot;label&quot;: &quot;/25 passt NICHT&quot;, &quot;show&quot;: [&quot;mark4&quot;, &quot;mark1&quot;, &quot;mark2&quot;, &quot;mark3&quot;], &quot;blink&quot;: [&quot;mark3&quot;], &quot;hide&quot;: [], &quot;set&quot;: [{&quot;el&quot;: &quot;verdict&quot;, &quot;tx&quot;: &quot;&quot;}], &quot;html&quot;: &quot;<b>/25 (142.143.144.128):</b> Das 25. Bit verlangt Host-Teil ≥ 128 — unsere .4 liegt darunter. <b>Kein Treffer.</b>&quot;}, {&quot;label&quot;: &quot;Gewinner: /24 → Router R&quot;, &quot;show&quot;: [&quot;mark2&quot;], &quot;blink&quot;: [&quot;mark2&quot;], &quot;hide&quot;: [&quot;mark1&quot;, &quot;mark3&quot;, &quot;mark4&quot;], &quot;set&quot;: [{&quot;el&quot;: &quot;verdict&quot;, &quot;tx&quot;: &quot;Längstes passendes Präfix = /24  →  Router R&quot;}], &quot;html&quot;: &quot;<b>Ergebnis:</b> Unter allen Treffern (/0, /16, /24) hat <b>/24</b> das längste Präfix → das Paket geht an <b>Router R</b>. Die Tabelle wird genau deshalb nach <b>abnehmender Präfixlänge</b> sortiert.&quot;}];
let current = 0;
let _lh=0;
function fit(){try{var h=document.body.scrollHeight;if(window.frameElement&amp;&amp;Math.abs(h-_lh)>1){_lh=h;window.frameElement.style.height=h+&quot;px&quot;;}}catch(e){}}
function render(idx){
  const s = steps[idx];
  document.getElementById(&quot;step-label&quot;).textContent = (idx+1)+&quot; / &quot;+steps.length+&quot; — &quot;+s.label;
  document.getElementById(&quot;step-content&quot;).innerHTML = s.html;
  (s.hide||[]).forEach(id=>{const e=document.getElementById(id);if(e){e.style.opacity=&quot;0&quot;;e.classList.remove(&quot;blinking&quot;);}});
  (s.show||[]).forEach(id=>{const e=document.getElementById(id);if(e){e.style.opacity=&quot;1&quot;;e.classList.remove(&quot;blinking&quot;);}});
  (s.blink||[]).forEach(id=>{const e=document.getElementById(id);if(e){e.style.opacity=&quot;1&quot;;e.classList.add(&quot;blinking&quot;);}});
  (s.set||[]).forEach(p=>{const e=document.getElementById(p.el);if(e){e.textContent=p.tx;}});
  document.querySelectorAll(&quot;.step-dot&quot;).forEach((d,i)=>{d.className=&quot;step-dot&quot;+(i===idx?&quot; active&quot;:i<idx?&quot; done&quot;:&quot;&quot;);});
  document.getElementById(&quot;btn-prev&quot;).disabled = idx===0;
  document.getElementById(&quot;btn-next&quot;).disabled = idx===steps.length-1;
  document.getElementById(&quot;btn-next&quot;).textContent = idx===steps.length-1 ? &quot;Fertig&quot; : &quot;Weiter&quot;;
  fit();
}
function changeStep(d){current=Math.max(0,Math.min(steps.length-1,current+d));render(current);}
const dotsEl=document.getElementById(&quot;dots&quot;);
steps.forEach((_,i)=>{const d=document.createElement(&quot;div&quot;);d.className=&quot;step-dot&quot;;d.textContent=i+1;d.onclick=()=>{current=i;render(i);};dotsEl.appendChild(d);});
render(0);
window.addEventListener(&quot;load&quot;,fit);
if(window.ResizeObserver){new ResizeObserver(fit).observe(document.body);}
setTimeout(fit,60);
</script></body></html>" width="100%" height="816" loading="lazy" sandbox="allow-scripts allow-same-origin allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:lpm -->

> [!example] Sender-Seite
> Bei `z-netz = ziel-IP & netmask` wird verglichen: gleich dem eigenen Netz → **direct routing** (lokal); sonst an den passenden Router (**indirect**) oder an den **Default-Router**.

## Verwandte Themen
[[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]] · [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Protokolle]] · [[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/IPv4-Paket\|⬅️ IPv4-Paket]]  ·  [[5 Vermittlungsschicht/ARP\|ARP ➡️]]
