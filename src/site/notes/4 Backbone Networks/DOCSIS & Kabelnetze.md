---
{"dg-publish":true,"permalink":"/4 Backbone Networks/DOCSIS & Kabelnetze/","tags":["computernetworks","backbone"],"updated":"2026-06-18T15:04:04.898+02:00","dg-note-properties":{"tags":["computernetworks","backbone"],"aliases":["DOCSIS","HFC","Kabelfernsehen","Hybrid Fiber Coax"]}}
---


# DOCSIS & Kabelnetze

> [!abstract] Auf einen Blick
> Kabelfernseh-Anbieter nutzen ein **hybrides Netz aus Glasfaser und Koax (HFC)**. Das Protokoll **DOCSIS** (Data Over Cable Service Interface Specification) ist ein **Breitband-Netz** mit einer Reichweite **zwischen** reinem Access und Backbone.

## Aufbau (HFC)
<!-- viz:hfc -->
<iframe srcdoc="<!DOCTYPE html>
<html lang=&quot;de&quot;><head><meta charset=&quot;UTF-8&quot;>
<meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;>
<title>DOCSIS / HFC-Netz</title><style>
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
<body><div class=&quot;widget&quot;>
<h1 class=&quot;viz-title&quot;>DOCSIS / HFC-Netz</h1>
<p class=&quot;viz-sub&quot;>Vom Headend über Glasfaser und Koax zum Haushalt</p>
<div class=&quot;diagram-frame&quot;><svg viewBox=&quot;0 0 700 240&quot; role=&quot;img&quot;>
<defs><marker id=&quot;arrow&quot; viewBox=&quot;0 0 10 10&quot; refX=&quot;8&quot; refY=&quot;5&quot; markerWidth=&quot;7&quot; markerHeight=&quot;7&quot; orient=&quot;auto-start-reverse&quot;><path d=&quot;M2 1L8 5L2 9&quot; fill=&quot;none&quot; stroke=&quot;context-stroke&quot; stroke-width=&quot;1.6&quot; stroke-linecap=&quot;round&quot; stroke-linejoin=&quot;round&quot;/></marker></defs>
<g class=&quot;c3 card&quot;><rect x=&quot;20&quot; y=&quot;90&quot; width=&quot;120&quot; height=&quot;56&quot; rx=&quot;11&quot;/><text class=&quot;ts&quot; x=&quot;80&quot; y=&quot;112&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Headend</text><text class=&quot;tm&quot; x=&quot;80&quot; y=&quot;130&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>TV/Sat/Internet</text></g>
<g class=&quot;c1 card&quot;><rect x=&quot;190&quot; y=&quot;90&quot; width=&quot;110&quot; height=&quot;56&quot; rx=&quot;11&quot;/><text class=&quot;ts&quot; x=&quot;245&quot; y=&quot;112&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Hub</text><text class=&quot;tm&quot; x=&quot;245&quot; y=&quot;130&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>regional</text></g>
<g class=&quot;c2 card&quot;><rect x=&quot;350&quot; y=&quot;90&quot; width=&quot;120&quot; height=&quot;56&quot; rx=&quot;11&quot;/><text class=&quot;ts&quot; x=&quot;410&quot; y=&quot;112&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Optical Node</text><text class=&quot;tm&quot; x=&quot;410&quot; y=&quot;130&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Licht → Strom</text></g>
<g class=&quot;c6 card&quot;><rect x=&quot;540&quot; y=&quot;60&quot; width=&quot;130&quot; height=&quot;38&quot; rx=&quot;10&quot;/><text class=&quot;tm&quot; x=&quot;605&quot; y=&quot;79&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Haushalt 1</text></g>
<g class=&quot;c6 card&quot;><rect x=&quot;540&quot; y=&quot;108&quot; width=&quot;130&quot; height=&quot;38&quot; rx=&quot;10&quot;/><text class=&quot;tm&quot; x=&quot;605&quot; y=&quot;127&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>Haushalt 2</text></g>
<g class=&quot;c6 card&quot;><rect x=&quot;540&quot; y=&quot;156&quot; width=&quot;130&quot; height=&quot;38&quot; rx=&quot;10&quot;/><text class=&quot;tm&quot; x=&quot;605&quot; y=&quot;175&quot; text-anchor=&quot;middle&quot; dominant-baseline=&quot;central&quot;>… (Shared Coax)</text></g>
<line x1=&quot;140&quot; y1=&quot;118&quot; x2=&quot;188&quot; y2=&quot;118&quot; class=&quot;arr&quot; stroke=&quot;#8a7a5e&quot; marker-end=&quot;url(#arrow)&quot;/>
<line x1=&quot;300&quot; y1=&quot;118&quot; x2=&quot;348&quot; y2=&quot;118&quot; class=&quot;arr&quot; stroke=&quot;#8a7a5e&quot; marker-end=&quot;url(#arrow)&quot;/>
<text class=&quot;tm&quot; x=&quot;244&quot; y=&quot;80&quot; text-anchor=&quot;middle&quot; fill=&quot;#2f8f4e&quot;>Glasfaser</text>
<line x1=&quot;470&quot; y1=&quot;118&quot; x2=&quot;538&quot; y2=&quot;79&quot; class=&quot;arr&quot; stroke=&quot;#cc5a42&quot; marker-end=&quot;url(#arrow)&quot;/>
<line x1=&quot;470&quot; y1=&quot;118&quot; x2=&quot;538&quot; y2=&quot;127&quot; class=&quot;arr&quot; stroke=&quot;#cc5a42&quot; marker-end=&quot;url(#arrow)&quot;/>
<line x1=&quot;470&quot; y1=&quot;118&quot; x2=&quot;538&quot; y2=&quot;175&quot; class=&quot;arr&quot; stroke=&quot;#cc5a42&quot; marker-end=&quot;url(#arrow)&quot;/>
<text class=&quot;tm&quot; x=&quot;505&quot; y=&quot;210&quot; text-anchor=&quot;middle&quot; fill=&quot;#cc5a42&quot;>Koax (Shared Medium)</text>
</svg></div>
<p style=&quot;text-align:center;color:#5f6b7a;font-size:13px;max-width:620px;margin:14px auto 0&quot;>
Hybrid Fiber-Coax (HFC): Glasfaser bis zur <b>Optical Node</b> (versorgt einige hundert Haushalte), dann <b>Koax</b> als geteiltes Medium. <b>DOCSIS</b> nutzt Frequenz-Multiplexing; Version 4 theoretisch bis ~22 Gbit/s.</p>
</div>
<script></script></body></html>" width="100%" height="440" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:hfc -->

Das **Headend** erhält Signale (TV, Satellit, Internet) und verteilt sie an regionale **Hubs**. Über **Glasfaser** geht es zu **Optical Nodes**, die in elektrische Signale für **Koax** umwandeln. Eine Optical Node versorgt einige hundert Haushalte — das Koax ist damit ein **Shared Medium**.

## Eigenschaften
DOCSIS spezifiziert die Ebenen 1 und 2 und erlaubt unterschiedliche Implementierungen: verschiedene Modulationen/Bandbreiten, **Frequenz-Multiplexing** und QoS. Version 4 erreicht theoretisch bis ~22 Gbit/s.

## Verwandte Notes
[[4 Backbone Networks/Backbone Grundlagen\|Backbone Grundlagen]] · [[4 Backbone Networks/SONET, SDH & DWDM\|SONET, SDH & DWDM]] · [[3 Access Networks/DSL\|DSL]] · [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]]

[[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[4 Backbone Networks/SONET, SDH & DWDM\|⬅️ SONET, SDH & DWDM]]  ·  [[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|Kapitel 5: Vermittlungsschicht ➡️]]