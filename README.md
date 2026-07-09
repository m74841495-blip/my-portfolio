# my-portfolio<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>まりお | 音と絵のあいだで</title>
<meta name="description" content="まりお の作品集。イラストレーションと楽曲制作。">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Shippori+Antique+B1&family=Noto+Sans+JP:wght@300;400;500;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #100e1a;
    --surface: #1b1830;
    --surface-2: #241f3f;
    --text: #f0ead9;
    --text-muted: #8d87a8;
    --line: #34304f;
    --amber: #e9a23b;   /* illustration */
    --violet: #7c6cf0;  /* music */
    --amber-dim: #6b5527;
    --violet-dim: #362f6b;
    --display: 'Shippori Antique B1', sans-serif;
    --body: 'Noto Sans JP', sans-serif;
    --mono: 'JetBrains Mono', monospace;
  }

  *{ box-sizing: border-box; margin:0; padding:0; }

  html{ scroll-behavior: smooth; }

  body{
    background: var(--bg);
    color: var(--text);
    font-family: var(--body);
    line-height: 1.8;
    overflow-x: hidden;
  }

  a{ color: inherit; text-decoration: none; }

  ::selection{ background: var(--violet); color: var(--bg); }

  /* focus visibility */
  a:focus-visible, button:focus-visible, input:focus-visible{
    outline: 2px solid var(--amber);
    outline-offset: 3px;
  }

  .wrap{
    max-width: 980px;
    margin: 0 auto;
    padding: 0 24px;
  }

  /* ---------- Header ---------- */
  header{
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 50;
    background: rgba(16,14,26,0.85);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid var(--line);
  }
  header .wrap{
    display:flex;
    align-items:center;
    justify-content: space-between;
    height: 64px;
    max-width: 1040px;
  }
  .logo{
    font-family: var(--display);
    font-size: 1.15rem;
    letter-spacing: 0.08em;
  }
  .logo span{ color: var(--amber); }
  nav ul{
    display:flex;
    gap: 28px;
    list-style:none;
    font-family: var(--mono);
    font-size: 0.72rem;
    letter-spacing: 0.12em;
  }
  nav a{
    color: var(--text-muted);
    transition: color .25s ease;
    position: relative;
    padding-bottom: 4px;
  }
  nav a:hover{ color: var(--text); }
  nav a::after{
    content:"";
    position:absolute; left:0; bottom:0;
    width:0; height:1px;
    background: var(--amber);
    transition: width .25s ease;
  }
  nav a:hover::after{ width:100%; }

  /* ---------- Hero ---------- */
  .hero{
    min-height: 100svh;
    display:flex;
    flex-direction: column;
    justify-content:center;
    position: relative;
    padding-top: 64px;
  }
  .hero-grid{
    position:absolute;
    inset:0;
    background-image:
      linear-gradient(var(--line) 1px, transparent 1px),
      linear-gradient(90deg, var(--line) 1px, transparent 1px);
    background-size: 42px 42px;
    opacity: 0.18;
    mask-image: radial-gradient(ellipse at 50% 40%, black 10%, transparent 70%);
  }
  .hero-content{
    position: relative;
    z-index: 2;
    text-align:center;
  }
  .eyebrow{
    font-family: var(--mono);
    font-size: 0.75rem;
    letter-spacing: 0.35em;
    color: var(--text-muted);
    margin-bottom: 18px;
  }
  .hero h1{
    font-family: var(--display);
    font-size: clamp(3.2rem, 12vw, 7.5rem);
    letter-spacing: 0.03em;
    line-height: 1;
    background: linear-gradient(120deg, var(--amber) 0%, var(--text) 35%, var(--violet) 75%);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
  }
  .hero-tagline{
    margin-top: 22px;
    font-size: 1.05rem;
    color: var(--text-muted);
    letter-spacing: 0.04em;
  }
  .hero-roles{
    margin-top: 10px;
    font-family: var(--mono);
    font-size: 0.8rem;
    color: var(--text-muted);
  }
  .hero-roles .amber{ color: var(--amber); }
  .hero-roles .violet{ color: var(--violet); }

  /* oscilloscope */
  .scope{
    position: relative;
    z-index: 2;
    width: min(560px, 84vw);
    height: 90px;
    margin: 48px auto 0;
  }
  .scope svg{ width:100%; height:100%; display:block; }
  .scope path{
    fill:none;
    stroke: var(--violet);
    stroke-width: 1.6;
    stroke-dasharray: 6 4;
    animation: scope-flow 6s linear infinite;
    opacity: 0.85;
  }
  .scope path.b{
    stroke: var(--amber);
    animation-duration: 8s;
    animation-direction: reverse;
    opacity: 0.5;
  }
  @keyframes scope-flow{
    to{ stroke-dashoffset: -400; }
  }
  .scroll-cue{
    position:absolute;
    bottom: 34px; left:50%;
    transform: translateX(-50%);
    font-family: var(--mono);
    font-size: 0.68rem;
    letter-spacing: 0.3em;
    color: var(--text-muted);
    display:flex; flex-direction:column; align-items:center; gap:8px;
  }
  .scroll-cue .stem{
    width:1px; height:26px;
    background: linear-gradient(var(--text-muted), transparent);
    animation: cue-pulse 1.8s ease-in-out infinite;
  }
  @keyframes cue-pulse{
    0%,100%{ opacity:.3; } 50%{ opacity:1; }
  }

  /* ---------- Section shared ---------- */
  section{ padding: 120px 0; position:relative; }
  .section-head{
    display:flex;
    align-items: baseline;
    gap: 16px;
    margin-bottom: 48px;
  }
  .section-num{
    font-family: var(--mono);
    color: var(--text-muted);
    font-size: 0.8rem;
  }
  .section-head h2{
    font-family: var(--display);
    font-size: 2rem;
    letter-spacing: 0.05em;
  }
  .section-head .rule{
    flex:1;
    height:1px;
    background: var(--line);
  }

  /* ---------- Profile ---------- */
  .profile{
    display:grid;
    grid-template-columns: 1.1fr 0.9fr;
    gap: 56px;
    align-items:start;
  }
  .profile p{ color: var(--text-muted); font-size: 0.98rem; }
  .profile p + p{ margin-top: 16px; }
  .profile strong{ color: var(--text); font-weight:500; }

  .influence-panel{
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: 4px;
    padding: 24px;
  }
  .influence-panel h3{
    font-family: var(--mono);
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    color: var(--text-muted);
    margin-bottom: 16px;
  }
  .patch-list{ list-style:none; display:flex; flex-direction:column; gap: 10px; }
  .patch-list li{
    display:flex;
    align-items:center;
    gap: 12px;
    font-size: 0.92rem;
    padding: 8px 0;
    border-bottom: 1px dashed var(--line);
  }
  .patch-list li:last-child{ border-bottom:none; }
  .jack{
    width: 9px; height:9px;
    border-radius:50%;
    background: var(--violet);
    box-shadow: 0 0 8px var(--violet);
    flex-shrink:0;
  }
  .patch-list li:nth-child(even) .jack{
    background: var(--amber);
    box-shadow: 0 0 8px var(--amber);
  }

  /* ---------- Works / toggle ---------- */
  .works-toggle{
    display:inline-flex;
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: 999px;
    padding: 4px;
    margin-bottom: 40px;
    gap: 2px;
  }
  .works-toggle input{
    position:absolute;
    opacity:0;
    pointer-events:none;
  }
  .works-toggle label{
    font-family: var(--mono);
    font-size: 0.72rem;
    letter-spacing: 0.12em;
    padding: 9px 20px;
    border-radius: 999px;
    cursor:pointer;
    color: var(--text-muted);
    transition: all .25s ease;
    user-select:none;
  }
  .works-toggle input:checked + label{
    background: var(--surface-2);
    color: var(--text);
  }
  .works-toggle input#f-all:checked + label{ box-shadow: inset 0 0 0 1px var(--line); }
  .works-toggle input#f-illust:checked + label{ color: var(--amber); box-shadow: inset 0 0 0 1px var(--amber-dim); }
  .works-toggle input#f-music:checked + label{ color: var(--violet); box-shadow: inset 0 0 0 1px var(--violet-dim); }

  .grid{
    display:grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
  }
  .card{
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: 4px;
    overflow:hidden;
    transition: transform .3s ease, border-color .3s ease;
  }
  .card:hover{ transform: translateY(-4px); border-color: var(--text-muted); }
  .card[hidden]{ display:none; }
  .card-thumb{
    aspect-ratio: 4/3;
    position:relative;
    display:flex;
    align-items:center;
    justify-content:center;
    font-family: var(--mono);
    font-size: 0.68rem;
    letter-spacing: 0.15em;
    color: var(--text-muted);
  }
  .card[data-cat="illust"] .card-thumb{
    background:
      repeating-linear-gradient(135deg, transparent 0 12px, rgba(233,162,59,0.10) 12px 13px),
      radial-gradient(circle at 30% 30%, rgba(233,162,59,0.18), transparent 60%),
      var(--surface-2);
  }
  .card[data-cat="music"] .card-thumb{
    background:
      repeating-linear-gradient(90deg, transparent 0 10px, rgba(124,108,240,0.14) 10px 11px),
      radial-gradient(circle at 70% 60%, rgba(124,108,240,0.20), transparent 60%),
      var(--surface-2);
  }
  .card-body{ padding: 16px 18px 20px; }
  .card-cat{
    font-family: var(--mono);
    font-size: 0.65rem;
    letter-spacing: 0.15em;
  }
  .card[data-cat="illust"] .card-cat{ color: var(--amber); }
  .card[data-cat="music"] .card-cat{ color: var(--violet); }
  .card h3{
    font-family: var(--display);
    font-size: 1.15rem;
    margin: 8px 0 6px;
    letter-spacing: 0.02em;
  }
  .card p{ color: var(--text-muted); font-size: 0.85rem; }

  /* ---------- Contact ---------- */
  .contact-panel{
    background: var(--surface);
    border: 1px solid var(--line);
    border-radius: 4px;
    padding: 40px;
    display:grid;
    grid-template-columns: 1fr 1fr;
    gap: 24px;
  }
  .contact-link{
    display:flex;
    align-items:center;
    justify-content: space-between;
    padding: 18px 20px;
    background: var(--surface-2);
    border-radius: 4px;
    border: 1px solid var(--line);
    transition: border-color .25s ease;
  }
  .contact-link:hover{ border-color: var(--amber); }
  .contact-link .cl-label{ font-family: var(--mono); font-size: 0.85rem; letter-spacing:0.05em; }
  .contact-link .cl-handle{ font-size: 0.8rem; color: var(--text-muted); }
  .contact-link .cl-arrow{ font-family: var(--mono); color: var(--amber); }

  footer{
    padding: 40px 0 60px;
    text-align:center;
    font-family: var(--mono);
    font-size: 0.7rem;
    letter-spacing: 0.1em;
    color: var(--text-muted);
  }

  /* ---------- Responsive ---------- */
  @media (max-width: 760px){
    nav ul{ gap: 16px; }
    nav a{ font-size: 0.65rem; }
    .profile{ grid-template-columns: 1fr; }
    .grid{ grid-template-columns: 1fr 1fr; }
    .contact-panel{ grid-template-columns: 1fr; padding: 24px; }
  }
  @media (max-width: 480px){
    .grid{ grid-template-columns: 1fr; }
    .works-toggle{ flex-wrap:wrap; }
  }

  @media (prefers-reduced-motion: reduce){
    html{ scroll-behavior: auto; }
    .scope path, .scroll-cue .stem{ animation: none; }
  }
</style>
</head>
<body>

<header>
  <div class="wrap">
    <div class="logo">mari<span>o</span></div>
    <nav>
      <ul>
        <li><a href="#profile">PROFILE</a></li>
        <li><a href="#works">WORKS</a></li>
        <li><a href="#contact">CONTACT</a></li>
      </ul>
    </nav>
  </div>
</header>

<section class="hero">
  <div class="hero-grid" aria-hidden="true"></div>
  <div class="hero-content wrap">
    <div class="eyebrow">ILLUSTRATOR / COMPOSER</div>
    <h1>まり<span>お</span></h1>
    <p class="hero-tagline">音と絵、ふたつの周波数のあいだで作品をつくっています。</p>
    <p class="hero-roles"><span class="amber">ILLUST</span>  &nbsp;&nbsp;/&nbsp;&nbsp;<span class="violet">MUSIC</span> </p>
    <div class="scope" aria-hidden="true">
      <svg viewBox="0 0 560 90" preserveAspectRatio="none">
        <path class="a" d="M0,45 Q20,10 40,45 T80,45 T120,45 Q140,80 160,45 T200,45 T240,45 Q260,15 280,45 T320,45 T360,45 Q380,75 400,45 T440,45 T480,45 Q500,20 520,45 T560,45"/>
        <path class="b" d="M0,45 Q30,70 60,45 T120,45 Q150,20 180,45 T240,45 Q270,65 300,45 T360,45 Q390,25 420,45 T480,45 Q510,60 540,45 T560,45"/>
      </svg>
    </div>
  </div>
  <div class="scroll-cue"><span>SCROLL</span><span class="stem"></span></div>
</section>

<section id="profile">
  <div class="wrap">
    <div class="section-head">
      <span class="section-num">01</span>
      <h2>Profile</h2>
      <span class="rule"></span>
    </div>
    <div class="profile">
      <div>
        <p>18歳。睡眠時間を創作にあて、<strong>5年前からイラスト制作と音楽制作</strong>を続けています。日本の電子音楽の系譜に強く影響を受け、コード進行や理論の探求も並行して行っています。</p>
        <p>イラストでは<strong>グリザイユを軸にしたデジタル制作</strong>とデッサンを行き来しながら、線と陰影の理論を探求中。X(旧Twitter)では「まりお」名義でオリジナルイラストを、Niconico動画では楽曲を発表しています。</p>
        <p style="font-size:0.8rem; color:var(--text-muted); margin-top:20px;"></p>
      </div>
      <div class="influence-panel">
        <h3>TOOLS</h3>
        <ul class="patch-list">
          <li><span class="jack" aria-hidden="true"></span>Cubase</li>
          <li><span class="jack" aria-hidden="true"></span>Clip Studio Paint</li>
       
        </ul>
      </div>
    </div>
  </div>
</section>

<section id="works">
  <div class="wrap">
    <div class="section-head">
      <span class="section-num">02</span>
      <h2>Works</h2>
      <span class="rule"></span>
    </div>

    <div class="works-toggle" role="group" aria-label="作品カテゴリで絞り込み">
      <input type="radio" name="filter" id="f-all" checked>
      <label for="f-all">ALL</label>
      <input type="radio" name="filter" id="f-illust">
      <label for="f-illust">ILLUST</label>
      <input type="radio" name="filter" id="f-music">
      <label for="f-music">MUSIC</label>
    </div>

    <div class="grid" id="worksGrid">
      <article class="card" data-cat="illust">
        <div class="card-thumb">1200×900 推奨</div>
        <div class="card-body">
          <div class="card-cat">ILLUSTRATION</div>
          <h3>作品タイトル 01</h3>
          <p>ここに作品の説明文を入れます。</p>
        </div>
      </article>
      <article class="card" data-cat="music">
        <div class="card-thumb">ジャケット画像</div>
        <div class="card-body">
          <div class="card-cat">MUSIC — VOCALOID</div>
          <h3>楽曲タイトル 01</h3>
          <p>Niconico動画へのリンクをここに。</p>
        </div>
      </article>
      <article class="card" data-cat="illust">
        <div class="card-thumb">1200×900 推奨</div>
        <div class="card-body">
          <div class="card-cat">ILLUSTRATION</div>
          <h3>作品タイトル 02</h3>
          <p>ここに作品の説明文を入れます。</p>
        </div>
      </article>
      <article class="card" data-cat="music">
        <div class="card-thumb">ジャケット画像</div>
        <div class="card-body">
          <div class="card-cat">MUSIC — DTM</div>
          <h3>楽曲タイトル 02</h3>
          <p>Niconico動画へのリンクをここに。</p>
        </div>
      </article>
      <article class="card" data-cat="illust">
        <div class="card-thumb">1200×900 推奨</div>
        <div class="card-body">
          <div class="card-cat">ILLUSTRATION</div>
          <h3>作品タイトル 03</h3>
          <p>ここに作品の説明文を入れます。</p>
        </div>
      </article>
      <article class="card" data-cat="music">
        <div class="card-thumb">ジャケット画像</div>
        <div class="card-body">
          <div class="card-cat">MUSIC — VOCALOID</div>
          <h3>楽曲タイトル 03</h3>
          <p>Niconico動画へのリンクをここに。</p>
        </div>
      </article>
    </div>
  </div>
</section>

<section id="contact">
  <div class="wrap">
    <div class="section-head">
      <span class="section-num">03</span>
      <h2>Contact</h2>
      <span class="rule"></span>
    </div>
    <div class="contact-panel">
      <a class="contact-link" href="https://x.com/kanarino" target="_blank" rel="noopener">
        <span>
          <span class="cl-label">X (illustration)</span><br>
          <span class="cl-handle">@kanarino</span>
        </span>
        <span class="cl-arrow">→</span>
      </a>
      <a class="contact-link" href="https://www.nicovideo.jp/" target="_blank" rel="noopener">
        <span>
          <span class="cl-label">Niconico (music)</span><br>
          <span class="cl-handle">ここにマイページURL</span>
        </span>
        <span class="cl-arrow">→</span>
      </a>
    </div>
  </div>
</section>

<footer>
  <div class="wrap">kanarino — hand-built with HTML/CSS/JS</div>
</footer>

<script>
  // ---- 作品フィルタ ----
  const cards = document.querySelectorAll('#worksGrid .card');
  const radios = document.querySelectorAll('.works-toggle input');

  function applyFilter(){
    const active = document.querySelector('.works-toggle input:checked').id;
    cards.forEach(card => {
      if(active === 'f-all'){ card.hidden = false; return; }
      const cat = active === 'f-illust' ? 'illust' : 'music';
      card.hidden = card.dataset.cat !== cat;
    });
  }
  radios.forEach(r => r.addEventListener('change', applyFilter));
</script>

</body>
</html>
