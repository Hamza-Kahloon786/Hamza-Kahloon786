<!DOCTYPE html>
<html>
<head>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap');

  *{box-sizing:border-box;margin:0;padding:0}
  :root{
    --bg:#050508;
    --bg2:#0c0c14;
    --bg3:#12121e;
    --border:#ffffff12;
    --border2:#ffffff22;
    --purple:#7f77dd;
    --purple2:#534ab7;
    --purple3:#afa9ec;
    --purple4:#cecbf6;
    --text:#e8e6ff;
    --muted:#8884aa;
    --faint:#3d3a5c;
    --green:#1de9a4;
    --amber:#f5a623;
  }
  body{
    background:var(--bg);
    color:var(--text);
    font-family:'Syne',sans-serif;
    font-size:14px;
    line-height:1.6;
    overflow-x:hidden;
    padding-bottom:60px;
  }
  .mono{font-family:'Space Mono',monospace}

  /* HEADER */
  .header{
    position:relative;
    padding:60px 40px 50px;
    border-bottom:1px solid var(--border);
    overflow:hidden;
    text-align:center;
  }
  .header-grid{
    position:absolute;inset:0;
    background-image:
      linear-gradient(var(--border) 1px,transparent 1px),
      linear-gradient(90deg,var(--border) 1px,transparent 1px);
    background-size:40px 40px;
    mask-image:radial-gradient(ellipse 80% 80% at 50% 50%,black 30%,transparent 100%);
  }
  .header-glow{
    position:absolute;
    width:500px;height:300px;
    background:radial-gradient(ellipse,#534ab755 0%,transparent 70%);
    left:50%;top:50%;transform:translate(-50%,-60%);
    pointer-events:none;
  }
  .status-pill{
    display:inline-flex;align-items:center;gap:6px;
    background:#0f1a14;border:1px solid #1de9a430;
    color:var(--green);font-family:'Space Mono',monospace;
    font-size:10px;padding:4px 12px;border-radius:100px;
    margin-bottom:24px;letter-spacing:1px;
    position:relative;z-index:1;
  }
  .status-dot{
    width:6px;height:6px;border-radius:50%;
    background:var(--green);
    animation:pulse 2s ease-in-out infinite;
  }
  @keyframes pulse{0%,100%{opacity:1}50%{opacity:0.3}}
  h1{
    font-size:56px;font-weight:800;
    letter-spacing:-2px;line-height:1;
    position:relative;z-index:1;
    background:linear-gradient(135deg,#ffffff 0%,var(--purple4) 50%,var(--purple) 100%);
    -webkit-background-clip:text;-webkit-text-fill-color:transparent;
    background-clip:text;
    margin-bottom:10px;
  }
  .role-line{
    font-family:'Space Mono',monospace;
    font-size:11px;letter-spacing:3px;
    color:var(--muted);text-transform:uppercase;
    position:relative;z-index:1;margin-bottom:28px;
  }
  .header-badges{
    display:flex;flex-wrap:wrap;gap:8px;
    justify-content:center;position:relative;z-index:1;
  }
  .badge{
    display:inline-flex;align-items:center;gap:5px;
    padding:6px 14px;border-radius:6px;
    font-size:11px;font-family:'Space Mono',monospace;
    border:1px solid var(--border2);
    background:var(--bg2);
    color:var(--muted);
    text-decoration:none;
    transition:all 0.2s;cursor:pointer;
  }
  .badge:hover{border-color:var(--purple);color:var(--purple3);background:#1a1830}
  .badge-dot{width:5px;height:5px;border-radius:50%}

  /* METRICS */
  .metrics{
    display:grid;grid-template-columns:repeat(6,1fr);
    gap:1px;background:var(--border);
    border-top:1px solid var(--border);
    border-bottom:1px solid var(--border);
  }
  .metric{
    background:var(--bg);
    padding:24px 16px;text-align:center;
  }
  .metric-val{
    font-size:26px;font-weight:800;
    color:#fff;letter-spacing:-1px;
    display:block;
  }
  .metric-val span{color:var(--purple)}
  .metric-label{
    font-family:'Space Mono',monospace;
    font-size:9px;letter-spacing:1.5px;
    color:var(--muted);text-transform:uppercase;
    margin-top:4px;
  }

  /* MAIN CONTENT */
  .content{padding:0 40px;max-width:860px;margin:0 auto}

  /* SECTION HEADERS */
  .section{margin-top:52px}
  .section-head{
    display:flex;align-items:center;gap:12px;
    margin-bottom:24px;
    padding-bottom:12px;
    border-bottom:1px solid var(--border);
  }
  .section-tag{
    font-family:'Space Mono',monospace;
    font-size:10px;letter-spacing:2px;
    color:var(--purple);text-transform:uppercase;
    background:#130f2a;border:1px solid #534ab755;
    padding:3px 10px;border-radius:4px;
  }
  .section-title{
    font-size:13px;font-weight:700;
    color:var(--muted);letter-spacing:1px;
    text-transform:uppercase;
  }
  .section-line{flex:1;height:1px;background:var(--border)}

  /* WHO AM I */
  .whoami-block{
    background:var(--bg2);
    border:1px solid var(--border);
    border-radius:10px;
    overflow:hidden;
  }
  .code-bar{
    display:flex;align-items:center;gap:8px;
    padding:10px 16px;
    background:var(--bg3);
    border-bottom:1px solid var(--border);
  }
  .code-dot{width:10px;height:10px;border-radius:50%}
  .code-dot.r{background:#ff5f57}.code-dot.y{background:#febc2e}.code-dot.g{background:#28c840}
  .code-filename{
    font-family:'Space Mono',monospace;font-size:10px;
    color:var(--muted);margin-left:8px;
  }
  .code-body{
    padding:20px 24px;
    font-family:'Space Mono',monospace;
    font-size:12px;line-height:2;
  }
  .c-k{color:#c084fc}
  .c-v{color:var(--purple4)}
  .c-s{color:#34d399}
  .c-n{color:#f9a8d4}
  .c-c{color:var(--muted);font-style:italic}

  /* TABS */
  .tab-nav{
    display:flex;gap:0;
    border:1px solid var(--border);border-radius:8px;
    overflow:hidden;margin-bottom:20px;
  }
  .tab-btn{
    flex:1;padding:10px;
    background:transparent;border:none;
    color:var(--muted);font-family:'Syne',sans-serif;
    font-size:11px;font-weight:700;letter-spacing:1px;
    text-transform:uppercase;cursor:pointer;
    border-right:1px solid var(--border);
    transition:all 0.15s;
  }
  .tab-btn:last-child{border-right:none}
  .tab-btn.active{background:var(--bg3);color:var(--purple3)}
  .tab-btn:hover:not(.active){background:#0d0d18;color:var(--text)}
  .tab-panel{display:none}
  .tab-panel.active{display:block}

  /* SKILL ROWS */
  .skill-group{margin-bottom:20px}
  .skill-group-label{
    font-family:'Space Mono',monospace;font-size:9px;
    letter-spacing:2px;color:var(--faint);
    text-transform:uppercase;margin-bottom:10px;
  }
  .skill-chips{display:flex;flex-wrap:wrap;gap:6px}
  .chip{
    display:inline-flex;align-items:center;gap:6px;
    padding:5px 12px;border-radius:5px;
    font-size:11px;font-family:'Space Mono',monospace;
    border:1px solid var(--border2);
    color:var(--muted);background:var(--bg2);
    transition:all 0.15s;
  }
  .chip:hover{border-color:var(--purple2);color:var(--purple3);background:#141228}
  .chip-dot{width:5px;height:5px;border-radius:50%;flex-shrink:0}
  .expert .chip-dot{background:#1de9a4}
  .advanced .chip-dot{background:#7f77dd}
  .intermediate .chip-dot{background:#534ab7}

  /* SKILL BARS */
  .skill-bar-row{
    display:grid;grid-template-columns:100px 1fr 36px;
    align-items:center;gap:12px;margin-bottom:10px;
  }
  .skill-bar-label{font-size:11px;color:var(--muted);font-family:'Space Mono',monospace}
  .skill-bar-track{
    height:3px;background:var(--bg3);
    border-radius:2px;overflow:hidden;
  }
  .skill-bar-fill{
    height:100%;border-radius:2px;
    background:linear-gradient(90deg,var(--purple2),var(--purple3));
    transform-origin:left;
    animation:growbar 1s cubic-bezier(0.4,0,0.2,1) both;
  }
  @keyframes growbar{from{transform:scaleX(0)}to{transform:scaleX(1)}}
  .skill-bar-pct{font-size:10px;color:var(--faint);font-family:'Space Mono',monospace;text-align:right}

  /* PROJECTS */
  .project-card{
    border:1px solid var(--border);
    border-radius:10px;background:var(--bg2);
    padding:24px;margin-bottom:12px;
    transition:all 0.2s;cursor:default;
    position:relative;overflow:hidden;
  }
  .project-card::before{
    content:'';position:absolute;
    top:0;left:0;right:0;height:2px;
    background:linear-gradient(90deg,var(--purple2),var(--purple3),transparent);
    opacity:0;transition:opacity 0.2s;
  }
  .project-card:hover{border-color:var(--border2);background:#0f0f1c}
  .project-card:hover::before{opacity:1}
  .project-header{display:flex;align-items:flex-start;justify-content:space-between;gap:16px;margin-bottom:10px}
  .project-title{font-size:15px;font-weight:700;color:#fff}
  .project-live{
    font-family:'Space Mono',monospace;font-size:9px;
    letter-spacing:1px;color:var(--green);
    background:#0a1a12;border:1px solid #1de9a420;
    padding:3px 8px;border-radius:4px;flex-shrink:0;
    text-transform:uppercase;
  }
  .project-desc{font-size:12px;color:var(--muted);line-height:1.7;margin-bottom:14px}
  .project-tags{display:flex;flex-wrap:wrap;gap:5px;margin-bottom:16px}
  .project-tag{
    font-family:'Space Mono',monospace;font-size:9px;
    letter-spacing:1px;padding:2px 8px;border-radius:3px;
    background:#1a1838;border:1px solid var(--purple2);
    color:var(--purple3);
  }
  .project-stats{
    display:flex;gap:16px;padding-top:14px;
    border-top:1px solid var(--border);
  }
  .project-stat{text-align:center}
  .project-stat-val{font-size:16px;font-weight:800;color:#fff;display:block}
  .project-stat-key{font-size:9px;font-family:'Space Mono',monospace;color:var(--muted);letter-spacing:1px}

  /* TIMELINE */
  .timeline{position:relative;padding-left:24px}
  .timeline::before{
    content:'';position:absolute;
    left:0;top:4px;bottom:4px;
    width:1px;background:var(--border2);
  }
  .timeline-item{position:relative;margin-bottom:28px}
  .timeline-dot{
    position:absolute;left:-29px;top:3px;
    width:11px;height:11px;border-radius:50%;
    border:2px solid var(--bg);
    background:var(--purple2);
  }
  .timeline-dot.active{background:var(--purple);box-shadow:0 0 0 4px #7f77dd22}
  .timeline-year{
    font-family:'Space Mono',monospace;font-size:9px;
    letter-spacing:2px;color:var(--purple);
    text-transform:uppercase;margin-bottom:4px;
  }
  .timeline-title{font-size:13px;font-weight:700;color:#fff;margin-bottom:4px}
  .timeline-sub{font-size:11px;color:var(--muted)}

  /* CERTS */
  .cert-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px}
  .cert-card{
    background:var(--bg2);border:1px solid var(--border);
    border-radius:8px;padding:14px 16px;
    display:flex;align-items:center;gap:12px;
  }
  .cert-icon{
    width:32px;height:32px;border-radius:6px;
    background:#1a1838;display:flex;align-items:center;justify-content:center;
    font-size:14px;flex-shrink:0;
  }
  .cert-name{font-size:11px;font-weight:700;color:var(--text);margin-bottom:2px}
  .cert-org{font-size:10px;font-family:'Space Mono',monospace;color:var(--muted)}
  .cert-year{
    font-family:'Space Mono',monospace;font-size:9px;
    color:var(--purple);margin-left:auto;flex-shrink:0;
  }

  /* CONNECT */
  .connect-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px}
  .connect-card{
    background:var(--bg2);border:1px solid var(--border);
    border-radius:8px;padding:16px;
    display:flex;align-items:center;gap:12px;
    transition:all 0.2s;
  }
  .connect-card:hover{border-color:var(--purple2);background:#0f0f1c}
  .connect-icon{
    width:36px;height:36px;border-radius:8px;
    display:flex;align-items:center;justify-content:center;
    font-size:16px;flex-shrink:0;
  }
  .connect-channel{font-size:11px;font-weight:700;color:var(--text);margin-bottom:2px}
  .connect-val{font-size:10px;font-family:'Space Mono',monospace;color:var(--muted)}
  .connect-resp{
    margin-left:auto;font-family:'Space Mono',monospace;
    font-size:9px;color:var(--green);
    background:#0a1a12;border:1px solid #1de9a420;
    padding:2px 7px;border-radius:3px;flex-shrink:0;
  }

  /* FOOTER */
  .footer{
    margin-top:60px;
    padding:40px;
    text-align:center;
    border-top:1px solid var(--border);
  }
  .quote{
    font-size:18px;font-weight:700;
    color:var(--purple4);line-height:1.5;
    max-width:500px;margin:0 auto 24px;
  }
  .quote em{color:var(--purple3);font-style:normal}
  .footer-name{
    font-family:'Space Mono',monospace;font-size:10px;
    color:var(--muted);letter-spacing:2px;
  }
</style>
</head>
<body>

<!-- HEADER -->
<div class="header">
  <div class="header-grid"></div>
  <div class="header-glow"></div>
  <div class="status-pill">
    <span class="status-dot"></span>
    AVAILABLE FOR HIRE · LAHORE, PAKISTAN
  </div>
  <h1>Hamza Kahloon</h1>
  <div class="role-line">Full Stack Developer &nbsp;·&nbsp; AI/ML Engineer &nbsp;·&nbsp; Problem Architect</div>
  <div class="header-badges">
    <span class="badge"><span class="badge-dot" style="background:#7f77dd"></span>Inter Tech Global</span>
    <span class="badge"><span class="badge-dot" style="background:#1de9a4"></span>4+ Years Experience</span>
    <span class="badge"><span class="badge-dot" style="background:#f5a623"></span>BS Software Engineering</span>
    <span class="badge"><span class="badge-dot" style="background:#c084fc"></span>University of Lahore · 3.3 GPA</span>
    <span class="badge"><span class="badge-dot" style="background:#34d399"></span>98% On-Time Rate</span>
  </div>
</div>

<!-- METRICS -->
<div class="metrics">
  <div class="metric">
    <span class="metric-val">25<span>+</span></span>
    <div class="metric-label">Projects</div>
  </div>
  <div class="metric">
    <span class="metric-val">92<span>%</span></span>
    <div class="metric-label">AI Accuracy</div>
  </div>
  <div class="metric">
    <span class="metric-val">1K<span>+</span></span>
    <div class="metric-label">Daily Users</div>
  </div>
  <div class="metric">
    <span class="metric-val">4.9<span>/5</span></span>
    <div class="metric-label">Client Rating</div>
  </div>
  <div class="metric">
    <span class="metric-val">10<span>+</span></span>
    <div class="metric-label">Countries</div>
  </div>
  <div class="metric">
    <span class="metric-val">500<span>+</span></span>
    <div class="metric-label">GitHub Stars</div>
  </div>
</div>

<div class="content">

  <!-- WHO AM I -->
  <div class="section">
    <div class="section-head">
      <span class="section-tag">01</span>
      <span class="section-title">Identity</span>
      <span class="section-line"></span>
    </div>
    <div class="whoami-block">
      <div class="code-bar">
        <span class="code-dot r"></span><span class="code-dot y"></span><span class="code-dot g"></span>
        <span class="code-filename">hamza.config.ts</span>
      </div>
      <div class="code-body">
        <span class="c-k">const</span> <span class="c-s">hamza</span> = {<br>
        &nbsp;&nbsp;<span class="c-n">role</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;: <span class="c-v">"Full Stack Developer · AI/ML Engineer"</span>,<br>
        &nbsp;&nbsp;<span class="c-n">company</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;: <span class="c-v">"Inter Tech Global"</span>,<br>
        &nbsp;&nbsp;<span class="c-n">location</span>&nbsp;&nbsp;&nbsp;&nbsp;: <span class="c-v">"Lahore, Punjab, Pakistan 🇵🇰"</span>,<br>
        &nbsp;&nbsp;<span class="c-n">experience</span>&nbsp;&nbsp;: <span class="c-v">"4+ years · 25+ production apps"</span>,<br>
        &nbsp;&nbsp;<span class="c-n">ai_focus</span>&nbsp;&nbsp;&nbsp;: [<span class="c-v">"GPT-4o"</span>, <span class="c-v">"YOLOv8"</span>, <span class="c-v">"RAG"</span>, <span class="c-v">"Voice AI"</span>],<br>
        &nbsp;&nbsp;<span class="c-n">availability</span>: <span class="c-v">"Freelance &amp; Full-time"</span>,<br>
        &nbsp;&nbsp;<span class="c-n">contact</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;: <span class="c-v">"hamzaakahloon903@gmail.com"</span>,<br>
        &nbsp;&nbsp;<span class="c-c">// "Code is poetry written in logic — AI is the rhythm that makes it dance."</span><br>
        };
      </div>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="section-head">
      <span class="section-tag">02</span>
      <span class="section-title">Tech Stack</span>
      <span class="section-line"></span>
    </div>

    <div class="tab-nav">
      <button class="tab-btn active" onclick="switchTab(this,'lang')">Languages</button>
      <button class="tab-btn" onclick="switchTab(this,'fe')">Frontend</button>
      <button class="tab-btn" onclick="switchTab(this,'be')">Backend</button>
      <button class="tab-btn" onclick="switchTab(this,'ai')">AI / Voice</button>
      <button class="tab-btn" onclick="switchTab(this,'infra')">Infra</button>
    </div>

    <div id="tab-lang" class="tab-panel active">
      <div style="margin-bottom:20px">
        <div class="skill-bar-row"><span class="skill-bar-label">Python</span><div class="skill-bar-track"><div class="skill-bar-fill" style="width:95%"></div></div><span class="skill-bar-pct">95%</span></div>
        <div class="skill-bar-row"><span class="skill-bar-label">JavaScript</span><div class="skill-bar-track"><div class="skill-bar-fill" style="width:90%;animation-delay:0.1s"></div></div><span class="skill-bar-pct">90%</span></div>
        <div class="skill-bar-row"><span class="skill-bar-label">TypeScript</span><div class="skill-bar-track"><div class="skill-bar-fill" style="width:82%;animation-delay:0.2s"></div></div><span class="skill-bar-pct">82%</span></div>
        <div class="skill-bar-row"><span class="skill-bar-label">Java</span><div class="skill-bar-track"><div class="skill-bar-fill" style="width:85%;animation-delay:0.3s"></div></div><span class="skill-bar-pct">85%</span></div>
        <div class="skill-bar-row"><span class="skill-bar-label">C++</span><div class="skill-bar-track"><div class="skill-bar-fill" style="width:80%;animation-delay:0.4s"></div></div><span class="skill-bar-pct">80%</span></div>
        <div class="skill-bar-row"><span class="skill-bar-label">PHP</span><div class="skill-bar-track"><div class="skill-bar-fill" style="width:70%;animation-delay:0.5s"></div></div><span class="skill-bar-pct">70%</span></div>
      </div>
    </div>

    <div id="tab-fe" class="tab-panel">
      <div class="skill-group"><div class="skill-group-label">Expert</div><div class="skill-chips expert"><span class="chip"><span class="chip-dot"></span>React.js</span><span class="chip"><span class="chip-dot"></span>Next.js</span><span class="chip"><span class="chip-dot"></span>Tailwind CSS</span><span class="chip"><span class="chip-dot"></span>Redux</span></div></div>
      <div class="skill-group"><div class="skill-group-label">Advanced</div><div class="skill-chips advanced"><span class="chip"><span class="chip-dot"></span>Three.js / R3F</span><span class="chip"><span class="chip-dot"></span>Mapbox GL JS</span><span class="chip"><span class="chip-dot"></span>HTML5 / CSS3</span><span class="chip"><span class="chip-dot"></span>Framer Motion</span></div></div>
      <div class="skill-group"><div class="skill-group-label">Intermediate</div><div class="skill-chips intermediate"><span class="chip"><span class="chip-dot"></span>Flutter</span><span class="chip"><span class="chip-dot"></span>Vue.js</span><span class="chip"><span class="chip-dot"></span>GraphQL</span></div></div>
    </div>

    <div id="tab-be" class="tab-panel">
      <div class="skill-group"><div class="skill-group-label">Expert</div><div class="skill-chips expert"><span class="chip"><span class="chip-dot"></span>Node.js</span><span class="chip"><span class="chip-dot"></span>FastAPI</span><span class="chip"><span class="chip-dot"></span>Express.js</span></div></div>
      <div class="skill-group"><div class="skill-group-label">Advanced</div><div class="skill-chips advanced"><span class="chip"><span class="chip-dot"></span>Django</span><span class="chip"><span class="chip-dot"></span>Flask</span><span class="chip"><span class="chip-dot"></span>REST APIs</span><span class="chip"><span class="chip-dot"></span>WebSocket</span></div></div>
      <div class="skill-group"><div class="skill-group-label">Intermediate</div><div class="skill-chips intermediate"><span class="chip"><span class="chip-dot"></span>Spring Boot</span><span class="chip"><span class="chip-dot"></span>Laravel</span><span class="chip"><span class="chip-dot"></span>gRPC</span></div></div>
    </div>

    <div id="tab-ai" class="tab-panel">
      <div class="skill-group"><div class="skill-group-label">LLM / RAG</div><div class="skill-chips expert"><span class="chip"><span class="chip-dot"></span>GPT-4o</span><span class="chip"><span class="chip-dot"></span>LangChain</span><span class="chip"><span class="chip-dot"></span>ChromaDB</span><span class="chip"><span class="chip-dot"></span>RAG Pipeline</span></div></div>
      <div class="skill-group"><div class="skill-group-label">Voice AI</div><div class="skill-chips expert"><span class="chip"><span class="chip-dot"></span>Vapi.ai</span><span class="chip"><span class="chip-dot"></span>ElevenLabs</span><span class="chip"><span class="chip-dot"></span>Deepgram</span><span class="chip"><span class="chip-dot"></span>Twilio</span></div></div>
      <div class="skill-group"><div class="skill-group-label">ML / CV</div><div class="skill-chips advanced"><span class="chip"><span class="chip-dot"></span>YOLOv8</span><span class="chip"><span class="chip-dot"></span>TensorFlow</span><span class="chip"><span class="chip-dot"></span>scikit-learn</span><span class="chip"><span class="chip-dot"></span>OpenCV</span></div></div>
    </div>

    <div id="tab-infra" class="tab-panel">
      <div class="skill-group"><div class="skill-group-label">Databases</div><div class="skill-chips expert"><span class="chip"><span class="chip-dot"></span>MongoDB</span><span class="chip"><span class="chip-dot"></span>PostgreSQL</span><span class="chip"><span class="chip-dot"></span>MySQL</span><span class="chip"><span class="chip-dot"></span>Redis</span></div></div>
      <div class="skill-group"><div class="skill-group-label">DevOps</div><div class="skill-chips advanced"><span class="chip"><span class="chip-dot"></span>Docker</span><span class="chip"><span class="chip-dot"></span>Nginx</span><span class="chip"><span class="chip-dot"></span>PM2</span><span class="chip"><span class="chip-dot"></span>Git</span><span class="chip"><span class="chip-dot"></span>AWS</span></div></div>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section">
    <div class="section-head">
      <span class="section-tag">03</span>
      <span class="section-title">Featured Projects</span>
      <span class="section-line"></span>
    </div>

    <div class="project-card">
      <div class="project-header">
        <div class="project-title">Storm AI — Field Service Management SaaS</div>
        <span class="project-live">● LIVE</span>
      </div>
      <div class="project-desc">Production SaaS for field service businesses. AI sales assistant, CRM pipeline, GPS smart scheduling, customer portal, and mobile technician dispatch app.</div>
      <div class="project-tags">
        <span class="project-tag">React.js</span><span class="project-tag">Node.js</span><span class="project-tag">MongoDB</span><span class="project-tag">Twilio</span><span class="project-tag">QuickBooks API</span><span class="project-tag">AI Integration</span>
      </div>
      <div class="project-stats">
        <div class="project-stat"><span class="project-stat-val">1K+</span><span class="project-stat-key">Daily Users</span></div>
        <div class="project-stat"><span class="project-stat-val">99.9%</span><span class="project-stat-key">Uptime</span></div>
        <div class="project-stat"><span class="project-stat-val">&lt;150ms</span><span class="project-stat-key">Response</span></div>
        <div class="project-stat"><span class="project-stat-val">4.8/5</span><span class="project-stat-key">CSAT</span></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-header">
        <div class="project-title">VoiceOps — AI Calling Agent Platform</div>
        <span class="project-live">● LIVE</span>
      </div>
      <div class="project-desc">Full-stack AI voice calling agent with real-time transcription, voicemail detection, dynamic call flows, and live dashboard. Near-human conversation quality.</div>
      <div class="project-tags">
        <span class="project-tag">Vapi.ai</span><span class="project-tag">GPT-4o</span><span class="project-tag">ElevenLabs</span><span class="project-tag">Deepgram</span><span class="project-tag">Twilio</span><span class="project-tag">Node.js</span>
      </div>
    </div>

    <div class="project-card">
      <div class="project-header">
        <div class="project-title">Nozama.ai — AI-Powered E-Commerce</div>
        <span class="project-live">● DEPLOYED</span>
      </div>
      <div class="project-desc">ML-driven marketplace with dynamic pricing, 96%-accuracy recommendations, personalized UX, and 24/7 AI customer support chatbot.</div>
      <div class="project-tags">
        <span class="project-tag">React.js</span><span class="project-tag">Node.js</span><span class="project-tag">MongoDB</span><span class="project-tag">ML Recommendation</span>
      </div>
      <div class="project-stats">
        <div class="project-stat"><span class="project-stat-val">+45%</span><span class="project-stat-key">Conversion</span></div>
        <div class="project-stat"><span class="project-stat-val">+60%</span><span class="project-stat-key">Retention</span></div>
        <div class="project-stat"><span class="project-stat-val">-70%</span><span class="project-stat-key">Support Tickets</span></div>
        <div class="project-stat"><span class="project-stat-val">300%</span><span class="project-stat-key">User Growth</span></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-header">
        <div class="project-title">Legal Assistant AI Bot</div>
        <span class="project-live">● ENTERPRISE</span>
      </div>
      <div class="project-desc">Enterprise legal research assistant across 5+ law firms. AI-powered risk assessment, automated client communications, full GDPR/CCPA audit logs.</div>
      <div class="project-tags">
        <span class="project-tag">GPT-4</span><span class="project-tag">RAG Pipeline</span><span class="project-tag">ChromaDB</span><span class="project-tag">React.js</span><span class="project-tag">Node.js</span>
      </div>
      <div class="project-stats">
        <div class="project-stat"><span class="project-stat-val">70%</span><span class="project-stat-key">Time Saved</span></div>
        <div class="project-stat"><span class="project-stat-val">94%</span><span class="project-stat-key">Accuracy</span></div>
        <div class="project-stat"><span class="project-stat-val">$50K+</span><span class="project-stat-key">Annual Savings</span></div>
        <div class="project-stat"><span class="project-stat-val">4.9/5</span><span class="project-stat-key">CSAT</span></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-header">
        <div class="project-title">AIPAS — AI Procurement Automation</div>
        <span class="project-live">● FYP</span>
      </div>
      <div class="project-desc">Intelligent procurement system using OCR + NLP to read, classify, and act on supplier documents. Processes 1,000+ documents/hour with 92% decision accuracy.</div>
      <div class="project-tags">
        <span class="project-tag">Python</span><span class="project-tag">FastAPI</span><span class="project-tag">OCR</span><span class="project-tag">NLP</span><span class="project-tag">MongoDB</span>
      </div>
      <div class="project-stats">
        <div class="project-stat"><span class="project-stat-val">92%</span><span class="project-stat-key">Accuracy</span></div>
        <div class="project-stat"><span class="project-stat-val">10×</span><span class="project-stat-key">Faster</span></div>
        <div class="project-stat"><span class="project-stat-val">35%</span><span class="project-stat-key">Cost Cut</span></div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-header">
        <div class="project-title">GAECA — Emergency Vehicle Clearance Engine</div>
        <span class="project-live">● MVP</span>
      </div>
      <div class="project-desc">Real-time traffic simulation for emergency vehicle clearance with intelligent lane management, collision avoidance, and civilian vehicle routing via Mapbox GL JS.</div>
      <div class="project-tags">
        <span class="project-tag">React.js</span><span class="project-tag">Mapbox GL JS</span><span class="project-tag">Node.js</span><span class="project-tag">Real-time Sim</span>
      </div>
    </div>

  </div>

  <!-- TIMELINE -->
  <div class="section">
    <div class="section-head">
      <span class="section-tag">04</span>
      <span class="section-title">Career Timeline</span>
      <span class="section-line"></span>
    </div>
    <div class="timeline">
      <div class="timeline-item">
        <div class="timeline-dot active"></div>
        <div class="timeline-year">2025 — Now</div>
        <div class="timeline-title">Inter Tech Global · Full Stack Developer</div>
        <div class="timeline-sub">VoiceOps · GAECA · CleanOps · AIPAS FYP · R3F Virtual Girlfriend · 5+ production deployments</div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-year">2024</div>
        <div class="timeline-title">Storm AI Launch · Legal AI Bot · E-Commerce AI</div>
        <div class="timeline-sub">1,000+ DAU achieved · 5 law firm deployments · PNY Web Cert · Great Learning UI/UX</div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-year">2023</div>
        <div class="timeline-title">BitBash · AI/ML Research · Computer Vision</div>
        <div class="timeline-sub">YOLOv8 dental X-ray model · AI/ML fundamentals · Python & C++ certifications</div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-year">2022</div>
        <div class="timeline-title">First Freelance Projects · Core Certifications</div>
        <div class="timeline-sub">Advanced JavaScript (Coursera) · MongoDB University · Database foundations</div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-year">2021</div>
        <div class="timeline-title">BS Software Engineering — University of Lahore</div>
        <div class="timeline-sub">Started the journey · Software engineering foundations</div>
      </div>
    </div>
  </div>

  <!-- CERTS -->
  <div class="section">
    <div class="section-head">
      <span class="section-tag">05</span>
      <span class="section-title">Certifications</span>
      <span class="section-line"></span>
    </div>
    <div class="cert-grid">
      <div class="cert-card"><div class="cert-icon">🎓</div><div><div class="cert-name">Full Stack Development</div><div class="cert-org">PGE — Pangea Global Enterprise</div></div><span class="cert-year">2025</span></div>
      <div class="cert-card"><div class="cert-icon">🌐</div><div><div class="cert-name">Web Designer & Developer</div><div class="cert-org">PNY Training (verified)</div></div><span class="cert-year">2024</span></div>
      <div class="cert-card"><div class="cert-icon">🎨</div><div><div class="cert-name">UI/UX Design</div><div class="cert-org">Great Learning Academy</div></div><span class="cert-year">2024</span></div>
      <div class="cert-card"><div class="cert-icon">🤖</div><div><div class="cert-name">AI/ML Fundamentals</div><div class="cert-org">SoloLearn</div></div><span class="cert-year">2023</span></div>
      <div class="cert-card"><div class="cert-icon">🐍</div><div><div class="cert-name">Python Programming</div><div class="cert-org">SoloLearn</div></div><span class="cert-year">2023</span></div>
      <div class="cert-card"><div class="cert-icon">⚙️</div><div><div class="cert-name">C++ Programming</div><div class="cert-org">Great Learning Academy</div></div><span class="cert-year">2023</span></div>
      <div class="cert-card"><div class="cert-icon">📜</div><div><div class="cert-name">Advanced JavaScript</div><div class="cert-org">Coursera</div></div><span class="cert-year">2022</span></div>
      <div class="cert-card"><div class="cert-icon">🗄️</div><div><div class="cert-name">Database Management</div><div class="cert-org">MongoDB University</div></div><span class="cert-year">2022</span></div>
    </div>
  </div>

  <!-- CONNECT -->
  <div class="section">
    <div class="section-head">
      <span class="section-tag">06</span>
      <span class="section-title">Connect</span>
      <span class="section-line"></span>
    </div>
    <div class="connect-grid">
      <div class="connect-card"><div class="connect-icon" style="background:#1a1060">🌐</div><div><div class="connect-channel">Portfolio</div><div class="connect-val">portfolio-lvc1.vercel.app</div></div><span class="connect-resp">Always on</span></div>
      <div class="connect-card"><div class="connect-icon" style="background:#001830">💼</div><div><div class="connect-channel">LinkedIn</div><div class="connect-val">hamza-kahloon-12a14125a</div></div><span class="connect-resp">&lt;24h</span></div>
      <div class="connect-card"><div class="connect-icon" style="background:#1a0a0a">📧</div><div><div class="connect-channel">Email</div><div class="connect-val">hamzaakahloon903@gmail.com</div></div><span class="connect-resp">&lt;24h</span></div>
      <div class="connect-card"><div class="connect-icon" style="background:#0a1a10">💬</div><div><div class="connect-channel">WhatsApp</div><div class="connect-val">+92 309 145 3950</div></div><span class="connect-resp">&lt;12h</span></div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="quote">"Code is poetry written in logic — <em>AI is the rhythm that makes it dance.</em>"</div>
    <div class="footer-name">— HAMZA KAHLOON · LAHORE, PAKISTAN</div>
  </div>

</div>

<script>
function switchTab(btn, id) {
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.querySelectorAll('.tab-panel').forEach(p => p.classList.remove('active'));
  btn.classList.add('active');
  document.getElementById('tab-' + id).classList.add('active');
}
</script>
</body>
</html>
