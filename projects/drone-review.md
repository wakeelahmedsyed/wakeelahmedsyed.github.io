<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Drone Technology Systematic Review | Syed Wakeel Ahmed Portfolio</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@300;400;700&family=Source+Sans+3:ital,wght@0,300;0,400;0,600;0,700;1,400&display=swap" rel="stylesheet" />

  <style>
    /* ═══════════════════════════════════════════════════════════
       DESIGN TOKENS — Replicating your Portfolio Style
    ═══════════════════════════════════════════════════════════ */
    :root {
      --blue:          #155799;
      --green:         #159957;
      --green-mid:     #0d7a52;
      --amber:         #c8861a;
      --red:           #c0392b;
      --text:          #606c71;
      --text-dark:     #2c3e3f;
      --text-muted:    #9badb0;
      --bg:            #ffffff;
      --bg-subtle:     #f3f7f6;
      --border:        #d0ddd8;
      --accent-bg:     #e8f5ee;
      --shadow:        0 2px 16px rgba(21,87,153,0.07), 0 1px 4px rgba(0,0,0,0.04);
      --shadow-up:     0 6px 28px rgba(21,87,153,0.13), 0 2px 8px rgba(0,0,0,0.06);
      --r:             8px;
      --r-lg:          16px;
      --font-head:     'Merriweather', Georgia, serif;
      --font-body:     'Source Sans 3', 'Helvetica Neue', sans-serif;
      --w:             900px;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { font-size: 16px; scroll-behavior: smooth; }
    body { font-family: var(--font-body); color: var(--text); background: var(--bg); line-height: 1.78; -webkit-font-smoothing: antialiased; }
    a { color: var(--green); text-decoration: none; font-weight: 600; }
    
    /* HEADER */
    .site-header { background: linear-gradient(135deg, var(--blue) 0%, var(--green) 100%); padding: 4rem 2rem 3.5rem; text-align: center; position: relative; overflow: hidden; }
    .field-label { font-size: 0.72rem; font-weight: 700; letter-spacing: 0.16em; text-transform: uppercase; color: rgba(255,255,255,0.6); margin-bottom: 0.5rem; }
    .site-header h1 { font-family: var(--font-head); font-size: clamp(1.75rem, 4vw, 2.65rem); font-weight: 700; color: #fff; line-height: 1.22; margin: 0 auto 0.85rem; }
    .header-sub { font-size: 1.05rem; color: rgba(255,255,255,0.78); max-width: 640px; margin: 0 auto 2.2rem; font-weight: 400; }
    
    .wrap { max-width: var(--w); margin: 0 auto; padding: 0 1.5rem 5rem; }
    .section { padding: 3rem 0 0; }
    .sec-label { font-size: 0.71rem; font-weight: 700; letter-spacing: 0.15em; text-transform: uppercase; color: var(--green); margin-bottom: 0.55rem; }
    .sec-num { display: inline-block; font-size: 0.65rem; font-weight: 700; letter-spacing: 0.12em; background: var(--accent-bg); color: var(--green-mid); border: 1px solid #b8dfc8; border-radius: 999px; padding: 0.15rem 0.6rem; margin-right: 0.45rem; vertical-align: middle; }
    
    /* SKILLS PILLS */
    .pills { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 1rem; }
    .pill { background: var(--bg-subtle); border: 1px solid var(--border); color: var(--text-dark); font-size: 0.82rem; font-weight: 600; padding: 0.35rem 0.9rem; border-radius: 999px; }

    /* ACHIEVEMENT */
    .achievement-banner { background: linear-gradient(115deg, var(--blue) 0%, var(--green) 100%); border-radius: var(--r-lg); padding: 2.3rem 2.6rem; margin-top: 1.5rem; color: #fff; }
    .achievement-banner blockquote { font-family: var(--font-head); font-size: 1.1rem; font-style: italic; border: none; }

    /* STATS */
    .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(165px, 1fr)); gap: 1rem; margin-top: 1.5rem; }
    .stat-card { background: var(--bg-subtle); border: 1px solid var(--border); border-radius: var(--r-lg); padding: 1.4rem 1.2rem; text-align: center; }
    .stat-num { font-family: var(--font-head); font-size: 2.1rem; font-weight: 700; color: var(--blue); }
    .stat-unit { font-size: 0.75rem; font-weight: 700; text-transform: uppercase; color: var(--green); }

    /* TABLE */
    .table-wrap { overflow-x: auto; border-radius: var(--r); border: 1px solid var(--border); margin-top: 1rem; }
    table { width: 100%; border-collapse: collapse; font-size: 0.85rem; }
    thead { background: var(--blue); color: #fff; }
    th, td { padding: 0.75rem; border-bottom: 1px solid var(--border); text-align: left; }
    
    /* FINDINGS GRID */
    .findings-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.1rem; margin-top: 1.5rem; }
    .finding-card { background: var(--bg-subtle); border-left: 4px solid var(--green); padding: 1.2rem; border-radius: 4px; }
  </style>
</head>
<body>

<header class="site-header">
  <p class="field-label">Industry 4.0 <span style="opacity:0.5">/</span> Research &amp; Meta-Analysis</p>
  <h1>
    Systematic Review: Drone Integration in Industrial Inspection<br>
    <em>Economic &amp; Operational Viability Assessment</em>
  </h1>
  <p class="header-sub">
    A comprehensive meta-analysis of 1,900+ academic sources to evaluate the transition from human-based to UAV-based inspection in hazardous manufacturing environments.
  </p>
  <a href="/" style="color:rgba(255,255,255,0.7); font-size:0.8rem">← Back to Portfolio</a>
</header>

<main class="wrap">

  <section class="section">
    <p class="sec-label"><span class="sec-num">01</span> Project Scope</p>
    <div class="pills">
      <span class="pill">PRISMA Framework</span>
      <span class="pill">Systematic Literature Review (SLR)</span>
      <span class="pill">Economic Modeling</span>
      <span class="pill">HSE Risk Management</span>
      <span class="pill">Industry 4.0</span>
      <span class="pill">Quantitative Data Synthesis</span>
    </div>
  </section>

  <section class="section">
    <p class="sec-label"><span class="sec-num">02</span> Executive Summary</p>
    <div class="achievement-banner">
      <blockquote>
        Identified the primary conveniences making inspection drones a viable substitute for human methods in manufacturing. Developed an <strong>8-point Economic Assessment Framework</strong> to guide organizations through the transition, balancing CAPEX costs against long-term safety and operational gains.
      </blockquote>
    </div>
  </section>

  <section class="section">
    <p class="sec-label"><span class="sec-num">03</span> Methodology &amp; Rigor</p>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">1,900+</div>
        <div class="stat-unit">Articles Screened</div>
        <p style="font-size:0.8rem">Initial database search across Scopus, ScienceDirect, and IEEE Xplore.</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">6</div>
        <div class="stat-unit">Major Databases</div>
        <p style="font-size:0.8rem">Including Taylor &amp; Francis, SpringerLink, and MDPI.</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">27</div>
        <div class="stat-unit">Final Selected Papers</div>
        <p style="font-size:0.8rem">Narrowed via strict inclusion/exclusion criteria for high-quality evidence.</p>
      </div>
    </div>
  </section>

  <section class="section">
    <p class="sec-label"><span class="sec-num">04</span> Systematic Objective Mapping</p>
    <p>Synthesis of core research findings across industrial domains:</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Core Objective</th>
            <th>UAV Tech Progress</th>
            <th>Mfg. Status</th>
            <th>Risk/Obstacles</th>
            <th>Economic/HSE</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Agarwal et al. (2023)</td>
            <td style="text-align:center">✓</td>
            <td style="text-align:center"></td>
            <td style="text-align:center">✓</td>
            <td style="text-align:center"></td>
          </tr>
          <tr>
            <td>Al-Dosari et al. (2023)</td>
            <td style="text-align:center">✓</td>
            <td style="text-align:center"></td>
            <td style="text-align:center">✓</td>
            <td style="text-align:center"></td>
          </tr>
          <tr>
            <td>Rejeb et al. (2021)</td>
            <td style="text-align:center">✓</td>
            <td style="text-align:center"></td>
            <td style="text-align:center">✓</td>
            <td style="text-align:center"></td>
          </tr>
          <tr>
            <td>Nooralishahi et al. (2021)</td>
            <td style="text-align:center">✓</td>
            <td style="text-align:center">✓</td>
            <td style="text-align:center">✓</td>
            <td style="text-align:center"></td>
          </tr>
        </tbody>
      </table>
    </div>
  </section>

  <section class="section">
    <p class="sec-label"><span class="sec-num">05</span> Original Economic Framework</p>
    <p>Synthesized 8 critical decision points for manufacturing industries considering UAV adoption:</p>
    <div class="findings-grid">
      <div class="finding-card">
        <h3>1. Cost-Benefit Ratio</h3>
        <p>Balancing initial acquisition/maintenance against labor savings.</p>
      </div>
      <div class="finding-card">
        <h3>2. Operational Efficiency</h3>
        <p>Gains in responsive logistics and reduced inspection downtime.</p>
      </div>
      <div class="finding-card">
        <h3>3. Data Integrity</h3>
        <p>Comparing UAV sensory accuracy vs. manual human reporting.</p>
      </div>
      <div class="finding-card">
        <h3>4. Regulatory Compliance</h3>
        <p>Navigating FAA/EU legal ambiguity and liability insurance.</p>
      </div>
    </div>
  </section>

</main>

<footer style="text-align:center; padding: 2rem; background: #f3f7f6; font-size:0.8rem; color:#9badb0">
  Independent Research Project · 2024 · Systematic Review Methodology
</footer>

</body>
</html>
