---
{"dg-publish":true,"permalink":"/6-transportschicht/ports-and-sockets/","tags":["computernetworks","transport"],"dg-note-properties":{"tags":["computernetworks","transport"],"aliases":["Port","Socket","Multiplexing","Demultiplexing","well-known ports"]}}
---


# Ports & Sockets

> [!abstract] Auf einen Blick
> Auf [[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|L3]] ist nur der **Host** adressierbar. **Ports** (nummerierte Endpunkte im OS) unterscheiden die **Anwendungen**; ein **Socket** ist der prozess-interne Endpunkt (≈ Datei). So wird zwischen IP und Anwendung **(de-)multiplext**.

## (De-)Multiplexing
<!-- viz:ports-multiplexing -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>Ports &amp; Sockets – (De-)Multiplexing</title><style>
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
<h1 class=&quot;viz-title&quot;>Ports &amp; Sockets – (De-)Multiplexing</h1>
<p class=&quot;viz-sub&quot;>Wie ein Host Segmente der richtigen Anwendung zuordnet</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 320&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>Ports &amp; Sockets – (De-)Multiplexing</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<g class=&quot;c4 card&quot;><rect x=&quot;250&quot; y=&quot;40&quot; width=&quot;200&quot; height=&quot;240&quot; rx=&quot;16&quot;/><text class=&quot;th&quot; x=&quot;350&quot; y=&quot;64&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Host  93.184.x.x</text>
  <text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;86&quot; text-anchor=&quot;middle&quot;>Transport: Demux nach Port</text></g>
<g class=&quot;c2 card&quot;><rect x=&quot;290&quot; y=&quot;110&quot; width=&quot;120&quot; height=&quot;36&quot; rx=&quot;9&quot;/><text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;128&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Port 22 · SSH</text></g>
<g class=&quot;c1 card&quot;><rect x=&quot;290&quot; y=&quot;160&quot; width=&quot;120&quot; height=&quot;36&quot; rx=&quot;9&quot;/><text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;178&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Port 80 · Web</text></g>
<g class=&quot;c3 card&quot;><rect x=&quot;290&quot; y=&quot;210&quot; width=&quot;120&quot; height=&quot;36&quot; rx=&quot;9&quot;/><text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;228&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Port 443 · HTTPS</text></g>
<g id=&quot;seg80&quot; opacity=&quot;0&quot;><rect x=&quot;30&quot; y=&quot;150&quot; width=&quot;120&quot; height=&quot;26&quot; rx=&quot;6&quot; fill=&quot;#1d5fa7&quot;/><text x=&quot;90&quot; y=&quot;163&quot; font-size=&quot;10&quot; fill=&quot;#fff&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Segment → :80</text></g>
<g id=&quot;seg443&quot; opacity=&quot;0&quot;><rect x=&quot;30&quot; y=&quot;210&quot; width=&quot;120&quot; height=&quot;26&quot; rx=&quot;6&quot; fill=&quot;#c67a00&quot;/><text x=&quot;90&quot; y=&quot;223&quot; font-size=&quot;10&quot; fill=&quot;#fff&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Segment → :443</text></g>
<g id=&quot;a80&quot; opacity=&quot;0&quot;><line x1=&quot;152&quot; y1=&quot;163&quot; x2=&quot;288&quot; y2=&quot;178&quot; class=&quot;arr&quot; stroke=&quot;#1d5fa7&quot; marker-end=&quot;url(#arrow)&quot;/></g>
<g id=&quot;a443&quot; opacity=&quot;0&quot;><line x1=&quot;152&quot; y1=&quot;223&quot; x2=&quot;288&quot; y2=&quot;228&quot; class=&quot;arr&quot; stroke=&quot;#c67a00&quot; marker-end=&quot;url(#arrow)&quot;/></g>
<g id=&quot;tuple&quot; opacity=&quot;0&quot;><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;305&quot; text-anchor=&quot;middle&quot; fill=&quot;#442b7f&quot;>(Quell-IP, Quell-Port, Ziel-IP, Ziel-Port) = eine Verbindung</text></g>

</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Mehrere Segmente an dieselbe IP&quot;, &quot;show&quot;: [&quot;seg80&quot;, &quot;seg443&quot;], &quot;blink&quot;: [&quot;seg80&quot;, &quot;seg443&quot;], &quot;hide&quot;: [&quot;a80&quot;, &quot;a443&quot;, &quot;tuple&quot;], &quot;html&quot;: &quot;<b>Schritt 1:</b> Beim Host kommen zwei TCP-Segmente an — beide an dieselbe IP-Adresse.&quot;}, {&quot;label&quot;: &quot;L3 adressiert nur den Host&quot;, &quot;show&quot;: [&quot;seg80&quot;, &quot;seg443&quot;], &quot;blink&quot;: [], &quot;hide&quot;: [&quot;a80&quot;, &quot;a443&quot;, &quot;tuple&quot;], &quot;html&quot;: &quot;<b>Schritt 2:</b> Die Vermittlungsschicht kann nur den <b>Host als Ganzes</b> ansprechen. Aber welche der laufenden Anwendungen soll die Daten bekommen?&quot;}, {&quot;label&quot;: &quot;Demultiplexing nach Ziel-Port&quot;, &quot;show&quot;: [&quot;seg80&quot;, &quot;seg443&quot;, &quot;a80&quot;, &quot;a443&quot;], &quot;blink&quot;: [&quot;a80&quot;, &quot;a443&quot;], &quot;hide&quot;: [&quot;tuple&quot;], &quot;html&quot;: &quot;<b>Schritt 3:</b> Die Transportschicht liest den <b>Ziel-Port</b> und leitet jedes Segment an den richtigen <b>Socket</b> / die richtige App (:80 → Web, :443 → HTTPS). Das ist <b>Multiplexing/Demultiplexing</b>.&quot;}, {&quot;label&quot;: &quot;Das 4-Tupel identifiziert die Verbindung&quot;, &quot;show&quot;: [&quot;seg80&quot;, &quot;seg443&quot;, &quot;a80&quot;, &quot;a443&quot;, &quot;tuple&quot;], &quot;blink&quot;: [&quot;tuple&quot;], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Schritt 4:</b> Bei TCP identifiziert das <b>4-Tupel</b> (Quell-IP, Quell-Port, Ziel-IP, Ziel-Port) eindeutig einen <b>Socket</b> und eine Verbindung. Ports: well-known 0–1023, registriert 1024–49151, dynamisch 49152–65535.&quot;}];
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
<!-- /viz:ports-multiplexing -->

## Port-Bereiche
- **0–1023** — *well-known* / kontrollierte Ports (z. B. 80 = HTTP, 22 = SSH); brauchen meist besondere Rechte.
- **1024–49151** — registrierte, frei verwendbare Ports.
- **49152–65535** — dynamische/private Ports.

> [!info] Identifikation
> Bei [[6 Transportschicht/TCP\|TCP]] identifiziert das **4-Tupel** (Quell-IP, Quell-Port, Ziel-IP, Ziel-Port) eindeutig eine Verbindung. Bei [[6 Transportschicht/UDP\|UDP]] genügt das **2-Tupel** (Ziel-IP, Ziel-Port).

## Verwandte Notes
[[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/UDP\|UDP]] · [[6 Transportschicht/Socket-API\|Socket-API]] · [[6 Transportschicht/Transportschicht Grundlagen\|Transportschicht Grundlagen]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/Transportschicht Grundlagen\|⬅️ Grundlagen]]  ·  [[6 Transportschicht/TCP\|TCP ➡️]]

---
<!-- coffee-button -->
<a href="https://paypal.me/joelkowylin" target="_blank" rel="noopener" style="display:block;max-width:340px;margin:10px auto;padding:12px 18px;border-radius:14px;border:2px solid #c67a00;background:linear-gradient(180deg,#ffe08a,#ffce47);color:#5a3d00;text-decoration:none;text-align:center;box-shadow:0 4px 14px rgba(180,130,20,.25)"><span style="display:block;font-size:1.15em;font-weight:800">Buy me a coffee ☕</span><span style="display:block;font-size:0.72em;margin-top:3px;opacity:.85">Diese Website zu hosten hat mich 10€ gekostet 😭</span></a>
<!-- /coffee-button -->
