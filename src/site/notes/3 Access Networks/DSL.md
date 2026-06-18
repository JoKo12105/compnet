---
{"dg-publish":true,"permalink":"/3-access-networks/dsl/","tags":["computernetworks","access"],"dg-note-properties":{"tags":["computernetworks","access"],"aliases":["DSL","ADSL","DMT","Digital Subscriber Line"]}}
---


# DSL

> [!abstract] Auf einen Blick
> **DSL (Digital Subscriber Line)** ist eine digitale **Punkt-zu-Punkt**-Technik über die zweiadrige **Telefonleitung**. Sie nutzt die oberhalb der Sprache **ungenutzten Frequenzen** und intensiv [[2 Link Layer/MAC – Medienzugang\|Frequenz-Multiplexing]].

## Idee
Telefonie belegt nur 0–4 kHz. DSL legt darüber **Daten-Bänder** und teilt das Spektrum per **DMT (Discrete MultiTone)** in viele schmale **Unterträger**, die einzeln und dynamisch moduliert werden. Meist **asymmetrisch** (ADSL): mehr Bandbreite für den Downstream.

## Interaktiv: Frequenz-Multiplexing bei DSL
<!-- viz:dsl -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>DSL &amp; DMT – Frequenz-Multiplexing auf der Telefonleitung</title><style>
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
<h1 class=&quot;viz-title&quot;>DSL &amp; DMT – Frequenz-Multiplexing auf der Telefonleitung</h1>
<p class=&quot;viz-sub&quot;>Wie aus einer Telefonleitung ein Breitband-Anschluss wird</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 710 340&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>DSL &amp; DMT – Frequenz-Multiplexing auf der Telefonleitung</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<line x1=&quot;60&quot; y1=&quot;300&quot; x2=&quot;660&quot; y2=&quot;300&quot; stroke=&quot;#8a7a5e&quot; stroke-width=&quot;2&quot; marker-end=&quot;url(#arrow)&quot;/>
<text class=&quot;ts&quot; x=&quot;660&quot; y=&quot;322&quot; text-anchor=&quot;end&quot; fill=&quot;#5f6b7a&quot;>Frequenz →</text>
<text class=&quot;tm&quot; x=&quot;78&quot; y=&quot;322&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>0</text>
<text class=&quot;tm&quot; x=&quot;120&quot; y=&quot;322&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>4 kHz</text>
<text class=&quot;tm&quot; x=&quot;210&quot; y=&quot;322&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>138 kHz</text>
<text class=&quot;tm&quot; x=&quot;640&quot; y=&quot;322&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>2,2 MHz</text>
<g id=&quot;b-voice&quot; class=&quot;c2 card&quot; opacity=&quot;0&quot;><rect x=&quot;78&quot; y=&quot;250&quot; width=&quot;44&quot; height=&quot;50&quot; rx=&quot;6&quot;/>
  <text class=&quot;tm&quot; x=&quot;100&quot; y=&quot;240&quot; text-anchor=&quot;middle&quot; fill=&quot;#1d5d32&quot;>Telefonie</text></g>
<g id=&quot;b-up&quot; class=&quot;c1 card&quot; opacity=&quot;0&quot;><rect x=&quot;130&quot; y=&quot;210&quot; width=&quot;80&quot; height=&quot;90&quot; rx=&quot;6&quot;/>
  <text class=&quot;tm&quot; x=&quot;170&quot; y=&quot;200&quot; text-anchor=&quot;middle&quot; fill=&quot;#123a63&quot;>Upstream</text></g>
<g id=&quot;b-down&quot; class=&quot;c3 card&quot; opacity=&quot;0&quot;><rect x=&quot;214&quot; y=&quot;120&quot; width=&quot;430&quot; height=&quot;180&quot; rx=&quot;6&quot;/>
  <text class=&quot;tm&quot; x=&quot;430&quot; y=&quot;110&quot; text-anchor=&quot;middle&quot; fill=&quot;#6e4300&quot;>Downstream (größer)</text></g>
<g id=&quot;carriers&quot; opacity=&quot;0&quot;><line x1=&quot;224&quot; y1=&quot;125&quot; x2=&quot;224&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;237&quot; y1=&quot;125&quot; x2=&quot;237&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;250&quot; y1=&quot;125&quot; x2=&quot;250&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;263&quot; y1=&quot;125&quot; x2=&quot;263&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;276&quot; y1=&quot;125&quot; x2=&quot;276&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;289&quot; y1=&quot;125&quot; x2=&quot;289&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;302&quot; y1=&quot;125&quot; x2=&quot;302&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;315&quot; y1=&quot;125&quot; x2=&quot;315&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;328&quot; y1=&quot;125&quot; x2=&quot;328&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;341&quot; y1=&quot;125&quot; x2=&quot;341&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;354&quot; y1=&quot;125&quot; x2=&quot;354&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;367&quot; y1=&quot;125&quot; x2=&quot;367&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;380&quot; y1=&quot;125&quot; x2=&quot;380&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;393&quot; y1=&quot;125&quot; x2=&quot;393&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;406&quot; y1=&quot;125&quot; x2=&quot;406&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;419&quot; y1=&quot;125&quot; x2=&quot;419&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;432&quot; y1=&quot;125&quot; x2=&quot;432&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;445&quot; y1=&quot;125&quot; x2=&quot;445&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;458&quot; y1=&quot;125&quot; x2=&quot;458&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;471&quot; y1=&quot;125&quot; x2=&quot;471&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;484&quot; y1=&quot;125&quot; x2=&quot;484&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;497&quot; y1=&quot;125&quot; x2=&quot;497&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;510&quot; y1=&quot;125&quot; x2=&quot;510&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;523&quot; y1=&quot;125&quot; x2=&quot;523&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;536&quot; y1=&quot;125&quot; x2=&quot;536&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;549&quot; y1=&quot;125&quot; x2=&quot;549&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;562&quot; y1=&quot;125&quot; x2=&quot;562&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;575&quot; y1=&quot;125&quot; x2=&quot;575&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;588&quot; y1=&quot;125&quot; x2=&quot;588&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;601&quot; y1=&quot;125&quot; x2=&quot;601&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;614&quot; y1=&quot;125&quot; x2=&quot;614&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;627&quot; y1=&quot;125&quot; x2=&quot;627&quot; y2=&quot;298&quot; stroke=&quot;#c67a00&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/></g>
<g id=&quot;carriers-up&quot; opacity=&quot;0&quot;><line x1=&quot;138&quot; y1=&quot;215&quot; x2=&quot;138&quot; y2=&quot;298&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;149&quot; y1=&quot;215&quot; x2=&quot;149&quot; y2=&quot;298&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;160&quot; y1=&quot;215&quot; x2=&quot;160&quot; y2=&quot;298&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;171&quot; y1=&quot;215&quot; x2=&quot;171&quot; y2=&quot;298&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;182&quot; y1=&quot;215&quot; x2=&quot;182&quot; y2=&quot;298&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;193&quot; y1=&quot;215&quot; x2=&quot;193&quot; y2=&quot;298&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/><line x1=&quot;204&quot; y1=&quot;215&quot; x2=&quot;204&quot; y2=&quot;298&quot; stroke=&quot;#1d5fa7&quot; stroke-width=&quot;1&quot; opacity=&quot;0.6&quot;/></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Die Telefonleitung trägt nur Sprache&quot;, &quot;show&quot;: [&quot;b-voice&quot;], &quot;blink&quot;: [&quot;b-voice&quot;], &quot;hide&quot;: [&quot;b-up&quot;, &quot;b-down&quot;, &quot;carriers&quot;, &quot;carriers-up&quot;], &quot;html&quot;: &quot;<b>Ausgangslage:</b> Klassische Telefonie nutzt nur das schmale Band <b>0–4 kHz</b> der Kupfer-Doppelader. Der Rest des Spektrums liegt brach.&quot;}, {&quot;label&quot;: &quot;DSL nutzt die hohen Frequenzen&quot;, &quot;show&quot;: [&quot;b-voice&quot;, &quot;b-up&quot;, &quot;b-down&quot;], &quot;blink&quot;: [&quot;b-up&quot;, &quot;b-down&quot;], &quot;hide&quot;: [&quot;carriers&quot;, &quot;carriers-up&quot;], &quot;html&quot;: &quot;<b>DSL-Idee:</b> Oberhalb der Sprache (ab ~25 kHz bis ~2,2 MHz) werden die <b>ungenutzten Frequenzen</b> für Daten verwendet — Telefonie und Internet laufen gleichzeitig über dieselbe Leitung.&quot;}, {&quot;label&quot;: &quot;Asymmetrie: Up- vs. Downstream&quot;, &quot;show&quot;: [&quot;b-voice&quot;, &quot;b-up&quot;, &quot;b-down&quot;], &quot;blink&quot;: [&quot;b-down&quot;], &quot;hide&quot;: [&quot;carriers&quot;, &quot;carriers-up&quot;], &quot;html&quot;: &quot;<b>Asymmetrie (ADSL):</b> Dem <b>Downstream</b> wird ein viel größerer Frequenzbereich zugewiesen als dem <b>Upstream</b> — weil Nutzer typischerweise mehr empfangen als senden.&quot;}, {&quot;label&quot;: &quot;DMT: viele kleine Unterträger&quot;, &quot;show&quot;: [&quot;b-voice&quot;, &quot;b-up&quot;, &quot;b-down&quot;, &quot;carriers&quot;, &quot;carriers-up&quot;], &quot;blink&quot;: [&quot;carriers&quot;], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>DMT (Discrete MultiTone):</b> Jedes Band wird in viele schmale <b>Unterträger</b> zerlegt, die <b>einzeln und dynamisch</b> moduliert werden. Gestörte Träger tragen weniger Bits, gute mehr. DSL ist <b>Punkt-zu-Punkt</b> über die Telefonleitung und nutzt intensiv Frequenz-Multiplexing.&quot;}];
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
</script></body></html>" width="100%" height="620" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:dsl -->

> [!note] Glasfaser als Ablösung
> Wo höhere Datenraten gefragt sind, ersetzt zunehmend **Glasfaser** das Kupfer (siehe [[1 Grundlagen/Übertragungsmedien & Frequenzen\|Übertragungsmedien & Frequenzen]] und [[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|Backbone]]).

## Verwandte Notes
[[1 Grundlagen/Physikalische Grundlagen\|Physikalische Grundlagen]] · [[1 Grundlagen/Übertragungsmedien & Frequenzen\|Übertragungsmedien & Frequenzen]] · [[3 Access Networks/Ethernet\|Ethernet]] · [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]]

[[3 Access Networks/3.0 Access Networks (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[3 Access Networks/Access Networks Grundlagen\|⬅️ Grundlagen]]  ·  [[3 Access Networks/Ethernet\|Ethernet ➡️]]