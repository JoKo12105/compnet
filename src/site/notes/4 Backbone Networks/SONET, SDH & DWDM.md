---
{"dg-publish":true,"permalink":"/4-backbone-networks/sonet-sdh-and-dwdm/","tags":["computernetworks","backbone"],"dg-note-properties":{"tags":["computernetworks","backbone"],"aliases":["SONET","SDH","DWDM","Wellenlängen-Multiplexing"]}}
---


# SONET, SDH & DWDM

> [!abstract] Auf einen Blick
> **SONET/SDH** sind synchrone optische **Transportprotokolle** (Ebene 1) auf Basis von **TDM**. Die heute wichtigste Technik nutzt stattdessen **FDM** im optischen Bereich: **DWDM** — viele Wellenlängen in einer Faser.

## SONET / SDH
**Synchronous Optical Networking / Synchronous Digital Hierarchy** liefert hohe Datenraten (bis ~30 Gbit/s), arbeitet per **TDM** und braucht dafür **sehr genau synchronisierte** Zeit (Atomuhren). Es transportiert unterschiedliche Datenformate (Ethernet, ATM, IP) und wird heute v. a. in Mission-Critical-Systemen (SCADA) eingesetzt.

## DWDM
**Dense Wavelength Division Multiplexing** ist die aktuell wichtigste Backbone-Technik: 5–160 Kanäle über dicht beieinander liegende Wellenlängen (1530–1625 nm), pro Kanal bis 800 Gbit/s, bis ~35 Tbit/s pro Faser. Einsatz: klassische Backbones und Überseekabel.

<!-- viz:dwdm -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>DWDM – viele Lichtfarben in einer Faser</title><style>
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
<h1 class=&quot;viz-title&quot;>DWDM – viele Lichtfarben in einer Faser</h1>
<p class=&quot;viz-sub&quot;>Wellenlängen-Multiplexing im optischen Backbone</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 270&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>DWDM – viele Lichtfarben in einer Faser</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs><g id=&quot;src1&quot; class=&quot;c1 card&quot; opacity=&quot;0&quot;><rect x=&quot;40&quot; y=&quot;70&quot; width=&quot;74&quot; height=&quot;34&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;77&quot; y=&quot;87&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Sender λ1</text></g><line id=&quot;lin1&quot; opacity=&quot;0&quot; x1=&quot;114&quot; y1=&quot;87&quot; x2=&quot;208&quot; y2=&quot;160&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;2.5&quot;/><g id=&quot;src2&quot; class=&quot;c2 card&quot; opacity=&quot;0&quot;><rect x=&quot;40&quot; y=&quot;120&quot; width=&quot;74&quot; height=&quot;34&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;77&quot; y=&quot;137&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Sender λ2</text></g><line id=&quot;lin2&quot; opacity=&quot;0&quot; x1=&quot;114&quot; y1=&quot;137&quot; x2=&quot;208&quot; y2=&quot;160&quot; stroke=&quot;#2f8f4e&quot; stroke-width=&quot;2.5&quot;/><g id=&quot;src3&quot; class=&quot;c3 card&quot; opacity=&quot;0&quot;><rect x=&quot;40&quot; y=&quot;170&quot; width=&quot;74&quot; height=&quot;34&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;77&quot; y=&quot;187&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Sender λ3</text></g><line id=&quot;lin3&quot; opacity=&quot;0&quot; x1=&quot;114&quot; y1=&quot;187&quot; x2=&quot;208&quot; y2=&quot;160&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;2.5&quot;/><g id=&quot;src4&quot; class=&quot;c4 card&quot; opacity=&quot;0&quot;><rect x=&quot;40&quot; y=&quot;220&quot; width=&quot;74&quot; height=&quot;34&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;77&quot; y=&quot;237&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Sender λ4</text></g><line id=&quot;lin4&quot; opacity=&quot;0&quot; x1=&quot;114&quot; y1=&quot;237&quot; x2=&quot;208&quot; y2=&quot;160&quot; stroke=&quot;#7452c7&quot; stroke-width=&quot;2.5&quot;/><g id=&quot;dst1&quot; class=&quot;c1 card&quot; opacity=&quot;0&quot;><rect x=&quot;566&quot; y=&quot;70&quot; width=&quot;74&quot; height=&quot;34&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;603&quot; y=&quot;87&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ziel λ1</text></g><line id=&quot;lout1&quot; opacity=&quot;0&quot; x1=&quot;472&quot; y1=&quot;160&quot; x2=&quot;564&quot; y2=&quot;87&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;2.5&quot;/><g id=&quot;dst2&quot; class=&quot;c2 card&quot; opacity=&quot;0&quot;><rect x=&quot;566&quot; y=&quot;120&quot; width=&quot;74&quot; height=&quot;34&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;603&quot; y=&quot;137&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ziel λ2</text></g><line id=&quot;lout2&quot; opacity=&quot;0&quot; x1=&quot;472&quot; y1=&quot;160&quot; x2=&quot;564&quot; y2=&quot;137&quot; stroke=&quot;#2f8f4e&quot; stroke-width=&quot;2.5&quot;/><g id=&quot;dst3&quot; class=&quot;c3 card&quot; opacity=&quot;0&quot;><rect x=&quot;566&quot; y=&quot;170&quot; width=&quot;74&quot; height=&quot;34&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;603&quot; y=&quot;187&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ziel λ3</text></g><line id=&quot;lout3&quot; opacity=&quot;0&quot; x1=&quot;472&quot; y1=&quot;160&quot; x2=&quot;564&quot; y2=&quot;187&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;2.5&quot;/><g id=&quot;dst4&quot; class=&quot;c4 card&quot; opacity=&quot;0&quot;><rect x=&quot;566&quot; y=&quot;220&quot; width=&quot;74&quot; height=&quot;34&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;603&quot; y=&quot;237&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ziel λ4</text></g><line id=&quot;lout4&quot; opacity=&quot;0&quot; x1=&quot;472&quot; y1=&quot;160&quot; x2=&quot;564&quot; y2=&quot;237&quot; stroke=&quot;#7452c7&quot; stroke-width=&quot;2.5&quot;/>
<g id=&quot;mux&quot; opacity=&quot;0&quot;><polygon points=&quot;208,78 258,128 258,192 208,242&quot; fill=&quot;#efe7d8&quot; stroke=&quot;#8a7a5e&quot; stroke-width=&quot;2&quot;/>
  <text class=&quot;tm&quot; x=&quot;233&quot; y=&quot;160&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>MUX</text></g>
<g id=&quot;fiber&quot; opacity=&quot;0&quot;><line x1=&quot;258&quot; y1=&quot;160&quot; x2=&quot;472&quot; y2=&quot;160&quot; stroke=&quot;#9a8a6e&quot; stroke-width=&quot;9&quot; stroke-linecap=&quot;round&quot;/>
  <text class=&quot;tm&quot; x=&quot;365&quot; y=&quot;135&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>eine Glasfaser</text>
  <g id=&quot;fc&quot;><line x1=&quot;262&quot; y1=&quot;153&quot; x2=&quot;468&quot; y2=&quot;153&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;2&quot;/><line x1=&quot;262&quot; y1=&quot;158&quot; x2=&quot;468&quot; y2=&quot;158&quot; stroke=&quot;#2f8f4e&quot; stroke-width=&quot;2&quot;/><line x1=&quot;262&quot; y1=&quot;163&quot; x2=&quot;468&quot; y2=&quot;163&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;2&quot;/><line x1=&quot;262&quot; y1=&quot;168&quot; x2=&quot;468&quot; y2=&quot;168&quot; stroke=&quot;#7452c7&quot; stroke-width=&quot;2&quot;/></g></g>
<g id=&quot;amp&quot; opacity=&quot;0&quot;><polygon points=&quot;350,150 372,160 350,170&quot; fill=&quot;#cc5a42&quot;/>
  <text class=&quot;tm&quot; x=&quot;365&quot; y=&quot;190&quot; text-anchor=&quot;middle&quot; fill=&quot;#cc5a42&quot;>opt. Verstärker (~80 km)</text></g>
<g id=&quot;demux&quot; opacity=&quot;0&quot;><polygon points=&quot;472,78 522,128 522,192 472,242&quot; fill=&quot;#efe7d8&quot; stroke=&quot;#8a7a5e&quot; stroke-width=&quot;2&quot; transform=&quot;translate(0,0)&quot;/>
  <text class=&quot;tm&quot; x=&quot;497&quot; y=&quot;160&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>DEMUX</text></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Ein Sender, eine Wellenlänge&quot;, &quot;show&quot;: [&quot;src1&quot;, &quot;lin1&quot;], &quot;blink&quot;: [&quot;src1&quot;], &quot;hide&quot;: [&quot;src2&quot;, &quot;lin2&quot;, &quot;src3&quot;, &quot;lin3&quot;, &quot;src4&quot;, &quot;lin4&quot;, &quot;mux&quot;, &quot;fiber&quot;, &quot;amp&quot;, &quot;demux&quot;, &quot;dst1&quot;, &quot;dst2&quot;, &quot;dst3&quot;, &quot;dst4&quot;, &quot;lout1&quot;, &quot;lout2&quot;, &quot;lout3&quot;, &quot;lout4&quot;], &quot;html&quot;: &quot;<b>Schritt 1:</b> Ein Sender moduliert seine Daten auf eine bestimmte <b>Wellenlänge λ1</b> (eine „Lichtfarbe“).&quot;}, {&quot;label&quot;: &quot;Mehrere Wellenlängen (Farben)&quot;, &quot;show&quot;: [&quot;src1&quot;, &quot;lin1&quot;, &quot;src2&quot;, &quot;lin2&quot;, &quot;src3&quot;, &quot;lin3&quot;, &quot;src4&quot;, &quot;lin4&quot;], &quot;blink&quot;: [&quot;src2&quot;, &quot;src3&quot;, &quot;src4&quot;], &quot;hide&quot;: [&quot;mux&quot;, &quot;fiber&quot;, &quot;amp&quot;, &quot;demux&quot;, &quot;dst1&quot;, &quot;dst2&quot;, &quot;dst3&quot;, &quot;dst4&quot;, &quot;lout1&quot;, &quot;lout2&quot;, &quot;lout3&quot;, &quot;lout4&quot;], &quot;html&quot;: &quot;<b>Schritt 2:</b> Mehrere Sender nutzen <b>unterschiedliche, dicht beieinander liegende Wellenlängen</b> (1530–1625 nm) — jede trägt einen eigenen Datenstrom.&quot;}, {&quot;label&quot;: &quot;MUX bündelt alles in eine Faser&quot;, &quot;show&quot;: [&quot;src1&quot;, &quot;lin1&quot;, &quot;src2&quot;, &quot;lin2&quot;, &quot;src3&quot;, &quot;lin3&quot;, &quot;src4&quot;, &quot;lin4&quot;, &quot;mux&quot;, &quot;fiber&quot;], &quot;blink&quot;: [&quot;mux&quot;], &quot;hide&quot;: [&quot;amp&quot;, &quot;demux&quot;, &quot;dst1&quot;, &quot;dst2&quot;, &quot;dst3&quot;, &quot;dst4&quot;, &quot;lout1&quot;, &quot;lout2&quot;, &quot;lout3&quot;, &quot;lout4&quot;], &quot;html&quot;: &quot;<b>Schritt 3 — DWDM:</b> Ein <b>Multiplexer</b> bündelt alle Wellenlängen in <b>eine einzige Glasfaser</b>. Das ist Frequenz-Multiplexing im optischen Bereich (Dense Wavelength Division Multiplexing).&quot;}, {&quot;label&quot;: &quot;Über die Faser (+ Verstärker)&quot;, &quot;show&quot;: [&quot;src1&quot;, &quot;lin1&quot;, &quot;src2&quot;, &quot;lin2&quot;, &quot;src3&quot;, &quot;lin3&quot;, &quot;src4&quot;, &quot;lin4&quot;, &quot;mux&quot;, &quot;fiber&quot;, &quot;amp&quot;], &quot;blink&quot;: [&quot;amp&quot;], &quot;hide&quot;: [&quot;demux&quot;, &quot;dst1&quot;, &quot;dst2&quot;, &quot;dst3&quot;, &quot;dst4&quot;, &quot;lout1&quot;, &quot;lout2&quot;, &quot;lout3&quot;, &quot;lout4&quot;], &quot;html&quot;: &quot;<b>Schritt 4:</b> Das gebündelte Licht läuft über die Faser; <b>optische Verstärker</b> (alle ~80 km) frischen das Signal auf. Pro Kanal bis zu <b>800 Gbit/s</b>, insgesamt bis ~<b>35 Tbit/s</b> pro Faser.&quot;}, {&quot;label&quot;: &quot;DEMUX trennt die Wellenlängen&quot;, &quot;show&quot;: [&quot;src1&quot;, &quot;lin1&quot;, &quot;src2&quot;, &quot;lin2&quot;, &quot;src3&quot;, &quot;lin3&quot;, &quot;src4&quot;, &quot;lin4&quot;, &quot;mux&quot;, &quot;fiber&quot;, &quot;amp&quot;, &quot;demux&quot;, &quot;dst1&quot;, &quot;dst2&quot;, &quot;dst3&quot;, &quot;dst4&quot;, &quot;lout1&quot;, &quot;lout2&quot;, &quot;lout3&quot;, &quot;lout4&quot;], &quot;blink&quot;: [&quot;demux&quot;], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Schritt 5:</b> Am Ziel trennt ein <b>Demultiplexer</b> die Wellenlängen wieder auf, und jeder Datenstrom erreicht sein eigenes Ziel. Einsatz: klassische <b>Backbones</b> und <b>Überseekabel</b>.&quot;}];
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
</script></body></html>" width="100%" height="560" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:dwdm -->

## Verwandte Notes
[[4 Backbone Networks/Backbone Grundlagen\|Backbone Grundlagen]] · [[1 Grundlagen/Übertragungsmedien & Frequenzen\|Übertragungsmedien & Frequenzen]] · [[3 Access Networks/DSL\|DSL]] · [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]]

[[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[4 Backbone Networks/Backbone Grundlagen\|⬅️ Backbone Grundlagen]]  ·  [[4 Backbone Networks/DOCSIS & Kabelnetze\|DOCSIS & Kabelnetze ➡️]]