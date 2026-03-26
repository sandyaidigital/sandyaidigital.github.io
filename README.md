<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sandy AI Digital Studio | KI Kunst → Einkommen</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Playfair+Display:ital,wght@0,700;0,900;1,700&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --black: #050508;
  --deep: #08080e;
  --dark: #0e0e18;
  --card: #121220;
  --pink: #ff1a7a;
  --pink2: #ff5ca8;
  --pink-dim: rgba(255,26,122,0.12);
  --gold: #d4a843;
  --gold2: #f0c96a;
  --silver: #b8b8cc;
  --light: #e8e8f4;
  --white: #f8f8ff;
}

*, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior: smooth; }

body {
  background: var(--deep);
  color: var(--light);
  font-family: 'DM Sans', sans-serif;
  overflow-x: hidden;
}

/* ── NOISE OVERLAY ── */
body::after {
  content:'';
  position:fixed; inset:0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events:none; z-index:999; opacity:.4;
}

/* ── NAV ── */
nav {
  position: fixed; top:0; left:0; right:0; z-index:100;
  display: flex; justify-content:space-between; align-items:center;
  padding: 1.4rem 5vw;
  background: rgba(8,8,14,0.88);
  backdrop-filter: blur(24px);
  border-bottom: 1px solid rgba(255,26,122,0.1);
}
.nav-logo {
  font-family: 'Bebas Neue', sans-serif;
  font-size: 1.4rem; letter-spacing:4px;
  background: linear-gradient(90deg, var(--pink), var(--gold));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
}
.nav-links { display:flex; gap:2.5rem; list-style:none; }
.nav-links a {
  color: var(--silver); text-decoration:none;
  font-size:.75rem; letter-spacing:2.5px; text-transform:uppercase; font-weight:500;
  transition: color .25s;
}
.nav-links a:hover { color: var(--pink); }
.nav-btn {
  background: var(--pink); color:#fff; border:none;
  padding:.65rem 1.6rem;
  font-family:'DM Sans',sans-serif; font-size:.75rem;
  letter-spacing:2px; text-transform:uppercase; font-weight:700;
  cursor:pointer; transition: all .3s;
  clip-path: polygon(10px 0%,100% 0%,calc(100% - 10px) 100%,0% 100%);
}
.nav-btn:hover { background:var(--pink2); transform:translateY(-1px); box-shadow:0 0 24px rgba(255,26,122,.5); }

/* ── HERO ── */
.hero {
  min-height: 100vh;
  display: grid; grid-template-columns: 1fr 1fr;
  align-items: center; gap:0;
  padding: 7rem 5vw 5rem;
  position: relative; overflow:hidden;
}

/* animated gradient bg */
.hero-glow {
  position:absolute; inset:0; pointer-events:none;
  background:
    radial-gradient(ellipse 55% 70% at 60% 40%, rgba(255,26,122,.14) 0%, transparent 65%),
    radial-gradient(ellipse 40% 50% at 10% 80%, rgba(212,168,67,.07) 0%, transparent 60%);
  animation: glowPulse 6s ease-in-out infinite alternate;
}
@keyframes glowPulse {
  from { opacity:.7; } to { opacity:1; }
}

/* diagonal accent line */
.hero::before {
  content:'';
  position:absolute; top:0; right:42%; bottom:0; width:1px;
  background: linear-gradient(180deg, transparent, rgba(255,26,122,.25) 30%, rgba(255,26,122,.25) 70%, transparent);
}

.hero-left { position:relative; z-index:1; padding-right:4rem; }

.eyebrow {
  display:inline-flex; align-items:center; gap:.6rem;
  background: rgba(255,26,122,.08);
  border: 1px solid rgba(255,26,122,.25);
  padding:.38rem 1rem;
  font-size:.68rem; letter-spacing:3px; text-transform:uppercase;
  color:var(--pink2); margin-bottom:2rem;
  animation: fadeUp .7s ease both;
}
.eyebrow-dot {
  width:6px; height:6px; border-radius:50%; background:var(--pink);
  animation: blink 2s infinite;
}
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:.2} }

.hero-h1 {
  font-family:'Bebas Neue',sans-serif;
  font-size: clamp(3.8rem, 7vw, 7.5rem);
  line-height:.92; letter-spacing:1px;
  margin-bottom:1.6rem;
  animation: fadeUp .7s .1s ease both;
}
.h1-muted { color:rgba(232,232,244,.35); display:block; }
.h1-main  { color:var(--white); display:block; }
.h1-pink  {
  display:block;
  background: linear-gradient(90deg, var(--pink), var(--pink2), var(--gold));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
  background-clip:text;
}

.hero-p {
  font-size:1rem; line-height:1.75; color:var(--silver);
  max-width:420px; margin-bottom:2.5rem; font-weight:300;
  animation: fadeUp .7s .2s ease both;
}
.hero-p strong { color:var(--white); font-weight:600; }

.hero-btns {
  display:flex; gap:1rem; align-items:center;
  animation: fadeUp .7s .3s ease both;
}
.btn-main {
  background: linear-gradient(135deg, var(--pink), #a8005a);
  color:#fff; border:none; padding:1rem 2.4rem;
  font-family:'DM Sans',sans-serif;
  font-size:.85rem; letter-spacing:2px; text-transform:uppercase; font-weight:700;
  cursor:pointer; position:relative; overflow:hidden;
  clip-path: polygon(12px 0%,100% 0%,calc(100% - 12px) 100%,0% 100%);
  transition: all .35s;
  box-shadow: 0 0 32px rgba(255,26,122,.35);
}
.btn-main:hover { transform:translateY(-3px); box-shadow:0 0 52px rgba(255,26,122,.55); }
.btn-main::after {
  content:''; position:absolute; inset:0;
  background: linear-gradient(135deg, rgba(255,255,255,.1), transparent);
}
.btn-link {
  color:var(--silver); font-size:.8rem; letter-spacing:2px;
  text-transform:uppercase; font-weight:500; text-decoration:none;
  display:flex; align-items:center; gap:.4rem;
  transition: color .25s;
}
.btn-link:hover { color:var(--pink); }
.btn-link span { transition: transform .25s; }
.btn-link:hover span { transform:translateX(4px); }

/* Hero right – visual block */
.hero-right {
  position:relative; z-index:1;
  display:flex; flex-direction:column; gap:1.2rem;
  padding-left:3rem;
  animation: fadeUp .7s .25s ease both;
}

.stat-row { display:grid; grid-template-columns:1fr 1fr; gap:1.2rem; }

.stat-box {
  background: var(--card);
  border:1px solid rgba(255,26,122,.12);
  padding:1.8rem 1.5rem;
  position:relative; overflow:hidden;
  transition: border-color .3s, transform .3s;
}
.stat-box:hover { border-color:rgba(255,26,122,.35); transform:translateY(-3px); }
.stat-box::before {
  content:''; position:absolute; top:0; left:0; right:0; height:2px;
  background:linear-gradient(90deg, transparent, var(--pink), transparent);
}
.stat-n {
  font-family:'Bebas Neue',sans-serif; font-size:3.2rem; line-height:1;
  background:linear-gradient(135deg,var(--pink),var(--gold));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
}
.stat-l { font-size:.68rem; letter-spacing:2px; text-transform:uppercase; color:var(--silver); margin-top:.25rem; }

.hero-quote {
  background: linear-gradient(135deg, rgba(255,26,122,.07), rgba(212,168,67,.04));
  border:1px solid rgba(255,26,122,.15);
  border-left: 3px solid var(--pink);
  padding:1.8rem 2rem;
}
.hero-quote p {
  font-family:'Playfair Display',serif; font-style:italic;
  font-size:1.05rem; line-height:1.6; color:var(--light);
}
.hero-quote cite { display:block; margin-top:.8rem; font-size:.72rem; letter-spacing:2px; color:var(--pink2); font-style:normal; text-transform:uppercase; }

/* ── GLOW DIVIDER ── */
.glow-div {
  height:1px;
  background:linear-gradient(90deg,transparent,rgba(255,26,122,.3) 30%,rgba(212,168,67,.2) 70%,transparent);
}

/* ── PROBLEM ── */
.problem {
  padding:8rem 5vw;
  text-align:center;
  background:linear-gradient(180deg,transparent,rgba(255,26,122,.04) 50%,transparent);
}
.section-label {
  font-size:.68rem; letter-spacing:4px; text-transform:uppercase;
  color:var(--pink); font-weight:600; margin-bottom:1rem;
}
.section-h2 {
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(2.2rem,4.5vw,3.8rem);
  line-height:1; letter-spacing:1px; margin-bottom:3rem;
}

.versus {
  display:grid; grid-template-columns:1fr 2px 1fr;
  gap:0; max-width:900px; margin:0 auto;
}
.versus-divider { background:rgba(255,26,122,.2); }
.versus-col { padding:3rem 3.5rem; text-align:left; }
.versus-col.no  { background:rgba(255,255,255,.02); }
.versus-col.yes { background:rgba(255,26,122,.04); }

.versus-head {
  font-family:'Bebas Neue',sans-serif;
  font-size:1.1rem; letter-spacing:3px; margin-bottom:2rem;
}
.versus-col.no .versus-head  { color:rgba(184,184,204,.4); }
.versus-col.yes .versus-head { color:var(--pink); }

.versus-item {
  display:flex; gap:.9rem; align-items:flex-start;
  margin-bottom:1.1rem; font-size:.88rem; color:var(--silver); line-height:1.55;
}
.vi-icon { flex-shrink:0; margin-top:2px; }

/* ── ANGEBOTE ── */
.offers {
  padding:8rem 5vw;
}
.offers-header { text-align:center; margin-bottom:4.5rem; }

.cards {
  display:grid; grid-template-columns:repeat(3,1fr);
  gap:2px; max-width:1100px; margin:0 auto;
  background:rgba(255,26,122,.07);
}
.card {
  background:var(--card); padding:3rem 2.5rem;
  position:relative; overflow:hidden;
  transition:background .35s, transform .35s;
}
.card:hover { background:rgba(255,26,122,.05); transform:translateY(-5px); }

.card.star {
  background:rgba(255,26,122,.06);
  border:1px solid rgba(255,26,122,.22);
  margin:-1px;
}
.card-badge {
  position:absolute; top:0; left:0; right:0;
  background:var(--pink); text-align:center;
  font-size:.62rem; letter-spacing:3px; padding:.4rem;
  font-weight:700; color:#fff; text-transform:uppercase;
}
.card.star { padding-top:3.5rem; }

.card-num {
  font-family:'Bebas Neue',sans-serif;
  font-size:4.5rem; color:rgba(255,26,122,.1); line-height:1; margin-bottom:.4rem;
}
.card-title {
  font-family:'Bebas Neue',sans-serif;
  font-size:1.7rem; letter-spacing:2px; color:var(--white); margin-bottom:.3rem;
}
.card-sub {
  font-size:.68rem; letter-spacing:2px; text-transform:uppercase;
  color:var(--pink2); margin-bottom:1.5rem;
}
.card-body { font-size:.87rem; color:var(--silver); line-height:1.7; margin-bottom:2rem; }
.card-price {
  font-family:'Bebas Neue',sans-serif; font-size:2.8rem; line-height:1;
  background:linear-gradient(135deg,var(--pink),var(--gold));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
  margin-bottom:1.8rem;
}
.card-cta {
  display:inline-block; border:1px solid rgba(255,26,122,.45);
  color:var(--pink); padding:.72rem 1.6rem;
  font-size:.72rem; letter-spacing:2px; text-transform:uppercase;
  font-weight:600; text-decoration:none; cursor:pointer;
  transition:all .3s; background:transparent;
  font-family:'DM Sans',sans-serif;
}
.card.star .card-cta { background:var(--pink); color:#fff; border-color:var(--pink); }
.card-cta:hover { background:var(--pink); color:#fff; }

/* ── AI QUEENS ── */
.queens {
  padding:8rem 5vw;
  background:linear-gradient(180deg,transparent,rgba(212,168,67,.04),transparent);
}
.queens-inner {
  max-width:1100px; margin:0 auto;
  display:grid; grid-template-columns:1fr 1fr; gap:7rem; align-items:center;
}
.queens-features { display:flex; flex-direction:column; gap:1.8rem; margin-top:2rem; }
.qf {
  display:flex; gap:1.2rem; align-items:flex-start;
  padding:1.5rem; background:var(--card);
  border:1px solid rgba(255,26,122,.1);
  transition:border-color .3s;
}
.qf:hover { border-color:rgba(255,26,122,.3); }
.qf-icon {
  width:44px; height:44px; flex-shrink:0;
  background:rgba(255,26,122,.1);
  border:1px solid rgba(255,26,122,.2);
  display:flex; align-items:center; justify-content:center;
  font-size:1.2rem;
}
.qf-title { font-weight:600; font-size:.92rem; margin-bottom:.25rem; color:var(--white); }
.qf-desc  { font-size:.82rem; color:var(--silver); line-height:1.55; }

/* Queens visual */
.queens-visual {
  position:relative;
}
.queens-box {
  background:var(--card);
  border:1px solid rgba(255,26,122,.18);
  padding:3.5rem;
  text-align:center;
  position:relative; overflow:hidden;
}
.queens-box::before {
  content:'';position:absolute;top:0;left:0;right:0;height:3px;
  background:linear-gradient(90deg,var(--pink),var(--gold));
}
.queens-box-title {
  font-family:'Bebas Neue',sans-serif;
  font-size:3.5rem; line-height:1; letter-spacing:2px;
  background:linear-gradient(135deg,var(--pink),var(--gold2));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
  margin-bottom:.5rem;
}
.queens-box-sub { font-size:.75rem; letter-spacing:3px; color:var(--silver); text-transform:uppercase; margin-bottom:2.5rem; }

.queens-pills { display:flex; flex-wrap:wrap; gap:.6rem; justify-content:center; margin-bottom:2rem; }
.pill {
  background:rgba(255,26,122,.08); border:1px solid rgba(255,26,122,.2);
  padding:.35rem .9rem; font-size:.72rem; letter-spacing:1.5px;
  text-transform:uppercase; color:var(--pink2);
}

.queens-note {
  font-size:.82rem; color:var(--silver); line-height:1.6;
  border-top:1px solid rgba(255,26,122,.1); padding-top:1.5rem;
}
.queens-note strong { color:var(--pink); }

/* ── TOOLS ── */
.tools { padding:6rem 5vw; border-top:1px solid rgba(255,26,122,.07); }
.tools-inner { max-width:900px; margin:0 auto; text-align:center; }
.tools-grid {
  display:flex; flex-wrap:wrap; gap:.7rem;
  justify-content:center; margin-top:2.5rem;
}
.tool {
  background:var(--card); border:1px solid rgba(255,26,122,.1);
  padding:.55rem 1.2rem;
  font-size:.78rem; letter-spacing:1.5px; text-transform:uppercase; color:var(--silver);
  transition:all .25s;
}
.tool:hover { border-color:var(--pink); color:var(--pink); }

/* ── CTA ── */
.cta-section {
  padding:9rem 5vw;
  text-align:center; position:relative; overflow:hidden;
}
.cta-glow {
  position:absolute; inset:0; pointer-events:none;
  background:radial-gradient(ellipse 60% 60% at center, rgba(255,26,122,.12) 0%, transparent 70%);
}
.cta-h2 {
  font-family:'Bebas Neue',sans-serif;
  font-size:clamp(2.8rem,6vw,5.5rem);
  line-height:.94; margin-bottom:1.5rem; position:relative;
}
.cta-h2 em { color:var(--pink); font-style:normal; }
.cta-p {
  font-size:1rem; color:var(--silver); max-width:480px;
  margin:0 auto 2.8rem; line-height:1.7; font-weight:300; position:relative;
}
.cta-price-hint {
  display:inline-block; background:rgba(255,26,122,.08);
  border:1px solid rgba(255,26,122,.2); padding:.5rem 1.5rem;
  font-size:.78rem; letter-spacing:2px; color:var(--pink2);
  text-transform:uppercase; margin-bottom:2rem; position:relative;
}

/* ── FOOTER ── */
footer {
  border-top:1px solid rgba(255,26,122,.08);
  padding:2.2rem 5vw;
  display:flex; justify-content:space-between; align-items:center;
  font-size:.76rem; color:rgba(184,184,204,.35);
}
footer a { color:var(--pink); text-decoration:none; }
.footer-links { display:flex; gap:2rem; }
.footer-logo {
  font-family:'Bebas Neue',sans-serif; font-size:1.1rem; letter-spacing:3px;
  background:linear-gradient(90deg,var(--pink),var(--gold));
  -webkit-background-clip:text; -webkit-text-fill-color:transparent;
}

@keyframes fadeUp {
  from { opacity:0; transform:translateY(28px); }
  to   { opacity:1; transform:translateY(0); }
}

/* ── RESPONSIVE ── */
@media(max-width:900px){
  .hero { grid-template-columns:1fr; padding:7rem 5vw 4rem; }
  .hero::before { display:none; }
  .hero-left { padding-right:0; }
  .hero-right { padding-left:0; }
  .stat-row { grid-template-columns:1fr 1fr; }
  .cards { grid-template-columns:1fr; }
  .versus { grid-template-columns:1fr; }
  .versus-divider { display:none; }
  .queens-inner { grid-template-columns:1fr; gap:3.5rem; }
  nav .nav-links { display:none; }
  .about-inner { grid-template-columns:1fr; }
  footer { flex-direction:column; gap:1rem; text-align:center; }
  .footer-links { flex-wrap:wrap; justify-content:center; }
}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">Sandy AI Digital Studio</div>
  <ul class="nav-links">
    <li><a href="#angebote">Angebote</a></li>
    <li><a href="#queens">AI Queens</a></li>
    <li><a href="#about">Über mich</a></li>
    <li><a href="#kontakt">Kontakt</a></li>
  </ul>
  <button class="nav-btn">Leitfaden – 47€</button>
</nav>

<!-- ══ HERO ══ -->
<section class="hero">
  <div class="hero-glow"></div>

  <div class="hero-left">
    <div class="eyebrow">
      <span class="eyebrow-dot"></span>
      KI-Expertin &amp; Digitale Künstlerin seit 2017
    </div>

    <h1 class="hero-h1">
      <span class="h1-muted">Andere</span>
      <span class="h1-main">Träumen.</span>
      <span class="h1-pink">Ich kreiere.</span>
    </h1>

    <p class="hero-p">
      Ich verwandle <strong>KI in echtes Einkommen.</strong><br>
      Seit 2017 kombiniere ich künstliche Intelligenz, digitale Kunst und Automation –
      und zeige Frauen, wie sie dasselbe tun können.
    </p>

    <div class="hero-btns">
      <button class="btn-main">Leitfaden sichern – 47€</button>
      <a href="#queens" class="btn-link">AI Queens Circle <span>→</span></a>
    </div>
  </div>

  <div class="hero-right">
    <div class="stat-row">
      <div class="stat-box">
        <div class="stat-n">100+</div>
        <div class="stat-l">KI-Projekte</div>
      </div>
      <div class="stat-box">
        <div class="stat-n">7+</div>
        <div class="stat-l">Jahre Erfahrung</div>
      </div>
      <div class="stat-box">
        <div class="stat-n">500+</div>
        <div class="stat-l">Prompts entwickelt</div>
      </div>
      <div class="stat-box">
        <div class="stat-n">2017</div>
        <div class="stat-l">Gestartet</div>
      </div>
    </div>

    <div class="hero-quote">
      <p>„Ich habe gesehen, wie viele warten, während andere digitale Kunst-Imperien aufbauen. Ich liefere Ergebnisse statt Ausreden."</p>
      <cite>— Sandy, Gründerin Sandy AI Digital Studio</cite>
    </div>
  </div>
</section>

<div class="glow-div"></div>

<!-- ══ PROBLEM ══ -->
<section class="problem">
  <div class="section-label">Die Realität</div>
  <h2 class="section-h2">KI ist kein Trend.<br>KI ist ein Werkzeug.</h2>

  <div class="versus">
    <div class="versus-col no">
      <div class="versus-head">❌ &nbsp;Die meisten warten</div>
      <div class="versus-item"><span class="vi-icon">—</span>„Ich weiß nicht wo ich anfangen soll"</div>
      <div class="versus-item"><span class="vi-icon">—</span>Schauen zu, wie andere Imperien bauen</div>
      <div class="versus-item"><span class="vi-icon">—</span>Kein System, keine Ergebnisse</div>
      <div class="versus-item"><span class="vi-icon">—</span>Investieren Zeit ohne Richtung</div>
      <div class="versus-item"><span class="vi-icon">—</span>KI bleibt ein Mysterium</div>
    </div>
    <div class="versus-divider"></div>
    <div class="versus-col yes">
      <div class="versus-head">✦ &nbsp;AI Queens handeln</div>
      <div class="versus-item"><span class="vi-icon">→</span>Klares System mit echten Schritten</div>
      <div class="versus-item"><span class="vi-icon">→</span>Bauen passive Einnahmequellen auf</div>
      <div class="versus-item"><span class="vi-icon">→</span>Nutzen KI als Werkzeug – nicht Magie</div>
      <div class="versus-item"><span class="vi-icon">→</span>Ergebnisse statt Ausreden</div>
      <div class="versus-item"><span class="vi-icon">→</span>Kunst wird zu digitalem Einkommen</div>
    </div>
  </div>
</section>

<div class="glow-div"></div>

<!-- ══ ANGEBOTE ══ -->
<section class="offers" id="angebote">
  <div class="offers-header">
    <div class="section-label">Meine Angebote</div>
    <h2 class="section-h2">Dein Weg ins digitale Imperium</h2>
  </div>

  <div class="cards">
    <div class="card">
      <div class="card-num">01</div>
      <div class="card-title">AI Kunst Leitfaden</div>
      <div class="card-sub">Digitales Produkt · Sofort-Download</div>
      <div class="card-body">
        Schritt für Schritt: KI-Kunst erstellen, die richtigen Tools auswählen, deine Kunst verkaufen und dein erstes digitales Einkommen aufbauen. Kein Theoriekurs – nur Systeme, die wirklich funktionieren.
      </div>
      <div class="card-price">47€</div>
      <button class="card-cta">Jetzt kaufen</button>
    </div>

    <div class="card star">
      <div class="card-badge">★ &nbsp;Empfohlen &nbsp;★</div>
      <div class="card-num">02</div>
      <div class="card-title">AI Queens Circle</div>
      <div class="card-sub">Community · Umsetzung · Support</div>
      <div class="card-body">
        Beim Kauf des Leitfadens bekommst du sofort Zugang. Eine Community für Frauen, die nicht nur konsumieren – sondern umsetzen. KI-Kunst, digitale Produkte, echter Austausch. Kein Lurking.
      </div>
      <div class="card-price">Inklusive 👑</div>
      <button class="card-cta">Leitfaden + Community</button>
    </div>

    <div class="card">
      <div class="card-num">03</div>
      <div class="card-title">1:1 Mentoring</div>
      <div class="card-sub">Exklusiv · 3 Monate · Intensiv</div>
      <div class="card-body">
        Für Frauen, die schnell und gezielt skalieren wollen. Ich zeige dir persönlich wie du mit KI-Design, digitaler Kunst und Automation dein monatliches Einkommen nachhaltig aufbaust.
      </div>
      <div class="card-price">997€+</div>
      <a href="https://calendly.com/sandraschuelerkaiser/lassunsreden" class="card-cta">Kostenloses Gespräch</a>
    </div>
  </div>
</section>

<div class="glow-div"></div>

<!-- ══ AI QUEENS ══ -->
<section class="queens" id="queens">
  <div class="queens-inner">
    <div>
      <div class="section-label">Community</div>
      <h2 class="section-h2">AI Queens<br>Circle 👑</h2>
      <p style="color:var(--silver);line-height:1.75;margin:1rem 0;font-size:.95rem;font-weight:300;">
        Kein Lurking. Keine leere Theorie. Nur Frauen die ihre Vision in echtes Einkommen verwandeln – gemeinsam, mit System, mit Support.
      </p>

      <div class="queens-features">
        <div class="qf">
          <div class="qf-icon">🎨</div>
          <div>
            <div class="qf-title">KI-Kunst erstellen &amp; verkaufen</div>
            <div class="qf-desc">Anleitungen, Feedback und Tools die wirklich funktionieren. Von der Idee zum verkauften Artwork.</div>
          </div>
        </div>
        <div class="qf">
          <div class="qf-icon">💰</div>
          <div>
            <div class="qf-title">Digitale Produkte &amp; passives Einkommen</div>
            <div class="qf-desc">Prompts, Leitfäden, Vorlagen – einmal erstellen, immer wieder verkaufen.</div>
          </div>
        </div>
        <div class="qf">
          <div class="qf-icon">👑</div>
          <div>
            <div class="qf-title">Community &amp; echter Austausch</div>
            <div class="qf-desc">Frauen auf demselben Weg. Motivation, Ideen, gemeinsame Wins – und keine Einzelkämpferei.</div>
          </div>
        </div>
      </div>

      <div style="margin-top:2.5rem;">
        <button class="btn-main">Leitfaden kaufen &amp; beitreten</button>
      </div>
    </div>

    <div class="queens-visual">
      <div class="queens-box">
        <div class="queens-box-title">Digital<br>Mastermind</div>
        <div class="queens-box-sub">WhatsApp · Community · Umsetzung</div>

        <div class="queens-pills">
          <span class="pill">KI Kunst</span>
          <span class="pill">AI Art verkaufen</span>
          <span class="pill">Digitale Produkte</span>
          <span class="pill">Monetarisieren</span>
          <span class="pill">Automation</span>
          <span class="pill">Einkommen</span>
        </div>

        <div class="queens-note">
          Zugang <strong>nur mit Leitfaden.</strong><br>
          Keine Theorie. Hier wird umgesetzt.<br><br>
          DM <strong>„AI"</strong> auf WhatsApp oder Instagram für mehr Infos.
        </div>
      </div>
    </div>
  </div>
</section>

<div class="glow-div"></div>

<!-- ══ TOOLS ══ -->
<section class="tools">
  <div class="tools-inner">
    <div class="section-label">Mein Toolset</div>
    <h2 class="section-h2" style="font-size:clamp(1.8rem,3vw,2.5rem);">Tools mit denen ich täglich arbeite</h2>
    <div class="tools-grid">
      <span class="tool">ChatGPT</span>
      <span class="tool">Midjourney</span>
      <span class="tool">DALL-E 3</span>
      <span class="tool">Leonardo AI</span>
      <span class="tool">Gemini</span>
      <span class="tool">Claude AI</span>
      <span class="tool">Adobe Firefly</span>
      <span class="tool">n8n Automation</span>
      <span class="tool">Copilot</span>
      <span class="tool">Stable Diffusion</span>
      <span class="tool">Adobe Stock</span>
      <span class="tool">Etsy</span>
      <span class="tool">Gumroad</span>
    </div>
  </div>
</section>

<div class="glow-div"></div>

<!-- ══ CTA ══ -->
<section class="cta-section" id="kontakt">
  <div class="cta-glow"></div>
  <div class="section-label">Bereit?</div>
  <h2 class="cta-h2">
    Andere träumen.<br>
    <em>AI Queens bauen.</em>
  </h2>
  <p class="cta-p">
    Dein Imperium startet mit einem Schritt. Der Leitfaden gibt dir das System. Der Queens Circle gibt dir die Community. Du gibst die Umsetzung.
  </p>
  <div class="cta-price-hint">AI Kunst Leitfaden + Queens Circle Zugang – 47€</div>
  <br><br>
  <button class="btn-main" style="font-size:.9rem;padding:1.1rem 3rem;">
    Jetzt Leitfaden sichern →
  </button>
  <p style="margin-top:1.5rem;font-size:.78rem;color:rgba(184,184,204,.4);letter-spacing:1px;">
    oder DM „AI" auf Instagram &nbsp;·&nbsp; 
    <a href="https://calendly.com/sandraschuelerkaiser/lassunsreden" style="color:var(--pink);text-decoration:none;">Kostenloses Gespräch buchen</a>
  </p>
</section>

<!-- ══ FOOTER ══ -->
<footer>
  <div class="footer-logo">Sandy AI Digital Studio</div>
  <div class="footer-links">
    <a href="#">Datenschutz</a>
    <a href="#">Impressum</a>
    <a href="#">AGB</a>
    <a href="https://www.instagram.com/sandradigitalart/">Instagram</a>
  </div>
  <div>© 2026 Sandy AI Digital Studio</div>
</footer>

</body>
</html>
