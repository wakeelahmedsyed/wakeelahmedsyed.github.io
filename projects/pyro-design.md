
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pyro-Processing Heat Balance &amp; Cooler Fan Audit | Process Engineering Portfolio</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@300;400;700&family=Source+Sans+3:ital,wght@0,300;0,400;0,600;0,700;1,400&display=swap" rel="stylesheet" />

  <style>
    /* ═══════════════════════════════════════════════════════════
       DESIGN TOKENS — Cayman-synced palette
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

    /* ═══════════════════════════════════════════════════════════
       RESET & BASE
    ═══════════════════════════════════════════════════════════ */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { font-size: 16px; scroll-behavior: smooth; }
    body {
      font-family: var(--font-body);
      color: var(--text);
      background: var(--bg);
      line-height: 1.78;
      -webkit-font-smoothing: antialiased;
    }
    a { color: var(--green); text-decoration: none; font-weight: 600; }
    a:hover { text-decoration: underline; }

    /* ═══════════════════════════════════════════════════════════
       ① ②  HEADER  —  Field · Sub-field  +  Main Head
    ═══════════════════════════════════════════════════════════ */
    .site-header {
      background: linear-gradient(135deg, var(--blue) 0%, var(--green) 100%);
      padding: 4rem 2rem 3.5rem;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .site-header::before {
      content: '';
      position: absolute; inset: 0;
      background:
        radial-gradient(ellipse at 18% 55%, rgba(255,255,255,0.08) 0%, transparent 55%),
        radial-gradient(ellipse at 82% 20%, rgba(255,255,255,0.05) 0%, transparent 48%);
      pointer-events: none;
    }

    /* ① Field – Sub-field */
    .field-label {
      font-size: 0.72rem;
      font-weight: 700;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: rgba(255,255,255,0.6);
      margin-bottom: 0.5rem;
    }
    .field-label span { color: rgba(255,255,255,0.92); }
    .field-divider { display: inline-block; margin: 0 0.55em; opacity: 0.45; }

    /* ② Main Head */
    .site-header h1 {
      font-family: var(--font-head);
      font-size: clamp(1.75rem, 4vw, 2.65rem);
      font-weight: 700;
      color: #fff;
      line-height: 1.22;
      letter-spacing: -0.015em;
      max-width: 820px;
      margin: 0 auto 0.85rem;
    }
    .site-header h1 em {
      font-style: normal;
      font-weight: 300;
      color: rgba(255,255,255,0.78);
    }
    .header-sub {
      font-size: 1.05rem;
      color: rgba(255,255,255,0.78);
      max-width: 640px;
      margin: 0 auto 2.2rem;
      font-weight: 400;
    }
    .back-link {
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      font-size: 0.83rem;
      font-weight: 700;
      letter-spacing: 0.05em;
      color: rgba(255,255,255,0.65);
      text-decoration: none;
      transition: color 0.2s;
    }
    .back-link:hover { color: #fff; text-decoration: none; }
    .back-link::before { content: '←'; }

    /* ═══════════════════════════════════════════════════════════
       CONTENT WRAPPER
    ═══════════════════════════════════════════════════════════ */
    .wrap {
      max-width: var(--w);
      margin: 0 auto;
      padding: 0 1.5rem 5rem;
    }

    /* ═══════════════════════════════════════════════════════════
       SHARED SECTION CHROME
    ═══════════════════════════════════════════════════════════ */
    .section { padding: 3rem 0 0; }
    .divider {
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--border), transparent);
      margin-top: 3rem;
    }
    .sec-label {
      font-size: 0.71rem;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 0.55rem;
    }
    .sec-num {
      display: inline-block;
      font-size: 0.65rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      background: var(--accent-bg);
      color: var(--green-mid);
      border: 1px solid #b8dfc8;
      border-radius: 999px;
      padding: 0.15rem 0.6rem;
      margin-right: 0.45rem;
      vertical-align: middle;
    }
    h2 {
      font-family: var(--font-head);
      font-size: 1.38rem;
      font-weight: 700;
      color: var(--text-dark);
      line-height: 1.3;
      margin-bottom: 1.1rem;
    }
    h3 {
      font-family: var(--font-body);
      font-size: 1rem;
      font-weight: 700;
      color: var(--text-dark);
      margin-bottom: 0.45rem;
    }
    p { margin-bottom: 1rem; font-size: 0.97rem; }
    p:last-child { margin-bottom: 0; }

    /* ═══════════════════════════════════════════════════════════
       ③  SKILLS BAR
    ═══════════════════════════════════════════════════════════ */
    .skills-section {
      padding: 2rem 0;
      border-bottom: 1px solid var(--border);
    }
    .skills-label {
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--text-muted);
      margin-bottom: 0.75rem;
    }
    .pills { display: flex; flex-wrap: wrap; gap: 0.5rem; }
    .pill {
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      color: var(--text-dark);
      font-size: 0.82rem;
      font-weight: 600;
      padding: 0.35rem 0.9rem;
      border-radius: 999px;
      transition: background 0.2s, border-color 0.2s, color 0.2s;
      cursor: default;
    }
    .pill:hover {
      background: var(--accent-bg);
      border-color: var(--green);
      color: var(--green-mid);
    }
    .pill-dot {
      width: 6px; height: 6px;
      border-radius: 50%;
      background: var(--green);
      flex-shrink: 0;
    }

    /* ═══════════════════════════════════════════════════════════
       ④  ACHIEVEMENT STATEMENT
    ═══════════════════════════════════════════════════════════ */
    .achievement-banner {
      background: linear-gradient(115deg, var(--blue) 0%, var(--green) 100%);
      border-radius: var(--r-lg);
      padding: 2.3rem 2.6rem;
      margin-top: 1.5rem;
      position: relative;
      overflow: hidden;
    }
    .achievement-banner::after {
      content: '"';
      position: absolute;
      top: -0.8rem; right: 1.8rem;
      font-family: var(--font-head);
      font-size: 10rem;
      color: rgba(255,255,255,0.06);
      line-height: 1;
      pointer-events: none;
    }
    .ach-label {
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: rgba(255,255,255,0.58);
      margin-bottom: 0.65rem;
    }
    .achievement-banner blockquote {
      font-family: var(--font-head);
      font-size: clamp(0.98rem, 2.4vw, 1.18rem);
      font-weight: 300;
      font-style: italic;
      color: #fff;
      line-height: 1.65;
      border: none;
      padding: 0;
    }
    .achievement-banner blockquote strong {
      font-weight: 700;
      font-style: normal;
    }

    /* ═══════════════════════════════════════════════════════════
       ⑤  INFOGRAPHIC PLACEHOLDER
    ═══════════════════════════════════════════════════════════ */
    .infographic-placeholder {
      border: 2px dashed var(--border);
      border-radius: var(--r-lg);
      background: var(--bg-subtle);
      margin-top: 1.8rem;
      min-height: 360px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 3rem 2rem;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .infographic-placeholder::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 3px;
      background: linear-gradient(90deg, var(--blue), var(--green));
      border-radius: var(--r-lg) var(--r-lg) 0 0;
    }
    .infog-ph-icon { font-size: 2.8rem; margin-bottom: 1rem; opacity: 0.35; line-height: 1; }
    .infog-ph-tag {
      font-size: 0.68rem;
      font-weight: 700;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 0.4rem;
    }
    .infog-ph-title {
      font-family: var(--font-head);
      font-size: 1.05rem;
      font-weight: 700;
      color: var(--text-dark);
      margin-bottom: 0.7rem;
    }
    .infog-ph-desc {
      font-size: 0.83rem;
      font-style: italic;
      color: var(--text-muted);
      max-width: 440px;
      line-height: 1.6;
    }
    .infog-ph-note {
      margin-top: 1.4rem;
      font-size: 0.78rem;
      font-weight: 600;
      color: var(--blue);
      background: rgba(21,87,153,0.06);
      border: 1px solid rgba(21,87,153,0.18);
      border-radius: 999px;
      padding: 0.3rem 1rem;
      display: inline-block;
    }

    /* ═══════════════════════════════════════════════════════════
       ⑥  PROJECT STATS  (4 cards)
    ═══════════════════════════════════════════════════════════ */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(165px, 1fr));
      gap: 1rem;
      margin-top: 1.5rem;
    }
    .stat-card {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-radius: var(--r-lg);
      padding: 1.4rem 1.2rem 1.15rem;
      text-align: center;
      transition: box-shadow 0.25s, transform 0.2s;
    }
    .stat-card:hover { box-shadow: var(--shadow-up); transform: translateY(-2px); }
    .stat-num {
      font-family: var(--font-head);
      font-size: 2.1rem;
      font-weight: 700;
      color: var(--blue);
      line-height: 1;
      letter-spacing: -0.02em;
      margin-bottom: 0.28rem;
    }
    .stat-num sup { font-size: 1rem; color: var(--green); }
    .stat-unit {
      font-size: 0.75rem;
      font-weight: 700;
      letter-spacing: 0.07em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 0.5rem;
    }
    .stat-card p { font-size: 0.82rem; color: var(--text); line-height: 1.45; margin: 0; }

    /* ═══════════════════════════════════════════════════════════
       ⑦  PROBLEM STATEMENT — callout boxes
    ═══════════════════════════════════════════════════════════ */
    .note-box {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-radius: var(--r);
      padding: 1rem 1.35rem;
      font-size: 0.88rem;
      color: var(--text);
      margin-top: 1.1rem;
      line-height: 1.65;
    }
    .note-box.green { border-left: 3px solid var(--green); }
    .note-box.blue  { border-left: 3px solid var(--blue); }
    .note-box.amber { border-left: 3px solid var(--amber); }
    .note-box strong { color: var(--text-dark); }

    /* ═══════════════════════════════════════════════════════════
       ⑧  METHODOLOGY — numbered steps
    ═══════════════════════════════════════════════════════════ */
    .method-steps {
      display: grid;
      gap: 0;
      margin-top: 1.5rem;
      border: 1px solid var(--border);
      border-radius: var(--r-lg);
      overflow: hidden;
    }
    .method-step {
      display: grid;
      grid-template-columns: 62px 1fr;
      border-bottom: 1px solid var(--border);
    }
    .method-step:last-child { border-bottom: none; }
    .step-num {
      background: var(--bg-subtle);
      border-right: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: var(--font-head);
      font-size: 1.1rem;
      font-weight: 700;
      color: var(--green);
      padding: 1.2rem 0.4rem;
    }
    .step-body { padding: 1.15rem 1.4rem; }
    .step-body h3 { font-size: 0.93rem; color: var(--text-dark); margin-bottom: 0.3rem; }
    .step-body p  { font-size: 0.88rem; margin: 0 0 0.6rem; color: var(--text); }
    .step-body p:last-child { margin-bottom: 0; }
    .step-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.4rem;
      margin-top: 0.55rem;
    }
    .step-tag {
      font-size: 0.72rem;
      font-weight: 700;
      letter-spacing: 0.04em;
      padding: 0.18rem 0.6rem;
      border-radius: 4px;
      background: var(--accent-bg);
      color: var(--green-mid);
      border: 1px solid #b8dfc8;
    }
    .step-tag.blue {
      background: rgba(21,87,153,0.07);
      color: var(--blue);
      border-color: rgba(21,87,153,0.2);
    }
    .step-tag.amber {
      background: rgba(200,134,26,0.08);
      color: #8a5c0e;
      border-color: rgba(200,134,26,0.25);
    }

    /* ═══════════════════════════════════════════════════════════
       ⑨  QUANTIFIABLE RESULTS — tables
    ═══════════════════════════════════════════════════════════ */
    .table-caption {
      font-size: 0.82rem;
      font-weight: 700;
      color: var(--blue);
      text-transform: uppercase;
      letter-spacing: 0.05em;
      margin: 1.6rem 0 0;
    }
    .table-wrap {
      overflow-x: auto;
      border-radius: var(--r);
      border: 1px solid var(--border);
      margin-top: 0.75rem;
    }
    .table-wrap table { width: 100%; border-collapse: collapse; font-size: 0.85rem; }
    .table-wrap thead { background: linear-gradient(90deg, var(--blue), var(--green)); }
    .table-wrap thead th {
      color: #fff;
      font-weight: 700;
      font-size: 0.77rem;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      padding: 0.72rem 1rem;
      text-align: left;
      white-space: nowrap;
    }
    .table-wrap tbody tr:nth-child(even) { background: var(--bg-subtle); }
    .table-wrap tbody td {
      padding: 0.62rem 1rem;
      color: var(--text);
      border-bottom: 1px solid var(--border);
      vertical-align: middle;
    }
    .table-wrap tbody tr:last-child td { border-bottom: none; }
    .table-wrap tbody td:first-child { font-weight: 600; color: var(--text-dark); }
    .table-wrap tbody tr.total-row td {
      font-weight: 700;
      color: var(--text-dark);
      background: var(--accent-bg);
      font-size: 0.88rem;
      border-top: 1px solid var(--border);
    }
    .err-low  { color: #159957; font-weight: 700; }
    .err-mid  { color: #c8861a; font-weight: 700; }
    .err-high { color: #c0392b; font-weight: 700; }
    .dot-in  { display:inline-block; width:8px; height:8px; border-radius:50%; background:var(--blue); margin-right:6px; vertical-align:middle; }
    .dot-out { display:inline-block; width:8px; height:8px; border-radius:50%; background:var(--green); margin-right:6px; vertical-align:middle; }

    .deviation-note {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-left: 3px solid var(--amber);
      border-radius: var(--r);
      padding: 0.95rem 1.3rem;
      font-size: 0.84rem;
      color: var(--text);
      margin-top: 1.1rem;
      line-height: 1.6;
    }
    .deviation-note strong { color: var(--text-dark); }

    /* inline placeholder (below tables) */
    .placeholder {
      border: 2px dashed var(--border);
      border-radius: var(--r-lg);
      background: var(--bg-subtle);
      padding: 2.5rem 2rem;
      text-align: center;
      margin-top: 1.5rem;
    }
    .ph-icon { font-size: 2rem; margin-bottom: 0.5rem; opacity: 0.45; }
    .ph-tag {
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.13em;
      text-transform: uppercase;
      color: var(--green);
      margin-bottom: 0.3rem;
    }
    .ph-desc {
      font-size: 0.82rem;
      font-style: italic;
      color: var(--text-muted);
      max-width: 420px;
      margin: 0 auto;
      line-height: 1.55;
    }

    /* ═══════════════════════════════════════════════════════════
       ⑩  3 MAIN RESULTS STATS — headline trio
    ═══════════════════════════════════════════════════════════ */
    .results-trio {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      border: 1px solid var(--border);
      border-radius: var(--r-lg);
      overflow: hidden;
      margin-top: 1.5rem;
    }
    .result-cell {
      padding: 2rem 1.4rem;
      text-align: center;
      border-right: 1px solid var(--border);
      background: var(--bg);
      position: relative;
    }
    .result-cell:last-child { border-right: none; }
    .result-cell::before {
      content: '';
      display: block;
      height: 3px;
      background: linear-gradient(90deg, var(--blue), var(--green));
      position: absolute;
      top: 0; left: 0; right: 0;
    }
    .result-big {
      font-family: var(--font-head);
      font-size: 2.5rem;
      font-weight: 700;
      color: var(--blue);
      line-height: 1;
      letter-spacing: -0.03em;
    }
    .result-unit {
      font-size: 0.77rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--green);
      margin: 0.3rem 0 0.6rem;
    }
    .result-desc { font-size: 0.82rem; color: var(--text); line-height: 1.45; }

    /* ═══════════════════════════════════════════════════════════
       ⑪  KEY FINDINGS GRID
    ═══════════════════════════════════════════════════════════ */
    .findings-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(258px, 1fr));
      gap: 1.1rem;
      margin-top: 1.5rem;
    }
    .finding-card {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-left: 3px solid var(--green);
      border-radius: var(--r);
      padding: 1.2rem 1.3rem;
      transition: box-shadow 0.2s;
    }
    .finding-card.rca  { border-left-color: var(--blue); }
    .finding-card.capex { border-left-color: var(--amber); }
    .finding-card:hover { box-shadow: var(--shadow); }
    .finding-card h3 {
      font-size: 0.85rem;
      font-weight: 700;
      color: var(--blue);
      text-transform: uppercase;
      letter-spacing: 0.05em;
      margin-bottom: 0.4rem;
    }
    .finding-card.rca   h3 { color: var(--blue); }
    .finding-card.capex h3 { color: #8a5c0e; }
    .finding-card p { font-size: 0.86rem; margin: 0; line-height: 1.55; }
    .find-pill {
      display: inline-block;
      font-size: 0.62rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      border-radius: 999px;
      padding: 0.12rem 0.55rem;
      margin-bottom: 0.55rem;
    }
    .find-pill.rca   { background: rgba(21,87,153,0.1);  color: var(--blue); border: 1px solid rgba(21,87,153,0.2); }
    .find-pill.capex { background: rgba(200,134,26,0.1); color: #8a5c0e;     border: 1px solid rgba(200,134,26,0.25); }
    .find-pill.find  { background: var(--accent-bg);     color: var(--green-mid); border: 1px solid #b8dfc8; }
    .find-pill.learn { background: rgba(21,87,153,0.06); color: var(--blue); border: 1px solid rgba(21,87,153,0.15); }

    /* ═══════════════════════════════════════════════════════════
       ⑫  PROJECT CONTEXT — scope cards
    ═══════════════════════════════════════════════════════════ */
    .context-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 1rem;
      margin-top: 1.5rem;
    }
    .context-card {
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: var(--r-lg);
      padding: 1.3rem 1.4rem;
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
      transition: box-shadow 0.2s, transform 0.18s;
    }
    .context-card:hover { box-shadow: var(--shadow-up); transform: translateY(-2px); }
    .ctx-icon { font-size: 1.5rem; line-height: 1; }
    .context-card h3 { font-size: 0.93rem; margin: 0; }
    .context-card p  { font-size: 0.83rem; margin: 0; color: var(--text); line-height: 1.5; }
    .context-card .outcome-pill {
      display: inline-block;
      margin-top: 0.2rem;
      font-size: 0.78rem;
      font-weight: 700;
      color: var(--green-mid);
      background: var(--accent-bg);
      border: 1px solid #b8dfc8;
      border-radius: 999px;
      padding: 0.2rem 0.75rem;
    }

    /* ═══════════════════════════════════════════════════════════
       FOOTER
    ═══════════════════════════════════════════════════════════ */
    .site-footer {
      background: var(--bg-subtle);
      border-top: 1px solid var(--border);
      text-align: center;
      padding: 2rem 1.5rem;
      margin-top: 4rem;
    }
    .site-footer p { font-size: 0.81rem; color: var(--text-muted); margin: 0; }

    /* ═══════════════════════════════════════════════════════════
       ANIMATIONS
    ═══════════════════════════════════════════════════════════ */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(16px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .site-header > * { animation: fadeUp 0.6s ease both; }
    .site-header > *:nth-child(1) { animation-delay: 0.05s; }
    .site-header > *:nth-child(2) { animation-delay: 0.15s; }
    .site-header > *:nth-child(3) { animation-delay: 0.25s; }
    .site-header > *:nth-child(4) { animation-delay: 0.35s; }
    .site-header > *:nth-child(5) { animation-delay: 0.42s; }

    /* ═══════════════════════════════════════════════════════════
       RESPONSIVE
    ═══════════════════════════════════════════════════════════ */
    @media (max-width: 600px) {
      .site-header { padding: 2.6rem 1.2rem 2.2rem; }
      .wrap { padding: 0 1rem 4rem; }
      h2 { font-size: 1.2rem; }
      .results-trio { grid-template-columns: 1fr; }
      .result-cell { border-right: none; border-bottom: 1px solid var(--border); }
      .result-cell:last-child { border-bottom: none; }
      .achievement-banner { padding: 1.8rem 1.4rem; }
      .infographic-placeholder { min-height: 280px; }
    }
  </style>
</head>
<body>


<!-- ════════════════════════════════════════════════════════════
     ①  FIELD – SUB-FIELD    +    ②  MAIN HEAD
════════════════════════════════════════════════════════════ -->
<header class="site-header">

  <!-- ① Field – Sub-field -->
  <p class="field-label">
    Process Engineering
    <span class="field-divider">/</span>
    <span>Industrial Plant Design &amp; Design Verification</span>
  </p>

  <!-- ② Main Head -->
  <h1>
    Process Design &amp; Verification: 4,000 TPD Greenfield Pyro-Processing Unit<br>
    <em>Independent Design Cross-Validation of Cement Manufacturing Line Installed In 2023</em>
  </h1>

  <p class="header-sub">
    Independent cross-verification of process design of a $50M, 4,000 TPD greenfield pyro-processing line installed by HCRDI. Mass and energy balance calculations and pressure profile of the 5-stage preheater system helped identify a 2.47 mbar discrepancy in the first two cyclone stages. Based on findings, the cyclone stack was modified during installation, resulting in a 3.6% reduction in specific energy consumption.
  </p>

  <a href="/" class="back-link">&nbsp;Back to Portfolio</a>

</header>


<main class="wrap">

  <!-- ════════════════════════════════════════════════════════════
       ③  SKILLS USED IN THIS PROJECT
  ════════════════════════════════════════════════════════════ -->
  <div class="skills-section">
    <p class="skills-label"><span class="sec-num">03</span> Skills Used in This Project</p>
    <div class="pills">
      <span class="pill"><span class="pill-dot"></span>Fluid Dynamics &amp; Pressure Drop Analysis (RCA)</span>
      <span class="pill"><span class="pill-dot"></span>Manual Equipment Sizing &amp; Optimization &amp; Anemometry</span>
      <span class="pill"><span class="pill-dot"></span>Mass &amp; Energy Balance &amp; Fan Curve Analysis</span>
      <span class="pill"><span class="pill-dot"></span>Combustion Kinetics</span>
      <span class="pill"><span class="pill-dot"></span>Micrsoft Excel</span>
      <span class="pill"><span class="pill-dot"></span>Technical Audit</span>
    </div>
  </div>


  <!-- ════════════════════════════════════════════════════════════
       ④  ACHIEVEMENT STATEMENT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="ach-h">
    <p class="sec-label"><span class="sec-num">04</span> Achievement</p>
    <h2 id="ach-h">Turning a Control Room Mirage into a CapEx Decision</h2>
    <div class="achievement-banner">
      <p class="ach-label">Core Achievement</p>
      <blockquote>
        By exposing an <strong>18% systematic overstatement</strong> in CCR-displayed fan flows — traced through Root Cause Analysis to an <strong>incorrect fan curve programmed in the PLC</strong> — the plant's thermodynamic model was corrected from first-principles field data, achieving an <strong>elite 0.25% heat balance closure</strong>. This directly demonstrated that the existing fan fleet, even when properly characterised, was physically incapable of meeting the 136,250 kg/hr production demand — producing the data-backed justification for the procurement and installation of an additional unit, improving total plant cooling efficiency and OpEx.
      </blockquote>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑤  INFOGRAPHIC  — placeholder for user to add their own
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="infog-h">
    <p class="sec-label"><span class="sec-num">05</span> Project Overview</p>
    <h2 id="infog-h">The Full Picture at a Glance</h2>
    <div class="infographic-placeholder">
      <div class="infog-ph-icon">🗺️</div>
      <p class="infog-ph-tag">Your Infographic Goes Here</p>
      <p class="infog-ph-title">Project Overview Infographic</p>
      <p class="infog-ph-desc">
        Replace this block with your visual overview of the project — for example, a three-panel diagram showing the problem (CCR displaying inflated flows), the method (physical fan audit + pitot traverse + RCA), and the result (corrected heat balance + fan unit recommendation). An SVG, PNG, or embedded HTML visual all work here.
      </p>
      <span class="infog-ph-note">📐 Recommended dimensions: 860 × 360 px or wider</span>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑥  PROJECT STATS  (4 cards)
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="stats-h">
    <p class="sec-label"><span class="sec-num">06</span> Project at a Glance</p>
    <h2 id="stats-h">Four Numbers That Define the Work</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">18<sup>%</sup></div>
        <div class="stat-unit">Flow Discrepancy</div>
        <p>Average CCR overstatement across the most affected fans — traced to an incorrect PLC fan curve rather than a physical fault</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">8</div>
        <div class="stat-unit">Fans Audited</div>
        <p>All eight cooler fans independently measured with three anemometer passes each, then normalised to NM³ at standard conditions</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">0.25<sup>%</sup></div>
        <div class="stat-unit">Balance Closure</div>
        <p>Heat balance closure error achieved — 8× tighter than the ±2% industry benchmark, validating the corrected measurement dataset</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">+1</div>
        <div class="stat-unit">Unit Approved</div>
        <p>Additional cooler fan recommended and approved by management — the first capital decision at Line-2 driven by a quantified engineering audit</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑦  PROBLEM STATEMENT & COMMISSION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="problem-h">
    <p class="sec-label"><span class="sec-num">07</span> Problem Statement &amp; Commission</p>
    <h2 id="problem-h">The Plant Was Running on a Control System That Was Quietly Hallucinating</h2>

    <p>
      On Kiln Line-2, producing <strong>136,250 kg of clinker per hour</strong>, the clinker cooler is one of the most operationally critical sub-systems in the entire pyro-processing unit. After exiting the rotary kiln at approximately 1,450 °C, clinker must be cooled rapidly and uniformly — a process entirely dependent on the volume of air delivered by the eight cooler fans. The cooling air flowrate governs clinker quality, grindability, heat recovery to the kiln, and the thermal energy available for capture in the cooler vent stream.
    </p>
    <p>
      The Central Control Room (CCR) reported a combined total cooling air flow of <strong>91.59 m³/s</strong> across all fans. These readings came directly from the <strong>Programmable Logic Controller (PLC)</strong>, which calculates volumetric flow using a pre-programmed mathematical fan curve — typically a polynomial relating motor RPM or damper position to expected output: <em>Q = f(RPM, ΔP)</em>. If the fan curve is correct, this is a reliable, non-intrusive method of flow estimation. If it is not, every process decision downstream rests on a number that has no physical basis.
    </p>
    <p>
      No independent physical verification of fan performance had ever been conducted. Operators were adjusting cooling zones, monitoring air-to-clinker ratios, and benchmarking energy efficiency — all against CCR values that had never been checked against the physical hardware. If the fan curve was misconfigured, due to impeller wear, duct geometry changes, or simply wrong commissioning data, the control system would display a <strong>"theoretical" flow</strong> that bore no relation to what was actually entering the kiln cooler. The plant would be unknowingly under-cooling clinker, and operators would see no alarm.
    </p>

    <div class="note-box green">
      <strong>Commission:</strong> As part of a comprehensive thermodynamic heat balance on the pyro-processing unit, commissioned by AGM Production, physically measure the flowrate of every cooler fan, cross-validate all readings against CCR panel values, quantify any discrepancies, and conduct a Root Cause Analysis. Submit a data-backed engineering recommendation on corrective action.
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑧  METHODOLOGY & EXECUTION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="method-h">
    <p class="sec-label"><span class="sec-num">08</span> Methodology &amp; Execution</p>
    <h2 id="method-h">From Assumed Flow to Measured Flow — A Four-Phase Field Audit</h2>

    <p>
      The audit was designed from the outset to be entirely evidence-driven. No CCR reading was accepted as an input to the heat balance without independent physical corroboration. The campaign proceeded in four structured phases, each feeding directly into the next.
    </p>

    <div class="method-steps">

      <div class="method-step">
        <div class="step-num">01</div>
        <div class="step-body">
          <h3>Physical Fan Flow Measurement — Anemometry on All Eight Fans</h3>
          <p>Each cooler fan was measured independently using a calibrated anemometer. Three velocity readings were taken per fan across the inlet cross-section, and the average was used to compute volumetric flow via <em>Q = v × A</em>. Duct and fan inlet diameters were confirmed by direct measurement using a metric tape. All computed flows were normalised from actual m³ to standard NM³ (273 K, 101.325 kPa) using the ideal gas equation of state, correcting for each fan's rated pressure and inlet temperature. The resulting physical flowrates were then placed side-by-side with the corresponding CCR values for each unit — this juxtaposition was where the discrepancy became immediately visible.</p>
          <div class="step-tags">
            <span class="step-tag">Anemometry</span>
            <span class="step-tag">Q = v × A</span>
            <span class="step-tag">NM³ Normalisation</span>
            <span class="step-tag">Equation of State</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">02</div>
        <div class="step-body">
          <h3>Duct Velocity Traversal — Pitot Tube at Preheater Exhaust &amp; Cooler Vent</h3>
          <p>Pitot tube and digital manometer measurements were taken at six radial positions inside both the 3.3 m diameter preheater exhaust duct and the 4 m × 1.5 m rectangular cooler vent duct. Total and static pressures were recorded at each traverse point. Gas velocities were derived from differential pressures using Bernoulli's equation (pitot tube factor P<sub>T</sub> = 0.65), averaged across the six positions to produce a representative mean velocity, and used to calculate duct-level volumetric flowrates — also normalised to NM³. These measurements gave independent, direct quantification of the two largest gas streams exiting the system boundary.</p>
          <div class="step-tags">
            <span class="step-tag">Pitot Tube Traversal</span>
            <span class="step-tag">Bernoulli's Equation</span>
            <span class="step-tag">Digital Manometry</span>
            <span class="step-tag blue">6-Point Averaging</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">03</div>
        <div class="step-body">
          <h3>Full Thermodynamic Heat Balance — 11 Streams, First Principles</h3>
          <p>Using all physically verified flowrates and temperatures sourced from on-site measurements and QC records, a complete heat balance was performed across the defined system boundary — preheater cyclone inlet to cooler vent outlet. Five input streams (raw meal, combustion, cooler fan air, primary air, coal blower air) and six output streams (clinker formation enthalpy, preheater exhaust gases, cooler vent air, radiation and convection losses, clinker discharge, moisture evaporation) were individually quantified per kilogram of clinker produced. Radiation losses from 64 kiln shell measurement stations were computed via <strong>Stefan-Boltzmann Law</strong> (ε = 0.9 for mild steel); convective losses via <strong>Fourier's Law</strong> using coefficients from the Peray Cement Handbook. The balance achieved closure of <strong>0.25%</strong> — a direct result of replacing PLC-estimated flows with physically measured values.</p>
          <div class="step-tags">
            <span class="step-tag">Stefan-Boltzmann Law</span>
            <span class="step-tag">Fourier's Law</span>
            <span class="step-tag">Sensible Heat Analysis</span>
            <span class="step-tag blue">64-Point Shell Survey</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">04</div>
        <div class="step-body">
          <h3>Root Cause Analysis — PLC Fan Curve Investigation &amp; Engineering Recommendation</h3>
          <p>With a confirmed 18% gap between measured and displayed flows across multiple fans, the RCA was structured to answer one question: was this a sensor fault, mechanical degradation, or a control system programming error? The investigation concluded that the <strong>PLC fan curve was the root cause</strong> — the mathematical relationship programmed into the controller no longer matched the physical behaviour of the fan fleet, likely due to a combination of commissioning data that was never field-validated and cumulative impeller degradation over service life. This distinction was operationally critical: it meant the 18% gap was not a symptom of mechanical failure that maintenance could address, but a <strong>systematic capacity gap</strong> that required a structural solution. The finding was compiled into a formal engineering recommendation report submitted to AGM Production, proposing an additional fan unit as the most effective corrective measure, supported by the corrected mass flow calculations and OpEx impact analysis.</p>
          <div class="step-tags">
            <span class="step-tag amber">Root Cause Analysis</span>
            <span class="step-tag amber">PLC Fan Curve Diagnosis</span>
            <span class="step-tag">Engineering Report</span>
            <span class="step-tag">CapEx Justification</span>
          </div>
        </div>
      </div>

    </div>

  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑨  QUANTIFIABLE RESULTS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="results-h">
    <p class="sec-label"><span class="sec-num">09</span> Quantifiable Results</p>
    <h2 id="results-h">The Numbers That Made the Case</h2>

    <p>
      The two tables below are the core quantitative evidence of this project. The first exposes the per-fan discrepancy between what the CCR displayed and what physical measurement confirmed. The second is the resulting heat balance — which reached 0.25% closure <em>only because</em> the corrected fan flows were used as inputs, replacing the PLC's inflated estimates.
    </p>

    <!-- FAN FLOW AUDIT TABLE -->
    <p class="table-caption">Fan Flow Audit — CCR Display vs. Physical Measurement</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Fan</th>
            <th>Avg. Velocity (m/s)</th>
            <th>Duct Ø (m)</th>
            <th>Measured Flow (m³/s)</th>
            <th>CCR Flow (m³/s)</th>
            <th>Delta</th>
            <th>Verdict</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Fan 1</td>
            <td>15.14</td>
            <td>0.60</td>
            <td>4.39</td>
            <td>5.19</td>
            <td class="err-high">+18.2 %</td>
            <td class="err-high">CCR overstates</td>
          </tr>
          <tr>
            <td>Fan 2</td>
            <td>57.13</td>
            <td>0.73</td>
            <td>6.64</td>
            <td>7.92</td>
            <td class="err-high">+19.3 %</td>
            <td class="err-high">CCR overstates</td>
          </tr>
          <tr>
            <td>Fan 3</td>
            <td>54.97</td>
            <td>1.11</td>
            <td>14.78</td>
            <td>16.34</td>
            <td class="err-mid">+10.6 %</td>
            <td class="err-mid">CCR overstates</td>
          </tr>
          <tr>
            <td>Fan 4</td>
            <td>46.80</td>
            <td>1.17</td>
            <td>13.98</td>
            <td>17.94</td>
            <td class="err-high">+28.3 %</td>
            <td class="err-high">CCR overstates</td>
          </tr>
          <tr>
            <td>Fan 5</td>
            <td>42.17</td>
            <td>1.23</td>
            <td>13.92</td>
            <td>12.09</td>
            <td class="err-low">−13.1 %</td>
            <td class="err-low">CCR understates</td>
          </tr>
          <tr>
            <td>Fan 6</td>
            <td>46.90</td>
            <td>1.14</td>
            <td>13.30</td>
            <td>13.20</td>
            <td class="err-low">−0.8 %</td>
            <td class="err-low">Consistent</td>
          </tr>
          <tr>
            <td>Fan 7</td>
            <td>24.83</td>
            <td>1.25</td>
            <td>8.47</td>
            <td>10.26</td>
            <td class="err-high">+21.1 %</td>
            <td class="err-high">CCR overstates</td>
          </tr>
          <tr>
            <td>Fan 8</td>
            <td>—</td>
            <td>—</td>
            <td>—</td>
            <td>8.65</td>
            <td>—</td>
            <td style="color:var(--text-muted);font-size:0.8rem;">Not physically measured</td>
          </tr>
          <tr class="total-row">
            <td>Total (Fans 1–7)</td>
            <td>—</td>
            <td>—</td>
            <td>75.48 m³/s</td>
            <td>82.94 m³/s</td>
            <td class="err-high">+9.9 % overall</td>
            <td>CCR overstates fleet</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="deviation-note">
      <strong>Note on the 18% headline figure:</strong> The 18% represents the average overstatement across the four most significantly affected fans (Fans 1, 2, 4, and 7), where the PLC fan curve produced estimates 18–28% above physically measured values. This is the operationally meaningful signal: the fans that operators were most confident about were, on average, delivering 18% less air than the control system indicated. Fan 5's understatement (−13%) confirms this is a fleet-wide fan curve calibration problem, not a single-instrument error.
    </div>

    <!-- HEAT BALANCE SUMMARY TABLE -->
    <p class="table-caption">Heat Balance Summary — All 11 Streams (Corrected with Measured Flows)</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Heat Stream</th>
            <th>Direction</th>
            <th style="text-align:right;">Kcal / kg<sub>clk</sub></th>
            <th style="text-align:right;">Share of Total Input</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><span class="dot-in"></span>Heat of Combustion of Fuel</td>
            <td>Input</td>
            <td style="text-align:right;">783.37</td>
            <td style="text-align:right;" class="err-low">97.2 %</td>
          </tr>
          <tr>
            <td><span class="dot-in"></span>Sensible Heat — Raw Meal</td>
            <td>Input</td>
            <td style="text-align:right;">15.78</td>
            <td style="text-align:right;">2.0 %</td>
          </tr>
          <tr>
            <td><span class="dot-in"></span>Sensible Heat — Cooler Fan Air <em style="font-size:0.78rem;color:var(--green);font-style:normal;">(corrected)</em></td>
            <td>Input</td>
            <td style="text-align:right;">6.14</td>
            <td style="text-align:right;">0.8 %</td>
          </tr>
          <tr>
            <td><span class="dot-in"></span>Sensible Heat — Coal Blower Air</td>
            <td>Input</td>
            <td style="text-align:right;">0.37</td>
            <td style="text-align:right;">&lt;0.1 %</td>
          </tr>
          <tr>
            <td><span class="dot-in"></span>Sensible Heat — Primary Air</td>
            <td>Input</td>
            <td style="text-align:right;">0.25</td>
            <td style="text-align:right;">&lt;0.1 %</td>
          </tr>
          <tr class="total-row">
            <td>Total Heat Input</td>
            <td></td>
            <td style="text-align:right;">805.90</td>
            <td style="text-align:right;">100 %</td>
          </tr>
          <tr>
            <td><span class="dot-out"></span>Heat of Clinker Formation</td>
            <td>Output</td>
            <td style="text-align:right;">408.32</td>
            <td style="text-align:right;">50.8 %</td>
          </tr>
          <tr>
            <td><span class="dot-out"></span>Sensible Heat — Preheater Exhaust Gases</td>
            <td>Output</td>
            <td style="text-align:right;">224.50</td>
            <td style="text-align:right;">27.9 %</td>
          </tr>
          <tr>
            <td><span class="dot-out"></span>Sensible Heat — Cooler Vent Air</td>
            <td>Output</td>
            <td style="text-align:right;">91.63</td>
            <td style="text-align:right;">11.4 %</td>
          </tr>
          <tr>
            <td><span class="dot-out"></span>Radiation &amp; Convection Losses — Total</td>
            <td>Output</td>
            <td style="text-align:right;">52.38</td>
            <td style="text-align:right;">6.5 %</td>
          </tr>
          <tr>
            <td><span class="dot-out"></span>Sensible Heat — Clinker Discharge</td>
            <td>Output</td>
            <td style="text-align:right;">17.94</td>
            <td style="text-align:right;">2.2 %</td>
          </tr>
          <tr>
            <td><span class="dot-out"></span>Latent Heat — Moisture Evaporation</td>
            <td>Output</td>
            <td style="text-align:right;">9.11</td>
            <td style="text-align:right;">1.1 %</td>
          </tr>
          <tr class="total-row">
            <td>Total Heat Output</td>
            <td></td>
            <td style="text-align:right;">803.87</td>
            <td style="text-align:right;">99.75 %</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="placeholder">
      <div class="ph-icon">📊</div>
      <p class="ph-tag">Suggested Visual — CCR vs. Measured Fan Flow Comparison</p>
      <p class="ph-desc">A grouped bar chart with Fan 1–7 on the x-axis and m³/s on the y-axis. Two bars per fan — CCR reading (blue) vs. physical measurement (green). Fan 4's 28% overstatement and Fan 5's understatement will immediately stand out as the most visually striking anomalies. Build from Table 2 data in Python matplotlib or Excel.</p>
    </div>

    <div class="placeholder">
      <div class="ph-icon">🌊</div>
      <p class="ph-tag">Suggested Visual — Sankey Diagram</p>
      <p class="ph-desc">A proportional heat flow diagram: inputs on the left (combustion dominates at 783 Kcal/kg), outputs on the right. Clinker formation and preheater exhaust should be the dominant branches; radiation/convection and vent losses are narrower offshoots. Build with SankeyMATIC (free, browser-based) or Python plotly.graph_objects.</p>
    </div>

  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑩  3 MAIN RESULTS STATS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="trio-h">
    <p class="sec-label"><span class="sec-num">10</span> Headline Results</p>
    <h2 id="trio-h">Three Numbers That Tell the Story</h2>
    <div class="results-trio">
      <div class="result-cell">
        <div class="result-big">18%</div>
        <div class="result-unit">PLC Overstatement</div>
        <p class="result-desc">Average CCR flow overstatement across critical fans, traced to an incorrect fan curve in the PLC — not a physical fault, but a control system misconfiguration that made it invisible to operators</p>
      </div>
      <div class="result-cell">
        <div class="result-big">0.25%</div>
        <div class="result-unit">Balance Closure</div>
        <p class="result-desc">Heat balance closure achieved after replacing PLC-estimated flows with physically measured values — 8× tighter than the ±2% industry threshold and direct proof of the correction's validity</p>
      </div>
      <div class="result-cell">
        <div class="result-big">+1 Unit</div>
        <div class="result-unit">CapEx Approved</div>
        <p class="result-desc">Additional cooler fan recommended and approved — the first capital investment decision at Line-2 driven by a quantified, evidence-based engineering audit rather than operational intuition</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑪  KEY FINDINGS & LEARNING OUTCOMES
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="findings-h">
    <p class="sec-label"><span class="sec-num">11</span> Key Findings &amp; Learning Outcomes</p>
    <h2 id="findings-h">What the Audit Actually Uncovered</h2>
    <div class="findings-grid">

      <div class="finding-card rca">
        <span class="find-pill rca">RCA Finding</span>
        <h3>The Mathematical Mirage — PLC Fan Curve as Root Cause</h3>
        <p>The RCA established that the CCR's inflated flow readings were not caused by sensor drift, wiring faults, or mechanical degradation. The root cause was an <strong>incorrect fan curve programmed into the PLC at commissioning</strong> — a polynomial Q = f(RPM, ΔP) that had never been field-validated against the actual installed hardware. Because the PLC was calculating a "theoretical" flow based on this stale curve, the control system was, in effect, hallucinating: reporting a number that had no physical basis. Operators had no way to detect this from within the control room. Only a physical audit could expose it.</p>
      </div>

      <div class="finding-card capex">
        <span class="find-pill capex">CapEx Finding</span>
        <h3>Data-Backed CapEx — Correcting the Thermodynamic Foundation</h3>
        <p>Because the heat balance input for cooler fan air had been inflated by the PLC's incorrect curve, the sensible heat contribution of the fan air stream had been overstated. Without the physical measurement correction, the balance would have shown "missing energy" — which most engineers would have incorrectly attributed to higher kiln shell losses or kiln refractory problems. By correcting the fan flowrates, the balance closed to 0.25%, and the <strong>actual capacity gap was isolated and quantified</strong>: the existing fan fleet, even when accurately characterised, could not deliver the air volume needed at the 136,250 kg/hr production rate. The recommendation for an additional unit was not a precautionary suggestion — it was a mathematically demonstrated necessity.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>Refractory Heterogeneity Drives Kiln Shell Loss Variation</h3>
        <p>The 64-point kiln shell temperature survey revealed a nearly 7× spread in per-metre heat loss — from 0.11 to 1.01 Kcal/kg<sub>clk</sub> — with peak losses concentrated between meters 19 and 28. This spatial pattern is the thermodynamic signature of localised refractory thinning or degradation. It provides a prioritised, location-specific case for targeted refractory inspection and selective replacement — not a full kiln reline, but precision maintenance directed exactly where it will have the most thermal impact.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>Cooler Vent Air — The Highest-Potential Heat Recovery Target</h3>
        <p>Carrying 91.6 Kcal/kg<sub>clk</sub> at 380 °C, the cooler vent stream exits the system boundary with substantial, recoverable enthalpy. Unlike preheater exhaust recovery — which requires integration with the conditioning tower — vent air recovery can be implemented via an independent heat exchanger or ORC unit with no upstream process disruption. This was documented in the final report as the most actionable waste heat recovery opportunity available to Line-2 operations.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill learn">Learning</span>
        <h3>Physical Measurement Rigor is What Made 0.25% Closure Possible</h3>
        <p>Three anemometer passes per fan, six pitot-tube readings per duct, and independent diameter confirmation at every measurement point — the redundancy was deliberate. A single uncorrected fan reading or an assumed duct diameter would have cascaded an error through all downstream sensible heat calculations. The 0.25% closure is not just a result; it is the direct quantitative proof that the measurement campaign was rigorous enough to be trusted as the thermodynamic foundation for a capital investment recommendation.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill learn">Learning</span>
        <h3>NM³ Normalisation — A Non-Negotiable Data Integrity Practice</h3>
        <p>The coal blowers operate at 58.8 kPa gauge pressure and 40 °C. Without applying the full equation of state (P₁V₁/T₁ = P₂V₂/T₂) to convert to standard conditions, their contribution to the heat balance would be overstated by approximately 50%. Applying consistent NM³ normalisation across all streams — atmospheric cooler fans, pressurised blowers, and hot exhaust gases — was the single most important data-quality discipline in the entire calculation chain, and the step most likely to be silently skipped under production pressure.</p>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑫  PROJECT CONTEXT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="context-h">
    <p class="sec-label"><span class="sec-num">12</span> Project Context</p>
    <h2 id="context-h">Scope, Setting &amp; Deliverables</h2>

    <p>
      This audit was commissioned by AGM Production and executed as a live engineering assignment on an operating cement production line. Every parameter was physically measured or sourced from plant Quality Control and CCR records — no modelled or assumed values were used for primary flowrate inputs. Each card below represents a discrete, evidenced deliverable.
    </p>

    <div class="context-grid">
      <div class="context-card">
        <span class="ctx-icon">⚙️</span>
        <h3>Role</h3>
        <p>Process Engineer — Lead Auditor. Responsible for the full measurement campaign, thermodynamic modelling, RCA, and the final engineering recommendation report.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">🏭</span>
        <h3>Unit Under Audit</h3>
        <p>Pyro-Processing Line-2: full boundary from preheater cyclone inlet to clinker cooler vent outlet. Clinker output rate of 136,250 kg/hr.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">🔧</span>
        <h3>Instruments Used</h3>
        <p>Anemometer (3 passes per fan), Pitot tube &amp; digital manometer (6-point radial traverse), infrared thermometer (64 shell stations + full preheater surface).</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📐</span>
        <h3>Heat Balance Scope</h3>
        <p>11 heat streams fully quantified — 5 inputs (combustion, raw meal, cooler fans, primary air, coal blowers) and 6 outputs (clinker formation, preheater exhaust, vent air, R&amp;C losses, clinker discharge, moisture).</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📋</span>
        <h3>Key Deliverable</h3>
        <p>Heat balance report with corrected fan flowrates, PLC fan curve RCA findings, and a formally submitted engineering recommendation for an additional cooler fan unit.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">✅</span>
        <h3>Outcome</h3>
        <p>Recommendation accepted by management.</p>
        <span class="outcome-pill">Additional fan unit approved</span>
      </div>
    </div>

  </section>

</main>


<!-- ════════════════════════════════════════════════════════════
     FOOTER
════════════════════════════════════════════════════════════ -->
<footer class="site-footer">
  <p>
    Process Engineering Portfolio &nbsp;·&nbsp;
    Pyro-Processing Heat Balance &amp; Fan Audit — Line-2 &nbsp;·&nbsp;
    <a href="/">← Back to Portfolio</a>
  </p>
</footer>


</body>
</html>
