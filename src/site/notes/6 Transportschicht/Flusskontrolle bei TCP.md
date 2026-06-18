---
{"dg-publish":true,"permalink":"/6 Transportschicht/Flusskontrolle bei TCP/","tags":["computernetworks","transport"],"updated":"2026-06-18T18:01:55.648+02:00","dg-note-properties":{"tags":["computernetworks","transport"],"aliases":["Flusskontrolle","Sliding Window","Window Size","RTT","Timeout","Retransmit"]}}
---


# Flusskontrolle bei TCP

> [!abstract] Auf einen Blick
> TCP sendet mehrere Segmente, ohne auf jedes ACK einzeln zu warten: ein **Sendefenster** (Window Size) begrenzt die Menge **unbestätigter** Bytes und „rutscht“ mit jedem ACK weiter — **Sliding Window**. So steuert der **Empfänger** das Tempo.

## Sliding Window
<!-- viz:tcp-sliding-window -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>TCP-Flusskontrolle: Sliding Window</title><style>
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
<h1 class=&quot;viz-title&quot;>TCP-Flusskontrolle: Sliding Window</h1>
<p class=&quot;viz-sub&quot;>Wie das Fenster mit jedem ACK weiterrutscht</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 600 200&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>TCP-Flusskontrolle: Sliding Window</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs><text class=&quot;tm&quot; x=&quot;50&quot; y=&quot;100&quot; fill=&quot;rgb(95,107,122)&quot;>Bytes/Segmente des Datenstroms →</text><g class=&quot;card&quot;><rect x=&quot;50&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;78&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>1</text></g><g class=&quot;card&quot;><rect x=&quot;114&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;142&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>2</text></g><g class=&quot;card&quot;><rect x=&quot;178&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;206&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>3</text></g><g class=&quot;card&quot;><rect x=&quot;242&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;270&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>4</text></g><g class=&quot;card&quot;><rect x=&quot;306&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;334&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>5</text></g><g class=&quot;card&quot;><rect x=&quot;370&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;398&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>6</text></g><g class=&quot;card&quot;><rect x=&quot;434&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;462&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>7</text></g><g class=&quot;card&quot;><rect x=&quot;498&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(207,197,180)&quot;/><text class=&quot;ts&quot; x=&quot;526&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>8</text></g><g id=&quot;wina&quot; opacity=&quot;0&quot;><rect x=&quot;44&quot; y=&quot;112&quot; width=&quot;248&quot; height=&quot;56&quot; rx=&quot;10&quot; fill=&quot;none&quot; stroke=&quot;rgb(37,73,184)&quot; stroke-width=&quot;3&quot;/><text class=&quot;ts&quot; x=&quot;168.0&quot; y=&quot;186&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(37,73,184)&quot;>Sendefenster</text></g><g id=&quot;winb&quot; opacity=&quot;0&quot;><rect x=&quot;108&quot; y=&quot;112&quot; width=&quot;248&quot; height=&quot;56&quot; rx=&quot;10&quot; fill=&quot;none&quot; stroke=&quot;rgb(37,73,184)&quot; stroke-width=&quot;3&quot;/><text class=&quot;ts&quot; x=&quot;232.0&quot; y=&quot;186&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(37,73,184)&quot;>Sendefenster</text></g><g id=&quot;winc&quot; opacity=&quot;0&quot;><rect x=&quot;236&quot; y=&quot;112&quot; width=&quot;248&quot; height=&quot;56&quot; rx=&quot;10&quot; fill=&quot;none&quot; stroke=&quot;rgb(37,73,184)&quot; stroke-width=&quot;3&quot;/><text class=&quot;ts&quot; x=&quot;360.0&quot; y=&quot;186&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(37,73,184)&quot;>Sendefenster</text></g><g id=&quot;ack1&quot; opacity=&quot;0&quot;><rect x=&quot;50&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(216,245,223)&quot; stroke=&quot;rgb(47,143,78)&quot; stroke-width=&quot;2&quot;/><text class=&quot;ts&quot; x=&quot;78&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot; fill=&quot;rgb(29,93,50)&quot;>1✓</text></g><g id=&quot;ack3&quot; opacity=&quot;0&quot;><rect x=&quot;50&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(216,245,223)&quot; stroke=&quot;rgb(47,143,78)&quot; stroke-width=&quot;2&quot;/><text class=&quot;ts&quot; x=&quot;78&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot; fill=&quot;rgb(29,93,50)&quot;>1✓</text><rect x=&quot;114&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(216,245,223)&quot; stroke=&quot;rgb(47,143,78)&quot; stroke-width=&quot;2&quot;/><text class=&quot;ts&quot; x=&quot;142&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot; fill=&quot;rgb(29,93,50)&quot;>2✓</text><rect x=&quot;178&quot; y=&quot;120&quot; width=&quot;56&quot; height=&quot;40&quot; rx=&quot;7&quot; fill=&quot;rgb(216,245,223)&quot; stroke=&quot;rgb(47,143,78)&quot; stroke-width=&quot;2&quot;/><text class=&quot;ts&quot; x=&quot;206&quot; y=&quot;140&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot; fill=&quot;rgb(29,93,50)&quot;>3✓</text></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Das Sendefenster&quot;, &quot;show&quot;: [&quot;wina&quot;], &quot;blink&quot;: [&quot;wina&quot;], &quot;hide&quot;: [&quot;winb&quot;, &quot;winc&quot;, &quot;ack1&quot;, &quot;ack3&quot;], &quot;html&quot;: &quot;<b>Schritt 1:</b> Das <b>Window Size</b>-Feld im TCP-Header sagt, wie viele Bytes <b>unbestätigt</b> unterwegs sein dürfen. Hier umfasst das Fenster die Segmente <b>1–4</b>.&quot;}, {&quot;label&quot;: &quot;Senden ohne auf jedes ACK zu warten&quot;, &quot;show&quot;: [&quot;wina&quot;], &quot;blink&quot;: [&quot;wina&quot;], &quot;hide&quot;: [&quot;winb&quot;, &quot;winc&quot;, &quot;ack1&quot;, &quot;ack3&quot;], &quot;html&quot;: &quot;<b>Schritt 2:</b> Der Sender darf <b>1–4 sofort</b> senden, ohne auf das ACK von 1 zu warten — das hält die Leitung gefüllt (anders als reines Stop-and-Wait, vgl. LLC – Sicherung).&quot;}, {&quot;label&quot;: &quot;ACK 1 → Fenster rutscht&quot;, &quot;show&quot;: [&quot;winb&quot;, &quot;ack1&quot;], &quot;blink&quot;: [&quot;winb&quot;], &quot;hide&quot;: [&quot;wina&quot;, &quot;winc&quot;, &quot;ack3&quot;], &quot;html&quot;: &quot;<b>Schritt 3:</b> Kommt das <b>ACK für 1</b>, „rutscht“ das Fenster nach rechts (jetzt 2–5) — Segment <b>5</b> wird zum Senden frei. Daher <b>Sliding Window</b>.&quot;}, {&quot;label&quot;: &quot;Weitere ACKs schieben weiter&quot;, &quot;show&quot;: [&quot;winc&quot;, &quot;ack3&quot;], &quot;blink&quot;: [&quot;winc&quot;], &quot;hide&quot;: [&quot;wina&quot;, &quot;winb&quot;, &quot;ack1&quot;], &quot;html&quot;: &quot;<b>Schritt 4:</b> Mit jedem ACK wandert das Fenster weiter (hier 4–7). Der <b>Empfänger</b> steuert über die Window Size die <b>Flusskontrolle</b> — er bremst einen zu schnellen Sender.&quot;}, {&quot;label&quot;: &quot;Timeout &amp; RTT&quot;, &quot;show&quot;: [&quot;winc&quot;, &quot;ack3&quot;], &quot;blink&quot;: [], &quot;hide&quot;: [&quot;wina&quot;, &quot;winb&quot;, &quot;ack1&quot;], &quot;html&quot;: &quot;<b>Schritt 5:</b> Bleibt ein ACK aus, läuft ein <b>Timeout</b> ab und das Segment wird erneut gesendet. Der Timeout-Wert orientiert sich an der <b>RTT</b> (Round Trip Time) — sie bestimmt maßgeblich die erreichbare Datenrate.&quot;}];
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
</script></body></html>" width="100%" height="480" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:tcp-sliding-window -->

## Timeout & RTT
TCP startet beim Senden einen **Timer**. Läuft er ab (Segment oder ACK verschwand, oder ACK zu spät), erfolgt ein **Retransmit**. Der Timeout-Wert wird dynamisch berechnet und sollte etwas größer als die **RTT (Round Trip Time)** sein. Da auf ACKs gewartet werden muss, bestimmt die **RTT** maßgeblich die erreichbare **Datenrate**.

> [!note] Verwandtschaft
> Dieselbe Idee – Bestätigen & ggf. Wiederholen – kennen wir von [[2 Link Layer/LLC – Sicherung\|ARQ]] auf Ebene 2. TCP setzt sie **Ende-zu-Ende** um.

## Verwandte Notes
[[6 Transportschicht/TCP\|TCP]] · [[6 Transportschicht/TCP-Verbindung\|TCP-Verbindung]] · [[2 Link Layer/LLC – Sicherung\|LLC – Sicherung]] · [[6 Transportschicht/UDP\|UDP]]

[[6 Transportschicht/6.0 Transportschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[6 Transportschicht/TCP-Verbindung\|⬅️ TCP-Verbindung]]  ·  [[6 Transportschicht/UDP\|UDP ➡️]]