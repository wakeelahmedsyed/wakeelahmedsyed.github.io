<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Drone Technology Systematic Review | Process Engineering Portfolio</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@300;400;700&family=Source+Sans+3:ital,wght@0,300;0,400;0,600;0,700;1,400&display=swap" rel="stylesheet" />

  <style>
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
    a:hover { text-decoration: underline; }

    .site-header { background: linear-gradient(135deg, var(--blue) 0%, var(--green) 100%); padding: 4rem 2rem 3.5rem; text-align: center; position: relative; overflow: hidden; }
    .site-header::before { content: ''; position: absolute; inset: 0; background: radial-gradient(ellipse at 18% 55%, rgba(255,255,255,0.08) 0%, transparent 55%), radial-gradient(ellipse at 82% 20%, rgba(255,255,255,0.05) 0%, transparent 48%); pointer-events: none; }
    .field-label { font-size: 0.72rem; font-weight: 700; letter-spacing: 0.16em; text-transform: uppercase; color: rgba(255,255,255,0.6); margin-bottom: 0.5rem; }
    .field-label span { color: rgba(255,255,255,0.92); }
    .field-divider { display: inline-block; margin: 0 0.55em; opacity: 0.45; }
    .site-header h1 { font-family: var(--font-head); font-size: clamp(1.75rem, 4vw, 2.65rem); font-weight: 700; color: #fff; line-height: 1.22; letter-spacing: -0.015em; max-width: 820px; margin: 0 auto 0.85rem; }
    .site-header h1 em { font-style: normal; font-weight: 300; color: rgba(255,255,255,0.78); }
    .header-sub { font-size: 1.05rem; color: rgba(255,255,255,0.78); max-width: 640px; margin: 0 auto 2.2rem; font-weight: 400; }
    .back-link { display: inline-flex; align-items: center; gap: 0.35rem; font-size: 0.83rem; font-weight: 700; letter-spacing: 0.05em; color: rgba(255,255,255,0.65); text-decoration: none; transition: color 0.2s; }
    .back-link:hover { color: #fff; text-decoration: none; }
    .back-link::before { content: '←'; }

    .wrap { max-width: var(--w); margin: 0 auto; padding: 0 1.5rem 5rem; }
    .section { padding: 3rem 0 0; }
    .divider { height: 1px; background: linear-gradient(90deg, transparent, var(--border), transparent); margin-top: 3rem; }
    .sec-label { font-size: 0.71rem; font-weight: 700; letter-spacing: 0.15em; text-transform: uppercase; color: var(--green); margin-bottom: 0.55rem; }
    .sec-num { display: inline-block; font-size: 0.65rem; font-weight: 700; letter-spacing: 0.12em; background: var(--accent-bg); color: var(--green-mid); border: 1px solid #b8dfc8; border-radius: 999px; padding: 0.15rem 0.6rem; margin-right: 0.45rem; vertical-align: middle; }
    h2 { font-family: var(--font-head); font-size: 1.38rem; font-weight: 700; color: var(--text-dark); line-height: 1.3; margin-bottom: 1.1rem; }
    h3 { font-family: var(--font-body); font-size: 1rem; font-weight: 700; color: var(--text-dark); margin-bottom: 0.45rem; }
    p { margin-bottom: 1rem; font-size: 0.97rem; }
    p:last-child { margin-bottom: 0; }

    .skills-section { padding: 2rem 0; border-bottom: 1px solid var(--border); }
    .skills-label { font-size: 0.7rem; font-weight: 700; letter-spacing: 0.14em; text-transform: uppercase; color: var(--text-muted); margin-bottom: 0.75rem; }
    .pills { display: flex; flex-wrap: wrap; gap: 0.5rem; }
    .pill { display: inline-flex; align-items: center; gap: 0.35rem; background: var(--bg-subtle); border: 1px solid var(--border); color: var(--text-dark); font-size: 0.82rem; font-weight: 600; padding: 0.35rem 0.9rem; border-radius: 999px; cursor: default; }
    .pill:hover { background: var(--accent-bg); border-color: var(--green); color: var(--green-mid); }
    .pill-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--green); flex-shrink: 0; }

    .achievement-banner { background: linear-gradient(115deg, var(--blue) 0%, var(--green) 100%); border-radius: var(--r-lg); padding: 2.3rem 2.6rem; margin-top: 1.5rem; position: relative; overflow: hidden; }
    .achievement-banner::after { content: '"'; position: absolute; top: -0.8rem; right: 1.8rem; font-family: var(--font-head); font-size: 10rem; color: rgba(255,255,255,0.06); line-height: 1; pointer-events: none; }
    .ach-label { font-size: 0.7rem; font-weight: 700; letter-spacing: 0.16em; text-transform: uppercase; color: rgba(255,255,255,0.58); margin-bottom: 0.65rem; }
    .achievement-banner blockquote { font-family: var(--font-head); font-size: clamp(0.98rem, 2.4vw, 1.18rem); font-weight: 300; font-style: italic; color: #fff; line-height: 1.65; border: none; padding: 0; }
    .achievement-banner blockquote strong { font-weight: 700; font-style: normal; }

    .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(165px, 1fr)); gap: 1rem; margin-top: 1.5rem; }
    .stat-card { background: var(--bg-subtle); border: 1px solid var(--border); border-radius: var(--r-lg); padding: 1.4rem 1.2rem 1.15rem; text-align: center; transition: box-shadow 0.25s, transform 0.2s; }
    .stat-card:hover { box-shadow: var(--shadow-up); transform: translateY(-2px); }
    .stat-num { font-family: var(--font-head); font-size: 2.1rem; font-weight: 700; color: var(--blue); line-height: 1; letter-spacing: -0.02em; margin-bottom: 0.28rem; }
    .stat-num sup { font-size: 1rem; color: var(--green); }
    .stat-unit { font-size: 0.75rem; font-weight: 700; letter-spacing: 0.07em; text-transform: uppercase; color: var(--green); margin-bottom: 0.5rem; }
    .stat-card p { font-size: 0.82rem; color: var(--text); line-height: 1.45; margin: 0; }

    .note-box { background: var(--bg-subtle); border: 1px solid var(--border); border-radius: var(--r); padding: 1rem 1.35rem; font-size: 0.88rem; color: var(--text); margin-top: 1.1rem; line-height: 1.65; }
    .note-box.green { border-left: 3px solid var(--green); }
    .note-box.blue  { border-left: 3px solid var(--blue); }
    .note-box.amber { border-left: 3px solid var(--amber); }
    .note-box strong { color: var(--text-dark); }

    .method-steps { display: grid; gap: 0; margin-top: 1.5rem; border: 1px solid var(--border); border-radius: var(--r-lg); overflow: hidden; }
    .method-step { display: grid; grid-template-columns: 62px 1fr; border-bottom: 1px solid var(--border); }
    .method-step:last-child { border-bottom: none; }
    .step-num { background: var(--bg-subtle); border-right: 1px solid var(--border); display: flex; align-items: center; justify-content: center; font-family: var(--font-head); font-size: 1.1rem; font-weight: 700; color: var(--green); padding: 1.2rem 0.4rem; }
    .step-body { padding: 1.15rem 1.4rem; }
    .step-body h3 { font-size: 0.93rem; color: var(--text-dark); margin-bottom: 0.3rem; }
    .step-body p  { font-size: 0.88rem; margin: 0 0 0.6rem; color: var(--text); }
    .step-body p:last-child { margin-bottom: 0; }
    .step-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 0.55rem; }
    .step-tag { font-size: 0.72rem; font-weight: 700; letter-spacing: 0.04em; padding: 0.18rem 0.6rem; border-radius: 4px; background: var(--accent-bg); color: var(--green-mid); border: 1px solid #b8dfc8; }
    .step-tag.blue { background: rgba(21,87,153,0.07); color: var(--blue); border-color: rgba(21,87,153,0.2); }
    .step-tag.amber { background: rgba(200,134,26,0.08); color: #8a5c0e; border-color: rgba(200,134,26,0.25); }

    .table-caption { font-size: 0.82rem; font-weight: 700; color: var(--blue); text-transform: uppercase; letter-spacing: 0.05em; margin: 1.6rem 0 0; }
    .table-wrap { overflow-x: auto; border-radius: var(--r); border: 1px solid var(--border); margin-top: 0.75rem; }
    .table-wrap table { width: 100%; border-collapse: collapse; font-size: 0.85rem; }
    .table-wrap thead { background: linear-gradient(90deg, var(--blue), var(--green)); }
    .table-wrap thead th { color: #fff; font-weight: 700; font-size: 0.77rem; letter-spacing: 0.05em; text-transform: uppercase; padding: 0.72rem 1rem; text-align: left; white-space: nowrap; }
    .table-wrap tbody tr:nth-child(even) { background: var(--bg-subtle); }
    .table-wrap tbody td { padding: 0.62rem 1rem; color: var(--text); border-bottom: 1px solid var(--border); vertical-align: middle; }
    .table-wrap tbody tr:last-child td { border-bottom: none; }
    .table-wrap tbody td:first-child { font-weight: 600; color: var(--text-dark); }

    .results-trio { display: grid; grid-template-columns: repeat(3, 1fr); border: 1px solid var(--border); border-radius: var(--r-lg); overflow: hidden; margin-top: 1.5rem; }
    .result-cell { padding: 2rem 1.4rem; text-align: center; border-right: 1px solid var(--border); background: var(--bg); position: relative; }
    .result-cell:last-child { border-right: none; }
    .result-cell::before { content: ''; display: block; height: 3px; background: linear-gradient(90deg, var(--blue), var(--green)); position: absolute; top: 0; left: 0; right: 0; }
    .result-big { font-family: var(--font-head); font-size: 2.5rem; font-weight: 700; color: var(--blue); line-height: 1; letter-spacing: -0.03em; }
    .result-unit { font-size: 0.77rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; color: var(--green); margin: 0.3rem 0 0.6rem; }
    .result-desc { font-size: 0.82rem; color: var(--text); line-height: 1.45; }

    .findings-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(258px, 1fr)); gap: 1.1rem; margin-top: 1.5rem; }
    .finding-card { background: var(--bg-subtle); border: 1px solid var(--border); border-left: 3px solid var(--green); border-radius: var(--r); padding: 1.2rem 1.3rem; transition: box-shadow 0.2s; }
    .finding-card.challenge { border-left-color: var(--amber); }
    .finding-card.learning  { border-left-color: var(--blue); }
    .finding-card:hover { box-shadow: var(--shadow); }
    .finding-card h3 { font-size: 0.85rem; font-weight: 700; color: var(--green-mid); text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 0.4rem; }
    .finding-card.challenge h3 { color: #8a5c0e; }
    .finding-card.learning  h3 { color: var(--blue); }
    .finding-card p { font-size: 0.86rem; margin: 0; line-height: 1.55; }
    .find-pill { display: inline-block; font-size: 0.62rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; border-radius: 999px; padding: 0.12rem 0.55rem; margin-bottom: 0.55rem; }
    .find-pill.find      { background: var(--accent-bg);     color: var(--green-mid); border: 1px solid #b8dfc8; }
    .find-pill.challenge { background: rgba(200,134,26,0.1); color: #8a5c0e;          border: 1px solid rgba(200,134,26,0.25); }
    .find-pill.learn     { background: rgba(21,87,153,0.06); color: var(--blue);      border: 1px solid rgba(21,87,153,0.15); }

    .context-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 1rem; margin-top: 1.5rem; }
    .context-card { background: var(--bg); border: 1px solid var(--border); border-radius: var(--r-lg); padding: 1.3rem 1.4rem; display: flex; flex-direction: column; gap: 0.5rem; transition: box-shadow 0.2s, transform 0.18s; }
    .context-card:hover { box-shadow: var(--shadow-up); transform: translateY(-2px); }
    .ctx-icon { font-size: 1.5rem; line-height: 1; }
    .context-card h3 { font-size: 0.93rem; margin: 0; }
    .context-card p  { font-size: 0.83rem; margin: 0; color: var(--text); line-height: 1.5; }
    .context-card .outcome-pill { display: inline-block; margin-top: 0.2rem; font-size: 0.78rem; font-weight: 700; color: var(--green-mid); background: var(--accent-bg); border: 1px solid #b8dfc8; border-radius: 999px; padding: 0.2rem 0.75rem; }

    .placeholder { border: 2px dashed var(--border); border-radius: var(--r-lg); background: var(--bg-subtle); padding: 2.5rem 2rem; text-align: center; margin-top: 1.5rem; }
    .ph-icon { font-size: 2rem; margin-bottom: 0.5rem; opacity: 0.45; }
    .ph-tag { font-size: 0.7rem; font-weight: 700; letter-spacing: 0.13em; text-transform: uppercase; color: var(--green); margin-bottom: 0.3rem; }
    .ph-desc { font-size: 0.82rem; font-style: italic; color: var(--text-muted); max-width: 420px; margin: 0 auto; line-height: 1.55; }

    .site-footer { background: var(--bg-subtle); border-top: 1px solid var(--border); text-align: center; padding: 2rem 1.5rem; margin-top: 4rem; }
    .site-footer p { font-size: 0.81rem; color: var(--text-muted); margin: 0; }

    @keyframes fadeUp { from { opacity: 0; transform: translateY(16px); } to { opacity: 1; transform: translateY(0); } }
    .site-header > * { animation: fadeUp 0.6s ease both; }
    .site-header > *:nth-child(1) { animation-delay: 0.05s; }
    .site-header > *:nth-child(2) { animation-delay: 0.15s; }
    .site-header > *:nth-child(3) { animation-delay: 0.25s; }
    .site-header > *:nth-child(4) { animation-delay: 0.35s; }

    @media (max-width: 600px) {
      .site-header { padding: 2.6rem 1.2rem 2.2rem; }
      .wrap { padding: 0 1rem 4rem; }
      h2 { font-size: 1.2rem; }
      .results-trio { grid-template-columns: 1fr; }
      .result-cell { border-right: none; border-bottom: 1px solid var(--border); }
      .result-cell:last-child { border-bottom: none; }
      .achievement-banner { padding: 1.8rem 1.4rem; }
    }
  </style>
</head>
<body>


<!-- HEADER -->
<header class="site-header">
  <p class="field-label">
    Industry 4.0
    <span class="field-divider">/</span>
    <span>Research &amp; Technology Assessment</span>
  </p>

  <h1>
    Drone Technology for Industrial Inspection<br>
    <em>Systematic Literature Review &amp; Economic Viability Framework</em>
  </h1>

  <p class="header-sub">
    An independent systematic review of drone technology for non-destructive inspection in industrial and manufacturing environments, synthesizing 1,900+ screened studies into an 8-point decision framework for operational adoption.
  </p>

  <a href="/" class="back-link">&nbsp;Back to Portfolio</a>
</header>


<main class="wrap">

  <!-- SKILLS -->
  <div class="skills-section">
    <p class="skills-label"><span class="sec-num">03</span> Skills Used in This Project</p>
    <div class="pills">
      <span class="pill"><span class="pill-dot"></span>Systematic Literature Review</span>
      <span class="pill"><span class="pill-dot"></span>PRISMA Screening</span>
      <span class="pill"><span class="pill-dot"></span>Research Synthesis</span>
      <span class="pill"><span class="pill-dot"></span>Industry 4.0 Assessment</span>
      <span class="pill"><span class="pill-dot"></span>Technology Readiness Analysis</span>
      <span class="pill"><span class="pill-dot"></span>Economic Framework Design</span>
      <span class="pill"><span class="pill-dot"></span>HSE Evaluation</span>
      <span class="pill"><span class="pill-dot"></span>Operational Risk Analysis</span>
    </div>
  </div>


  <!-- ACHIEVEMENT -->
  <section class="section" aria-labelledby="ach-h">
    <p class="sec-label"><span class="sec-num">04</span> Achievement</p>
    <h2 id="ach-h">From Scattered Literature to an Actionable Industrial Decision Framework</h2>
    <div class="achievement-banner">
      <p class="ach-label">Core Achievement</p>
      <blockquote>
        Conducted a structured systematic review of drone technology for industrial inspection, narrowing an initial pool of <strong>1,900+ studies</strong> to a focused evidence base and synthesizing the findings into an <strong>8-point economic and operational framework</strong> for manufacturing organizations evaluating the shift from human-based inspection to UAV-supported inspection.
      </blockquote>
    </div>
  </section>

  <div class="divider"></div>


  <!-- PROJECT OVERVIEW -->
  <section class="section" aria-labelledby="infog-h">
    <p class="sec-label"><span class="sec-num">05</span> Project Overview</p>
    <h2 id="infog-h">The Full Picture at a Glance</h2>

    <div class="placeholder">
      <div class="ph-icon">📚</div>
      <p class="ph-tag">Suggested Visual — PRISMA Flow Diagram</p>
      <p class="ph-desc">
        Replace this placeholder with your PRISMA-style literature screening visual showing the progression from initial database search results to final selected papers used in the synthesis.
      </p>
    </div>
  </section>

  <div class="divider"></div>


  <!-- STATS -->
  <section class="section" aria-labelledby="stats-h">
    <p class="sec-label"><span class="sec-num">06</span> Project at a Glance</p>
    <h2 id="stats-h">Four Numbers That Define the Work</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">1,900<sup>+</sup></div>
        <div class="stat-unit">Articles Screened</div>
        <p>Initial search universe compiled from major academic databases using drone, inspection, and manufacturing-related keywords</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">27</div>
        <div class="stat-unit">Final Papers Synthesized</div>
        <p>Peer-reviewed studies selected after screening, filtering, duplication removal, and relevance assessment</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">8</div>
        <div class="stat-unit">Decision Factors</div>
        <p>Original economic and operational framework developed for evaluating drone adoption in manufacturing inspection</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">6</div>
        <div class="stat-unit">Database Sources</div>
        <p>Literature gathered from MDPI, ScienceDirect, IEEE Xplore, Scopus, SpringerLink, and Taylor &amp; Francis</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- PROBLEM -->
  <section class="section" aria-labelledby="problem-h">
    <p class="sec-label"><span class="sec-num">07</span> Problem Statement</p>
    <h2 id="problem-h">Manufacturing Needs Better Inspection Tools — But Adoption Cannot Run Ahead of Evidence</h2>

    <p>
      Across industrial environments, inspections of large, elevated, hazardous, or hard-to-access assets remain expensive, labor-intensive, and operationally disruptive. Manufacturing facilities rely on inspections to protect uptime, worker safety, and equipment integrity — yet many conventional methods still depend heavily on human access in risky or inefficient conditions.
    </p>
    <p>
      Drone technology presents an obvious promise: faster inspections, reduced personnel exposure, broader area coverage, and richer visual or thermal data. However, the industrial case for drones cannot rest on promise alone. The question is not simply whether drones are technically possible — it is whether they are economically justified, operationally scalable, and sufficiently reliable to replace or support human inspection in manufacturing contexts.
    </p>
    <p>
      The literature on drones is broad but fragmented. Valuable findings exist across power infrastructure, mining, construction, photovoltaics, wind turbines, and radiological monitoring — but these findings are rarely synthesized specifically for manufacturing decision-makers. This project addressed that gap by systematically reviewing the literature and converting it into an applied framework relevant to industrial operations.
    </p>

    <div class="note-box green">
      <strong>Core Research Question:</strong> What conveniences do inspection drones offer that make them a viable substitute to human inspection methods in manufacturing industries?
    </div>

    <div class="note-box blue">
      <strong>Why This Matters:</strong> For manufacturing organizations, inspection is not just a maintenance issue — it is a cost, safety, uptime, and strategic competitiveness issue. A technology assessment must therefore connect engineering feasibility to business logic.
    </div>
  </section>

  <div class="divider"></div>


  <!-- METHODOLOGY -->
  <section class="section" aria-labelledby="method-h">
    <p class="sec-label"><span class="sec-num">08</span> Methodology &amp; Execution</p>
    <h2 id="method-h">A Structured Literature Review Built for Industrial Decision-Making</h2>

    <p>
      The project followed a systematic review approach designed to convert a large, cross-disciplinary body of literature into an interpretable industrial assessment. The method emphasized relevance, traceability, and synthesis over simple summary.
    </p>

    <div class="method-steps">

      <div class="method-step">
        <div class="step-num">01</div>
        <div class="step-body">
          <h3>Research Framing — Defining the Industrial Use Case</h3>
          <p>The review was scoped around drone technology for inspection, with a specific interest in industrial and manufacturing environments. Instead of treating drones as a generic emerging technology, the framing focused on their practical application in inspection workflows where cost, safety, accessibility, and operational continuity matter. This narrowed the review from broad UAV literature to an applied industrial problem.</p>
          <div class="step-tags">
            <span class="step-tag">Problem Definition</span>
            <span class="step-tag">Industrial Scope</span>
            <span class="step-tag blue">Manufacturing Focus</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">02</div>
        <div class="step-body">
          <h3>Database Search — Building the Initial Evidence Pool</h3>
          <p>Search strings were developed around drone technology, industrial inspection, manufacturing, and non-destructive inspection use cases. Literature was collected from major academic databases including MDPI, ScienceDirect, Elsevier, Scopus, SpringerLink, and Taylor &amp; Francis. This first pass produced an initial search universe of over 1,900 studies, ensuring the review was broad enough to capture multiple industrial sectors while remaining anchored in peer-reviewed evidence.</p>
          <div class="step-tags">
            <span class="step-tag">Keyword Search</span>
            <span class="step-tag">Scopus</span>
            <span class="step-tag">ScienceDirect</span>
            <span class="step-tag blue">IEEE Xplore</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">03</div>
        <div class="step-body">
          <h3>Screening &amp; Selection — From Volume to Relevance</h3>
          <p>Titles, abstracts, publication dates, language, and duplication were used to progressively reduce the evidence base. Studies were retained when they explicitly contributed to one or more of the following: drone technology progress, industrial inspection use cases, adoption barriers, or economic and health-and-safety impacts. This stage converted a large, noisy body of research into a focused set of high-relevance papers suitable for thematic synthesis.</p>
          <div class="step-tags">
            <span class="step-tag">PRISMA Logic</span>
            <span class="step-tag">Duplicate Removal</span>
            <span class="step-tag blue">Relevance Filtering</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">04</div>
        <div class="step-body">
          <h3>Thematic Synthesis — Mapping Findings to Industrial Objectives</h3>
          <p>The final literature set was analysed against four practical objectives: progress in drone technology, manufacturing adoption status, barriers to implementation, and economic or occupational health impacts. This objective-based mapping allowed the literature to be read not as isolated case studies, but as a connected industrial technology landscape. Particular emphasis was given to energy infrastructure, wind turbines, photovoltaics, power lines, and hazardous-site inspections because these offered the strongest evidence for transfer into manufacturing inspection logic.</p>
          <div class="step-tags">
            <span class="step-tag">Objective Mapping</span>
            <span class="step-tag">Cross-Sector Synthesis</span>
            <span class="step-tag blue">Industrial Interpretation</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">05</div>
        <div class="step-body">
          <h3>Framework Development — Translating Research into Action</h3>
          <p>The final step was not merely summarization, but translation. Based on the synthesized literature, an 8-point economic and operational assessment framework was developed for organizations considering drone adoption for inspection. This framework linked the research findings to actual decision variables: cost-benefit ratio, inspection efficiency, data quality, regulation, scalability, environmental impact, public perception, and risk. This turned the review into an applied industrial decision tool rather than a passive academic summary.</p>
          <div class="step-tags">
            <span class="step-tag">Framework Design</span>
            <span class="step-tag">Decision Support</span>
            <span class="step-tag blue">Applied Research Output</span>
          </div>
        </div>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- TABLE -->
  <section class="section" aria-labelledby="results-h">
    <p class="sec-label"><span class="sec-num">09</span> Research Synthesis</p>
    <h2 id="results-h">Objective-Based Mapping of the Literature</h2>

    <p>
      Rather than summarizing papers one by one, the review mapped them against practical industrial questions. This allowed patterns to emerge across different sectors and use cases.
    </p>

    <p class="table-caption">Literature Mapping — Research Objectives vs. Evidence Categories</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Research Objective</th>
            <th>What Was Assessed</th>
            <th>Observed Pattern</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Drone Technology Progress</td>
            <td>Advances in UAV design, sensors, payloads, and maneuverability</td>
            <td>Strong evidence of rapid capability growth, especially in inspection and monitoring use cases</td>
          </tr>
          <tr>
            <td>Manufacturing Adoption Status</td>
            <td>Current level of drone use in industrial and manufacturing settings</td>
            <td>Adoption growing, but still fragmented and stronger in adjacent sectors than in core manufacturing</td>
          </tr>
          <tr>
            <td>Challenges &amp; Barriers</td>
            <td>Battery limits, regulation, vibration, access distance, environmental interference</td>
            <td>Technical capability is often ahead of implementation readiness</td>
          </tr>
          <tr>
            <td>Economic &amp; HSE Impact</td>
            <td>Cost savings, inspection speed, reduced worker exposure, operational continuity</td>
            <td>Most convincing case for adoption comes from safety and downtime reduction</td>
          </tr>
        </tbody>
      </table>
    </div>
  </section>

  <div class="divider"></div>


  <!-- RESULTS TRIO -->
  <section class="section" aria-labelledby="trio-h">
    <p class="sec-label"><span class="sec-num">10</span> Headline Results</p>
    <h2 id="trio-h">Three Conclusions That Matter Most</h2>
    <div class="results-trio">
      <div class="result-cell">
        <div class="result-big">Faster</div>
        <div class="result-unit">Inspection Cycles</div>
        <p class="result-desc">Across multiple sectors, drone-supported inspection consistently reduced access time, setup burden, and human exposure in difficult environments</p>
      </div>
      <div class="result-cell">
        <div class="result-big">Safer</div>
        <div class="result-unit">Work Conditions</div>
        <p class="result-desc">The strongest recurring value proposition was the reduction of human entry into hazardous, elevated, confined, or radiological zones</p>
      </div>
      <div class="result-cell">
        <div class="result-big">Structured</div>
        <div class="result-unit">Adoption Logic</div>
        <p class="result-desc">The final 8-point framework transformed scattered research findings into a usable decision model for industrial technology adoption</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- KEY FINDINGS -->
  <section class="section" aria-labelledby="findings-h">
    <p class="sec-label"><span class="sec-num">11</span> Key Findings &amp; Learning Outcomes</p>
    <h2 id="findings-h">What the Review Actually Uncovered</h2>
    <div class="findings-grid">

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>Inspection Drones Are Strongest Where Human Access Is Weakest</h3>
        <p>The most compelling use cases consistently appeared in environments that are elevated, hazardous, remote, or difficult to access — such as wind turbine blades, power lines, photovoltaic farms, mining sites, and radiological zones. The value of drones rises sharply when human inspection carries high access cost or safety burden.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>Operational Value Is Broader Than Cost Savings Alone</h3>
        <p>The literature did not support a narrow "drones save money" narrative. The stronger case was operational: reduced downtime, improved responsiveness, richer inspection data, better coverage, and lower worker exposure. These factors often create greater long-term value than direct inspection labor reduction alone.</p>
      </div>

      <div class="finding-card challenge">
        <span class="find-pill challenge">Challenge</span>
        <h3>Battery Endurance Remains a Structural Limitation</h3>
        <p>Rotary-wing drones offer the maneuverability required for inspection in industrial settings, but their endurance remains limited. This creates a recurring constraint for long missions, large sites, or tasks requiring prolonged hovering and heavy sensor payloads. In practice, this means drone utility is high, but not universally unconstrained.</p>
      </div>

      <div class="finding-card challenge">
        <span class="find-pill challenge">Challenge</span>
        <h3>Regulation and Implementation Lag Behind Technical Capability</h3>
        <p>Many studies showed that the technical capability to perform the inspection already exists, but regulatory ambiguity, legal liability, privacy concerns, and organizational hesitation slow deployment. In other words, adoption barriers are often managerial and policy-based, not purely engineering-based.</p>
      </div>

      <div class="finding-card learning">
        <span class="find-pill learn">Learning</span>
        <h3>Cross-Sector Evidence Can Be Meaningfully Transferred to Manufacturing</h3>
        <p>Even though direct manufacturing literature was thinner than adjacent-sector evidence, strong analogues exist. Lessons from PV inspections, power lines, wind turbines, mining, and hazardous-site monitoring can be responsibly transferred into manufacturing inspection logic when interpreted through operational similarity rather than industry labels alone.</p>
      </div>

      <div class="finding-card learning">
        <span class="find-pill learn">Learning</span>
        <h3>Research Becomes Valuable When It Ends in a Decision Tool</h3>
        <p>The most important outcome of this project was not the summary itself, but the framework derived from it. Turning literature into an adoption model — something a plant manager, operations head, or HSE leader can actually use — is what made the research practically meaningful.</p>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- 8-POINT FRAMEWORK -->
  <section class="section" aria-labelledby="framework-h">
    <p class="sec-label"><span class="sec-num">12</span> Original Economic Framework</p>
    <h2 id="framework-h">8-Point Decision Framework for Drone Adoption in Manufacturing</h2>

    <p>
      Synthesized from the full body of reviewed literature, this framework provides a structured assessment model for any manufacturing organization evaluating whether drone-based inspection is viable, justified, and scalable for their specific operational context.
    </p>

    <div class="method-steps">

      <div class="method-step">
        <div class="step-num">01</div>
        <div class="step-body">
          <h3>Cost-Benefit Analysis</h3>
          <p>Weigh acquisition, maintenance, and upgrade costs of drone systems against the labor, equipment, and insurance costs of conventional inspection. Factor in the growth of skilled UAV operators and service providers as a cost-reduction trend.</p>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">02</div>
        <div class="step-body">
          <h3>Operational Efficiency Gains</h3>
          <p>Assess whether drone-based inspection can reduce inspection cycle time, increase inspection frequency, or expand inspection coverage without proportional cost increases. Quantify the value of reduced downtime.</p>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">03</div>
        <div class="step-body">
          <h3>Data Quality and Accuracy</h3>
          <p>Compare the quality, consistency, and analytical potential of drone-collected data against human-collected data. Assess whether drone data enables better defect detection, predictive maintenance, or automated analysis pipelines.</p>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">04</div>
        <div class="step-body">
          <h3>Regulatory Compliance and Legal Considerations</h3>
          <p>Map the current regulatory environment for commercial drone operations in the relevant jurisdiction. Identify licensing, airspace, and liability requirements. Account for the cost of compliance as part of total adoption cost.</p>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">05</div>
        <div class="step-body">
          <h3>Technological Scalability</h3>
          <p>Evaluate whether the selected drone technology can scale across multiple inspection tasks, production lines, or facility types. Assess future-proofing against anticipated advances in sensors, AI-based defect detection, and autonomous flight.</p>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">06</div>
        <div class="step-body">
          <h3>Environmental Impact</h3>
          <p>Quantify the environmental benefit of replacing 
