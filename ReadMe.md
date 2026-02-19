<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Madusha Senevirathna — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Mono:ital,wght@0,300;0,400;1,300&family=Outfit:wght@300;400;600;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #050810;
    --surface: #0b1020;
    --accent: #00d4ff;
    --accent2: #ff6b35;
    --accent3: #a78bfa;
    --text: #e8eaf6;
    --muted: #5a6070;
    --grid: rgba(0, 212, 255, 0.04);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Outfit', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom Cursor */
  .cursor {
    width: 10px; height: 10px;
    background: var(--accent);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9999;
    mix-blend-mode: screen;
    transition: transform 0.1s ease;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1px solid rgba(0,212,255,0.4);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9998;
    transition: all 0.18s ease;
  }

  /* Grid Background */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image:
      linear-gradient(var(--grid) 1px, transparent 1px),
      linear-gradient(90deg, var(--grid) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* Glowing orbs */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    opacity: 0.12;
    pointer-events: none;
    z-index: 0;
    animation: drift 20s ease-in-out infinite alternate;
  }
  .orb-1 { width: 600px; height: 600px; background: var(--accent); top: -200px; right: -100px; animation-delay: 0s; }
  .orb-2 { width: 400px; height: 400px; background: var(--accent2); bottom: 100px; left: -150px; animation-delay: -7s; }
  .orb-3 { width: 300px; height: 300px; background: var(--accent3); top: 50%; left: 50%; animation-delay: -14s; }

  @keyframes drift {
    0% { transform: translate(0, 0) scale(1); }
    100% { transform: translate(40px, -40px) scale(1.1); }
  }

  /* Sections */
  section { position: relative; z-index: 1; }

  /* ─── HERO ─── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center; align-items: flex-start;
    padding: 0 10vw;
    overflow: hidden;
  }

  .hero-tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    letter-spacing: 0.3em;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.2s ease forwards;
  }

  .hero-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(5rem, 14vw, 13rem);
    line-height: 0.88;
    letter-spacing: -0.01em;
    background: linear-gradient(135deg, #fff 0%, var(--accent) 60%, var(--accent3) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    opacity: 0;
    animation: fadeUp 0.8s 0.4s ease forwards;
  }

  .hero-role {
    font-size: clamp(1rem, 2.5vw, 1.5rem);
    font-weight: 300;
    color: var(--muted);
    margin-top: 1.5rem;
    letter-spacing: 0.05em;
    opacity: 0;
    animation: fadeUp 0.8s 0.6s ease forwards;
  }
  .hero-role span { color: var(--accent2); font-weight: 600; }

  .hero-cta {
    display: flex; gap: 1rem; margin-top: 3rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.8s ease forwards;
  }

  .btn {
    padding: 0.8rem 2rem;
    font-family: 'DM Mono', monospace;
    font-size: 0.8rem;
    letter-spacing: 0.1em;
    border: none; cursor: pointer;
    text-decoration: none;
    transition: all 0.3s ease;
  }
  .btn-primary {
    background: var(--accent);
    color: var(--bg);
    font-weight: 600;
    clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 12px 100%, 0 calc(100% - 12px));
  }
  .btn-primary:hover { background: #fff; transform: translateY(-2px); box-shadow: 0 10px 40px rgba(0,212,255,0.3); }
  .btn-ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--muted);
    clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 12px 100%, 0 calc(100% - 12px));
  }
  .btn-ghost:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }

  .hero-scroll {
    position: absolute; bottom: 3rem; left: 10vw;
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: var(--muted);
    letter-spacing: 0.2em;
    display: flex; align-items: center; gap: 1rem;
    opacity: 0;
    animation: fadeUp 0.8s 1.2s ease forwards;
  }
  .hero-scroll::after {
    content: '';
    width: 60px; height: 1px;
    background: linear-gradient(90deg, var(--muted), transparent);
  }

  /* ─── STATUS BAR ─── */
  .status-bar {
    background: var(--surface);
    border-top: 1px solid rgba(255,255,255,0.04);
    border-bottom: 1px solid rgba(255,255,255,0.04);
    padding: 1rem 10vw;
    display: flex; gap: 3rem; align-items: center;
    overflow-x: auto;
    white-space: nowrap;
  }
  .status-item {
    display: flex; align-items: center; gap: 0.6rem;
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    letter-spacing: 0.05em;
  }
  .status-dot {
    width: 6px; height: 6px; border-radius: 50%;
    animation: pulse 2s ease-in-out infinite;
  }
  .dot-green { background: #00ff88; box-shadow: 0 0 10px #00ff88; }
  .dot-yellow { background: #ffcc00; }
  .dot-blue { background: var(--accent); }
  @keyframes pulse { 0%, 100% { opacity: 1; } 50% { opacity: 0.4; } }

  /* ─── ABOUT ─── */
  .about {
    padding: 8rem 10vw;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: center;
  }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--accent);
    letter-spacing: 0.3em;
    text-transform: uppercase;
    margin-bottom: 1rem;
    display: flex; align-items: center; gap: 1rem;
  }
  .section-label::before {
    content: '';
    width: 30px; height: 1px;
    background: var(--accent);
  }

  .section-heading {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(2.5rem, 5vw, 4rem);
    line-height: 1;
    margin-bottom: 1.5rem;
    color: #fff;
  }

  .about-text {
    font-size: 1rem;
    line-height: 1.9;
    color: var(--muted);
    font-weight: 300;
  }
  .about-text em { color: var(--accent); font-style: normal; font-weight: 600; }

  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.06);
  }
  .stat-box {
    background: var(--bg);
    padding: 2rem;
    text-align: center;
    transition: background 0.3s;
  }
  .stat-box:hover { background: var(--surface); }
  .stat-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 3.5rem;
    color: var(--accent);
    line-height: 1;
  }
  .stat-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: var(--muted);
    letter-spacing: 0.15em;
    margin-top: 0.4rem;
    text-transform: uppercase;
  }

  /* ─── SKILLS ─── */
  .skills { padding: 8rem 10vw; }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: rgba(255,255,255,0.06);
    margin-top: 4rem;
  }

  .skill-category {
    background: var(--bg);
    padding: 2.5rem;
    transition: background 0.3s;
    position: relative;
    overflow: hidden;
  }
  .skill-category::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--accent-cat), transparent);
    transform: scaleX(0);
    transition: transform 0.4s ease;
  }
  .skill-category:hover::before { transform: scaleX(1); }
  .skill-category:hover { background: var(--surface); }

  .skill-category:nth-child(1) { --accent-cat: var(--accent); }
  .skill-category:nth-child(2) { --accent-cat: var(--accent2); }
  .skill-category:nth-child(3) { --accent-cat: var(--accent3); }

  .cat-icon {
    font-size: 2rem;
    margin-bottom: 1rem;
    display: block;
  }
  .cat-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.5rem;
    letter-spacing: 0.05em;
    margin-bottom: 1.5rem;
    color: #fff;
  }

  .skill-tags {
    display: flex; flex-wrap: wrap; gap: 0.5rem;
  }
  .tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.08em;
    padding: 0.3rem 0.7rem;
    border: 1px solid rgba(255,255,255,0.08);
    color: var(--muted);
    transition: all 0.2s;
  }
  .tag:hover { border-color: var(--accent-cat); color: var(--text); }

  /* ─── WHAT I DO ─── */
  .what {
    padding: 8rem 10vw;
    background: var(--surface);
    border-top: 1px solid rgba(255,255,255,0.04);
    border-bottom: 1px solid rgba(255,255,255,0.04);
  }

  .what-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
    margin-top: 4rem;
  }

  .what-card {
    padding: 2.5rem;
    border: 1px solid rgba(255,255,255,0.06);
    position: relative;
    overflow: hidden;
    cursor: default;
    transition: border-color 0.3s, transform 0.3s;
  }
  .what-card:hover { border-color: rgba(0,212,255,0.2); transform: translateY(-4px); }
  .what-card::after {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(0,212,255,0.03), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .what-card:hover::after { opacity: 1; }

  .card-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 5rem;
    color: rgba(255,255,255,0.03);
    position: absolute; top: -0.5rem; right: 1rem;
    line-height: 1;
    pointer-events: none;
  }
  .card-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 1.6rem;
    letter-spacing: 0.05em;
    color: #fff;
    margin-bottom: 0.8rem;
  }
  .card-desc {
    font-size: 0.9rem;
    line-height: 1.8;
    color: var(--muted);
    font-weight: 300;
  }
  .card-marker {
    width: 30px; height: 2px;
    margin-bottom: 1.5rem;
  }

  /* ─── CONNECT ─── */
  .connect {
    padding: 8rem 10vw;
    text-align: center;
  }

  .connect-heading {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(3rem, 8vw, 8rem);
    line-height: 1;
    background: linear-gradient(135deg, #fff, var(--accent3));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 1.5rem;
  }

  .connect-sub {
    font-size: 1rem;
    color: var(--muted);
    margin-bottom: 3rem;
    font-weight: 300;
  }

  .social-row {
    display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;
    margin-top: 2rem;
  }

  .social-link {
    display: flex; align-items: center; gap: 0.6rem;
    padding: 0.75rem 1.5rem;
    border: 1px solid rgba(255,255,255,0.08);
    color: var(--muted);
    text-decoration: none;
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.1em;
    transition: all 0.3s;
    clip-path: polygon(0 0, calc(100% - 8px) 0, 100% 8px, 100% 100%, 8px 100%, 0 calc(100% - 8px));
  }
  .social-link:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-3px); background: rgba(0,212,255,0.05); }

  /* ─── FOOTER ─── */
  footer {
    padding: 2rem 10vw;
    border-top: 1px solid rgba(255,255,255,0.04);
    display: flex; justify-content: space-between; align-items: center;
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: var(--muted);
    letter-spacing: 0.1em;
  }

  /* Animations */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(40px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* Responsive */
  @media (max-width: 768px) {
    .about { grid-template-columns: 1fr; gap: 3rem; }
    .skills-grid { grid-template-columns: 1fr; }
    .what-grid { grid-template-columns: 1fr; }
    .status-bar { gap: 1.5rem; }
  }
</style>
</head>
<body>

<!-- Custom Cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Glowing Orbs -->
<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="orb orb-3"></div>

<!-- ─── HERO ─── -->
<section class="hero">
  <div class="hero-tag">// Portfolio v2025</div>
  <div class="hero-name">Madusha<br>Sene<br>virathna</div>
  <p class="hero-role">Fullstack Developer &nbsp;·&nbsp; <span>UI/UX Enthusiast</span> &nbsp;·&nbsp; Creative Coder</p>
  <div class="hero-cta">
    <a href="mailto:ncsmis23@gmail.com" class="btn btn-primary">GET IN TOUCH</a>
    <a href="https://www.linkedin.com/in/madu-isuranga-ab129a234/" class="btn btn-ghost">VIEW LINKEDIN</a>
  </div>
  <div class="hero-scroll">SCROLL TO EXPLORE</div>
</section>

<!-- ─── STATUS BAR ─── -->
<div class="status-bar">
  <div class="status-item"><div class="status-dot dot-green"></div> Available for projects</div>
  <div class="status-item"><div class="status-dot dot-blue"></div> Learning: Microservices + K8s</div>
  <div class="status-item"><div class="status-dot dot-yellow"></div> Building: High-performance React apps</div>
  <div class="status-item"><div class="status-dot dot-blue"></div> Open to: MERN / Java collaboration</div>
</div>

<!-- ─── ABOUT ─── -->
<section class="about">
  <div class="reveal">
    <div class="section-label">About</div>
    <h2 class="section-heading">I BUILD THINGS THAT MOVE</h2>
    <p class="about-text">
      I bridge the gap between <em>complex backend systems</em> and sleek, interactive front-end experiences. 
      From smooth GSAP animations to scalable Spring Boot microservices — I care deeply about every pixel and every endpoint.
      <br><br>
      Currently deep-diving into <em>Advanced React patterns</em>, <em>DevOps</em>, and building production-ready applications that don't just work — they <em>delight</em>.
    </p>
  </div>
  <div class="reveal" style="transition-delay: 0.2s">
    <div class="stats-grid">
      <div class="stat-box">
        <div class="stat-num">3+</div>
        <div class="stat-label">Years Coding</div>
      </div>
      <div class="stat-box">
        <div class="stat-num">20+</div>
        <div class="stat-label">Technologies</div>
      </div>
      <div class="stat-box">
        <div class="stat-num">∞</div>
        <div class="stat-label">Ideas Building</div>
      </div>
      <div class="stat-box">
        <div class="stat-num">01</div>
        <div class="stat-label">Focus: Quality</div>
      </div>
    </div>
  </div>
</section>

<!-- ─── SKILLS ─── -->
<section class="skills">
  <div class="reveal">
    <div class="section-label">Stack</div>
    <h2 class="section-heading">TECH I WORK WITH</h2>
  </div>
  <div class="skills-grid">
    <div class="skill-category reveal">
      <span class="cat-icon">⚡</span>
      <div class="cat-title">Frontend & Animation</div>
      <div class="skill-tags">
        <span class="tag">React</span>
        <span class="tag">Vue</span>
        <span class="tag">Next.js</span>
        <span class="tag">TypeScript</span>
        <span class="tag">GSAP</span>
        <span class="tag">Tailwind</span>
        <span class="tag">HTML</span>
        <span class="tag">CSS</span>
        <span class="tag">Figma</span>
      </div>
    </div>
    <div class="skill-category reveal" style="transition-delay:0.1s">
      <span class="cat-icon">🛠</span>
      <div class="cat-title">Backend & Databases</div>
      <div class="skill-tags">
        <span class="tag">Node.js</span>
        <span class="tag">Express</span>
        <span class="tag">Java</span>
        <span class="tag">Spring Boot</span>
        <span class="tag">PHP</span>
        <span class="tag">.NET</span>
        <span class="tag">MySQL</span>
        <span class="tag">PostgreSQL</span>
        <span class="tag">MongoDB</span>
        <span class="tag">Firebase</span>
      </div>
    </div>
    <div class="skill-category reveal" style="transition-delay:0.2s">
      <span class="cat-icon">🚀</span>
      <div class="cat-title">DevOps & Tools</div>
      <div class="skill-tags">
        <span class="tag">Git</span>
        <span class="tag">Docker</span>
        <span class="tag">Kubernetes</span>
        <span class="tag">AWS</span>
        <span class="tag">Linux</span>
        <span class="tag">Postman</span>
        <span class="tag">Unity</span>
        <span class="tag">Arduino</span>
      </div>
    </div>
  </div>
</section>

<!-- ─── WHAT I DO ─── -->
<section class="what">
  <div class="reveal">
    <div class="section-label">Services</div>
    <h2 class="section-heading">WHAT I DO</h2>
  </div>
  <div class="what-grid">
    <div class="what-card reveal">
      <div class="card-num">01</div>
      <div class="card-marker" style="background: linear-gradient(90deg, var(--accent), transparent)"></div>
      <div class="card-title">Fullstack Development</div>
      <p class="card-desc">End-to-end web applications from database design to polished UI, using the MERN stack or Java Spring Boot with React/Vue frontends.</p>
    </div>
    <div class="what-card reveal" style="transition-delay:0.1s">
      <div class="card-num">02</div>
      <div class="card-marker" style="background: linear-gradient(90deg, var(--accent2), transparent)"></div>
      <div class="card-title">UI/UX & Animation</div>
      <p class="card-desc">Turning wireframes into fluid, interactive experiences. GSAP animations, micro-interactions, and obsessive attention to UI details.</p>
    </div>
    <div class="what-card reveal" style="transition-delay:0.2s">
      <div class="card-num">03</div>
      <div class="card-marker" style="background: linear-gradient(90deg, var(--accent3), transparent)"></div>
      <div class="card-title">Microservices & DevOps</div>
      <p class="card-desc">Designing scalable microservice architectures with Spring Boot and containerizing them with Docker and Kubernetes for production.</p>
    </div>
    <div class="what-card reveal" style="transition-delay:0.3s">
      <div class="card-num">04</div>
      <div class="card-marker" style="background: linear-gradient(90deg, #00ff88, transparent)"></div>
      <div class="card-title">Creative Coding</div>
      <p class="card-desc">Bridging art and technology. From generative visuals to interactive 3D experiments — I enjoy turning ideas into unexpected digital experiences.</p>
    </div>
  </div>
</section>

<!-- ─── CONNECT ─── -->
<section class="connect">
  <div class="reveal">
    <div class="section-label" style="justify-content: center;">Contact</div>
    <h2 class="connect-heading">LET'S BUILD<br>SOMETHING</h2>
    <p class="connect-sub">Open to collaborations, freelance work, or just a good conversation about code.</p>
    <a href="mailto:ncsmis23@gmail.com" class="btn btn-primary" style="font-size:0.9rem; padding: 1rem 3rem;">ncsmis23@gmail.com</a>
    <div class="social-row">
      <a href="https://www.linkedin.com/in/madu-isuranga-ab129a234/" class="social-link" target="_blank">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
        LINKEDIN
      </a>
      <a href="https://www.youtube.com/@AiArtistry-g8i" class="social-link" target="_blank">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M22.54 6.42a2.78 2.78 0 0 0-1.95-1.96C18.88 4 12 4 12 4s-6.88 0-8.59.46A2.78 2.78 0 0 0 1.46 6.42 29 29 0 0 0 1 12a29 29 0 0 0 .46 5.58 2.78 2.78 0 0 0 1.95 1.95C5.12 20 12 20 12 20s6.88 0 8.59-.47a2.78 2.78 0 0 0 1.95-1.95A29 29 0 0 0 23 12a29 29 0 0 0-.46-5.58z"/><polygon points="9.75 15.02 15.5 12 9.75 8.98 9.75 15.02" fill="#050810"/></svg>
        YOUTUBE
      </a>
      <a href="https://instagram.com/isuranga.madusha" class="social-link" target="_blank">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg>
        INSTAGRAM
      </a>
    </div>
  </div>
</section>

<!-- ─── FOOTER ─── -->
<footer>
  <span>© 2025 MADUSHA SENEVIRATHNA</span>
  <span>DESIGNED &amp; CODED WITH ♥</span>
</footer>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.transform = `translate(${mx - 5}px, ${my - 5}px)`;
  });
  function animRing() {
    rx += (mx - rx - 18) * 0.14;
    ry += (my - ry - 18) * 0.14;
    ring.style.transform = `translate(${rx}px, ${ry}px)`;
    requestAnimationFrame(animRing);
  }
  animRing();

  document.querySelectorAll('a, button, .stat-box, .what-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform += ' scale(2)';
      ring.style.transform += ' scale(1.5)';
      ring.style.borderColor = 'rgba(0,212,255,0.8)';
    });
    el.addEventListener('mouseleave', () => {
      ring.style.borderColor = 'rgba(0,212,255,0.4)';
    });
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const obs = new IntersectionObserver((entries) => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.15 });
  reveals.forEach(el => obs.observe(el));
</script>
</body>
</html>
