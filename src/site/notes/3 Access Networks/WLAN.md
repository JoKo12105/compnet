---
{"dg-publish":true,"permalink":"/3 Access Networks/WLAN/","tags":["computernetworks","access"],"updated":"2026-06-18T18:01:53.961+02:00","dg-note-properties":{"tags":["computernetworks","access"],"aliases":["WLAN","WiFi",802.11,"CSMA/CA","RTS/CTS","SSID","BSS"]}}
---


# WLAN

> [!abstract] Auf einen Blick
> **WLAN** (IEEE 802.11) ist drahtloses LAN. Da der Sender Kollisionen **nicht** erkennen kann (Funk, Hidden Stations), nutzt es **CSMA/CA** (Collision Avoidance) mit ACKs auf Ebene 2 und optional **RTS/CTS**-Reservierung.

## Aufbau: BSS, SSID, Association
- Ein **Access Point (AP)** bekommt eine **SSID**; AP + Stationen mit gleicher SSID bilden ein **BSS** (= ein Ebene-2-Netz).
- Mehrere BSS unter einer ESSID.
- **Association:** Der AP sendet periodisch Broadcasts (SSID + MAC). Die Station wählt einen AP und führt das **Association Protocol** aus (inkl. Sicherheit wie WPA2). Danach kann sie per [[5 Vermittlungsschicht/DHCP\|DHCP]] eine IP holen und ist Teil des [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Subnetzes]].

## Medienzugang: CSMA/CA mit RTS/CTS
<!-- viz:csma-ca -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>CSMA/CA mit RTS/CTS im WLAN</title><style>
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
<h1 class=&quot;viz-title&quot;>CSMA/CA mit RTS/CTS im WLAN</h1>
<p class=&quot;viz-sub&quot;>Collision Avoidance und Reservierung gegen Hidden Stations</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 420&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>CSMA/CA mit RTS/CTS im WLAN</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<g class=&quot;c1 card&quot;><rect x=&quot;40&quot; y=&quot;20&quot; width=&quot;120&quot; height=&quot;38&quot; rx=&quot;10&quot;/><text class=&quot;th&quot; x=&quot;100&quot; y=&quot;39&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Station</text></g>
<g class=&quot;c3 card&quot;><rect x=&quot;540&quot; y=&quot;20&quot; width=&quot;120&quot; height=&quot;38&quot; rx=&quot;10&quot;/><text class=&quot;th&quot; x=&quot;600&quot; y=&quot;39&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Access Point</text></g>
<line x1=&quot;100&quot; y1=&quot;58&quot; x2=&quot;100&quot; y2=&quot;410&quot; stroke=&quot;rgb(185,173,150)&quot; stroke-width=&quot;2&quot;/>
<line x1=&quot;600&quot; y1=&quot;58&quot; x2=&quot;600&quot; y2=&quot;410&quot; stroke=&quot;rgb(185,173,150)&quot; stroke-width=&quot;2&quot;/>
<g id=&quot;busy&quot; opacity=&quot;0&quot; class=&quot;c6 card&quot;><rect x=&quot;40&quot; y=&quot;72&quot; width=&quot;200&quot; height=&quot;32&quot; rx=&quot;9&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;88&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Kanal belegt → warten</text></g>
<g id=&quot;backoff&quot; opacity=&quot;0&quot; class=&quot;c3 card&quot;><rect x=&quot;40&quot; y=&quot;116&quot; width=&quot;200&quot; height=&quot;32&quot; rx=&quot;9&quot;/><text class=&quot;ts&quot; x=&quot;140&quot; y=&quot;132&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Kanal frei → Backoff-Timer</text></g>
<g id=&quot;rts&quot; opacity=&quot;0&quot;><line x1=&quot;105&quot; y1=&quot;170&quot; x2=&quot;595&quot; y2=&quot;200&quot; class=&quot;arr&quot; stroke=&quot;rgb(29,95,167)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;178&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(29,95,167)&quot;>RTS (Request To Send)</text></g>
<g id=&quot;cts&quot; opacity=&quot;0&quot;><line x1=&quot;595&quot; y1=&quot;218&quot; x2=&quot;105&quot; y2=&quot;248&quot; class=&quot;arr&quot; stroke=&quot;rgb(198,122,0)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;226&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(198,122,0)&quot;>CTS (Clear To Send)</text></g>
<g id=&quot;nav&quot; opacity=&quot;0&quot;><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;270&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(116,82,199)&quot;>Nachbarn hören CTS → sie warten (NAV)</text></g>
<g id=&quot;data&quot; opacity=&quot;0&quot;><line x1=&quot;105&quot; y1=&quot;295&quot; x2=&quot;595&quot; y2=&quot;325&quot; class=&quot;arr&quot; stroke=&quot;rgb(29,95,167)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;303&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(29,95,167)&quot;>DATA-Frame</text></g>
<g id=&quot;ack&quot; opacity=&quot;0&quot;><line x1=&quot;595&quot; y1=&quot;343&quot; x2=&quot;105&quot; y2=&quot;373&quot; class=&quot;arr&quot; stroke=&quot;rgb(47,143,78)&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;351&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(47,143,78)&quot;>ACK (nach SIFS)</text></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Kanal belegt → die Station wartet&quot;, &quot;show&quot;: [&quot;busy&quot;], &quot;blink&quot;: [&quot;busy&quot;], &quot;hide&quot;: [&quot;backoff&quot;, &quot;rts&quot;, &quot;cts&quot;, &quot;nav&quot;, &quot;data&quot;, &quot;ack&quot;], &quot;html&quot;: &quot;<b>Schritt 1:</b> Im WLAN kann der Sender Kollisionen <b>nicht</b> erkennen (Funk). Also gilt: ist der Kanal belegt, wird <b>nicht</b> gesendet.&quot;}, {&quot;label&quot;: &quot;Kanal frei → Backoff-Timer&quot;, &quot;show&quot;: [&quot;busy&quot;, &quot;backoff&quot;], &quot;blink&quot;: [&quot;backoff&quot;], &quot;hide&quot;: [&quot;rts&quot;, &quot;cts&quot;, &quot;nav&quot;, &quot;data&quot;, &quot;ack&quot;], &quot;html&quot;: &quot;<b>Schritt 2:</b> Wird der Kanal frei, startet ein <b>Timer</b>, der nur bei freiem Kanal weiterläuft. Erst nach dessen Ablauf wird gesendet → <b>Kollisionen werden vermieden</b> (Collision Avoidance).&quot;}, {&quot;label&quot;: &quot;RTS – Sendewunsch anmelden&quot;, &quot;show&quot;: [&quot;busy&quot;, &quot;backoff&quot;, &quot;rts&quot;], &quot;blink&quot;: [&quot;rts&quot;], &quot;hide&quot;: [&quot;cts&quot;, &quot;nav&quot;, &quot;data&quot;, &quot;ack&quot;], &quot;html&quot;: &quot;<b>Schritt 3 (optional):</b> Bei <b>Hidden Stations</b> hilft Carrier Sensing nicht. Die Station sendet ein <b>RTS</b> mit gewünschter Dauer und Adressen voraus.&quot;}, {&quot;label&quot;: &quot;CTS – AP gibt frei&quot;, &quot;show&quot;: [&quot;busy&quot;, &quot;backoff&quot;, &quot;rts&quot;, &quot;cts&quot;], &quot;blink&quot;: [&quot;cts&quot;], &quot;hide&quot;: [&quot;nav&quot;, &quot;data&quot;, &quot;ack&quot;], &quot;html&quot;: &quot;<b>Schritt 4:</b> Der AP antwortet mit <b>CTS</b>. Dieses hören <b>alle benachbarten Stationen</b> des Empfängers.&quot;}, {&quot;label&quot;: &quot;Nachbarn reservieren (NAV)&quot;, &quot;show&quot;: [&quot;busy&quot;, &quot;backoff&quot;, &quot;rts&quot;, &quot;cts&quot;, &quot;nav&quot;], &quot;blink&quot;: [&quot;nav&quot;], &quot;hide&quot;: [&quot;data&quot;, &quot;ack&quot;], &quot;html&quot;: &quot;<b>Schritt 5:</b> Die Nachbarn merken sich die Dauer und <b>schweigen</b> so lange (Network Allocation Vector). Damit ist der Kanal <b>reserviert</b> — keine Kollision mehr möglich.&quot;}, {&quot;label&quot;: &quot;DATA-Frame senden&quot;, &quot;show&quot;: [&quot;busy&quot;, &quot;backoff&quot;, &quot;rts&quot;, &quot;cts&quot;, &quot;nav&quot;, &quot;data&quot;], &quot;blink&quot;: [&quot;data&quot;], &quot;hide&quot;: [&quot;ack&quot;], &quot;html&quot;: &quot;<b>Schritt 6:</b> Jetzt überträgt die Station ihr <b>DATA</b>-Frame ungestört.&quot;}, {&quot;label&quot;: &quot;ACK bestätigt den Empfang&quot;, &quot;show&quot;: [&quot;busy&quot;, &quot;backoff&quot;, &quot;rts&quot;, &quot;cts&quot;, &quot;nav&quot;, &quot;data&quot;, &quot;ack&quot;], &quot;blink&quot;: [&quot;ack&quot;], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Schritt 7:</b> Der AP bestätigt nach kurzer Pause (SIFS) mit einem <b>ACK</b> auf Ebene 2. Das ist <b>CSMA/CA</b> mit optionalem <b>RTS/CTS</b>. Wegen des Overheads lohnt RTS/CTS vor allem bei großen Frames.&quot;}];
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
<!-- /viz:csma-ca -->

> [!warning] Hidden Stations
> Zwei Stationen, die sich gegenseitig nicht „hören“, stören am AP trotzdem. **RTS/CTS** löst das per Reservierung — lohnt aber wegen Overhead nur bei großen Frames.

## Entwicklung
Mehr Leistung durch **MIMO**, breitere Bänder (2,4 + 5 GHz), bessere Modulation (**OFDM**, QAM) und **Beamforming** (bis ~8 Gbit/s bei Wi-Fi 7 / 802.11be).

## Verwandte Notes
[[3 Access Networks/Ethernet\|Ethernet]] · [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]] · [[3 Access Networks/Mobilfunk\|Mobilfunk]] · [[5 Vermittlungsschicht/DHCP\|DHCP]]

[[3 Access Networks/3.0 Access Networks (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[3 Access Networks/Ethernet\|⬅️ Ethernet]]  ·  [[3 Access Networks/Mobilfunk\|Mobilfunk ➡️]]