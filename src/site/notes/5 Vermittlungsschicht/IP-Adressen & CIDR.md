---
{"dg-publish":true,"permalink":"/5 Vermittlungsschicht/IP-Adressen & CIDR/","tags":["computernetworks","vermittlung"],"updated":"2026-06-18T15:25:52.107+02:00","dg-note-properties":{"tags":["computernetworks","vermittlung"],"aliases":["IP-Adresse","CIDR","Netzmaske","Subnetz","Subnetting","private IP-Adressen"]}}
---


# IP-Adressen & CIDR

> [!abstract] Auf einen Blick
> Eine **IPv4-Adresse** ist eine 32-Bit-Größe (Dotted Decimal, z. B. `192.41.6.20`), die ein Interface identifiziert. Sie ist **hierarchisch**: `<Netz><Host>`. Die **Netzmaske** (CIDR-Präfix) legt die Grenze fest.

## Netz- und Host-Teil
- **Netz-Teil** — gemeinsam für alle Hosts eines Netzes; nur diesen müssen die meisten Router kennen (kleine Tabellen).
- **Host-Teil** — wählt den Ziel-Host innerhalb des Netzes.

## CIDR & Netzmaske
**Classless Inter-Domain Routing:** Die Grenze gibt ein Präfix `/sn` an, z. B. `134.73.17.5/22`. Äquivalent als Dotted-Decimal-Maske (`255.255.252.0`). Lokal kann der Host-Teil weiter in **Subnetze** unterteilt werden (`<netz><subnetz><host>`) — intern sichtbar, eigene Broadcast-Domain.

## Interaktiv: Subnetz-Rechner
Probiere es aus — IP eingeben, Präfix schieben:

<!-- viz:subnetz -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>Subnetz-Rechner (CIDR)</title><style>
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
.sub-row{display:flex;flex-wrap:wrap;gap:14px;justify-content:center;align-items:center;margin-bottom:14px}
.sub-ip{font-size:17px;font-weight:700;padding:8px 12px;border-radius:10px;border:1.5px solid #cfc5b4;background:#fffdf8;width:200px;text-align:center;font-family:monospace}
.sub-pl{font-weight:800;color:#2549b8;font-size:17px;min-width:46px;text-align:center}
.sub-slider{width:260px}
.sub-out{max-width:560px;margin:0 auto;background:#fffdf8;border:1px solid #e8dece;border-radius:16px;padding:8px 6px}
.sub-out table{width:100%;border-collapse:collapse;font-size:14px}
.sub-out td{padding:7px 12px;border-bottom:1px solid #efe7d8}
.sub-out td:first-child{color:#5f6b7a;font-weight:600}
.sub-out td:last-child{font-family:monospace;font-weight:700;text-align:right;color:#1e2430}
.sub-bits{font-family:monospace;font-size:13px;text-align:center;margin:10px auto 0;letter-spacing:1px;word-break:break-all}
.bn{color:#2549b8;font-weight:700}.bh{color:#c67a00;font-weight:700}
.sub-err{color:#cc3b2a;text-align:center;font-weight:700}
</style></head>
<body><div class=&quot;widget&quot;>
<h1 class=&quot;viz-title&quot;>Subnetz-Rechner (CIDR)</h1>
<p class=&quot;viz-sub&quot;>IP eingeben, Präfix schieben — Netz, Broadcast &amp; Host-Bereich live</p>
<div class=&quot;sub-row&quot;>
  <input id=&quot;ip&quot; class=&quot;sub-ip&quot; value=&quot;192.168.10.130&quot; />
  <span style=&quot;font-size:17px;font-weight:800&quot;>/</span>
  <input id=&quot;pl&quot; type=&quot;range&quot; min=&quot;0&quot; max=&quot;32&quot; value=&quot;26&quot; class=&quot;sub-slider&quot; oninput=&quot;calc()&quot;/>
  <span id=&quot;pllbl&quot; class=&quot;sub-pl&quot;>/26</span>
</div>
<div class=&quot;sub-out&quot;><table id=&quot;tbl&quot;></table><div id=&quot;bits&quot; class=&quot;sub-bits&quot;></div></div>
</div>
<script>
function ipToInt(s){const p=s.trim().split('.');if(p.length!==4)return null;let n=0;for(const x of p){const v=+x;if(!(v>=0&amp;&amp;v<=255)||x==='')return null;n=(n*256)+v;}return n>>>0;}
function intToIp(n){return [(n>>>24)&amp;255,(n>>>16)&amp;255,(n>>>8)&amp;255,n&amp;255].join('.');}
function bits32(n){let s='';for(let i=31;i>=0;i--){s+=((n>>>i)&amp;1);if(i%8===0&amp;&amp;i>0)s+=' ';}return s;}
function calc(){
  const ipv=document.getElementById('ip').value;
  const pl=+document.getElementById('pl').value;
  document.getElementById('pllbl').textContent='/'+pl;
  const ip=ipToInt(ipv);
  const tbl=document.getElementById('tbl');const bits=document.getElementById('bits');
  if(ip===null){tbl.innerHTML='<tr><td colspan=2 class=sub-err>Ungültige IPv4-Adresse</td></tr>';bits.innerHTML='';return;}
  const mask=pl===0?0:((0xFFFFFFFF<<(32-pl))>>>0);
  const net=(ip&amp;mask)>>>0;const bc=(net|((~mask)>>>0))>>>0;
  const total=Math.pow(2,32-pl);
  let hosts, first, last;
  if(pl>=31){hosts=(pl===32?1:2);first='—';last='—';}
  else{hosts=total-2;first=intToIp((net+1)>>>0);last=intToIp((bc-1)>>>0);}
  tbl.innerHTML=
   `<tr><td>Netzmaske</td><td>${intToIp(mask)}  (/${pl})</td></tr>`+
   `<tr><td>Netz-ID</td><td>${intToIp(net)}</td></tr>`+
   `<tr><td>Broadcast</td><td>${intToIp(bc)}</td></tr>`+
   `<tr><td>Erster Host</td><td>${first}</td></tr>`+
   `<tr><td>Letzter Host</td><td>${last}</td></tr>`+
   `<tr><td>Nutzbare Hosts</td><td>${hosts.toLocaleString('de-DE')}</td></tr>`;
  // bit view: net bits blue, host bits amber, based on the IP
  let s='';for(let i=31;i>=0;i--){const b=(ip>>>i)&amp;1;const cls=(31-i)<pl?'bn':'bh';s+=`<span class=&quot;${cls}&quot;>${b}</span>`;if(i%8===0&amp;&amp;i>0)s+=' ';}
  bits.innerHTML='<div>Netzanteil (<span class=bn>blau</span>) · Hostanteil (<span class=bh>orange</span>)</div>'+s;
}
document.getElementById('ip').addEventListener('input',calc);
calc();
</script></body></html>" width="100%" height="520" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:subnetz -->

> [!info] Spezielle Adressen
> Host-Teil **alle 0** = Netz-ID, **alle 1** = Broadcast (z. B. `255.255.255.255`). Privat (nicht im Internet routbar): `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`. `127.0.0.0/8` = Loopback.

## Verwandte Notes
[[5 Vermittlungsschicht/Longest Prefix Match\|Longest Prefix Match]] · [[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket]] · [[5 Vermittlungsschicht/Routing & Forwarding\|Routing & Forwarding]] · [[5 Vermittlungsschicht/IPv6\|IPv6]] · [[5 Vermittlungsschicht/DHCP\|DHCP]]

[[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[5 Vermittlungsschicht/Routing-Protokolle\|⬅️ Routing-Protokolle]]  ·  [[5 Vermittlungsschicht/IPv4-Paket\|IPv4-Paket ➡️]]