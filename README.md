
<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=JetBrains+Mono:wght@400;500&display=swap');

#root {
  background: #07091a;
  color: #c9e8ff;
  font-family: 'JetBrains Mono', monospace;
  min-height: 100vh;
  overflow-x: hidden;
  padding-bottom: 3rem;
}

canvas#bg { position: fixed; top:0; left:0; width:100%; height:100%; pointer-events:none; z-index:0; }

.z1 { position: relative; z-index: 1; }

.topbar {
  display: flex; align-items: center; justify-content: space-between;
  padding: 1rem 2rem; border-bottom: 1px solid #00f7ff18;
}
.topbar-left { font-family: 'Orbitron', sans-serif; font-size: 0.7rem; color: #00f7ff88; letter-spacing: 0.2em; text-transform: uppercase; }
#clock { font-size: 0.72rem; color: #00f7ff99; letter-spacing: 0.12em; }
#prog-wrap { height: 2px; background: #00f7ff18; }
#prog-bar { height: 2px; background: #00f7ff; width: 0%; transition: width 0.15s; }

.hero {
  text-align: center; padding: 3rem 2rem 2rem;
  perspective: 800px;
}
#hero-inner {
  display: inline-block;
  transform-style: preserve-3d;
  transform: rotateX(5deg);
  transition: transform 0.08s ease;
  max-width: 640px; width: 100%;
  border: 1px solid #00f7ff22;
  border-radius: 18px;
  padding: 2.5rem 2rem;
  background: #0a1a33cc;
}
.hero-name {
  font-family: 'Orbitron', sans-serif;
  font-size: clamp(1.4rem, 3.5vw, 2.2rem);
  font-weight: 900;
  color: #00f7ff;
  letter-spacing: 0.04em;
  margin-bottom: 0.5rem;
  text-shadow: 0 0 30px #00f7ff44;
}
.hero-roles { font-size: 0.72rem; color: #7ec8e3; letter-spacing: 0.12em; text-transform: uppercase; margin-bottom: 1rem; line-height: 1.9; }
.hero-quote { font-size: 0.73rem; color: #4a7a9b; border-left: 2px solid #00f7ff33; padding-left: 1rem; text-align: left; font-style: italic; line-height: 1.7; margin-top: 1rem; }
.online-dot { display: inline-block; width: 7px; height: 7px; border-radius: 50%; background: #4ade80; margin-right: 6px; animation: blink 1.4s ease-in-out infinite; }
@keyframes blink { 0%,100%{opacity:1;} 50%{opacity:0.3;} }
.status-pill { display: inline-flex; align-items: center; font-size: 0.68rem; color: #4ade80; background: #4ade8011; border: 1px solid #4ade8033; border-radius: 100px; padding: 4px 14px; margin-top: 1rem; letter-spacing: 0.08em; text-transform: uppercase; }

.section { padding: 2rem 2rem 0; }
.sh {
  font-family: 'Orbitron', sans-serif; font-size: 0.72rem; letter-spacing: 0.2em;
  text-transform: uppercase; color: #00f7ff; margin-bottom: 1.25rem;
  display: flex; align-items: center; gap: 10px;
}
.sh::before { content: '//'; opacity: 0.4; }
.sh::after { content: ''; flex: 1; height: 1px; background: #00f7ff1a; }

.stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); gap: 10px; }
.stat-card {
  background: #0a1a2e; border: 1px solid #00f7ff1a; border-radius: 12px;
  padding: 1rem; text-align: center;
  transition: border-color 0.2s, transform 0.2s;
}
.stat-card:hover { border-color: #00f7ff44; transform: translateY(-3px); }
.stat-num { display: block; font-family: 'Orbitron', sans-serif; font-size: 1.4rem; font-weight: 700; color: #00f7ff; }
.stat-lbl { display: block; font-size: 0.62rem; color: #4a7090; text-transform: uppercase; letter-spacing: 0.1em; margin-top: 4px; }

.gh-imgs { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 1rem; }
.gh-imgs img { border-radius: 10px; max-width: 48%; flex: 1; min-width: 200px; border: 1px solid #00f7ff11; }

.exp-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 14px; }
.exp-card {
  background: #0a1a2e; border: 1px solid #00f7ff1a; border-radius: 14px;
  padding: 1.25rem;
  transition: transform 0.2s, border-color 0.2s;
  position: relative; overflow: hidden;
}
.exp-card::before { content: ''; position: absolute; top:0; left:0; right:0; height:2px; background: #00f7ff44; }
.exp-card:hover { transform: translateY(-4px); border-color: #00f7ff33; }
.exp-co { font-family: 'Orbitron', sans-serif; font-size: 0.8rem; color: #00f7ff; margin-bottom: 4px; }
.exp-role { font-size: 0.72rem; color: #7ec8e3; margin-bottom: 0.75rem; }
.exp-bullets { list-style: none; padding: 0; margin: 0; }
.exp-bullets li { font-size: 0.7rem; color: #5a8aaa; line-height: 1.7; padding-left: 14px; position: relative; }
.exp-bullets li::before { content: '>'; position: absolute; left: 0; color: #00f7ff55; }

.proj-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 12px; }
.proj-card {
  background: #0d1a38; border: 1px solid #7b68ee22; border-radius: 14px;
  padding: 1.25rem; position: relative; overflow: hidden;
  transition: transform 0.2s, box-shadow 0.2s;
}
.proj-card::after { content: ''; position: absolute; left:0; top:0; width:3px; height:100%; background: #7b68ee; border-radius: 0; }
.proj-card:hover { transform: translateX(4px); box-shadow: -3px 0 16px #7b68ee22; }
.proj-top { display: flex; align-items: center; justify-content: space-between; margin-bottom: 0.6rem; }
.proj-name { font-family: 'Orbitron', sans-serif; font-size: 0.78rem; color: #b8a4ff; }
.wip { font-size: 0.58rem; padding: 2px 8px; border-radius: 100px; background: #fbbf2411; border: 1px solid #fbbf2433; color: #fbbf24; letter-spacing: 0.07em; text-transform: uppercase; display: flex; align-items: center; gap: 5px; }
.wip-d { width: 4px; height: 4px; border-radius: 50%; background: #fbbf24; animation: blink 1s infinite; }
.proj-desc { font-size: 0.68rem; color: #5a7a9a; line-height: 1.65; margin-bottom: 0.75rem; }
.tags { display: flex; flex-wrap: wrap; gap: 5px; }
.tag { font-size: 0.6rem; padding: 2px 8px; border-radius: 100px; border: 1px solid #00f7ff22; color: #7ec8e3; background: #00f7ff08; }
.tag.ai { border-color: #b8a4ff33; color: #b8a4ff; background: #b8a4ff08; }
.tag.hot { border-color: #fb923c33; color: #fb923c; background: #fb923c08; }

.skills-list { display: grid; gap: 10px; }
.skrow { display: grid; grid-template-columns: 150px 1fr 36px; align-items: center; gap: 10px; }
.sk-lbl { font-size: 0.68rem; color: #7ec8e3; }
.sk-track { height: 4px; background: #00f7ff0d; border-radius: 10px; overflow: hidden; }
.sk-fill { height: 100%; border-radius: 10px; background: #00f7ff; width: 0%; transition: width 1.3s cubic-bezier(0.4,0,0.2,1); }
.sk-pct { font-size: 0.62rem; color: #2a5070; text-align: right; }

.terminal {
  background: #06101e; border: 1px solid #00f7ff1a; border-radius: 12px;
  padding: 1.25rem; font-size: 0.72rem; line-height: 1.8;
  color: #4ade80;
}
.t-prompt { color: #00f7ff88; }
.t-comment { color: #2a5a70; }

.connect-row { display: flex; gap: 10px; flex-wrap: wrap; }
.cbtn {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 9px 18px; border-radius: 10px;
  font-size: 0.7rem; font-family: 'JetBrains Mono', monospace;
  text-decoration: none; border: 1px solid #00f7ff2a; color: #7ec8e3;
  background: #0a1a2e; letter-spacing: 0.04em;
  transition: all 0.18s ease;
}
.cbtn:hover { background: #00f7ff12; border-color: #00f7ff; color: #00f7ff; transform: translateY(-2px); }

.footer { text-align: center; padding: 2.5rem 1rem 0.5rem; font-size: 0.62rem; color: #1a3a55; border-top: 1px solid #00f7ff08; margin-top: 2rem; }
</style>

<div id="root">
<canvas id="bg"></canvas>

<div id="prog-wrap" class="z1"><div id="prog-bar"></div></div>

<div class="topbar z1">
  <div class="topbar-left"><i class="ti ti-terminal-2" aria-hidden="true"></i> mujeeb.qadri :: portfolio v2.0</div>
  <div id="clock">—</div>
</div>

<section class="hero z1">
  <div id="hero-inner">
    <div class="hero-name">Mujeeb Qadri</div>
    <div class="hero-roles">
      AI Workflow Builder &nbsp;·&nbsp; QA Operations Specialist<br>
      Automation Engineer &nbsp;·&nbsp; Salon AI Developer
    </div>
    <div class="hero-quote">"Building scalable AI-driven workflows for modern operational systems."</div>
    <div class="status-pill"><span class="online-dot"></span>Available for opportunities</div>
  </div>
</section>

<section class="section z1">
  <div class="sh">Live dashboard</div>
  <div class="stats-grid">
    <div class="stat-card"><span class="stat-num" id="s-yoe">0</span><span class="stat-lbl">Years exp.</span></div>
    <div class="stat-card"><span class="stat-num" id="s-proj">0</span><span class="stat-lbl">Active builds</span></div>
    <div class="stat-card"><span class="stat-num" id="s-tools">0</span><span class="stat-lbl">Tools built</span></div>
    <div class="stat-card"><span class="stat-num" style="font-size:0.95rem; padding-top:2px;" id="s-time">—</span><span class="stat-lbl">IST now</span></div>
  </div>
  <div class="gh-imgs">
    <img src="https://github-readme-stats.vercel.app/api?username=4lt41r&show_icons=true&theme=tokyonight&hide_border=true&bg_color=07091a&title_color=00f7ff&text_color=7ec8e3&icon_color=7b68ee" alt="GitHub stats" />
    <img src="https://github-readme-streak-stats.herokuapp.com/?user=4lt41r&theme=tokyonight&hide_border=true&background=07091a&ring=00f7ff&fire=7b68ee&currStreakLabel=7ec8e3" alt="Streak stats" />
  </div>
</section>

<section class="section z1">
  <div class="sh">Experience journey</div>
  <div class="exp-grid">
    <div class="exp-card">
      <div class="exp-co"><i class="ti ti-building" style="font-size:14px; margin-right:6px" aria-hidden="true"></i>Cognizant</div>
      <div class="exp-role">Quality Analyst / QA Leadership</div>
      <ul class="exp-bullets">
        <li>Led QA operations and quality monitoring</li>
        <li>Optimized reviewer performance workflows</li>
        <li>Managed escalation handling systems</li>
        <li>Created scalable review processes</li>
      </ul>
    </div>
    <div class="exp-card">
      <div class="exp-co"><i class="ti ti-building" style="font-size:14px; margin-right:6px" aria-hidden="true"></i>Concentrix</div>
      <div class="exp-role">Content Moderator / Operations</div>
      <ul class="exp-bullets">
        <li>Managed high-volume moderation operations</li>
        <li>Ensured policy compliance &amp; quality standards</li>
        <li>Coordinated cross-team operational workflows</li>
      </ul>
    </div>
    <div class="exp-card">
      <div class="exp-co"><i class="ti ti-tools" style="font-size:14px; margin-right:6px" aria-hidden="true"></i>Independent</div>
      <div class="exp-role">AI Workflow Builder &amp; Automation Engineer</div>
      <ul class="exp-bullets">
        <li>Building Salon AI &amp; Salon CRM platforms</li>
        <li>Local AI infrastructure experiments</li>
        <li>Operational dashboard engineering</li>
      </ul>
    </div>
  </div>
</section>

<section class="section z1">
  <div class="sh">Active systems</div>
  <div class="proj-grid">
    <div class="proj-card">
      <div class="proj-top">
        <div class="proj-name">Salon AI</div>
        <div class="wip"><span class="wip-d"></span>active</div>
      </div>
      <div class="proj-desc">AI-powered salon ops — smart scheduling, AI receptionist concepts, analytics, attendance &amp; workflow monitoring.</div>
      <div class="tags"><span class="tag ai">LLM</span><span class="tag ai">AI</span><span class="tag hot">automation</span><span class="tag">ops</span></div>
    </div>
    <div class="proj-card">
      <div class="proj-top">
        <div class="proj-name">Salon CRM</div>
        <div class="wip"><span class="wip-d"></span>active</div>
      </div>
      <div class="proj-desc">Modern CRM for salons — appointments, staff dashboards, inventory, billing workflows, customer management.</div>
      <div class="tags"><span class="tag">JavaScript</span><span class="tag">Apps Script</span><span class="tag hot">CRM</span></div>
    </div>
    <div class="proj-card">
      <div class="proj-top">
        <div class="proj-name">Local AI</div>
        <div class="wip"><span class="wip-d"></span>active</div>
      </div>
      <div class="proj-desc">Offline-first AI infrastructure — edge models, privacy-first QA copilots, report generation, zero cloud dependency.</div>
      <div class="tags"><span class="tag ai">Ollama</span><span class="tag ai">edge AI</span><span class="tag hot">privacy</span></div>
    </div>
    <div class="proj-card">
      <div class="proj-top">
        <div class="proj-name">QA Automation</div>
        <div class="wip" style="background:#4ade8011; border-color:#4ade8033; color:#4ade80;"><span class="wip-d" style="background:#4ade80;"></span>shipped</div>
      </div>
      <div class="proj-desc">Apps Script toolkit for QA assignment rotation, error logging, and performance tracking across review teams.</div>
      <div class="tags"><span class="tag">Apps Script</span><span class="tag">Google Sheets</span></div>
    </div>
  </div>
</section>

<section class="section z1">
  <div class="sh">Tech arsenal</div>
  <div class="skills-list" id="skills-list">
    <div class="skrow"><div class="sk-lbl">QA &amp; Content Ops</div><div class="sk-track"><div class="sk-fill" data-w="95"></div></div><div class="sk-pct">95%</div></div>
    <div class="skrow"><div class="sk-lbl">Google Apps Script</div><div class="sk-track"><div class="sk-fill" data-w="85"></div></div><div class="sk-pct">85%</div></div>
    <div class="skrow"><div class="sk-lbl">AI integration</div><div class="sk-track"><div class="sk-fill" data-w="80"></div></div><div class="sk-pct">80%</div></div>
    <div class="skrow"><div class="sk-lbl">JavaScript</div><div class="sk-track"><div class="sk-fill" data-w="75"></div></div><div class="sk-pct">75%</div></div>
    <div class="skrow"><div class="sk-lbl">Python</div><div class="sk-track"><div class="sk-fill" data-w="65"></div></div><div class="sk-pct">65%</div></div>
    <div class="skrow"><div class="sk-lbl">HTML / CSS</div><div class="sk-track"><div class="sk-fill" data-w="72"></div></div><div class="sk-pct">72%</div></div>
    <div class="skrow"><div class="sk-lbl">Dashboard design</div><div class="sk-track"><div class="sk-fill" data-w="78"></div></div><div class="sk-pct">78%</div></div>
  </div>
</section>

<section class="section z1" style="margin-top:1.5rem;">
  <div class="sh">Currently building</div>
  <div class="terminal">
    <div><span class="t-prompt">$ </span>cat active_systems.log</div>
    <div class="t-comment">[ ACTIVE SYSTEMS — 2025 ]</div>
    <div><span style="color:#00f7ff55;">✓ </span>Salon AI &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#fbbf24; font-size:0.62rem;">▓▓▓▓▓▓▓░░ 70%</span></div>
    <div><span style="color:#00f7ff55;">✓ </span>Salon CRM &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#fbbf24; font-size:0.62rem;">▓▓▓▓▓░░░░ 55%</span></div>
    <div><span style="color:#00f7ff55;">✓ </span>Local AI Infrastructure &nbsp;<span style="color:#fbbf24; font-size:0.62rem;">▓▓▓░░░░░░ 35%</span></div>
    <div><span style="color:#00f7ff55;">✓ </span>AI Workflow Automation &nbsp;<span style="color:#fbbf24; font-size:0.62rem;">▓▓▓▓░░░░░ 45%</span></div>
    <div><span style="color:#4ade80;">✓ </span>QA Automation Suite &nbsp;&nbsp;<span style="color:#4ade80; font-size:0.62rem;">▓▓▓▓▓▓▓▓▓ shipped</span></div>
    <div style="margin-top:0.5rem;"><span class="t-prompt">$ </span><span style="animation: blink 1s step-end infinite; color:#00f7ff;">_</span></div>
  </div>
</section>

<section class="section z1" style="margin-top:1.5rem;">
  <div class="sh">Connect</div>
  <div class="connect-row">
    <a class="cbtn" href="https://www.linkedin.com/in/mujeeb-ul-haq-qadri-81796a161/" target="_blank">
      <i class="ti ti-brand-linkedin" style="font-size:16px" aria-hidden="true"></i>LinkedIn
    </a>
    <a class="cbtn" href="mailto:syedmujeeb.qadri@gmail.com">
      <i class="ti ti-mail" style="font-size:16px" aria-hidden="true"></i>Gmail
    </a>
    <a class="cbtn" href="https://github.com/4lt41r" target="_blank">
      <i class="ti ti-brand-github" style="font-size:16px" aria-hidden="true"></i>GitHub / 4lt41r
    </a>
  </div>
</section>

<div class="footer z1">
  <span style="color:#0a2a40;">⚡</span> Mujeeb Qadri &nbsp;·&nbsp; 4lt41r &nbsp;·&nbsp; Built with code &amp; intent
</div>
</div>

<script>
(function(){
  const canvas = document.getElementById('bg');
  const ctx = canvas.getContext('2d');
  let W, H, pts = [];

  function resize(){
    W = canvas.width = window.innerWidth;
    H = canvas.height = Math.max(document.body.scrollHeight, window.innerHeight);
  }

  function mkPts(){
    pts = Array.from({length:160}, ()=>({
      x: Math.random()*W, y: Math.random()*H,
      r: Math.random()*1.2+0.2,
      ph: Math.random()*Math.PI*2,
      sp: Math.random()*0.004+0.001
    }));
  }

  let fr = 0;
  function draw(){
    ctx.clearRect(0,0,W,H);
    fr++;
    pts.forEach(p=>{
      const a = 0.25 + 0.35*Math.sin(fr*p.sp+p.ph);
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI*2);
      ctx.fillStyle = `rgba(0,200,255,${a})`;
      ctx.fill();
    });
    requestAnimationFrame(draw);
  }

  resize(); mkPts(); draw();
  window.addEventListener('resize', ()=>{ resize(); mkPts(); });

  window.addEventListener('scroll', ()=>{
    const t = document.body.scrollHeight - window.innerHeight;
    const p = t > 0 ? Math.min(100,(window.scrollY/t)*100) : 0;
    document.getElementById('prog-bar').style.width = Math.round(p)+'%';
  });

  document.getElementById('hero-inner').addEventListener('mousemove', function(e){
    const r = this.getBoundingClientRect();
    const cx = r.left + r.width/2, cy = r.top + r.height/2;
    const dx = (e.clientX - cx)/(r.width/2);
    const dy = (e.clientY - cy)/(r.height/2);
    this.style.transform = `rotateX(${5-dy*9}deg) rotateY(${dx*9}deg)`;
  });
  document.getElementById('hero-inner').addEventListener('mouseleave', function(){
    this.style.transform = 'rotateX(5deg) rotateY(0deg)';
  });

  function tick(){
    const now = new Date();
    const t = now.toLocaleTimeString('en-IN',{hour12:false,timeZone:'Asia/Kolkata'});
    const d = now.toLocaleDateString('en-IN',{weekday:'short',day:'numeric',month:'short',timeZone:'Asia/Kolkata'});
    const txt = `IST ${t} · ${d}`;
    document.getElementById('clock').textContent = txt;
    document.getElementById('s-time').textContent = t;
  }
  tick(); setInterval(tick, 1000);

  function counter(el, end, sfx, dur){
    let s=0, step=dur/end, last=performance.now();
    function f(now){ const dt=now-last; last=now; s+=dt/step; if(s>=end){el.textContent=end+sfx;return;} el.textContent=Math.floor(s)+sfx; requestAnimationFrame(f); }
    requestAnimationFrame(f);
  }
  setTimeout(()=>{
    counter(document.getElementById('s-yoe'), 6, '+', 1200);
    counter(document.getElementById('s-proj'), 4, '', 900);
    counter(document.getElementById('s-tools'), 12, '+', 1400);
  }, 400);

  const obs = new IntersectionObserver(entries=>{
    entries.forEach(e=>{
      if(e.isIntersecting){
        e.target.style.width = e.target.dataset.w+'%';
        obs.unobserve(e.target);
      }
    });
  }, {threshold:0.3});
  document.querySelectorAll('.sk-fill').forEach(f=>obs.observe(f));
})();
</script>
