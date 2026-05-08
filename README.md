<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FRAME — Intelligence & Research</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Mono:wght@300;400&family=Playfair+Display:ital@1&display=swap" rel="stylesheet">
<style>
:root{--black:#0a0a0a;--white:#f2ede8;--red:#c8392b;--grey:#222}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{background:var(--black);color:var(--white);font-family:'DM Mono',monospace;font-weight:300;overflow-x:hidden}

nav{position:fixed;top:0;left:0;right:0;padding:1.8rem 3rem;display:flex;justify-content:space-between;align-items:center;z-index:100;border-bottom:1px solid rgba(255,255,255,0.05);background:rgba(10,10,10,0.9);backdrop-filter:blur(10px)}
.nav-logo{font-family:‘Bebas Neue’,sans-serif;font-size:1.6rem;letter-spacing:.3em;color:var(–white);text-decoration:none}
.nav-links{display:flex;gap:2.5rem;list-style:none}
.nav-links a{font-size:.65rem;letter-spacing:.2em;text-transform:uppercase;color:var(–white);text-decoration:none;opacity:.5;transition:opacity .3s}
.nav-links a:hover{opacity:1}

.hero{min-height:100vh;display:flex;flex-direction:column;justify-content:flex-end;padding:8rem 3rem 6rem;position:relative;overflow:hidden}
.hero-bg{position:absolute;top:0;left:0;right:0;bottom:0;font-family:‘Bebas Neue’,sans-serif;font-size:30vw;color:transparent;-webkit-text-stroke:1px rgba(255,255,255,0.03);display:flex;align-items:center;justify-content:center;pointer-events:none;user-select:none}
.hero-eyebrow{font-size:.65rem;letter-spacing:.3em;text-transform:uppercase;color:var(–red);margin-bottom:1.5rem;opacity:0;animation:up 1s ease forwards .3s}
.hero-title{font-family:‘Bebas Neue’,sans-serif;font-size:clamp(4rem,11vw,10rem);line-height:.92;opacity:0;animation:up 1s ease forwards .5s}
.hero-title span{color:var(–red)}
.hero-sub{margin-top:2.5rem;font-size:.78rem;line-height:1.9;max-width:420px;color:#888;opacity:0;animation:up 1s ease forwards .8s}
.hero-cta{margin-top:2.5rem;opacity:0;animation:up 1s ease forwards 1s}
.btn{display:inline-block;padding:.9rem 2.2rem;border:1px solid var(–white);font-family:‘DM Mono’,monospace;font-size:.68rem;letter-spacing:.2em;text-transform:uppercase;color:var(–white);text-decoration:none;transition:all .3s;position:relative;overflow:hidden}
.btn::before{content:’’;position:absolute;top:0;left:-100%;width:100%;height:100%;background:var(–red);transition:left .3s ease;z-index:-1}
.btn:hover::before{left:0}
.btn:hover{border-color:var(–red)}

.ticker{border-top:1px solid var(–grey);border-bottom:1px solid var(–grey);padding:.9rem 0;overflow:hidden;white-space:nowrap}
.ticker-track{display:inline-flex;gap:4rem;animation:tick 25s linear infinite}
.ticker-item{font-size:.62rem;letter-spacing:.25em;text-transform:uppercase;color:#3a3a3a}
.ticker-item span{color:var(–red);margin-right:.8rem}

section{padding:7rem 3rem;max-width:1300px;margin:0 auto}
.section-label{font-size:.62rem;letter-spacing:.3em;text-transform:uppercase;color:var(–red);margin-bottom:.8rem}
.section-title{font-family:‘Bebas Neue’,sans-serif;font-size:clamp(2.2rem,4.5vw,4rem);letter-spacing:.04em;margin-bottom:4rem}

.services-grid{display:grid;grid-template-columns:repeat(3,1fr);border-top:1px solid var(–grey);border-left:1px solid var(–grey)}
.service{padding:2.5rem;border-right:1px solid var(–grey);border-bottom:1px solid var(–grey);position:relative;transition:background .3s}
.service:hover{background:rgba(255,255,255,0.02)}
.service::after{content:’’;position:absolute;top:0;left:0;width:0;height:2px;background:var(–red);transition:width .4s}
.service:hover::after{width:100%}
.service-num{font-size:.58rem;color:var(–red);letter-spacing:.3em;margin-bottom:1.5rem}
.service-name{font-family:‘Bebas Neue’,sans-serif;font-size:1.6rem;letter-spacing:.04em;margin-bottom:1rem}
.service-desc{font-size:.72rem;line-height:1.9;color:#666}
.service-price{margin-top:1.5rem;font-size:.62rem;letter-spacing:.15em;color:#444}

.clients-full{background:#0d0d0d;padding:7rem 0}
.clients-inner{max-width:1300px;margin:0 auto;padding:0 3rem}
.clients-grid{display:grid;grid-template-columns:1fr 1fr;gap:0;border-top:1px solid var(–grey)}
.client{padding:3rem;border-bottom:1px solid var(–grey);border-right:1px solid var(–grey)}
.client:nth-child(2n){border-right:none}
.client h3{font-family:‘Bebas Neue’,sans-serif;font-size:1.5rem;letter-spacing:.04em;margin-bottom:1rem}
.client p{font-size:.72rem;line-height:1.9;color:#555}

.process-steps{display:grid;grid-template-columns:repeat(4,1fr);border-top:1px solid var(–grey)}
.step{padding:3rem 2rem 3rem 0;border-right:1px solid var(–grey)}
.step:last-child{border-right:none}
.step:not(:first-child){padding-left:2rem}
.step-num{font-family:‘Bebas Neue’,sans-serif;font-size:4rem;color:rgba(255,255,255,0.04);line-height:1;margin-bottom:.8rem}
.step-title{font-family:‘Bebas Neue’,sans-serif;font-size:1.2rem;letter-spacing:.04em;margin-bottom:.8rem}
.step-desc{font-size:.7rem;line-height:1.9;color:#555}

.proof-full{background:var(–red);padding:7rem 3rem}
.proof-inner{max-width:1300px;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:6rem;align-items:center}
.proof-quote{font-family:‘Playfair Display’,serif;font-style:italic;font-size:clamp(1.4rem,2.5vw,2.2rem);line-height:1.5;color:var(–black)}
.proof-stats{display:flex;flex-direction:column;gap:2rem}
.proof-stat{border-bottom:1px solid rgba(0,0,0,0.15);padding-bottom:2rem}
.proof-stat:last-child{border-bottom:none;padding-bottom:0}
.proof-stat-num{font-family:‘Bebas Neue’,sans-serif;font-size:3rem;color:var(–black);line-height:1}
.proof-stat-label{font-size:.65rem;letter-spacing:.2em;text-transform:uppercase;color:rgba(0,0,0,0.5);margin-top:.4rem}

.contact-grid{display:grid;grid-template-columns:1fr 1fr;gap:6rem}
.contact-title{font-family:‘Bebas Neue’,sans-serif;font-size:clamp(2.5rem,5vw,5rem);line-height:.95;margin-bottom:1.5rem}
.contact-title em{font-family:‘Playfair Display’,serif;font-style:italic;color:var(–red)}
.contact-desc{font-size:.73rem;line-height:1.9;color:#555;margin-bottom:2.5rem}
.contact-meta{display:flex;flex-direction:column;gap:1.2rem}
.meta-label{font-size:.58rem;letter-spacing:.3em;text-transform:uppercase;color:var(–red)}
.meta-val{font-size:.78rem;color:var(–white)}
.form{display:flex;flex-direction:column}
.field{border-bottom:1px solid var(–grey);padding:1.3rem 0;display:flex;flex-direction:column;gap:.4rem}
.field label{font-size:.58rem;letter-spacing:.3em;text-transform:uppercase;color:#444}
.field input,.field select,.field textarea{background:none;border:none;outline:none;font-family:‘DM Mono’,monospace;font-size:.82rem;color:var(–white);font-weight:300;resize:none}
.field input::placeholder,.field textarea::placeholder{color:#2a2a2a}
.field select option{background:var(–black)}
.form-btn{margin-top:2.5rem}

footer{border-top:1px solid var(–grey);padding:2.5rem 3rem;display:flex;justify-content:space-between;align-items:center;max-width:100%}
.footer-logo{font-family:‘Bebas Neue’,sans-serif;font-size:1.1rem;letter-spacing:.3em}
.footer-copy,.footer-tag{font-size:.58rem;letter-spacing:.15em;color:#2a2a2a;text-transform:uppercase}
.footer-tag{font-style:italic;text-transform:none;letter-spacing:.05em}

.reveal{opacity:0;transform:translateY(30px);transition:opacity .7s ease,transform .7s ease}
.reveal.on{opacity:1;transform:none}

@keyframes up{from{opacity:0;transform:translateY(25px)}to{opacity:1;transform:none}}
@keyframes tick{from{transform:translateX(0)}to{transform:translateX(-50%)}}

@media(max-width:768px){
nav{padding:1.2rem 1.5rem}
.nav-links{display:none}
.hero{padding:6rem 1.5rem 4rem}
section{padding:5rem 1.5rem}
.services-grid{grid-template-columns:1fr}
.clients-grid{grid-template-columns:1fr}
.client{border-right:none}
.process-steps{grid-template-columns:1fr 1fr}
.proof-inner{grid-template-columns:1fr}
.contact-grid{grid-template-columns:1fr}
.proof-full{padding:5rem 1.5rem}
footer{padding:2rem 1.5rem;flex-direction:column;gap:1rem;text-align:center}
.clients-inner{padding:0 1.5rem}
}
</style>

</head>
<body>

<nav>
  <a href="#" class="nav-logo">FRAME</a>
  <ul class="nav-links">
    <li><a href="#services">Services</a></li>
    <li><a href="#clients">Clients</a></li>
    <li><a href="#process">Process</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<div class="hero">
  <div class="hero-bg">FRAME</div>
  <p class="hero-eyebrow">Intelligence & Research — Sydney</p>
  <h1 class="hero-title">We find<br><span>what others</span><br>can't see.</h1>
  <p class="hero-sub">FRAME delivers deep intelligence for law firms, investment funds, and corporates who need to know more than their competitors.</p>
  <div class="hero-cta"><a href="#contact" class="btn">Start an Engagement</a></div>
</div>

<div class="ticker">
  <div class="ticker-track">
    <span class="ticker-item"><span>—</span>Due Diligence</span>
    <span class="ticker-item"><span>—</span>Competitor Intelligence</span>
    <span class="ticker-item"><span>—</span>Person Research</span>
    <span class="ticker-item"><span>—</span>Market Mapping</span>
    <span class="ticker-item"><span>—</span>Investment Research</span>
    <span class="ticker-item"><span>—</span>Legal Intelligence</span>
    <span class="ticker-item"><span>—</span>Due Diligence</span>
    <span class="ticker-item"><span>—</span>Competitor Intelligence</span>
    <span class="ticker-item"><span>—</span>Person Research</span>
    <span class="ticker-item"><span>—</span>Market Mapping</span>
    <span class="ticker-item"><span>—</span>Investment Research</span>
    <span class="ticker-item"><span>—</span>Legal Intelligence</span>
  </div>
</div>

<section id="services">
  <p class="section-label reveal">What We Do</p>
  <h2 class="section-title reveal">Services</h2>
  <div class="services-grid">
    <div class="service reveal">
      <p class="service-num">01</p>
      <h3 class="service-name">Due Diligence</h3>
      <p class="service-desc">Comprehensive background research on individuals, companies, and assets before you commit. We find what isn't in the filing and what isn't on the website.</p>
      <p class="service-price">From AUD $5,000</p>
    </div>
    <div class="service reveal">
      <p class="service-num">02</p>
      <h3 class="service-name">Competitor Intelligence</h3>
      <p class="service-desc">Deep mapping of competitor strategy, personnel, positioning, and vulnerabilities. Know their next move before they make it.</p>
      <p class="service-price">From AUD $8,000</p>
    </div>
    <div class="service reveal">
      <p class="service-num">03</p>
      <h3 class="service-name">Person Research</h3>
      <p class="service-desc">Granular research on specific individuals — executives, acquisition targets, counterparties, witnesses. Professional history, network mapping, public record analysis.</p>
      <p class="service-price">From AUD $3,500</p>
    </div>
    <div class="service reveal">
      <p class="service-num">04</p>
      <h3 class="service-name">Market Mapping</h3>
      <p class="service-desc">Full landscape analysis of a market sector — key players, emerging entrants, funding activity, strategic movements. Built for entry strategy and investment thesis.</p>
      <p class="service-price">From AUD $10,000</p>
    </div>
    <div class="service reveal">
      <p class="service-num">05</p>
      <h3 class="service-name">Investment Research</h3>
      <p class="service-desc">Pre-investment intelligence for private equity, venture capital, and family offices. Beyond the pitch deck. Behind the numbers.</p>
      <p class="service-price">From AUD $7,500</p>
    </div>
    <div class="service reveal">
      <p class="service-num">06</p>
      <h3 class="service-name">Legal Intelligence</h3>
      <p class="service-desc">Research support for litigation, arbitration, and regulatory matters. Asset tracing, witness background, opposing party analysis.</p>
      <p class="service-price">From AUD $6,000</p>
    </div>
  </div>
</section>

<div class="clients-full" id="clients">
  <div class="clients-inner">
    <p class="section-label reveal">Who We Serve</p>
    <h2 class="section-title reveal">Clients</h2>
    <div class="clients-grid">
      <div class="client reveal">
        <h3>Law Firms</h3>
        <p>Litigation support, due diligence on counterparties, witness background research, asset tracing. We integrate with your matter team and deliver to your timeline.</p>
      </div>
      <div class="client reveal">
        <h3>Investment Funds</h3>
        <p>Pre-investment due diligence, portfolio monitoring, acquisition target research. Private equity, venture capital, hedge funds, and family offices.</p>
      </div>
      <div class="client reveal">
        <h3>Corporates</h3>
        <p>Competitor intelligence, market mapping, executive background checks, strategic partner due diligence. We work with strategy, M&A, and risk teams.</p>
      </div>
      <div class="client reveal">
        <h3>High Net Worth Individuals</h3>
        <p>Discreet research on business partners, investment opportunities, and personal matters. Confidential, thorough, delivered directly.</p>
      </div>
    </div>
  </div>
</div>

<section id="process">
  <p class="section-label reveal">How It Works</p>
  <h2 class="section-title reveal">Process</h2>
  <div class="process-steps">
    <div class="step reveal">
      <div class="step-num">01</div>
      <h3 class="step-title">Brief</h3>
      <p class="step-desc">Tell us what you need to know and why. We establish scope, timeline, and deliverable format in a single conversation.</p>
    </div>
    <div class="step reveal">
      <div class="step-num">02</div>
      <h3 class="step-title">Research</h3>
      <p class="step-desc">We go deep. Public records, corporate filings, media, professional networks, proprietary databases. Every source interrogated.</p>
    </div>
    <div class="step reveal">
      <div class="step-num">03</div>
      <h3 class="step-title">Analysis</h3>
      <p class="step-desc">Raw information becomes intelligence. Patterns identified, gaps flagged, implications drawn. We tell you what it means, not just what it is.</p>
    </div>
    <div class="step reveal">
      <div class="step-num">04</div>
      <h3 class="step-title">Deliver</h3>
      <p class="step-desc">A concise, actionable report. No padding. No filler. Everything you need to make the decision you're facing.</p>
    </div>
  </div>
</section>

<div class="proof-full">
  <div class="proof-inner">
    <p class="proof-quote">"They found information in four hours that our internal team had been looking for for two weeks. We now use them on every significant transaction."</p>
    <div class="proof-stats">
      <div class="proof-stat">
        <div class="proof-stat-num">48hr</div>
        <div class="proof-stat-label">Standard turnaround on person research</div>
      </div>
      <div class="proof-stat">
        <div class="proof-stat-num">100%</div>
        <div class="proof-stat-label">Confidential. No subcontractors. No data retention.</div>
      </div>
      <div class="proof-stat">
        <div class="proof-stat-num">$0</div>
        <div class="proof-stat-label">Upfront. Pay on delivery.</div>
      </div>
    </div>
  </div>
</div>

<section id="contact">
  <div class="contact-grid">
    <div>
      <h2 class="contact-title reveal">Start an<br><em>engagement.</em></h2>
      <p class="contact-desc reveal">Tell us what you need to know. We'll tell you if we can find it and what it will cost. No obligation until you're satisfied with the scope.</p>
      <div class="contact-meta reveal">
        <div>
          <p class="meta-label">Location</p>
          <p class="meta-val">Sydney, NSW — Australia</p>
        </div>
        <div>
          <p class="meta-label">Response Time</p>
          <p class="meta-val">Within 4 business hours</p>
        </div>
        <div>
          <p class="meta-label">Confidentiality</p>
          <p class="meta-val">NDA available on request</p>
        </div>
      </div>
    </div>
    <div class="form reveal">
      <div class="field">
        <label>Name</label>
        <input type="text" placeholder="Your name">
      </div>
      <div class="field">
        <label>Organisation</label>
        <input type="text" placeholder="Company or firm">
      </div>
      <div class="field">
        <label>Email</label>
        <input type="email" placeholder="you@firm.com">
      </div>
      <div class="field">
        <label>Service Required</label>
        <select>
          <option value="" disabled selected>Select a service</option>
          <option>Due Diligence</option>
          <option>Competitor Intelligence</option>
          <option>Person Research</option>
          <option>Market Mapping</option>
          <option>Investment Research</option>
          <option>Legal Intelligence</option>
          <option>Other</option>
        </select>
      </div>
      <div class="field">
        <label>Brief Description</label>
        <textarea rows="4" placeholder="What do you need to know?"></textarea>
      </div>
      <div class="form-btn">
        <a href="mailto:hello@frameintelligence.com.au" class="btn">Submit Brief</a>
      </div>
    </div>
  </div>
</section>

<footer>
  <span class="nav-logo">FRAME</span>
  <span class="footer-tag">We find what others can't see.</span>
  <span class="footer-copy">© 2026 Frame Intelligence Pty Ltd — Sydney</span>
</footer>

<script>
const reveals = document.querySelectorAll('.reveal');
const obs = new IntersectionObserver(entries => {
  entries.forEach((e,i) => {
    if(e.isIntersecting){
      setTimeout(()=>e.target.classList.add('on'), i*70);
      obs.unobserve(e.target);
    }
  });
},{threshold:0.1});
reveals.forEach(el=>obs.observe(el));
</script>

</body>
</html>
