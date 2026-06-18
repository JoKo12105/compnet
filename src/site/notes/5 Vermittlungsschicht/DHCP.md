---
{"dg-publish":true,"permalink":"/5-vermittlungsschicht/dhcp/","tags":["computernetworks","vermittlung"],"dg-note-properties":{"tags":["computernetworks","vermittlung"],"aliases":["DHCP","DORA","Dynamic Host Configuration Protocol","Lease"]}}
---


# DHCP

> [!abstract] Auf einen Blick
> **DHCP** teilt einem Host beim Booten **dynamisch** seine IP-Konfiguration zu: IP-Adresse, Netzmaske, [[5 Vermittlungsschicht/Routing & Forwarding\|Default-Router]] und DNS-Server. Der Ablauf heißt **DORA** (Discover · Offer · Request · Ack) und läuft über [[6 Transportschicht/UDP\|UDP]].

## Ablauf: DORA
<!-- viz:dhcp -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>DHCP – Adresse beziehen (DORA)</title><style>
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
<h1 class=&quot;viz-title&quot;>DHCP – Adresse beziehen (DORA)</h1>
<p class=&quot;viz-sub&quot;>Discover · Offer · Request · Ack</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 380&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>DHCP – Adresse beziehen (DORA)</title>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<g class=&quot;c1 card&quot;><rect x=&quot;40&quot; y=&quot;20&quot; width=&quot;130&quot; height=&quot;38&quot; rx=&quot;10&quot;/><text class=&quot;th&quot; x=&quot;105&quot; y=&quot;39&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Client (bootet)</text></g>
<g class=&quot;c3 card&quot;><rect x=&quot;530&quot; y=&quot;20&quot; width=&quot;130&quot; height=&quot;38&quot; rx=&quot;10&quot;/><text class=&quot;th&quot; x=&quot;595&quot; y=&quot;39&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>DHCP-Server</text></g>
<line x1=&quot;105&quot; y1=&quot;58&quot; x2=&quot;105&quot; y2=&quot;380&quot; stroke=&quot;#b9ad96&quot; stroke-width=&quot;2&quot;/>
<line x1=&quot;595&quot; y1=&quot;58&quot; x2=&quot;595&quot; y2=&quot;380&quot; stroke=&quot;#b9ad96&quot; stroke-width=&quot;2&quot;/>
<g id=&quot;d&quot; opacity=&quot;0&quot;><line x1=&quot;110&quot; y1=&quot;80&quot; x2=&quot;590&quot; y2=&quot;110&quot; class=&quot;arr&quot; stroke=&quot;#1d5fa7&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;88&quot; text-anchor=&quot;middle&quot; fill=&quot;#1d5fa7&quot;>① DISCOVER (Broadcast)</text></g>
<g id=&quot;o&quot; opacity=&quot;0&quot;><line x1=&quot;590&quot; y1=&quot;128&quot; x2=&quot;110&quot; y2=&quot;158&quot; class=&quot;arr&quot; stroke=&quot;#c67a00&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;136&quot; text-anchor=&quot;middle&quot; fill=&quot;#c67a00&quot;>② OFFER (IP-Angebot)</text></g>
<g id=&quot;r&quot; opacity=&quot;0&quot;><line x1=&quot;110&quot; y1=&quot;176&quot; x2=&quot;590&quot; y2=&quot;206&quot; class=&quot;arr&quot; stroke=&quot;#1d5fa7&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;184&quot; text-anchor=&quot;middle&quot; fill=&quot;#1d5fa7&quot;>③ REQUEST (nehme dieses an)</text></g>
<g id=&quot;a&quot; opacity=&quot;0&quot;><line x1=&quot;590&quot; y1=&quot;224&quot; x2=&quot;110&quot; y2=&quot;254&quot; class=&quot;arr&quot; stroke=&quot;#2f8f4e&quot; marker-end=&quot;url(#arrow)&quot;/><text class=&quot;ts&quot; x=&quot;350&quot; y=&quot;232&quot; text-anchor=&quot;middle&quot; fill=&quot;#2f8f4e&quot;>④ ACK (bestätigt + Konfig)</text></g>
<g id=&quot;cfg&quot; opacity=&quot;0&quot; class=&quot;c2 card&quot;><rect x=&quot;40&quot; y=&quot;290&quot; width=&quot;280&quot; height=&quot;76&quot; rx=&quot;11&quot;/>
 <text class=&quot;ts&quot; x=&quot;180&quot; y=&quot;310&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Client erhält:</text>
 <text class=&quot;tm&quot; x=&quot;180&quot; y=&quot;330&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>IP-Adresse + Netzmaske</text>
 <text class=&quot;tm&quot; x=&quot;180&quot; y=&quot;348&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Default-Router + DNS-Server</text></g>

</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;DISCOVER&quot;, &quot;show&quot;: [&quot;d&quot;], &quot;blink&quot;: [&quot;d&quot;], &quot;hide&quot;: [&quot;o&quot;, &quot;r&quot;, &quot;a&quot;, &quot;cfg&quot;], &quot;html&quot;: &quot;<b>① Discover:</b> Beim Booten hat der Client noch keine IP. Er sendet eine <b>Broadcast</b>-Nachricht ins Netz: „Gibt es einen DHCP-Server?“&quot;}, {&quot;label&quot;: &quot;OFFER&quot;, &quot;show&quot;: [&quot;d&quot;, &quot;o&quot;], &quot;blink&quot;: [&quot;o&quot;], &quot;hide&quot;: [&quot;r&quot;, &quot;a&quot;, &quot;cfg&quot;], &quot;html&quot;: &quot;<b>② Offer:</b> Ein (oder mehrere) DHCP-Server antworten mit einem <b>IP-Angebot</b>.&quot;}, {&quot;label&quot;: &quot;REQUEST&quot;, &quot;show&quot;: [&quot;d&quot;, &quot;o&quot;, &quot;r&quot;], &quot;blink&quot;: [&quot;r&quot;], &quot;hide&quot;: [&quot;a&quot;, &quot;cfg&quot;], &quot;html&quot;: &quot;<b>③ Request:</b> Der Client <b>wählt ein Angebot</b> und fordert es offiziell an (per Broadcast, damit die anderen Server ihr Angebot zurückziehen).&quot;}, {&quot;label&quot;: &quot;ACK&quot;, &quot;show&quot;: [&quot;d&quot;, &quot;o&quot;, &quot;r&quot;, &quot;a&quot;], &quot;blink&quot;: [&quot;a&quot;], &quot;hide&quot;: [&quot;cfg&quot;], &quot;html&quot;: &quot;<b>④ Ack:</b> Der Server <b>bestätigt</b> und liefert die Konfiguration. Die Zuteilung gilt befristet (<b>Lease Time</b>).&quot;}, {&quot;label&quot;: &quot;Konfiguration steht&quot;, &quot;show&quot;: [&quot;d&quot;, &quot;o&quot;, &quot;r&quot;, &quot;a&quot;, &quot;cfg&quot;], &quot;blink&quot;: [&quot;cfg&quot;], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Ergebnis:</b> Der Client kennt nun IP-Adresse, Netzmaske, Default-Router und DNS-Server. DHCP kommuniziert über eine vereinfachte Form von UDP (Merkhilfe: <b>D-O-R-A</b>).&quot;}];
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
</script></body></html>" width="100%" height="680" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:dhcp -->

Die Zuteilung gilt **befristet** (Lease Time) und kann verlängert werden. Mehrere Server können antworten — der Client wählt eines der Angebote.

## Verwandte Notes
[[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]] · [[5 Vermittlungsschicht/ARP\|ARP]] · [[3 Access Networks/WLAN\|WLAN]] · [[6 Transportschicht/UDP\|UDP]] · [[5 Vermittlungsschicht/IPv6\|IPv6]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/ARP\|⬅️ ARP]]  ·  [[5 Vermittlungsschicht/ICMP\|ICMP ➡️]]