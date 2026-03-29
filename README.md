[Vatshal portfolio.html](https://github.com/user-attachments/files/26329643/Vatshal.portfolio.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Vatshal Modanwal | Data Scientist & Analyst</title>
  <link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;600;700&family=Orbitron:wght@700;900&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg:        #050d1a;
      --bg2:       #07122a;
      --aura:      #3b82f6;
      --aura2:     #60a5fa;
      --aura3:     #93c5fd;
      --glow:      rgba(59,130,246,0.35);
      --glow2:     rgba(59,130,246,0.12);
      --text:      #e2eeff;
      --muted:     #7a9cc7;
      --border:    rgba(59,130,246,0.28);
      --card:      rgba(7,18,42,0.85);
      --mono:      'Share Tech Mono', monospace;
      --display:   'Orbitron', sans-serif;
      --body-font: 'Rajdhani', sans-serif;
    }

    *, *::before, *::after { box-sizing:border-box; margin:0; padding:0; }
    html { scroll-behavior:smooth; }
    body {
      background:var(--bg); color:var(--text);
      font-family:var(--body-font); font-size:17px;
      line-height:1.7; overflow-x:hidden; cursor:none;
    }

    /* ── CUSTOM CURSOR ── */
    #cursor-dot {
      position:fixed; top:0; left:0; width:10px; height:10px;
      background:var(--aura2); border-radius:50%;
      pointer-events:none; z-index:99999;
      transform:translate(-50%,-50%);
      transition:transform .08s ease, opacity .1s, background .2s;
      box-shadow:0 0 8px var(--aura), 0 0 20px var(--glow);
    }
    #cursor-ring {
      position:fixed; top:0; left:0; width:36px; height:36px;
      border:2px solid var(--aura2); border-radius:50%;
      pointer-events:none; z-index:99998;
      transform:translate(-50%,-50%);
      transition:width .25s ease, height .25s ease, border-color .25s, transform .12s ease, opacity .2s;
      opacity:0.7;
    }
    #cursor-blink-bar {
      position:fixed; top:0; left:0; width:3px; height:20px;
      background:var(--aura2); border-radius:2px;
      pointer-events:none; z-index:99999;
      transform:translate(10px,-50%); opacity:0;
      box-shadow:0 0 8px var(--aura), 0 0 18px var(--glow);
      animation:cursorBlink .8s step-end infinite;
    }
    #cursor-blink-bar.visible { opacity:1; }
    @keyframes cursorBlink { 0%,100%{opacity:1} 50%{opacity:0} }
    body.hovering #cursor-ring { width:56px; height:56px; border-color:var(--aura3); opacity:1; }
    body.hovering #cursor-dot  { transform:translate(-50%,-50%) scale(0.5); background:var(--aura3); }
    a,button,input,textarea,.skill-card,.project-card,.stat-box,.contact-link,.btn,nav { cursor:none!important; }

    /* ── BACKGROUND ── */
    body::before {
      content:''; position:fixed; inset:0;
      background-image:
        linear-gradient(var(--border) 1px, transparent 1px),
        linear-gradient(90deg, var(--border) 1px, transparent 1px);
      background-size:50px 50px; opacity:.15;
      pointer-events:none; z-index:0;
    }
    .orb { position:fixed; border-radius:50%; filter:blur(90px); pointer-events:none; z-index:0; animation:floatOrb 12s ease-in-out infinite alternate; }
    .orb1{width:500px;height:500px;background:rgba(59,130,246,.13);top:-120px;right:-100px}
    .orb2{width:320px;height:320px;background:rgba(96,165,250,.09);bottom:5%;left:-80px;animation-delay:-5s}
    .orb3{width:220px;height:220px;background:rgba(147,197,253,.07);top:45%;right:18%;animation-delay:-8s}
    @keyframes floatOrb{from{transform:translateY(0)scale(1)}to{transform:translateY(40px)scale(1.06)}}

    /* ══════════════════════════════════
       SCROLL REVEAL SYSTEM
    ══════════════════════════════════ */
    /* Base reveal – slide up */
    .reveal {
      opacity:0;
      transform:translateY(55px);
      transition:opacity .7s cubic-bezier(.22,1,.36,1), transform .7s cubic-bezier(.22,1,.36,1);
    }
    .reveal.from-left  { transform:translateX(-65px); }
    .reveal.from-right { transform:translateX(65px); }
    .reveal.visible    { opacity:1!important; transform:none!important; }

    /* Pop-up bounce reveal */
    .pop-reveal {
      opacity:0;
      transform:translateY(50px) scale(.93);
      transition:opacity .65s cubic-bezier(.34,1.56,.64,1), transform .65s cubic-bezier(.34,1.56,.64,1);
    }
    .pop-reveal.visible { opacity:1; transform:none; }

    /* Stagger grid children */
    .stagger > * {
      opacity:0; transform:translateY(40px);
      transition:opacity .55s cubic-bezier(.22,1,.36,1), transform .55s cubic-bezier(.22,1,.36,1);
    }
    .stagger.visible > *:nth-child(1){opacity:1;transform:none;transition-delay:.04s}
    .stagger.visible > *:nth-child(2){opacity:1;transform:none;transition-delay:.13s}
    .stagger.visible > *:nth-child(3){opacity:1;transform:none;transition-delay:.22s}
    .stagger.visible > *:nth-child(4){opacity:1;transform:none;transition-delay:.31s}
    .stagger.visible > *:nth-child(5){opacity:1;transform:none;transition-delay:.40s}
    .stagger.visible > *:nth-child(6){opacity:1;transform:none;transition-delay:.49s}

    /* ── NAV ── */
    nav {
      position:fixed; top:0; left:0; right:0; z-index:1000;
      display:flex; align-items:center; justify-content:space-between;
      padding:0 6%; height:64px;
      background:rgba(5,13,26,.92); backdrop-filter:blur(18px);
      border-bottom:1px solid var(--border);
      transition:box-shadow .3s;
    }
    nav.scrolled { box-shadow:0 4px 30px rgba(59,130,246,.18); }
    .nav-logo {
      font-family:var(--display); font-size:1.1rem; color:var(--aura2);
      letter-spacing:2px; text-decoration:none; position:relative;
    }
    .nav-logo::after {
      content:''; position:absolute; bottom:-4px; left:0; right:0; height:2px;
      background:var(--aura2); transform:scaleX(0); transform-origin:left;
      transition:transform .3s ease; box-shadow:0 0 8px var(--aura);
    }
    .nav-logo:hover::after { transform:scaleX(1); }

    .nav-links { display:flex; gap:2rem; list-style:none; }
    .nav-links a {
      font-family:var(--mono); font-size:.78rem; color:var(--muted);
      text-decoration:none; letter-spacing:1px;
      position:relative; padding-bottom:4px;
      transition:color .3s;
    }
    /* slide-in underline */
    .nav-links a::after {
      content:''; position:absolute; bottom:0; left:0; width:100%; height:2px;
      background:linear-gradient(90deg,var(--aura),var(--aura3));
      transform:scaleX(0); transform-origin:left;
      transition:transform .3s cubic-bezier(.22,1,.36,1);
      border-radius:2px; box-shadow:0 0 8px var(--aura);
    }
    .nav-links a:hover,
    .nav-links a.active { color:var(--aura2); }
    .nav-links a:hover::after,
    .nav-links a.active::after { transform:scaleX(1); }

    /* ── LAYOUT ── */
    section { position:relative; z-index:1; }
    .container { max-width:1100px; margin:0 auto; padding:0 6%; }
    .section-tag { font-family:var(--mono); font-size:.75rem; color:var(--aura); letter-spacing:3px; margin-bottom:.5rem; }
    .section-title { font-family:var(--display); font-size:clamp(1.6rem,4vw,2.4rem); color:var(--text); margin-bottom:2.5rem; letter-spacing:1px; }
    .section-title span { color:var(--aura2); }
    .divider { height:1px; background:linear-gradient(90deg,transparent,var(--aura),transparent); margin:0 6%; opacity:.35; }

    /* ── HERO ── */
    #home { min-height:100vh; display:flex; align-items:center; padding-top:64px; }
    .hero-inner { display:flex; align-items:center; justify-content:space-between; gap:3rem; width:100%; }
    .hero-left { flex:1; }
    .hero-init { font-family:var(--mono); font-size:.78rem; color:var(--aura); letter-spacing:3px; margin-bottom:1.2rem; opacity:0; animation:fadeUp .8s .2s forwards; }
    .hero-name { font-family:var(--display); font-size:clamp(2.2rem,6vw,4rem); font-weight:900; line-height:1.1; margin-bottom:1rem; opacity:0; animation:fadeUp .8s .4s forwards; }
    .hero-name .first{color:var(--text)}.hero-name .last{color:var(--aura2)}
    .hero-role { font-family:var(--mono); font-size:1rem; color:var(--aura3); margin-bottom:1.4rem; opacity:0; animation:fadeUp .8s .6s forwards; }
    .hero-role::before { content:'> '; color:var(--aura); }
    .hero-bio { color:var(--muted); font-size:1rem; max-width:520px; margin-bottom:2rem; opacity:0; animation:fadeUp .8s .8s forwards; }
    .hero-btns { display:flex; gap:1rem; flex-wrap:wrap; opacity:0; animation:fadeUp .8s 1s forwards; }
    .hero-socials { display:flex; gap:1.2rem; margin-top:2rem; flex-wrap:wrap; opacity:0; animation:fadeUp .8s 1.2s forwards; }

    /* buttons */
    .btn {
      font-family:var(--mono); font-size:.8rem; letter-spacing:1.5px;
      padding:.7rem 1.6rem; border-radius:4px; text-decoration:none;
      position:relative; overflow:hidden; transition:all .3s; display:inline-block;
    }
    .btn::before {
      content:''; position:absolute; top:50%; left:50%; width:0; height:0;
      background:rgba(255,255,255,.15); border-radius:50%;
      transform:translate(-50%,-50%); transition:width .5s, height .5s;
    }
    .btn:hover::before { width:300px; height:300px; }
    .btn-primary { background:var(--aura); color:#fff; border:none; box-shadow:0 0 20px var(--glow); }
    .btn-primary:hover { background:var(--aura2); box-shadow:0 0 35px rgba(59,130,246,.6); transform:translateY(-3px); }
    .btn-outline { background:transparent; color:var(--aura2); border:1px solid var(--aura); }
    .btn-outline:hover { background:var(--glow2); transform:translateY(-3px); box-shadow:0 0 20px var(--glow2); }

    /* social links */
    .hero-socials a {
      font-family:var(--mono); font-size:.75rem; color:var(--muted);
      text-decoration:none; border:1px solid var(--border);
      padding:.4rem .9rem; border-radius:3px;
      position:relative; overflow:hidden; transition:all .3s;
    }
    .hero-socials a::before {
      content:''; position:absolute; bottom:0; left:0; width:100%; height:2px;
      background:linear-gradient(90deg,var(--aura),var(--aura3));
      transform:scaleX(0); transform-origin:left; transition:transform .3s ease;
    }
    .hero-socials a:hover { color:var(--aura2); border-color:var(--aura); background:var(--glow2); }
    .hero-socials a:hover::before { transform:scaleX(1); }

    /* profile */
    .hero-right { flex-shrink:0; opacity:0; animation:fadeIn 1s .6s forwards; }
    .profile-card { position:relative; width:280px; }
    .profile-img-wrap {
      width:240px; height:240px; border-radius:50%;
      border:3px solid var(--aura);
      box-shadow:0 0 40px var(--glow),0 0 80px rgba(59,130,246,.15);
      overflow:hidden; margin:0 auto; background:var(--bg2);
      display:flex; align-items:center; justify-content:center;
      animation:profilePulse 3s ease-in-out infinite;
    }
    @keyframes profilePulse{0%,100%{box-shadow:0 0 40px var(--glow),0 0 80px rgba(59,130,246,.15)}50%{box-shadow:0 0 65px rgba(59,130,246,.55),0 0 120px rgba(59,130,246,.25)}}
    .profile-placeholder { font-family:var(--display); font-size:4.5rem; color:var(--aura2); font-weight:900; }
    .profile-badge {
      position:absolute; bottom:10px; right:10px;
      background:var(--bg2); border:1px solid var(--aura);
      border-radius:6px; padding:.5rem .9rem;
      font-family:var(--mono); font-size:.7rem; color:var(--aura2);
      box-shadow:0 0 14px var(--glow); animation:badgePulse 2s ease-in-out infinite;
    }
    @keyframes badgePulse{0%,100%{opacity:1}50%{opacity:.7}}
    @keyframes fadeUp{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:none}}
    @keyframes fadeIn{from{opacity:0}to{opacity:1}}

    /* ── ABOUT ── */
    #about { padding:100px 0; }
    .about-grid { display:grid; grid-template-columns:1fr 1fr; gap:3rem; align-items:start; }
    .about-text p { color:var(--muted); margin-bottom:1rem; }
    .about-stats { display:grid; grid-template-columns:1fr 1fr; gap:1rem; margin-top:1.5rem; }
    .stat-box {
      background:var(--card); border:1px solid var(--border);
      border-radius:8px; padding:1.2rem; text-align:center;
      position:relative; overflow:hidden;
      transition:border-color .3s, box-shadow .3s, transform .3s;
    }
    .stat-box::before {
      content:''; position:absolute; bottom:0; left:0; width:100%; height:3px;
      background:linear-gradient(90deg,var(--aura),var(--aura3));
      transform:scaleX(0); transform-origin:left; transition:transform .4s ease;
    }
    .stat-box:hover { border-color:var(--aura); box-shadow:0 0 25px var(--glow2); transform:translateY(-4px); }
    .stat-box:hover::before { transform:scaleX(1); }
    .stat-num { font-family:var(--display); font-size:1.8rem; color:var(--aura2); font-weight:900; }
    .stat-label { font-family:var(--mono); font-size:.65rem; color:var(--muted); letter-spacing:1px; }

    .terminal {
      background:#050e1f; border:1px solid var(--border);
      border-radius:10px; overflow:hidden;
      box-shadow:0 0 30px var(--glow2); transition:box-shadow .3s;
    }
    .terminal:hover { box-shadow:0 0 50px rgba(59,130,246,.25); }
    .terminal-header { background:#0a1830; padding:.6rem 1rem; display:flex; align-items:center; gap:.5rem; border-bottom:1px solid var(--border); }
    .dot{width:12px;height:12px;border-radius:50%}.dot-r{background:#ff5f57}.dot-y{background:#febc2e}.dot-g{background:#28c840}
    .terminal-body { padding:1.4rem; font-family:var(--mono); font-size:.82rem; color:var(--text); line-height:2; }
    .t-prompt{color:var(--aura)}.t-cmd{color:var(--aura3)}.t-out{color:var(--muted)}
    .t-cursor{display:inline-block;width:8px;height:14px;background:var(--aura);animation:blink 1s step-end infinite;vertical-align:middle}
    @keyframes blink{50%{opacity:0}}

    /* ── EDUCATION ── */
    #education { padding:80px 0; }
    .edu-card {
      background:var(--card); border:1px solid var(--border);
      border-radius:10px; padding:2rem 2.5rem; max-width:700px;
      position:relative; overflow:hidden;
      transition:border-color .3s, box-shadow .3s, transform .3s;
    }
    .edu-card::after {
      content:''; position:absolute; top:0; left:0; width:4px; height:100%;
      background:linear-gradient(180deg,var(--aura),var(--aura3));
      transform:scaleY(0); transform-origin:top;
      transition:transform .4s cubic-bezier(.22,1,.36,1);
    }
    .edu-card:hover { border-color:var(--aura); box-shadow:0 0 35px var(--glow2); transform:translateY(-5px); }
    .edu-card:hover::after { transform:scaleY(1); }
    .edu-badge { font-family:var(--mono); font-size:.7rem; color:var(--aura); border:1px solid var(--aura); padding:.2rem .7rem; border-radius:3px; display:inline-block; margin-bottom:1rem; }
    .edu-degree { font-family:var(--display); font-size:1.3rem; color:var(--text); margin-bottom:.4rem; }
    .edu-uni { color:var(--aura2); font-size:1rem; margin-bottom:.5rem; }
    .edu-desc { color:var(--muted); font-size:.95rem; }

    /* ── SKILLS ── */
    #skills { padding:80px 0; }
    .skills-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(160px,1fr)); gap:1rem; }
    .skill-card {
      background:var(--card); border:1px solid var(--border);
      border-radius:8px; padding:1.4rem 1rem; text-align:center;
      position:relative; overflow:hidden;
      transition:all .35s cubic-bezier(.34,1.56,.64,1);
    }
    .skill-card::before {
      content:''; position:absolute; inset:0;
      background:radial-gradient(circle at center,rgba(59,130,246,.2),transparent 70%);
      opacity:0; transition:opacity .3s;
    }
    .skill-card:hover { border-color:var(--aura); box-shadow:0 0 28px var(--glow); transform:translateY(-8px) scale(1.05); }
    .skill-card:hover::before { opacity:1; }
    .skill-icon { font-size:2rem; margin-bottom:.5rem; transition:transform .3s; }
    .skill-card:hover .skill-icon { transform:scale(1.2) rotate(-6deg); }
    .skill-name { font-family:var(--mono); font-size:.8rem; color:var(--aura3); letter-spacing:1px; }

    /* ── PROJECTS ── */
    #projects { padding:80px 0; }
    .projects-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(320px,1fr)); gap:1.5rem; }
    .project-card {
      background:var(--card); border:1px solid var(--border);
      border-radius:10px; padding:1.8rem;
      display:flex; flex-direction:column;
      position:relative; overflow:hidden;
      transition:all .35s cubic-bezier(.22,1,.36,1);
    }
    /* animated shimmer top bar */
    .project-card::before {
      content:''; position:absolute; top:0; left:0; right:0; height:2px;
      background:linear-gradient(90deg,var(--aura),var(--aura3),var(--aura));
      background-size:200% 100%;
      transform:scaleX(0); transform-origin:left;
      transition:transform .4s ease;
      animation:shimmer 2.5s linear infinite paused;
    }
    .project-card:hover { border-color:var(--aura); box-shadow:0 8px 40px var(--glow2); transform:translateY(-6px); }
    .project-card:hover::before { transform:scaleX(1); animation-play-state:running; }
    @keyframes shimmer{0%{background-position:200% 0}100%{background-position:-200% 0}}

    .project-num { font-family:var(--mono); font-size:.68rem; color:var(--aura); letter-spacing:3px; margin-bottom:.8rem; }
    .project-title { font-family:var(--display); font-size:1.15rem; color:var(--text); margin-bottom:.8rem; }
    .project-desc { color:var(--muted); font-size:.93rem; flex:1; margin-bottom:1.2rem; }
    .project-tags { display:flex; flex-wrap:wrap; gap:.5rem; margin-bottom:1.2rem; }
    .tag {
      font-family:var(--mono); font-size:.68rem; color:var(--aura2);
      background:rgba(59,130,246,.1); border:1px solid rgba(59,130,246,.3);
      padding:.2rem .6rem; border-radius:3px;
      transition:background .2s, border-color .2s;
    }
    .tag:hover { background:rgba(59,130,246,.22); border-color:var(--aura2); }
    .project-links { display:flex; gap:.8rem; }
    /* slide-fill link button */
    .project-link {
      font-family:var(--mono); font-size:.72rem; color:var(--aura2);
      text-decoration:none; border:1px solid var(--border);
      padding:.35rem .8rem; border-radius:3px;
      position:relative; overflow:hidden; transition:color .3s, border-color .3s;
      z-index:1;
    }
    .project-link::before {
      content:''; position:absolute; inset:0;
      background:var(--aura); transform:translateX(-101%);
      transition:transform .3s cubic-bezier(.22,1,.36,1); z-index:-1;
    }
    .project-link:hover { border-color:var(--aura); color:#fff; }
    .project-link:hover::before { transform:none; }
    .wip { color:var(--muted); font-family:var(--mono); font-size:.7rem; padding:.35rem .8rem; border:1px dashed var(--border); border-radius:3px; }

    /* ── CONTACT ── */
    #contact { padding:80px 0 120px; }
    .contact-inner { display:grid; grid-template-columns:1fr 1fr; gap:3rem; }
    .contact-info p { color:var(--muted); margin-bottom:2rem; }
    .contact-links { display:flex; flex-direction:column; gap:.8rem; }
    .contact-link {
      font-family:var(--mono); font-size:.82rem; color:var(--muted);
      text-decoration:none; display:flex; align-items:center; gap:.7rem;
      border:1px solid var(--border); padding:.7rem 1rem; border-radius:6px;
      position:relative; overflow:hidden; transition:all .3s;
    }
    .contact-link::after {
      content:''; position:absolute; bottom:0; left:0; width:100%; height:2px;
      background:linear-gradient(90deg,var(--aura),var(--aura3));
      transform:scaleX(0); transform-origin:left; transition:transform .35s ease;
    }
    .contact-link:hover { color:var(--aura2); border-color:var(--aura); background:var(--glow2); transform:translateX(6px); }
    .contact-link:hover::after { transform:scaleX(1); }
    .contact-icon { font-size:1.1rem; }

    .contact-form { display:flex; flex-direction:column; gap:1rem; }
    .form-label { font-family:var(--mono); font-size:.7rem; color:var(--aura); letter-spacing:1px; margin-bottom:.3rem; display:block; }
    .form-input,.form-textarea {
      width:100%; background:var(--bg2); border:1px solid var(--border);
      border-radius:6px; padding:.75rem 1rem; color:var(--text);
      font-family:var(--body-font); font-size:.95rem; outline:none;
      transition:border-color .3s, box-shadow .3s;
    }
    .form-input:focus,.form-textarea:focus { border-color:var(--aura); box-shadow:0 0 16px var(--glow2); }
    .form-textarea { min-height:120px; resize:vertical; }
    .form-btn {
      font-family:var(--mono); font-size:.8rem; letter-spacing:2px;
      padding:.85rem; background:var(--aura); color:#fff;
      border:none; border-radius:6px; cursor:none;
      position:relative; overflow:hidden;
      transition:all .3s; box-shadow:0 0 20px var(--glow);
    }
    .form-btn::before {
      content:''; position:absolute; top:50%; left:50%; width:0; height:0;
      background:rgba(255,255,255,.2); border-radius:50%;
      transform:translate(-50%,-50%); transition:width .5s, height .5s;
    }
    .form-btn:hover { background:var(--aura2); box-shadow:0 0 35px rgba(59,130,246,.6); }
    .form-btn:hover::before { width:400px; height:400px; }

    /* ── FOOTER ── */
    footer { text-align:center; padding:1.5rem; font-family:var(--mono); font-size:.72rem; color:var(--muted); border-top:1px solid var(--border); position:relative; z-index:1; }

    /* ── RESPONSIVE ── */
    @media(max-width:768px){
      .hero-inner{flex-direction:column-reverse;text-align:center}
      .hero-btns,.hero-socials{justify-content:center}
      .about-grid,.contact-inner{grid-template-columns:1fr}
      .profile-card{width:200px}.profile-img-wrap{width:180px;height:180px}
    }
    @media(max-width:500px){ .nav-links{gap:1rem} .nav-links a{font-size:.68rem} }
  </style>
</head>
<body>

  <div class="orb orb1"></div>
  <div class="orb orb2"></div>
  <div class="orb orb3"></div>

  <!-- NAV -->
  <nav id="main-nav">
    <a href="#home" class="nav-logo">VM</a>
    <ul class="nav-links">
      <li><a href="#home"      data-section="home">home</a></li>
      <li><a href="#about"     data-section="about">about</a></li>
      <li><a href="#education" data-section="education">education</a></li>
      <li><a href="#skills"    data-section="skills">skills</a></li>
      <li><a href="#projects"  data-section="projects">projects</a></li>
      <li><a href="#contact"   data-section="contact">contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="home">
    <div class="container">
      <div class="hero-inner">
        <div class="hero-left">
          
          <h1 class="hero-name"><span class="first">Vatshal </span><br><span class="last">Modanwal</span></h1>
          <p class="hero-role">Data Scientist &amp; Data Analyst</p>
          <p class="hero-bio">A curious and hardworking learner focused on turning data into insights. Exploring programming, problem-solving, and growing step by step toward meaningful goals.</p>
          <div class="hero-btns">
            <a href="#projects" class="btn btn-primary">View Projects</a>
            <a href="#contact"  class="btn btn-outline">Contact Me</a>
          </div>
          <div class="hero-socials">
            <a href="https://github.com/vatshal18-rcb"target="_blank">GitHub</a>
            <a href="https://www.linkedin.com/in/vatshal-modanwal-773bb3389/"target="_blank">LinkedIn</a>
            <a href="mailto:vatshal098@gmail.com">Email</a>
          </div>
        </div>
        <div class="hero-right">
          <div class="profile-card">
            <div class="profile-img-wrap"><span class="profile-placeholder">VM</span></div>
            <div class="profile-badge">[ OPEN TO WORK ]</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- ABOUT -->
  <section id="about">
    <div class="container">
      <p class="section-tag reveal">// 01. ABOUT</p>
      <h2 class="section-title reveal">Who Am <span>I?</span></h2>
      <div class="about-grid">
        <div class="about-text reveal from-left">
          <p>I'm <strong style="color:var(--aura2)">Vatshal Modanwal</strong>, a curious and hardworking learner who thrives on improving skills every day. I enjoy exploring programming concepts like C++ and sharpening problem-solving techniques.</p>
          <p>I value clear explanations and clean, readable code. My focus is on learning and growing step by step — building a strong foundation in data science, analytics, and software development.</p>
          <p>Currently pursuing my BCA degree while diving deep into data structures, algorithms, and real-world data projects that challenge me to think differently.</p>
          <div class="about-stats stagger">
            <div class="stat-box"><div class="stat-num">6+</div><div class="stat-label">SKILLS LEARNED</div></div>
            <div class="stat-box"><div class="stat-num">2+</div><div class="stat-label">PROJECTS</div></div>
            <div class="stat-box"><div class="stat-num">BCA</div><div class="stat-label">PURSUING</div></div>
            <div class="stat-box"><div class="stat-num">100%</div><div class="stat-label">DEDICATION</div></div>
          </div>
        </div>
        <div class="terminal reveal from-right">
          <div class="terminal-header">
            <div class="dot dot-r"></div><div class="dot dot-y"></div><div class="dot dot-g"></div>
          </div>
          <div class="terminal-body">
            <div><span class="t-prompt">vatshal@data:~$</span> <span class="t-cmd">whoami</span></div>
            <div class="t-out">Vatshal_Modanwal</div><br>
            <div><span class="t-prompt">vatshal@data:~$</span> <span class="t-cmd">cat role.txt</span></div>
            <div class="t-out">Data Scientist | Data Analyst</div><br>
            <div><span class="t-prompt">vatshal@data:~$</span> <span class="t-cmd">cat interests.txt</span></div>
            <div class="t-out">Data Analysis, ML, DSA, Python</div><br>
            <div><span class="t-prompt">vatshal@data:~$</span> <span class="t-cmd">echo $STATUS</span></div>
            <div class="t-out">ACTIVELY LEARNING &amp; GROWING</div><br>
            <div><span class="t-prompt">vatshal@data:~$</span> <span class="t-cursor"></span></div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- EDUCATION -->
  <section id="education">
    <div class="container">
      <p class="section-tag reveal">// 02. EDUCATION</p>
      <h2 class="section-title reveal">Academic <span>Journey</span></h2>
      <div class="edu-card pop-reveal">
        <span class="edu-badge">CURRENT</span>
        <div class="edu-degree">Bachelor of Computer Applications (BCA)</div>
        <div class="edu-uni">Dr. Hari Singh Gour University &nbsp;|&nbsp; 2025 – 2028</div>
        <p class="edu-desc">Pursuing BCA with a focus on data science, programming fundamentals, and analytical thinking. Building a strong base in computer science while exploring real-world data applications.</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- SKILLS -->
  <section id="skills">
    <div class="container">
      <p class="section-tag reveal">// 03. SKILLS</p>
      <h2 class="section-title reveal">My <span>Arsenal</span></h2>
      <div class="skills-grid stagger">
        <div class="skill-card"><div class="skill-icon">⚙️</div><div class="skill-name">C</div></div>
        <div class="skill-card"><div class="skill-icon">💻</div><div class="skill-name">C++</div></div>
        <div class="skill-card"><div class="skill-icon">🧠</div><div class="skill-name">DSA</div></div>
        <div class="skill-card"><div class="skill-icon">🌐</div><div class="skill-name">HTML &amp; CSS</div></div>
        <div class="skill-card"><div class="skill-icon">☕</div><div class="skill-name">Java</div></div>
        <div class="skill-card"><div class="skill-icon">🧹</div><div class="skill-name">Data Cleaning</div></div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="container">
      <p class="section-tag reveal">// 04. PROJECTS</p>
      <h2 class="section-title reveal">My <span>Operations</span></h2>
      <div class="projects-grid">
        <div class="project-card pop-reveal" style="transition-delay:.05s">
          <div class="project-num">// PROJECT_01</div>
          <div class="project-title">Library Management System</div>
          <p class="project-desc">A system to manage library operations including book records, member management, issue/return tracking, and fine calculation. Built with clean logic and structured data handling.</p>
          <div class="project-tags"><span class="tag">C++</span><span class="tag">DSA</span><span class="tag">File Handling</span></div>
          <div class="project-links"><span class="wip">LINK PENDING</span></div>
        </div>
        <div class="project-card pop-reveal" style="transition-delay:.18s">
          <div class="project-num">// PROJECT_02</div>
          <div class="project-title">Data Cleaning Pipeline</div>
          <p class="project-desc">A data preprocessing and cleaning workflow that handles missing values, duplicate removal, outlier detection, and data formatting to prepare datasets for analysis.</p>
          <div class="project-tags"><span class="tag">Python</span><span class="tag">Data Analysis</span><span class="tag">Pandas</span></div>
          <div class="project-links"><span class="wip">IN PROGRESS</span></div>
        </div>
      </div>
    </div>
  </section>

  <div class="divider"></div>

  <!-- CONTACT -->
  <section id="contact">
    <div class="container">
      <p class="section-tag reveal">// 05. CONTACT</p>
      <h2 class="section-title reveal">Get In <span>Touch</span></h2>
      <div class="contact-inner">
        <div class="contact-info reveal from-left">
          <p>Whether you want to collaborate on a data project, discuss analytics concepts, or just connect — my inbox is always open. Let's build something meaningful together.</p>
          <div class="contact-links">
            <a href="mailto:#" class="contact-link"><span class="contact-icon">📧</span> vatshal098@gmail.com</a>
            <a href="#"        class="contact-link"><span class="contact-icon">🐙</span> github.com/vatshal</a>
            <a href="#"        class="contact-link"><span class="contact-icon">💼</span> linkedin.com/in/vatshal</a>
          </div>
        </div>
        <div class="contact-form reveal from-right">
          <div>
            <label class="form-label">// YOUR NAME</label>
            <input type="text" class="form-input" placeholder="Enter your name"/>
          </div>
          <div>
            <label class="form-label">// EMAIL ADDRESS</label>
            <input type="email" class="form-input" placeholder="Enter your email"/>
          </div>
          <div>
            <label class="form-label">// MESSAGE</label>
            <textarea class="form-textarea" placeholder="Write your message..."></textarea>
          </div>
          <button class="form-btn">SEND MESSAGE</button>
        </div>
      </div>
    </div>
  </section>

  <footer>Designed &amp; Built by Vatshal Modanwal &nbsp;|&nbsp; 2025 &nbsp;|&nbsp; Keep Learning 📊</footer>

  <!-- CURSOR -->
  <div id="cursor-dot"></div>
  <div id="cursor-ring"></div>
  <div id="cursor-blink-bar"></div>

  <script>
    /* ── CURSOR ── */
    const dot=document.getElementById('cursor-dot'),ring=document.getElementById('cursor-ring'),bar=document.getElementById('cursor-blink-bar');
    let mx=0,my=0,rx=0,ry=0;
    document.addEventListener('mousemove',e=>{
      mx=e.clientX;my=e.clientY;
      dot.style.left=mx+'px';dot.style.top=my+'px';
      bar.style.left=mx+'px';bar.style.top=my+'px';
    });
    (function loop(){rx+=(mx-rx)*.12;ry+=(my-ry)*.12;ring.style.left=rx+'px';ring.style.top=ry+'px';requestAnimationFrame(loop)})();
    document.querySelectorAll('a,button,input,textarea,.skill-card,.project-card,.stat-box,.contact-link,.btn,.edu-card,.nav-links li').forEach(el=>{
      el.addEventListener('mouseenter',()=>{document.body.classList.add('hovering');bar.classList.add('visible');});
      el.addEventListener('mouseleave',()=>{document.body.classList.remove('hovering');bar.classList.remove('visible');});
    });
    document.addEventListener('mouseleave',()=>{dot.style.opacity='0';ring.style.opacity='0';bar.classList.remove('visible');});
    document.addEventListener('mouseenter',()=>{dot.style.opacity='1';ring.style.opacity='0.7';});
    document.addEventListener('mousedown',()=>{ring.style.transform='translate(-50%,-50%) scale(.75)';});
    document.addEventListener('mouseup',  ()=>{ring.style.transform='translate(-50%,-50%) scale(1)';});

    /* ── SCROLL REVEAL ── */
    const obs = new IntersectionObserver(entries=>{
      entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('visible'); obs.unobserve(e.target); } });
    },{threshold:.13, rootMargin:'0px 0px -40px 0px'});
    document.querySelectorAll('.reveal,.pop-reveal,.stagger').forEach(el=>obs.observe(el));

    /* ── NAV ACTIVE HIGHLIGHT ── */
    const sections = document.querySelectorAll('section[id]');
    const navLinks = document.querySelectorAll('.nav-links a[data-section]');
    const mainNav  = document.getElementById('main-nav');

    const navObs = new IntersectionObserver(entries=>{
      entries.forEach(e=>{
        if(e.isIntersecting){
          navLinks.forEach(a=>a.classList.remove('active'));
          const a=document.querySelector(`.nav-links a[data-section="${e.target.id}"]`);
          if(a) a.classList.add('active');
        }
      });
    },{threshold:.4});
    sections.forEach(s=>navObs.observe(s));

    window.addEventListener('scroll',()=>{ mainNav.classList.toggle('scrolled',scrollY>40); });
  </script>
</body>
</html>
