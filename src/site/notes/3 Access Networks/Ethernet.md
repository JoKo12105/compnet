---
{"dg-publish":true,"permalink":"/3-access-networks/ethernet/","tags":["computernetworks","access"],"dg-note-properties":{"tags":["computernetworks","access"],"aliases":["Ethernet","CSMA/CD","MAC-Adresse","IEEE 802.3","Frame"]}}
---


# Ethernet

> [!abstract] Auf einen Blick
> **Ethernet** (IEEE 802.3) ist das wichtigste [[2 Link Layer/MAC – Medienzugang\|Random-Access]]-Verfahren und eines der wichtigsten Netzwerk-Protokolle überhaupt: flexibel, günstig, sehr verlässlich (CRC), von 10 Mbit/s bis 100 Gbit/s, über Kupfer und Glasfaser.

## Das Ethernet-Frame
Alle Standards nutzen dasselbe Frame-Format — von der Präambel über die [[3 Access Networks/Ethernet#MAC-Adresse\|MAC-Adressen]] bis zur CRC-Prüfsumme:

<!-- viz:ethernet-frame -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>Aufbau eines Ethernet-Frames</title><style>
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
<h1 class=&quot;viz-title&quot;>Aufbau eines Ethernet-Frames</h1>
<p class=&quot;viz-sub&quot;>Die Felder von der Präambel bis zur CRC-Prüfsumme</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 250&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>Aufbau eines Ethernet-Frames</title>
<g id=&quot;ef-pre&quot; class=&quot;c5 card&quot; opacity=&quot;1&quot;><rect x=&quot;40&quot; y=&quot;150&quot; width=&quot;86&quot; height=&quot;58&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;83.0&quot; y=&quot;179&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Präambel+SFD</text></g><text class=&quot;tm&quot; x=&quot;83.0&quot; y=&quot;226&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>8 B</text><g id=&quot;ef-dst&quot; class=&quot;c4 card&quot; opacity=&quot;1&quot;><rect x=&quot;126&quot; y=&quot;150&quot; width=&quot;92&quot; height=&quot;58&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;172.0&quot; y=&quot;179&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ziel-MAC</text></g><text class=&quot;tm&quot; x=&quot;172.0&quot; y=&quot;226&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>6 B</text><g id=&quot;ef-src&quot; class=&quot;c4 card&quot; opacity=&quot;1&quot;><rect x=&quot;218&quot; y=&quot;150&quot; width=&quot;92&quot; height=&quot;58&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;264.0&quot; y=&quot;179&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Quell-MAC</text></g><text class=&quot;tm&quot; x=&quot;264.0&quot; y=&quot;226&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>6 B</text><g id=&quot;ef-typ&quot; class=&quot;c3 card&quot; opacity=&quot;1&quot;><rect x=&quot;310&quot; y=&quot;150&quot; width=&quot;70&quot; height=&quot;58&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;345.0&quot; y=&quot;179&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Type/Len</text></g><text class=&quot;tm&quot; x=&quot;345.0&quot; y=&quot;226&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>2 B</text><g id=&quot;ef-dat&quot; class=&quot;c1 card&quot; opacity=&quot;1&quot;><rect x=&quot;380&quot; y=&quot;150&quot; width=&quot;176&quot; height=&quot;58&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;468.0&quot; y=&quot;179&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Daten</text></g><text class=&quot;tm&quot; x=&quot;468.0&quot; y=&quot;226&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>46–1500 B</text><g id=&quot;ef-crc&quot; class=&quot;c2 card&quot; opacity=&quot;1&quot;><rect x=&quot;556&quot; y=&quot;150&quot; width=&quot;86&quot; height=&quot;58&quot; rx=&quot;8&quot;/><text class=&quot;tm&quot; x=&quot;599.0&quot; y=&quot;179&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>FCS (CRC)</text></g><text class=&quot;tm&quot; x=&quot;599.0&quot; y=&quot;226&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>4 B</text>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Das Ethernet-Frame (IEEE 802.3)&quot;, &quot;blink&quot;: [], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Überblick:</b> Alle Ethernet-Standards nutzen dasselbe MAC-Frame-Format. Klicke dich durch die Felder.&quot;}, {&quot;label&quot;: &quot;Präambel + SFD&quot;, &quot;blink&quot;: [&quot;ef-pre&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Präambel:</b> sieben Bytes <code>10101010</code> + ein <b>SFD</b> (<code>10101011</code>) erlauben die <b>Takt-Synchronisation</b> des Empfängers.&quot;}, {&quot;label&quot;: &quot;Ziel-MAC-Adresse&quot;, &quot;blink&quot;: [&quot;ef-dst&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Ziel-Adresse (6 B):</b> An wen geht das Frame? Das erste Bit unterscheidet <b>Unicast (0)</b> und <b>Multicast (1)</b>; alles 1 = <b>Broadcast</b>.&quot;}, {&quot;label&quot;: &quot;Quell-MAC-Adresse&quot;, &quot;blink&quot;: [&quot;ef-src&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Quell-Adresse (6 B):</b> die fest und global eindeutig der Netzwerkkarte (NIC) zugeordnete <b>MAC-Adresse</b>, z. B. <code>00:D0:59:5C:03:8A</code>. Flacher Adressraum (keine Hierarchie, anders als IP).&quot;}, {&quot;label&quot;: &quot;Type / Length&quot;, &quot;blink&quot;: [&quot;ef-typ&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Type/Length (2 B):</b> Wert ≥ 0x600 → <b>Typ</b> des transportierten Protokolls (z. B. IPv4). Wert < 0x600 → <b>Länge</b> des Datenfelds.&quot;}, {&quot;label&quot;: &quot;Daten (Payload)&quot;, &quot;blink&quot;: [&quot;ef-dat&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Daten:</b> die Nutzlast. Die maximale Größe ist die <b>MTU</b> (Ethernet: <b>1500 Byte</b>). Zu kurze Frames werden per <b>Pad</b> auf eine Mindestgröße aufgefüllt.&quot;}, {&quot;label&quot;: &quot;FCS – die CRC-Prüfsumme&quot;, &quot;blink&quot;: [&quot;ef-crc&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>FCS (4 B):</b> eine <b>CRC-Prüfsumme</b>. Sie erkennt nahezu alle 1-, 2- und 3-Bit-Fehler (Fehlerquote im LAN < 10⁻¹²). Ethernet <b>korrigiert</b> aber nicht — es ist <b>keine zuverlässige</b> Übertragung.&quot;}];
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
<!-- /viz:ethernet-frame -->

## MAC-Adresse
6 Byte lang, **flacher Adressraum** (keine Hierarchie wie bei [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP]]), fest und global eindeutig der NIC zugeordnet, hexadezimal (z. B. `00:D0:59:5C:03:8A`). Erstes Bit: **Unicast (0)** / **Multicast (1)**; alles 1 = **Broadcast**.

## Medienzugang: CSMA/CD
Klassisches Ethernet (10/100Base) nutzt ein **Shared Medium** und damit **CSMA/CD**: senden bei freiem Kanal, bei Kollision abbrechen und nach zufälligem Backoff erneut senden:

<!-- viz:csma-cd -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>CSMA/CD – Kollision im klassischen Ethernet</title><style>
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
<h1 class=&quot;viz-title&quot;>CSMA/CD – Kollision im klassischen Ethernet</h1>
<p class=&quot;viz-sub&quot;>Carrier Sense, Collision Detection und zufälliger Backoff</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 315&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>CSMA/CD – Kollision im klassischen Ethernet</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<g class=&quot;c1 card&quot;><rect x=&quot;40&quot; y=&quot;30&quot; width=&quot;120&quot; height=&quot;40&quot; rx=&quot;10&quot;/><text class=&quot;th&quot; x=&quot;100&quot; y=&quot;50&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Station A</text></g>
<g class=&quot;c2 card&quot;><rect x=&quot;540&quot; y=&quot;30&quot; width=&quot;120&quot; height=&quot;40&quot; rx=&quot;10&quot;/><text class=&quot;th&quot; x=&quot;600&quot; y=&quot;50&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Station B</text></g>
<line x1=&quot;100&quot; y1=&quot;70&quot; x2=&quot;100&quot; y2=&quot;150&quot; stroke=&quot;#b9ad96&quot; stroke-width=&quot;2&quot;/>
<line x1=&quot;600&quot; y1=&quot;70&quot; x2=&quot;600&quot; y2=&quot;150&quot; stroke=&quot;#b9ad96&quot; stroke-width=&quot;2&quot;/>
<rect x=&quot;60&quot; y=&quot;150&quot; width=&quot;580&quot; height=&quot;34&quot; rx=&quot;8&quot; fill=&quot;#eee7d8&quot; stroke=&quot;#cfc5b4&quot;/>
<text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;167&quot; text-anchor=&quot;middle&quot; fill=&quot;#5f6b7a&quot;>gemeinsames Medium (Bus / Shared Medium)</text>
<rect id=&quot;sigA&quot; x=&quot;100&quot; y=&quot;156&quot; width=&quot;250&quot; height=&quot;22&quot; rx=&quot;4&quot; fill=&quot;#1d5fa7&quot; opacity=&quot;0&quot;/>
<rect id=&quot;sigB&quot; x=&quot;350&quot; y=&quot;156&quot; width=&quot;250&quot; height=&quot;22&quot; rx=&quot;4&quot; fill=&quot;#2f8f4e&quot; opacity=&quot;0&quot;/>
<g id=&quot;coll&quot; opacity=&quot;0&quot;><text x=&quot;350&quot; y=&quot;172&quot; font-size=&quot;26&quot; fill=&quot;#cc3b2a&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>💥</text>
  <text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;205&quot; text-anchor=&quot;middle&quot; fill=&quot;#cc3b2a&quot;>Kollision!</text></g>
<g id=&quot;jam&quot; opacity=&quot;0&quot;><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;230&quot; text-anchor=&quot;middle&quot; fill=&quot;#cc3b2a&quot;>beide senden JAM-Signal &amp;amp; brechen ab</text></g>
<g id=&quot;boA&quot; opacity=&quot;0&quot; class=&quot;c3 card&quot;><rect x=&quot;40&quot; y=&quot;250&quot; width=&quot;150&quot; height=&quot;34&quot; rx=&quot;9&quot;/><text class=&quot;ts&quot; x=&quot;115&quot; y=&quot;267&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>A: Backoff kurz ⏱</text></g>
<g id=&quot;boB&quot; opacity=&quot;0&quot; class=&quot;c3 card&quot;><rect x=&quot;510&quot; y=&quot;250&quot; width=&quot;150&quot; height=&quot;34&quot; rx=&quot;9&quot;/><text class=&quot;ts&quot; x=&quot;585&quot; y=&quot;267&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>B: Backoff lang ⏱⏱</text></g>
<rect id=&quot;sigA2&quot; x=&quot;100&quot; y=&quot;156&quot; width=&quot;500&quot; height=&quot;22&quot; rx=&quot;4&quot; fill=&quot;#1d5fa7&quot; opacity=&quot;0&quot;/>
<text id=&quot;okmsg&quot; class=&quot;ts&quot; x=&quot;350&quot; y=&quot;300&quot; text-anchor=&quot;middle&quot; fill=&quot;#22814b&quot; opacity=&quot;0&quot;>A sendet erfolgreich — Medium war frei</text>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Medium frei, A und B wollen senden&quot;, &quot;hide&quot;: [&quot;sigA&quot;, &quot;sigB&quot;, &quot;coll&quot;, &quot;jam&quot;, &quot;boA&quot;, &quot;boB&quot;, &quot;sigA2&quot;, &quot;okmsg&quot;], &quot;show&quot;: [], &quot;html&quot;: &quot;<b>Ausgangslage:</b> Das Medium ist frei. Sowohl A als auch B haben Daten zum Senden.&quot;}, {&quot;label&quot;: &quot;A sendet (Carrier Sense: frei)&quot;, &quot;show&quot;: [&quot;sigA&quot;], &quot;hide&quot;: [&quot;sigB&quot;, &quot;coll&quot;, &quot;jam&quot;, &quot;boA&quot;, &quot;boB&quot;, &quot;sigA2&quot;, &quot;okmsg&quot;], &quot;html&quot;: &quot;<b>Carrier Sense:</b> A hört das Medium ab, findet es frei und beginnt zu senden. Das Signal breitet sich aus — aber mit <b>endlicher Geschwindigkeit</b>.&quot;, &quot;blink&quot;: [&quot;sigA&quot;]}, {&quot;label&quot;: &quot;B hört (noch) nichts und sendet auch&quot;, &quot;show&quot;: [&quot;sigA&quot;, &quot;sigB&quot;], &quot;blink&quot;: [&quot;sigB&quot;], &quot;hide&quot;: [&quot;coll&quot;, &quot;jam&quot;, &quot;boA&quot;, &quot;boB&quot;, &quot;sigA2&quot;, &quot;okmsg&quot;], &quot;html&quot;: &quot;<b>Das Problem:</b> A's Signal hat B noch nicht erreicht. B hält das Medium für frei und sendet <b>ebenfalls</b>.&quot;}, {&quot;label&quot;: &quot;Kollision in der Mitte&quot;, &quot;show&quot;: [&quot;sigA&quot;, &quot;sigB&quot;, &quot;coll&quot;], &quot;blink&quot;: [&quot;coll&quot;], &quot;hide&quot;: [&quot;jam&quot;, &quot;boA&quot;, &quot;boB&quot;, &quot;sigA2&quot;, &quot;okmsg&quot;], &quot;html&quot;: &quot;<b>Kollision:</b> Die beiden Signale treffen sich und überlagern sich — die Daten werden zerstört.&quot;}, {&quot;label&quot;: &quot;Collision Detection + JAM&quot;, &quot;show&quot;: [&quot;sigA&quot;, &quot;sigB&quot;, &quot;coll&quot;, &quot;jam&quot;], &quot;blink&quot;: [&quot;jam&quot;], &quot;hide&quot;: [&quot;boA&quot;, &quot;boB&quot;, &quot;sigA2&quot;, &quot;okmsg&quot;], &quot;html&quot;: &quot;<b>Collision Detection:</b> Beide Sender <b>erkennen</b> die Kollision (am Kabel möglich!), senden ein kurzes <b>JAM</b>-Signal und brechen ab.&quot;}, {&quot;label&quot;: &quot;Zufälliger Backoff&quot;, &quot;show&quot;: [&quot;jam&quot;, &quot;boA&quot;, &quot;boB&quot;], &quot;blink&quot;: [&quot;boA&quot;, &quot;boB&quot;], &quot;hide&quot;: [&quot;sigA&quot;, &quot;sigB&quot;, &quot;coll&quot;, &quot;sigA2&quot;, &quot;okmsg&quot;], &quot;html&quot;: &quot;<b>Backoff:</b> Beide warten ein <b>zufälliges</b>, mit jedem Versuch wachsendes Intervall. Hier zieht A die kürzere Zeit.&quot;}, {&quot;label&quot;: &quot;A sendet erfolgreich&quot;, &quot;show&quot;: [&quot;okmsg&quot;], &quot;blink&quot;: [&quot;okmsg&quot;], &quot;hide&quot;: [&quot;sigA&quot;, &quot;sigB&quot;, &quot;coll&quot;, &quot;jam&quot;, &quot;boA&quot;, &quot;boB&quot;], &quot;set&quot;: [], &quot;html&quot;: &quot;<b>Erfolg:</b> A's Timer läuft zuerst ab, das Medium ist frei, A sendet ungestört. Das ist <b>CSMA/CD</b> — verwendet im klassischen Ethernet (10/100Base). Moderne, voll-geswitchte Netze brauchen es nicht mehr.&quot;}];
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
</script></body></html>" width="100%" height="640" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:csma-cd -->

> [!info] Modernes Ethernet
> Ab (10-)Gigabit-Ethernet gibt es nur noch **dedizierte, voll-geswitchte** Medien im **Full-Duplex** — damit **keine Kollisionen** und kein CSMA/CD mehr. Ein [[1 Grundlagen/Netzwerk-Geräte\|Switch]] filtert Frames nach Ziel-MAC.

## Verwandte Notes
[[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]] · [[1 Grundlagen/Netzwerk-Geräte\|Netzwerk-Geräte]] · [[3 Access Networks/WLAN\|WLAN]] · [[5 Vermittlungsschicht/ARP\|ARP]] · [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]]

[[3 Access Networks/3.0 Access Networks (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[3 Access Networks/DSL\|⬅️ DSL]]  ·  [[3 Access Networks/WLAN\|WLAN ➡️]]