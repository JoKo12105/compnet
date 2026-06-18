---
{"dg-publish":true,"permalink":"/4 Backbone Networks/DOCSIS & Kabelnetze/","tags":["computernetworks","backbone"],"updated":"2026-06-18T18:28:32.019+02:00","dg-note-properties":{"tags":["computernetworks","backbone"],"aliases":["DOCSIS","HFC","Kabelfernsehen","Hybrid Fiber Coax"]}}
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
<line x1=&quot;140&quot; y1=&quot;118&quot; x2=&quot;188&quot; y2=&quot;118&quot; class=&quot;arr&quot; stroke=&quot;rgb(138,122,94)&quot; marker-end=&quot;url(#arrow)&quot;/>
<line x1=&quot;300&quot; y1=&quot;118&quot; x2=&quot;348&quot; y2=&quot;118&quot; class=&quot;arr&quot; stroke=&quot;rgb(138,122,94)&quot; marker-end=&quot;url(#arrow)&quot;/>
<text class=&quot;tm&quot; x=&quot;244&quot; y=&quot;80&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(47,143,78)&quot;>Glasfaser</text>
<line x1=&quot;470&quot; y1=&quot;118&quot; x2=&quot;538&quot; y2=&quot;79&quot; class=&quot;arr&quot; stroke=&quot;rgb(204,90,66)&quot; marker-end=&quot;url(#arrow)&quot;/>
<line x1=&quot;470&quot; y1=&quot;118&quot; x2=&quot;538&quot; y2=&quot;127&quot; class=&quot;arr&quot; stroke=&quot;rgb(204,90,66)&quot; marker-end=&quot;url(#arrow)&quot;/>
<line x1=&quot;470&quot; y1=&quot;118&quot; x2=&quot;538&quot; y2=&quot;175&quot; class=&quot;arr&quot; stroke=&quot;rgb(204,90,66)&quot; marker-end=&quot;url(#arrow)&quot;/>
<text class=&quot;tm&quot; x=&quot;505&quot; y=&quot;210&quot; text-anchor=&quot;middle&quot; fill=&quot;rgb(204,90,66)&quot;>Koax (Shared Medium)</text>
</svg></div>
<p style=&quot;text-align:center;color:rgb(170,182,200);font-size:13px;max-width:620px;margin:14px auto 0&quot;>
Hybrid Fiber-Coax (HFC): Glasfaser bis zur <b>Optical Node</b> (versorgt einige hundert Haushalte), dann <b>Koax</b> als geteiltes Medium. <b>DOCSIS</b> nutzt Frequenz-Multiplexing; Version 4 theoretisch bis ~22 Gbit/s.</p>
</div>
<script></script></body></html>" width="100%" height="520" loading="lazy" sandbox="allow-scripts allow-popups" style="border:none;width:100%;background:transparent" scrolling="no"></iframe>
<!-- /viz:hfc -->

Das **Headend** erhält Signale (TV, Satellit, Internet) und verteilt sie an regionale **Hubs**. Über **Glasfaser** geht es zu **Optical Nodes**, die in elektrische Signale für **Koax** umwandeln. Eine Optical Node versorgt einige hundert Haushalte — das Koax ist damit ein **Shared Medium**.

## Eigenschaften
DOCSIS spezifiziert die Ebenen 1 und 2 und erlaubt unterschiedliche Implementierungen: verschiedene Modulationen/Bandbreiten, **Frequenz-Multiplexing** und QoS. Version 4 erreicht theoretisch bis ~22 Gbit/s.

## Verwandte Themen
[[4 Backbone Networks/Backbone Grundlagen\|Backbone Grundlagen]] · [[4 Backbone Networks/SONET, SDH & DWDM\|SONET, SDH & DWDM]] · [[3 Access Networks/DSL\|DSL]] · [[2 Link Layer/MAC – Medienzugang\|MAC – Medienzugang]]

[[4 Backbone Networks/4.0 Backbone Networks (Übersicht)\|← Kapitelübersicht]]

---
<!-- kapitel-nav -->
[[4 Backbone Networks/SONET, SDH & DWDM\|⬅️ SONET, SDH & DWDM]]  ·  [[5 Vermittlungsschicht/5.0 Vermittlungsschicht (Übersicht)\|Kapitel 5: Vermittlungsschicht ➡️]]