---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/IPv6/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T18:01:55.247+02:00","dg-note-properties":{"tags":["computernetworks","vermittlung"],"aliases":["IPv6","IPv6-Adresse","Dual-Stack","Neighbor Discovery"]}}
---


# IPv6

> [!abstract] Auf einen Blick
> **IPv6** löst zwei Probleme von IPv4: die **Adressknappheit** (jetzt **128 Bit**) und fehlende Echtzeit-Garantien. Der Header ist **einfacher** (keine Prüfsumme, keine Fragmentierungsinfo), erlaubt **Erweiterungsheader** und **Autokonfiguration**.

## Adressen & Schreibweise
128 Bit, in 8 Hex-Gruppen. Zwei Kürzungsregeln machen sie lesbar:

<!-- viz:ipv6-kompression -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>IPv6-Adressen komprimieren</title><style>
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
<h1 class=&quot;viz-title&quot;>IPv6-Adressen komprimieren</h1>
<p class=&quot;viz-sub&quot;>Führende Nullen weglassen und Null-Blöcke zu :: zusammenfassen</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 700 250&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>IPv6-Adressen komprimieren</title>
<rect x=&quot;40&quot; y=&quot;120&quot; width=&quot;620&quot; height=&quot;60&quot; rx=&quot;12&quot; fill=&quot;rgb(255,253,248)&quot; stroke=&quot;rgb(232,222,206)&quot;/>
<text id=&quot;addr&quot; x=&quot;350&quot; y=&quot;150&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot; font-family=&quot;monospace&quot; font-size=&quot;19&quot; font-weight=&quot;700&quot; fill=&quot;rgb(30,36,48)&quot;>FE80:0000:0000:0000:0000:0800:5A12:3456</text>
<text id=&quot;note&quot; x=&quot;350&quot; y=&quot;220&quot; text-anchor=&quot;middle&quot; font-size=&quot;13&quot; fill=&quot;rgb(95,107,122)&quot;></text>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Die volle 128-Bit-Adresse&quot;, &quot;set&quot;: [[&quot;addr&quot;, &quot;FE80:0000:0000:0000:0000:0800:5A12:3456&quot;], [&quot;note&quot;, &quot;8 Gruppen à 16 Bit, hexadezimal&quot;\|&quot;addr&quot;, &quot;FE80:0000:0000:0000:0000:0800:5A12:3456&quot;], [&quot;note&quot;, &quot;8 Gruppen à 16 Bit, hexadezimal&quot;]], &quot;show&quot;: [], &quot;blink&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Ausgangslage:</b> Eine IPv6-Adresse ist <b>128 Bit</b> lang — 8 Gruppen zu je 16 Bit (4 Hex-Ziffern), durch Doppelpunkte getrennt. Das ist lang und voller Nullen.&quot;}, {&quot;label&quot;: &quot;Regel 1: führende Nullen weglassen&quot;, &quot;set&quot;: [[&quot;addr&quot;, &quot;FE80:0:0:0:0:800:5A12:3456&quot;], [&quot;note&quot;, &quot;führende Nullen je Gruppe entfernt&quot;\|&quot;addr&quot;, &quot;FE80:0:0:0:0:800:5A12:3456&quot;], [&quot;note&quot;, &quot;führende Nullen je Gruppe entfernt&quot;]], &quot;show&quot;: [], &quot;blink&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Regel 1:</b> In jeder Gruppe dürfen <b>führende Nullen</b> entfallen: <code>0000 → 0</code>, <code>0800 → 800</code>.&quot;}, {&quot;label&quot;: &quot;Regel 2: längsten Nuller-Block zu ::&quot;, &quot;set&quot;: [[&quot;addr&quot;, &quot;FE80::800:5A12:3456&quot;], [&quot;note&quot;, &quot;ein zusammenhängender 0-Block → ::&quot;\|&quot;addr&quot;, &quot;FE80::800:5A12:3456&quot;], [&quot;note&quot;, &quot;ein zusammenhängender 0-Block → ::&quot;]], &quot;show&quot;: [], &quot;blink&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Regel 2:</b> Ein zusammenhängender Block aus <b>Null-Gruppen</b> wird durch <b>::</b> ersetzt — aber nur <b>einmal</b> pro Adresse (sonst mehrdeutig).&quot;}, {&quot;label&quot;: &quot;Fertig komprimiert&quot;, &quot;set&quot;: [[&quot;addr&quot;, &quot;FE80::800:5A12:3456&quot;], [&quot;note&quot;, &quot;kompakt &amp; eindeutig&quot;\|&quot;addr&quot;, &quot;FE80::800:5A12:3456&quot;], [&quot;note&quot;, &quot;kompakt &amp; eindeutig&quot;]], &quot;show&quot;: [], &quot;blink&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Ergebnis:</b> Aus 39 Zeichen werden 19. Weitere Notationen: <code>::1/128</code> = Loopback, <code>2000::/3</code> = globale Unicast-Adressen, <code>FF00::/8</code> = Multicast. IPv4 lässt sich einbetten: <code>::FFFF:142.35.67.23</code>.&quot;}];
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
</script></body></html>" width="100%" height="520" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:ipv6-kompression -->

Adressen sind **unicast/multicast/anycast** und gliedern sich in `<Global Routing Prefix><Subnet><Interface>`. Über das Präfix wird (provider-/geografisch) geroutet, was die Routing-Tabellen klein hält.

## Begleit-Protokolle & Migration
- **Neighbor Discovery (ND)** statt [[5 Vermittlungsschicht/ARP\|ARP]], **ICMPv6**, **DHCPv6**.
- Migration nur **inkrementell**: **Dual-Stack** (IPv4 + IPv6 parallel), **Tunnel** (z. B. 6to4), **Übersetzung**. Beispiel: IPv4-mapped `::FFFF:120.124.67.23`.

## Verwandte Notes
[[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]] · [[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket]] · [[5 Vermittlungsschicht/ARP\|ARP]] · [[5 Vermittlungsschicht/Routing-Protokolle\|Routing-Protokolle]] · [[5 Vermittlungsschicht/ICMP\|ICMP]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/ICMP\|⬅️ ICMP]]  ·  [[6 Transportschicht/6.0 Transportschicht (Übersicht)\|Kapitel 6: Transportschicht ➡️]]