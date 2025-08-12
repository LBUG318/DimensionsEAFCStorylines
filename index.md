<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>FauxPress — Local Mock News</title>
  <style>
    /* ======= QUICK TWEAKS ======= */
    :root{
      --bg:#ffffff;
      --ink:#111111;
      --muted:#5a5f6a;
      --accent:#1a73e8; /* change to taste */
      --border:#e6e8ec;
      --chip:#f4f6f9;
      --font-sans: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji", "Segoe UI Emoji";
      --font-serif: ui-serif, Georgia, Cambria, "Times New Roman", Times, serif;
      --maxw: 1200px;
    }

    html,body{margin:0;padding:0;background:var(--bg);color:var(--ink);font-family:var(--font-sans);}
    a{color:inherit;text-decoration:none}
    img{max-width:100%;height:auto;display:block}
    .container{max-width:var(--maxw);margin:0 auto;padding:24px}
    .topbar{border-bottom:1px solid var(--border);background:#fff;position:sticky;top:0;z-index:50}
    .topbar-inner{display:flex;align-items:center;gap:16px;justify-content:space-between;padding:12px 0}
    .brand{font-family:var(--font-serif);font-weight:800;letter-spacing:0.5px;font-size:28px}
    .brand .dot{color:var(--accent)}
    .nav{display:flex;gap:18px;font-size:14px;color:var(--muted)}
    .nav a{padding:8px 10px;border-radius:8px}
    .nav a.active,.nav a:hover{background:var(--chip);color:var(--ink)}

    .hero{display:grid;grid-template-columns:1.6fr 1fr;gap:24px;margin-top:24px}
    .hero-card{border:1px solid var(--border);border-radius:16px;overflow:hidden;background:#fff}
    .hero-media{aspect-ratio:16/9;background:#cfd7e3}
    .hero-body{padding:18px 20px}
    .kicker{font-size:12px;text-transform:uppercase;letter-spacing:.12em;color:var(--accent);font-weight:700}
    h1{font-family:var(--font-serif);font-size:38px;line-height:1.1;margin:6px 0 10px}
    .meta{display:flex;gap:12px;align-items:center;color:var(--muted);font-size:13px}
    .meta .dot{width:4px;height:4px;background:var(--muted);border-radius:50%}
    .excerpt{color:#2a2f38;font-size:16px;line-height:1.5;margin-top:8px}

    .grid{display:grid;grid-template-columns:2fr 1fr;gap:24px;margin-top:28px}

    .card{border:1px solid var(--border);border-radius:16px;overflow:hidden;background:#fff;display:flex;flex-direction:column}
    .card-media{aspect-ratio:16/10;background:#e7ebf3}
    .card-body{padding:16px 18px}
    .card h3{font-family:var(--font-serif);font-size:22px;line-height:1.2;margin:6px 0 8px}
    .card p{color:#2c313b;font-size:15px;margin:0}

    .list{display:grid;grid-template-columns:1fr 1fr;gap:16px}
    .list-item{display:grid;grid-template-columns:120px 1fr;gap:14px;border:1px solid var(--border);border-radius:14px;padding:10px;background:#fff}
    .thumb{aspect-ratio:16/10;background:#e7ebf3;border-radius:10px}
    .list h4{font-family:var(--font-serif);font-size:18px;margin:2px 0 6px}
    .list .snippet{color:#343a46;font-size:14px}

    .sidebar{display:flex;flex-direction:column;gap:18px}
    .widget{border:1px solid var(--border);border-radius:14px;background:#fff}
    .widget h5{font-size:14px;color:var(--muted);text-transform:uppercase;letter-spacing:.12em;margin:0;padding:12px 14px;border-bottom:1px solid var(--border)}
    .widget .content{padding:12px 14px}
    .pill{display:inline-block;background:var(--chip);padding:6px 10px;border-radius:999px;border:1px solid var(--border);font-size:12px;margin:4px 6px 0 0}

    .footer{margin-top:40px;border-top:1px solid var(--border)}
    .footer-inner{display:flex;gap:24px;justify-content:space-between;align-items:center;padding:16px 0;color:var(--muted);font-size:13px}

    /* utilities */
    .row{display:flex;gap:12px;align-items:center}
    .space{height:8px}
    .byline{font-weight:600}

    /* Make content easy to edit for quick screenshots */
    [contenteditable="true"]{outline: 1px dashed transparent}
    [contenteditable="true"]:focus{outline-color: var(--accent);}

    /* Responsive tweaks */
    @media (max-width: 960px){
      .hero{grid-template-columns:1fr}
      .grid{grid-template-columns:1fr}
      .list{grid-template-columns:1fr}
      .list-item{grid-template-columns:90px 1fr}
    }
  </style>
</head>
<body>
  <!-- ===== Top Bar ===== -->
  <header class="topbar">
    <div class="container topbar-inner">
      <div class="brand" contenteditable="true">FauxPress<span class="dot">.</span></div>
      <nav class="nav" aria-label="Primary">
        <a href="#" class="active" contenteditable="true">Home</a>
        <a href="#" contenteditable="true">World</a>
        <a href="#" contenteditable="true">Sports</a>
        <a href="#" contenteditable="true">Culture</a>
        <a href="#" contenteditable="true">Tech</a>
      </nav>
    </div>
  </header>

  <main class="container">
    <!-- ===== Hero ===== -->
    <section class="hero">
      <article class="hero-card">
        <div class="hero-media" title="Drop your image file into this box in your editor and adjust src below.">
          <!-- Replace src with a file you have locally, e.g., images/hero.jpg -->
          <img src="" alt="Hero image (optional)" style="width:100%;height:100%;object-fit:cover;display:none" onerror="this.style.display='none'">
        </div>
        <div class="hero-body">
          <div class="kicker" contenteditable="true">Breaking</div>
          <h1 contenteditable="true">Coach declares: “The door is wide open.” Squad tensions simmer as preseason peaks</h1>
          <div class="meta">
            <span class="byline" contenteditable="true">By Staff Reporter</span>
            <span class="dot"></span>
            <time contenteditable="true">Aug 12, 2025</time>
            <span class="dot"></span>
            <span contenteditable="true">6 min read</span>
          </div>
          <p class="excerpt" contenteditable="true">After a blunt press conference, supporters wonder: does calling other clubs “the big teams” reveal a quiet doubt—or a motivational feint?</p>
        </div>
      </article>

      <aside class="card">
        <div class="card-media"></div>
        <div class="card-body">
          <div class="kicker" contenteditable="true">Opinion</div>
          <h3 contenteditable="true">Is the “big door” speech genius psychology—or just hubris?</h3>
          <p contenteditable="true">A surgical read on language, leadership, and locker-room semiotics.</p>
        </div>
      </aside>
    </section>

    <!-- ===== Grid ===== -->
    <section class="grid">
      <div>
        <div class="list">
          <!-- Repeat list-item blocks as needed -->
          <article class="list-item">
            <div class="thumb"></div>
            <div>
              <div class="kicker" contenteditable="true">Analysis</div>
              <h4 contenteditable="true">Calling others “another big club”: rhetorical tactic or self-demotion?</h4>
              <p class="snippet" contenteditable="true">A close read of phrasing, identity, and status signaling inside modern football narratives.</p>
            </div>
          </article>

          <article class="list-item">
            <div class="thumb"></div>
            <div>
              <div class="kicker" contenteditable="true">Report</div>
              <h4 contenteditable="true">Transfer window: who walks through the big door—and who walks out?</h4>
              <p class="snippet" contenteditable="true">Thirty days to define the project: wages, roles, and the psychology of staying.</p>
            </div>
          </article>

          <article class="list-item">
            <div class="thumb"></div>
            <div>
              <div class="kicker" contenteditable="true">Feature</div>
              <h4 contenteditable="true">Blueprints of belief: building a “big club” from the inside out</h4>
              <p class="snippet" contenteditable="true">Culture, candor, and the slow accrual of gravitas.</p>
            </div>
          </article>

          <article class="list-item">
            <div class="thumb"></div>
            <div>
              <div class="kicker" contenteditable="true">Notebook</div>
              <h4 contenteditable="true">Four lines from the presser that reveal the real plan</h4>
              <p class="snippet" contenteditable="true">Between bravado and blueprint: what he actually promised.</p>
            </div>
          </article>
        </div>
      </div>

      <aside class="sidebar">
        <div class="widget">
          <h5>Trending</h5>
          <div class="content">
            <a class="pill" href="#" contenteditable="true">#TheBigDoor</a>
            <a class="pill" href="#" contenteditable="true">#ProjectGlory</a>
            <a class="pill" href="#" contenteditable="true">#EuropaBound</a>
            <a class="pill" href="#" contenteditable="true">#PreseasonPulse</a>
          </div>
        </div>
        <div class="widget">
          <h5>About</h5>
          <div class="content" contenteditable="true">
            This is a 100% local mockup for screenshots. No tracking, no scripts, no servers—just vibes.
          </div>
        </div>
      </aside>
    </section>

    <div class="space"></div>

    <!-- ===== Footer ===== -->
    <footer class="footer">
      <div class="footer-inner">
        <div contenteditable="true">© 2025 FauxPress — Parody / Satire only.</div>
        <div class="row">
          <a href="#" contenteditable="true">Terms</a>
          <span class="dot" style="width:3px;height:3px"></span>
          <a href="#" contenteditable="true">Privacy</a>
        </div>
      </div>
    </footer>
  </main>

  <!-- Optional: quick helper to toggle a compact header for tight screenshots -->
  <script>
    // No external dependencies; everything is local.
    // Tip: You can paste images by dragging them into your editor and setting the img src paths.
  </script>
</body>
</html>
