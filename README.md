<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Rohit Maurya — GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Fira+Code:wght@300;400;500&family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --cyan: #00fff0;
    --green: #00ff88;
    --purple: #b16cff;
    --orange: #ff9a3c;
    --red: #ff4d6d;
    --dark: #060a12;
    --dark2: #0d1321;
    --dark3: #111827;
    --glass: rgba(255,255,255,0.04);
    --glass-border: rgba(255,255,255,0.08);
    --text: #e2e8f0;
    --muted: #64748b;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--dark);
    color: var(--text);
    font-family: 'Space Grotesk', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  /* ─── PARTICLE CANVAS ─── */
  #particles { position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none; }

  /* ─── GRID BACKGROUND ─── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,255,240,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,255,240,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    z-index: 0;
    pointer-events: none;
  }

  /* ─── AMBIENT GLOWS ─── */
  .glow-orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(100px);
    pointer-events: none;
    z-index: 0;
    animation: drift 8s ease-in-out infinite alternate;
  }
  .glow-orb.g1 { width: 500px; height: 500px; background: rgba(0,255,240,0.06); top: -100px; left: -100px; animation-delay: 0s; }
  .glow-orb.g2 { width: 400px; height: 400px; background: rgba(177,108,255,0.06); bottom: 100px; right: -100px; animation-delay: -3s; }
  .glow-orb.g3 { width: 300px; height: 300px; background: rgba(0,255,136,0.04); top: 50%; left: 50%; transform: translate(-50%,-50%); animation-delay: -6s; }

  @keyframes drift {
    from { transform: translate(0,0) scale(1); }
    to { transform: translate(30px, -30px) scale(1.1); }
  }

  /* ─── LAYOUT ─── */
  .wrapper { position: relative; z-index: 1; max-width: 900px; margin: 0 auto; padding: 0 24px 80px; }

  /* ─── HERO ─── */
  .hero {
    text-align: center;
    padding: 80px 0 60px;
    position: relative;
  }

  .hero-eyebrow {
    font-family: 'Fira Code', monospace;
    font-size: 13px;
    color: var(--cyan);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 20px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.3s forwards;
  }

  .hero-name {
    font-family: 'Orbitron', monospace;
    font-size: clamp(42px, 7vw, 80px);
    font-weight: 900;
    line-height: 1;
    background: linear-gradient(135deg, #ffffff 0%, var(--cyan) 40%, var(--purple) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 8px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.5s forwards;
    position: relative;
  }

  .hero-name::after {
    content: '';
    display: block;
    width: 120px;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--cyan), transparent);
    margin: 20px auto 0;
    animation: pulseWidth 3s ease-in-out infinite;
  }

  @keyframes pulseWidth {
    0%, 100% { width: 120px; opacity: 0.5; }
    50% { width: 300px; opacity: 1; }
  }

  .hero-title {
    font-size: 16px;
    color: var(--muted);
    margin-top: 24px;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.7s forwards;
  }

  .hero-title span { color: var(--cyan); font-weight: 600; }

  /* ─── TYPING TERMINAL ─── */
  .terminal {
    background: rgba(0,0,0,0.6);
    border: 1px solid var(--glass-border);
    border-top: 2px solid var(--cyan);
    border-radius: 12px;
    padding: 20px 24px;
    margin: 40px 0;
    font-family: 'Fira Code', monospace;
    font-size: 14px;
    position: relative;
    overflow: hidden;
    opacity: 0;
    animation: fadeUp 0.8s ease 0.9s forwards;
    backdrop-filter: blur(10px);
  }

  .terminal::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--cyan), transparent);
    animation: scanLine 3s linear infinite;
  }

  @keyframes scanLine {
    0% { opacity: 0; transform: translateX(-100%); }
    50% { opacity: 1; }
    100% { opacity: 0; transform: translateX(100%); }
  }

  .terminal-dots {
    display: flex;
    gap: 8px;
    margin-bottom: 16px;
  }
  .terminal-dots span {
    width: 12px; height: 12px; border-radius: 50%;
    display: inline-block;
  }
  .terminal-dots span:nth-child(1) { background: #ff5f57; }
  .terminal-dots span:nth-child(2) { background: #ffbd2e; }
  .terminal-dots span:nth-child(3) { background: #28c940; }

  .terminal-line { color: var(--muted); margin-bottom: 6px; line-height: 1.7; }
  .terminal-line .prompt { color: var(--cyan); }
  .terminal-line .cmd { color: var(--green); }
  .terminal-line .value { color: #fff; }
  .terminal-line .comment { color: #444; }

  .cursor {
    display: inline-block;
    width: 8px;
    height: 14px;
    background: var(--cyan);
    margin-left: 2px;
    vertical-align: middle;
    animation: blink 1s step-end infinite;
  }
  @keyframes blink { 0%,100% { opacity: 1; } 50% { opacity: 0; } }

  /* ─── BADGES ─── */
  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    justify-content: center;
    margin: 32px 0;
    opacity: 0;
    animation: fadeUp 0.8s ease 1.1s forwards;
  }

  .badge {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 50px;
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 0.5px;
    border: 1px solid transparent;
    cursor: pointer;
    transition: all 0.3s ease;
    text-decoration: none;
    color: inherit;
  }

  .badge.linkedin {
    background: rgba(10,102,194,0.15);
    border-color: rgba(10,102,194,0.4);
    color: #4da6ff;
  }
  .badge.gmail {
    background: rgba(234,67,53,0.15);
    border-color: rgba(234,67,53,0.4);
    color: #ff7b6b;
  }
  .badge.github {
    background: rgba(255,255,255,0.05);
    border-color: rgba(255,255,255,0.15);
    color: #cbd5e1;
  }

  .badge:hover { transform: translateY(-3px) scale(1.03); filter: brightness(1.3); }
  .badge svg { width: 18px; height: 18px; fill: currentColor; }

  /* ─── SECTION HEADER ─── */
  .section {
    margin: 60px 0 32px;
  }

  .section-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 28px;
  }

  .section-tag {
    font-family: 'Fira Code', monospace;
    font-size: 13px;
    color: var(--cyan);
    background: rgba(0,255,240,0.08);
    border: 1px solid rgba(0,255,240,0.2);
    padding: 4px 12px;
    border-radius: 4px;
  }

  .section-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, rgba(0,255,240,0.3), transparent);
  }

  /* ─── ABOUT ─── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  .about-card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 14px;
    padding: 20px;
    position: relative;
    overflow: hidden;
    transition: all 0.4s ease;
    cursor: default;
  }

  .about-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(0,255,240,0.05), transparent);
    opacity: 0;
    transition: opacity 0.4s;
  }

  .about-card:hover::before { opacity: 1; }
  .about-card:hover {
    border-color: rgba(0,255,240,0.3);
    transform: translateY(-4px);
    box-shadow: 0 20px 60px rgba(0,255,240,0.05);
  }

  .about-card .icon { font-size: 28px; margin-bottom: 12px; display: block; }
  .about-card h4 { font-size: 13px; color: var(--cyan); font-family: 'Fira Code', monospace; margin-bottom: 6px; }
  .about-card p { font-size: 14px; color: #94a3b8; line-height: 1.6; }

  /* ─── TECH STACK ─── */
  .stack-group { margin-bottom: 24px; }
  .stack-label {
    font-family: 'Fira Code', monospace;
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  .tech-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .pill {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 7px 14px;
    border-radius: 8px;
    font-size: 13px;
    font-weight: 500;
    border: 1px solid;
    transition: all 0.3s ease;
    cursor: default;
    position: relative;
    overflow: hidden;
  }

  .pill::after {
    content: '';
    position: absolute;
    inset: 0;
    background: currentColor;
    opacity: 0;
    transition: opacity 0.3s;
  }

  .pill:hover { transform: translateY(-2px) scale(1.05); }
  .pill:hover::after { opacity: 0.08; }

  .pill.cyan  { color: var(--cyan);   background: rgba(0,255,240,0.07);   border-color: rgba(0,255,240,0.2); }
  .pill.green { color: var(--green);  background: rgba(0,255,136,0.07);   border-color: rgba(0,255,136,0.2); }
  .pill.purple{ color: var(--purple); background: rgba(177,108,255,0.07); border-color: rgba(177,108,255,0.2); }
  .pill.orange{ color: var(--orange); background: rgba(255,154,60,0.07);  border-color: rgba(255,154,60,0.2); }
  .pill.red   { color: var(--red);    background: rgba(255,77,109,0.07);  border-color: rgba(255,77,109,0.2); }

  /* ─── PROJECTS ─── */
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  .project-card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 16px;
    padding: 24px;
    position: relative;
    overflow: hidden;
    transition: all 0.4s cubic-bezier(0.23,1,0.32,1);
    cursor: default;
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: -60px; left: -60px;
    width: 180px; height: 180px;
    border-radius: 50%;
    filter: blur(40px);
    opacity: 0;
    transition: opacity 0.5s;
  }

  .project-card.pc1::before { background: var(--cyan); }
  .project-card.pc2::before { background: var(--green); }
  .project-card.pc3::before { background: var(--purple); }
  .project-card.pc4::before { background: var(--orange); }
  .project-card.pc5::before { background: var(--red); }
  .project-card.pc6::before { background: #60a5fa; }

  .project-card:hover::before { opacity: 0.07; }
  .project-card:hover {
    transform: translateY(-6px);
    border-color: rgba(255,255,255,0.15);
    box-shadow: 0 30px 80px rgba(0,0,0,0.5);
  }

  .project-dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    display: inline-block;
    margin-right: 8px;
    box-shadow: 0 0 8px currentColor;
    animation: pulse-dot 2s ease-in-out infinite;
  }
  @keyframes pulse-dot {
    0%,100% { transform: scale(1); opacity: 1; }
    50% { transform: scale(1.4); opacity: 0.7; }
  }

  .project-card h3 {
    font-size: 15px;
    font-weight: 600;
    color: #f1f5f9;
    margin-bottom: 6px;
    display: flex;
    align-items: center;
  }

  .project-subtitle {
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    color: var(--muted);
    margin-bottom: 12px;
    letter-spacing: 0.5px;
  }

  .project-card p {
    font-size: 13px;
    color: #64748b;
    line-height: 1.7;
    margin-bottom: 16px;
  }

  .project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .project-tag {
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    padding: 3px 10px;
    border-radius: 4px;
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.08);
    color: #94a3b8;
  }

  /* ─── STATS ─── */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    margin-bottom: 16px;
  }

  .stat-card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 14px;
    padding: 20px;
    text-align: center;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
  }

  .stat-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--cyan), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .stat-card:hover { transform: translateY(-4px); border-color: rgba(0,255,240,0.25); }
  .stat-card:hover::after { opacity: 1; }

  .stat-number {
    font-family: 'Orbitron', monospace;
    font-size: 32px;
    font-weight: 700;
    background: linear-gradient(135deg, var(--cyan), var(--purple));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    display: block;
    margin-bottom: 6px;
  }

  .stat-label {
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 1px;
    text-transform: uppercase;
    font-family: 'Fira Code', monospace;
  }

  /* ─── GOAL TERMINAL ─── */
  .code-block {
    background: #0a0f1a;
    border: 1px solid rgba(0,255,240,0.15);
    border-radius: 12px;
    padding: 24px;
    font-family: 'Fira Code', monospace;
    font-size: 13px;
    line-height: 2;
    position: relative;
    overflow: hidden;
  }

  .code-block::before {
    content: 'goals.py';
    position: absolute;
    top: 12px; right: 16px;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 1px;
  }

  .kw { color: #c084fc; }
  .str { color: #86efac; }
  .var { color: #7dd3fc; }
  .comment { color: #374151; }
  .bracket { color: #94a3b8; }
  .key { color: var(--orange); }

  /* ─── FOOTER ─── */
  .footer {
    text-align: center;
    padding: 60px 0 20px;
    border-top: 1px solid var(--glass-border);
    margin-top: 60px;
  }

  .footer-text {
    font-family: 'Fira Code', monospace;
    font-size: 13px;
    color: var(--muted);
    margin-bottom: 16px;
  }

  .footer-glow {
    font-family: 'Orbitron', monospace;
    font-size: 15px;
    color: var(--cyan);
    letter-spacing: 3px;
    animation: textGlow 3s ease-in-out infinite;
  }

  @keyframes textGlow {
    0%,100% { text-shadow: 0 0 10px rgba(0,255,240,0.3); }
    50% { text-shadow: 0 0 30px rgba(0,255,240,0.8), 0 0 60px rgba(0,255,240,0.3); }
  }

  /* ─── ANIMATED REVEAL ─── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.7s cubic-bezier(0.23,1,0.32,1);
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ─── SCROLLBAR ─── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--dark); }
  ::-webkit-scrollbar-thumb { background: rgba(0,255,240,0.3); border-radius: 3px; }

  @media (max-width: 640px) {
    .about-grid, .projects-grid { grid-template-columns: 1fr; }
    .stats-row { grid-template-columns: 1fr 1fr; }
  }
</style>
</head>
<body>

<canvas id="particles"></canvas>
<div class="glow-orb g1"></div>
<div class="glow-orb g2"></div>
<div class="glow-orb g3"></div>

<div class="wrapper">

  <!-- ─── HERO ─── -->
  <div class="hero">
    <p class="hero-eyebrow">// initializing profile...</p>
    <h1 class="hero-name">ROHIT MAURYA</h1>
    <p class="hero-title">
      <span>AI Engineer</span> &nbsp;/&nbsp; <span>Data Engineer</span> &nbsp;/&nbsp; <span>Agentic AI Developer</span>
    </p>

    <div class="badges">
      <a class="badge linkedin" href="https://linkedin.com/in/rohitmaurya26" target="_blank">
        <svg viewBox="0 0 24 24"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        LinkedIn
      </a>
      <a class="badge gmail" href="mailto:rohitmaurya441865@gmail.com">
        <svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
        Gmail
      </a>
      <a class="badge github" href="https://github.com/HelloRohit26" target="_blank">
        <svg viewBox="0 0 24 24"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0 1 12 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0 0 22 12.017C22 6.484 17.522 2 12 2z"/></svg>
        GitHub
      </a>
    </div>

    <!-- Terminal -->
    <div class="terminal">
      <div class="terminal-dots"><span></span><span></span><span></span></div>
      <div class="terminal-line"><span class="prompt">rohit@nexus:~$ </span><span class="cmd">cat ./identity.json</span></div>
      <div class="terminal-line">&nbsp;</div>
      <div class="terminal-line"><span style="color:#475569">{</span></div>
      <div class="terminal-line">&nbsp;&nbsp;<span style="color:#f97316">"role"</span><span style="color:#475569">:</span> <span style="color:#86efac">"AI + Data Engineer"</span><span style="color:#475569">,</span></div>
      <div class="terminal-line">&nbsp;&nbsp;<span style="color:#f97316">"base"</span><span style="color:#475569">:</span> <span style="color:#86efac">"Varanasi, India 🇮🇳"</span><span style="color:#475569">,</span></div>
      <div class="terminal-line">&nbsp;&nbsp;<span style="color:#f97316">"focus"</span><span style="color:#475569">:</span> <span style="color:#86efac">["Agentic AI", "RAG", "MLOps", "Multi-Agent Systems"]</span><span style="color:#475569">,</span></div>
      <div class="terminal-line">&nbsp;&nbsp;<span style="color:#f97316">"status"</span><span style="color:#475569">:</span> <span style="color:#4ade80">"OPEN_TO_WORK"</span> <span style="color:#374151">// actively seeking opportunities</span></div>
      <div class="terminal-line"><span style="color:#475569">}</span></div>
      <div class="terminal-line">&nbsp;</div>
      <div class="terminal-line"><span class="prompt">rohit@nexus:~$ </span><span class="cursor"></span></div>
    </div>
  </div>

  <!-- ─── ABOUT ─── -->
  <div class="section reveal">
    <div class="section-header">
      <span class="section-tag">// about</span>
      <div class="section-line"></div>
    </div>
    <div class="about-grid">
      <div class="about-card">
        <span class="icon">🤖</span>
        <h4>> currently_building</h4>
        <p>Multi-Agent Systems with MCP + LangChain — autonomous agents that reason, plan, and execute complex workflows without human intervention.</p>
      </div>
      <div class="about-card">
        <span class="icon">🧠</span>
        <h4>> currently_learning</h4>
        <p>Advanced LLM Orchestration — prompt chaining, tool use, memory management, and production-grade RAG architectures at scale.</p>
      </div>
      <div class="about-card">
        <span class="icon">🏗️</span>
        <h4>> engineering_focus</h4>
        <p>Real-time data pipelines (Kafka + Airflow), cloud-native MLOps (Docker + AWS), and intelligent API backends with FastAPI.</p>
      </div>
      <div class="about-card">
        <span class="icon">📡</span>
        <h4>> open_to_collab</h4>
        <p>Open Source AI projects, agentic system design, and anything at the intersection of Data Engineering + Large Language Models.</p>
      </div>
    </div>
  </div>

  <!-- ─── TECH STACK ─── -->
  <div class="section reveal">
    <div class="section-header">
      <span class="section-tag">// tech_stack</span>
      <div class="section-line"></div>
    </div>

    <div class="stack-group">
      <div class="stack-label">── Languages</div>
      <div class="tech-pills">
        <span class="pill cyan">🐍 Python</span>
        <span class="pill cyan">🗄️ SQL</span>
        <span class="pill cyan">🌐 HTML5</span>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-label">── AI / ML / LLM</div>
      <div class="tech-pills">
        <span class="pill green">🦜 LangChain</span>
        <span class="pill green">✨ Gemini API</span>
        <span class="pill green">🤗 HuggingFace</span>
        <span class="pill green">⚡ XGBoost</span>
        <span class="pill green">🔬 Scikit-Learn</span>
        <span class="pill green">📊 MLflow</span>
        <span class="pill green">🔗 MCP Protocol</span>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-label">── Data Engineering</div>
      <div class="tech-pills">
        <span class="pill purple">📨 Apache Kafka</span>
        <span class="pill purple">🌀 Airflow</span>
        <span class="pill purple">⚡ Apache Spark</span>
        <span class="pill purple">❄️ Snowflake</span>
        <span class="pill purple">🐘 PostgreSQL</span>
        <span class="pill purple">📊 Power BI</span>
      </div>
    </div>

    <div class="stack-group">
      <div class="stack-label">── Cloud / DevOps</div>
      <div class="tech-pills">
        <span class="pill orange">☁️ AWS</span>
        <span class="pill orange">🐳 Docker</span>
        <span class="pill orange">⚡ FastAPI</span>
        <span class="pill orange">🔧 Git</span>
        <span class="pill orange">📓 Jupyter</span>
      </div>
    </div>
  </div>

  <!-- ─── PROJECTS ─── -->
  <div class="section reveal">
    <div class="section-header">
      <span class="section-tag">// featured_projects</span>
      <div class="section-line"></div>
    </div>

    <div class="projects-grid">

      <div class="project-card pc1">
        <h3><span class="project-dot" style="color:var(--cyan);background:var(--cyan)"></span>FinSentinel</h3>
        <div class="project-subtitle">// real-time fraud detection pipeline</div>
        <p>Streaming financial transactions via Kafka → FastAPI → Isolation Forest → Gemini AI explainability. Sub-second anomaly detection with AI-generated alert narratives.</p>
        <div class="project-tags">
          <span class="project-tag">Kafka</span>
          <span class="project-tag">FastAPI</span>
          <span class="project-tag">Isolation Forest</span>
          <span class="project-tag">Gemini</span>
          <span class="project-tag">Docker</span>
        </div>
      </div>

      <div class="project-card pc2">
        <h3><span class="project-dot" style="color:var(--green);background:var(--green)"></span>Urban Yield AI</h3>
        <div class="project-subtitle">// real estate intelligence platform</div>
        <p>End-to-end pricing engine combining LangChain agents, XGBoost models, and TF-IDF semantic search on PostgreSQL. Natural language Q&A on property data.</p>
        <div class="project-tags">
          <span class="project-tag">LangChain</span>
          <span class="project-tag">XGBoost</span>
          <span class="project-tag">PostgreSQL</span>
          <span class="project-tag">TF-IDF</span>
        </div>
      </div>

      <div class="project-card pc3">
        <h3><span class="project-dot" style="color:var(--purple);background:var(--purple)"></span>MultiAgent Analyst</h3>
        <div class="project-subtitle">// autonomous data analysis system</div>
        <p>Orchestrated AI agents that write SQL, execute queries, generate charts, and narrate business insights — fully autonomous, zero human mid-flow.</p>
        <div class="project-tags">
          <span class="project-tag">LangChain Agents</span>
          <span class="project-tag">SQL</span>
          <span class="project-tag">Python</span>
        </div>
      </div>

      <div class="project-card pc4">
        <h3><span class="project-dot" style="color:var(--orange);background:var(--orange)"></span>Hybrid RAG Chatbot</h3>
        <div class="project-subtitle">// context-aware ai assistant</div>
        <p>Production RAG pipeline with dual retrieval (dense + sparse), Gemini as reasoning core, ChromaDB as vector store. Handles complex multi-hop queries.</p>
        <div class="project-tags">
          <span class="project-tag">Gemini API</span>
          <span class="project-tag">ChromaDB</span>
          <span class="project-tag">RAG</span>
        </div>
      </div>

      <div class="project-card pc5">
        <h3><span class="project-dot" style="color:var(--red);background:var(--red)"></span>MCP Neural Nexus</h3>
        <div class="project-subtitle">// model context protocol demo</div>
        <p>Live demonstration of MCP — connecting AI models to real-time data sources, external tools, and APIs through a structured protocol layer.</p>
        <div class="project-tags">
          <span class="project-tag">MCP</span>
          <span class="project-tag">LLM</span>
          <span class="project-tag">API Integration</span>
        </div>
      </div>

      <div class="project-card pc6">
        <h3><span class="project-dot" style="color:#60a5fa;background:#60a5fa"></span>Predictive Maintenance</h3>
        <div class="project-subtitle">// industrial failure forecasting</div>
        <p>ML pipeline for predicting industrial equipment failures before they occur using sensor time-series data. Reduces unplanned downtime significantly.</p>
        <div class="project-tags">
          <span class="project-tag">Scikit-Learn</span>
          <span class="project-tag">Time Series</span>
          <span class="project-tag">Python</span>
        </div>
      </div>

    </div>
  </div>

  <!-- ─── STATS ─── -->
  <div class="section reveal">
    <div class="section-header">
      <span class="section-tag">// github_metrics</span>
      <div class="section-line"></div>
    </div>
    <div class="stats-row">
      <div class="stat-card">
        <span class="stat-number" data-target="6">0</span>
        <span class="stat-label">Projects</span>
      </div>
      <div class="stat-card">
        <span class="stat-number" data-target="12">0</span>
        <span class="stat-label">Tech Tools</span>
      </div>
      <div class="stat-card">
        <span class="stat-number" data-target="3">0</span>
        <span class="stat-label">AI Frameworks</span>
      </div>
    </div>
    <div style="margin-top:16px; border-radius:14px; overflow:hidden; border: 1px solid var(--glass-border);">
      <img src="https://github-readme-stats.vercel.app/api?username=HelloRohit26&show_icons=true&theme=tokyonight&hide_border=true&bg_color=060a12&title_color=00fff0&icon_color=00ff88&text_color=94a3b8&ring_color=b16cff" style="width:100%; display:block;" />
    </div>
    <div style="margin-top:12px; border-radius:14px; overflow:hidden; border: 1px solid var(--glass-border);">
      <img src="https://github-readme-streak-stats.herokuapp.com?user=HelloRohit26&theme=tokyonight&hide_border=true&background=060a12&ring=00fff0&fire=00ff88&currStreakLabel=00fff0" style="width:100%; display:block;" />
    </div>
  </div>

  <!-- ─── GOALS CODE BLOCK ─── -->
  <div class="section reveal">
    <div class="section-header">
      <span class="section-tag">// roadmap</span>
      <div class="section-line"></div>
    </div>
    <div class="code-block">
      <div><span class="kw">goals</span> <span class="bracket">= {</span></div>
      <div>&nbsp;&nbsp;<span class="key">"short_term"</span> <span class="bracket">: [</span><span class="str">"Land Data/AI Engineer role 🎯"</span><span class="bracket">,</span> <span class="str">"Contribute to Open Source AI"</span><span class="bracket">],</span></div>
      <div>&nbsp;&nbsp;<span class="key">"medium_term"</span><span class="bracket">: [</span><span class="str">"Build production Agentic AI systems"</span><span class="bracket">,</span> <span class="str">"AWS + MLflow certifications"</span><span class="bracket">],</span></div>
      <div>&nbsp;&nbsp;<span class="key">"long_term"</span>  <span class="bracket">: [</span><span class="str">"Ship an LLM-powered SaaS product"</span><span class="bracket">,</span> <span class="str">"Speak at a tech conference"</span><span class="bracket">],</span></div>
      <div><span class="bracket">}</span></div>
      <div>&nbsp;</div>
      <div><span class="kw">learning_now</span> <span class="bracket">= [</span><span class="str">"Advanced LLM Orchestration"</span><span class="bracket">,</span> <span class="str">"Agentic Patterns"</span><span class="bracket">,</span> <span class="str">"DSA"</span><span class="bracket">]</span></div>
      <div>&nbsp;</div>
      <div><span class="comment"># Currently open to: Data Engineer / AI Engineer / MLOps roles</span></div>
    </div>
  </div>

  <!-- ─── FOOTER ─── -->
  <div class="footer reveal">
    <p class="footer-text">// end of file — thanks for scrolling this far</p>
    <p class="footer-glow">LET'S BUILD SOMETHING THAT MATTERS</p>
    <div style="margin-top:20px;">
      <img src="https://komarev.com/ghpvc/?username=HelloRohit26&color=00fff0&style=for-the-badge&label=PROFILE+VIEWS" alt="views"/>
    </div>
  </div>

</div>

<script>
// ─── PARTICLES ───
const canvas = document.getElementById('particles');
const ctx = canvas.getContext('2d');
let W, H, particles = [];

function resize() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

class Particle {
  constructor() { this.reset(); }
  reset() {
    this.x = Math.random() * W;
    this.y = Math.random() * H;
    this.size = Math.random() * 1.5 + 0.3;
    this.speedX = (Math.random() - 0.5) * 0.4;
    this.speedY = (Math.random() - 0.5) * 0.4;
    this.opacity = Math.random() * 0.5 + 0.1;
    this.color = Math.random() > 0.7 ? '#00fff0' : Math.random() > 0.5 ? '#b16cff' : '#00ff88';
  }
  update() {
    this.x += this.speedX;
    this.y += this.speedY;
    if (this.x < 0 || this.x > W || this.y < 0 || this.y > H) this.reset();
  }
  draw() {
    ctx.save();
    ctx.globalAlpha = this.opacity;
    ctx.fillStyle = this.color;
    ctx.shadowBlur = 6;
    ctx.shadowColor = this.color;
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
    ctx.fill();
    ctx.restore();
  }
}

for (let i = 0; i < 120; i++) particles.push(new Particle());

function connectParticles() {
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const dist = Math.sqrt(dx * dx + dy * dy);
      if (dist < 100) {
        ctx.save();
        ctx.globalAlpha = (1 - dist / 100) * 0.08;
        ctx.strokeStyle = '#00fff0';
        ctx.lineWidth = 0.5;
        ctx.beginPath();
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        ctx.stroke();
        ctx.restore();
      }
    }
  }
}

function animate() {
  ctx.clearRect(0, 0, W, H);
  particles.forEach(p => { p.update(); p.draw(); });
  connectParticles();
  requestAnimationFrame(animate);
}
animate();

// ─── SCROLL REVEAL ───
const reveals = document.querySelectorAll('.reveal');
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.1 });
reveals.forEach(r => observer.observe(r));

// ─── COUNT UP ANIMATION ───
const counters = document.querySelectorAll('.stat-number[data-target]');
const countObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const el = entry.target;
      const target = parseInt(el.dataset.target);
      let current = 0;
      const increment = target / 40;
      const timer = setInterval(() => {
        current += increment;
        if (current >= target) { el.textContent = target + '+'; clearInterval(timer); }
        else { el.textContent = Math.floor(current); }
      }, 30);
      countObserver.unobserve(el);
    }
  });
}, { threshold: 0.5 });
counters.forEach(c => countObserver.observe(c));
</script>
</body>
</html>
