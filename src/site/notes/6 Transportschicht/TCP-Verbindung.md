---
{"dg-publish":true,"permalink":"/6 Transportschicht/TCP-Verbindung/","tags":["computernetworks","transport"],"updated":"2026-06-18T22:32:42.910+02:00","dg-note-properties":{"permalink":"/6 Transportschicht/TCP-Verbindung/","tags":["computernetworks","transport"],"updated":"2026-06-18T22:20:30.766+02:00"}}
---



# TCP-Verbindung

> [!abstract] Auf einen Blick
> Eine TCP-Kommunikation hat drei Teile: **Aufbau** (3-Wege-Handshake mit SYN/SYN-ACK/ACK), **Datenaustausch** (ESTABLISHED) und **Abbau** (vier Pakete, da beide Seiten getrennt schließen).

## Auf- und Abbau
<!-- viz:tcp-handshake -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>TCP – Verbindungsaufbau &amp; -abbau</title><style>
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
<h1 class=&quot;viz-title&quot;>TCP – Verbindungsaufbau &amp; -abbau</h1>
<p class=&quot;viz-sub&quot;>3-Wege-Handshake und das Schließen in vier Schritten</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 410&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>TCP – Verbindungsaufbau &amp; -abbau</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<g class=&quot;c1 card&quot;><rect x=&quot;40&quot; y=&quot;18&quot; width=&quot;130&quot; height=&quot;36&quot; rx=&quot;10&quot;/><text class=&quot;th&quot; x=&quot;105&quot; y=&quot;36&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Client</text></g>
<g class=&quot;c2 card&quot;><rect x=&quot;530&quot; y=&quot;18&quot; width=&quot;130&quot; height=&quot;36&quot; rx=&quot;10&quot;/><text class=&quot;th&quot; x=&quot;595&quot; y=&quot;36&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Server (LISTEN)</text></g>
<line x1=&quot;105&quot; y1=&quot;54&quot; x2=&quot;105&quot; y2=&quot;400&quot; stroke=&quot;rgb(185,173,150)&quot; stroke-width=&quot;2&quot;/>
<line x1=&quot;595&quot; y1=&quot;54&quot; x2=&quot;595&quot; y2=&quot;400&quot; stroke=&quot;rgb(185,173,150)&quot; stroke-width=&quot;2&quot;/>
<g id=&quot;syn&quot; opacity=&quot;0&quot;><line x1=&quot;110&quot; y1=&quot;74&quot; x2=&quot;590&quot; y2=&quot;104&quot; class=&quot;arr&quot; stroke=&quot;rgb(29,95,167)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;82&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(29,95,167)&quot;>SYN, SEQ=x</text></g>
<g id=&quot;synack&quot; opacity=&quot;0&quot;><line x1=&quot;590&quot; y1=&quot;120&quot; x2=&quot;110&quot; y2=&quot;150&quot; class=&quot;arr&quot; stroke=&quot;rgb(198,122,0)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;128&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(198,122,0)&quot;>SYN, ACK, SEQ=y</text></g>
<g id=&quot;ack&quot; opacity=&quot;0&quot;><line x1=&quot;110&quot; y1=&quot;166&quot; x2=&quot;590&quot; y2=&quot;196&quot; class=&quot;arr&quot; stroke=&quot;rgb(29,95,167)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;174&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(29,95,167)&quot;>ACK</text></g>
<g id=&quot;est&quot; opacity=&quot;0&quot;><rect x=&quot;230&quot; y=&quot;205&quot; width=&quot;240&quot; height=&quot;30&quot; rx=&quot;9&quot; fill=&quot;rgb(216,245,223)&quot; stroke=&quot;rgb(47,143,78)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;220&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot; fill=&quot;rgb(29,93,50)&quot;>ESTABLISHED — Datenaustausch</text></g>
<g id=&quot;fin1&quot; opacity=&quot;0&quot;><line x1=&quot;110&quot; y1=&quot;255&quot; x2=&quot;590&quot; y2=&quot;285&quot; class=&quot;arr&quot; stroke=&quot;rgb(204,90,66)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;263&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(204,90,66)&quot;>FIN</text></g>
<g id=&quot;ack1&quot; opacity=&quot;0&quot;><line x1=&quot;590&quot; y1=&quot;301&quot; x2=&quot;110&quot; y2=&quot;331&quot; class=&quot;arr&quot; stroke=&quot;rgb(47,143,78)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;309&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(47,143,78)&quot;>ACK</text></g>
<g id=&quot;fin2&quot; opacity=&quot;0&quot;><line x1=&quot;590&quot; y1=&quot;333&quot; x2=&quot;110&quot; y2=&quot;360&quot; class=&quot;arr&quot; stroke=&quot;rgb(204,90,66)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;346&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(204,90,66)&quot;>FIN</text></g>
<g id=&quot;ack2&quot; opacity=&quot;0&quot;><line x1=&quot;110&quot; y1=&quot;364&quot; x2=&quot;590&quot; y2=&quot;391&quot; class=&quot;arr&quot; stroke=&quot;rgb(47,143,78)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;382&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(47,143,78)&quot;>ACK → TIME_WAIT</text></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Verbindungsaufbau: SYN&quot;, &quot;show&quot;: [&quot;syn&quot;], &quot;blink&quot;: [&quot;syn&quot;], &quot;hide&quot;: [&quot;synack&quot;, &quot;ack&quot;, &quot;est&quot;, &quot;fin1&quot;, &quot;ack1&quot;, &quot;fin2&quot;, &quot;ack2&quot;], &quot;html&quot;: &quot;<b>3-Wege-Handshake (1):</b> Der Client sendet <b>SYN</b> mit seiner initialen Folgenummer (SEQ=x). SYN=1, ACK=0.&quot;}, {&quot;label&quot;: &quot;SYN + ACK&quot;, &quot;show&quot;: [&quot;syn&quot;, &quot;synack&quot;], &quot;blink&quot;: [&quot;synack&quot;], &quot;hide&quot;: [&quot;ack&quot;, &quot;est&quot;, &quot;fin1&quot;, &quot;ack1&quot;, &quot;fin2&quot;, &quot;ack2&quot;], &quot;html&quot;: &quot;<b>(2):</b> Der Server bestätigt mit <b>SYN=1, ACK=1</b> und seiner eigenen Folgenummer (SEQ=y).&quot;}, {&quot;label&quot;: &quot;ACK – Verbindung steht&quot;, &quot;show&quot;: [&quot;syn&quot;, &quot;synack&quot;, &quot;ack&quot;], &quot;blink&quot;: [&quot;ack&quot;], &quot;hide&quot;: [&quot;est&quot;, &quot;fin1&quot;, &quot;ack1&quot;, &quot;fin2&quot;, &quot;ack2&quot;], &quot;html&quot;: &quot;<b>(3):</b> Der Client bestätigt mit <b>ACK</b>. Damit ist die Verbindung in beide Richtungen synchronisiert.&quot;}, {&quot;label&quot;: &quot;ESTABLISHED&quot;, &quot;show&quot;: [&quot;syn&quot;, &quot;synack&quot;, &quot;ack&quot;, &quot;est&quot;], &quot;blink&quot;: [&quot;est&quot;], &quot;hide&quot;: [&quot;fin1&quot;, &quot;ack1&quot;, &quot;fin2&quot;, &quot;ack2&quot;], &quot;html&quot;: &quot;<b>ESTABLISHED:</b> Jetzt fließen Daten als zuverlässiger, vollduplexer <b>Byte-Strom</b> (SEQ/ACK, Fenstertechnik).&quot;}, {&quot;label&quot;: &quot;Abbau: FIN&quot;, &quot;show&quot;: [&quot;syn&quot;, &quot;synack&quot;, &quot;ack&quot;, &quot;est&quot;, &quot;fin1&quot;], &quot;blink&quot;: [&quot;fin1&quot;], &quot;hide&quot;: [&quot;ack1&quot;, &quot;fin2&quot;, &quot;ack2&quot;], &quot;html&quot;: &quot;<b>Abbau (1):</b> Da TCP <b>vollduplex</b> ist, müssen <b>beide Seiten</b> schließen. Hier schließt der Client aktiv mit <b>FIN</b> (Zustand FIN_WAIT).&quot;}, {&quot;label&quot;: &quot;ACK des Servers&quot;, &quot;show&quot;: [&quot;syn&quot;, &quot;synack&quot;, &quot;ack&quot;, &quot;est&quot;, &quot;fin1&quot;, &quot;ack1&quot;], &quot;blink&quot;: [&quot;ack1&quot;], &quot;hide&quot;: [&quot;fin2&quot;, &quot;ack2&quot;], &quot;html&quot;: &quot;<b>(2):</b> Der Server bestätigt das FIN mit <b>ACK</b> (Zustand CLOSE_WAIT).&quot;}, {&quot;label&quot;: &quot;FIN des Servers&quot;, &quot;show&quot;: [&quot;syn&quot;, &quot;synack&quot;, &quot;ack&quot;, &quot;est&quot;, &quot;fin1&quot;, &quot;ack1&quot;, &quot;fin2&quot;], &quot;blink&quot;: [&quot;fin2&quot;], &quot;hide&quot;: [&quot;ack2&quot;], &quot;html&quot;: &quot;<b>(3):</b> Auch der Server sendet sein <b>FIN</b>, wenn er fertig ist.&quot;}, {&quot;label&quot;: &quot;ACK → TIME_WAIT&quot;, &quot;show&quot;: [&quot;syn&quot;, &quot;synack&quot;, &quot;ack&quot;, &quot;est&quot;, &quot;fin1&quot;, &quot;ack1&quot;, &quot;fin2&quot;, &quot;ack2&quot;], &quot;blink&quot;: [&quot;ack2&quot;], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>(4):</b> Der Client bestätigt final und geht in <b>TIME_WAIT</b> (Dauer 2×MSL) — um ein evtl. erneutes FIN noch zu beantworten und alte Pakete „aussterben“ zu lassen. Insgesamt: <b>4 Pakete</b> beim Abbau.&quot;}];
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
  (s.set||[]).forEach(p=>{const e=document.getElementById(p[0]);if(e){e.textContent=p[1];}});
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
</script></body></html>" width="100%" height="989" loading="lazy" sandbox="allow-scripts allow-same-origin allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:tcp-handshake -->

## Die wichtigsten Socket-Zustände
- **LISTEN** — der Server wartet auf Anfragen.
- **SYN_RCVD** — Handshake läuft.
- **ESTABLISHED** — Datenverkehr findet statt.
- **FIN_WAIT** — eigenes aktives Schließen (close() vor Erhalt des FIN).
- **CLOSE_WAIT** — die Gegenseite hat zuerst geschlossen.
- **TIME_WAIT** — nur die **aktiv schließende** Seite; bleibt **2×MSL** (Maximum Segment Lifetime) hier, um ein verloren gegangenes letztes ACK abzufangen und alte „Inkarnationen“ zu trennen.

## Verwandte Themen
[[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle bei TCP]] · [[6 Transportschicht/Socket-API\|Socket-API]] · [[6 Transportschicht/Ports & Sockets\|Ports & Sockets]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/TCP\|⬅️ TCP]]  ·  [[6 Transportschicht/Flusskontrolle bei TCP\|Flusskontrolle bei TCP ➡️]]