---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/ARP/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T22:32:42.858+02:00","dg-note-properties":{"permalink":"/5 Vermittlungsschicht/ARP/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T22:20:29.866+02:00"}}
---



# ARP

> [!abstract] Auf einen Blick
> Im LAN wird tatsächlich mit **MAC-Adressen** ([[3 Access Networks/Ethernet\|Ethernet]]) adressiert, nicht mit IP. Das **ARP (Address Resolution Protocol)** bildet eine **IP- auf eine MAC-Adresse** ab — per Broadcast-Frage, Unicast-Antwort, gespeichert im **ARP-Cache**.

## Ablauf
<!-- viz:arp -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>ARP – von der IP- zur MAC-Adresse</title><style>
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
<h1 class=&quot;viz-title&quot;>ARP – von der IP- zur MAC-Adresse</h1>
<p class=&quot;viz-sub&quot;>Broadcast-Frage, Unicast-Antwort, Cache</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 270&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>ARP – von der IP- zur MAC-Adresse</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<rect x=&quot;40&quot; y=&quot;150&quot; width=&quot;620&quot; height=&quot;20&quot; rx=&quot;6&quot; fill=&quot;rgb(238,231,216)&quot; stroke=&quot;rgb(207,197,180)&quot;/>
<text class=&quot;tm&quot; x=&quot;350&quot; y=&quot;160&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(95,107,122)&quot;>LAN (Broadcast-Domain)</text>
<g class=&quot;c1 card&quot;><rect x=&quot;40&quot; y=&quot;60&quot; width=&quot;120&quot; height=&quot;46&quot; rx=&quot;10&quot;/><text class=&quot;ts&quot; x=&quot;100&quot; y=&quot;76&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Host A</text><text class=&quot;tm&quot; x=&quot;100&quot; y=&quot;93&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>will 10.0.0.5</text></g>
<g class=&quot;c4 card&quot;><rect x=&quot;250&quot; y=&quot;60&quot; width=&quot;110&quot; height=&quot;46&quot; rx=&quot;10&quot;/><text class=&quot;ts&quot; x=&quot;305&quot; y=&quot;76&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Host B</text><text class=&quot;tm&quot; x=&quot;305&quot; y=&quot;93&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>10.0.0.7</text></g>
<g class=&quot;c2 card&quot;><rect x=&quot;400&quot; y=&quot;60&quot; width=&quot;110&quot; height=&quot;46&quot; rx=&quot;10&quot;/><text class=&quot;ts&quot; x=&quot;455&quot; y=&quot;76&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Host C</text><text class=&quot;tm&quot; x=&quot;455&quot; y=&quot;93&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>10.0.0.5 ✓</text></g>
<g class=&quot;c4 card&quot;><rect x=&quot;550&quot; y=&quot;60&quot; width=&quot;110&quot; height=&quot;46&quot; rx=&quot;10&quot;/><text class=&quot;ts&quot; x=&quot;605&quot; y=&quot;76&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Host D</text><text class=&quot;tm&quot; x=&quot;605&quot; y=&quot;93&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>10.0.0.9</text></g>
<g id=&quot;bcB&quot; opacity=&quot;0&quot;><line x1=&quot;120&quot; y1=&quot;150&quot; x2=&quot;290&quot; y2=&quot;108&quot; class=&quot;arr&quot; stroke=&quot;rgb(29,95,167)&quot; marker-end=&quot;url(#arrow)&quot;/></g>
<g id=&quot;bcC&quot; opacity=&quot;0&quot;><line x1=&quot;160&quot; y1=&quot;150&quot; x2=&quot;440&quot; y2=&quot;108&quot; class=&quot;arr&quot; stroke=&quot;rgb(29,95,167)&quot; marker-end=&quot;url(#arrow)&quot;/></g>
<g id=&quot;bcD&quot; opacity=&quot;0&quot;><line x1=&quot;200&quot; y1=&quot;150&quot; x2=&quot;590&quot; y2=&quot;108&quot; class=&quot;arr&quot; stroke=&quot;rgb(29,95,167)&quot; marker-end=&quot;url(#arrow)&quot;/></g>
<g id=&quot;bclbl&quot; opacity=&quot;0&quot;><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;200&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(29,95,167)&quot;>Broadcast: „Wer hat 10.0.0.5?“</text></g>
<g id=&quot;reply&quot; opacity=&quot;0&quot;><line x1=&quot;440&quot; y1=&quot;108&quot; x2=&quot;120&quot; y2=&quot;150&quot; class=&quot;arr&quot; stroke=&quot;rgb(47,143,78)&quot; marker-end=&quot;url(#arrow)&quot;/>
  <text class=&quot;ts&quot; x=&quot;300&quot; y=&quot;138&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(47,143,78)&quot;>Unicast: „10.0.0.5 = MAC cc:..“</text></g>
<g id=&quot;cache&quot; opacity=&quot;0&quot; class=&quot;c3 card&quot;><rect x=&quot;40&quot; y=&quot;220&quot; width=&quot;280&quot; height=&quot;34&quot; rx=&quot;9&quot;/><text class=&quot;ts&quot; x=&quot;180&quot; y=&quot;237&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>ARP-Cache: 10.0.0.5 → cc:dd:ee:..</text></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;A kennt die IP, aber nicht die MAC&quot;, &quot;hide&quot;: [&quot;bcB&quot;, &quot;bcC&quot;, &quot;bcD&quot;, &quot;bclbl&quot;, &quot;reply&quot;, &quot;cache&quot;], &quot;show&quot;: [], &quot;html&quot;: &quot;<b>Schritt 1:</b> Host A will an <b>10.0.0.5</b> senden. Für die Übertragung im LAN braucht es aber die <b>MAC-Adresse</b> (Ethernet) — die kennt A noch nicht.&quot;}, {&quot;label&quot;: &quot;ARP-Request per Broadcast&quot;, &quot;show&quot;: [&quot;bcB&quot;, &quot;bcC&quot;, &quot;bcD&quot;, &quot;bclbl&quot;], &quot;blink&quot;: [&quot;bclbl&quot;], &quot;hide&quot;: [&quot;reply&quot;, &quot;cache&quot;], &quot;html&quot;: &quot;<b>Schritt 2:</b> A fragt per <b>Broadcast</b> das ganze LAN: „Wer hat 10.0.0.5?“ — alle Hosts empfangen die Frage.&quot;}, {&quot;label&quot;: &quot;Nur der Besitzer antwortet&quot;, &quot;show&quot;: [&quot;bcB&quot;, &quot;bcC&quot;, &quot;bcD&quot;, &quot;bclbl&quot;, &quot;reply&quot;], &quot;blink&quot;: [&quot;reply&quot;], &quot;hide&quot;: [&quot;cache&quot;], &quot;html&quot;: &quot;<b>Schritt 3:</b> Nur <b>Host C</b> (Besitzer von 10.0.0.5) antwortet — per <b>Unicast</b> mit seiner MAC-Adresse.&quot;}, {&quot;label&quot;: &quot;Ergebnis im ARP-Cache&quot;, &quot;show&quot;: [&quot;bclbl&quot;, &quot;reply&quot;, &quot;cache&quot;], &quot;blink&quot;: [&quot;cache&quot;], &quot;hide&quot;: [&quot;bcB&quot;, &quot;bcC&quot;, &quot;bcD&quot;], &quot;html&quot;: &quot;<b>Schritt 4:</b> A speichert die Zuordnung im <b>ARP-Cache</b> und kann nun direkt an die MAC senden. <b>ARP</b> bildet also IP → MAC ab.&quot;}];
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
</script></body></html>" width="100%" height="805" loading="lazy" sandbox="allow-scripts allow-same-origin allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:arp -->

Für jeden Sendevorgang muss zur Ziel-IP die MAC gefunden werden: per **Broadcast** „Wer hat IP x?“ fragen; der Besitzer antwortet mit seiner MAC. Ergebnisse landen im **ARP-Cache** (damit nicht jedes Mal neu gefragt werden muss).

> [!note] Zusammenspiel mit Forwarding
> Liegt das Ziel im **gleichen** Netz, fragt ARP nach der **Ziel-IP**. Liegt es **fremd**, fragt ARP nach der MAC des **Next-Hop-Routers** — dann adressieren Ethernet und IP unterschiedliche Rechner.

## Verwandte Themen
[[3 Access Networks/Ethernet\|Ethernet]] · [[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[5 Vermittlungsschicht/DHCP\|DHCP]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/Longest Prefix Match\|⬅️ Longest Prefix Match]]  ·  [[5 Vermittlungsschicht/DHCP\|DHCP ➡️]]