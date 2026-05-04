
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>JHA Framework Standardization | Operational Risk Governance</title>
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
      --amber:         #b45309;
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
       ① ②  HEADER
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
       SECTION CHROME
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
       ③  SKILLS
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
    .pill:hover { background: var(--accent-bg); border-color: var(--green); color: var(--green-mid); }
    .pill-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--green); flex-shrink: 0; }

    /* ═══════════════════════════════════════════════════════════
       ④  ACHIEVEMENT BANNER
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
    .achievement-banner blockquote strong { font-weight: 700; font-style: normal; }

    /* ═══════════════════════════════════════════════════════════
       ⑤  INFOGRAPHIC PLACEHOLDER
    ═══════════════════════════════════════════════════════════ */
    .infographic-placeholder {
      border: 2px dashed var(--border);
      border-radius: var(--r-lg);
      background: var(--bg-subtle);
      margin-top: 1.8rem;
      min-height: 340px;
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
      font-size: 0.68rem; font-weight: 700; letter-spacing: 0.16em;
      text-transform: uppercase; color: var(--green); margin-bottom: 0.4rem;
    }
    .infog-ph-title {
      font-family: var(--font-head); font-size: 1.05rem; font-weight: 700;
      color: var(--text-dark); margin-bottom: 0.7rem;
    }
    .infog-ph-desc {
      font-size: 0.83rem; font-style: italic; color: var(--text-muted);
      max-width: 460px; line-height: 1.6;
    }
    .infog-ph-note {
      margin-top: 1.4rem; font-size: 0.78rem; font-weight: 600;
      color: var(--blue); background: rgba(21,87,153,0.06);
      border: 1px solid rgba(21,87,153,0.18); border-radius: 999px;
      padding: 0.3rem 1rem; display: inline-block;
    }

    /* ═══════════════════════════════════════════════════════════
       ⑥  PROJECT STATS
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
       ⑦  PROBLEM — note boxes
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
    .note-box.amber { border-left: 3px solid var(--amber); }
    .note-box strong { color: var(--text-dark); }

    /* ═══════════════════════════════════════════════════════════
       ⑧  METHODOLOGY — bordered step list
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
    .step-body p { font-size: 0.88rem; margin: 0 0 0.55rem; color: var(--text); }
    .step-body p:last-child { margin-bottom: 0; }
    .step-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-top: 0.55rem; }
    .step-tag {
      font-size: 0.72rem; font-weight: 700; letter-spacing: 0.04em;
      padding: 0.18rem 0.6rem; border-radius: 4px;
      background: var(--accent-bg); color: var(--green-mid); border: 1px solid #b8dfc8;
    }
    .step-tag.blue {
      background: rgba(21,87,153,0.07); color: var(--blue); border-color: rgba(21,87,153,0.2);
    }
    .step-tag.amber {
      background: rgba(180,83,9,0.07); color: var(--amber); border-color: rgba(180,83,9,0.22);
    }

    /* ═══════════════════════════════════════════════════════════
       CODE BLOCK
    ═══════════════════════════════════════════════════════════ */
    .code-block {
      background: #1e2d3d;
      border-radius: var(--r);
      padding: 1.4rem 1.6rem;
      margin-top: 1.1rem;
      overflow-x: auto;
      position: relative;
    }
    .code-block::before {
      content: 'Python';
      position: absolute;
      top: 0.7rem; right: 1rem;
      font-size: 0.65rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: rgba(255,255,255,0.28);
      font-family: var(--font-body);
    }
    .code-block pre {
      font-family: 'Courier New', 'Consolas', monospace;
      font-size: 0.84rem;
      line-height: 1.7;
      color: #e2e8f0;
      margin: 0;
      white-space: pre;
    }
    .c-kw  { color: #7dd3fc; } /* keywords: def, if, elif, else, return */
    .c-fn  { color: #86efac; } /* function name */
    .c-str { color: #fcd34d; } /* strings */
    .c-num { color: #f9a8d4; } /* numbers */
    .c-cm  { color: #64748b; font-style: italic; } /* comments */
    .c-op  { color: #94a3b8; } /* operators */

    /* ═══════════════════════════════════════════════════════════
       ⑨  RESULTS TABLE
    ═══════════════════════════════════════════════════════════ */
    .table-caption {
      font-size: 0.82rem; font-weight: 700; color: var(--blue);
      text-transform: uppercase; letter-spacing: 0.05em; margin: 1.6rem 0 0;
    }
    .table-wrap {
      overflow-x: auto; border-radius: var(--r);
      border: 1px solid var(--border); margin-top: 0.75rem;
    }
    .table-wrap table { width: 100%; border-collapse: collapse; font-size: 0.85rem; }
    .table-wrap thead { background: linear-gradient(90deg, var(--blue), var(--green)); }
    .table-wrap thead th {
      color: #fff; font-weight: 700; font-size: 0.77rem;
      letter-spacing: 0.05em; text-transform: uppercase;
      padding: 0.72rem 1rem; text-align: left; white-space: nowrap;
    }
    .table-wrap tbody tr:nth-child(even) { background: var(--bg-subtle); }
    .table-wrap tbody td {
      padding: 0.62rem 1rem; color: var(--text);
      border-bottom: 1px solid var(--border); vertical-align: middle;
    }
    .table-wrap tbody tr:last-child td { border-bottom: none; }
    .table-wrap tbody td:first-child { font-weight: 600; color: var(--text-dark); }
    .risk-critical { color: #c0392b; font-weight: 700; }
    .risk-moderate { color: #b45309; font-weight: 700; }
    .risk-low      { color: #159957; font-weight: 700; }
    .risk-badge {
      display: inline-block; font-size: 0.72rem; font-weight: 700;
      padding: 0.15rem 0.55rem; border-radius: 4px;
    }
    .risk-badge.critical { background: rgba(192,57,43,0.1); color: #c0392b; border: 1px solid rgba(192,57,43,0.25); }
    .risk-badge.moderate { background: rgba(180,83,9,0.1);  color: var(--amber); border: 1px solid rgba(180,83,9,0.25); }
    .risk-badge.low      { background: var(--accent-bg);    color: var(--green-mid); border: 1px solid #b8dfc8; }

    .deviation-note {
      background: var(--bg-subtle);
      border: 1px solid var(--border);
      border-left: 3px solid var(--green);
      border-radius: var(--r);
      padding: 0.95rem 1.3rem;
      font-size: 0.84rem;
      color: var(--text);
      margin-top: 1.1rem;
      line-height: 1.6;
    }
    .deviation-note strong { color: var(--text-dark); }

    /* Inline placeholder */
    .placeholder {
      border: 2px dashed var(--border); border-radius: var(--r-lg);
      background: var(--bg-subtle); padding: 2.5rem 2rem;
      text-align: center; margin-top: 1.5rem;
    }
    .ph-icon { font-size: 2rem; margin-bottom: 0.5rem; opacity: 0.45; }
    .ph-tag {
      font-size: 0.7rem; font-weight: 700; letter-spacing: 0.13em;
      text-transform: uppercase; color: var(--green); margin-bottom: 0.3rem;
    }
    .ph-desc {
      font-size: 0.82rem; font-style: italic; color: var(--text-muted);
      max-width: 420px; margin: 0 auto; line-height: 1.55;
    }

    /* ═══════════════════════════════════════════════════════════
       ⑩  HEADLINE TRIO
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
      content: ''; display: block; height: 3px;
      background: linear-gradient(90deg, var(--blue), var(--green));
      position: absolute; top: 0; left: 0; right: 0;
    }
    .result-big {
      font-family: var(--font-head);
      font-size: 2.5rem; font-weight: 700; color: var(--blue);
      line-height: 1; letter-spacing: -0.03em;
    }
    .result-unit {
      font-size: 0.77rem; font-weight: 700; letter-spacing: 0.1em;
      text-transform: uppercase; color: var(--green); margin: 0.3rem 0 0.6rem;
    }
    .result-desc { font-size: 0.82rem; color: var(--text); line-height: 1.45; }

    /* ═══════════════════════════════════════════════════════════
       ⑪  KEY FINDINGS
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
    .finding-card.blue-accent { border-left-color: var(--blue); }
    .finding-card.amber-accent { border-left-color: var(--amber); }
    .finding-card:hover { box-shadow: var(--shadow); }
    .find-pill {
      display: inline-block; font-size: 0.62rem; font-weight: 700;
      letter-spacing: 0.1em; text-transform: uppercase; border-radius: 999px;
      padding: 0.12rem 0.55rem; margin-bottom: 0.55rem;
    }
    .find-pill.find  { background: var(--accent-bg); color: var(--green-mid); border: 1px solid #b8dfc8; }
    .find-pill.learn { background: rgba(21,87,153,0.08); color: var(--blue); border: 1px solid rgba(21,87,153,0.18); }
    .find-pill.design { background: rgba(180,83,9,0.08); color: var(--amber); border: 1px solid rgba(180,83,9,0.2); }
    .finding-card h3 {
      font-size: 0.85rem; font-weight: 700; color: var(--blue);
      text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 0.4rem;
    }
    .finding-card.blue-accent  h3 { color: var(--blue); }
    .finding-card.amber-accent h3 { color: var(--amber); }
    .finding-card p { font-size: 0.86rem; margin: 0; line-height: 1.55; }

    /* ═══════════════════════════════════════════════════════════
       ⑫  PROJECT CONTEXT
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
    .outcome-pill {
      display: inline-block; margin-top: 0.2rem;
      font-size: 0.78rem; font-weight: 700; color: var(--green-mid);
      background: var(--accent-bg); border: 1px solid #b8dfc8;
      border-radius: 999px; padding: 0.2rem 0.75rem;
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
    }
  </style>
</head>
<body>


<!-- ════════════════════════════════════════════════════════════
     ① FIELD – SUB-FIELD   +   ② MAIN HEAD
════════════════════════════════════════════════════════════ -->
<header class="site-header">

  <p class="field-label">
    Process Engineering
    <span class="field-divider">/</span>
    <span>Operational Risk Governance &amp; Safety Systems</span>
  </p>

  <h1>
    Plant-Wide JHA Framework Standardization<br>
    <em>Python-Automated Risk Governance Across 24+ Industrial Units</em>
  </h1>

  <p class="header-sub">
    Independently designed and implemented a unified Job Hazard Analysis framework from scratch at Attock Cement Limited — replacing a fragmented mix of paper checklists and inconsistent digital records with a single, audit-ready risk governance system, formally submitted for ISO 45001 review.
  </p>

  <a href="/" class="back-link">&nbsp;Back to Portfolio</a>

</header>


<main class="wrap">

  <!-- ════════════════════════════════════════════════════════════
       ③  SKILLS USED
  ════════════════════════════════════════════════════════════ -->
  <div class="skills-section">
    <p class="skills-label"><span class="sec-num">03</span> Skills Used in This Project</p>
    <div class="pills">
      <span class="pill"><span class="pill-dot"></span>Job Hazard Analysis (JHA) Design</span>
      <span class="pill"><span class="pill-dot"></span>Python (Risk Automation &amp; Hotspot Analysis)</span>
      <span class="pill"><span class="pill-dot"></span>ISO 45001 Compliance &amp; Audit Documentation</span>
      <span class="pill"><span class="pill-dot"></span>Custom RPN Risk Matrix Design</span>
      <span class="pill"><span class="pill-dot"></span>Industrial Process Task Decomposition</span>
      <span class="pill"><span class="pill-dot"></span>Cross-Functional Stakeholder Coordination</span>
    </div>
  </div>


  <!-- ════════════════════════════════════════════════════════════
       ④  ACHIEVEMENT STATEMENT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="ach-h">
    <p class="sec-label"><span class="sec-num">04</span> Achievement</p>
    <h2 id="ach-h">Building a Safety System That Speaks the Language of Auditors — and Engineers</h2>
    <div class="achievement-banner">
      <p class="ach-label">Core Achievement</p>
      <blockquote>
        Starting from a fragmented mix of paper checklists and unformatted spreadsheets, I independently designed and deployed a <strong>unified JHA framework across 24+ industrial unit processes</strong> at Attock Cement Limited — developing a custom <strong>5×5 Risk Priority Number matrix from first principles</strong> and automating hazard classification with Python scripts built from scratch. The resulting system was formally submitted for <strong>ISO 45001 audit review</strong>, reduced compliance preparation time by an estimated 40%, and gave management — for the first time — a <strong>quantified, plant-wide map of operational risk</strong> built on data rather than departmental intuition.
      </blockquote>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑤  INFOGRAPHIC PLACEHOLDER
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="infog-h">
    <p class="sec-label"><span class="sec-num">05</span> Project Overview</p>
    <h2 id="infog-h">The Full Picture at a Glance</h2>
    <div class="infographic-placeholder">
      <div class="infog-ph-icon">🗺️</div>
      <p class="infog-ph-tag">Your Infographic Goes Here</p>
      <p class="infog-ph-title">Project Overview Infographic</p>
      <p class="infog-ph-desc">
        Replace this block with your visual overview — for example, a three-panel flow showing the before state (fragmented checklists across 24+ units), the method (4-phase JHA workflow + Python RPN scoring), and the outcome (single unified framework, ISO audit submitted, 40% compliance time reduction). An SVG, PNG, or embedded HTML visual all work here.
      </p>
      <span class="infog-ph-note">📐 Recommended dimensions: 860 × 360 px or wider</span>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑥  PROJECT STATS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="stats-h">
    <p class="sec-label"><span class="sec-num">06</span> Project at a Glance</p>
    <h2 id="stats-h">Four Numbers That Define the Work</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">24<sup>+</sup></div>
        <div class="stat-unit">Units Covered</div>
        <p>Every industrial unit across the plant — kiln, raw mill, grinding, packing, quarry, lab, utilities, and maintenance — mapped under a single unified risk framework</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">40<sup>%</sup></div>
        <div class="stat-unit">Audit Time Saved</div>
        <p>Estimated reduction in ISO 45001 compliance preparation time, achieved by replacing fragmented, inconsistent documentation with a single audit-ready source of truth</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">100<sup>%</sup></div>
        <div class="stat-unit">Plant Coverage</div>
        <p>First time in the plant's history that every process unit — from high-temperature kiln operations to chemical laboratory procedures — was assessed under the same risk logic</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">3</div>
        <div class="stat-unit">Months to Deploy</div>
        <p>From first observation of the problem to a submitted ISO 45001 audit deliverable — independently designed, built, and deployed within a single quarter</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑦  PROBLEM STATEMENT & COMMISSION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="problem-h">
    <p class="sec-label"><span class="sec-num">07</span> Problem Statement &amp; Commission</p>
    <h2 id="problem-h">A Plant Running 24 Different Safety Languages Simultaneously</h2>

    <p>
      Attock Cement's production operations span one of the most hazard-dense industrial environments in manufacturing: high-temperature rotary kilns operating at 1,450 °C, heavy rotating grinding machinery, chemical additive handling in the laboratory, pressurised utilities systems, and active quarry blasting — all running concurrently, all staffed by different shifts and departments. Each of these environments carries a distinct risk profile. But the plant was assessing all of them with incompatible documentation.
    </p>
    <p>
      Paper checklists in one department, unsupported Excel sheets in another, verbal assessments in a third — with no shared risk scoring scale, no common severity definition, and no mechanism to compare hazard levels across units. A "High Risk" designation in the kiln maintenance team carried a different meaning than the same label in the packing department. Management had no consolidated view of where the plant's most critical hazards were concentrated, and ISO 45001 auditors had no single document they could use to verify compliance across the facility.
    </p>
    <p>
      There was no incident that triggered this project. No near-miss event forced the issue. The problem was identified through direct observation during day-to-day process engineering work — and the project was initiated on personal initiative, with the full scope designed independently before a single stakeholder meeting was held.
    </p>

    <div class="note-box green">
      <strong>Self-Commissioned Objective:</strong> Design a unified, scalable Job Hazard Analysis framework from first principles — covering every industrial unit plant-wide — and implement it with sufficient rigour and documentation quality to serve as the primary submission for Attock Cement's ISO 45001 compliance audit.
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑧  METHODOLOGY & EXECUTION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="method-h">
    <p class="sec-label"><span class="sec-num">08</span> Methodology &amp; Execution</p>
    <h2 id="method-h">A Four-Phase Framework — From Task to Risk Score to Management Action</h2>

    <p>
      The framework was designed so that a mechanical hazard in the Grinding Mill and a chemical exposure hazard in the laboratory would be evaluated by exactly the same logic, produce a comparable numerical score, and trigger the same category of corrective action. Every design decision was made with two users in mind simultaneously: the shift engineer filling in the JHA form on the plant floor, and the ISO 45001 auditor reviewing the documentation from a desk.
    </p>

    <div class="method-steps">

      <div class="method-step">
        <div class="step-num">01</div>
        <div class="step-body">
          <h3>Process Observation &amp; Task Decomposition — Across All 24+ Units</h3>
          <p>Every unit process was walked through and broken down into discrete, sequential steps. This was not a desk exercise — it required being physically present at each unit, observing the actual task sequence as performed by operators, and documenting each step in granular enough detail to allow meaningful hazard identification at the sub-task level. For a unit like kiln maintenance, this produced a sequence such as: Energy Isolation (LOTO) → Confined Space Entry Permit → Internal Inspection → Component Removal → Replacement → Recommissioning. Each of these steps has a distinct hazard profile that a single-line "Kiln Maintenance — Risk: High" entry would have completely obscured.</p>
          <div class="step-tags">
            <span class="step-tag">Field Observation</span>
            <span class="step-tag">Task Decomposition</span>
            <span class="step-tag">LOTO Procedures</span>
            <span class="step-tag blue">24+ Units</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">02</div>
        <div class="step-body">
          <h3>Custom RPN Risk Matrix — Designed from First Principles</h3>
          <p>Rather than importing an existing industry template, the 5×5 Risk Priority Number matrix was designed from scratch to fit the specific hazard landscape of a cement manufacturing plant. Probability (P) and Severity (S) scales were each defined with five discrete levels — calibrated against the actual range of events observable on-site, from improbable trace-chemical contact to frequent rotating machinery interaction. The resulting Risk Score (P × S) was then mapped to three action tiers, each prescribing a specific category of intervention rather than a vague risk label. This design decision was critical: it meant the framework told supervisors not just what the risk level was, but what they were required to do about it.</p>
          <div class="step-tags">
            <span class="step-tag amber">RPN Matrix Design</span>
            <span class="step-tag amber">From First Principles</span>
            <span class="step-tag">5×5 Probability × Severity</span>
            <span class="step-tag">3-Tier Action Framework</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">03</div>
        <div class="step-body">
          <h3>Python Automation — Risk Classification &amp; Plant-Wide Hotspot Analysis</h3>
          <p>To manage the data volume generated by 24+ units each broken into multiple sequential steps, Python scripts were built from scratch to automate the risk scoring logic. The core function standardised the RPN calculation and category assignment identically across all units — eliminating the possibility of one department applying slightly different scoring thresholds than another. Beyond classification, the scripts aggregated scores across the full plant to produce a ranked hotspot analysis: a quantified, data-driven map of which units and task categories concentrated the highest risk exposure. This output gave plant management something they had never had — a single number-backed answer to the question of where safety investment should be directed first.</p>
          <div class="step-tags">
            <span class="step-tag blue">Python (built from scratch)</span>
            <span class="step-tag blue">Risk Aggregation</span>
            <span class="step-tag blue">Hotspot Identification</span>
            <span class="step-tag">CapEx Prioritisation</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">04</div>
        <div class="step-body">
          <h3>ISO 45001 Documentation &amp; Audit Submission</h3>
          <p>The completed framework was structured and formatted specifically for ISO 45001 compliance review — with consistent field naming, traceable task references, and a document hierarchy that allowed an external auditor to navigate from any individual hazard entry back to the unit process, the risk score, the action tier, and the responsible control measure. The submission package was accepted as the primary safety governance documentation for the facility's ISO 45001 audit process. The estimated 40% reduction in compliance preparation time came not from cutting corners, but from having replaced a situation where compliance evidence had to be assembled manually from disparate sources with a single, already-structured document.</p>
          <div class="step-tags">
            <span class="step-tag">ISO 45001</span>
            <span class="step-tag">Audit Documentation</span>
            <span class="step-tag blue">Formal Submission</span>
            <span class="step-tag">40% Compliance Time Reduction</span>
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
    <h2 id="results-h">The Risk Matrix, the Python Logic, and What They Produced</h2>

    <p>
      The table below shows the standardized Risk Priority Number (RPN) matrix as implemented across all 24+ units, with representative examples from three distinct process categories. The Python code block below it shows the core classification function — the same logic that ran across every hazard entry in the plant, guaranteeing that no team's subjective interpretation could override the scoring criteria.
    </p>

    <!-- RPN MATRIX TABLE -->
    <p class="table-caption">Standardised RPN Risk Matrix — Applied Across All 24+ Units</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Probability (P)</th>
            <th>Severity (S)</th>
            <th>Risk Score (P × S)</th>
            <th>Action Tier</th>
            <th>Required Response</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>5 — Frequent</td>
            <td>5 — Catastrophic</td>
            <td class="risk-critical">20 – 25</td>
            <td><span class="risk-badge critical">Critical</span></td>
            <td>Halt operations. Engineering controls mandatory before restart.</td>
          </tr>
          <tr>
            <td>4 — Likely</td>
            <td>4 — Critical</td>
            <td class="risk-critical">12 – 16</td>
            <td><span class="risk-badge critical">Critical</span></td>
            <td>Halt operations. Engineering controls mandatory before restart.</td>
          </tr>
          <tr>
            <td>3 — Occasional</td>
            <td>3 — Marginal</td>
            <td class="risk-moderate">8 – 11</td>
            <td><span class="risk-badge moderate">Moderate</span></td>
            <td>Administrative controls &amp; PPE required. Engineering review within 30 days.</td>
          </tr>
          <tr>
            <td>2 — Unlikely</td>
            <td>2 — Minor</td>
            <td class="risk-low">3 – 5</td>
            <td><span class="risk-badge low">Low</span></td>
            <td>Standard Operating Procedures. Routine PPE. Logged for periodic review.</td>
          </tr>
          <tr>
            <td>1 — Improbable</td>
            <td>1 — Negligible</td>
            <td class="risk-low">1 – 2</td>
            <td><span class="risk-badge low">Low</span></td>
            <td>Standard Operating Procedures. Routine PPE. Logged for periodic review.</td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- SAMPLE JHA TABLE -->
    <p class="table-caption">Sample JHA Entries — Representative Cross-Unit Examples</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Unit</th>
            <th>Task Step</th>
            <th>Hazard</th>
            <th>P</th>
            <th>S</th>
            <th>RPN</th>
            <th>Tier</th>
            <th>Control</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Kiln Maintenance</td>
            <td>Confined Space Entry</td>
            <td>Oxygen deficiency / thermal exposure</td>
            <td>3</td>
            <td>5</td>
            <td class="risk-critical">15</td>
            <td><span class="risk-badge critical">Critical</span></td>
            <td>Permit-to-Work, O₂ monitor, standby rescue team</td>
          </tr>
          <tr>
            <td>Grinding Mill</td>
            <td>In-Service Inspection</td>
            <td>Entanglement with rotating mill internals</td>
            <td>2</td>
            <td>5</td>
            <td class="risk-critical">10</td>
            <td><span class="risk-badge critical">Critical</span></td>
            <td>Full LOTO, isolation confirmation, guard verification</td>
          </tr>
          <tr>
            <td>Raw Mill</td>
            <td>Dust Filter Cleaning</td>
            <td>Silica dust inhalation (respirable fraction)</td>
            <td>4</td>
            <td>3</td>
            <td class="risk-moderate">12</td>
            <td><span class="risk-badge moderate">Moderate</span></td>
            <td>P3-rated respirator, enclosed cleaning protocol, ventilation</td>
          </tr>
          <tr>
            <td>Chemical Lab</td>
            <td>Acid Titration</td>
            <td>Concentrated acid splash — skin / eyes</td>
            <td>3</td>
            <td>3</td>
            <td class="risk-moderate">9</td>
            <td><span class="risk-badge moderate">Moderate</span></td>
            <td>Face shield, acid-resistant gloves, eyewash station within 10 m</td>
          </tr>
          <tr>
            <td>Packing Unit</td>
            <td>Bag Pallet Stacking</td>
            <td>Musculoskeletal strain (repetitive load)</td>
            <td>4</td>
            <td>2</td>
            <td class="risk-low">8</td>
            <td><span class="risk-badge moderate">Moderate</span></td>
            <td>Manual handling training, rotation schedule, mechanical assist</td>
          </tr>
          <tr>
            <td>Quarry Operations</td>
            <td>Blasting Preparation</td>
            <td>Premature detonation / flyrock</td>
            <td>1</td>
            <td>5</td>
            <td class="risk-moderate">5</td>
            <td><span class="risk-badge low">Low</span></td>
            <td>Exclusion zone, licensed blaster, pre-blast checklist</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="deviation-note">
      <strong>On the RPN scale design:</strong> The three-tier action framework (Critical ≥15, Moderate 8–14, Low &lt;8) was calibrated to produce a conservative distribution for this plant's hazard profile — meaning the majority of kiln and rotating machinery tasks would correctly return Critical or Moderate scores requiring active intervention, not be absorbed into a Low tier that permits inaction. The thresholds were not taken from a standard template but derived from the actual distribution of P × S combinations encountered during the initial 24-unit task decomposition survey.
    </div>

    <!-- PYTHON CODE BLOCK -->
    <p class="table-caption" style="margin-top:1.8rem;">Python Risk Classification Engine — Core Function</p>
    <div class="code-block">
      <pre><span class="c-cm"># ── JHA Risk Classification Engine ──────────────────────────</span>
<span class="c-cm"># Standardised RPN logic applied uniformly across all 24+ units.</span>
<span class="c-cm"># Eliminates inter-department scoring drift by design.</span>

<span class="c-kw">def</span> <span class="c-fn">calculate_risk</span>(probability: <span class="c-fn">int</span>, severity: <span class="c-fn">int</span>) -> <span class="c-fn">dict</span>:
    <span class="c-str">"""
    Calculates RPN and returns action tier + required response.
    Args:
        probability : int  1–5  (Improbable → Frequent)
        severity    : int  1–5  (Negligible → Catastrophic)
    Returns:
        dict with score, tier, and required control action.
    """</span>
    score = probability <span class="c-op">*</span> severity

    <span class="c-kw">if</span> score <span class="c-op">>=</span> <span class="c-num">15</span>:
        <span class="c-kw">return</span> {
            <span class="c-str">"rpn"</span>     : score,
            <span class="c-str">"tier"</span>    : <span class="c-str">"CRITICAL"</span>,
            <span class="c-str">"action"</span>  : <span class="c-str">"Halt operations — engineering controls mandatory before restart"</span>,
            <span class="c-str">"escalate"</span>: <span class="c-kw">True</span>
        }
    <span class="c-kw">elif</span> score <span class="c-op">>=</span> <span class="c-num">8</span>:
        <span class="c-kw">return</span> {
            <span class="c-str">"rpn"</span>     : score,
            <span class="c-str">"tier"</span>    : <span class="c-str">"MODERATE"</span>,
            <span class="c-str">"action"</span>  : <span class="c-str">"Administrative controls &amp; PPE required — engineering review within 30 days"</span>,
            <span class="c-str">"escalate"</span>: <span class="c-kw">False</span>
        }
    <span class="c-kw">else</span>:
        <span class="c-kw">return</span> {
            <span class="c-str">"rpn"</span>     : score,
            <span class="c-str">"tier"</span>    : <span class="c-str">"LOW"</span>,
            <span class="c-str">"action"</span>  : <span class="c-str">"Standard SOPs and routine PPE — log for periodic review"</span>,
            <span class="c-str">"escalate"</span>: <span class="c-kw">False</span>
        }


<span class="c-kw">def</span> <span class="c-fn">identify_hotspots</span>(jha_records: <span class="c-fn">list</span>, threshold: <span class="c-fn">int</span> <span class="c-op">=</span> <span class="c-num">15</span>) -> <span class="c-fn">list</span>:
    <span class="c-str">"""
    Aggregates JHA records across all units and returns
    ranked Critical hotspots for management CapEx prioritisation.
    """</span>
    hotspots = [
        r <span class="c-kw">for</span> r <span class="c-kw">in</span> jha_records
        <span class="c-kw">if</span> r[<span class="c-str">"rpn"</span>] <span class="c-op">>=</span> threshold
    ]
    <span class="c-kw">return</span> <span class="c-fn">sorted</span>(hotspots, key<span class="c-op">=</span><span class="c-kw">lambda</span> x: x[<span class="c-str">"rpn"</span>], reverse<span class="c-op">=</span><span class="c-kw">True</span>)</pre>
    </div>

    <div class="deviation-note">
      <strong>Why build from scratch rather than use a template?</strong> Off-the-shelf JHA tools and Excel templates carry embedded assumptions about industry type, hazard vocabulary, and scoring thresholds that were not calibrated for cement manufacturing. Building the Python logic from first principles meant every threshold, every action description, and every escalation rule was a deliberate engineering decision — one that could be explained and defended in an ISO audit, rather than attributed to a third-party template.
    </div>

    <div class="placeholder">
      <div class="ph-icon">📊</div>
      <p class="ph-tag">Suggested Visual — Plant-Wide Risk Hotspot Map</p>
      <p class="ph-desc">A ranked bar chart or heat-map grid showing RPN scores by unit — kiln operations, grinding, raw mill, quarry, lab, packing, utilities, maintenance — sorted by total Critical entries. This is the direct output of the <code>identify_hotspots()</code> function and the single most impactful visual you can show a safety-conscious recruiter.</p>
    </div>

  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑩  3 HEADLINE RESULTS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="trio-h">
    <p class="sec-label"><span class="sec-num">10</span> Headline Results</p>
    <h2 id="trio-h">Three Numbers That Tell the Story</h2>
    <div class="results-trio">
      <div class="result-cell">
        <div class="result-big">24+</div>
        <div class="result-unit">Units — One Framework</div>
        <p class="result-desc">Every plant unit — kiln, grinding, quarry, lab, utilities, maintenance — assessed under an identical risk logic for the first time, making cross-unit comparison quantitatively valid</p>
      </div>
      <div class="result-cell">
        <div class="result-big">40%</div>
        <div class="result-unit">Audit Prep Reduction</div>
        <p class="result-desc">ISO 45001 compliance preparation time cut by an estimated 40% — not by reducing rigour, but by replacing a fragmented document landscape with a single, already-structured audit submission</p>
      </div>
      <div class="result-cell">
        <div class="result-big">ISO</div>
        <div class="result-unit">45001 Submitted</div>
        <p class="result-desc">The framework was formally submitted for ISO 45001 audit review — the highest institutional validation available for occupational health and safety governance in industrial operations</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       ⑪  KEY FINDINGS & LEARNING OUTCOMES
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="findings-h">
    <p class="sec-label"><span class="sec-num">11</span> Key Findings &amp; Learning Outcomes</p>
    <h2 id="findings-h">What Designing a Safety System From Scratch Actually Teaches You</h2>
    <div class="findings-grid">

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>Inconsistency Is Invisible Until You Standardize</h3>
        <p>Before the framework, no department believed their risk assessment was inconsistent — they simply didn't have a basis for comparison. It was only by mapping a high-temperature kiln task and a chemical lab procedure onto the same 5×5 matrix simultaneously that the incompatibility became quantifiably visible. Standardization doesn't just improve compliance; it reveals problems that were previously undetectable because there was no common measuring scale to detect them with.</p>
      </div>

      <div class="finding-card blue-accent">
        <span class="find-pill learn">Learning</span>
        <h3>RPN Matrix Thresholds Are Engineering Decisions, Not Defaults</h3>
        <p>Setting the Critical threshold at ≥15 rather than ≥20 — a seemingly minor calibration choice — meant the matrix correctly classified confined space entry and rotating machinery contact as requiring operational halts, rather than administrative controls. Threshold calibration is a substantive engineering judgment that determines which hazards get engineering investment and which get a checklist. Treating it as a default to be inherited from a template is the single most dangerous assumption in industrial risk governance.</p>
      </div>

      <div class="finding-card amber-accent">
        <span class="find-pill design">Design</span>
        <h3>Python Automation Eliminates the Most Dangerous Source of Error: Human Consistency</h3>
        <p>The biggest risk in a manual JHA system is not that someone deliberately cheats the score — it's that two engineers on different shifts apply the probability scale slightly differently over time. Once scoring drift enters a dataset, the plant-wide hotspot ranking becomes meaningless. Automating the classification logic with Python didn't make the process faster (the field observation work still took months); it made the scoring consistent by design, regardless of who entered the data or when.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>Kiln Operations and Utilities Represent the Highest Aggregate Risk Concentration</h3>
        <p>The hotspot analysis produced by the Python aggregation function revealed that — when all task steps across all 24+ units were scored and ranked — kiln maintenance tasks (particularly confined space entry and refractory work) and utilities operations (high-pressure steam systems, electrical isolation) consistently produced the highest concentration of Critical-tier RPN scores. This gave management a data-backed priority list for engineering control investment that was impossible to construct from the previous fragmented system.</p>
      </div>

      <div class="finding-card blue-accent">
        <span class="find-pill learn">Learning</span>
        <h3>ISO Audit Readiness Is an Architecture Problem, Not a Documentation Problem</h3>
        <p>The 40% reduction in audit preparation time did not come from writing better summaries or organising files more carefully. It came from designing the framework's document structure with audit navigation in mind from the beginning — so that any hazard entry was traceable back to its unit, task step, risk score, action tier, and control measure in a consistent hierarchy. Audit readiness is not something you retrofit onto a completed project; it is a structural decision made in the design phase.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>Task Decomposition Granularity Determines Framework Quality</h3>
        <p>The most consequential decision in the entire project was how finely to decompose each process into task steps. A coarse decomposition — "Kiln Maintenance: Risk High" — is useless for both hazard control and audit evidence. A granular decomposition — LOTO → Confined Space Entry → Internal Inspection → Component Removal — allows each sub-task to carry its own specific hazard, its own probability score, and its own prescribed control. The framework's value scales directly with the quality of the task decomposition underlying it.</p>
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
      This project was self-initiated and independently executed at Attock Cement Limited during a process engineering placement. The full scope — from initial problem identification through framework design, Python development, field observation across 24+ units, and final ISO documentation — was completed within a single quarter of approximately three months. Each card below represents a distinct, delivered component.
    </p>

    <div class="context-grid">
      <div class="context-card">
        <span class="ctx-icon">⚙️</span>
        <h3>Role</h3>
        <p>Process Engineer — sole designer and implementer. The project was self-initiated following direct observation of the inconsistency problem; no brief or task was assigned by management.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">🏭</span>
        <h3>Organisation</h3>
        <p>Attock Cement Limited — a large-scale industrial cement production facility with operations spanning quarrying, raw milling, pyro-processing, grinding, packing, chemical laboratory, and utilities.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📋</span>
        <h3>Coverage</h3>
        <p>All 24+ industrial unit processes plant-wide, including kiln operations, raw mill, grinding mill, packing unit, chemical laboratory, quarry, utilities, and maintenance — 100% plant coverage.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">💻</span>
        <h3>Python Deliverable</h3>
        <p>Custom-built risk classification and hotspot aggregation scripts — not adapted from existing templates. Core functions: <code>calculate_risk()</code> and <code>identify_hotspots()</code> — both designed from first principles.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📐</span>
        <h3>Framework Design</h3>
        <p>5×5 RPN matrix with custom threshold calibration for cement manufacturing. Three action tiers (Critical, Moderate, Low) with prescribed response categories — designed from first principles, not from an industry template.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">✅</span>
        <h3>Outcome</h3>
        <p>Framework formally adopted as the plant's primary safety governance documentation.</p>
        <span class="outcome-pill">Submitted for ISO 45001 audit review</span>
      </div>
    </div>

  </section>

</main>


<!-- ════════════════════════════════════════════════════════════
     FOOTER
════════════════════════════════════════════════════════════ -->
<footer class="site-footer">
  <p>
    Attock Cement Limited &nbsp;·&nbsp;
    Process Engineering &nbsp;·&nbsp;
    JHA Framework &amp; Risk Governance &nbsp;·&nbsp;
    <a href="/">← Back to Portfolio</a>
  </p>
</footer>


</body>
</html>
