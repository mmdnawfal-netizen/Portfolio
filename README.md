<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Mohamed Nawfal M — Video Editor</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
<style>
:root{
  --bg:#0B0B0D;
  --card:#151517;
  --text:#F2F2F2;
  --muted:#9A9AA2;
  --accent:#00C2CC;
  --line: rgba(255,255,255,.08);
  --font-head:'Space Grotesk', sans-serif;
  --font-body:'Inter', sans-serif;
}
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{background:var(--bg); color:var(--text); font-family:var(--font-body); line-height:1.6;}
a{color:inherit; text-decoration:none;}
img{max-width:100%; display:block;}
.container{max-width:1040px; margin:0 auto; padding:0 24px;}
section{padding:90px 0;}
@media (max-width:640px){ section{padding:60px 0;} }
h1,h2,h3{font-family:var(--font-head); font-weight:600;}
.eyebrow{font-size:.78rem; letter-spacing:.15em; text-transform:uppercase; color:var(--accent); margin-bottom:12px;}
.section-title{font-size:clamp(1.7rem,3.4vw,2.4rem); margin-bottom:14px;}
.section-sub{color:var(--muted); max-width:560px; font-size:.98rem;}

/* fade in on scroll, subtle */
.reveal{opacity:0; transform:translateY(16px); transition:opacity .6s ease, transform .6s ease;}
.reveal.in-view{opacity:1; transform:translateY(0);}

/* NAV */
nav{
  position:sticky; top:0; z-index:50; display:flex; align-items:center; justify-content:space-between;
  padding:20px 24px; background:rgba(11,11,13,.85); backdrop-filter:blur(10px); border-bottom:1px solid var(--line);
}
.logo{font-family:var(--font-head); font-weight:700; font-size:1.1rem;}
.logo span{color:var(--accent);}
.nav-links{display:flex; gap:28px; list-style:none;}
.nav-links a{font-size:.86rem; color:var(--muted); transition:color .2s;}
.nav-links a:hover{color:var(--text);}
@media (max-width:720px){ .nav-links{display:none;} }
.nav-cta{padding:9px 18px; border-radius:8px; background:var(--accent); color:#06131a; font-size:.82rem; font-weight:600;}

/* HERO */
.hero{padding:100px 0 80px; text-align:center;}
.hero-tag{font-size:.8rem; letter-spacing:.15em; text-transform:uppercase; color:var(--muted); margin-bottom:18px;}
.hero h1{font-size:clamp(2rem,5.5vw,3.2rem); line-height:1.15;}
.hero h1 span{color:var(--accent);}
.hero-sub{margin:18px auto 0; max-width:480px; color:var(--muted); font-size:1.02rem;}
.hero-ctas{display:flex; gap:14px; justify-content:center; margin-top:32px; flex-wrap:wrap;}
.btn{padding:13px 26px; border-radius:8px; font-size:.9rem; font-weight:600; font-family:var(--font-head); display:inline-flex; align-items:center; gap:8px; transition:opacity .2s, background .2s;}
.btn-primary{background:var(--accent); color:#06131a;}
.btn-primary:hover{opacity:.9;}
.btn-outline{border:1px solid var(--line); color:var(--text);}
.btn-outline:hover{border-color:var(--accent); color:var(--accent);}

/* SHOWREEL */
.reel-frame{border-radius:12px; overflow:hidden; border:1px solid var(--line); margin-top:20px;}
.reel-frame video{width:100%; display:block; aspect-ratio:16/9; object-fit:cover;}

/* SERVICES */
.grid{display:grid; grid-template-columns:repeat(3,1fr); gap:14px; margin-top:36px;}
@media (max-width:760px){ .grid{grid-template-columns:repeat(2,1fr);} }
@media (max-width:480px){ .grid{grid-template-columns:1fr;} }
.card{background:var(--card); border:1px solid var(--line); border-radius:12px; padding:22px;}
.card i{color:var(--accent); font-size:1.1rem; margin-bottom:12px; display:block;}
.card h3{font-size:.98rem; margin-bottom:6px;}
.card p{font-size:.84rem; color:var(--muted);}

/* PORTFOLIO */
.p-grid{display:grid; grid-template-columns:repeat(3,1fr); gap:16px; margin-top:36px;}
@media (max-width:760px){ .p-grid{grid-template-columns:repeat(2,1fr);} }
@media (max-width:480px){ .p-grid{grid-template-columns:1fr;} }
.p-card{border-radius:12px; overflow:hidden; border:1px solid var(--line); background:var(--card);}
.p-thumb{aspect-ratio:16/10; display:flex; align-items:center; justify-content:center; position:relative;}
.p-thumb i{font-size:1.6rem; color:rgba(255,255,255,.3);}
.thumb-1{background:linear-gradient(135deg,#0d3a3f,#0B0B0D);}
.thumb-2{background:linear-gradient(135deg,#2a1a45,#0B0B0D);}
.thumb-3{background:linear-gradient(135deg,#003a3f,#0B0B0D);}
.thumb-4{background:linear-gradient(135deg,#1f0d3a,#0B0B0D);}
.thumb-5{background:linear-gradient(135deg,#3a1030,#0B0B0D);}
.thumb-6{background:linear-gradient(135deg,#063a2f,#0B0B0D);}
.p-body{padding:16px 18px 20px;}
.p-cat{font-size:.68rem; letter-spacing:.1em; text-transform:uppercase; color:var(--accent);}
.p-body h3{font-size:.96rem; margin:6px 0;}
.p-body p{font-size:.82rem; color:var(--muted);}

/* SKILLS */
.tags{display:flex; flex-wrap:wrap; gap:10px; margin-top:28px;}
.tag{padding:9px 16px; border-radius:100px; border:1px solid var(--line); font-size:.83rem; color:var(--muted);}

/* ABOUT */
.about-wrap{display:grid; grid-template-columns:.7fr 1.3fr; gap:40px; align-items:center;}
@media (max-width:720px){ .about-wrap{grid-template-columns:1fr;} }
.avatar{aspect-ratio:1; border-radius:16px; background:var(--card); border:1px solid var(--line); display:flex; align-items:center; justify-content:center;}
.avatar span{font-family:var(--font-head); font-size:3rem; color:var(--accent);}
.about-wrap p{color:var(--muted); margin-bottom:14px; font-size:.96rem;}

/* CONTACT */
.contact-wrap{display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-top:32px;}
@media (max-width:640px){ .contact-wrap{grid-template-columns:1fr;} }
.contact-card{background:var(--card); border:1px solid var(--line); border-radius:12px; padding:22px; display:flex; align-items:center; gap:14px;}
.contact-card i{color:var(--accent); font-size:1.1rem;}
.contact-card .label{font-size:.72rem; color:var(--muted); text-transform:uppercase; letter-spacing:.08em;}
.contact-card .value{font-size:.94rem; font-weight:500;}
.social-row{display:flex; gap:10px; margin-top:24px;}
.social-icon{width:38px; height:38px; border-radius:8px; border:1px solid var(--line); display:flex; align-items:center; justify-content:center; transition:.2s;}
.social-icon:hover{border-color:var(--accent); color:var(--accent);}

footer{padding:30px 0; border-top:1px solid var(--line); text-align:center; color:var(--muted); font-size:.82rem;}
.contact-form{
    max-width:700px;
    margin:40px auto 0;
}

.form-group{
    margin-bottom:18px;
}

.contact-form input,
.contact-form textarea{
    width:100%;
    background:var(--card);
    border:1px solid var(--line);
    color:var(--text);
    padding:16px;
    border-radius:10px;
    font-size:15px;
    font-family:var(--font-body);
    transition:.3s;
}

.contact-form input:focus,
.contact-form textarea:focus{
    outline:none;
    border-color:var(--accent);
    box-shadow:0 0 0 3px rgba(0,194,204,.15);
}

.contact-form textarea{
    resize:vertical;
    min-height:160px;
}
</style>
</head>
<body>

<nav>
  <div class="logo">NAWFAL<span>.</span></div>
  <ul class="nav-links">
    <li><a href="#work">Work</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="#contact" class="nav-cta">Hire Me</a>
</nav>

<section class="hero">
  <div class="container">
    <div class="hero-tag">Freelance Video Editor</div>
    <h1>Mohamed Nawfal M — <span>turning raw footage into stories.</span></h1>
    <p class="hero-sub">I edit YouTube videos, reels, promos and short-form content with clean cuts, color grading and sound design.</p>
    <div class="hero-ctas">
      <a href="#work" class="btn btn-primary">View Portfolio</a>
      <a href="#contact" class="btn btn-outline">Hire Me</a>
    </div>
  </div>
</section>

<section id="showreel" style="padding-top:0;">
  <div class="container">
    <div class="eyebrow reveal">Showreel</div>
    <h2 class="section-title reveal">A quick look at my editing.</h2>
    <div class="reel-frame reveal">
      <video autoplay muted loop playsinline>
        <source src="edit.mp4" type="video/mp4">
      </video>
    </div>
  </div>
</section>

<section id="services">
  <div class="container">
    <div class="eyebrow reveal">Services</div>
    <h2 class="section-title reveal">What I can help with</h2>
    <p class="section-sub reveal">Editing services for creators, brands and small businesses.</p>
    <div class="grid">
      <div class="card reveal"><i class="fa-brands fa-youtube"></i><h3>YouTube Editing</h3><p>Engaging cuts built to keep viewers watching.</p></div>
      <div class="card reveal"><i class="fa-brands fa-instagram"></i><h3>Reels & Shorts</h3><p>Short-form edits for Instagram, TikTok and Shorts.</p></div>
      <div class="card reveal"><i class="fa-solid fa-bullhorn"></i><h3>Promo & Ads</h3><p>Promotional videos and simple ad edits.</p></div>
      <div class="card reveal"><i class="fa-solid fa-palette"></i><h3>Color Grading</h3><p>Consistent, clean color grading for any footage.</p></div>
      <div class="card reveal"><i class="fa-solid fa-microphone-lines"></i><h3>Podcast Editing</h3><p>Trimmed, clean audio and clip-ready segments.</p></div>
      <div class="card reveal"><i class="fa-solid fa-wand-magic-sparkles"></i><h3>Motion Graphics</h3><p>Simple titles, text animation and overlays.</p></div>
    </div>
  </div>
</section>



<section id="skills" style="padding-top:0;">
  <div class="container">
    <div class="eyebrow reveal">Skills & Software</div>
    <h2 class="section-title reveal">Tools I work with</h2>
    <div class="tags">
      <span class="tag reveal">Premiere Pro</span>
      <span class="tag reveal">After Effects</span>
      <span class="tag reveal">DaVinci Resolve</span>
      <span class="tag reveal">CapCut Pro</span>
      <span class="tag reveal">Photoshop</span>
      <span class="tag reveal">Audition</span>
      <span class="tag reveal">Storytelling</span>
      <span class="tag reveal">Color Grading</span>
      <span class="tag reveal">Sound Design</span>
      <span class="tag reveal">Transitions</span>
    </div>
  </div>
</section>

<section id="about">
  <div class="container">
    <div class="about-wrap">
      <div class="avatar reveal"><span>MN</span></div>
      <div class="reveal">
        <div class="eyebrow">About Me</div>
        <h2 class="section-title">Hi, I'm Nawfal.</h2>
        <p>I'm a freelance video editor who enjoys turning raw footage into clear, engaging stories — for YouTube, social media and small brand projects.</p>
        <p>I focus on clean editing, simple color grading and good pacing, and I'm always happy to revise until the video feels right.</p>
      </div>
    </div>
  </div>
</section>

<section id="contact">
  <div class="container">
    <div class="eyebrow reveal">Contact</div>
    <h2 class="section-title reveal">Let's Work Together</h2>
    <p class="section-sub reveal">
      Tell me about your project and I'll get back to you as soon as possible.
    </p>

    <form class="contact-form reveal"
      action="https://formsubmit.co/mmdnawfal@gmail.com"
      method="POST">

      <!-- Replace with your email -->
      <input type="hidden" name="_captcha" value="false">
      <input type="hidden" name="_subject" value="New Portfolio Enquiry">

      <div class="form-group">
        <input type="text" name="name" placeholder="Your Name" required>
      </div>

      <div class="form-group">
        <input type="email" name="email" placeholder="Your Email" required>
      </div>

      <div class="form-group">
        <input type="text" name="subject" placeholder="Project Type">
      </div>

      <div class="form-group">
        <textarea name="message" rows="6"
          placeholder="Tell me about your project..."
          required></textarea>
      </div>

      <button type="submit" class="btn btn-primary">
        Send Enquiry
      </button>

    </form>
  </div>
</section>
  </div>
</section>

<footer>© 2026 Mohamed Nawfal M</footer>

<script>
const els = document.querySelectorAll('.reveal');
const io = new IntersectionObserver(entries=>{
  entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('in-view'); io.unobserve(e.target); } });
}, { threshold:0.15 });
els.forEach(el=>io.observe(el));
</script>
</body>
</html>
