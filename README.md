# My-records-site
Find.best.records-store
<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>חנות — Find Best Records</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Frank+Ruhl+Libre:wght@300;400;500;600;700&family=Heebo:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --black:#15130f;
    --black-soft:#1c1a15;
    --cream:#ede6d6;
    --paper:#f4efe4;
    --amber:#c9501f;
    --amber-soft:#dd7a4a;
    --olive:#6e7456;
    --text:#f2eee3;
    --text-dim:#a89e8a;
    --line: rgba(242,238,227,0.14);
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth; overflow-x:hidden;}
  body{
    background:var(--black);
    color:var(--text);
    font-family:'Heebo', sans-serif;
    -webkit-font-smoothing:antialiased;
    overflow-x:hidden;
  }
  @media (prefers-reduced-motion: reduce){
    *{animation-duration:0.001ms !important; animation-iteration-count:1 !important; transition-duration:0.001ms !important;}
  }
  a{color:inherit; text-decoration:none;}
  .display{font-family:'Frank Ruhl Libre', serif;}
  .mono{font-family:'Heebo', sans-serif; letter-spacing:0.03em;}
  .wrap{max-width:1240px; margin:0 auto; padding:0 32px;}

  /* ---------- focus ---------- */
  a:focus-visible, button:focus-visible{
    outline:2px solid var(--amber-soft);
    outline-offset:3px;
  }

  /* ---------- header ---------- */
  header{
    position:sticky; top:0; z-index:50;
    background:rgba(21,19,15,0.88);
    backdrop-filter: blur(10px);
    border-bottom:1px solid var(--line);
  }
  .nav{
    display:flex; align-items:center; justify-content:space-between;
    padding:20px 32px;
  }
  .logo{
    font-family:'Frank Ruhl Libre', serif;
    font-weight:600;
    font-size:1.08rem;
    letter-spacing:0.01em;
    white-space:nowrap;
    display:flex; align-items:center; gap:10px;
  }
  .logo .dot{
    width:11px; height:11px; border-radius:50%;
    background:var(--amber);
    box-shadow:0 0 0 3px rgba(201,80,31,0.18);
  }
  .navlinks{
    display:flex; gap:36px; font-size:0.92rem; color:var(--text-dim);
    letter-spacing:0.02em;
  }
  .navlinks a{ transition:color .2s; }
  .navlinks a:hover{ color:var(--text); }
  .navright{ display:flex; align-items:center; gap:22px; }
  .cart-btn{
    display:flex; align-items:center; gap:8px;
    font-family:'Heebo', sans-serif;
    font-size:0.82rem;
    border:1px solid var(--line);
    padding:9px 14px;
    border-radius:2px;
    background:transparent;
    color:var(--text);
    cursor:pointer;
    transition:border-color .2s, background .2s;
  }
  .cart-btn:hover{ border-color:var(--amber-soft); }

  /* Back to Home — sits beside the cart button in the header */
  .back-home-link{
    font-family:'Heebo', sans-serif;
    font-size:0.82rem;
    color:var(--text-dim);
    letter-spacing:0.02em;
    transition:color .2s;
  }
  .back-home-link:hover{ color:var(--amber-soft); }
  @media (max-width:520px){ .back-home-link{ display:none; } }

  .navlinks{ display:flex; }
  @media (max-width:760px){ .navlinks{display:none;} }

  /* ---------- hero ---------- */
  .hero{
    padding:96px 32px 110px;
    position:relative;
  }
  .hero-grid{
    max-width:1240px; margin:0 auto;
    display:grid; grid-template-columns:1.1fr 0.9fr;
    gap:60px; align-items:center;
  }
  /* Grid items don't shrink below their content's natural size by
     default — without this, the fixed-size vinyl visual below can
     force the whole page wider than the screen on narrow devices,
     which is what was causing the page to shimmy while scrolling. */
  .hero-grid > *{ min-width:0; }
  @media (max-width:880px){ .hero-grid{grid-template-columns:1fr; gap:64px;} }

  .eyebrow{
    font-family:'Heebo', sans-serif;
    font-size:0.78rem;
    letter-spacing:0.14em;
    color:var(--amber-soft);
    text-transform:uppercase;
    margin-bottom:22px;
    display:flex; align-items:center; gap:10px;
  }
  .eyebrow::before{
    content:""; width:24px; height:1px; background:var(--amber-soft);
  }
  .hero h1{
    font-size:clamp(2.6rem, 5.4vw, 4.4rem);
    font-weight:500;
    line-height:1.04;
    letter-spacing:-0.01em;
    margin-bottom:26px;
  }
  .hero h1 em{
    font-style:italic;
    font-weight:400;
    color:var(--amber-soft);
  }
  .hero p{
    font-size:1.08rem;
    line-height:1.6;
    color:var(--text-dim);
    max-width:440px;
    margin-bottom:36px;
  }
  .hero-ctas{ display:flex; gap:16px; align-items:center; }
  .btn-primary{
    background:var(--amber);
    color:var(--paper);
    padding:14px 26px;
    border-radius:2px;
    font-size:0.92rem;
    font-weight:600;
    letter-spacing:0.01em;
    border:none; cursor:pointer;
    transition:background .2s, transform .2s;
  }
  .btn-primary:hover{ background:var(--amber-soft); transform:translateY(-1px); }
  .btn-ghost{
    font-size:0.88rem;
    color:var(--text-dim);
    border-bottom:1px solid var(--line);
    padding-bottom:3px;
    transition:color .2s, border-color .2s;
  }
  .btn-ghost:hover{ color:var(--text); border-color:var(--text); }

  /* ---------- spinning vinyl signature ---------- */
  .platter-stage{
    position:relative;
    display:flex; align-items:center; justify-content:center;
    height:440px;
    max-width:100%;
  }
  .platter{
    position:relative;
    width:min(340px, 78vw); height:min(340px, 78vw);
  }
  .disc{
    width:100%; height:100%;
    border-radius:50%;
    background:
      repeating-radial-gradient(circle at center,
        #0c0b08 0px, #0c0b08 2px,
        #211e18 3px, #211e18 4px);
    box-shadow:0 30px 70px -20px rgba(0,0,0,0.7), 0 0 0 1px rgba(255,255,255,0.03);
    animation: spin 7s linear infinite;
    position:relative;
  }
  @keyframes spin{ to{ transform:rotate(360deg); } }
  .label{
    position:absolute; top:50%; left:50%;
    width:128px; height:128px;
    transform:translate(-50%,-50%);
    border-radius:50%;
    background: radial-gradient(circle at 35% 30%, var(--amber-soft), var(--amber) 70%);
    display:flex; align-items:center; justify-content:center;
  }
  .label-ring{
    position:absolute; inset:0;
  }
  .label-text{
    position:relative;
    width:96px; height:96px;
  }
  .spindle{
    position:absolute; top:50%; left:50%; transform:translate(-50%,-50%);
    width:7px; height:7px; border-radius:50%; background:#15130f;
  }
  .tonearm{
    position:absolute;
    top:-18px; right:6px;
    width:150px; height:150px;
    transform-origin: 88% 12%;
    transform: rotate(-18deg);
    transition: transform 1.1s cubic-bezier(.4,0,.2,1);
    pointer-events:none;
  }
  .platter-stage:hover .tonearm{ transform: rotate(4deg); }
  .tonearm svg{ width:100%; height:100%; overflow:visible; }

  .deadwax-ring{
    position:absolute; inset:-34px;
    width:min(340px, 78vw); height:min(340px, 78vw);
    animation: spin 7s linear infinite;
  }
  .deadwax-ring text{
    font-family:'Heebo', sans-serif;
    font-size:9.5px;
    letter-spacing:3px;
    fill: rgba(242,238,227,0.3);
  }

  /* ---------- strip ---------- */
  .strip{
    border-top:1px solid var(--line);
    border-bottom:1px solid var(--line);
    overflow:hidden;
    background:var(--black-soft);
    /* שורות התיקון למניעת הריצוד: */
    width: 100%;
    position: relative;
  }
  .strip-track{
    display:flex; gap:48px;
    padding:16px 0;
    white-space:nowrap;
    animation: marquee 26s linear infinite;
    width:max-content;
  }
  @keyframes marquee{ from{transform:translateX(0);} to{transform:translateX(-50%);} }
  .strip-track span{
    font-family:'Heebo', sans-serif;
    font-size:0.78rem;
    letter-spacing:0.08em;
    color:var(--text-dim);
    text-transform:uppercase;
  }
  .strip-track span.acc{ color:var(--amber-soft); }

  /* ---------- catalog ---------- */
  .catalog{ padding:110px 32px 60px; }
  .cat-head{
    display:flex; justify-content:space-between; align-items:flex-end;
    flex-wrap:wrap; gap:24px;
    margin-bottom:48px;
  }
  .cat-head h2{
    font-size:clamp(2rem, 3.4vw, 2.6rem);
    font-weight:500;
  }
  .cat-head p{ color:var(--text-dim); font-size:0.95rem; max-width:380px; margin-top:10px;}
  .filters{ display:flex; gap:10px; flex-wrap:wrap; }
  .filter{
    font-family:'Heebo', sans-serif;
    font-size:0.76rem;
    letter-spacing:0.04em;
    padding:8px 14px;
    border:1px solid var(--line);
    border-radius:20px;
    color:var(--text-dim);
    background:transparent;
    cursor:pointer;
    transition:all .2s;
  }
  .filter:hover{ color:var(--text); border-color:var(--text-dim); }
  .filter.active{ background:var(--amber); color:var(--paper); border-color:var(--amber); }

  .grid{
    display:grid;
    grid-template-columns:repeat(4, 1fr);
    gap:1px;
    background:var(--line);
    border:1px solid var(--line);
  }
  @media (max-width:980px){ .grid{grid-template-columns:repeat(2,1fr);} }
  @media (max-width:560px){ .grid{grid-template-columns:1fr;} }

  .card{
    background:var(--black);
    padding:26px 24px 22px;
    display:flex; flex-direction:column;
    transition:background .25s;
  }
  .card:hover{ background:var(--black-soft); }
  .card-cat{
    font-family:'Heebo', sans-serif;
    font-size:0.7rem;
    color:var(--text-dim);
    letter-spacing:0.06em;
    margin-bottom:14px;
    display:flex; justify-content:space-between;
  }
  .sleeve-stage{
    position:relative;
    aspect-ratio:1/1;
    margin-bottom:18px;
    perspective:900px;
  }
  .sleeve{
    position:absolute; inset:0;
    border-radius:3px;
    transition:transform .45s ease;
    box-shadow:0 18px 30px -14px rgba(0,0,0,0.6);
    z-index:2;
  }
  .mini-disc{
    position:absolute; top:6%; left:6%;
    width:88%; height:88%;
    border-radius:50%;
    background:
      repeating-radial-gradient(circle at center,
        #0c0b08 0px, #0c0b08 1.6px,
        #221f19 2.6px, #221f19 3.4px);
    z-index:1;
    transform:translateX(0%);
    transition:transform .45s ease;
    box-shadow:0 10px 24px -10px rgba(0,0,0,0.7);
  }
  .mini-disc::after{
    content:""; position:absolute; top:50%; left:50%;
    width:34%; height:34%; border-radius:50%;
    transform:translate(-50%,-50%);
    background:var(--ring-color, var(--olive));
  }
  .sleeve-stage:hover .sleeve{ transform: translateX(-14%) rotate(-3deg); }
  .sleeve-stage:hover .mini-disc{ transform: translateX(18%); }

  .card-title{ font-family:'Frank Ruhl Libre', serif; font-size:1.18rem; font-weight:500; margin-bottom:4px; }
  .card-artist{ color:var(--text-dim); font-size:0.88rem; margin-bottom:14px; }
  .card-foot{
    margin-top:auto;
    display:flex; align-items:center; justify-content:space-between;
    padding-top:14px; border-top:1px solid var(--line);
  }
  .card-price{ font-family:'Heebo', sans-serif; font-size:0.95rem; }
  .card-format{ font-size:0.72rem; color:var(--text-dim); margin-top:2px;}
  .add-btn{
    font-family:'Heebo', sans-serif;
    font-size:0.74rem;
    letter-spacing:0.03em;
    background:transparent;
    border:1px solid var(--line);
    color:var(--text);
    padding:8px 13px;
    border-radius:2px;
    cursor:pointer;
    transition:all .2s;
  }
  .add-btn:hover{ border-color:var(--amber-soft); color:var(--amber-soft); }
  .add-btn.added{ background:var(--olive); border-color:var(--olive); color:var(--paper); }

  /* "Ask about this record" link — sits under each product card */
  .ask-link{
    margin-top:10px;
    width:100%;
    font-family:'Heebo', sans-serif;
    font-size:0.76rem;
    color:var(--text-dim);
    background:transparent;
    border:1px dashed var(--line);
    border-radius:2px;
    padding:9px;
    cursor:pointer;
    transition:all .2s;
  }
  .ask-link:hover{ border-color:var(--amber-soft); color:var(--amber-soft); }

  /* ---------- inquiry chat modal ---------- */
  .inquiry-modal{
    position:fixed; z-index:96; top:50%; left:50%;
    transform:translate(-50%,-50%) scale(0.96);
    width:min(420px, 92vw);
    max-height:85vh;
    background:var(--black-soft);
    border:1px solid var(--line);
    border-radius:6px;
    display:flex; flex-direction:column;
    opacity:0; pointer-events:none;
    transition:opacity .25s, transform .25s;
  }
  .inquiry-modal.open{ opacity:1; pointer-events:auto; transform:translate(-50%,-50%) scale(1); }
  .inquiry-head{
    padding:18px 20px; border-bottom:1px solid var(--line);
    display:flex; justify-content:space-between; align-items:flex-start; gap:10px;
  }
  .inquiry-record .title{ font-family:'Frank Ruhl Libre', serif; font-size:1.05rem; }
  .inquiry-record .artist{ font-size:0.8rem; color:var(--text-dim); margin-top:2px; }
  .inquiry-close{ background:none; border:none; color:var(--text-dim); font-size:1.15rem; cursor:pointer; line-height:1; }
  .inquiry-close:hover{ color:var(--text); }
  .inquiry-chat{ padding:18px 20px; max-height:180px; overflow-y:auto; }
  .chat-bubble{
    background:var(--black); border:1px solid var(--line); border-radius:10px;
    padding:12px 14px; font-size:0.86rem; line-height:1.55; max-width:92%;
  }
  .chat-bubble.success{ border-color:var(--olive); }
  .inquiry-form{
    padding:16px 20px 20px; border-top:1px solid var(--line);
    display:flex; flex-direction:column; gap:10px;
  }
  .inquiry-form input, .inquiry-form textarea{
    background:transparent; border:1px solid var(--line); border-radius:2px;
    padding:10px 12px; color:var(--text); font-family:'Heebo', sans-serif;
    font-size:0.86rem; resize:vertical;
  }
  .inquiry-form input::placeholder, .inquiry-form textarea::placeholder{ color:var(--text-dim); }
  .inquiry-form input:focus, .inquiry-form textarea:focus{ outline:2px solid var(--amber-soft); outline-offset:2px; }

  /* ---------- about / footer ---------- */
  .about{
    padding:110px 32px;
    border-top:1px solid var(--line);
    background:var(--black-soft);
  }
  .about-grid{
    max-width:1240px; margin:0 auto;
    display:grid; grid-template-columns:0.9fr 1.1fr; gap:70px; align-items:center;
  }
  @media (max-width:880px){ .about-grid{grid-template-columns:1fr;} }
  .about h3{ font-family:'Frank Ruhl Libre', serif; font-size:2rem; font-weight:500; margin-bottom:20px; line-height:1.18;}
  .about p{ color:var(--text-dim); line-height:1.7; font-size:0.98rem; margin-bottom:16px; max-width:480px;}
  .stat-row{ display:flex; gap:50px; flex-wrap:wrap; }
  .stat .num{ font-family:'Frank Ruhl Libre', serif; font-size:2.4rem; color:var(--amber-soft); }
  .stat .lbl{ font-family:'Heebo', sans-serif; font-size:0.72rem; color:var(--text-dim); letter-spacing:0.05em; margin-top:4px;}

  footer{ padding:70px 32px 40px; }
  .foot-grid{
    max-width:1240px; margin:0 auto;
    display:grid; grid-template-columns:1.4fr 1fr 1fr;
    gap:50px;
    padding-bottom:40px; border-bottom:1px solid var(--line);
  }
  @media (max-width:760px){ .foot-grid{grid-template-columns:1fr; gap:36px;} }
  .foot-grid h4{ font-size:0.78rem; letter-spacing:0.06em; color:var(--text-dim); margin-bottom:16px; font-family:'Heebo', sans-serif;}
  .foot-links{ display:flex; flex-direction:column; gap:10px; font-size:0.9rem; }
  .foot-links a{ color:var(--text-dim); transition:color .2s; }
  .foot-links a:hover{ color:var(--text); }
  .newsletter{ display:flex; gap:0; max-width:340px; margin-top:6px;}
  .newsletter input{
    flex:1; background:transparent; border:1px solid var(--line); border-right:none;
    padding:11px 14px; color:var(--text); font-size:0.86rem; border-radius:2px 0 0 2px;
    font-family:'Heebo', sans-serif;
  }
  .newsletter input::placeholder{ color:var(--text-dim); }
  .newsletter button{
    background:var(--amber); color:var(--paper); border:none; padding:0 18px;
    font-size:0.8rem; cursor:pointer; border-radius:0 2px 2px 0; font-weight:600;
  }
  .bottom-bar{
    max-width:1240px; margin:0 auto; padding-top:24px;
    display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:14px;
    font-size:0.78rem; color:var(--text-dim); font-family:'Heebo', sans-serif;
  }

  /* ---------- cart drawer ---------- */
  .overlay{
    position:fixed; inset:0; background:rgba(10,9,7,0.55);
    opacity:0; pointer-events:none; transition:opacity .3s; z-index:90;
  }
  .overlay.open{ opacity:1; pointer-events:auto; }
  .drawer{
    position:fixed; top:0; right:0; bottom:0;
    width:min(420px, 92vw);
    background:var(--black-soft);
    border-left:1px solid var(--line);
    z-index:95;
    transform:translateX(100%);
    transition:transform .35s cubic-bezier(.4,0,.2,1);
    display:flex; flex-direction:column;
  }
  .drawer.open{ transform:translateX(0); }
  .drawer-head{
    padding:26px 26px 20px; border-bottom:1px solid var(--line);
    display:flex; justify-content:space-between; align-items:center;
  }
  .drawer-head h3{ font-family:'Frank Ruhl Libre', serif; font-size:1.3rem; font-weight:500;}
  .drawer-close{ background:none; border:none; color:var(--text-dim); font-size:1.3rem; cursor:pointer; line-height:1; }
  .drawer-close:hover{ color:var(--text); }
  .drawer-items{ flex:1; overflow-y:auto; padding:10px 26px; }
  .drawer-item{
    display:flex; gap:14px; padding:18px 0; border-bottom:1px solid var(--line);
  }
  .di-swatch{ width:54px; height:54px; border-radius:2px; flex-shrink:0; }
  .di-info{ flex:1; }
  .di-title{ font-size:0.92rem; font-weight:500; }
  .di-artist{ font-size:0.78rem; color:var(--text-dim); margin-top:2px;}
  .di-bottom{ display:flex; justify-content:space-between; align-items:center; margin-top:8px;}
  .di-price{ font-family:'Heebo', sans-serif; font-size:0.84rem;}
  .di-remove{ background:none; border:none; color:var(--text-dim); font-size:0.74rem; cursor:pointer; text-decoration:underline; font-family:'Heebo', sans-serif;}
  .di-remove:hover{ color:var(--amber-soft); }
  .drawer-empty{ padding:60px 0; text-align:center; color:var(--text-dim); font-size:0.9rem; }
  .drawer-foot{ padding:22px 26px 28px; border-top:1px solid var(--line); }
  .df-row{ display:flex; justify-content:space-between; font-family:'Heebo', sans-serif; font-size:0.9rem; margin-bottom:18px;}
  .checkout-btn{
    width:100%; background:var(--amber); color:var(--paper); border:none;
    padding:15px; font-size:0.92rem; font-weight:600; border-radius:2px; cursor:pointer;
    transition:background .2s;
  }
  .checkout-btn:hover{ background:var(--amber-soft); }
  .checkout-note{ font-size:0.74rem; color:var(--text-dim); text-align:center; margin-top:12px;}

  .toast{
    position:fixed; bottom:28px; left:50%; transform:translateX(-50%) translateY(20px);
    background:var(--cream); color:var(--black); padding:13px 22px; border-radius:3px;
    font-family:'Heebo', sans-serif; font-size:0.82rem;
    opacity:0; pointer-events:none; transition:all .3s; z-index:99;
  }
  .toast.show{ opacity:1; transform:translateX(-50%) translateY(0); }
</style>
</head>
<body>

<header>
  <nav class="nav wrap" style="padding-left:0;padding-right:0;">
    <div class="logo"><span class="dot"></span>FIND BEST RECORDS</div>
    <div class="navlinks">
      <a href="#catalog">חנות</a>
      <a href="#catalog">ז'אנרים</a>
      <a href="#about">אודות</a>
    </div>
    <div class="navright">
      <!-- חזרה לדף הבית: מוביל לעמוד הנחיתה (index.html) -->
      <a href="index.html" class="back-home-link">→ חזרה לדף הבית</a>
      <button class="cart-btn" id="cartOpenBtn">עגלה · <span id="cartCount">0</span></button>
    </div>
  </nav>
</header>

<section class="hero">
  <div class="hero-grid">
    <div>
      <div class="eyebrow">קיימים במהדורות מוגבלות</div>
      <h1>תקליטים שנבחרו<br>במיוחד <em>בשבילכם!</em></h1>
      <p>כל עטיפה כאן נבדקה, הושמעה מקצה לקצה ודורגה ביד. בלי סחורת מילוי זולה — רק הפקות ששוות מקום על המדף.</p>
      <div class="hero-ctas">
        <button class="btn-primary" onclick="document.getElementById('catalog').scrollIntoView({behavior:'smooth'})">לצפייה בקטלוג</button>
        <a class="btn-ghost" href="#about">איך אנחנו מדרגים ←</a>
      </div>
    </div>
    <div class="platter-stage">
      <svg class="deadwax-ring" viewBox="0 0 340 340" width="340" height="340">
        <defs>
          <path id="ringpath" d="M 170,30 A 140,140 0 1,1 169.9,30"></path>
        </defs>
        <text>
          <textPath href="#ringpath" startOffset="0%">
            FIND BEST RECORDS · הפקות נבחרות ביד · צד א׳ · FBR-001 ·
          </textPath>
        </text>
      </svg>
      <div class="platter">
        <div class="disc">
          <div class="label">
            <span class="mono" style="font-size:0.55rem; letter-spacing:0.06em; color:#15130f; text-align:center; line-height:1.4;">FBR<br>33⅓ RPM</span>
          </div>
          <div class="spindle"></div>
        </div>
      </div>
      <div class="tonearm">
        <svg viewBox="0 0 150 150">
          <circle cx="128" cy="22" r="9" fill="#3a362c"/>
          <line x1="128" y1="22" x2="32" y2="118" stroke="#3a362c" stroke-width="5" stroke-linecap="round"/>
          <rect x="18" y="110" width="22" height="11" rx="2" fill="#c9501f"/>
        </svg>
      </div>
    </div>
  </div>
</section>

<div class="strip">
  <div class="strip-track" id="stripTrack"></div>
</div>

<section class="catalog" id="catalog">
  <div class="wrap">
    <div class="cat-head">
      <div>
        <h2>הקטלוג</h2>
        <p>שישה עשר תקליטים במלאי השבוע. הגעות חדשות בכל יום שישי.</p>
      </div>
      <div class="filters" id="filters"></div>
    </div>
    <div class="grid" id="grid"></div>
  </div>
</section>

<section class="about" id="about">
  <div class="about-grid">
    <div>
      <h3>מדורגים כמו שאספן אמיתי מדרג.</h3>
      <p>כל תקליט עובר בדיקה חזותית והאזנה מלאה מקצה לקצה לפני שהוא עולה למכירה. אנחנו מציינים רעשי משטח, בלאי בעטיפה וכל חוסר מילוי — כדי שמה שאתם רואים הוא בדיוק מה שינגן אצלכם.</p>
      <p>הזמנות נשלחות בימי שלישי ושישי באריזה קשיחה, כשהתקליט ארוז בנפרד מהעטיפה.</p>
    </div>
    <div class="stat-row">
      <div class="stat"><div class="num">1,400+</div><div class="lbl">תקליטים דורגו השנה</div></div>
      <div class="stat"><div class="num">VG+</div><div class="lbl">דירוג מינימלי למכירה</div></div>
      <div class="stat"><div class="num">48 שעות</div><div class="lbl">זמן משלוח ממוצע</div></div>
    </div>
  </div>
</section>

<footer>
  <div class="foot-grid">
    <div>
      <div class="logo" style="margin-bottom:14px;"><span class="dot"></span>FIND BEST RECORDS</div>
      <p style="color:var(--text-dim); font-size:0.88rem; max-width:300px; line-height:1.6; margin-bottom:20px;">קבלו עדכון כשמגיעות הפקות חדשות — בדרך כלל פעם בשבוע, לא יותר.</p>
      <div class="newsletter">
        <input type="email" placeholder="you@email.com" aria-label="כתובת אימייל">
        <button onclick="subscribe()">הרשמה</button>
      </div>
    </div>
    <div>
      <h4>חנות</h4>
      <div class="foot-links">
        <a href="#catalog">הגעות חדשות</a>
        <a href="#catalog">כל הז'אנרים</a>
        <a href="#about">מדריך דירוג</a>
      </div>
    </div>
    <div>
      <h4>תמיכה</h4>
      <div class="foot-links">
        <a href="#">משלוחים והחזרות</a>
        <a href="#">מעקב אחר הזמנה</a>
        <a href="#">צור קשר</a>
      </div>
    </div>
  </div>
  <div class="bottom-bar" style="flex-direction:column; align-items:flex-start; gap:6px;">
    <div style="display:flex; justify-content:space-between; width:100%; flex-wrap:wrap; gap:14px;">
      <span>© 2026 FIND BEST RECORDS</span>
      <span>קיימים במהדורות מוגבלות, נשלחים בקפידה</span>
    </div>
    <span>תקליטים שנבחרו במיוחד בשבילכם</span>
  </div>
</footer>

<div class="overlay" id="overlay" onclick="closeDrawer()"></div>
<aside class="drawer" id="drawer" aria-label="עגלת קניות">
  <div class="drawer-head">
    <h3>הארגז שלכם</h3>
    <button class="drawer-close" onclick="closeDrawer()" aria-label="סגירת עגלה">✕</button>
  </div>
  <div class="drawer-items" id="drawerItems"></div>
  <div class="drawer-foot">
    <div class="df-row"><span>סה"כ ביניים</span><span id="subtotal">$0.00</span></div>
    <button class="checkout-btn" id="checkoutBtn" onclick="checkout()">שליחת הזמנה לוואטסאפ</button>
    <div class="checkout-note">תיאום תשלום ומשלוח ייעשה מולנו ישירות בוואטסאפ</div>
  </div>
</aside>

<!-- ============================================
     INQUIRY MODAL
     "Ask about this record" — opened from a button on
     each product card. Front-end only for now; see the
     JS comment near sendInquiry() for wiring up real
     delivery (email/Slack/WhatsApp) of these messages.
============================================ -->
<div class="overlay" id="inquiryOverlay" onclick="closeInquiry()"></div>
<div class="inquiry-modal" id="inquiryModal" role="dialog" aria-label="שאלה על התקליט">
  <div class="inquiry-head">
    <div class="inquiry-record" id="inquiryRecordInfo"></div>
    <button class="inquiry-close" onclick="closeInquiry()" aria-label="סגירה">✕</button>
  </div>
  <div class="inquiry-chat">
    <div class="chat-bubble" id="inquiryBotBubble"></div>
  </div>
  <form class="inquiry-form" id="inquiryForm">
    <input type="text" id="inquiryName" placeholder="שם מלא" required>
    <input type="text" id="inquiryContact" placeholder="טלפון או אימייל" required>
    <textarea id="inquiryMessage" rows="3" placeholder="ההודעה שלכם..."></textarea>
    <button type="submit" class="btn-primary" style="width:100%;">שליחת הודעה</button>
  </form>
</div>

<div class="toast" id="toast"></div>

<script>
const RECORDS = [
  {id:1, cat:'FBR-014-A', title:'Midnight Cartography', artist:'Glass Harbor', genre:'Jazz', price:32, format:'180g LP · שחור', ring:'#6e7456', sleeve:'linear-gradient(155deg,#2b3b3a,#0f1716 60%)'},
  {id:2, cat:'FBR-019-A', title:'Low Static', artist:'Vesper Cole', genre:'Soul', price:28, format:'LP · שחור', ring:'#c9501f', sleeve:'linear-gradient(155deg,#3a2418,#170f0a 65%)'},
  {id:3, cat:'FBR-022-A', title:'Concrete Orchard', artist:'The Tin Foxes', genre:'Rock', price:30, format:'180g LP · שחור', ring:'#8b7355', sleeve:'linear-gradient(155deg,#3c3328,#15120d 60%)'},
  {id:4, cat:'FBR-031-A', title:'Phosphene', artist:'Auric Drift', genre:'Electronic', price:34, format:'LP · שקוף', ring:'#4a6b6e', sleeve:'linear-gradient(155deg,#1f3438,#0c1517 60%)'},
  {id:5, cat:'FBR-008-A', title:'Dust & Diesel', artist:'Mara Lune', genre:'Folk', price:26, format:'LP · שחור', ring:'#a87c3f', sleeve:'linear-gradient(155deg,#3d3220,#16120a 60%)'},
  {id:6, cat:'FBR-040-A', title:'Open Channel', artist:'Echo Valve', genre:'Hip-Hop', price:29, format:'LP · שחור', ring:'#c9501f', sleeve:'linear-gradient(155deg,#34211c,#120c0a 60%)'},
  {id:7, cat:'FBR-027-A', title:'Salt Lung', artist:'Coral Index', genre:'Rock', price:31, format:'180g LP · מנומר', ring:'#6e7456', sleeve:'linear-gradient(155deg,#27332a,#0e1310 60%)'},
  {id:8, cat:'FBR-011-A', title:'Marigold Static', artist:'Hollow Pine', genre:'Soul', price:27, format:'LP · שחור', ring:'#c98a1f', sleeve:'linear-gradient(155deg,#3a2e16,#15110a 60%)'},
  {id:9, cat:'FBR-036-A', title:'Tidewater', artist:'Glass Harbor', genre:'Jazz', price:33, format:'LP · שחור', ring:'#4a6b6e', sleeve:'linear-gradient(155deg,#1c2e34,#0b1416 60%)'},
  {id:10, cat:'FBR-045-A', title:'Halflight', artist:'Auric Drift', genre:'Electronic', price:36, format:'180g LP · שחור', ring:'#8b7355', sleeve:'linear-gradient(155deg,#241f30,#0c0a14 60%)'},
  {id:11, cat:'FBR-017-A', title:'Wrought Iron Hymn', artist:'The Tin Foxes', genre:'Rock', price:29, format:'LP · שחור', ring:'#c9501f', sleeve:'linear-gradient(155deg,#3a261c,#140d0a 60%)'},
  {id:12, cat:'FBR-052-A', title:'Paper Moon Static', artist:'Echo Valve', genre:'Hip-Hop', price:30, format:'LP · משויש', ring:'#6e7456', sleeve:'linear-gradient(155deg,#272f1e,#0e120c 60%)'},
  {id:13, cat:'FBR-009-A', title:'Backroad Choir', artist:'Mara Lune', genre:'Folk', price:25, format:'LP · שחור', ring:'#a87c3f', sleeve:'linear-gradient(155deg,#3d3322,#15120c 60%)'},
  {id:14, cat:'FBR-029-A', title:'Coral Index II', artist:'Coral Index', genre:'Rock', price:32, format:'180g LP · שחור', ring:'#4a6b6e', sleeve:'linear-gradient(155deg,#202d33,#0c1315 60%)'},
  {id:15, cat:'FBR-021-A', title:'Hollow Pine, Pt. 2', artist:'Hollow Pine', genre:'Soul', price:28, format:'LP · שחור', ring:'#c98a1f', sleeve:'linear-gradient(155deg,#382c19,#14100a 60%)'},
  {id:16, cat:'FBR-038-A', title:'Vesper Cole Live', artist:'Vesper Cole', genre:'Soul', price:38, format:'2LP · שחור', ring:'#c9501f', sleeve:'linear-gradient(155deg,#34221a,#120d0a 60%)'},
];

// Genre codes stay in English internally (used for filtering/data-*
// attributes); this map supplies the Hebrew label shown to the user.
const GENRE_LABELS = {
  All: 'הכל',
  Jazz: "ג'אז",
  Soul: 'סול',
  Rock: 'רוק',
  Electronic: 'אלקטרוני',
  Folk: 'פולק',
  'Hip-Hop': 'היפ הופ'
};

const genres = ['All', ...Array.from(new Set(RECORDS.map(r=>r.genre)))];
let activeGenre = 'All';
let cart = [];

function renderFilters(){
  const el = document.getElementById('filters');
  el.innerHTML = genres.map(g =>
    `<button class="filter ${g===activeGenre?'active':''}" data-genre="${g}">${GENRE_LABELS[g] || g}</button>`
  ).join('');
  el.querySelectorAll('.filter').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      activeGenre = btn.dataset.genre;
      renderFilters();
      renderGrid();
    });
  });
}

function renderGrid(){
  const list = activeGenre==='All' ? RECORDS : RECORDS.filter(r=>r.genre===activeGenre);
  const grid = document.getElementById('grid');
  grid.innerHTML = list.map(r => `
    <div class="card">
      <div class="card-cat"><span>${r.cat}</span><span>${(GENRE_LABELS[r.genre] || r.genre)}</span></div>
      <div class="sleeve-stage">
        <div class="mini-disc" style="--ring-color:${r.ring}"></div>
        <div class="sleeve" style="background:${r.sleeve}"></div>
      </div>
      <div class="card-title">${r.title}</div>
      <div class="card-artist">${r.artist}</div>
      <div class="card-foot">
        <div>
          <div class="card-price">₪${r.price.toFixed(2)}</div>
          <div class="card-format">${r.format}</div>
        </div>
        <button class="add-btn" data-id="${r.id}">+ הוספה</button>
      </div>
      <button class="ask-link" data-id="${r.id}">יש שאלה? בררו זמינות ←</button>
    </div>
  `).join('');
  grid.querySelectorAll('.add-btn').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      addToCart(parseInt(btn.dataset.id));
      btn.textContent = 'נוסף ✓';
      btn.classList.add('added');
      setTimeout(()=>{ btn.textContent='+ הוספה'; btn.classList.remove('added'); }, 1100);
    });
  });
  grid.querySelectorAll('.ask-link').forEach(btn=>{
    btn.addEventListener('click', ()=> openInquiry(parseInt(btn.dataset.id)));
  });
}

function addToCart(id){
  const rec = RECORDS.find(r=>r.id===id);
  const existing = cart.find(c=>c.id===id);
  if(existing){ existing.qty += 1; } else { cart.push({...rec, qty:1}); }
  updateCartUI();
  showToast(`${rec.title} נוסף לארגז שלכם`);
}

function removeFromCart(id){
  cart = cart.filter(c=>c.id!==id);
  updateCartUI();
}

function updateCartUI(){
  document.getElementById('cartCount').textContent = cart.reduce((a,c)=>a+c.qty,0);
  const itemsEl = document.getElementById('drawerItems');
  if(cart.length===0){
    itemsEl.innerHTML = `<div class="drawer-empty">הארגז שלכם ריק.<br>לכו לחפור משהו טוב.</div>`;
  } else {
    itemsEl.innerHTML = cart.map(c => `
      <div class="drawer-item">
        <div class="di-swatch" style="background:${c.sleeve}"></div>
        <div class="di-info">
          <div class="di-title">${c.title} ${c.qty>1 ? `× ${c.qty}` : ''}</div>
          <div class="di-artist">${c.artist}</div>
          <div class="di-bottom">
            <div class="di-price">₪${(c.price*c.qty).toFixed(2)}</div>
            <button class="di-remove" data-id="${c.id}">הסרה</button>
          </div>
        </div>
      </div>
    `).join('');
    itemsEl.querySelectorAll('.di-remove').forEach(btn=>{
      btn.addEventListener('click', ()=> removeFromCart(parseInt(btn.dataset.id)));
    });
  }
  const subtotal = cart.reduce((a,c)=>a+c.price*c.qty,0);
  document.getElementById('subtotal').textContent = `₪${subtotal.toFixed(2)}`;
}

function openDrawer(){
  document.getElementById('drawer').classList.add('open');
  document.getElementById('overlay').classList.add('open');
}
function closeDrawer(){
  document.getElementById('drawer').classList.remove('open');
  document.getElementById('overlay').classList.remove('open');
}
document.getElementById('cartOpenBtn').addEventListener('click', openDrawer);

let toastTimer;
function showToast(msg){
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(()=> t.classList.remove('show'), 2200);
}

// ------------------------------------------------------------
// CHECKOUT — sends the order straight to WhatsApp instead of a
// card-payment flow. Builds a clean, formatted order summary from
// the cart, then opens WhatsApp (wa.me) with that message pre-filled
// and addressed to the store's WhatsApp number. Payment itself
// (Bit/PayBox) and delivery are then coordinated directly in the chat.
// ------------------------------------------------------------
function checkout(){
  if(cart.length===0){ showToast('הארגז שלכם ריק'); return; }

  // Store's WhatsApp number in international format (no leading 0).
  const phoneNumber = "972508450542";

  let message = "היי צ'ילי, אני רוצה לבצע הזמנה של תקליטים מהאתר Find Best Records!\n\n";
  message += "🛒 *פירוט ההזמנה:*\n";

  cart.forEach((item, index) => {
    const lineTotal = item.price * item.qty;
    message += `${index + 1}. *${item.title}* — ${item.artist} (${item.format}) x${item.qty} — ₪${lineTotal}\n`;
  });

  const total = cart.reduce((sum, item) => sum + item.price * item.qty, 0);
  message += `\n💰 *סך הכל לתשלום:* ₪${total}\n\n`;
  message += "אשמח שתחזרו אליי לתיאום תשלום (ביט/פייבוקס) ומשלוח. תודה!";

  const encodedMessage = encodeURIComponent(message);
  const whatsappUrl = `https://wa.me/${phoneNumber}?text=${encodedMessage}`;
  window.open(whatsappUrl, '_blank');
}

function subscribe(){
  showToast('זו חנות הדגמה — אין עדיין הרשמה אמיתית.');
}

// ------------------------------------------------------------
// PRODUCT INQUIRY ("ask about this record") — a small chat-style
// box opened from each product card, similar to "ask the seller
// a question" on eBay. Currently front-end only.
//
// To make this actually reach you, send `inquiryPayload` to a
// real destination when the form is submitted, e.g.:
//   - Formspree / Getform (no backend needed, just a form endpoint):
//       await fetch('https://formspree.io/f/YOUR_FORM_ID', {
//         method: 'POST',
//         headers: { 'Content-Type': 'application/json' },
//         body: JSON.stringify(inquiryPayload)
//       });
//   - Or your own backend route, which could then email you,
//     post to Slack, or forward to WhatsApp.
// ------------------------------------------------------------
let currentInquiryRecord = null;

function openInquiry(id){
  const rec = RECORDS.find(r=>r.id===id);
  if(!rec) return;
  currentInquiryRecord = rec;

  document.getElementById('inquiryRecordInfo').innerHTML = `
    <div class="title">${rec.title}</div>
    <div class="artist">${rec.artist} · ${rec.cat}</div>
  `;
  document.getElementById('inquiryBotBubble').innerHTML =
    `שלום! יש לכם שאלה לגבי <strong>${rec.title}</strong>? השאירו פרטים ונחזור אליכם עם זמינות מדויקת.`;

  const form = document.getElementById('inquiryForm');
  form.style.display = 'flex';
  document.getElementById('inquiryName').value = '';
  document.getElementById('inquiryContact').value = '';
  document.getElementById('inquiryMessage').value =
    `שלום, מתעניין/ת ב"${rec.title}" של ${rec.artist} — האם זה זמין במלאי?`;

  document.getElementById('inquiryOverlay').classList.add('open');
  document.getElementById('inquiryModal').classList.add('open');
}

function closeInquiry(){
  document.getElementById('inquiryOverlay').classList.remove('open');
  document.getElementById('inquiryModal').classList.remove('open');
}

document.getElementById('inquiryForm').addEventListener('submit', function(e){
  e.preventDefault();
  if(!currentInquiryRecord) return;

  const name = document.getElementById('inquiryName').value.trim();
  const contact = document.getElementById('inquiryContact').value.trim();
  const message = document.getElementById('inquiryMessage').value.trim();
  if(!name || !contact) return;

  const inquiryPayload = {
    recordId: currentInquiryRecord.id,
    recordTitle: currentInquiryRecord.title,
    artist: currentInquiryRecord.artist,
    sku: currentInquiryRecord.cat,
    name,
    contact,
    message,
    createdAt: new Date().toISOString()
  };

  // Placeholder — swap for a real request (see comment above).
  console.log('[inquiry] ready to send:', inquiryPayload);

  document.getElementById('inquiryBotBubble').innerHTML =
    `תודה, ${name}! קיבלנו את הפנייה לגבי <strong>${currentInquiryRecord.title}</strong> ונחזור אליכם בהקדם ל-${contact}.`;
  document.getElementById('inquiryForm').style.display = 'none';

  setTimeout(closeInquiry, 2600);
});

function renderStrip(){
  const words = ['הגעות חדשות בימי שישי', 'דירוג ידני', 'דירוג מינימלי VG+', 'משלוח באריזה קשיחה', 'הפקות במהדורות מוגבלות', 'בלי סחורת מילוי זולה'];
  const html = words.map((w,i)=>`<span class="${i%2===0?'acc':''}">${w}</span>`).join('');
  document.getElementById('stripTrack').innerHTML = html + html; // duplicate for seamless loop
}

renderFilters();
renderGrid();
updateCartUI();
renderStrip();
</script>

</body>
</html>
