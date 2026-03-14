<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Arpit — Web Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --bg2: #111118;
    --card: #15151e;
    --border: rgba(255,255,255,0.07);
    --accent: #5b6bff;
    --accent2: #ff6b6b;
    --green: #00e5a0;
    --text: #f0f0f8;
    --muted: #7a7a9a;
    --gold: #ffd166;
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 16px;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 1.2rem 2rem;
    display: flex; align-items: center; justify-content: space-between;
    background: rgba(10,10,15,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.4rem;
    letter-spacing: -0.03em;
    background: linear-gradient(135deg, var(--accent), var(--green));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.9rem;
    font-weight: 500;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--text); }
  .nav-cta {
    background: var(--accent);
    color: #fff !important;
    padding: 0.5rem 1.2rem;
    border-radius: 50px;
    font-weight: 500 !important;
    font-size: 0.85rem !important;
    transition: opacity 0.2s !important;
  }
  .nav-cta:hover { opacity: 0.85; }
  .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
  .hamburger span { width: 24px; height: 2px; background: var(--text); border-radius: 2px; }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex; align-items: center; justify-content: center;
    padding: 8rem 2rem 4rem;
    position: relative;
    overflow: hidden;
  }
  .hero-grid {
    position: absolute; inset: 0;
    background-image: linear-gradient(var(--border) 1px, transparent 1px),
                      linear-gradient(90deg, var(--border) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black 30%, transparent 100%);
  }
  .hero-glow {
    position: absolute;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(91,107,255,0.15) 0%, transparent 70%);
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    pointer-events: none;
  }
  .hero-content {
    max-width: 820px;
    text-align: center;
    position: relative; z-index: 2;
  }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 0.5rem;
    background: rgba(91,107,255,0.1);
    border: 1px solid rgba(91,107,255,0.25);
    color: var(--accent);
    padding: 0.4rem 1rem;
    border-radius: 50px;
    font-size: 0.8rem;
    font-weight: 500;
    margin-bottom: 1.8rem;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    animation: fadeDown 0.8s ease both;
  }
  .hero-badge::before {
    content: '';
    width: 6px; height: 6px;
    background: var(--green);
    border-radius: 50%;
    box-shadow: 0 0 8px var(--green);
    animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.8rem, 7vw, 5.5rem);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -0.04em;
    margin-bottom: 1.5rem;
    animation: fadeUp 0.9s 0.1s ease both;
  }
  .hero h1 .highlight {
    background: linear-gradient(135deg, var(--accent), var(--green));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .hero p {
    font-size: 1.15rem;
    color: var(--muted);
    max-width: 560px;
    margin: 0 auto 2.5rem;
    line-height: 1.7;
    font-weight: 300;
    animation: fadeUp 0.9s 0.2s ease both;
  }
  .hero-btns {
    display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;
    animation: fadeUp 0.9s 0.3s ease both;
  }
  .btn-primary {
    background: var(--accent);
    color: #fff;
    padding: 0.85rem 2rem;
    border-radius: 50px;
    text-decoration: none;
    font-weight: 500;
    font-size: 0.95rem;
    display: inline-flex; align-items: center; gap: 0.5rem;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 0 30px rgba(91,107,255,0.3);
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 0 40px rgba(91,107,255,0.5); }
  .btn-outline {
    background: transparent;
    color: var(--text);
    padding: 0.85rem 2rem;
    border-radius: 50px;
    text-decoration: none;
    font-weight: 500;
    font-size: 0.95rem;
    border: 1px solid var(--border);
    display: inline-flex; align-items: center; gap: 0.5rem;
    transition: border-color 0.2s, background 0.2s;
  }
  .btn-outline:hover { border-color: var(--accent); background: rgba(91,107,255,0.05); }
  .hero-stats {
    display: flex; gap: 3rem; justify-content: center; flex-wrap: wrap;
    margin-top: 4rem;
    animation: fadeUp 0.9s 0.4s ease both;
  }
  .stat { text-align: center; }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 2rem;
    font-weight: 800;
    background: linear-gradient(135deg, var(--text), var(--muted));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .stat-label { font-size: 0.8rem; color: var(--muted); text-transform: uppercase; letter-spacing: 0.08em; }

  @keyframes fadeUp { from{opacity:0;transform:translateY(20px)} to{opacity:1;transform:translateY(0)} }
  @keyframes fadeDown { from{opacity:0;transform:translateY(-10px)} to{opacity:1;transform:translateY(0)} }

  /* SECTIONS */
  section { padding: 6rem 2rem; }
  .container { max-width: 1100px; margin: 0 auto; }
  .section-label {
    font-size: 0.75rem;
    color: var(--accent);
    text-transform: uppercase;
    letter-spacing: 0.12em;
    font-weight: 600;
    margin-bottom: 0.8rem;
  }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 800;
    letter-spacing: -0.03em;
    margin-bottom: 1.2rem;
    line-height: 1.1;
  }
  .section-sub {
    color: var(--muted);
    font-size: 1.05rem;
    max-width: 540px;
    line-height: 1.7;
    font-weight: 300;
  }

  /* ABOUT */
  .about { background: var(--bg2); }
  .about-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: center;
  }
  .about-visual {
    position: relative;
    display: flex; align-items: center; justify-content: center;
  }
  .about-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 2.5rem;
    width: 100%;
    max-width: 340px;
    position: relative;
    overflow: hidden;
  }
  .about-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: linear-gradient(90deg, var(--accent), var(--green));
  }
  .about-avatar {
    width: 80px; height: 80px;
    background: linear-gradient(135deg, var(--accent), var(--green));
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 2rem;
    font-weight: 800;
    color: #fff;
    margin-bottom: 1.2rem;
  }
  .about-card h3 {
    font-family: 'Syne', sans-serif;
    font-size: 1.3rem;
    font-weight: 700;
    margin-bottom: 0.3rem;
  }
  .about-card .role { color: var(--accent); font-size: 0.85rem; margin-bottom: 1.2rem; }
  .about-skills { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 1.2rem; }
  .skill-tag {
    background: rgba(91,107,255,0.1);
    border: 1px solid rgba(91,107,255,0.2);
    color: var(--accent);
    padding: 0.3rem 0.8rem;
    border-radius: 50px;
    font-size: 0.75rem;
    font-weight: 500;
  }
  .about-text p { color: var(--muted); line-height: 1.8; margin-bottom: 1rem; font-weight: 300; }
  .about-text p strong { color: var(--text); font-weight: 600; }

  /* PRICING TOGGLE */
  .pricing { background: var(--bg); }
  .pricing-header { text-align: center; margin-bottom: 3rem; }
  .pricing-toggle {
    display: inline-flex;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 50px;
    padding: 4px;
    margin-top: 1.5rem;
  }
  .toggle-btn {
    padding: 0.6rem 1.5rem;
    border-radius: 50px;
    font-size: 0.9rem;
    font-weight: 500;
    cursor: pointer;
    border: none;
    background: transparent;
    color: var(--muted);
    transition: all 0.3s;
    font-family: 'DM Sans', sans-serif;
  }
  .toggle-btn.active {
    background: var(--accent);
    color: #fff;
  }
  .pricing-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }
  .price-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 2.2rem;
    position: relative;
    transition: transform 0.3s, border-color 0.3s;
    overflow: hidden;
  }
  .price-card:hover { transform: translateY(-6px); border-color: rgba(91,107,255,0.3); }
  .price-card.featured {
    border-color: var(--accent);
    background: linear-gradient(160deg, rgba(91,107,255,0.08), var(--card));
  }
  .popular-badge {
    position: absolute; top: 1.5rem; right: 1.5rem;
    background: var(--accent);
    color: #fff;
    font-size: 0.7rem;
    font-weight: 600;
    padding: 0.3rem 0.8rem;
    border-radius: 50px;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }
  .price-tier {
    font-size: 0.75rem;
    color: var(--accent);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    font-weight: 600;
    margin-bottom: 0.5rem;
  }
  .price-name {
    font-family: 'Syne', sans-serif;
    font-size: 1.4rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
  }
  .price-amount {
    font-family: 'Syne', sans-serif;
    font-size: 2.8rem;
    font-weight: 800;
    color: var(--text);
    margin: 1rem 0;
    line-height: 1;
  }
  .price-amount span { font-size: 1.2rem; color: var(--muted); font-weight: 400; }
  .price-divider { height: 1px; background: var(--border); margin: 1.2rem 0; }
  .price-features { list-style: none; display: flex; flex-direction: column; gap: 0.7rem; margin-bottom: 2rem; }
  .price-features li {
    display: flex; align-items: center; gap: 0.6rem;
    font-size: 0.9rem;
    color: var(--muted);
  }
  .price-features li::before {
    content: '✓';
    color: var(--green);
    font-weight: 700;
    font-size: 0.85rem;
    flex-shrink: 0;
  }
  .price-btn {
    display: block;
    text-align: center;
    padding: 0.85rem;
    border-radius: 12px;
    text-decoration: none;
    font-weight: 600;
    font-size: 0.9rem;
    transition: all 0.2s;
  }
  .price-btn-outline {
    border: 1px solid var(--border);
    color: var(--text);
  }
  .price-btn-outline:hover { border-color: var(--accent); color: var(--accent); }
  .price-btn-solid { background: var(--accent); color: #fff; }
  .price-btn-solid:hover { opacity: 0.88; }
  .pricing-plans { display: block; }
  .pricing-plans.hidden { display: none; }

  /* REDESIGN */
  .redesign { background: var(--bg2); }
  .redesign-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
  }
  .redesign-features { display: flex; flex-direction: column; gap: 1rem; margin-top: 2rem; }
  .redesign-feature {
    display: flex; gap: 1rem; align-items: flex-start;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.2rem;
    transition: border-color 0.2s;
  }
  .redesign-feature:hover { border-color: rgba(91,107,255,0.3); }
  .feature-icon {
    width: 42px; height: 42px;
    background: rgba(91,107,255,0.1);
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }
  .feature-text h4 { font-size: 0.95rem; font-weight: 600; margin-bottom: 0.2rem; }
  .feature-text p { font-size: 0.85rem; color: var(--muted); line-height: 1.5; }
  .redesign-visual {
    position: relative;
  }
  .redesign-mockup {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    overflow: hidden;
  }
  .mockup-bar {
    background: rgba(255,255,255,0.04);
    padding: 0.8rem 1.2rem;
    display: flex; align-items: center; gap: 0.5rem;
    border-bottom: 1px solid var(--border);
  }
  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .mockup-content { padding: 1.5rem; }
  .mockup-line { height: 10px; background: var(--border); border-radius: 50px; margin-bottom: 0.8rem; }
  .mockup-line.w60 { width: 60%; }
  .mockup-line.w80 { width: 80%; }
  .mockup-line.w40 { width: 40%; }
  .arrow-anim {
    text-align: center;
    font-size: 2rem;
    padding: 1rem;
    color: var(--accent);
    animation: bounce 1.5s infinite;
  }
  @keyframes bounce { 0%,100%{transform:translateX(0)} 50%{transform:translateX(8px)} }
  .mockup-after { background: linear-gradient(135deg, rgba(91,107,255,0.05), rgba(0,229,160,0.05)); }
  .mockup-after .mockup-line { background: rgba(91,107,255,0.2); }

  /* TESTIMONIALS */
  .testimonials { background: var(--bg); }
  .testimonials-header { text-align: center; margin-bottom: 3.5rem; }
  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
  }
  .testimonial-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 2rem;
    transition: transform 0.3s, border-color 0.3s;
    position: relative;
  }
  .testimonial-card:hover { transform: translateY(-5px); border-color: rgba(91,107,255,0.3); }
  .testimonial-card::before {
    content: '"';
    position: absolute;
    top: 1rem; right: 1.5rem;
    font-size: 5rem;
    font-family: 'Syne', sans-serif;
    color: rgba(91,107,255,0.1);
    line-height: 1;
  }
  .stars { color: var(--gold); font-size: 1rem; margin-bottom: 1rem; letter-spacing: 2px; }
  .testimonial-text {
    color: var(--muted);
    font-size: 0.95rem;
    line-height: 1.7;
    font-weight: 300;
    margin-bottom: 1.5rem;
  }
  .testimonial-author {
    display: flex; align-items: center; gap: 0.8rem;
  }
  .author-avatar {
    width: 40px; height: 40px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 0.9rem;
    font-weight: 700;
    color: #fff;
    flex-shrink: 0;
  }
  .author-name { font-weight: 600; font-size: 0.9rem; }
  .author-type { font-size: 0.8rem; color: var(--muted); }

  /* CONTACT */
  .contact { background: var(--bg2); }
  .contact-inner {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }
  .contact-info { display: flex; flex-direction: column; gap: 1.2rem; margin-top: 2rem; }
  .contact-item {
    display: flex; align-items: center; gap: 1rem;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 1.2rem;
  }
  .contact-icon {
    width: 44px; height: 44px;
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.2rem;
    flex-shrink: 0;
  }
  .contact-detail .label { font-size: 0.75rem; color: var(--muted); text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 0.2rem; }
  .contact-detail a { color: var(--text); text-decoration: none; font-weight: 500; transition: color 0.2s; }
  .contact-detail a:hover { color: var(--accent); }
  .contact-btns { display: flex; flex-direction: column; gap: 1rem; margin-top: 2rem; }
  .wa-btn {
    display: flex; align-items: center; gap: 1rem;
    background: #25D366;
    color: #fff;
    padding: 1rem 1.5rem;
    border-radius: 14px;
    text-decoration: none;
    font-weight: 600;
    font-size: 1rem;
    transition: opacity 0.2s, transform 0.2s;
  }
  .wa-btn:hover { opacity: 0.9; transform: translateY(-2px); }
  .call-btn {
    display: flex; align-items: center; gap: 1rem;
    background: var(--accent);
    color: #fff;
    padding: 1rem 1.5rem;
    border-radius: 14px;
    text-decoration: none;
    font-weight: 600;
    font-size: 1rem;
    transition: opacity 0.2s, transform 0.2s;
  }
  .call-btn:hover { opacity: 0.9; transform: translateY(-2px); }
  .btn-icon { font-size: 1.3rem; }

  /* FLOATING BUTTONS */
  .floating-btns {
    position: fixed;
    bottom: 2rem; right: 1.5rem;
    display: flex; flex-direction: column; gap: 0.8rem;
    z-index: 200;
  }
  .float-btn {
    width: 52px; height: 52px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.3rem;
    text-decoration: none;
    color: #fff;
    box-shadow: 0 4px 20px rgba(0,0,0,0.4);
    transition: transform 0.2s;
  }
  .float-btn:hover { transform: scale(1.1); }
  .float-wa { background: #25D366; }
  .float-call { background: var(--accent); }

  /* FOOTER */
  footer {
    background: var(--bg);
    border-top: 1px solid var(--border);
    padding: 3rem 2rem;
    text-align: center;
  }
  .footer-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.5rem;
    background: linear-gradient(135deg, var(--accent), var(--green));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 1rem;
  }
  .footer-links { display: flex; gap: 2rem; justify-content: center; margin-bottom: 1.5rem; }
  .footer-links a { color: var(--muted); text-decoration: none; font-size: 0.9rem; transition: color 0.2s; }
  .footer-links a:hover { color: var(--text); }
  .footer-copy { color: var(--muted); font-size: 0.85rem; }

  /* SCROLL ANIMATIONS */
  .reveal {
    opacity: 0;
    transform: translateY(28px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* RESPONSIVE */
  @media (max-width: 900px) {
    .nav-links { display: none; }
    .hamburger { display: flex; }
    .about-inner, .contact-inner { grid-template-columns: 1fr; gap: 2.5rem; }
    .pricing-grid, .testimonials-grid { grid-template-columns: 1fr; }
    .about-visual { justify-content: flex-start; }
  }
  @media (max-width: 600px) {
    .hero h1 { font-size: 2.6rem; }
    .hero-stats { gap: 2rem; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">Arpit.</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#testimonials">Reviews</a></li>
    <li><a href="#contact" class="nav-cta">Hire Me</a></li>
  </ul>
  <div class="hamburger" onclick="toggleMenu()">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-grid"></div>
  <div class="hero-glow"></div>
  <div class="hero-content">
    <div class="hero-badge">Available for Projects</div>
    <h1>Professional <span class="highlight">Web Development</span> Services</h1>
    <p>I create fast, responsive, and modern websites that help businesses grow online — delivered on time, every time.</p>
    <div class="hero-btns">
      <a href="#pricing" class="btn-primary">View Pricing →</a>
      <a href="#contact" class="btn-outline">💬 Contact Me</a>
    </div>
    <div class="hero-stats">
      <div class="stat">
        <div class="stat-num">50+</div>
        <div class="stat-label">Projects Done</div>
      </div>
      <div class="stat">
        <div class="stat-num">3–5</div>
        <div class="stat-label">Day Delivery</div>
      </div>
      <div class="stat">
        <div class="stat-num">100%</div>
        <div class="stat-label">Client Satisfaction</div>
      </div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section class="about" id="about">
  <div class="container">
    <div class="about-inner">
      <div class="about-visual reveal">
        <div class="about-card">
          <div class="about-avatar">A</div>
          <h3>Arpit</h3>
          <div class="role">Freelance Web Developer</div>
          <p style="font-size:0.85rem;color:var(--muted);line-height:1.6;">Creating fast, modern, and SEO-friendly websites for businesses and individuals.</p>
          <div class="about-skills">
            <span class="skill-tag">HTML/CSS</span>
            <span class="skill-tag">JavaScript</span>
            <span class="skill-tag">Responsive</span>
            <span class="skill-tag">SEO</span>
            <span class="skill-tag">Performance</span>
          </div>
        </div>
      </div>
      <div class="about-text reveal">
        <div class="section-label">About Me</div>
        <h2 class="section-title">Building Websites That <span style="color:var(--accent)">Actually Work</span></h2>
        <p>Hi, I'm <strong>Arpit</strong>, a freelance web developer specializing in modern, responsive, and SEO-friendly websites.</p>
        <p>I help businesses and individuals build a <strong>strong online presence</strong> with professional web design and development — combining clean code, beautiful design, and fast performance.</p>
        <p>Every project gets personal attention. I don't just build websites — I build tools that help your business grow.</p>
        <a href="#contact" class="btn-primary" style="display:inline-flex;margin-top:1.5rem;">Let's Talk →</a>
      </div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing" id="pricing">
  <div class="container">
    <div class="pricing-header reveal">
      <div class="section-label">Packages</div>
      <h2 class="section-title">Simple, Transparent Pricing</h2>
      <p class="section-sub" style="margin:0 auto 1.5rem;">Choose a package that fits your needs. No hidden fees, no surprises.</p>
      <div class="pricing-toggle">
        <button class="toggle-btn active" onclick="switchPlan('no-domain', this)">Without Domain</button>
        <button class="toggle-btn" onclick="switchPlan('with-domain', this)">With Domain</button>
      </div>
    </div>

    <!-- WITHOUT DOMAIN -->
    <div class="pricing-plans" id="no-domain">
      <div class="pricing-grid">
        <div class="price-card reveal">
          <div class="price-tier">Starter</div>
          <div class="price-name">Basic</div>
          <div class="price-amount">₹1500<span></span></div>
          <div class="price-divider"></div>
          <ul class="price-features">
            <li>1–3 Pages Website</li>
            <li>Mobile Responsive</li>
            <li>Basic Design</li>
            <li>Contact Form</li>
            <li>Delivery in 3 Days</li>
          </ul>
          <a href="https://wa.me/919817005438?text=Hi Arpit, I'm interested in the Basic Package (₹1500)" class="price-btn price-btn-outline">Get Started</a>
        </div>
        <div class="price-card featured reveal">
          <div class="popular-badge">Popular</div>
          <div class="price-tier">Most Popular</div>
          <div class="price-name">Standard</div>
          <div class="price-amount">₹1800<span></span></div>
          <div class="price-divider"></div>
          <ul class="price-features">
            <li>3–5 Pages Website</li>
            <li>Mobile Responsive</li>
            <li>Modern UI Design</li>
            <li>Contact Form</li>
            <li>Basic SEO</li>
            <li>Delivery in 3–4 Days</li>
          </ul>
          <a href="https://wa.me/919817005438?text=Hi Arpit, I'm interested in the Standard Package (₹1800)" class="price-btn price-btn-solid">Get Started</a>
        </div>
        <div class="price-card reveal">
          <div class="price-tier">Best Value</div>
          <div class="price-name">Premium</div>
          <div class="price-amount">₹2000<span></span></div>
          <div class="price-divider"></div>
          <ul class="price-features">
            <li>5+ Pages Website</li>
            <li>Premium Design</li>
            <li>Mobile Responsive</li>
            <li>Contact Form</li>
            <li>Basic SEO Optimization</li>
            <li>Fast Performance</li>
            <li>Delivery in 4–5 Days</li>
          </ul>
          <a href="https://wa.me/919817005438?text=Hi Arpit, I'm interested in the Premium Package (₹2000)" class="price-btn price-btn-outline">Get Started</a>
        </div>
      </div>
    </div>

    <!-- WITH DOMAIN -->
    <div class="pricing-plans hidden" id="with-domain">
      <div class="pricing-grid">
        <div class="price-card reveal">
          <div class="price-tier">Starter</div>
          <div class="price-name">Basic</div>
          <div class="price-amount">₹2500<span></span></div>
          <div class="price-divider"></div>
          <ul class="price-features">
            <li>🌐 Domain Included</li>
            <li>1–3 Pages Website</li>
            <li>Mobile Responsive</li>
            <li>Contact Form</li>
          </ul>
          <a href="https://wa.me/919817005438?text=Hi Arpit, I'm interested in the Basic Package with Domain (₹2500)" class="price-btn price-btn-outline">Get Started</a>
        </div>
        <div class="price-card featured reveal">
          <div class="popular-badge">Popular</div>
          <div class="price-tier">Most Popular</div>
          <div class="price-name">Standard</div>
          <div class="price-amount">₹2800<span></span></div>
          <div class="price-divider"></div>
          <ul class="price-features">
            <li>🌐 Domain Included</li>
            <li>3–5 Pages Website</li>
            <li>Modern UI Design</li>
            <li>Contact Form</li>
            <li>Basic SEO</li>
          </ul>
          <a href="https://wa.me/919817005438?text=Hi Arpit, I'm interested in the Standard Package with Domain (₹2800)" class="price-btn price-btn-solid">Get Started</a>
        </div>
        <div class="price-card reveal">
          <div class="price-tier">Best Value</div>
          <div class="price-name">Premium</div>
          <div class="price-amount">₹3000<span></span></div>
          <div class="price-divider"></div>
          <ul class="price-features">
            <li>🌐 Domain Included</li>
            <li>5+ Pages Website</li>
            <li>Premium UI Design</li>
            <li>Contact Form</li>
            <li>SEO Optimization</li>
            <li>Performance Optimization</li>
          </ul>
          <a href="https://wa.me/919817005438?text=Hi Arpit, I'm interested in the Premium Package with Domain (₹3000)" class="price-btn price-btn-outline">Get Started</a>
        </div>
      </div>
    </div>
  </div>
</section>


<!-- TESTIMONIALS -->
<section class="testimonials" id="testimonials">
  <div class="container">
    <div class="testimonials-header reveal">
      <div class="section-label">Client Reviews</div>
      <h2 class="section-title">What Clients Say</h2>
      <p class="section-sub" style="margin:0 auto;">Real feedback from real clients. Your satisfaction is my priority.</p>
    </div>
    <div class="testimonials-grid">
      <div class="testimonial-card reveal">
        <div class="stars">★★★★★</div>
        <p class="testimonial-text">Arpit created an amazing website for my business. The design was modern and delivered right on time. Exceeded my expectations!</p>
        <div class="testimonial-author">
          <div class="author-avatar" style="background:linear-gradient(135deg,#5b6bff,#00e5a0);">RS</div>
          <div>
            <div class="author-name">Rahul Sharma</div>
            <div class="author-type">Business Owner</div>
          </div>
        </div>
      </div>
      <div class="testimonial-card reveal">
        <div class="stars">★★★★★</div>
        <p class="testimonial-text">Very professional developer. My website looks great and works perfectly on mobile. Great communication throughout the project.</p>
        <div class="testimonial-author">
          <div class="author-avatar" style="background:linear-gradient(135deg,#ff6b6b,#ffd166);">PM</div>
          <div>
            <div class="author-name">Priya Mehta</div>
            <div class="author-type">Entrepreneur</div>
          </div>
        </div>
      </div>
      <div class="testimonial-card reveal">
        <div class="stars">★★★★★</div>
        <p class="testimonial-text">Affordable pricing and excellent work quality. Delivered a stunning website that helped increase my online inquiries. Highly recommended!</p>
        <div class="testimonial-author">
          <div class="author-avatar" style="background:linear-gradient(135deg,#00e5a0,#5b6bff);">AV</div>
          <div>
            <div class="author-name">Aman Verma</div>
            <div class="author-type">Startup Founder</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="container">
    <div class="contact-inner">
      <div class="reveal">
        <div class="section-label">Get in Touch</div>
        <h2 class="section-title">Let's Build Something <span style="color:var(--accent)">Great Together</span></h2>
        <p class="section-sub">Ready to start your project? Reach out via WhatsApp, call, or email. I'll get back to you quickly.</p>
        <div class="contact-info">
          <div class="contact-item">
            <div class="contact-icon" style="background:rgba(255,107,107,0.1);">📧</div>
            <div class="contact-detail">
              <div class="label">Email</div>
              <a href="mailto:arpit981700@gmail.com">arpit981700@gmail.com</a>
            </div>
          </div>
          <div class="contact-item">
            <div class="contact-icon" style="background:rgba(91,107,255,0.1);">📞</div>
            <div class="contact-detail">
              <div class="label">Phone</div>
              <a href="tel:+919817005438">+91 9817005438</a>
            </div>
          </div>
        </div>
      </div>
      <div class="reveal">
        <div style="background:var(--card);border:1px solid var(--border);border-radius:20px;padding:2.5rem;position:relative;overflow:hidden;">
          <div style="position:absolute;top:0;left:0;right:0;height:3px;background:linear-gradient(90deg,var(--accent),var(--green));"></div>
          <h3 style="font-family:'Syne',sans-serif;font-size:1.3rem;font-weight:700;margin-bottom:0.5rem;">Ready to get started?</h3>
          <p style="color:var(--muted);font-size:0.9rem;margin-bottom:2rem;font-weight:300;line-height:1.6;">Click below to reach out. I'll respond within a few hours and we can discuss your project.</p>
          <div class="contact-btns">
            <a href="https://wa.me/919817005438?text=Hi Arpit, I want to discuss a web development project" class="wa-btn">
              <span class="btn-icon">💬</span>
              <div>
                <div style="font-size:0.75rem;opacity:0.8;font-weight:400;">Message on</div>
                <div>WhatsApp Chat</div>
              </div>
            </a>
            <a href="tel:+919817005438" class="call-btn">
              <span class="btn-icon">📞</span>
              <div>
                <div style="font-size:0.75rem;opacity:0.8;font-weight:400;">Give me a</div>
                <div>Call Now</div>
              </div>
            </a>
          </div>
          <p style="font-size:0.8rem;color:var(--muted);margin-top:1.5rem;text-align:center;">⚡ Usually responds within 2 hours</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Arpit.</div>
  <div class="footer-links">
    <a href="#home">Home</a>
    <a href="#pricing">Pricing</a>
    <a href="#contact">Contact</a>
  </div>
  <p class="footer-copy">© 2026 Arpit Web Development. All rights reserved.</p>
</footer>

<!-- FLOATING BUTTONS -->
<div class="floating-btns">
  <a href="https://wa.me/919817005438" class="float-btn float-wa" title="WhatsApp">💬</a>
  <a href="tel:+919817005438" class="float-btn float-call" title="Call Now">📞</a>
</div>

<script>
  // Pricing toggle
  function switchPlan(plan, btn) {
    document.querySelectorAll('.pricing-plans').forEach(el => el.classList.add('hidden'));
    document.getElementById(plan).classList.remove('hidden');
    document.querySelectorAll('.toggle-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
  }

  // Scroll reveal
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
      }
    });
  }, { threshold: 0.12 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // Mobile menu (simple toggle)
  function toggleMenu() {
    const links = document.querySelector('.nav-links');
    if (links.style.display === 'flex') {
      links.style.display = 'none';
    } else {
      links.style.cssText = 'display:flex;flex-direction:column;position:absolute;top:70px;left:0;right:0;background:var(--bg2);padding:1.5rem 2rem;border-bottom:1px solid var(--border);gap:1.2rem;';
    }
  }
</script>
</body>
</html>
