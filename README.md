<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Vinland Saga — Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;900&family=Cinzel+Decorative:wght@400;700&family=IM+Fell+English:ital@0;1&display=swap" rel="stylesheet"/>
<style>
  :root {
    --gold: #c9a96e;
    --gold2: #e8c87a;
    --rust: #8B4513;
    --dark: #0a0705;
    --dark2: #12100a;
    --dark3: #1c1710;
    --stone: #2a2318;
    --fog: rgba(201,169,110,0.06);
    --text: #d4c4a0;
    --muted: #7a6a50;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--dark);
    color: var(--text);
    font-family: 'IM Fell English', serif;
    min-height: 100vh;
    overflow-x: hidden;
    cursor: default;
  }

  /* Parchment noise texture overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 200;
    opacity: 0.4;
  }

  /* Vignette */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background: radial-gradient(ellipse at center, transparent 40%, rgba(0,0,0,0.85) 100%);
    pointer-events: none;
    z-index: 1;
  }

  /* Floating particles */
  .particles {
    position: fixed;
    inset: 0;
    z-index: 0;
    overflow: hidden;
  }

  .particle {
    position: absolute;
    width: 2px;
    height: 2px;
    background: var(--gold);
    border-radius: 50%;
    opacity: 0;
    animation: drift linear infinite;
  }

  @keyframes drift {
    0% { transform: translateY(100vh) translateX(0); opacity: 0; }
    10% { opacity: 0.6; }
    90% { opacity: 0.3; }
    100% { transform: translateY(-10vh) translateX(30px); opacity: 0; }
  }

  /* Rune border top */
  .rune-header {
    position: relative;
    width: 100%;
    padding: 12px 0;
    text-align: center;
    border-bottom: 1px solid rgba(201,169,110,0.2);
    background: linear-gradient(180deg, rgba(201,169,110,0.05) 0%, transparent 100%);
    letter-spacing: 12px;
    font-size: 14px;
    color: rgba(201,169,110,0.35);
    animation: runeFlicker 6s ease-in-out infinite;
  }

  @keyframes runeFlicker {
    0%, 100% { opacity: 0.35; }
    50% { opacity: 0.6; }
    75% { opacity: 0.3; }
  }

  .container {
    position: relative;
    z-index: 2;
    max-width: 820px;
    margin: 0 auto;
    padding: 40px 24px 60px;
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding: 48px 0 40px;
    opacity: 0;
    animation: emergeUp 1.2s ease 0.3s forwards;
  }

  @keyframes emergeUp {
    from { opacity: 0; transform: translateY(32px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .avatar-scene {
    position: relative;
    display: inline-block;
    margin-bottom: 32px;
  }

  .avatar {
    width: 140px;
    height: 140px;
    border-radius: 50%;
    background: radial-gradient(circle at 40% 35%, #2a2318, #0a0705);
    border: 1px solid rgba(201,169,110,0.4);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 56px;
    box-shadow:
      0 0 0 6px rgba(201,169,110,0.06),
      0 0 40px rgba(201,169,110,0.15),
      0 20px 60px rgba(0,0,0,0.8);
    animation: breathe 4s ease-in-out infinite;
  }

  @keyframes breathe {
    0%, 100% { box-shadow: 0 0 0 6px rgba(201,169,110,0.06), 0 0 40px rgba(201,169,110,0.15), 0 20px 60px rgba(0,0,0,0.8); }
    50%       { box-shadow: 0 0 0 8px rgba(201,169,110,0.1),  0 0 60px rgba(201,169,110,0.25), 0 20px 60px rgba(0,0,0,0.8); }
  }

  /* Ornamental ring */
  .ring {
    position: absolute;
    inset: -14px;
    border-radius: 50%;
    border: 1px solid rgba(201,169,110,0.25);
    animation: slowSpin 20s linear infinite;
  }

  .ring::before, .ring::after {
    content: '✦';
    position: absolute;
    color: var(--gold);
    font-size: 10px;
    opacity: 0.7;
  }

  .ring::before { top: -6px; left: 50%; transform: translateX(-50%); }
  .ring::after  { bottom: -6px; left: 50%; transform: translateX(-50%); }

  .ring2 {
    position: absolute;
    inset: -24px;
    border-radius: 50%;
    border: 1px dashed rgba(201,169,110,0.1);
    animation: slowSpin 35s linear infinite reverse;
  }

  @keyframes slowSpin {
    from { transform: rotate(0deg); }
    to   { transform: rotate(360deg); }
  }

  .hero-name {
    font-family: 'Cinzel Decorative', serif;
    font-size: clamp(28px, 5vw, 44px);
    font-weight: 700;
    color: var(--gold2);
    letter-spacing: 6px;
    text-shadow: 0 0 40px rgba(201,169,110,0.4), 0 2px 4px rgba(0,0,0,0.8);
    margin-bottom: 10px;
  }

  .hero-title {
    font-family: 'Cinzel', serif;
    font-size: 11px;
    letter-spacing: 8px;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .hero-quote {
    font-style: italic;
    font-size: 15px;
    color: rgba(201,169,110,0.5);
    margin-bottom: 28px;
    line-height: 1.6;
  }

  /* Divider */
  .divider {
    display: flex;
    align-items: center;
    gap: 16px;
    margin: 32px 0;
    opacity: 0.4;
  }

  .divider::before, .divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
  }

  .divider-icon {
    color: var(--gold);
    font-size: 14px;
    letter-spacing: 6px;
  }

  /* Typing */
  .typing-wrap {
    height: 24px;
    margin-bottom: 28px;
  }

  .typing {
    font-family: 'Cinzel', serif;
    font-size: 13px;
    color: var(--gold);
    letter-spacing: 2px;
    border-right: 1px solid var(--gold);
    padding-right: 4px;
    animation: cursorBlink 0.8s step-end infinite;
  }

  @keyframes cursorBlink {
    0%, 100% { border-color: var(--gold); }
    50%       { border-color: transparent; }
  }

  /* Social badges */
  .social {
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .s-badge {
    padding: 7px 20px;
    border: 1px solid rgba(201,169,110,0.3);
    color: var(--muted);
    font-family: 'Cinzel', serif;
    font-size: 10px;
    letter-spacing: 3px;
    cursor: pointer;
    transition: all 0.4s;
    position: relative;
    background: rgba(201,169,110,0.02);
  }

  .s-badge:hover {
    border-color: var(--gold);
    color: var(--gold);
    background: rgba(201,169,110,0.07);
    box-shadow: 0 0 20px rgba(201,169,110,0.15);
    transform: translateY(-2px);
  }

  /* ── SECTIONS ── */
  .section {
    margin-bottom: 44px;
    opacity: 0;
    animation: emergeUp 0.9s ease forwards;
  }

  .section:nth-child(1) { animation-delay: 0.6s; }
  .section:nth-child(2) { animation-delay: 0.8s; }
  .section:nth-child(3) { animation-delay: 1.0s; }
  .section:nth-child(4) { animation-delay: 1.2s; }
  .section:nth-child(5) { animation-delay: 1.4s; }

  .sec-title {
    font-family: 'Cinzel', serif;
    font-size: 10px;
    letter-spacing: 6px;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 14px;
  }

  .sec-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, rgba(201,169,110,0.3), transparent);
  }

  /* About */
  .about-card {
    background: var(--fog);
    border: 1px solid rgba(201,169,110,0.1);
    border-left: 2px solid rgba(201,169,110,0.4);
    padding: 24px 28px;
    line-height: 2;
    font-size: 15px;
    color: #b0a080;
  }

  .about-card em { color: var(--gold); font-style: normal; }

  .about-meta {
    margin-top: 16px;
    display: flex;
    gap: 24px;
    flex-wrap: wrap;
    font-family: 'Cinzel', serif;
    font-size: 10px;
    letter-spacing: 2px;
    color: var(--muted);
  }

  /* Stack */
  .stack-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tech {
    padding: 8px 16px;
    border: 1px solid rgba(201,169,110,0.15);
    background: rgba(201,169,110,0.03);
    font-family: 'Cinzel', serif;
    font-size: 10px;
    letter-spacing: 2px;
    color: var(--muted);
    transition: all 0.35s;
    cursor: default;
  }

  .tech:hover {
    border-color: rgba(201,169,110,0.5);
    color: var(--gold);
    background: rgba(201,169,110,0.08);
    transform: translateY(-2px);
    box-shadow: 0 4px 20px rgba(201,169,110,0.1);
  }

  /* Stats */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
    margin-bottom: 16px;
  }

  .stat {
    border: 1px solid rgba(201,169,110,0.12);
    background: var(--fog);
    padding: 20px 16px;
    text-align: center;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }

  .stat::before {
    content: '';
    position: absolute;
    top: 0; left: -100%; right: 100%;
    height: 1px;
    background: var(--gold);
    transition: all 0.6s ease;
  }

  .stat:hover::before { left: 0; right: 0; }
  .stat:hover {
    border-color: rgba(201,169,110,0.3);
    box-shadow: 0 0 24px rgba(201,169,110,0.08);
  }

  .stat-n {
    font-family: 'Cinzel Decorative', serif;
    font-size: 30px;
    color: var(--gold);
    text-shadow: 0 0 20px rgba(201,169,110,0.4);
    display: block;
    line-height: 1;
    margin-bottom: 8px;
  }

  .stat-l {
    font-family: 'Cinzel', serif;
    font-size: 9px;
    letter-spacing: 3px;
    color: var(--muted);
  }

  /* Streak */
  .streak-wrap {
    border: 1px solid rgba(201,169,110,0.12);
    background: var(--fog);
    padding: 20px 24px;
  }

  .streak-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 14px;
  }

  .streak-label {
    font-family: 'Cinzel', serif;
    font-size: 9px;
    letter-spacing: 4px;
    color: var(--muted);
  }

  .streak-val {
    font-family: 'Cinzel Decorative', serif;
    font-size: 20px;
    color: var(--gold);
    text-shadow: 0 0 15px rgba(201,169,110,0.5);
  }

  .bar-track {
    height: 3px;
    background: rgba(255,255,255,0.04);
    position: relative;
    overflow: visible;
  }

  .bar-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--rust), var(--gold), var(--gold2));
    width: 0%;
    animation: growBar 2s ease 1.5s forwards;
    box-shadow: 0 0 12px rgba(201,169,110,0.5);
    position: relative;
  }

  .bar-fill::after {
    content: '';
    position: absolute;
    right: -1px; top: -3px;
    width: 9px; height: 9px;
    background: var(--gold2);
    border-radius: 50%;
    box-shadow: 0 0 10px var(--gold);
  }

  @keyframes growBar {
    to { width: 73%; }
  }

  /* Now */
  .now-list { list-style: none; }

  .now-item {
    display: flex;
    align-items: flex-start;
    gap: 20px;
    padding: 13px 0;
    border-bottom: 1px solid rgba(201,169,110,0.06);
    font-size: 14px;
    color: #8a7a5a;
    transition: all 0.3s;
  }

  .now-item:last-child { border-bottom: none; }
  .now-item:hover { color: var(--text); padding-left: 6px; }

  .now-key {
    font-family: 'Cinzel', serif;
    font-size: 9px;
    letter-spacing: 3px;
    color: var(--gold);
    min-width: 90px;
    padding-top: 2px;
    opacity: 0.8;
  }

  /* Footer */
  .footer {
    text-align: center;
    padding-top: 48px;
    opacity: 0;
    animation: emergeUp 0.9s ease 1.8s forwards;
  }

  .footer-rune {
    font-size: 18px;
    letter-spacing: 16px;
    color: rgba(201,169,110,0.2);
    margin-bottom: 16px;
    animation: runeFlicker 5s ease-in-out infinite;
  }

  .footer-quote {
    font-style: italic;
    font-size: 13px;
    color: var(--muted);
    line-height: 1.8;
  }

  .footer-sig {
    font-family: 'Cinzel', serif;
    font-size: 9px;
    letter-spacing: 5px;
    color: rgba(201,169,110,0.25);
    margin-top: 20px;
  }

  /* Scroll fade-in */
  .reveal {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }
</style>
</head>
<body>

<!-- Particles -->
<div class="particles" id="particles"></div>

<!-- Rune top bar -->
<div class="rune-header">ᚠ ᚢ ᚦ ᚨ ᚱ ᚲ ᚷ ᚹ ᚺ ᚾ ᛁ ᛃ ᛇ ᛈ ᛉ ᛊ ᛏ ᛒ ᛖ ᛗ ᛚ ᛜ ᛞ ᛟ</div>

<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="avatar-scene">
      <div class="ring2"></div>
      <div class="ring"></div>
      <div class="avatar">⚔️</div>
    </div>

    <div class="hero-name">YOUR NAME</div>
    <div class="hero-title">Frontend Developer · Craftsman of Interfaces</div>

    <div class="typing-wrap">
      <span class="typing" id="typing"></span>
    </div>

    <div class="hero-quote">
      "A true warrior needs no sword."
    </div>

    <div class="social">
      <span class="s-badge">⌘ PORTFOLIO</span>
      <span class="s-badge">◈ LINKEDIN</span>
      <span class="s-badge">✦ TWITTER</span>
    </div>
  </div>

  <div class="divider"><span class="divider-icon">✦ ✦ ✦</span></div>

  <!-- ABOUT -->
  <div class="section reveal">
    <div class="sec-title">✦ Of This Warrior</div>
    <div class="about-card">
      I am <em>YOUR NAME</em> — a Frontend Developer who believes that every interface
      should be felt, not just seen. I craft digital experiences at the intersection
      of <em>motion</em>, <em>typography</em>, and <em>interaction</em>.<br/><br/>
      Like a Norse explorer seeking new lands, I am always searching for
      the next frontier in creative development.
      <div class="about-meta">
        <span>🌍 IRAN</span>
        <span>⚔️ OPEN TO WORK</span>
        <span>☕ COFFEE-POWERED</span>
      </div>
    </div>
  </div>

  <!-- STACK -->
  <div class="section reveal">
    <div class="sec-title">✦ Weapons of Choice</div>
    <div class="stack-grid">
      <div class="tech">HTML5</div>
      <div class="tech">CSS3</div>
      <div class="tech">JAVASCRIPT</div>
      <div class="tech">TYPESCRIPT</div>
      <div class="tech">REACT</div>
      <div class="tech">NEXT.JS</div>
      <div class="tech">VUE</div>
      <div class="tech">TAILWIND</div>
      <div class="tech">GSAP</div>
      <div class="tech">FRAMER MOTION</div>
      <div class="tech">THREE.JS</div>
      <div class="tech">FIGMA</div>
    </div>
  </div>

  <!-- STATS -->
  <div class="section reveal">
    <div class="sec-title">✦ The Chronicles</div>
    <div class="stats-row">
      <div class="stat">
        <span class="stat-n" data-target="48">0</span>
        <div class="stat-l">REPOSITORIES</div>
      </div>
      <div class="stat">
        <span class="stat-n" data-target="312">0</span>
        <div class="stat-l">CONTRIBUTIONS</div>
      </div>
      <div class="stat">
        <span class="stat-n" data-target="27">0</span>
        <div class="stat-l">STARS EARNED</div>
      </div>
    </div>

    <div class="streak-wrap">
      <div class="streak-top">
        <span class="streak-label">CURRENT STREAK</span>
        <span class="streak-val">73 days 🔥</span>
      </div>
      <div class="bar-track">
        <div class="bar-fill"></div>
      </div>
    </div>
  </div>

  <!-- NOW -->
  <div class="section reveal">
    <div class="sec-title">✦ Current Chapter</div>
    <ul class="now-list">
      <li class="now-item"><span class="now-key">MASTERING</span> WebGL · Three.js · Creative Dev</li>
      <li class="now-item"><span class="now-key">FORGING</span> Something quiet but powerful</li>
      <li class="now-item"><span class="now-key">READING</span> Vinland Saga — every volume</li>
      <li class="now-item"><span class="now-key">LISTENING</span> Ambient · Folk · Forest sounds</li>
      <li class="now-item"><span class="now-key">SEEKING</span> Build one thing that lasts</li>
    </ul>
  </div>

  <div class="divider"><span class="divider-icon">✦ ✦ ✦</span></div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-rune">ᚠ ᚢ ᚦ ᚨ ᚱ ᚲ</div>
    <div class="footer-quote">
      "Real strength is not about having no weakness,<br/>
      but about not being stopped by it."
    </div>
    <div class="footer-sig">AND SO THE JOURNEY CONTINUES · 和 · PEACE IN EVERY COMMIT</div>
  </div>

</div>

<script>
  // Particles
  const pc = document.getElementById('particles');
  for (let i = 0; i < 28; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    p.style.cssText = `
      left: ${Math.random()*100}%;
      width: ${Math.random()*2+1}px;
      height: ${Math.random()*2+1}px;
      animation-duration: ${Math.random()*20+15}s;
      animation-delay: ${Math.random()*20}s;
      opacity: ${Math.random()*0.4};
    `;
    pc.appendChild(p);
  }

  // Typing
  const lines = [
    "Crafting interfaces with intention.",
    "Where design meets the frontier.",
    "Peace in code. Peace in design.",
    "A true warrior needs no sword.",
    "Building things that endure.",
  ];
  let li = 0, ci = 0, del = false;
  const tel = document.getElementById('typing');

  function type() {
    const cur = lines[li];
    if (!del) {
      tel.textContent = cur.slice(0, ci++);
      if (ci > cur.length) { del = true; setTimeout(type, 2000); return; }
    } else {
      tel.textContent = cur.slice(0, ci--);
      if (ci < 0) { del = false; li = (li+1) % lines.length; }
    }
    setTimeout(type, del ? 35 : 65);
  }
  type();

  // Count-up
  document.querySelectorAll('.stat-n').forEach(el => {
    const target = +el.dataset.target;
    let cur = 0;
    const step = target / 70;
    const t = setInterval(() => {
      cur = Math.min(cur + step, target);
      el.textContent = Math.floor(cur);
      if (cur >= target) clearInterval(t);
    }, 22);
  });

  // Scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>
