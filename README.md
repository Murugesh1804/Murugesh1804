<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Murugesh S — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Newsreader:ital,wght@0,400;0,500;0,600;1,400&family=DM+Sans:wght@300;400;500;600;700&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #f7f4f0;
    --surface: #ffffff;
    --surface2: #f2ede8;
    --border: #e8e0d6;
    --border2: #d6ccbf;
    --accent: #c96442;
    --accent2: #9b6b9e;
    --accent3: #2e7d5e;
    --text: #1a1714;
    --muted: #7a6f65;
    --glow: rgba(201, 100, 66, 0.1);
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed;
    width: 10px; height: 10px;
    background: var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.1s;
  }
  .cursor-trail {
    position: fixed;
    width: 28px; height: 28px;
    border: 1.5px solid var(--accent);
    border-radius: 50%;
    pointer-events: none;
    z-index: 9998;
    transition: all 0.15s ease;
    opacity: 0.35;
  }

  /* Subtle dot background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: radial-gradient(circle, rgba(201,100,66,0.08) 1px, transparent 1px);
    background-size: 28px 28px;
    pointer-events: none;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 60px 24px;
  }

  /* Terminal header */
  .terminal-header {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 12px 12px 0 0;
    padding: 11px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .dot { width: 12px; height: 12px; border-radius: 50%; }
  .dot.red { background: #ff5f57; }
  .dot.yellow { background: #febc2e; }
  .dot.green { background: #28c840; }
  .terminal-title { margin-left: 8px; color: var(--muted); font-size: 12px; font-family: 'DM Mono', monospace; }

  /* Hero section */
  .hero {
    background: var(--surface);
    border: 1px solid var(--border);
    border-top: none;
    padding: 48px;
    position: relative;
    overflow: hidden;
    border-radius: 0 0 12px 12px;
    margin-bottom: 24px;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 240px; height: 240px;
    background: radial-gradient(circle, rgba(201,100,66,0.1) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero::after {
    content: '';
    position: absolute;
    bottom: -40px; left: 40%;
    width: 180px; height: 180px;
    background: radial-gradient(circle, rgba(155,107,158,0.08) 0%, transparent 70%);
    pointer-events: none;
  }

  .greeting {
    color: var(--muted);
    font-size: 13px;
    font-family: 'DM Mono', monospace;
    letter-spacing: 0.08em;
    margin-bottom: 12px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.2s;
  }

  .name {
    font-family: 'Newsreader', Georgia, serif;
    font-size: clamp(2.2rem, 5vw, 3.8rem);
    font-weight: 600;
    font-style: italic;
    line-height: 1.05;
    margin-bottom: 16px;
    background: linear-gradient(135deg, #1a1714 30%, var(--accent) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.4s;
  }

  .role-line {
    color: var(--muted);
    font-size: 14px;
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.6s;
  }
  .role-line .highlight {
    color: var(--accent3);
    font-weight: 500;
  }

  /* Typing animation */
  .typing-wrap {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 9px 16px;
    margin-bottom: 36px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.8s;
    font-family: 'DM Mono', monospace;
  }
  .typing-prompt { color: var(--accent); font-size: 13px; }
  .typing-text { color: var(--text); font-size: 13px; min-width: 200px; }
  .cursor-blink {
    display: inline-block;
    width: 2px; height: 14px;
    background: var(--accent);
    animation: blink 1s step-end infinite;
    vertical-align: middle;
  }

  .badge-row {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 36px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 1s;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 6px 14px;
    font-size: 12px;
    color: var(--text);
    text-decoration: none;
    transition: all 0.2s;
    position: relative;
    overflow: hidden;
  }
  .badge::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    opacity: 0;
    transition: opacity 0.2s;
  }
  .badge:hover::before { opacity: 0.07; }
  .badge:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(201,100,66,0.12);
  }
  .badge span { position: relative; z-index: 1; }
  .badge .dot-status {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent3);
    animation: pulse 2s ease infinite;
    position: relative; z-index: 1;
  }

  /* Stats bar */
  .stats-bar {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 8px;
    overflow: hidden;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 1.1s;
  }
  .stat {
    background: var(--surface2);
    padding: 16px 20px;
    text-align: center;
    transition: background 0.2s;
  }
  .stat:hover { background: #1c2128; }
  .stat-num {
    font-family: 'Newsreader', serif;
    font-size: 1.7rem;
    font-weight: 600;
    color: var(--accent);
    display: block;
  }
  .stat-label { color: var(--muted); font-size: 11px; text-transform: uppercase; letter-spacing: 0.1em; font-weight: 500; }

  /* Info cards */
  .grid-2 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 24px;
  }

  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }
  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    transform: scaleX(0);
    transition: transform 0.3s;
    transform-origin: left;
  }
  .card:hover::before { transform: scaleX(1); }
  .card:hover {
    border-color: rgba(201,100,66,0.35);
    transform: translateY(-4px);
    box-shadow: 0 12px 40px rgba(201,100,66,0.08);
  }

  .card-icon { font-size: 1.5rem; margin-bottom: 12px; display: block; }
  .card-title {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.12em;
    margin-bottom: 8px;
  }
  .card-content { font-size: 14px; color: var(--text); line-height: 1.65; }
  .card-content a {
    color: var(--accent);
    text-decoration: none;
    border-bottom: 1px solid rgba(201,100,66,0.3);
    transition: border-color 0.2s;
  }
  .card-content a:hover { border-color: var(--accent); }

  /* Skills section */
  .section-title {
    font-family: 'DM Sans', sans-serif;
    font-size: 0.72rem;
    font-weight: 700;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.15em;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .skills-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 24px;
  }

  .skill-tag {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 8px 14px;
    font-size: 12px;
    transition: all 0.2s;
    cursor: default;
    position: relative;
    overflow: hidden;
  }
  .skill-tag:hover {
    border-color: var(--accent);
    background: rgba(201,100,66,0.05);
    transform: scale(1.05);
  }
  .skill-tag img { width: 16px; height: 16px; object-fit: contain; }

  /* Activity graph */
  .contrib-section {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 28px;
    margin-bottom: 24px;
  }

  .contrib-grid {
    display: grid;
    grid-template-columns: repeat(52, 1fr);
    gap: 3px;
    margin-top: 16px;
  }
  .contrib-cell {
    aspect-ratio: 1;
    border-radius: 2px;
    background: var(--surface2);
    transition: transform 0.1s;
    cursor: pointer;
  }
  .contrib-cell:hover { transform: scale(1.5); z-index: 1; position: relative; }
  .contrib-cell.l1 { background: rgba(201,100,66,0.15); }
  .contrib-cell.l2 { background: rgba(201,100,66,0.35); }
  .contrib-cell.l3 { background: rgba(201,100,66,0.6); }
  .contrib-cell.l4 { background: rgba(201,100,66,0.88); }

  /* Connect section */
  .connect-row {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    margin-bottom: 24px;
  }

  .connect-btn {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 12px 22px;
    border-radius: 8px;
    font-family: 'DM Sans', sans-serif;
    font-size: 14px;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.25s;
    border: 1px solid;
    cursor: pointer;
  }
  .connect-btn.primary {
    background: var(--accent);
    color: #fff;
    border-color: var(--accent);
  }
  .connect-btn.primary:hover {
    background: transparent;
    color: var(--accent);
    box-shadow: 0 0 20px rgba(201,100,66,0.2);
  }
  .connect-btn.outline {
    background: transparent;
    color: var(--text);
    border-color: var(--border);
  }
  .connect-btn.outline:hover {
    border-color: var(--accent);
    color: var(--accent);
    background: rgba(201,100,66,0.05);
  }

  /* Currently learning banner */
  .learning-banner {
    background: linear-gradient(135deg, rgba(46,125,94,0.07), rgba(201,100,66,0.04));
    border: 1px solid rgba(46,125,94,0.25);
    border-radius: 10px;
    padding: 16px 20px;
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 24px;
    font-size: 14px;
  }
  .learning-icon { font-size: 1.4rem; }
  .learning-text { flex: 1; color: var(--text); }
  .learning-text strong { color: var(--accent3); display: block; font-size: 11px; text-transform: uppercase; letter-spacing: 0.1em; margin-bottom: 4px; font-weight: 700; }
  .progress-bar {
    height: 4px;
    background: var(--border);
    border-radius: 2px;
    margin-top: 8px;
    overflow: hidden;
  }
  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--accent3), var(--accent));
    border-radius: 2px;
    width: 0%;
    transition: width 1.5s ease 1.5s;
  }

  /* Footer */
  .footer {
    text-align: center;
    color: var(--muted);
    font-size: 11px;
    padding-top: 24px;
    border-top: 1px solid var(--border);
    letter-spacing: 0.05em;
  }

  /* Animations */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; box-shadow: 0 0 0 0 rgba(16,185,129,0.4); }
    50% { opacity: 0.8; box-shadow: 0 0 0 4px rgba(16,185,129,0); }
  }
  @keyframes scanline {
    0% { transform: translateY(-100%); }
    100% { transform: translateY(100vh); }
  }

  .card, .contrib-section { opacity: 0; animation: fadeUp 0.6s ease forwards; }
  .card:nth-child(1) { animation-delay: 1.3s; }
  .card:nth-child(2) { animation-delay: 1.4s; }
  .card:nth-child(3) { animation-delay: 1.5s; }
  .card:nth-child(4) { animation-delay: 1.6s; }

  @media (max-width: 640px) {
    .grid-2 { grid-template-columns: 1fr; }
    .stats-bar { grid-template-columns: repeat(3, 1fr); }
    .hero { padding: 28px 20px; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-trail" id="cursorTrail"></div>

<div class="container">

  <!-- Terminal window header -->
  <div class="terminal-header">
    <div class="dot red"></div>
    <div class="dot yellow"></div>
    <div class="dot green"></div>
    <span class="terminal-title">murugesh-s — README.md</span>
  </div>

  <!-- Hero -->
  <div class="hero">
    <p class="greeting">// Hello, World! 👋</p>
    <h1 class="name">Murugesh S</h1>
    <p class="role-line">Backend Developer @ <span class="highlight">Techobite</span> · India 🇮🇳</p>

    <div class="typing-wrap">
      <span class="typing-prompt">~$</span>
      <span class="typing-text" id="typingText"></span>
      <span class="cursor-blink"></span>
    </div>

    <div class="badge-row">
      <span class="badge"><span class="dot-status"></span><span>Open to opportunities</span></span>
      <span class="badge"><span>📍</span><span>India</span></span>
      <span class="badge"><span>🏢</span><span>Techobite</span></span>
      <span class="badge"><span>🌱</span><span>Learning Next.js</span></span>
    </div>

    <div class="stats-bar">
      <div class="stat">
        <span class="stat-num" data-target="3">0</span>
        <span class="stat-label">Years Coding</span>
      </div>
      <div class="stat">
        <span class="stat-num" data-target="15">0</span>
        <span class="stat-label">Projects Built</span>
      </div>
      <div class="stat">
        <span class="stat-num" data-target="8">0</span>
        <span class="stat-label">Tech Stack</span>
      </div>
    </div>
  </div>

  <!-- Currently Learning -->
  <div class="learning-banner" style="opacity:0;animation:fadeUp 0.6s ease forwards 1.2s">
    <div class="learning-icon">⚡</div>
    <div class="learning-text">
      <strong>Currently Leveling Up</strong>
      Next.js — Building full-stack React applications with server-side rendering
      <div class="progress-bar"><div class="progress-fill" id="progressFill"></div></div>
    </div>
  </div>

  <!-- Info Cards -->
  <div class="grid-2">
    <div class="card">
      <span class="card-icon">👨‍💻</span>
      <div class="card-title">Portfolio</div>
      <div class="card-content">All projects live at<br><a href="https://murugesh.vercel.app" target="_blank">murugesh.vercel.app ↗</a></div>
    </div>
    <div class="card">
      <span class="card-icon">📄</span>
      <div class="card-title">Resume</div>
      <div class="card-content">View my full experience &amp; skills<br><a href="https://drive.google.com/file/d/1ymabeKbf-XunmoYJznlwBqiT_AvAZToa/view?usp=drive_link" target="_blank">Download Resume ↗</a></div>
    </div>
    <div class="card">
      <span class="card-icon">💬</span>
      <div class="card-title">Ask Me About</div>
      <div class="card-content"><code style="color:var(--accent);background:rgba(201,100,66,0.08);padding:1px 5px;border-radius:4px;font-family:'DM Mono',monospace;font-size:12px">C++</code> · <code style="color:var(--accent);background:rgba(201,100,66,0.08);padding:1px 5px;border-radius:4px;font-family:'DM Mono',monospace;font-size:12px">Python</code> · <code style="color:var(--accent);background:rgba(201,100,66,0.08);padding:1px 5px;border-radius:4px;font-family:'DM Mono',monospace;font-size:12px">JavaScript</code><br><span style="color:var(--muted);font-size:12px">Happy to chat, collaborate, or mentor</span></div>
    </div>
    <div class="card">
      <span class="card-icon">📫</span>
      <div class="card-title">Contact</div>
      <div class="card-content"><a href="mailto:dhanamurugesh1804@gmail.com">dhanamurugesh1804@gmail.com ↗</a></div>
    </div>
  </div>

  <!-- Skills -->
  <div style="opacity:0;animation:fadeUp 0.6s ease forwards 1.7s">
    <div class="section-title">Languages &amp; Tools</div>
    <div class="skills-grid">
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg" alt="C++">C++</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python">Python</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt="JS">JavaScript</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" alt="TS">TypeScript</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="React">React</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nextjs/nextjs-original.svg" alt="Next.js" style="filter:none;opacity:0.7">Next.js</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" alt="Node">Node.js</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg" alt="PostgreSQL">PostgreSQL</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg" alt="MongoDB">MongoDB</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git">Git</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" alt="Docker">Docker</div>
      <div class="skill-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" alt="Linux">Linux</div>
    </div>
  </div>

  <!-- Contribution graph -->
  <div class="contrib-section" style="animation-delay:1.9s">
    <div class="section-title">Contribution Activity</div>
    <div class="contrib-grid" id="contribGrid"></div>
    <p style="color:var(--muted);font-size:11px;margin-top:12px;text-align:right">Less <span id="legend"></span> More</p>
  </div>

  <!-- Connect -->
  <div style="opacity:0;animation:fadeUp 0.6s ease forwards 2.1s">
    <div class="section-title">Connect With Me</div>
    <div class="connect-row">
      <a href="mailto:dhanamurugesh1804@gmail.com" class="connect-btn primary">✉ Email Me</a>
      <a href="https://www.linkedin.com/in/murugesh-s/" target="_blank" class="connect-btn outline">in LinkedIn</a>
      <a href="https://murugesh.vercel.app" target="_blank" class="connect-btn outline">🌐 Portfolio</a>
      <a href="https://drive.google.com/file/d/1ymabeKbf-XunmoYJznlwBqiT_AvAZToa/view?usp=drive_link" target="_blank" class="connect-btn outline">📄 Resume</a>
    </div>
  </div>

  <div class="footer" style="opacity:0;animation:fadeUp 0.6s ease forwards 2.3s">
    <p>⚡ Crafted with passion · Murugesh S · Backend Developer · India</p>
  </div>

</div>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const trail = document.getElementById('cursorTrail');
  document.addEventListener('mousemove', e => {
    cursor.style.left = e.clientX - 6 + 'px';
    cursor.style.top = e.clientY - 6 + 'px';
    setTimeout(() => {
      trail.style.left = e.clientX - 16 + 'px';
      trail.style.top = e.clientY - 16 + 'px';
    }, 60);
  });
  document.querySelectorAll('a, button, .skill-tag, .badge, .connect-btn').forEach(el => {
    el.addEventListener('mouseenter', () => cursor.style.transform = 'scale(2)');
    el.addEventListener('mouseleave', () => cursor.style.transform = 'scale(1)');
  });

  // Typing effect
  const phrases = [
    'echo "Hello, World!"',
    'git commit -m "Build cool stuff"',
    'python solve_problems.py',
    'npm run dev  # Next.js journey 🚀',
    'SELECT * FROM passion WHERE skill="backend"'
  ];
  let phraseIdx = 0, charIdx = 0, deleting = false;
  const el = document.getElementById('typingText');
  function type() {
    const current = phrases[phraseIdx];
    if (!deleting) {
      el.textContent = current.slice(0, ++charIdx);
      if (charIdx === current.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      el.textContent = current.slice(0, --charIdx);
      if (charIdx === 0) { deleting = false; phraseIdx = (phraseIdx + 1) % phrases.length; }
    }
    setTimeout(type, deleting ? 40 : 80);
  }
  setTimeout(type, 1200);

  // Count up stats
  document.querySelectorAll('.stat-num').forEach(el => {
    const target = +el.dataset.target;
    let count = 0;
    const step = () => {
      count = Math.min(count + 1, target);
      el.textContent = count + (target > 10 ? '+' : '+');
      if (count < target) setTimeout(step, 80);
    };
    setTimeout(step, 1400);
  });

  // Contribution graph
  const grid = document.getElementById('contribGrid');
  const levels = ['', 'l1', 'l2', 'l3', 'l4'];
  for (let i = 0; i < 52 * 7; i++) {
    const cell = document.createElement('div');
    cell.className = 'contrib-cell';
    const r = Math.random();
    if (r > 0.65) cell.classList.add(levels[Math.floor(r * 4) + 1] || 'l1');
    grid.appendChild(cell);
  }
  // Animate cells in
  const cells = grid.querySelectorAll('.contrib-cell');
  cells.forEach((cell, i) => {
    setTimeout(() => cell.style.opacity = '1', 2000 + i * 2);
  });

  // Legend
  const legendEl = document.getElementById('legend');
  [0,'l1','l2','l3','l4'].forEach(l => {
    const s = document.createElement('span');
    s.style.cssText = `display:inline-block;width:10px;height:10px;border-radius:2px;margin:0 2px;vertical-align:middle;`;
    s.style.background = l === 0 ? '#e8e0d6' : l === 'l1' ? 'rgba(201,100,66,0.15)' : l === 'l2' ? 'rgba(201,100,66,0.35)' : l === 'l3' ? 'rgba(201,100,66,0.6)' : 'rgba(201,100,66,0.88)';
    legendEl.appendChild(s);
  });

  // Progress bar
  setTimeout(() => {
    document.getElementById('progressFill').style.width = '65%';
  }, 500);
</script>
</body>
</html>
