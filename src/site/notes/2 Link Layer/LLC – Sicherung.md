---
{"dg-publish":true,"permalink":"/2-link-layer/llc-sicherung/","tags":["computernetworks","linklayer"],"dg-note-properties":{"tags":["computernetworks","linklayer"],"aliases":["LLC","ARQ","FEC","Fehlerbehandlung","Frame","Logical Link Control"]}}
---


# LLC – Sicherung

> [!abstract] Auf einen Blick
> **LLC (Logical Link Control)** kontrolliert die **Daten** bei vorhandenem Zugang. Daten werden in **Frames** gesendet (kein ununterbrochener Strom). Fehlerfreiheit heißt: korrekte einzelne Frames, vollständige Folge, richtige Reihenfolge — plus **Flusskontrolle**.

## Warum Frames?
Das Senden in Frames verhindert die **Monopolisierung** des Mediums und erlaubt **Fehlererkennung** (z. B. per CRC-Prüfsumme im [[3 Access Networks/Ethernet\|Ethernet]]-Frame).

## Zwei Verfahren der Fehlerbehebung
- **ARQ (Automatic Repeat Request)** — der Sender erhält (direkt/indirekt) Information über den Status (**ACK**) und sendet bei Bedarf **erneut**. ARQ erfordert einen **Rückkanal** (bidirektional).
- **FEC (Forward Error Correction)** — der Sender hängt **redundante Daten** an (Parity, CRC, Reed-Solomon); der Empfänger **rekonstruiert** die Nachricht selbst, ohne Rückfrage.

In der Praxis sind oft **hybride Formen** im Einsatz — dieselbe Idee begegnet uns auf Ebene 4 wieder ([[6 Transportschicht/TCP\|TCP]]).

## Interaktiv: ARQ (Stop-and-Wait)
Ein Frame geht verloren, der Timer läuft ab, der Sender wiederholt:

<!-- viz:arq -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>ARQ – Stop-and-Wait mit Frame-Verlust</title><style>
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
<h1 class=&quot;viz-title&quot;>ARQ – Stop-and-Wait mit Frame-Verlust</h1>
<p class=&quot;viz-sub&quot;>Wie verlorene Frames durch erneutes Senden ausgeglichen werden</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 420&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>ARQ – Stop-and-Wait mit Frame-Verlust</title>

<defs>
  <marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;>
    <path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/>
  </marker>
</defs>
<g class=&quot;c1 card&quot;><rect x=&quot;60&quot; y=&quot;20&quot; width=&quot;140&quot; height=&quot;40&quot; rx=&quot;11&quot;/>
  <text class=&quot;th&quot; x=&quot;130&quot; y=&quot;40&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Sender</text></g>
<g class=&quot;c2 card&quot;><rect x=&quot;500&quot; y=&quot;20&quot; width=&quot;140&quot; height=&quot;40&quot; rx=&quot;11&quot;/>
  <text class=&quot;th&quot; x=&quot;570&quot; y=&quot;40&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Empfänger</text></g>
<line x1=&quot;130&quot; y1=&quot;60&quot; x2=&quot;130&quot; y2=&quot;410&quot; stroke=&quot;#b9ad96&quot; stroke-width=&quot;2&quot;/>
<line x1=&quot;570&quot; y1=&quot;60&quot; x2=&quot;570&quot; y2=&quot;410&quot; stroke=&quot;#b9ad96&quot; stroke-width=&quot;2&quot;/>

<g id=&quot;f0&quot; opacity=&quot;0&quot;><line x1=&quot;135&quot; y1=&quot;80&quot; x2=&quot;565&quot; y2=&quot;118&quot; class=&quot;arr&quot; stroke=&quot;#1d5fa7&quot; marker-end=&quot;url(#arrow)&quot;/>
  <text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;90&quot; text-anchor=&quot;middle&quot; fill=&quot;#1d5fa7&quot;>Frame 0</text></g>
<g id=&quot;a0&quot; opacity=&quot;0&quot;><line x1=&quot;565&quot; y1=&quot;135&quot; x2=&quot;135&quot; y2=&quot;173&quot; class=&quot;arr&quot; stroke=&quot;#2f8f4e&quot; marker-end=&quot;url(#arrow)&quot;/>
  <text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;148&quot; text-anchor=&quot;middle&quot; fill=&quot;#2f8f4e&quot;>ACK 0</text></g>

<g id=&quot;f1&quot; opacity=&quot;0&quot;><line x1=&quot;135&quot; y1=&quot;195&quot; x2=&quot;360&quot; y2=&quot;215&quot; class=&quot;arr&quot; stroke=&quot;#1d5fa7&quot; marker-end=&quot;url(#arrow)&quot;/>
  <text class=&quot;ts&quot; x=&quot;250&quot; y=&quot;200&quot; text-anchor=&quot;middle&quot; fill=&quot;#1d5fa7&quot;>Frame 1</text></g>
<g id=&quot;f1x&quot; opacity=&quot;0&quot;><text x=&quot;392&quot; y=&quot;222&quot; font-size=&quot;26&quot; fill=&quot;#cc3b2a&quot; text-anchor=&quot;middle&quot;>✖</text>
  <text class=&quot;ts&quot; x=&quot;430&quot; y=&quot;240&quot; text-anchor=&quot;middle&quot; fill=&quot;#cc3b2a&quot;>verloren</text></g>

<g id=&quot;tout&quot; opacity=&quot;0&quot; class=&quot;c3 card&quot;><rect x=&quot;60&quot; y=&quot;250&quot; width=&quot;150&quot; height=&quot;38&quot; rx=&quot;10&quot;/>
  <text class=&quot;ts&quot; x=&quot;135&quot; y=&quot;269&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>⏱ Timeout läuft ab</text></g>

<g id=&quot;f1r&quot; opacity=&quot;0&quot;><line x1=&quot;135&quot; y1=&quot;305&quot; x2=&quot;565&quot; y2=&quot;343&quot; class=&quot;arr&quot; stroke=&quot;#c67a00&quot; marker-end=&quot;url(#arrow)&quot;/>
  <text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;315&quot; text-anchor=&quot;middle&quot; fill=&quot;#c67a00&quot;>Frame 1 (Retransmit)</text></g>
<g id=&quot;a1&quot; opacity=&quot;0&quot;><line x1=&quot;565&quot; y1=&quot;360&quot; x2=&quot;135&quot; y2=&quot;398&quot; class=&quot;arr&quot; stroke=&quot;#2f8f4e&quot; marker-end=&quot;url(#arrow)&quot;/>
  <text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;373&quot; text-anchor=&quot;middle&quot; fill=&quot;#2f8f4e&quot;>ACK 1</text></g>

</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Sender schickt Frame 0&quot;, &quot;show&quot;: [&quot;f0&quot;], &quot;blink&quot;: [&quot;f0&quot;], &quot;hide&quot;: [&quot;a0&quot;, &quot;f1&quot;, &quot;f1x&quot;, &quot;tout&quot;, &quot;f1r&quot;, &quot;a1&quot;], &quot;html&quot;: &quot;<b>Schritt 1:</b> Der Sender überträgt <b>Frame 0</b> und startet einen <b>Timer</b>. Bei Stop-and-Wait wartet er nun auf die Bestätigung.&quot;}, {&quot;label&quot;: &quot;Empfänger bestätigt mit ACK 0&quot;, &quot;show&quot;: [&quot;f0&quot;, &quot;a0&quot;], &quot;blink&quot;: [&quot;a0&quot;], &quot;hide&quot;: [&quot;f1&quot;, &quot;f1x&quot;, &quot;tout&quot;, &quot;f1r&quot;, &quot;a1&quot;], &quot;html&quot;: &quot;<b>Schritt 2:</b> Frame 0 kommt korrekt an (CRC ok) → der Empfänger sendet <b>ACK 0</b> zurück. Der Sender darf weitermachen.&quot;}, {&quot;label&quot;: &quot;Frame 1 geht verloren&quot;, &quot;show&quot;: [&quot;f0&quot;, &quot;a0&quot;, &quot;f1&quot;, &quot;f1x&quot;], &quot;blink&quot;: [&quot;f1x&quot;], &quot;hide&quot;: [&quot;tout&quot;, &quot;f1r&quot;, &quot;a1&quot;], &quot;html&quot;: &quot;<b>Schritt 3:</b> Der Sender schickt <b>Frame 1</b> — doch es geht unterwegs <b>verloren</b> (Störung). Der Empfänger erfährt davon nichts.&quot;}, {&quot;label&quot;: &quot;Timeout beim Sender&quot;, &quot;show&quot;: [&quot;f0&quot;, &quot;a0&quot;, &quot;f1&quot;, &quot;f1x&quot;, &quot;tout&quot;], &quot;blink&quot;: [&quot;tout&quot;], &quot;hide&quot;: [&quot;f1r&quot;, &quot;a1&quot;], &quot;html&quot;: &quot;<b>Schritt 4:</b> Es kommt <b>kein ACK</b>. Der Timer läuft ab → der Sender erkennt indirekt, dass etwas schiefging.&quot;}, {&quot;label&quot;: &quot;Retransmit von Frame 1&quot;, &quot;show&quot;: [&quot;f0&quot;, &quot;a0&quot;, &quot;f1&quot;, &quot;f1x&quot;, &quot;tout&quot;, &quot;f1r&quot;], &quot;blink&quot;: [&quot;f1r&quot;], &quot;hide&quot;: [&quot;a1&quot;], &quot;html&quot;: &quot;<b>Schritt 5:</b> Der Sender überträgt <b>Frame 1 erneut</b>. Das ist das Kernprinzip von <b>ARQ (Automatic Repeat Request)</b>.&quot;}, {&quot;label&quot;: &quot;ACK 1 — erfolgreich&quot;, &quot;show&quot;: [&quot;f0&quot;, &quot;a0&quot;, &quot;f1&quot;, &quot;f1x&quot;, &quot;tout&quot;, &quot;f1r&quot;, &quot;a1&quot;], &quot;blink&quot;: [&quot;a1&quot;], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Schritt 6:</b> Jetzt kommt Frame 1 an und wird mit <b>ACK 1</b> bestätigt. <b>ARQ braucht einen Rückkanal</b> (bidirektional). Alternativ korrigiert <b>FEC</b> Fehler ganz ohne Rückfrage.&quot;}];
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
<!-- /viz:arq -->

## Verwandte Notes
[[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]] · [[3 Access Networks/Ethernet\|Ethernet]] · [[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle bei TCP]] · [[1 Grundlagen/Protokolle\|Protokolle]]

[[2 Link Layer/2.0 Link Layer (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[2 Link Layer/2.0 Link Layer (Übersicht)\|⬅️ Übersicht]]  ·  [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang ➡️]]