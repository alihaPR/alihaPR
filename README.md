<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Norse — Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;900&family=Cinzel+Decorative:wght@700;900&family=MedievalSharp&display=swap" rel="stylesheet"/>
<style>
  :root {
    --ice: #a8d8ea;
    --frost: #d4eef8;
    --blood: #8b1a1a;
    --ember: #c0392b;
    --gold: #c9a96e;
    --dark: #060810;
    --dark2: #0b0e18;
    --stone: #1a1e2e;
    --fog: rgba(168,216,234,0.05);
    --text: #c8d8e8;
    --muted: #5a6a7a;
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  body {
    background: var(--dark);
    color: var(--text);
    font-family: 'Cinzel', serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Aurora background */
  .aurora {
    position: fixed;
    inset: 0;
    z-index: 0;
    overflow: hidden;
  }

  .aurora-band {
    position: absolute;
    width: 200%;
    height: 300px;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0;
    animation: auroraDrift linear infinite;
  }

  .aurora-band:nth-child(1) {
    background: linear-gradient(90deg, transparent, rgba(0,80,120,0.25), rgba(0,150,100,0.2), transparent);
    top: 5%;
    animation-duration: 18s;
    animation-delay: 0s;
  }
  .aurora-band:nth-child(2) {
    background: linear-gradient(90deg, transparent, rgba(60,0,120,0.2), rgba(0,100,80,0.15), transparent);
    top: 12%;
    animation-duration: 24s;
    animation-delay: -8s;
  }
  .aurora-band:nth-child(3) {
    background: linear-gradient(90deg, transparent, rgba(0,60,100,0.2), rgba(80,0,100,0.15), transparent);
    top: 2%;
    animation-duration: 30s;
    animation-delay: -14s;
  }

  @keyframes auroraDrift {
    0%   { transform: translateX(-50%) scaleY(1);   opacity: 0; }
    15%  { opacity: 1; }
    50%  { transform: translateX(0%) scaleY(1.4);   opacity: 0.7; }
    85%  { opacity: 1; }
    100% { transform: translateX(50%) scaleY(1);    opacity: 0; }
  }

  /* Stars */
  .stars {
    position: fixed;
    inset: 0;
    z-index: 0;
  }

  .star {
    position: absolute;
    background: white;
    border-radius: 50%;
    animation: twinkle ease-in-out infinite;
  }

  @keyframes twinkle {
    0%, 100% { opacity: 0.1; transform: scale(1); }
    50%       { opacity: 0.9; transform: scale(1.3); }
  }

  /* Snow particles */
  .snow {
    position: fixed;
    inset: 0;
    z-index: 1;
    pointer-events: none;
  }

  .flake {
    position: absolute;
    top: -10px;
    color: rgba(168,216,234,0.6);
    font-size: 10px;
    animation: snowFall linear infinite;
    user-select: none;
  }

  @keyframes snowFall {
    0%   { transform: translateY(-20px) translateX(0) rotate(0deg);   opacity: 0; }
    10%  { opacity: 1; }
    90%  { opacity: 0.6; }
    100% { transform: translateY(105vh) translateX(40px) rotate(360deg); opacity: 0; }
  }

  /* Vignette */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background: radial-gradient(ellipse at center, transparent 30%, rgba(6,8,16,0.9) 100%);
    pointer-events: none;
    z-index: 2;
  }

  /* ── LAYOUT ── */
  .container {
    position: relative;
    z-index: 3;
    max-width: 860px;
    margin: 0 auto;
    padding: 0 24px 80px;
  }

  /* ── TOP BAR ── */
  .top-bar {
    text-align: center;
    padding: 18px 0 14px;
    border-bottom: 1px solid rgba(168,216,234,0.1);
    font-size: 11px;
    letter-spacing: 10px;
    color: rgba(168,216,234,0.2);
    animation: pulse 6s ease-in-out infinite;
  }

  @keyframes pulse {
    0%,100% { opacity:0.4; } 50% { opacity:0.9; }
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding: 60px 0 48px;
    opacity: 0;
    animation: riseUp 1.4s cubic-bezier(0.16,1,0.3,1) 0.4s forwards;
  }

  @keyframes riseUp {
    from { opacity:0; transform: translateY(40px); }
    to   { opacity:1; transform: translateY(0); }
  }

  /* Longship silhouette above avatar */
  .longship {
    font-size: 40px;
    margin-bottom: 24px;
    display: block;
    filter: drop-shadow(0 0 20px rgba(168,216,234,0.3));
    animation: shipFloat 6s ease-in-out infinite;
  }

  @keyframes shipFloat {
    0%,100% { transform: translateY(0) rotate(-1deg); }
    50%      { transform: translateY(-8px) rotate(1deg); }
  }

  .avatar-wrap {
    position: relative;
    display: inline-block;
    margin-bottom: 36px;
  }

  .avatar {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    background: radial-gradient(circle at 40% 35%, var(--stone), var(--dark));
    border: 1px solid rgba(168,216,234,0.25);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 64px;
    box-shadow:
      0 0 0 8px rgba(168,216,234,0.04),
      0 0 50px rgba(168,216,234,0.12),
      0 0 100px rgba(0,80,120,0.2),
      inset 0 0 30px rgba(0,0,0,0.5);
    animation: frostGlow 5s ease-in-out infinite;
  }

  @keyframes frostGlow {
    0%,100% { box-shadow: 0 0 0 8px rgba(168,216,234,0.04), 0 0 50px rgba(168,216,234,0.12), 0 0 100px rgba(0,80,120,0.2), inset 0 0 30px rgba(0,0,0,0.5); }
    50%      { box-shadow: 0 0 0 10px rgba(168,216,234,0.08), 0 0 70px rgba(168,216,234,0.22), 0 0 140px rgba(0,80,120,0.3), inset 0 0 30px rgba(0,0,0,0.5); }
  }

  /* Rotating rune ring */
  .rune-ring {
    position: absolute;
    inset: -18px;
    border-radius: 50%;
    animation: spinRing 25s linear infinite;
  }

  .rune-ring svg {
    width: 100%;
    height: 100%;
  }

  @keyframes spinRing { from{transform:rotate(0)} to{transform:rotate(360deg)} }

  .rune-ring2 {
    position: absolute;
    inset: -30px;
    border-radius: 50%;
    border: 1px dashed rgba(168,216,234,0.08);
    animation: spinRing 40s linear infinite reverse;
  }

  .hero-name {
    font-family: 'Cinzel Decorative', serif;
    font-size: clamp(30px, 5.5vw, 52px);
    font-weight: 900;
    letter-spacing: 5px;
    color: var(--frost);
    text-shadow:
      0 0 30px rgba(168,216,234,0.5),
      0 0 80px rgba(168,216,234,0.2),
      0 2px 4px rgba(0,0,0,0.9);
    margin-bottom: 10px;
    animation: nameGlitch 8s ease-in-out infinite;
  }

  @keyframes nameGlitch {
    0%,95%,100% { text-shadow: 0 0 30px rgba(168,216,234,0.5), 0 0 80px rgba(168,216,234,0.2), 0 2px 4px rgba(0,0,0,0.9); }
    96%  { text-shadow: 3px 0 var(--blood), -3px 0 var(--ice), 0 0 30px rgba(168,216,234,0.5); }
    97%  { text-shadow: -3px 0 var(--blood), 3px 0 var(--ice), 0 0 30px rgba(168,216,234,0.5); }
    98%  { text-shadow: 0 0 30px rgba(168,216,234,0.5), 0 0 80px rgba(168,216,234,0.2); }
  }

  .hero-sub {
    font-size: 10px;
    letter-spacing: 8px;
    color: var(--muted);
    margin-bottom: 20px;
    text-transform: uppercase;
  }

  /* Typing */
  .typing-box {
    height: 26px;
    margin-bottom: 32px;
  }

  #typing {
    font-size: 13px;
    letter-spacing: 2px;
    color: var(--ice);
    border-right: 1px solid var(--ice);
    padding-right: 3px;
    font-style: italic;
    animation: iceBlink 0.75s step-end infinite;
    text-shadow: 0 0 12px rgba(168,216,234,0.6);
  }

  @keyframes iceBlink {
    0%,100%{border-color:var(--ice)} 50%{border-color:transparent}
  }

  /* Badges */
  .badges {
    display: flex;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
  }

  .badge {
    padding: 8px 22px;
    border: 1px solid rgba(168,216,234,0.2);
    color: var(--muted);
    font-size: 9px;
    letter-spacing: 4px;
    cursor: pointer;
    transition: all 0.4s;
    position: relative;
    overflow: hidden;
    background: rgba(168,216,234,0.02);
  }

  .badge::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(168,216,234,0.1), rgba(168,216,234,0.02));
    transform: translateX(-100%);
    transition: transform 0.4s;
  }

  .badge:hover::before { transform: translateX(0); }
  .badge:hover {
    border-color: rgba(168,216,234,0.5);
    color: var(--ice);
    box-shadow: 0 0 20px rgba(168,216,234,0.1), inset 0 0 20px rgba(168,216,234,0.03);
    transform: translateY(-2px);
    text-shadow: 0 0 10px rgba(168,216,234,0.5);
  }

  /* ── DIVIDER ── */
  .divider {
    display: flex;
    align-items: center;
    gap: 16px;
    margin: 36px 0;
    opacity: 0.3;
  }

  .divider::before, .divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--ice), transparent);
  }

  .div-sym { color: var(--ice); font-size: 12px; letter-spacing: 8px; }

  /* ── SECTIONS ── */
  .section {
    margin-bottom: 48px;
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.9s ease, transform 0.9s ease;
  }

  .section.visible { opacity:1; transform:translateY(0); }

  .sec-head {
    font-size: 9px;
    letter-spacing: 7px;
    color: var(--ice);
    text-shadow: 0 0 12px rgba(168,216,234,0.4);
    margin-bottom: 22px;
    display: flex;
    align-items: center;
    gap: 14px;
    opacity: 0.7;
  }

  .sec-head::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, rgba(168,216,234,0.3), transparent);
  }

  /* About */
  .saga-card {
    border: 1px solid rgba(168,216,234,0.08);
    border-left: 2px solid rgba(168,216,234,0.3);
    background: var(--fog);
    padding: 28px 32px;
    font-family: 'Cinzel', serif;
    font-size: 14px;
    line-height: 2.1;
    color: #8a9aaa;
    position: relative;
    overflow: hidden;
  }

  .saga-card::before {
    content: '';
    position: absolute;
    top: 0; right: 0;
    width: 120px; height: 120px;
    background: radial-gradient(circle, rgba(168,216,234,0.04), transparent 70%);
  }

  .saga-card em { color: var(--ice); font-style: normal; text-shadow: 0 0 8px rgba(168,216,234,0.3); }

  .meta-row {
    margin-top: 18px;
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
    font-size: 9px;
    letter-spacing: 3px;
    color: var(--muted);
  }

  /* Stack */
  .weapons {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
    gap: 8px;
  }

  .weapon {
    border: 1px solid rgba(168,216,234,0.1);
    background: rgba(168,216,234,0.02);
    padding: 10px 14px;
    font-size: 9px;
    letter-spacing: 2px;
    color: var(--muted);
    text-align: center;
    cursor: default;
    transition: all 0.35s;
    position: relative;
    overflow: hidden;
  }

  .weapon::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 1px;
    background: var(--ice);
    transform: scaleX(0);
    transition: transform 0.35s;
  }

  .weapon:hover::after { transform: scaleX(1); }
  .weapon:hover {
    border-color: rgba(168,216,234,0.3);
    color: var(--ice);
    background: rgba(168,216,234,0.05);
    transform: translateY(-3px);
    box-shadow: 0 6px 24px rgba(168,216,234,0.06);
    text-shadow: 0 0 8px rgba(168,216,234,0.4);
  }

  /* Stats */
  .chronicle-grid {
    display: grid;
    grid-template-columns: repeat(3,1fr);
    gap: 10px;
    margin-bottom: 12px;
  }

  .chron {
    border: 1px solid rgba(168,216,234,0.1);
    background: var(--fog);
    padding: 22px 12px;
    text-align: center;
    transition: all 0.4s;
    position: relative;
    overflow: hidden;
  }

  .chron::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(168,216,234,0.04), transparent);
    opacity: 0;
    transition: opacity 0.4s;
  }

  .chron:hover::before { opacity: 1; }
  .chron:hover {
    border-color: rgba(168,216,234,0.25);
    box-shadow: 0 0 30px rgba(168,216,234,0.06);
    transform: translateY(-3px);
  }

  .chron-n {
    font-family: 'Cinzel Decorative', serif;
    font-size: 34px;
    color: var(--ice);
    text-shadow: 0 0 20px rgba(168,216,234,0.4);
    display: block;
    margin-bottom: 8px;
    line-height: 1;
  }

  .chron-l {
    font-size: 8px;
    letter-spacing: 3px;
    color: var(--muted);
  }

  /* Streak */
  .voyage-bar {
    border: 1px solid rgba(168,216,234,0.1);
    background: var(--fog);
    padding: 22px 26px;
  }

  .vb-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 16px;
  }

  .vb-label {
    font-size: 8px;
    letter-spacing: 5px;
    color: var(--muted);
  }

  .vb-val {
    font-family: 'Cinzel Decorative', serif;
    font-size: 22px;
    color: var(--ice);
    text-shadow: 0 0 15px rgba(168,216,234,0.5);
  }

  .bar-bg {
    height: 3px;
    background: rgba(168,216,234,0.05);
    position: relative;
  }

  .bar-ice {
    height: 100%;
    width: 0;
    background: linear-gradient(90deg, #1a3a5c, var(--ice), var(--frost));
    animation: iceGrow 2.2s cubic-bezier(0.16,1,0.3,1) 1.8s forwards;
    box-shadow: 0 0 14px rgba(168,216,234,0.5);
    position: relative;
  }

  .bar-ice::after {
    content: '❄';
    position: absolute;
    right: -8px; top: -10px;
    color: var(--ice);
    font-size: 10px;
    text-shadow: 0 0 10px var(--ice);
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes iceGrow { to { width: 73%; } }

  /* Now */
  .saga-list { list-style: none; }

  .saga-item {
    display: flex;
    gap: 22px;
    padding: 14px 0;
    border-bottom: 1px solid rgba(168,216,234,0.05);
    font-size: 13px;
    color: #5a6a7a;
    transition: all 0.35s;
    align-items: flex-start;
  }

  .saga-item:last-child { border-bottom: none; }

  .saga-item:hover {
    color: var(--text);
    padding-left: 8px;
  }

  .saga-key {
    font-size: 8px;
    letter-spacing: 3px;
    color: var(--ice);
    opacity: 0.6;
    min-width: 90px;
    padding-top: 3px;
    transition: opacity 0.35s;
  }

  .saga-item:hover .saga-key { opacity: 1; }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding-top: 52px;
    opacity: 0;
    animation: riseUp 1s ease 2s forwards;
  }

  .footer-runes {
    font-size: 16px;
    letter-spacing: 18px;
    color: rgba(168,216,234,0.15);
    margin-bottom: 20px;
    animation: pulse 7s ease-in-out infinite;
  }

  .footer-quote {
    font-style: italic;
    font-size: 14px;
    color: rgba(168,216,234,0.35);
    line-height: 1.9;
    margin-bottom: 20px;
  }

  .footer-sig {
    font-size: 8px;
    letter-spacing: 6px;
    color: rgba(168,216,234,0.12);
  }

  /* Ice crack on scroll */
  .crack-line {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(168,216,234,0.15), rgba(168,216,234,0.3), rgba(168,216,234,0.15), transparent);
    margin: 0;
    position: relative;
    overflow: visible;
  }
</style>
</head>
<body>

<!-- Aurora -->
<div class="aurora">
  <div class="aurora-band"></div>
  <div class="aurora-band"></div>
  <div class="aurora-band"></div>
</div>

<!-- Stars -->
<div class="stars" id="stars"></div>

<!-- Snow -->
<div class="snow" id="snow"></div>

<div class="container">

  <!-- Top rune bar -->
  <div class="top-bar">ᚠ ᚢ ᚦ ᚨ ᚱ ᚲ ᚷ ᚹ ᚺ ᚾ ᛁ ᛃ ᛇ ᛈ ᛉ ᛊ ᛏ ᛒ ᛖ ᛗ ᛚ ᛜ ᛞ ᛟ</div>

  <!-- HERO -->
  <div class="hero">

    <span class="longship">⛵</span>

    <div class="avatar-wrap">
      <div class="rune-ring2"></div>
      <div class="rune-ring">
        <svg viewBox="0 0 186 186" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="93" cy="93" r="89" stroke="rgba(168,216,234,0.2)" stroke-width="1" stroke-dasharray="4 8"/>
          <text font-family="serif" font-size="11" fill="rgba(168,216,234,0.35)">
            <textPath href="#circle-path">ᚠ ᚢ ᚦ ᚨ ᚱ ᚲ ᚷ ᚹ ᚺ ᚾ ᛁ ᛃ ᛇ ᛈ ᛉ ᛊ ᛏ ᛒ ᛖ ᛗ ᛚ ᛜ ᛞ ᛟ ✦ </textPath>
          </text>
          <defs>
            <path id="circle-path" d="M 93,4 a 89,89 0 1,1 -0.1,0"/>
          </defs>
        </svg>
      </div>
      <div class="avatar">🪓</div>
    </div>

    <div class="hero-name">YOUR NAME</div>
    <div class="hero-sub">Frontend Developer · Craftsman of the Digital North</div>

    <div class="typing-box">
      <span id="typing"></span>
    </div>

    <div class="badges">
      <span class="badge">⚓ PORTFOLIO</span>
      <span class="badge">❄ LINKEDIN</span>
      <span class="badge">🌊 TWITTER</span>
    </div>
  </div>

  <div class="crack-line"></div>
  <div class="divider"><span class="div-sym">✦ ✦ ✦</span></div>

  <!-- ABOUT -->
  <div class="section">
    <div class="sec-head">⊹ THE SAGA</div>
    <div class="saga-card">
      I am <em>YOUR NAME</em> — a warrior of the frontend realm,
      forging interfaces from the raw materials of code and design.<br/><br/>
      Like the Norse explorers who sailed beyond the known world,
      I seek the <em>frontier</em> — pushing past conventional UI into territories
      where <em>motion</em>, <em>interaction</em>, and <em>beauty</em> converge.<br/><br/>
      Every pixel placed with purpose. Every animation with intention.
      <div class="meta-row">
        <span>🌍 IRAN</span>
        <span>⚔️ OPEN TO WORK</span>
        <span>☕ COFFEE & CODE</span>
      </div>
    </div>
  </div>

  <!-- STACK -->
  <div class="section">
    <div class="sec-head">⊹ WEAPONS OF THE CRAFT</div>
    <div class="weapons">
      <div class="weapon">HTML5</div>
      <div class="weapon">CSS3</div>
      <div class="weapon">JAVASCRIPT</div>
      <div class="weapon">TYPESCRIPT</div>
      <div class="weapon">REACT</div>
      <div class="weapon">NEXT.JS</div>
      <div class="weapon">VUE</div>
      <div class="weapon">TAILWIND</div>
      <div class="weapon">GSAP</div>
      <div class="weapon">FRAMER</div>
      <div class="weapon">THREE.JS</div>
      <div class="weapon">FIGMA</div>
    </div>
  </div>

  <!-- STATS -->
  <div class="section">
    <div class="sec-head">⊹ THE CHRONICLES</div>
    <div class="chronicle-grid">
      <div class="chron">
        <span class="chron-n" data-target="48">0</span>
        <div class="chron-l">REPOSITORIES</div>
      </div>
      <div class="chron">
        <span class="chron-n" data-target="312">0</span>
        <div class="chron-l">CONTRIBUTIONS</div>
      </div>
      <div class="chron">
        <span class="chron-n" data-target="27">0</span>
        <div class="chron-l">STARS EARNED</div>
      </div>
    </div>

    <div class="voyage-bar">
      <div class="vb-top">
        <span class="vb-label">VOYAGE STREAK</span>
        <span class="vb-val">73 days ❄️</span>
      </div>
      <div class="bar-bg">
        <div class="bar-ice"></div>
      </div>
    </div>
  </div>

  <!-- NOW -->
  <div class="section">
    <div class="sec-head">⊹ CURRENT VOYAGE</div>
    <ul class="saga-list">
      <li class="saga-item"><span class="saga-key">MASTERING</span> WebGL · Three.js · Creative Dev</li>
      <li class="saga-item"><span class="saga-key">FORGING</span> Something cold and powerful</li>
      <li class="saga-item"><span class="saga-key">READING</span> Vinland Saga — all volumes</li>
      <li class="saga-item"><span class="saga-key">HEARING</span> Nordic folk · ambient cold</li>
      <li class="saga-item"><span class="saga-key">SEEKING</span> Build one thing that endures</li>
    </ul>
  </div>

  <div class="crack-line"></div>
  <div class="divider"><span class="div-sym">✦ ✦ ✦</span></div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-runes">ᚠ ᚢ ᚦ ᚨ ᚱ ᚲ ᛟ</div>
    <div class="footer-quote">
      "A man who has lived a good life has no fear of death.<br/>
      Let us not waste time — let us sail."
    </div>
    <div class="footer-sig">AND SO THE VOYAGE CONTINUES · PEACE IN EVERY COMMIT</div>
  </div>

</div>

<script>
  // Stars
  const starsEl = document.getElementById('stars');
  for (let i = 0; i < 120; i++) {
    const s = document.createElement('div');
    s.className = 'star';
    const sz = Math.random() * 1.8 + 0.4;
    s.style.cssText = `
      left:${Math.random()*100}%;
      top:${Math.random()*60}%;
      width:${sz}px; height:${sz}px;
      animation-duration:${Math.random()*4+2}s;
      animation-delay:${Math.random()*6}s;
    `;
    starsEl.appendChild(s);
  }

  // Snow
  const snowEl = document.getElementById('snow');
  const flakes = ['❄','❅','❆','·','*'];
  for (let i = 0; i < 35; i++) {
    const f = document.createElement('div');
    f.className = 'flake';
    f.textContent = flakes[Math.floor(Math.random()*flakes.length)];
    f.style.cssText = `
      left:${Math.random()*100}%;
      font-size:${Math.random()*10+6}px;
      animation-duration:${Math.random()*18+12}s;
      animation-delay:${Math.random()*20}s;
      opacity:${Math.random()*0.5+0.1};
    `;
    snowEl.appendChild(f);
  }

  // Typing
  const lines = [
    "Sailing beyond the known frontier.",
    "I craft interfaces that endure.",
    "Where the cold north meets clean code.",
    "Motion. Intention. Precision.",
    "Fear not the blank canvas.",
  ];
  let li = 0, ci = 0, del = false;
  const tel = document.getElementById('typing');

  function type() {
    const cur = lines[li];
    if (!del) {
      tel.textContent = cur.slice(0, ci++);
      if (ci > cur.length) { del = true; setTimeout(type, 2200); return; }
    } else {
      tel.textContent = cur.slice(0, ci--);
      if (ci < 0) { del = false; li = (li+1) % lines.length; }
    }
    setTimeout(type, del ? 32 : 60);
  }
  type();

  // Count-up
  document.querySelectorAll('.chron-n').forEach(el => {
    const target = +el.dataset.target;
    let cur = 0, step = target / 70;
    const t = setInterval(() => {
      cur = Math.min(cur + step, target);
      el.textContent = Math.floor(cur);
      if (cur >= target) clearInterval(t);
    }, 20);
  });

  // Scroll reveal
  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.08 });
  document.querySelectorAll('.section').forEach(el => obs.observe(el));
</script>
</body>
</html>
