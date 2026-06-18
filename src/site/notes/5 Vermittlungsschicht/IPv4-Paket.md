---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/IPv4-Paket/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T18:01:55.100+02:00","dg-note-properties":{"tags":["computernetworks","vermittlung"],"aliases":["IP-Paket","IPv4-Header","Datagram","TTL","Fragmentierung"]}}
---


# IPv4-Paket

> [!abstract] Auf einen Blick
> Ein **IP-Paket (Datagram)** besteht aus **Header + Nutzdaten**. Der Header trägt u. a. Quell-/Ziel-IP, **TTL**, **Protocol** und eine **Header-Prüfsumme**. IP bietet nur einen **unzuverlässigen** Dienst.

## Grundideen von IP
- **Konnektivität:** das Netz soll Teilausfälle verkraften → Übertragung in **Paketen**, minimale Anforderungen ans Netz.
- **Interoperabilität:** keine weitgehenden Annahmen über die darunterliegende Technik.

## Der Header
<!-- viz:ipv4-header -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>Aufbau des IPv4-Pakets</title><style>
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
<h1 class=&quot;viz-title&quot;>Aufbau des IPv4-Pakets</h1>
<p class=&quot;viz-sub&quot;>Die Felder des IP-Headers Schritt für Schritt</p>
<div class=&quot;steps-nav&quot; id=&quot;dots&quot;></div>
<div class=&quot;step-label&quot; id=&quot;step-label&quot;></div>
<div class=&quot;diagram-frame&quot;>
<svg viewBox=&quot;0 0 620 270&quot; id=&quot;stage-svg&quot; role=&quot;img&quot;><title>Aufbau des IPv4-Pakets</title>
<text class=&quot;tm&quot; x=&quot;40&quot; y=&quot;50&quot; fill=&quot;rgb(95,107,122)&quot;>Bit 0</text><text class=&quot;tm&quot; x=&quot;584&quot; y=&quot;50&quot; text-anchor=&quot;end&quot; fill=&quot;rgb(95,107,122)&quot;>31</text><g id=&quot;ip-ver&quot; class=&quot;c1 card&quot;><rect x=&quot;40&quot; y=&quot;60&quot; width=&quot;68&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;74.0&quot; y=&quot;78&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Ver</text></g><g id=&quot;ip-ihl&quot; class=&quot;c1 card&quot;><rect x=&quot;108&quot; y=&quot;60&quot; width=&quot;68&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;142.0&quot; y=&quot;78&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>IHL</text></g><g id=&quot;ip-tos&quot; class=&quot;c3 card&quot;><rect x=&quot;176&quot; y=&quot;60&quot; width=&quot;136&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;244.0&quot; y=&quot;78&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>TOS</text></g><g id=&quot;ip-len&quot; class=&quot;c2 card&quot;><rect x=&quot;312&quot; y=&quot;60&quot; width=&quot;272&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;448.0&quot; y=&quot;78&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Total Length</text></g><g id=&quot;ip-id&quot; class=&quot;c4 card&quot;><rect x=&quot;40&quot; y=&quot;100&quot; width=&quot;272&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;176.0&quot; y=&quot;118&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Identification</text></g><g id=&quot;ip-flg&quot; class=&quot;c6 card&quot;><rect x=&quot;312&quot; y=&quot;100&quot; width=&quot;51&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;337.5&quot; y=&quot;118&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Fl</text></g><g id=&quot;ip-fo&quot; class=&quot;c4 card&quot;><rect x=&quot;363&quot; y=&quot;100&quot; width=&quot;221&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;473.5&quot; y=&quot;118&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Fragment Offset</text></g><g id=&quot;ip-ttl&quot; class=&quot;c6 card&quot;><rect x=&quot;40&quot; y=&quot;140&quot; width=&quot;136&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;108.0&quot; y=&quot;158&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>TTL</text></g><g id=&quot;ip-pro&quot; class=&quot;c3 card&quot;><rect x=&quot;176&quot; y=&quot;140&quot; width=&quot;136&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;244.0&quot; y=&quot;158&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Protocol</text></g><g id=&quot;ip-chk&quot; class=&quot;c5 card&quot;><rect x=&quot;312&quot; y=&quot;140&quot; width=&quot;272&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;448.0&quot; y=&quot;158&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Header Checksum</text></g><g id=&quot;ip-src&quot; class=&quot;c1 card&quot;><rect x=&quot;40&quot; y=&quot;180&quot; width=&quot;544&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;312.0&quot; y=&quot;198&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Source Address (Quell-IP)</text></g><g id=&quot;ip-dst&quot; class=&quot;c2 card&quot;><rect x=&quot;40&quot; y=&quot;220&quot; width=&quot;544&quot; height=&quot;36&quot; rx=&quot;5&quot;/><text class=&quot;tm&quot; x=&quot;312.0&quot; y=&quot;238&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Destination Address (Ziel-IP)</text></g>
</svg></div>
<div class=&quot;step-description&quot; id=&quot;step-content&quot;></div>
<div class=&quot;btn-row&quot;>
<button class=&quot;btn&quot; id=&quot;btn-prev&quot; onclick=&quot;changeStep(-1)&quot;>Zur&amp;uuml;ck</button>
<button class=&quot;btn primary&quot; id=&quot;btn-next&quot; onclick=&quot;changeStep(1)&quot;>Weiter</button>
</div></div>
<script>
const steps = [{&quot;label&quot;: &quot;Der IPv4-Header (20 Byte ohne Optionen)&quot;, &quot;show&quot;: [], &quot;blink&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Überblick:</b> 32 Bit breit. Klicke dich durch die wichtigsten Felder.&quot;}, {&quot;label&quot;: &quot;Version &amp; IHL&quot;, &quot;blink&quot;: [&quot;ip-ver&quot;, &quot;ip-ihl&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Version</b> = 4 (oder 6). <b>IHL</b> = Header-Länge in 32-Bit-Worten (variabel wegen Optionen).&quot;}, {&quot;label&quot;: &quot;Total Length&quot;, &quot;blink&quot;: [&quot;ip-len&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Total Length:</b> Gesamtlänge des Pakets (Header + Daten), max. 64 KB.&quot;}, {&quot;label&quot;: &quot;Identification / Flags / Fragment Offset&quot;, &quot;blink&quot;: [&quot;ip-id&quot;, &quot;ip-flg&quot;, &quot;ip-fo&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>ID, Flags, Fragment Offset:</b> ermöglichen die <b>Fragmentierung</b> eines Pakets durch einen Router und das spätere Zusammensetzen.&quot;}, {&quot;label&quot;: &quot;Time To Live (TTL)&quot;, &quot;blink&quot;: [&quot;ip-ttl&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>TTL:</b> zählt die durchlaufenen Router herunter. Bei <b>0</b> wird das Paket verworfen (verhindert ewig kreisende Pakete). Bezug: ICMP TIME EXCEEDED, traceroute.&quot;}, {&quot;label&quot;: &quot;Protocol&quot;, &quot;blink&quot;: [&quot;ip-pro&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Protocol:</b> zu welchem Transport-Protokoll die Nutzdaten gehören — z. B. 6 = TCP, 17 = UDP, 1 = ICMP.&quot;}, {&quot;label&quot;: &quot;Header Checksum&quot;, &quot;blink&quot;: [&quot;ip-chk&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Header Checksum:</b> nur über den <b>Header</b>. Jeder Router prüft sie und muss sie wegen der sinkenden TTL <b>neu berechnen</b>. Fehlerhafte Pakete werden verworfen.&quot;}, {&quot;label&quot;: &quot;Quell- &amp; Ziel-Adresse&quot;, &quot;blink&quot;: [&quot;ip-src&quot;, &quot;ip-dst&quot;], &quot;show&quot;: [], &quot;hide&quot;: [], &quot;html&quot;: &quot;<b>Source/Destination Address:</b> die 32-Bit-IP-Adressen von Sender und Empfänger — die Basis für Forwarding und Longest Prefix Match.&quot;}];
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
<!-- /viz:ipv4-header -->

## Wichtige Felder kurz
- **TTL** — Hop-Zähler; bei 0 wird verworfen (→ [[5 Vermittlungsschicht/ICMP\|ICMP]], traceroute).
- **Protocol** — z. B. 6 = [[6 Transportschicht/TCP\|TCP]], 17 = [[6 Transportschicht/UDP\|UDP]], 1 = [[5 Vermittlungsschicht/ICMP\|ICMP]].
- **ID/Flags/Fragment Offset** — Fragmentierung.
- **Header Checksum** — nur über den Header, von jedem Router neu berechnet.

## Verwandte Notes
[[5 Vermittlungsschicht/IP-Adressen & CIDR\|IP-Adressen & CIDR]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[5 Vermittlungsschicht/ICMP\|ICMP]] · [[5 Vermittlungsschicht/IPv6\|IPv6]] · [[1 Grundlagen/Schichtenmodell\|Schichtenmodell]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/IP-Adressen & CIDR\|⬅️ IP-Adressen & CIDR]]  ·  [[5 Vermittlungsschicht/Longest Prefix Match\|Longest Prefix Match ➡️]]