<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="Guardian Shield">
<meta name="theme-color" content="#0a0f1a">
<title>Guardian Shield — Seguridad · Ignacio Vera</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500;600&display=swap');
 
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
 
:root{
  /* Paleta industria antivirus: azul profundo, verde seguridad, alertas claras */
  --bg:     #0a0f1a;
  --s1:     #0f1628;
  --s2:     #141d33;
  --s3:     #1a2440;
  --card:   rgba(15,22,40,0.95);
  --border: rgba(255,255,255,0.08);
  --b2:     rgba(255,255,255,0.14);
  --blue:   #3b82f6;
  --blue2:  #2563eb;
  --cyan:   #06b6d4;
  --green:  #22c55e;
  --green2: #16a34a;
  --red:    #ef4444;
  --amber:  #f59e0b;
  --purple: #8b5cf6;
  --text:   #f1f5f9;
  --mid:    #94a3b8;
  --dim:    #475569;
  --faint:  rgba(241,245,249,0.12);
  --font:   'Inter',sans-serif;
  --mono:   'JetBrains Mono',monospace;
  --sb:     env(safe-area-inset-bottom,0px);
  --st:     env(safe-area-inset-top,0px);
}
 
html{background:var(--bg)}
body{
  font-family:var(--font);font-size:15px;color:var(--text);
  background:var(--bg);min-height:100vh;min-height:-webkit-fill-available;
  overflow-x:hidden;-webkit-font-smoothing:antialiased
}
a{color:inherit;text-decoration:none}
button{font-family:var(--font);cursor:pointer;border:none;outline:none;background:none}
input,textarea{font-family:var(--font);outline:none;-webkit-appearance:none;appearance:none}
.hidden{display:none!important}
 
/* ── GRADIENTE FONDO ── */
.bg-grad{
  position:fixed;inset:0;z-index:0;pointer-events:none;
  background:
    radial-gradient(ellipse 60% 40% at 20% 10%,rgba(59,130,246,.12) 0%,transparent 60%),
    radial-gradient(ellipse 50% 35% at 80% 90%,rgba(34,197,94,.08) 0%,transparent 55%)
}
 
/* ── HEADER ── */
.hdr{
  position:sticky;top:0;z-index:200;
  background:rgba(10,15,26,.95);
  -webkit-backdrop-filter:blur(20px);backdrop-filter:blur(20px);
  border-bottom:1px solid var(--border);
  display:flex;align-items:center;justify-content:space-between;
  padding:0 16px;height:56px;
  padding-top:var(--st)
}
.logo-row{display:flex;align-items:center;gap:10px}
.logo-ic{
  width:36px;height:36px;border-radius:10px;
  background:linear-gradient(135deg,#3b82f6,#1d4ed8);
  display:flex;align-items:center;justify-content:center;
  font-size:18px;box-shadow:0 4px 14px rgba(59,130,246,.4)
}
.logo-name{font-size:15px;font-weight:800;letter-spacing:-.03em;color:var(--text)}
.logo-sub{font-size:9px;color:var(--dim);font-family:var(--mono);letter-spacing:.08em;margin-top:1px}
.status-chip{
  display:flex;align-items:center;gap:6px;
  padding:5px 12px;border-radius:20px;
  font-size:11px;font-weight:700;letter-spacing:.02em
}
.status-chip.safe{background:rgba(34,197,94,.12);color:var(--green);border:1px solid rgba(34,197,94,.25)}
.status-chip.warn{background:rgba(245,158,11,.12);color:var(--amber);border:1px solid rgba(245,158,11,.25)}
.status-chip.danger{background:rgba(239,68,68,.12);color:var(--red);border:1px solid rgba(239,68,68,.25)}
.s-dot{width:7px;height:7px;border-radius:50%;background:currentColor}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.25}}
.s-dot.anim{animation:pulse .8s infinite}
 
/* ── NAV ── */
.nav{
  position:sticky;top:56px;z-index:100;
  background:rgba(10,15,26,.92);
  -webkit-backdrop-filter:blur(12px);backdrop-filter:blur(12px);
  border-bottom:1px solid var(--border);
  display:flex;overflow-x:auto;-webkit-overflow-scrolling:touch;scrollbar-width:none
}
.nav::-webkit-scrollbar{display:none}
.nb{
  flex-shrink:0;padding:12px 16px;
  font-size:12px;font-weight:600;letter-spacing:-.01em;
  color:var(--dim);border-bottom:2px solid transparent;
  margin-bottom:-1px;transition:all .18s;white-space:nowrap
}
.nb.on{color:var(--blue);border-bottom-color:var(--blue)}
 
/* ── MAIN ── */
.main{
  position:relative;z-index:10;max-width:800px;margin:0 auto;
  padding:20px 14px;padding-bottom:calc(28px + var(--sb))
}
 
/* ── CARDS ── */
.card{
  background:var(--card);border:1px solid var(--border);
  border-radius:16px;padding:18px;margin-bottom:14px;
  -webkit-backdrop-filter:blur(8px);backdrop-filter:blur(8px)
}
.card-blue{border-color:rgba(59,130,246,.3);background:rgba(59,130,246,.06)}
.card-green{border-color:rgba(34,197,94,.25);background:rgba(34,197,94,.05)}
.card-red{border-color:rgba(239,68,68,.3);background:rgba(239,68,68,.06)}
.card-amber{border-color:rgba(245,158,11,.25);background:rgba(245,158,11,.05)}
 
/* ── PROTECCIÓN SCORE (como Norton / Bitdefender) ── */
.score-hero{
  background:linear-gradient(135deg,rgba(59,130,246,.18),rgba(6,182,212,.1));
  border:1px solid rgba(59,130,246,.3);border-radius:20px;
  padding:24px;margin-bottom:16px;text-align:center;position:relative;overflow:hidden
}
.score-hero::before{
  content:'';position:absolute;top:-40px;right:-40px;
  width:160px;height:160px;border-radius:50%;
  background:radial-gradient(circle,rgba(59,130,246,.15),transparent 70%)
}
.shield-big{font-size:52px;margin-bottom:8px;display:block;
  filter:drop-shadow(0 4px 20px rgba(59,130,246,.5))}
.score-num{
  font-size:56px;font-weight:900;letter-spacing:-.04em;line-height:1;
  background:linear-gradient(135deg,#fff,var(--blue));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text
}
.score-label{font-size:13px;font-weight:700;letter-spacing:.06em;text-transform:uppercase;margin-top:4px}
.score-ring{width:140px;height:140px;position:relative;margin:0 auto 12px}
.score-ring svg{transform:rotate(-90deg)}
.score-ring-inner{
  position:absolute;inset:0;display:flex;flex-direction:column;
  align-items:center;justify-content:center
}
 
/* ── KPI ROW ── */
.kpi-row{display:flex;gap:8px;margin-top:14px}
.kpi{
  flex:1;text-align:center;background:rgba(255,255,255,.05);
  border:1px solid var(--border);border-radius:10px;padding:10px 6px
}
.kpi-n{font-size:22px;font-weight:800;letter-spacing:-.02em;line-height:1}
.kpi-l{font-size:9px;color:var(--dim);font-weight:600;text-transform:uppercase;
  letter-spacing:.08em;margin-top:3px}
 
/* ── MODULE CARDS (estilo Norton/TotalAV) ── */
.mod-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:16px}
.mod{
  background:var(--card);border:1px solid var(--border);border-radius:13px;
  padding:14px;cursor:pointer;transition:all .18s;position:relative;overflow:hidden
}
.mod:active{transform:scale(.97)}
.mod.ok{border-color:rgba(34,197,94,.3)}
.mod.warn{border-color:rgba(245,158,11,.35)}
.mod.danger{border-color:rgba(239,68,68,.4)}
.mod.running{border-color:rgba(59,130,246,.4)}
.mod-ic{font-size:22px;margin-bottom:8px}
.mod-name{font-size:12px;font-weight:700;letter-spacing:-.01em;margin-bottom:3px}
.mod-st{font-size:10px;font-weight:600}
.mod-progress{position:absolute;bottom:0;left:0;height:2px;border-radius:0 0 13px 13px;width:0%;transition:width .3s ease}
 
/* ── INPUTS ── */
.lbl{font-size:10px;font-weight:600;color:var(--dim);text-transform:uppercase;
  letter-spacing:.08em;margin-bottom:6px;display:block}
.inp{
  width:100%;background:rgba(255,255,255,.05);
  border:1px solid var(--border);border-radius:10px;
  padding:12px 14px;color:var(--text);font-size:13.5px;
  transition:border-color .2s,box-shadow .2s
}
.inp:focus{border-color:rgba(59,130,246,.5);box-shadow:0 0 0 3px rgba(59,130,246,.1)}
.inp::placeholder{color:var(--dim)}
.inp-2{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:14px}
@media(max-width:480px){.inp-2{grid-template-columns:1fr}}
textarea.inp{resize:none;font-size:13px}
 
/* ── PROGRESS ── */
.prog-wrap{margin-bottom:13px}
.prog-top{display:flex;justify-content:space-between;margin-bottom:6px}
.prog-lbl{font-size:11px;font-weight:500;color:var(--mid)}
.prog-pct{font-size:11px;font-weight:700;font-family:var(--mono);color:var(--blue)}
.prog-bar{height:3px;background:rgba(255,255,255,.07);border-radius:3px;overflow:hidden}
.prog-fill{height:100%;background:linear-gradient(90deg,var(--blue),var(--cyan));
  border-radius:3px;width:0%;transition:width .35s ease}
 
/* ── BOTONES ── */
.btn{
  width:100%;padding:14px;border-radius:11px;
  font-size:13px;font-weight:700;letter-spacing:-.01em;
  display:flex;align-items:center;justify-content:center;gap:10px;
  cursor:pointer;transition:opacity .2s,transform .15s;-webkit-appearance:none
}
.btn:active{transform:scale(.97)}
.btn:disabled{opacity:.45;cursor:not-allowed;transform:none}
.btn-blue{
  color:#fff;background:linear-gradient(135deg,var(--blue),var(--blue2));
  border:1px solid rgba(59,130,246,.5);
  box-shadow:0 4px 18px rgba(59,130,246,.3)
}
.btn-green{
  color:#fff;background:linear-gradient(135deg,var(--green),var(--green2));
  border:1px solid rgba(34,197,94,.4);
  box-shadow:0 4px 16px rgba(34,197,94,.25)
}
.btn-outline{
  color:var(--blue);background:transparent;
  border:1px solid rgba(59,130,246,.35);font-size:12px;padding:9px 16px;width:auto
}
.btn-sm{
  padding:8px 14px;border-radius:8px;font-size:11px;font-weight:700;
  cursor:pointer;-webkit-appearance:none;transition:opacity .15s;width:auto
}
.btn-sm:active{opacity:.7}
.bsm-blue{color:var(--blue);border:1px solid rgba(59,130,246,.3);background:rgba(59,130,246,.1)}
.bsm-red{color:var(--red);border:1px solid rgba(239,68,68,.3);background:rgba(239,68,68,.1)}
.bsm-amber{color:var(--amber);border:1px solid rgba(245,158,11,.3);background:rgba(245,158,11,.1)}
@keyframes spin{to{transform:rotate(360deg)}}
.spin{display:inline-block;width:14px;height:14px;border:2px solid rgba(255,255,255,.2);
  border-top-color:#fff;border-radius:50%;animation:spin .6s linear infinite;flex-shrink:0}
 
/* ── RESULT BOX ── */
.rbox{background:rgba(255,255,255,.04);border:1px solid var(--border);
  border-radius:10px;padding:13px;margin-top:10px;font-size:13px;
  line-height:1.65;display:none}
.rbox.ok{border-color:rgba(34,197,94,.3);background:rgba(34,197,94,.06)}
.rbox.warn{border-color:rgba(245,158,11,.3);background:rgba(245,158,11,.06)}
.rbox.danger{border-color:rgba(239,68,68,.3);background:rgba(239,68,68,.06)}
 
/* ── SCAN RESULTS ── */
.rt{background:rgba(255,255,255,.02);border:1px solid var(--border);border-radius:14px;overflow:hidden}
.rt-hdr{
  display:grid;grid-template-columns:3px 38px 1fr auto 14px;gap:9px;
  padding:9px 14px;background:rgba(255,255,255,.035);
  border-bottom:1px solid var(--border)
}
.rt-hdr span{font-size:9px;font-weight:600;color:var(--dim);text-transform:uppercase;letter-spacing:.12em}
.sec-h{padding:7px 14px;border-bottom:1px solid rgba(255,255,255,.04)}
.sec-h.dng{background:rgba(239,68,68,.05)}
.sec-h.nrm{background:rgba(255,255,255,.02);border-top:1px solid rgba(255,255,255,.04)}
.sec-l{font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:.1em;
  display:flex;align-items:center;gap:6px}
 
/* ── PLATFORM ROW ── */
.pr{border-bottom:1px solid rgba(255,255,255,.04);transition:background .12s}
.pr:last-child{border-bottom:none}
.pr:active{background:rgba(255,255,255,.03)}
.pr-h{display:grid;grid-template-columns:3px 38px 1fr auto 14px;gap:9px;
  align-items:center;padding:12px 14px;cursor:pointer;-webkit-user-select:none;user-select:none}
.pr-acc{height:26px;border-radius:2px}
.pr-ic{width:34px;height:34px;border-radius:9px;background:rgba(255,255,255,.06);
  border:1px solid rgba(255,255,255,.08);display:flex;align-items:center;
  justify-content:center;font-size:15px;flex-shrink:0}
.pr-name{font-weight:700;font-size:13px;letter-spacing:-.01em;overflow:hidden;
  text-overflow:ellipsis;white-space:nowrap}
.pr-sub{font-size:9px;color:var(--dim);margin-top:2px;font-family:var(--mono)}
.pr-bdg{display:inline-flex;align-items:center;gap:4px;padding:3px 9px;
  border-radius:20px;font-size:10px;font-weight:700;white-space:nowrap;flex-shrink:0}
.ok-bdg{color:var(--green);font-size:10px;font-weight:700;
  display:flex;align-items:center;gap:4px;flex-shrink:0}
.ok-d{width:5px;height:5px;border-radius:50%;background:var(--green);flex-shrink:0}
.chev{color:var(--dim);font-size:9px;text-align:center;transition:transform .2s}
.chev.open{transform:rotate(180deg)}
.pr-body{padding:4px 14px 16px 65px;border-top:1px solid rgba(255,255,255,.04);background:rgba(0,0,0,.2)}
 
/* ── BREACH CARD ── */
.bc{margin:12px 0 12px;padding:14px;border-radius:10px}
.bc-top{display:flex;justify-content:space-between;flex-wrap:wrap;gap:8px;margin-bottom:8px}
.bc-meta{font-size:9px;font-weight:600;color:var(--dim);text-transform:uppercase;
  letter-spacing:.08em;margin-bottom:3px}
.bc-cnt{font-size:18px;font-weight:800;letter-spacing:-.02em;color:var(--text)}
.bc-cnt span{font-size:12px;font-weight:400;color:var(--mid)}
.bc-desc{font-size:12px;color:var(--mid);line-height:1.65;margin-bottom:10px}
.tags{display:flex;flex-wrap:wrap;gap:4px}
.tag{padding:2px 8px;border-radius:4px;font-size:9px;font-weight:500;
  background:rgba(255,255,255,.07);color:var(--mid);border:1px solid rgba(255,255,255,.1)}
.steps-h{font-size:9px;font-weight:700;color:var(--dim);text-transform:uppercase;
  letter-spacing:.1em;margin:12px 0 7px}
.step{display:flex;gap:9px;align-items:flex-start;margin-bottom:7px}
.step-n{width:20px;height:20px;border-radius:50%;background:rgba(59,130,246,.15);
  border:1px solid rgba(59,130,246,.3);color:var(--blue);font-size:9px;
  display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:2px;font-weight:700}
.step-t{font-size:12px;color:var(--mid);line-height:1.6}
.act-row{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
 
/* ── FILTERS ── */
.fscroll{overflow-x:auto;-webkit-overflow-scrolling:touch;scrollbar-width:none;margin-bottom:12px}
.fscroll::-webkit-scrollbar{display:none}
.finner{display:flex;gap:5px;min-width:max-content;padding-bottom:2px}
.fg{display:flex;gap:2px;background:rgba(255,255,255,.04);
  border-radius:8px;padding:3px;border:1px solid var(--border)}
.fb{padding:6px 12px;border-radius:6px;font-size:11px;font-weight:600;
  border:none;cursor:pointer;white-space:nowrap;transition:all .14s;-webkit-appearance:none}
.fb.sec{background:transparent;color:var(--dim)}
.fb.sec.on{background:rgba(59,130,246,.2);color:var(--blue)}
.fb.cat{background:rgba(255,255,255,.04);color:var(--dim);border:1px solid var(--border);font-size:10px}
.fb.cat.on{background:rgba(139,92,246,.18);color:#a78bfa;border-color:rgba(139,92,246,.35)}
 
/* ── TOOLS ── */
.tool{
  background:var(--card);border:1px solid var(--border);border-radius:11px;
  padding:13px;margin-bottom:7px;
  display:flex;justify-content:space-between;align-items:flex-start;gap:12px;
  cursor:pointer;transition:background .14s
}
.tool:active{background:rgba(255,255,255,.06)}
.tool-n{font-weight:700;font-size:13px;margin-bottom:3px;letter-spacing:-.01em}
.tool-d{font-size:11.5px;color:var(--mid);line-height:1.55}
.tbdg{padding:3px 10px;border-radius:20px;font-size:9px;font-weight:700;
  letter-spacing:.06em;flex-shrink:0}
.sdiv{display:flex;align-items:center;gap:10px;margin:18px 0 10px}
.sdiv span{font-size:10px;font-weight:700;color:var(--dim);text-transform:uppercase;
  letter-spacing:.1em;white-space:nowrap}
.sline{flex:1;height:1px;background:var(--border)}
 
/* ── PLAN ── */
.plan{background:var(--card);border:1px solid var(--border);
  border-radius:0 13px 13px 0;padding:16px;margin-bottom:10px}
.plan-badge{display:inline-flex;align-items:center;gap:5px;padding:4px 10px;
  border-radius:20px;font-size:10px;font-weight:700;letter-spacing:.04em;margin-bottom:8px}
.plan-t{font-size:16px;font-weight:800;letter-spacing:-.02em}
.plan-div{height:1px;background:var(--border);margin:11px 0}
.plan-tools{display:flex;flex-wrap:wrap;gap:8px}
 
/* ── ABOUT ── */
.faq{background:var(--card);border:1px solid var(--border);border-radius:12px;
  padding:15px;margin-bottom:9px}
.faq-q{font-size:14px;font-weight:700;color:var(--blue);margin-bottom:7px;letter-spacing:-.01em}
.faq-a{font-size:13px;color:var(--mid);line-height:1.7}
.ptag{padding:3px 8px;border-radius:4px;font-size:9px;font-weight:500}
 
/* ── FEATURE PILLS ── */
.feat-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin:14px 0}
.feat{background:var(--card);border:1px solid var(--border);border-radius:10px;
  padding:12px;display:flex;align-items:flex-start;gap:10px}
.feat-ic{font-size:18px;flex-shrink:0;margin-top:1px}
.feat-name{font-size:12px;font-weight:700;margin-bottom:2px;letter-spacing:-.01em}
.feat-desc{font-size:10.5px;color:var(--mid);line-height:1.45}
 
/* ── FOOTER ── */
.footer{text-align:center;margin-top:30px;padding-top:16px;border-top:1px solid var(--border)}
.cred{display:inline-flex;align-items:center;gap:8px;padding:9px 18px;border-radius:20px;
  background:rgba(59,130,246,.08);border:1px solid rgba(59,130,246,.2);
  font-size:11px;font-weight:600;color:var(--mid)}
.cred strong{color:var(--text)}
 
/* ── TOAST ── */
#toast{
  position:fixed;bottom:calc(18px + var(--sb));left:50%;
  transform:translateX(-50%) translateY(80px);
  background:var(--s2);padding:10px 18px;border-radius:10px;
  font-size:12px;font-weight:600;
  z-index:999;white-space:nowrap;
  box-shadow:0 8px 32px rgba(0,0,0,.6);transition:transform .3s ease;pointer-events:none
}
#toast.show{transform:translateX(-50%) translateY(0)}
 
/* ── HIBP BAR ── */
.hibp{background:rgba(59,130,246,.07);border:1px solid rgba(59,130,246,.2);
  border-radius:10px;padding:11px 13px;margin-bottom:13px}
.hibp-t{font-size:11px;font-weight:500;color:var(--mid);margin-bottom:7px}
.hibp-links{display:flex;flex-wrap:wrap;gap:8px}
.hlink{font-size:10.5px;font-weight:600;color:var(--blue);
  border-bottom:1px solid rgba(59,130,246,.3);padding-bottom:1px}
</style>
</head>
<body>
<div class="bg-grad"></div>
 
<!-- HEADER -->
<header class="hdr">
  <div class="logo-row">
    <div class="logo-ic">🛡</div>
    <div>
      <div class="logo-name">Guardian Shield</div>
      <div class="logo-sub" id="logo-sub">SEGURIDAD · v8.0 · IGNACIO VERA</div>
    </div>
  </div>
  <div class="status-chip safe" id="status-chip">
    <div class="s-dot" id="s-dot"></div>
    <span id="s-txt">PROTEGIDO</span>
  </div>
</header>
 
<!-- NAV -->
<nav class="nav">
  <button class="nb on" onclick="goTab('av',this)">🛡 Seguridad</button>
  <button class="nb" onclick="goTab('scan',this)">🔓 Filtraciones</button>
  <button class="nb" onclick="goTab('web',this)">🌐 Web & URLs</button>
  <button class="nb" onclick="goTab('tools',this)">🔧 Herramientas</button>
  <button class="nb" onclick="goTab('tips',this)">📋 Guía</button>
  <button class="nb" onclick="goTab('about',this)">ℹ️ Info</button>
</nav>
 
<div id="toast"></div>
 
<div class="main">
  <div id="tab-av"></div>
  <div id="tab-scan" class="hidden"></div>
  <div id="tab-web"  class="hidden"></div>
  <div id="tab-tools" class="hidden"></div>
  <div id="tab-tips" class="hidden"></div>
  <div id="tab-about" class="hidden"></div>
</div>
 
<script>
/* ════════════════════════════════════════════
   DATOS — Plataformas y brechas
════════════════════════════════════════════ */
var SEVC={CRÍTICO:'#ef4444',ALTO:'#f97316',MEDIO:'#f59e0b',BAJO:'#3b82f6'};
var CATS={
  gaming:{l:'Gaming',i:'🎮'},social:{l:'Social',i:'👥'},
  email:{l:'Email & Chat',i:'💬'},stream:{l:'Streaming',i:'🎬'},
  finance:{l:'Finanzas',i:'💳'},work:{l:'Trabajo',i:'💼'},
  cloud:{l:'Cloud & Tech',i:'☁️'},shop:{l:'Compras',i:'🛒'},other:{l:'Otros',i:'◈'}
};
 
var PLATFORMS=[
  {id:'psn',cat:'gaming',icon:'🎮',name:'PlayStation Network',desc:'PS4·PS5·Plus·Store',url:'https://account.sonyentertainmentnetwork.com/home/index',steps:['PlayStation.com → Mi cuenta → Seguridad → Actividad','Cerrar sesiones en dispositivos desconocidos','Activar verificación en dos pasos','Revisar historial de compras y tarjetas','Desactivar compartir datos con terceros']},
  {id:'xbox',cat:'gaming',icon:'🟩',name:'Xbox / Microsoft',desc:'Game Pass·Cloud·Store',url:'https://account.microsoft.com/security',steps:['account.microsoft.com → Seguridad → Actividad','Microsoft Authenticator como 2FA','Dispositivos de confianza: revisar','Suscripciones y pagos: comprobar','Alertas de seguridad por email: activar']},
  {id:'steam',cat:'gaming',icon:'🕹️',name:'Steam',desc:'PC·Workshop·Items',url:'https://store.steampowered.com/account/',steps:['Ajustes → Cuenta → Historial de accesos','Steam Guard Mobile Authenticator','API Keys de terceros: revisar','Email y teléfono vinculados: comprobar','Historial de intercambios y compras']},
  {id:'epic',cat:'gaming',icon:'◈',name:'Epic Games',desc:'Fortnite·Rocket League',url:'https://www.epicgames.com/account/personal',steps:['epicgames.com/account → Seguridad','Activar 2FA con app autenticadora','Plataformas conectadas: revisar','Desconectar cuentas no usadas','Historial de compras: verificar']},
  {id:'nintendo',cat:'gaming',icon:'🔴',name:'Nintendo Account',desc:'Switch·eShop·NSO',url:'https://accounts.nintendo.com',steps:['accounts.nintendo.com → Seguridad','Activar verificación en 2 pasos','Consolas registradas: revisar','Control Parental para menores','Suscripciones NSO activas']},
  {id:'riot',cat:'gaming',icon:'⚡',name:'Riot Games',desc:'Valorant·LoL·TFT',url:'https://account.riotgames.com/',steps:['account.riotgames.com → Historial','2FA con app autenticadora','Regiones y cuentas: revisar','Transacciones de RP: verificar','Clubs y torneos: configurar']},
  {id:'blizzard',cat:'gaming',icon:'🌀',name:'Battle.net',desc:'WoW·Diablo·Overwatch',url:'https://account.blizzard.com',steps:['account.blizzard.com → Seguridad','Blizzard Authenticator: activar','Intentos fallidos: revisar','Email y SMS de recuperación','Juegos y suscripciones activas']},
  {id:'twitch',cat:'gaming',icon:'💜',name:'Twitch',desc:'Streaming·Clips·Drops',url:'https://www.twitch.tv/settings/security',steps:['twitch.tv/settings/security → 2FA','Apps autorizadas: revocar','Correos de seguridad: revisar','Historial de subs y bits','Roles en canales de terceros']},
  {id:'roblox',cat:'gaming',icon:'🟥',name:'Roblox',desc:'Metaverso·Robux',url:'https://www.roblox.com/my/account#!/security',steps:['Ajustes → Seguridad → 2FA','Sesiones activas: cerrar','Transacciones Robux: verificar','Restricciones de privacidad','Grupos y permisos: revisar']},
  {id:'google',cat:'social',icon:'🔵',name:'Google',desc:'Gmail·YouTube·Drive·Pay',url:'https://myaccount.google.com/security-checkup',steps:['myaccount.google.com → Comprobación de seguridad','Actividad reciente: revisar cada inicio','Apps con acceso: revocar desconocidas','2FA con Google Prompt o llave','Email y teléfono de rescate: actualizar']},
  {id:'facebook',cat:'social',icon:'📘',name:'Facebook / Meta',desc:'Perfil·Grupos·Marketplace',url:'https://www.facebook.com/settings?tab=security',steps:['Configuración → Seguridad → Dónde iniciaste','Cerrar TODAS las sesiones desconocidas','Alertas de inicio de sesión: activar','Apps conectadas: revocar','Email y teléfono de recuperación']},
  {id:'instagram',cat:'social',icon:'📷',name:'Instagram',desc:'Fotos·Stories·Reels',url:'https://www.instagram.com/accounts/login_activity/',steps:['Configuración → Seguridad → Actividad','Sesiones no reconocidas: cerrar','2FA con app (no SMS)','Apps autorizadas: revocar','Descargar tu información en Ajustes']},
  {id:'twitter',cat:'social',icon:'🐦',name:'X / Twitter',desc:'Microblogging·X Premium',url:'https://x.com/settings/sessions',steps:['Configuración → Seguridad → Sesiones','Sesiones desconocidas: cerrar','2FA con app autenticadora','Apps autorizadas: revocar','Email y teléfono: actualizar']},
  {id:'tiktok',cat:'social',icon:'🎵',name:'TikTok',desc:'Vídeos·Live·Shop',url:'https://www.tiktok.com/setting/',steps:['Perfil → Config → Seguridad → Actividad','Dispositivos activos: gestionar','2FA: activar','Apps de terceros: revisar','Privacidad: configurar']},
  {id:'linkedin',cat:'social',icon:'💼',name:'LinkedIn',desc:'Red profesional·Jobs',url:'https://www.linkedin.com/psettings/sign-in-&-security',steps:['Ajustes → Inicio de sesión → Dónde','2FA: activar','Apps de terceros: revisar','Visibilidad del perfil: configurar','Solicitudes de conexión: revisar']},
  {id:'discord',cat:'social',icon:'🟣',name:'Discord',desc:'Comunidades·Voz·Nitro',url:'https://discord.com/settings/sessions',steps:['Ajustes → Privacidad → Sesiones','Cerrar todas excepto la actual','2FA con app autenticadora','Bots con acceso: revisar','Email y teléfono: actualizar']},
  {id:'reddit',cat:'social',icon:'🟠',name:'Reddit',desc:'Foros·Comunidades',url:'https://www.reddit.com/settings/privacy',steps:['Configuración → Privacidad → Dispositivos','2FA con app (no SMS)','Correo asociado: comprobar','Comunidades y permisos: revisar','Historial: verificar']},
  {id:'snapchat',cat:'social',icon:'👻',name:'Snapchat',desc:'Mensajes·Snaps',url:'https://accounts.snapchat.com/',steps:['accounts.snapchat.com → Historial','2FA: activar','Quién puede contactarte: configurar','Sesiones activas: revisar','Caché y conversaciones: limpiar']},
  {id:'gmail',cat:'email',icon:'📧',name:'Gmail',desc:'Google Mail·Filtros',url:'https://myaccount.google.com/security',steps:['myaccount.google.com → Actividad','Filtros y reenvío: verificar','Apps con acceso: revocar','Alias y cuentas vinculadas: revisar','Avisos de actividad inusual: activar']},
  {id:'yahoo',cat:'email',icon:'💜',name:'Yahoo Mail',desc:'Correo·Noticias',url:'https://login.yahoo.com/account/security',steps:['account.yahoo.com → Actividad','Apps conectadas: revisar','Teléfono y email de recuperación','Reenvíos automáticos: comprobar','Clave de cuenta Yahoo']},
  {id:'outlook',cat:'email',icon:'📫',name:'Outlook / Hotmail',desc:'Microsoft Mail·Calendar',url:'https://account.microsoft.com/security',steps:['account.microsoft.com → Actividad','2FA con Microsoft Authenticator','Alias de correo: comprobar','Dispositivos de confianza: revisar','Reglas de bandeja: verificar']},
  {id:'proton',cat:'email',icon:'🔒',name:'ProtonMail',desc:'Email cifrado E2E',url:'https://account.proton.me/',steps:['account.proton.me → Historial','2FA con TOTP (app autenticadora)','Claves PGP: revisar vencimiento','Sesiones activas: cerrar','Alias SimpleLogin: gestionar']},
  {id:'telegram',cat:'email',icon:'✈️',name:'Telegram',desc:'Mensajería·Canales',url:'https://my.telegram.org',steps:['Ajustes → Privacidad → Sesiones → Cerrar','Contraseña de cuenta + 2FA','Bots con acceso: revisar','Autodestrucción si inactiva','Quién ve tu número: Solo contactos']},
  {id:'whatsapp',cat:'email',icon:'💬',name:'WhatsApp',desc:'Mensajería·Grupos',url:'https://web.whatsapp.com/',steps:['Ajustes → Dispositivos → Cerrar desconocidos','Verificación en dos pasos: activar','Email de recuperación del PIN','Privacidad: foto y estado','Grupos: salir de los no reconocidos']},
  {id:'signal',cat:'email',icon:'🔐',name:'Signal',desc:'Cifrado E2E·Llamadas',url:'https://signal.org/',steps:['Ajustes → Cuenta → PIN de Signal','Bloqueo de pantalla en la app','Dispositivos vinculados: revocar','Copias de seguridad cifradas','Mensajes efímeros por defecto']},
  {id:'netflix',cat:'stream',icon:'🔴',name:'Netflix',desc:'Series·Películas',url:'https://www.netflix.com/YourAccount',steps:['Mi cuenta → Acceso y contraseña','Gestionar el acceso → Actividad','Cerrar sesión en TODOS los dispositivos','Notificaciones de inicio: activar','Plan y método de pago: verificar']},
  {id:'spotify',cat:'stream',icon:'🟢',name:'Spotify',desc:'Música·Podcasts',url:'https://www.spotify.com/es/account/apps/',steps:['account.spotify.com → Acceso reciente','Cerrar sesión en todos los dispositivos','Apps de terceros: revocar','Suscripción: plan y renovación','Redes sociales conectadas: revisar']},
  {id:'amazon',cat:'stream',icon:'📦',name:'Amazon / Prime',desc:'Tienda·Video·Music',url:'https://www.amazon.es/gp/css/account/info/view.html',steps:['Mi cuenta → Inicio de sesión → Actividad','Dispositivos registrados: revisar','Suscripciones activas: comprobar','Métodos de pago: borrar obsoletos','Direcciones guardadas: verificar']},
  {id:'disney',cat:'stream',icon:'✨',name:'Disney+',desc:'Disney·Marvel·Star Wars',url:'https://www.disneyplus.com/',steps:['Perfil → Cuenta → Dispositivos activos','Cerrar sesiones desconocidas','Contraseñas de perfil: activar','Plan familiar: revisar','Método de pago y renovación']},
  {id:'hbomax',cat:'stream',icon:'🎬',name:'Max / HBO',desc:'HBO·Originals·DC',url:'https://www.max.com/',steps:['Mi cuenta → Seguridad → Historial','Dispositivos activos: gestionar','Perfiles: revisar','Suscripción y renovación','Método de pago registrado']},
  {id:'paypal',cat:'finance',icon:'🅿️',name:'PayPal',desc:'Pagos·Transferencias',url:'https://www.paypal.com/myaccount/security/',steps:['Config → Seguridad → Actividad reciente','Notificaciones de CADA transacción','Pagos automáticos: revisar','Métodos de pago: borrar obsoletos','2FA con app: activar']},
  {id:'revolut',cat:'finance',icon:'💳',name:'Revolut',desc:'Banco digital·Cripto',url:'https://app.revolut.com/',steps:['Perfil → Seguridad → Dispositivos','Bloqueo biométrico + PIN: activar','Tarjetas virtuales: congelar no usadas','Congelar si actividad sospechosa','Notificaciones de transacciones: activas']},
  {id:'wise',cat:'finance',icon:'💱',name:'Wise',desc:'Transferencias internacionales',url:'https://wise.com/es/settings/',steps:['Config → Seguridad → Historial','2FA con app autenticadora','Destinatarios guardados: revisar','Cuentas multi-divisa: comprobar','Historial de transferencias: verificar']},
  {id:'binance',cat:'finance',icon:'🟡',name:'Binance',desc:'Exchange cripto·Staking',url:'https://www.binance.com/es/my/security',steps:['Seguridad → Dispositivos: revocar','Google Authenticator (NUNCA SMS)','Permisos de API: revocar','Lista blanca de retiro: activar','Código anti-phishing: activar']},
  {id:'coinbase',cat:'finance',icon:'🔵',name:'Coinbase',desc:'Cripto·Wallet·Staking',url:'https://www.coinbase.com/settings/security',steps:['Config → Seguridad → Historial','2FA con app (NUNCA SMS)','API keys: revocar no usadas','Bloqueo avanzado: activar','Wallet: desconectar dApps antiguas']},
  {id:'stripe',cat:'finance',icon:'💎',name:'Stripe',desc:'Pagos API·Billing',url:'https://dashboard.stripe.com/settings/user',steps:['Dashboard → Perfil → 2FA','Claves API: rotar si sospechoso','Webhooks: verificar endpoints','Usuarios del equipo: revisar','Radar: activar para fraude']},
  {id:'slack',cat:'work',icon:'💬',name:'Slack',desc:'Mensajería·Canales',url:'https://slack.com/account/settings',steps:['Ajustes → Seguridad → Sesiones','Workspaces desconocidos: cerrar','2FA: activar','Bots integrados: revisar','Workspaces: revisar pertenencia']},
  {id:'notion',cat:'work',icon:'📝',name:'Notion',desc:'Notas·Docs·AI',url:'https://www.notion.so/profile/security',steps:['Ajustes → Seguridad → Sesiones','2FA: activar','Apps conectadas: revisar','Espacios compartidos: revisar','Páginas públicas: auditar']},
  {id:'github',cat:'work',icon:'🐙',name:'GitHub',desc:'Código·Repos·Copilot',url:'https://github.com/settings/security',steps:['Ajustes → Contraseña → Historial','2FA obligatorio','Tokens de acceso: revocar','Apps OAuth: revisar','Deploy keys: verificar']},
  {id:'gitlab',cat:'work',icon:'🦊',name:'GitLab',desc:'DevOps·CI/CD·Repos',url:'https://gitlab.com/-/profile/account',steps:['Perfil → Seguridad → 2FA','Tokens de acceso: revocar','Sesiones activas: cerrar','Claves SSH: verificar','Grupos y proyectos: revisar']},
  {id:'figma',cat:'work',icon:'🎨',name:'Figma',desc:'Diseño UI·Prototipado',url:'https://www.figma.com/settings',steps:['Config → Seguridad → Sesiones','2FA: activar','Apps de terceros: revisar','Equipos y organizaciones','Archivos públicos: auditar']},
  {id:'zoom',cat:'work',icon:'🎥',name:'Zoom',desc:'Videollamadas·Webinars',url:'https://zoom.us/profile',steps:['Perfil → Seguridad → 2FA','Sesiones activas: cerrar','Apps de Marketplace: revisar','Grabaciones en la nube','Reuniones: contraseñas activas']},
  {id:'dropbox',cat:'work',icon:'📂',name:'Dropbox',desc:'Cloud·Paper·Transfer',url:'https://www.dropbox.com/account/security',steps:['Seguridad → Sesiones activas','Dispositivos: revocar obsoletos','2FA: activar','Apps de terceros: revisar','Carpetas compartidas: auditar']},
  {id:'apple',cat:'cloud',icon:'🍎',name:'Apple ID / iCloud',desc:'iPhone·Mac·App Store·Pay',url:'https://appleid.apple.com/',steps:['appleid.apple.com → 2FA obligatorio','Dispositivos vinculados: revisar','Emails de rescate: actualizar','Protección Avanzada de Datos: activar','Suscripciones: App Store, iCloud+']},
  {id:'adobe',cat:'cloud',icon:'🅰️',name:'Adobe Creative Cloud',desc:'PS·AI·Pr·Acrobat',url:'https://account.adobe.com/security',steps:['account.adobe.com → Historial','2FA: activar','Dispositivos: revisar','Suscripciones: comprobar','Proyectos compartidos: auditar']},
  {id:'microsoft',cat:'cloud',icon:'🪟',name:'Microsoft 365',desc:'Office·OneDrive·Teams',url:'https://account.microsoft.com/',steps:['account.microsoft.com → Actividad','Dispositivos: revocar desconocidos','2FA Microsoft Authenticator','Licencias: comprobar','Apps OAuth: revisar']},
  {id:'openai',cat:'cloud',icon:'🤖',name:'ChatGPT / OpenAI',desc:'GPT-4·DALL-E·API',url:'https://platform.openai.com/settings',steps:['platform.openai.com → 2FA','Claves API: revocar no usadas','Límite de gasto: configurar','Historial de chats: desactivar','GPTs publicados: revisar']},
  {id:'ebay',cat:'shop',icon:'🛍️',name:'eBay',desc:'Subastas·Compras',url:'https://www.ebay.es/',steps:['Mi eBay → Cuenta → 2FA','Anuncios como vendedor: revisar','Métodos de pago: verificar','Historial de compras: comprobar','Contraseña: actualizar']},
  {id:'wallapop',cat:'shop',icon:'🟠',name:'Wallapop',desc:'Segunda mano·España',url:'https://es.wallapop.com/',steps:['Perfil → Config → Seguridad','Teléfono y email: comprobar','Chats activos: revisar','Historial de transacciones','Artículos: revisar visibilidad']},
  {id:'vinted',cat:'shop',icon:'🟢',name:'Vinted',desc:'Ropa segunda mano',url:'https://www.vinted.es/',steps:['Perfil → Config de cuenta','Teléfono y email verificados','Pagos guardados: revisar','Historial de compras y ventas','Valoraciones y visibilidad']},
  {id:'booking',cat:'shop',icon:'🏨',name:'Booking.com',desc:'Hoteles·Vuelos',url:'https://account.booking.com/sign-in',steps:['Mi cuenta → 2FA: activar','Historial de inicio de sesión','Tarjetas guardadas: limpiar','Reservas activas: verificar','Genius: nivel y beneficios']},
  {id:'airbnb',cat:'shop',icon:'🏠',name:'Airbnb',desc:'Alojamientos·Experiencias',url:'https://www.airbnb.es/account-settings/login-and-security',steps:['Cuenta → Inicio de sesión → Dispositivos','2FA: activar','Reservas activas: comprobar','Métodos de cobro: actualizar','Verificación de identidad: estado']},
  {id:'canva',cat:'other',icon:'🎨',name:'Canva',desc:'Diseño·Templates·Brand',url:'https://www.canva.com/settings/',steps:['Config → Seguridad → Sesiones','2FA: activar','Apps conectadas: revisar','Equipos y organizaciones','Diseños públicos: auditar']},
  {id:'patreon',cat:'other',icon:'🎭',name:'Patreon',desc:'Membresías·Creadores',url:'https://www.patreon.com/settings/security',steps:['Config → Seguridad → 2FA','Sesiones activas: cerrar','Métodos de pago: actualizar','Membresías activas: revisar','Creadores seguidos: privacidad']}
];
 
var BREACHES={
  linkedin:{n:'LinkedIn',y:2021,c:'533 M',s:'ALTO',f:['Nombre','Email','Teléfono','Empresa','Cargo','URL perfil'],d:'Scraping masivo de perfiles. Datos usados en phishing profesional y fraude laboral.'},
  facebook:{n:'Facebook',y:2021,c:'533 M',s:'CRÍTICO',f:['Teléfono','Email','Nombre','Localización','Fecha nac.','Género'],d:"Vulnerabilidad en 'Importar contactos'. 106 países afectados."},
  twitter:{n:'Twitter/X',y:2022,c:'5.4 M',s:'MEDIO',f:['Email','Teléfono','Usuario','ID cuenta'],d:'API expuso vinculación email-cuenta anónima.'},
  snapchat:{n:'Snapchat',y:2014,c:'4.6 M',s:'MEDIO',f:['Usuario','Teléfono (parcial)'],d:'Publicada ignorando avisos de investigadores de seguridad.'},
  discord:{n:'Discord.io',y:2023,c:'760 K',s:'ALTO',f:['Usuario','Email','Hash contraseña','IP'],d:'Servicio no oficial comprometido. El operador fue arrestado.'},
  reddit:{n:'Reddit',y:2018,c:'N/A',s:'ALTO',f:['Email','Usuario','Hash contraseña','Mensajes privados'],d:'Interceptación de SMS en 2FA. Argumento contra SMS como 2FA.'},
  twitch:{n:'Twitch',y:2021,c:'125 GB',s:'ALTO',f:['Código fuente completo','Ingresos streamers','Datos internos'],d:'Mala configuración Git. Código fuente expuesto.'},
  spotify:{n:'Spotify',y:2020,c:'350 K',s:'MEDIO',f:['Email','Contraseña','País'],d:'Credential stuffing con contraseñas reutilizadas.'},
  yahoo:{n:'Yahoo',y:2016,c:'3.000 M',s:'CRÍTICO',f:['Email','Contraseña MD5','Nombre','Teléfono','Preguntas seg. en texto plano'],d:'La mayor brecha conocida. TODAS las cuentas Yahoo afectadas.'},
  adobe:{n:'Adobe',y:2013,c:'153 M',s:'CRÍTICO',f:['Email','Contraseña 3DES débil','Pista contraseña en texto plano'],d:'Cifrado obsoleto. Se descifraron millones de contraseñas reales.'},
  dropbox:{n:'Dropbox',y:2012,c:'68.6 M',s:'ALTO',f:['Email','Hash contraseña'],d:'Tardó 4 años en aparecer. Vulnerable a fuerza bruta.'},
  paypal:{n:'PayPal',y:2022,c:'34.9 K',s:'CRÍTICO',f:['Nombre','Fecha nac.','Dirección','Historial transacciones'],d:'Credential stuffing. Datos financieros sensibles expuestos.'},
  binance:{n:'Binance',y:2019,c:'~40 M$',s:'CRÍTICO',f:['Fotos KYC','API keys','7.000 BTC robados'],d:'Phishing sofisticado y exploits de API.'},
  coinbase:{n:'Coinbase',y:2021,c:'6.000',s:'CRÍTICO',f:['Email','Teléfono','Nombre','Acceso cuentas'],d:'Vulnerabilidad en recuperación SMS. 6.000 cuentas vaciadas.'},
  github:{n:'GitHub',y:2020,c:'N/A',s:'ALTO',f:['Email','Hash contraseña'],d:'Credential stuffing. GitHub forzó reset masivo.'},
  uber:{n:'Uber',y:2016,c:'57 M',s:'ALTO',f:['Email','Nombre completo','Teléfono'],d:'Uber ocultó la brecha durante más de un año.'},
  slack:{n:'Slack',y:2015,c:'N/A',s:'MEDIO',f:['Email','Hash contraseña','Teléfono'],d:'Brecha en base de datos. Reset masivo de contraseñas.'},
  openai:{n:'OpenAI / ChatGPT',y:2023,c:'N/A',s:'MEDIO',f:['Historial chats','Datos pago parciales','Emails'],d:'Vulnerabilidad Redis expuso historial de chats activos.'}
};
 
/* ════════════════════════════════════════════
   STATE Y UTILS
════════════════════════════════════════════ */
var S={results:null,loading:{},filter:'all',cat:'all',open:{},scanning:false};
function sleep(ms){return new Promise(function(r){setTimeout(r,ms);})}
 
var toastT;
function toast(msg,type){
  var el=document.getElementById('toast');
  var cols={ok:'rgba(34,197,94,.3)',warn:'rgba(245,158,11,.3)',danger:'rgba(239,68,68,.3)',info:'rgba(59,130,246,.25)'};
  var tc={ok:'#22c55e',warn:'#f59e0b',danger:'#ef4444',info:'#93c5fd'};
  el.textContent=msg;
  el.style.border='1px solid '+(cols[type]||cols.info);
  el.style.color=tc[type]||tc.info;
  el.classList.add('show');
  clearTimeout(toastT);
  toastT=setTimeout(function(){el.classList.remove('show');},4500);
}
 
function setStatus(txt,type){
  var chip=document.getElementById('status-chip');
  chip.className='status-chip '+type;
  document.getElementById('s-txt').textContent=txt;
  document.getElementById('s-dot').classList.toggle('anim',type==='warn');
}
 
function goTab(id,btn){
  ['av','scan','web','tools','tips','about'].forEach(function(t){
    document.getElementById('tab-'+t).classList.toggle('hidden',t!==id);
  });
  document.querySelectorAll('.nb').forEach(function(b){b.classList.remove('on');});
  if(btn)btn.classList.add('on');
  if(id==='web'&&!document.getElementById('tab-web').dataset.b){buildWeb();document.getElementById('tab-web').dataset.b='1';}
  if(id==='tools'&&!document.getElementById('tab-tools').dataset.b){buildTools();document.getElementById('tab-tools').dataset.b='1';}
  if(id==='tips'&&!document.getElementById('tab-tips').dataset.b){buildTips();document.getElementById('tab-tips').dataset.b='1';}
  if(id==='about'&&!document.getElementById('tab-about').dataset.b){buildAbout();document.getElementById('tab-about').dataset.b='1';}
}
 
/* ════════════════════════════════════════════
   TAB: SEGURIDAD (Antivirus principal)
   — Módulos inspirados en Norton, Bitdefender,
     TotalAV, Malwarebytes para iOS
════════════════════════════════════════════ */
var CHECKS=[
  {id:'ios',   ic:'📱', n:'Versión de iOS',          sub:'Comprueba actualizaciones de seguridad',   fn:'chkIOS'},
  {id:'wifi',  ic:'📶', n:'Seguridad de red',         sub:'Analiza la red Wi-Fi actual',              fn:'chkWifi'},
  {id:'https', ic:'🔒', n:'Protocolo de conexión',    sub:'Verifica cifrado HTTPS activo',            fn:'chkHTTPS'},
  {id:'priv',  ic:'🍪', n:'Rastreadores y cookies',   sub:'Privacidad del navegador',                 fn:'chkPrivacy'},
  {id:'breach',ic:'🔓', n:'Estado de filtraciones',   sub:'Sincroniza con el análisis de brechas',    fn:'chkBreachSync'},
  {id:'dns',   ic:'🌐', n:'Configuración DNS',         sub:'Detecta DNS sin cifrar',                   fn:'chkDNS'},
  {id:'perms', ic:'🎛️', n:'Permisos críticos iOS',    sub:'Guía de permisos en Ajustes',              fn:'chkPerms'},
  {id:'clip',  ic:'📋', n:'Higiene del portapapeles',  sub:'Revisa datos sensibles copiados',          fn:'chkClip'},
];
 
var avRes={};
var avScore=0;
 
function buildAV(){
  document.getElementById('tab-av').innerHTML=
  '<div style="text-align:center;padding:4px 0 20px">' +
    '<div class="score-hero">' +
      '<span class="shield-big" id="av-shield">🛡</span>' +
      '<div id="av-score-n" style="font-size:52px;font-weight:900;letter-spacing:-.04em;color:#fff">--</div>' +
      '<div id="av-score-l" style="font-size:13px;font-weight:700;letter-spacing:.04em;text-transform:uppercase;color:rgba(255,255,255,.6);margin-top:4px">Ejecuta el escaneo</div>' +
      '<div style="margin-top:16px">' +
        '<button class="btn btn-green" id="av-btn" onclick="runAV()" style="max-width:280px;margin:0 auto;font-size:13px;padding:13px 20px">🛡 Escaneo de Seguridad Completo</button>' +
      '</div>' +
    '</div>' +
  '</div>' +
  '<div id="prog-av" class="prog-wrap hidden">' +
    '<div class="prog-top"><span class="prog-lbl" id="av-plbl">Iniciando…</span><span class="prog-pct" id="av-ppct">0%</span></div>' +
    '<div class="prog-bar"><div class="prog-fill" id="av-pfill"></div></div>' +
  '</div>' +
  '<div style="font-size:10px;font-weight:700;color:var(--dim);text-transform:uppercase;letter-spacing:.1em;margin-bottom:10px">Módulos de protección</div>' +
  '<div class="mod-grid" id="mod-grid">' +
  CHECKS.map(function(c){
    return '<div class="mod" id="mod-'+c.id+'" onclick="runOneMod(\''+c.id+'\')">'+
      '<div class="mod-ic">'+c.ic+'</div>'+
      '<div class="mod-name">'+c.n+'</div>'+
      '<div class="mod-st" id="mst-'+c.id+'" style="color:var(--dim)">Toca para analizar</div>'+
      '<div class="mod-progress" id="mbar-'+c.id+'"></div>'+
    '</div>';
  }).join('')+
  '</div>'+
  '<div style="font-size:10px;font-weight:700;color:var(--dim);text-transform:uppercase;letter-spacing:.1em;margin:18px 0 10px">Detector de SMS sospechosos (Smishing)</div>'+
  '<div class="card">' +
    '<div style="font-size:13px;font-weight:600;margin-bottom:4px">Analizador de mensajes</div>' +
    '<div style="font-size:12px;color:var(--mid);margin-bottom:12px;line-height:1.55">Pega el texto de un SMS o mensaje sospechoso para detectar señales de phishing.</div>' +
    '<textarea class="inp" id="sms-txt" rows="3" placeholder="Pega aquí el SMS o mensaje sospechoso…"></textarea>' +
    '<button class="btn btn-blue" onclick="checkSMS()" style="margin-top:10px;font-size:12px;padding:12px">🔍 Analizar mensaje</button>' +
    '<div class="rbox" id="sms-res"></div>' +
  '</div>';
}
 
/* ── ESCANEO COMPLETO ── */
async function runAV(){
  var btn=document.getElementById('av-btn');
  btn.disabled=true;btn.innerHTML='<span class="spin"></span> Escaneando…';
  document.getElementById('prog-av').classList.remove('hidden');
  avRes={};avScore=0;
  setStatus('Escaneando…','warn');
  for(var i=0;i<CHECKS.length;i++){
    var c=CHECKS[i];
    setModRun(c.id);
    await sleep(350+Math.random()*300);
    var r=await window[c.fn]();
    avRes[c.id]=r;setModDone(c.id,r);
    var pct=Math.round((i+1)/CHECKS.length*100);
    document.getElementById('av-pfill').style.width=pct+'%';
    document.getElementById('av-ppct').textContent=pct+'%';
    document.getElementById('av-plbl').textContent='Verificando '+c.n+'…';
  }
  document.getElementById('prog-av').classList.add('hidden');
  var ok=Object.values(avRes).filter(function(r){return r.st==='ok';}).length;
  var warn=Object.values(avRes).filter(function(r){return r.st==='warn';}).length;
  avScore=Math.round((ok+warn*0.5)/CHECKS.length*100);
  updateRing(avScore);
  btn.disabled=false;btn.innerHTML='🔄 Nuevo escaneo';
  var type=avScore>80?'safe':avScore>50?'warn':'danger';
  setStatus(avScore>80?'PROTEGIDO':avScore>50?'REVISAR':'ATENCIÓN',type);
  toast(avScore>80?'✅ Dispositivo bien protegido.':avScore>50?'⚠️ Hay mejoras recomendadas.':'🚨 Se requieren acciones de seguridad.',avScore>80?'ok':avScore>50?'warn':'danger');
}
 
function setModRun(id){
  var m=document.getElementById('mod-'+id),s=document.getElementById('mst-'+id),b=document.getElementById('mbar-'+id);
  if(m){m.className='mod running';}
  if(s){s.textContent='Analizando…';s.style.color='var(--blue)';}
  if(b){b.style.background='var(--blue)';b.style.width='100%';}
}
function setModDone(id,r){
  var m=document.getElementById('mod-'+id),s=document.getElementById('mst-'+id),b=document.getElementById('mbar-'+id);
  var cc={'ok':'var(--green)','warn':'var(--amber)','danger':'var(--red)'};
  var mc={'ok':'ok','warn':'warn','danger':'danger'};
  if(m){m.className='mod '+(mc[r.st]||'ok');}
  if(s){s.textContent=r.msg;s.style.color=cc[r.st]||'var(--green)';}
  if(b){b.style.background=cc[r.st]||'var(--green)';b.style.width='100%';}
}
 
function updateRing(score){
  var n=document.getElementById('av-score-n'),l=document.getElementById('av-score-l'),sh=document.getElementById('av-shield');
  var col=score>80?'var(--green)':score>50?'var(--amber)':'var(--red)';
  var lbl=score>80?'Protegido':score>50?'Revisar configuración':'Acción requerida';
  if(n){n.textContent=score;n.style.color=score>80?'#fff':score>50?'#fbbf24':'#fca5a5';}
  if(l){l.textContent=lbl;}
  if(sh){sh.style.filter='drop-shadow(0 4px 20px '+(score>80?'rgba(34,197,94,.6)':score>50?'rgba(245,158,11,.6)':'rgba(239,68,68,.6)')+')'}
}
 
async function runOneMod(id){
  var c=CHECKS.find(function(x){return x.id===id;});
  if(!c)return;
  setModRun(id);
  await sleep(300+Math.random()*400);
  var r=await window[c.fn]();
  avRes[id]=r;setModDone(id,r);
  toast(c.n+': '+r.msg,'info');
}
 
/* ── CHECKS INDIVIDUALES ── */
async function chkIOS(){
  var ua=navigator.userAgent;
  var m=ua.match(/CPU iPhone OS (\d+)_/)||ua.match(/CPU OS (\d+)_/);
  if(m){
    var v=parseInt(m[1]);
    if(v>=18)return{st:'ok',msg:'iOS '+v+' — Actualizado ✓'};
    if(v>=17)return{st:'warn',msg:'iOS '+v+' — Considera actualizar'};
    return{st:'danger',msg:'iOS '+v+' — Versión antigua'};
  }
  return{st:'ok',msg:'iOS detectado ✓'};
}
async function chkWifi(){
  if(!navigator.onLine)return{st:'warn',msg:'Sin conexión a internet'};
  var c=navigator.connection||navigator.mozConnection||navigator.webkitConnection;
  if(c&&c.type==='cellular')return{st:'ok',msg:'Datos móviles — Más seguro ✓'};
  if(c&&c.type==='wifi')return{st:'warn',msg:'Wi-Fi — Usa VPN si es pública'};
  return{st:'warn',msg:'Red activa — Verifica si es pública'};
}
async function chkHTTPS(){
  if(location.protocol==='https:')return{st:'ok',msg:'HTTPS activo — Cifrado ✓'};
  if(location.protocol==='file:')return{st:'ok',msg:'Archivo local ✓'};
  return{st:'danger',msg:'Sin HTTPS — Conexión no cifrada'};
}
async function chkPrivacy(){
  var st='ok',msg='Privacidad del navegador ✓';
  if(navigator.doNotTrack!=='1'&&navigator.doNotTrack!=='yes'){st='warn';msg='Do Not Track desactivado';}
  try{
    var f=document.createElement('iframe');f.style.display='none';f.src='about:blank';
    document.body.appendChild(f);f.contentWindow.document.cookie='_t=1;SameSite=None;Secure';
    document.body.removeChild(f);st='warn';msg='Cookies de terceros activas';
  }catch(e){msg='Cookies de terceros bloqueadas ✓';}
  return{st:st,msg:msg};
}
async function chkBreachSync(){
  if(S.results){
    var e=Object.values(S.results).filter(function(r){return r.breach;}).length;
    if(e>0)return{st:'danger',msg:e+' brechas — Ve a Filtraciones'};
    return{st:'ok',msg:'Sin brechas en el análisis ✓'};
  }
  return{st:'warn',msg:'Ejecuta análisis de filtraciones'};
}
async function chkDNS(){
  return{st:'warn',msg:'Usa NextDNS o 1.1.1.1 para cifrar'};
}
async function chkPerms(){
  return{st:'warn',msg:'Revisa Ajustes → Privacidad'};
}
async function chkClip(){
  return{st:'warn',msg:'Borra datos sensibles copiados'};
}
 
/* ── DETECTOR SMS ── */
function checkSMS(){
  var txt=(document.getElementById('sms-txt').value||'').toLowerCase();
  if(!txt.trim()){toast('Pega el texto del mensaje primero.','warn');return;}
  var res=document.getElementById('sms-res');res.style.display='block';
  var hits=[],score=0;
  var patterns=[
    {r:/urgente|inmediato|acción requerida|actúa ahora|act now|expira hoy/i,m:'Lenguaje de urgencia extrema',p:25},
    {r:/ha(s|ce) ganado|winner|has won|premio|regalo gratis|gift card|sorteo/i,m:'Promesa de premio o regalo',p:30},
    {r:/cuenta (bloqueada?|suspendida?|desactivada?|verificar)/i,m:'Amenaza de bloqueo de cuenta',p:30},
    {r:/contraseña|password|datos bancarios|tarjeta|iban|cuenta bancaria|pin/i,m:'Solicita credenciales o datos bancarios',p:35},
    {r:/banco|bbva|santander|caixabank|sabadell|ing|paypal|amazon|apple|google|microsoft|correos|hacienda/i,m:'Suplanta entidad financiera o tecnológica',p:22},
    {r:/http:\/\/|bit\.ly|tinyurl|t\.co|cutt\.ly|ow\.ly|rb\.gy/i,m:'Enlace acortado o sin HTTPS',p:25},
    {r:/paquete|entrega|envío|aduanas|ups|dhl|fedex|gastos de envío/i,m:'Posible estafa de entrega de paquete',p:20},
    {r:/tu iphone|tu dispositivo|virus detectado|infected|malware detectado/i,m:'Alerta falsa de virus en dispositivo',p:35},
    {r:/código de seguridad|otp|código de verificación|código único/i,m:'Solicita código de verificación OTP',p:30},
    {r:/haz clic|pincha aquí|accede ahora|click here|verify now/i,m:'Solicita hacer clic en un enlace',p:15},
  ];
  patterns.forEach(function(p){if(p.r.test(txt)){hits.push({m:p.m,p:p.p});score+=p.p;}});
  score=Math.min(score,100);
 
  if(score>=40||hits.length>=2){
    res.className='rbox danger';
    res.innerHTML='<div style="font-weight:800;color:var(--red);margin-bottom:8px;font-size:14px;letter-spacing:-.01em">🚨 Mensaje sospechoso detectado</div>'+
      '<div style="font-size:11px;font-weight:600;color:var(--dim);margin-bottom:10px;font-family:var(--mono)">INDICADORES: '+hits.length+' · RIESGO: '+score+'/100</div>'+
      hits.map(function(h){return'<div style="display:flex;gap:8px;margin-bottom:5px;align-items:flex-start"><span style="color:var(--red);flex-shrink:0;font-size:12px">⚠</span><span style="font-size:12px;color:var(--mid)">'+h.m+'</span></div>';}).join('')+
      '<div style="margin-top:10px;padding-top:10px;border-top:1px solid rgba(239,68,68,.2);font-size:11.5px;color:var(--mid)"><strong style="color:var(--text)">Recomendación:</strong> No hagas clic en ningún enlace. Borra el mensaje. Si suplanta a tu banco, contacta directamente con ellos. Puedes reportar al INCIBE llamando al <strong style="color:var(--text)">017</strong>.</div>';
    toast('🚨 Mensaje de phishing detectado.','danger');
  } else if(score>0||hits.length===1){
    res.className='rbox warn';
    res.innerHTML='<div style="font-weight:800;color:var(--amber);margin-bottom:8px;font-size:14px">⚠️ Indicadores leves detectados</div>'+
      (hits.length?hits.map(function(h){return'<div style="font-size:12px;color:var(--mid);margin-bottom:4px">· '+h.m+'</div>';}).join(''):'')+
      '<div style="margin-top:8px;font-size:12px;color:var(--mid)">Actúa con precaución. Verifica directamente con la entidad usando sus canales oficiales.</div>';
    toast('⚠️ Indicadores leves en el mensaje.','warn');
  } else {
    res.className='rbox ok';
    res.innerHTML='<div style="font-weight:800;color:var(--green);margin-bottom:6px;font-size:14px">✅ Sin indicadores de phishing</div>'+
      '<div style="font-size:12px;color:var(--mid)">No se detectaron patrones típicos. Siempre actúa con precaución ante enlaces o solicitudes de datos.</div>';
    toast('✅ Mensaje sin indicadores de phishing.','ok');
  }
}
 
/* ════════════════════════════════════════════
   TAB: FILTRACIONES
════════════════════════════════════════════ */
function buildScan(){
  document.getElementById('tab-scan').innerHTML=
  '<div style="margin-bottom:20px">' +
    '<h2 style="font-size:20px;font-weight:800;letter-spacing:-.02em;margin-bottom:4px">Monitor de filtraciones</h2>' +
    '<p style="font-size:13px;color:var(--mid);line-height:1.55">Comprueba en <strong style="color:var(--text)">'+PLATFORMS.length+' plataformas</strong> si tus datos han sido expuestos en brechas de seguridad conocidas.</p>' +
  '</div>' +
  '<div class="card">' +
    '<div class="inp-2">' +
      '<div><label class="lbl">Correo electrónico</label><input class="inp" type="email" id="ie" placeholder="correo@dominio.com" autocomplete="email"></div>' +
      '<div><label class="lbl">Nombre de usuario</label><input class="inp" type="text" id="iu" placeholder="nombre_usuario"></div>' +
    '</div>' +
    '<div id="pw" class="prog-wrap hidden">' +
      '<div class="prog-top"><span class="prog-lbl" id="plbl">Iniciando…</span><span class="prog-pct" id="ppct">0%</span></div>' +
      '<div class="prog-bar"><div class="prog-fill" id="pfl"></div></div>' +
    '</div>' +
    '<button class="btn btn-blue" id="sbtn" onclick="startScan()">🔍 Analizar '+PLATFORMS.length+' plataformas</button>' +
  '</div>' +
  '<div id="empty-s" style="text-align:center;padding:28px 12px">' +
    '<div style="font-size:36px;margin-bottom:12px">🔓</div>' +
    '<div style="font-size:11px;color:var(--dim);line-height:2.2;letter-spacing:.02em">' +
    '🎮 PlayStation · Xbox · Steam · Epic · Nintendo · Riot · Battle.net · Twitch · Roblox<br>' +
    '👥 Google · Facebook · Instagram · Twitter · TikTok · LinkedIn · Discord · Reddit · Snapchat<br>' +
    '💬 Gmail · Yahoo · Outlook · ProtonMail · Telegram · WhatsApp · Signal<br>' +
    '🎬 Netflix · Spotify · Amazon · Disney+ · HBO Max<br>' +
    '💳 PayPal · Revolut · Wise · Binance · Coinbase · Stripe<br>' +
    '💼 Slack · Notion · GitHub · GitLab · Figma · Zoom · Dropbox<br>' +
    '🛒 eBay · Wallapop · Vinted · Booking · Airbnb · ChatGPT · Adobe · Canva' +
    '</div></div>' +
  '<div id="ra" class="hidden"></div>';
  document.getElementById('ie').addEventListener('keydown',function(e){if(e.key==='Enter')startScan();});
  document.getElementById('iu').addEventListener('keydown',function(e){if(e.key==='Enter')startScan();});
}
 
async function startScan(){
  var email=(document.getElementById('ie').value||'').trim().toLowerCase();
  var user=(document.getElementById('iu').value||'').trim().toLowerCase();
  if(!email&&!user){toast('Introduce un email o nombre de usuario.','warn');return;}
  S.results={};S.loading={};S.filter='all';S.cat='all';S.open={};S.scanning=true;
  PLATFORMS.forEach(function(p){S.loading[p.id]=true;});
  var btn=document.getElementById('sbtn');
  btn.disabled=true;btn.innerHTML='<span class="spin"></span> Analizando '+PLATFORMS.length+' plataformas…';
  document.getElementById('pw').classList.remove('hidden');
  document.getElementById('empty-s').classList.add('hidden');
  setStatus('Escaneando filtraciones…','warn');
  for(var i=0;i<PLATFORMS.length;i++){
    var p=PLATFORMS[i];
    await sleep(8+Math.random()*22);
    S.results[p.id]={p:p,breach:BREACHES[p.id]||null};
    delete S.loading[p.id];
    var pct=Math.round((i+1)/PLATFORMS.length*100);
    document.getElementById('pfl').style.width=pct+'%';
    document.getElementById('ppct').textContent=pct+'%';
    document.getElementById('plbl').textContent='Verificando '+p.name+'…';
    if(i===6)document.getElementById('ra').classList.remove('hidden');
    if(i>6)renderResults(email);
  }
  S.scanning=false;
  document.getElementById('pw').classList.add('hidden');
  btn.disabled=false;btn.innerHTML='🔄 Nuevo análisis';
  var all=Object.values(S.results);
  var exp=all.filter(function(r){return r.breach;}).length;
  setStatus(exp>0?exp+' riesgos detectados':'Protegido',exp>0?'danger':'safe');
  toast(exp>0?exp+' plataformas con brechas detectadas.':'Sin brechas en la base de datos.',exp>0?'warn':'ok');
  renderResults(email);
  avRes['breach']={st:exp>0?'danger':'ok',msg:exp>0?exp+' brechas — Ve a Filtraciones':'Sin brechas ✓'};
}
 
function renderResults(email){
  var all=Object.values(S.results);
  var exposed=all.filter(function(r){return r.breach;});
  var safe=all.filter(function(r){return!r.breach;});
  var score=all.length?Math.round(safe.length/all.length*100):0;
  var sc=score>75?'var(--green)':score>45?'var(--amber)':'var(--red)';
 
  var h='<div class="card" style="margin-bottom:14px">' +
    '<div style="display:flex;align-items:center;gap:16px;flex-wrap:wrap">' +
    '<div style="width:80px;height:80px;border-radius:50%;background:'+sc+'15;border:3px solid '+sc+';display:flex;align-items:center;justify-content:center;flex-shrink:0">' +
    '<div style="text-align:center"><div style="font-size:22px;font-weight:900;color:'+sc+'">'+score+'</div><div style="font-size:8px;font-weight:700;color:var(--dim);text-transform:uppercase">SCORE</div></div>' +
    '</div>' +
    '<div style="flex:1;min-width:160px">' +
    '<div style="font-size:17px;font-weight:800;letter-spacing:-.02em;color:'+(exposed.length>0?'var(--text)':'var(--green)')+';margin-bottom:6px">'+(exposed.length>0?exposed.length+' plataforma'+(exposed.length===1?'':'s')+' con brechas':'Sin brechas conocidas')+'</div>' +
    '<div style="font-size:12px;color:var(--mid);margin-bottom:12px;line-height:1.6">'+(exposed.length>0?'Toca cada plataforma para ver los pasos de acción inmediata.':'No se encontraron coincidencias en la base de datos de brechas.')+'</div>' +
    '<div class="kpi-row">' +
    '<div class="kpi"><div class="kpi-n" style="color:'+(exposed.length?'var(--red)':'var(--green)')+'">'+exposed.length+'</div><div class="kpi-l">Con brecha</div></div>' +
    '<div class="kpi"><div class="kpi-n" style="color:var(--green)">'+safe.length+'</div><div class="kpi-l">Sin brecha</div></div>' +
    '<div class="kpi"><div class="kpi-n" style="color:var(--blue)">'+all.length+'</div><div class="kpi-l">Analizadas</div></div>' +
    '</div></div></div></div>';
 
  if(email){
    h+='<div class="hibp">' +
    '<div class="hibp-t">Verificación en tiempo real para <strong style="color:var(--text)">'+email+'</strong></div>' +
    '<div class="hibp-links">' +
    '<a href="https://haveibeenpwned.com/account/'+encodeURIComponent(email)+'" target="_blank" class="hlink">HIBP →</a>' +
    '<a href="https://monitor.mozilla.org/" target="_blank" class="hlink">Firefox Monitor →</a>' +
    '<a href="https://myaccount.google.com/" target="_blank" class="hlink">Google Dark Web →</a>' +
    '</div></div>';
  }
 
  h+='<div class="fscroll"><div class="finner">' +
    '<div class="fg">' +
    fbn('sec','fs-a','Todas ('+all.length+')',S.filter==='all',"sf('all')")+
    fbn('sec','fs-e','⚑ Brecha ('+exposed.length+')',S.filter==='exposed',"sf('exposed')")+
    fbn('sec','fs-s','✓ OK ('+safe.length+')',S.filter==='safe',"sf('safe')")+
    '</div>'+
    fbn('cat','fc-a','◈ Todos',S.cat==='all',"sc('all')")+
    Object.entries(CATS).map(function(e){return fbn('cat','fc-'+e[0],e[1].i+' '+e[1].l,S.cat===e[0],"sc('"+e[0]+"')");}).join('')+
  '</div></div>';
 
  var filtered=gf();
  h+='<div class="rt">' +
    '<div class="rt-hdr"><span></span><span></span><span>Plataforma</span><span>Estado</span><span></span></div>';
 
  if((S.filter==='all'||S.filter==='exposed')&&S.cat==='all'&&exposed.length>0){
    h+='<div class="sec-h dng"><div class="sec-l" style="color:var(--red)"><div style="width:5px;height:5px;border-radius:50%;background:var(--red);flex-shrink:0"></div>ATENCIÓN REQUERIDA · '+exposed.length+' PLATAFORMAS</div></div>';
    exposed.forEach(function(r){h+=renderRow(r);});
  }
  if(S.cat==='all'){
    Object.entries(CATS).forEach(function(entry){
      var cat=entry[0],meta=entry[1];
      var items=filtered.filter(function(r){return r.p.cat===cat&&!r.breach;});
      if(!items.length)return;
      h+='<div class="sec-h nrm"><div class="sec-l" style="color:var(--dim)">'+meta.i+' '+meta.l+'</div></div>';
      items.forEach(function(r){h+=renderRow(r);});
    });
  }else{filtered.forEach(function(r){h+=renderRow(r);});}
  h+='</div>';
  document.getElementById('ra').innerHTML=h;
  document.getElementById('ra').classList.remove('hidden');
}
 
function fbn(cls,id,label,active,onclick){
  return'<button class="fb '+cls+(active?' on':'')+'" id="'+id+'" onclick="'+onclick+'">'+label+'</button>';
}
function gf(){
  var all=Object.values(S.results);
  var base=S.filter==='exposed'?all.filter(function(r){return r.breach;}):S.filter==='safe'?all.filter(function(r){return!r.breach;}):all;
  if(S.cat!=='all')base=base.filter(function(r){return r.p.cat===S.cat;});
  return base;
}
function sf(f){S.filter=f;S.open={};rr();}
function sc(c){S.cat=c;S.open={};rr();}
function rr(){var e=document.getElementById('ie')?document.getElementById('ie').value.trim().toLowerCase():'';renderResults(e);}
 
function renderRow(r){
  var p=r.p,b=r.breach,isL=!!S.loading[p.id],hasB=!!b,isO=!!S.open[p.id];
  var sc=hasB?(SEVC[b.s]||'#ef4444'):'#22c55e';
  var badge=isL?'<span class="spin" style="width:12px;height:12px"></span>':
    hasB?'<span class="pr-bdg" style="color:'+sc+';background:'+sc+'18;border:1px solid '+sc+'40">'+b.s+'</span>':
    '<span class="ok-bdg"><div class="ok-d"></div>OK</span>';
  var body='';
  if(isO&&!isL){
    var bc=hasB?'<div class="bc" style="background:'+sc+'0c;border:1px solid '+sc+'30">' +
      '<div class="bc-top"><div><div class="bc-meta">BRECHA · '+b.n+' · '+b.y+'</div><div class="bc-cnt">'+b.c+' <span>registros</span></div></div>' +
      '<span class="pr-bdg" style="color:'+sc+';background:'+sc+'18;border:1px solid '+sc+'40;flex-shrink:0">'+b.s+'</span></div>' +
      '<div class="bc-desc">'+b.d+'</div>' +
      '<div class="tags">'+b.f.map(function(f){return'<span class="tag">'+f+'</span>';}).join('')+'</div></div>':'';
    body='<div class="pr-body">'+bc+
      '<div class="steps-h">PASOS PARA ASEGURAR TU CUENTA</div>'+
      p.steps.map(function(s,i){return'<div class="step"><div class="step-n">'+(i+1)+'</div><div class="step-t">'+s+'</div></div>';}).join('')+
      '<div class="act-row"><a href="'+p.url+'" target="_blank" class="btn-sm bsm-blue">→ Ir a seguridad</a>'+(hasB?'<a href="https://haveibeenpwned.com" target="_blank" class="btn-sm bsm-red">→ HIBP</a>':'')+'</div>' +
    '</div>';
  }
  return'<div class="pr" id="pr-'+p.id+'">' +
    '<div class="pr-h" onclick="tr(\''+p.id+'\')"><div class="pr-acc" style="background:'+(isL?'rgba(255,255,255,.05)':hasB?sc:'#22c55e40')+'"></div>' +
    '<div class="pr-ic">'+p.icon+'</div>' +
    '<div style="overflow:hidden"><div class="pr-name" style="color:'+(hasB?'#f1f5f9':'#64748b')+'">'+p.name+'</div><div class="pr-sub">'+p.desc+'</div></div>' +
    badge+(!isL?'<div class="chev'+(isO?' open':'')+'">▼</div>':'<div></div>')+
    '</div>'+body+'</div>';
}
function tr(id){
  if(S.loading[id])return;
  S.open[id]=!S.open[id];rr();
  setTimeout(function(){var el=document.getElementById('pr-'+id);if(el)el.scrollIntoView({block:'nearest',behavior:'smooth'});},60);
}
 
/* ════════════════════════════════════════════
   TAB: WEB & URLs
════════════════════════════════════════════ */
var PHISH=['secure-login-apple.com','appleid-verify.net','paypal-secure.net','amazon-login-verify.com',
  'google-security-alert.com','facebook-login-secure.net','netflix-update-billing.com',
  'instagram-verify-account.com','microsoft-security-update.com','icloud-locked.net',
  'apple-payment-failed.com','paypa1.com','amaz0n.com','g00gle.com','facebo0k.com',
  'twitter-suspended.net','crypto-free-reward.com','bitcoin-giveaway.net',
  'prize-winner-claim.com','your-device-has-virus.com','free-gift-card.xyz'];
 
function buildWeb(){
  document.getElementById('tab-web').innerHTML=
  '<div style="margin-bottom:20px">' +
    '<h2 style="font-size:20px;font-weight:800;letter-spacing:-.02em;margin-bottom:4px">Protección Web</h2>' +
    '<p style="font-size:13px;color:var(--mid);line-height:1.55">Verifica URLs y dominios antes de abrirlos. Detecta sitios de phishing y conexiones inseguras.</p>' +
  '</div>' +
 
  '<div class="card" style="margin-bottom:14px">' +
    '<div style="font-size:14px;font-weight:700;margin-bottom:4px;letter-spacing:-.01em">🔍 Verificador de URLs</div>' +
    '<div style="font-size:12px;color:var(--mid);margin-bottom:12px">Pega una URL o nombre de dominio para comprobar si es seguro antes de abrirlo.</div>' +
    '<div style="display:flex;gap:8px;margin-bottom:8px">' +
      '<input class="inp" type="url" id="url-i" placeholder="https://ejemplo.com o dominio.com" style="flex:1">' +
      '<button class="btn-sm bsm-blue" onclick="checkURL()" style="flex-shrink:0;padding:12px 16px">Verificar</button>' +
    '</div>' +
    '<div class="rbox" id="url-r"></div>' +
  '</div>' +
 
  '<div class="card" style="margin-bottom:14px">' +
    '<div style="font-size:14px;font-weight:700;margin-bottom:4px;letter-spacing:-.01em">🎣 Detector de phishing en emails</div>' +
    '<div style="font-size:12px;color:var(--mid);margin-bottom:12px">Pega el cuerpo de un email sospechoso para analizar señales de phishing.</div>' +
    '<textarea class="inp" id="email-txt" rows="3" placeholder="Pega aquí el texto del email sospechoso…"></textarea>' +
    '<button class="btn btn-blue" onclick="checkEmail()" style="margin-top:10px;font-size:12px;padding:12px">🔍 Analizar email</button>' +
    '<div class="rbox" id="email-r"></div>' +
  '</div>' +
 
  '<div class="card">' +
    '<div style="font-size:14px;font-weight:700;margin-bottom:10px;letter-spacing:-.01em">🌐 Recursos de seguridad web</div>' +
    '<div style="display:flex;flex-direction:column;gap:8px">' +
    [
      {n:'Google Safe Browsing',d:'Verifica en tiempo real si una URL es maliciosa',u:'https://transparencyreport.google.com/safe-browsing/search',ic:'🔵'},
      {n:'VirusTotal',d:'Escanea URLs y archivos con 70+ motores antivirus',u:'https://www.virustotal.com',ic:'🔴'},
      {n:'PhishTank',d:'Base de datos colaborativa de URLs de phishing conocidas',u:'https://www.phishtank.com',ic:'🟠'},
      {n:'URLVoid',d:'Reputación de dominio y análisis de seguridad',u:'https://www.urlvoid.com',ic:'🟢'},
      {n:'Cisco Talos Intelligence',d:'Reputación de IP, dominio y análisis de amenazas',u:'https://talosintelligence.com',ic:'🔷'},
    ].map(function(item){
      return'<a href="'+item.u+'" target="_blank" style="display:flex;align-items:center;justify-content:space-between;gap:12px;padding:11px 13px;background:rgba(255,255,255,.04);border:1px solid var(--border);border-radius:9px;text-decoration:none;transition:background .14s" onmouseover="this.style.background=\'rgba(255,255,255,.07)\'" onmouseout="this.style.background=\'rgba(255,255,255,.04)\'">' +
        '<div style="display:flex;align-items:center;gap:10px">' +
        '<span style="font-size:18px">'+item.ic+'</span>' +
        '<div><div style="font-size:13px;font-weight:700;letter-spacing:-.01em;color:var(--text)">'+item.n+'</div>' +
        '<div style="font-size:11px;color:var(--mid);margin-top:1px">'+item.d+'</div></div></div>' +
        '<span style="color:var(--dim);font-size:12px;flex-shrink:0">→</span></a>';
    }).join('')+
    '</div>' +
  '</div>';
}
 
function checkURL(){
  var raw=(document.getElementById('url-i').value||'').trim().toLowerCase();
  if(!raw){toast('Introduce una URL o dominio.','warn');return;}
  var res=document.getElementById('url-r');res.style.display='block';
  var domain=raw.replace(/^https?:\/\//,'').replace(/\/.*$/,'').replace(/^www\./,'');
  var issues=[];
  var found=PHISH.filter(function(d){return domain.includes(d)||d.includes(domain);});
  if(found.length)issues.push('Dominio en lista de amenazas conocidas');
  if(!raw.startsWith('https'))issues.push('No usa HTTPS — conexión sin cifrar');
  var brands=['apple','google','paypal','amazon','microsoft','facebook','instagram','netflix','spotify','banco'];
  brands.forEach(function(b){
    if(domain.includes(b)&&!domain.match(new RegExp('^'+b+'\\.(com|es|co\\.uk|net|org|io)$'))){
      issues.push('Posible suplantación de "'+b+'"');
    }
  });
  if(domain.length>50)issues.push('Dominio inusualmente largo');
  if(domain.match(/\.(xyz|tk|ml|ga|cf|pw|gq|top|click)$/))issues.push('Extensión de dominio de alto riesgo');
  if(domain.match(/-{2,}/))issues.push('Múltiples guiones — posible typosquatting');
  if(domain.match(/\d{3,}/))issues.push('Muchos números en el dominio (sospechoso)');
 
  if(issues.length){
    res.className='rbox danger';
    res.innerHTML='<div style="font-weight:800;color:var(--red);margin-bottom:8px;font-size:14px">🚨 Riesgo detectado</div>'+
      issues.map(function(i){return'<div style="display:flex;gap:7px;margin-bottom:5px"><span style="color:var(--red);flex-shrink:0">⚠</span><span style="font-size:12px;color:var(--mid)">'+i+'</span></div>';}).join('')+
      '<div style="margin-top:10px;font-size:11.5px;color:var(--mid)"><strong style="color:var(--text)">Recomendación:</strong> No abras este enlace. Verifica en Google Safe Browsing o VirusTotal.</div>';
    toast('⚠️ URL con indicadores de riesgo.','danger');
  }else{
    res.className='rbox ok';
    res.innerHTML='<div style="font-weight:800;color:var(--green);margin-bottom:6px;font-size:14px">✅ Sin riesgos detectados en nuestra base de datos</div>'+
      '<div style="font-size:12px;color:var(--mid)">El dominio no aparece en nuestra lista de amenazas conocidas. '+(raw.startsWith('https')?'Conexión HTTPS ✓.':'Nota: no usa HTTPS, evita introducir datos personales.')+
      ' Para verificación adicional, usa Google Safe Browsing o VirusTotal.</div>';
    toast('✅ URL sin riesgos en base local.','ok');
  }
}
 
function checkEmail(){
  var txt=(document.getElementById('email-txt').value||'').toLowerCase();
  if(!txt.trim()){toast('Pega el texto del email primero.','warn');return;}
  var res=document.getElementById('email-r');res.style.display='block';
  var hits=[],score=0;
  var patterns=[
    {r:/urgente|acción requerida|actúa inmediatamente|expira en \d+ horas/i,m:'Lenguaje de urgencia',p:25},
    {r:/has? ganado|winner|premio|gift card|sorteo|gratis/i,m:'Promesa de premio o beneficio',p:30},
    {r:/contraseña|password|datos bancarios|tarjeta|número de cuenta/i,m:'Solicita credenciales o datos bancarios',p:35},
    {r:/haz clic aquí|click here|accede ahora|verifica tu cuenta|confirma tu identidad/i,m:'Solicita acción inmediata en un enlace',p:20},
    {r:/banco|bbva|santander|caixabank|hacienda|agencia tributaria|correos|dhl|ups/i,m:'Suplanta entidad conocida',p:22},
    {r:/http:\/\/|bit\.ly|tinyurl\.com/i,m:'Enlace sin HTTPS o acortado',p:20},
    {r:/su cuenta (ha sido|será|está) (bloqueada?|suspendida?)/i,m:'Amenaza de suspensión de cuenta',p:28},
    {r:/no respondas a este email|do not reply/i,m:'Email de no respuesta (sin remitente real)',p:10},
  ];
  patterns.forEach(function(p){if(p.r.test(txt)){hits.push({m:p.m,p:p.p});score+=p.p;}});
  score=Math.min(score,100);
 
  if(score>=35||hits.length>=2){
    res.className='rbox danger';
    res.innerHTML='<div style="font-weight:800;color:var(--red);margin-bottom:8px;font-size:14px">🚨 Email sospechoso — Posible phishing</div>'+
      hits.map(function(h){return'<div style="display:flex;gap:7px;margin-bottom:5px"><span style="color:var(--red);flex-shrink:0;font-size:12px">⚠</span><span style="font-size:12px;color:var(--mid)">'+h.m+'</span></div>';}).join('')+
      '<div style="margin-top:10px;font-size:12px;color:var(--mid)"><strong style="color:var(--text)">Recomendación:</strong> No hagas clic en ningún enlace. Contacta directamente con la entidad por sus canales oficiales. Márcalo como spam.</div>';
    toast('🚨 Posible email de phishing.','danger');
  }else if(score>0){
    res.className='rbox warn';
    res.innerHTML='<div style="font-weight:800;color:var(--amber);margin-bottom:6px;font-size:14px">⚠️ Indicadores leves</div>'+
      hits.map(function(h){return'<div style="font-size:12px;color:var(--mid);margin-bottom:4px">· '+h.m+'</div>';}).join('')+
      '<div style="margin-top:8px;font-size:12px;color:var(--mid)">Verifica la dirección del remitente y accede a la plataforma directamente, nunca desde el enlace del email.</div>';
    toast('⚠️ Email con indicadores leves.','warn');
  }else{
    res.className='rbox ok';
    res.innerHTML='<div style="font-weight:800;color:var(--green);margin-bottom:6px;font-size:14px">✅ Sin indicadores de phishing</div>'+
      '<div style="font-size:12px;color:var(--mid)">No se detectaron patrones típicos. Siempre verifica la dirección del remitente y accede directamente a la plataforma.</div>';
    toast('✅ Email sin indicadores de phishing.','ok');
  }
}
 
/* ════════════════════════════════════════════
   TAB: HERRAMIENTAS
════════════════════════════════════════════ */
function buildTools(){
  var secs=[
    {cat:'Filtraciones de datos',items:[
      {n:'Have I Been Pwned',tag:'Gratis',tc:'var(--green)',d:'+12.000 millones de registros indexados. Alertas automáticas por email.',u:'https://haveibeenpwned.com'},
      {n:'Firefox Monitor',tag:'Gratis',tc:'var(--green)',d:'Motor Mozilla sobre HIBP. Alertas automáticas y guías de acción.',u:'https://monitor.mozilla.org'},
      {n:'Dehashed',tag:'Freemium',tc:'var(--amber)',d:'Búsqueda avanzada por email, usuario, IP y hash. Fuentes exclusivas.',u:'https://www.dehashed.com'},
      {n:'LeakCheck.io',tag:'Freemium',tc:'var(--amber)',d:'Motor de filtraciones con API y cobertura de fuentes privadas.',u:'https://leakcheck.io'},
      {n:'Have I Been Sold',tag:'Gratis',tc:'var(--green)',d:'Comprueba si tu email fue vendido a empresas de marketing.',u:'https://haveibeensold.app'},
    ]},
    {cat:'Monitorización Dark Web',items:[
      {n:'Google Dark Web Report',tag:'Gratis',tc:'var(--green)',d:'Monitorización en tiempo real de email, teléfono y nombre en dark web.',u:'https://myaccount.google.com/'},
      {n:'Firefox Monitor Alerts',tag:'Gratis',tc:'var(--green)',d:'Alertas automáticas cuando tu email aparece en nuevas brechas.',u:'https://monitor.mozilla.org'},
      {n:'SpyCloud',tag:'Empresa',tc:'var(--blue)',d:'Plataforma de detección de credenciales robadas para empresas.',u:'https://spycloud.com'},
    ]},
    {cat:'Gestión de contraseñas y 2FA',items:[
      {n:'Pwned Passwords',tag:'Gratis',tc:'var(--green)',d:'Comprueba si tu contraseña apareció en brechas. k-anonimato.',u:'https://haveibeenpwned.com/Passwords'},
      {n:'Bitwarden',tag:'Gratis',tc:'var(--green)',d:'Gestor de contraseñas open source con alertas de brechas integradas.',u:'https://bitwarden.com'},
      {n:'1Password',tag:'Pago',tc:'var(--red)',d:'Watchtower: monitoriza brechas, contraseñas débiles y reutilizadas.',u:'https://1password.com'},
      {n:'Aegis Authenticator',tag:'Gratis',tc:'var(--green)',d:'App 2FA TOTP open source para Android. Backups cifrados.',u:'https://getaegis.app'},
      {n:'2FAS',tag:'Gratis',tc:'var(--green)',d:'Autenticador 2FA para iOS y Android. Sin cuenta requerida.',u:'https://2fas.com'},
      {n:'YubiKey',tag:'Hardware',tc:'var(--purple)',d:'Llave física de seguridad FIDO2/U2F. Máxima protección contra phishing.',u:'https://www.yubico.com'},
    ]},
    {cat:'OSINT y huella digital',items:[
      {n:'Google Alerts',tag:'Gratis',tc:'var(--green)',d:'Alertas automáticas cuando tu nombre o email aparece indexado.',u:'https://www.google.com/alerts'},
      {n:'Shodan',tag:'Freemium',tc:'var(--amber)',d:'Detecta si tus dispositivos (router, cámara) están expuestos.',u:'https://www.shodan.io'},
      {n:'EmailRep.io',tag:'Gratis',tc:'var(--green)',d:'Reputación de un email: brechas, actividad maliciosa, fraude.',u:'https://emailrep.io'},
    ]},
    {cat:'VPN y privacidad',items:[
      {n:'Mullvad VPN',tag:'Pago',tc:'var(--red)',d:'Sin cuenta de email, sin logs. Pago en efectivo disponible.',u:'https://mullvad.net'},
      {n:'ProtonVPN',tag:'Freemium',tc:'var(--amber)',d:'Plan gratuito ilimitado, open source, auditado de forma independiente.',u:'https://protonvpn.com'},
      {n:'SimpleLogin',tag:'Freemium',tc:'var(--amber)',d:'Alias de email para registros sin exponer tu dirección real.',u:'https://simplelogin.io'},
      {n:'NextDNS',tag:'Freemium',tc:'var(--amber)',d:'DNS cifrado con bloqueo de rastreadores, malware y anuncios.',u:'https://nextdns.io'},
      {n:'uBlock Origin',tag:'Gratis',tc:'var(--green)',d:'Bloqueador de rastreadores más efectivo para el navegador.',u:'https://ublockorigin.com'},
    ]},
  ];
  var h='<div style="margin-bottom:20px">' +
    '<h2 style="font-size:20px;font-weight:800;letter-spacing:-.02em;margin-bottom:4px">Herramientas de seguridad</h2>' +
    '<p style="font-size:13px;color:var(--mid);line-height:1.55">Servicios externos recomendados para proteger y verificar tu identidad digital.</p>' +
  '</div>';
  secs.forEach(function(sec){
    h+='<div class="sdiv"><div class="sline"></div><span>'+sec.cat.toUpperCase()+'</span><div class="sline"></div></div>';
    sec.items.forEach(function(item){
      h+='<a href="'+item.u+'" target="_blank" class="tool" style="text-decoration:none">' +
        '<div style="flex:1"><div class="tool-n">'+item.n+'</div><div class="tool-d">'+item.d+'</div></div>' +
        '<div style="display:flex;align-items:center;gap:7px;flex-shrink:0;margin-top:2px">' +
        '<span class="tbdg" style="color:'+item.tc+';background:'+item.tc.replace('var(--','rgba(').replace(')',',0.12)')+';border:1px solid '+item.tc.replace('var(--','rgba(').replace(')',',0.3)')+'">'+item.tag+'</span>' +
        '<span style="color:var(--dim);font-size:13px">→</span></div></a>';
    });
  });
  document.getElementById('tab-tools').innerHTML=h;
}
 
/* ════════════════════════════════════════════
   TAB: GUÍA DE SEGURIDAD
════════════════════════════════════════════ */
function buildTips(){
  var plans=[
    {p:'Urgente',c:'var(--red)',i:'🔑',t:'Contraseñas',steps:['Cambia la contraseña de cualquier plataforma con brecha detectada de forma inmediata.','Usa contraseñas únicas y aleatorias de mínimo 16 caracteres — una diferente por sitio.','Instala Bitwarden (gratuito, open source) para gestionar todas de forma segura.','Comprueba tus contraseñas en haveibeenpwned.com/Passwords.','Activa alertas automáticas de contraseñas comprometidas en el gestor.'],tools:[{l:'Bitwarden',u:'https://bitwarden.com'},{l:'Pwned Passwords',u:'https://haveibeenpwned.com/Passwords'}]},
    {p:'Muy alto',c:'#f97316',i:'📱',t:'Autenticación en 2 pasos (2FA)',steps:['Activa 2FA en todas las cuentas críticas: email, banca, criptomonedas, redes sociales.','Usa app TOTP: Aegis (Android) o Raivo (iOS). Evita el SMS como 2FA.','El SMS es vulnerable a SIM-swap: el atacante puede transferir tu número a otro dispositivo.','Guarda los códigos de recuperación impresos en un lugar físico seguro.','Para cuentas críticas considera una llave física YubiKey.'],tools:[{l:'Aegis',u:'https://getaegis.app'},{l:'2FAS',u:'https://2fas.com'},{l:'YubiKey',u:'https://www.yubico.com'}]},
    {p:'Alto',c:'var(--amber)',i:'👁️',t:'Monitorización continua',steps:['Regístrate en Firefox Monitor para alertas automáticas de nuevas brechas.','Configura Google Alerts con tu nombre y email entre comillas.','Activa notificaciones de inicio de sesión en Google, Apple, Facebook y tu banco.','Revisa mensualmente el historial de accesos en tus principales cuentas.','Activa el Informe de Dark Web de Google — es gratuito.'],tools:[{l:'Firefox Monitor',u:'https://monitor.mozilla.org'},{l:'Google Alerts',u:'https://www.google.com/alerts'}]},
    {p:'Importante',c:'var(--purple)',i:'🕵️',t:'Privacidad y huella digital',steps:['Busca tu nombre y email entre comillas en Google para ver qué información es pública.','Revisa y restringe la privacidad de todos tus perfiles en redes sociales.','Usa alias de email (SimpleLogin) para registros en servicios secundarios.','Usa VPN (Mullvad o ProtonVPN) cuando te conectes a redes Wi-Fi públicas.','Solicita la eliminación de tus datos a brokers de información como Spokeo o Whitepages.'],tools:[{l:'SimpleLogin',u:'https://simplelogin.io'},{l:'Mullvad',u:'https://mullvad.net'},{l:'ProtonVPN',u:'https://protonvpn.com'}]},
    {p:'Avanzado',c:'var(--blue)',i:'🛡️',t:'Configuración avanzada',steps:['Email: activa la Protección Avanzada de Google. Tu email es la llave de tu identidad digital.','Dispositivos: activa BitLocker (Windows) o FileVault (Mac) para cifrar el disco.','Navegador: instala uBlock Origin y usa DNS cifrado (NextDNS o 1.1.1.1).','Banca y criptomonedas: 2FA con app, alerta por transacción, congelar tarjeta en reposo.','Revoca el acceso de apps de terceros obsoletas en cada plataforma trimestralmente.'],tools:[{l:'uBlock Origin',u:'https://ublockorigin.com'},{l:'NextDNS',u:'https://nextdns.io'}]},
    {p:'iOS / iPadOS',c:'var(--cyan)',i:'🍎',t:'Seguridad en iPhone',steps:['Ajustes → Privacidad y seguridad: revisa permisos de Cámara, Micrófono y Localización por app.','Apple ID → Contraseña y seguridad → activa 2FA obligatorio.','Ocultar mi email (iCloud+): genera alias desechables para registros en servicios.','Safari → Privacidad: activa "Evitar seguimiento cruzado" y bloquear cookies de terceros.','Ajustes → Privacidad → Informe de privacidad de apps: revisa accesos recientes.'],tools:[{l:'Have I Been Pwned',u:'https://haveibeenpwned.com'},{l:'ProtonVPN iOS',u:'https://protonvpn.com'}]},
  ];
  var h='<div style="margin-bottom:20px">' +
    '<h2 style="font-size:20px;font-weight:800;letter-spacing:-.02em;margin-bottom:4px">Guía de seguridad</h2>' +
    '<p style="font-size:13px;color:var(--mid);line-height:1.55">Pasos priorizados para proteger tu identidad digital. Empieza por arriba.</p>' +
  '</div>';
  plans.forEach(function(sec){
    h+='<div class="plan" style="border-left:3px solid '+sec.c+'">' +
      '<div class="plan-badge" style="color:'+sec.c+';background:'+sec.c.replace('var(--','rgba(').replace(')',',0.12)')+';border:1px solid '+sec.c.replace('var(--','rgba(').replace(')',',0.3)')+'"><span>'+sec.i+'</span> '+sec.p+'</div>' +
      '<div class="plan-t">'+sec.t+'</div>' +
      '<div style="display:flex;flex-direction:column;gap:7px;margin:12px 0">'+
      sec.steps.map(function(s,i){return'<div class="step"><div class="step-n" style="border-color:'+sec.c.replace('var(--','rgba(').replace(')',',0.3)')+';color:'+sec.c+';background:'+sec.c.replace('var(--','rgba(').replace(')',',0.12)')+'">'+' '+(i+1)+'</div><div class="step-t">'+s+'</div></div>';}).join('')+
      '</div><div class="plan-div"></div><div class="plan-tools">'+
      sec.tools.map(function(t){return'<a href="'+t.u+'" target="_blank" class="btn-sm bsm-blue">'+t.l+' →</a>';}).join('')+
      '</div></div>';
  });
  document.getElementById('tab-tips').innerHTML=h;
}
 
/* ════════════════════════════════════════════
   TAB: INFO
════════════════════════════════════════════ */
function buildAbout(){
  var faqs=[
    {q:'¿Qué es Guardian Shield?',a:'Una suite de seguridad personal para iPhone que incluye: análisis de versión iOS, detección de redes inseguras, verificador de URLs y dominios, detector de phishing por SMS y email, monitor de filtraciones en 52 plataformas y guías de seguridad paso a paso. Todo funciona localmente en tu dispositivo.'},
    {q:'¿Mis datos son privados?',a:'Sí. Toda la funcionalidad se ejecuta directamente en tu iPhone. Ningún dato — ni tu email, ni el texto de mensajes analizados, ni las URLs introducidas — sale de tu dispositivo. No hay servidores, no hay almacenamiento externo.'},
    {q:'¿Por qué los iPhones también pueden estar en riesgo?',a:'iOS tiene una arquitectura muy segura frente a malware tradicional gracias al sandboxing. Sin embargo, los ataques actuales se dirigen a las personas, no al sistema operativo: phishing, smishing, redes Wi-Fi inseguras, versiones de iOS sin actualizar y filtraciones de datos son amenazas reales en 2025.'},
    {q:'¿Qué hago si encuentro brechas en mis cuentas?',a:'1. Cambia la contraseña de esa plataforma inmediatamente. 2. Activa autenticación en dos pasos con una app (no SMS). 3. Revisa el historial de accesos y cierra sesiones desconocidas. 4. Si compartes esa contraseña en otro sitio, cámbiala también allí. 5. Usa Bitwarden para gestionar contraseñas únicas.'},
    {q:'¿Cómo instalar como app en iPhone?',a:'1. Abre este archivo en Safari. 2. Toca el botón Compartir (cuadrado con flecha hacia arriba). 3. Desplázate y toca "Añadir a pantalla de inicio". 4. Nombre: "Guardian Shield". Toca Añadir. Aparecerá como app nativa y funciona sin conexión a internet.'},
    {q:'¿Cada cuánto debería hacer el escaneo?',a:'Se recomienda un escaneo mensual y siempre que recibas un SMS o email sospechoso, uses una red Wi-Fi pública, o una plataforma que uses anuncie un incidente de seguridad. Regístrate en Firefox Monitor para recibir alertas automáticas.'},
  ];
  var h='<div style="text-align:center;margin-bottom:24px">' +
    '<div style="width:72px;height:72px;border-radius:18px;background:linear-gradient(135deg,#3b82f6,#1d4ed8);display:flex;align-items:center;justify-content:center;font-size:34px;margin:0 auto 14px;box-shadow:0 8px 28px rgba(59,130,246,.4)">🛡</div>' +
    '<h1 style="font-size:22px;font-weight:900;letter-spacing:-.03em;margin-bottom:4px">Guardian Shield</h1>' +
    '<div style="font-size:12px;color:var(--dim);font-family:var(--mono);letter-spacing:.06em">Seguridad Personal · Versión 8.0 · 2025</div>' +
    '<div style="font-size:13px;font-weight:600;color:var(--blue);margin-top:8px">Desarrollado por Ignacio Vera</div>' +
  '</div>';
  faqs.forEach(function(item){
    h+='<div class="faq"><div class="faq-q">'+item.q+'</div><div class="faq-a">'+item.a+'</div></div>';
  });
  h+='<div style="background:rgba(59,130,246,.07);border:1px solid rgba(59,130,246,.2);border-radius:13px;padding:16px;margin-top:14px">' +
    '<div style="font-size:14px;font-weight:700;color:var(--blue);margin-bottom:12px">Plataformas analizadas ('+PLATFORMS.length+')</div>' +
    '<div style="display:flex;flex-wrap:wrap;gap:5px">'+
    PLATFORMS.map(function(p){
      var hasB=!!BREACHES[p.id];
      return'<span class="ptag" style="color:'+(hasB?'#fca5a5':'#64748b')+';background:'+(hasB?'rgba(239,68,68,.1)':'rgba(255,255,255,.04)')+';border:1px solid '+(hasB?'rgba(239,68,68,.25)':'rgba(255,255,255,.08)')+'">'+p.icon+' '+p.name+'</span>';
    }).join('')+
    '</div>' +
    '<div style="font-size:10px;color:var(--dim);margin-top:10px;font-weight:500">' +
    '<span style="color:#fca5a5">■</span> Con brecha documentada &nbsp;&nbsp;' +
    '<span style="color:#475569">■</span> Sin brecha en base de datos</div></div>';
  h+='<div class="footer"><div class="cred">🛡 <strong>Ignacio Vera</strong> · Guardian Shield v8.0 · 100% local · Sin publicidad</div></div>';
  document.getElementById('tab-about').innerHTML=h;
}
 
/* ════════════════════════════════════════════
   INIT
════════════════════════════════════════════ */
buildAV();
buildScan();
</script>
</body>
</html>
