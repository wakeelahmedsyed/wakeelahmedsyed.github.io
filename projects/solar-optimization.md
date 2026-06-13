<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Energy-Efficient Resource Scheduling &amp; Predictive Modelling | Sustainability Operations</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Merriweather:wght@300;400;700&amp;family=Source+Sans+3:ital,wght@0,300;0,400;0,600;0,700;1,400&amp;display=swap" rel="stylesheet" />

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
       HEADER
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
       SKILLS
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
       ACHIEVEMENT BANNER
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
       INFOGRAPHIC PLACEHOLDER
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
       PROJECT STATS
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
       PROBLEM — note boxes
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
       METHODOLOGY — bordered step list
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
    .c-kw  { color: #7dd3fc; } /* keywords */
    .c-fn  { color: #86efac; } /* function name */
    .c-str { color: #fcd34d; } /* strings */
    .c-num { color: #f9a8d4; } /* numbers */
    .c-cm  { color: #64748b; font-style: italic; } /* comments */
    .c-op  { color: #94a3b8; } /* operators */

    /* ═══════════════════════════════════════════════════════════
       RESULTS TABLE
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
       HEADLINE TRIO
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
       KEY FINDINGS
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
       PROJECT CONTEXT
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
     FIELD – SUB-FIELD   +   MAIN HEAD
════════════════════════════════════════════════════════════ -->
<header class="site-header">

  <p class="field-label">
    Sustainability &amp; Energy Operations
    <span class="field-divider">/</span>
    <span>Predictive Load Optimization &amp; Statistical Analysis</span>
  </p>

  <h1>
    Energy-Efficient Resource Scheduling &amp; Predictive Modelling<br />
    <em>Statistically-Driven Load Optimization for a 21 MW Solar Power Plant</em>
  </h1>

  <p class="header-sub">
    Engineered a proactive energy-utilization model for a 21 MW solar plant by applying Time Series Analysis and Hypothesis Testing to 15-minute generation intervals — transitioning the facility from reactive to predictive equipment scheduling and securing 6.25M PKR in combined operational savings.
  </p>

  <a href="/" class="back-link">&nbsp;Back to Portfolio</a>

</header>


<main class="wrap">

  <!-- ════════════════════════════════════════════════════════════
       SKILLS USED
  ════════════════════════════════════════════════════════════ -->
  <div class="skills-section">
    <p class="skills-label"><span class="sec-num">03</span> Skills Used in This Project</p>
    <div class="pills">
      <span class="pill"><span class="pill-dot"></span>Time Series Analysis (TSA)</span>
      <span class="pill"><span class="pill-dot"></span>Hypothesis Testing (Z-Tests / T-Tests)</span>
      <span class="pill"><span class="pill-dot"></span>Predictive Load Modelling</span>
      <span class="pill"><span class="pill-dot"></span>Variance &amp; Gap Analysis</span>
      <span class="pill"><span class="pill-dot"></span>Photovoltaic (PV) Systems &amp; Grid Integration</span>
      <span class="pill"><span class="pill-dot"></span>Senior Leadership Business Case Presentation</span>
    </div>
  </div>


  <!-- ════════════════════════════════════════════════════════════
       ACHIEVEMENT STATEMENT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="ach-h">
    <p class="sec-label"><span class="sec-num">04</span> Achievement</p>
    <h2 id="ach-h">Turning 15-Minute Generation Data Into a 6.25M PKR Operational Decision</h2>
    <div class="achievement-banner">
      <p class="ach-label">Core Achievement</p>
      <blockquote>
        Engineered an <strong>energy-utilization model for a 21 MW solar power plant</strong> by applying <strong>Time Series Analysis and Hypothesis Testing</strong> to 15-minute generation intervals — transitioning the facility from <strong>reactive to predictive equipment startup</strong> and securing <strong>4M PKR</strong> in operational savings. Further identified a <strong>2.25M PKR efficiency gap</strong> through variance analysis of product supply-vs-demand forecasting, and presented the resulting business case directly to senior leadership for operational restructuring.
      </blockquote>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       INFOGRAPHIC PLACEHOLDER
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="infog-h">
    <p class="sec-label"><span class="sec-num">05</span> Project Overview</p>
    <h2 id="infog-h">The Full Picture at a Glance</h2>
    <div class="infographic-placeholder">
      <div class="infog-ph-icon">☀️</div>
      <p class="infog-ph-tag">Your Infographic Goes Here</p>
      <p class="infog-ph-title">Project Overview Infographic</p>
      <p class="infog-ph-desc">
        Replace this block with your visual overview — for example, a three-panel flow showing the before state (reactive startup, unstructured 15-minute generation data), the method (TSA + Hypothesis Testing pipeline feeding a predictive load model), and the outcome (4M PKR predictive savings + 2.25M PKR gap recovery, leadership business case). An SVG, PNG, or embedded HTML visual all work here.
      </p>
      <span class="infog-ph-note">📐 Recommended dimensions: 860 × 360 px or wider</span>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       PROJECT STATS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="stats-h">
    <p class="sec-label"><span class="sec-num">06</span> Project at a Glance</p>
    <h2 id="stats-h">Four Numbers That Define the Work</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">21</div>
        <div class="stat-unit">MW Solar Plant</div>
        <p>Total capacity of the renewable energy facility for which the predictive energy-utilization model was engineered, covering the full generation footprint</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">4M</div>
        <div class="stat-unit">PKR Predictive Savings</div>
        <p>Operational cost reduction secured by transitioning equipment startup from a reactive schedule to a predictive model validated through hypothesis testing</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">2.25M</div>
        <div class="stat-unit">PKR Gap Recovered</div>
        <p>Additional efficiency gap identified through variance analysis of supply-vs-demand forecasting and presented as a leadership business case</p>
      </div>
      <div class="stat-card">
        <div class="stat-num">15<sup>min</sup></div>
        <div class="stat-unit">Interval Resolution</div>
        <p>Generation data was analysed at 15-minute resolution — fine enough to detect statistically significant variance windows that triggered scheduling decisions</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       PROBLEM STATEMENT & COMMISSION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="problem-h">
    <p class="sec-label"><span class="sec-num">07</span> Problem Statement &amp; Commission</p>
    <h2 id="problem-h">A 21 MW Asset Running on Reactive Scheduling</h2>

    <p>
      A 21 MW solar power plant generates a highly variable output profile driven by irradiance and temperature conditions that change throughout the day and across seasons. Despite this, equipment startup and shutdown decisions — and the broader operational shift schedule — were being made reactively, based on observed conditions in the moment rather than on any statistically grounded forecast of upcoming generation.
    </p>
    <p>
      This reactive approach meant equipment was frequently brought online later than optimal, or kept running during low-generation windows where the marginal cost of grid power exceeded the value of the additional output. At the same time, no one had systematically compared the plant's actual supply profile against operational demand to identify where the two were misaligned — leaving a quantifiable efficiency gap unexamined.
    </p>
    <p>
      The opportunity was identified through close engagement with the plant's generation data: 15-minute interval readings were already being logged, but no statistical framework existed to determine which fluctuations in that data were significant enough to warrant a change in operational behaviour, versus which were simply noise.
    </p>

    <div class="note-box green">
      <strong>Objective:</strong> Build a statistically validated predictive model — using Time Series Analysis and Hypothesis Testing on 15-minute generation intervals — that converts raw solar generation data into actionable equipment startup decisions and a quantified supply-vs-demand efficiency case for leadership.
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       METHODOLOGY & EXECUTION
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="method-h">
    <p class="sec-label"><span class="sec-num">08</span> Methodology &amp; Execution</p>
    <h2 id="method-h">From Raw Interval Data to a Predictive Startup Model and a Leadership Business Case</h2>

    <p>
      The methodology was designed around a simple principle: every operational decision — when to start equipment, when to shift load, when to restructure shifts — should be backed by a statistical test of whether the underlying generation pattern justified it, not by intuition or fixed schedules inherited from non-solar operations.
    </p>

    <div class="method-steps">

      <div class="method-step">
        <div class="step-num">01</div>
        <div class="step-body">
          <h3>15-Minute Interval Data Collection &amp; Time Series Structuring</h3>
          <p>Generation data from the 21 MW plant was structured into a continuous time series at 15-minute resolution — the same granularity at which the plant's monitoring systems already logged irradiance-driven output. This resolution was chosen because it was fine enough to capture meaningful intraday ramp patterns (morning ramp-up, midday peak, evening decline) while remaining coarse enough to filter out instrument-level noise that would otherwise obscure genuine operational signals.</p>
          <div class="step-tags">
            <span class="step-tag">Time Series Analysis</span>
            <span class="step-tag">15-Minute Resolution</span>
            <span class="step-tag blue">21 MW Generation Data</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">02</div>
        <div class="step-body">
          <h3>Hypothesis Testing to Validate Operational Triggers</h3>
          <p>Rather than reacting to every fluctuation in the generation series, Z-tests and T-tests were applied to determine whether the variance observed in a given interval was statistically significant relative to the expected baseline — or simply within normal stochastic range. Only intervals where the test indicated a genuine, statistically supported shift in generation conditions were flagged as candidates for a change in equipment startup or load-shedding protocol. This distinction — statistically significant versus noise — was the core mechanism that converted raw data into a defensible operational trigger.</p>
          <div class="step-tags">
            <span class="step-tag amber">Z-Tests / T-Tests</span>
            <span class="step-tag amber">Statistical Significance Thresholds</span>
            <span class="step-tag">Predictive Startup Protocol</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">03</div>
        <div class="step-body">
          <h3>Predictive Load Modelling — From Reactive to Proactive Scheduling</h3>
          <p>The validated time series patterns were used to build a predictive load model: a forward-looking view of expected generation that allowed equipment startup decisions to be made ahead of the generation event rather than in response to it. This shift — from reactive (waiting to observe conditions, then acting) to predictive (anticipating conditions based on a statistically validated pattern, then acting in advance) — was the central operational change that produced the 4M PKR savings figure, by reducing the number of startup cycles that occurred later than optimal or under suboptimal grid-power conditions.</p>
          <div class="step-tags">
            <span class="step-tag blue">Predictive Load Modelling</span>
            <span class="step-tag blue">Reactive → Predictive Transition</span>
            <span class="step-tag">4M PKR Savings</span>
          </div>
        </div>
      </div>

      <div class="method-step">
        <div class="step-num">04</div>
        <div class="step-body">
          <h3>Supply-vs-Demand Variance Analysis &amp; Leadership Business Case</h3>
          <p>In parallel, a separate variance analysis compared the plant's actual generation supply profile against operational demand — specifically, when shift schedules and equipment loads were drawing power relative to when the plant was generating it for free from solar. This analysis surfaced a 2.25M PKR efficiency gap: periods where demand was being met from grid power during windows of high solar availability, or where solar output was underutilised during low-demand windows. The findings were compiled into a business case and presented directly to senior leadership, recommending shift schedule restructuring to better align operational hours with peak renewable generation.</p>
          <div class="step-tags">
            <span class="step-tag">Variance Analysis</span>
            <span class="step-tag">Supply-vs-Demand Forecasting</span>
            <span class="step-tag blue">2.25M PKR Gap Identified</span>
            <span class="step-tag">Senior Leadership Presentation</span>
          </div>
        </div>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       QUANTIFIABLE RESULTS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="results-h">
    <p class="sec-label"><span class="sec-num">09</span> Quantifiable Results</p>
    <h2 id="results-h">The Statistical Logic, the Decision Framework, and What They Produced</h2>

    <p>
      The table below shows how generation interval variance was classified and mapped to operational action — the decision framework derived from the hypothesis testing results. The Python code block below it shows the core logic used to evaluate each 15-minute interval against the baseline and determine whether it warranted a predictive scheduling response.
    </p>

    <!-- DECISION FRAMEWORK TABLE -->
    <p class="table-caption">Generation Variance Classification &amp; Operational Response</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Test Result</th>
            <th>Interpretation</th>
            <th>Confidence</th>
            <th>Action Tier</th>
            <th>Required Response</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>p &lt; 0.01</td>
            <td>Highly significant deviation from baseline generation</td>
            <td class="risk-critical">&gt; 99%</td>
            <td><span class="risk-badge critical">Act Now</span></td>
            <td>Trigger predictive equipment startup / shutdown immediately</td>
          </tr>
          <tr>
            <td>p &lt; 0.05</td>
            <td>Statistically significant deviation</td>
            <td class="risk-moderate">&gt; 95%</td>
            <td><span class="risk-badge moderate">Schedule Adjustment</span></td>
            <td>Flag interval for predictive scheduling within next cycle</td>
          </tr>
          <tr>
            <td>p ≥ 0.05</td>
            <td>Within normal stochastic range — not significant</td>
            <td class="risk-low">N/A</td>
            <td><span class="risk-badge low">No Action</span></td>
            <td>Maintain current schedule; log interval for trend monitoring</td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- SAMPLE INTERVAL TABLE -->
    <p class="table-caption">Sample 15-Minute Interval Evaluations — Representative Examples</p>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Time Window</th>
            <th>Observed Output (MW)</th>
            <th>Baseline Expected (MW)</th>
            <th>Test</th>
            <th>p-value</th>
            <th>Result</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>06:00 – 06:15</td>
            <td>2.1</td>
            <td>1.4</td>
            <td>Z-test</td>
            <td class="risk-critical">0.004</td>
            <td><span class="risk-badge critical">Significant</span></td>
            <td>Bring auxiliary equipment online ahead of ramp</td>
          </tr>
          <tr>
            <td>11:30 – 11:45</td>
            <td>19.8</td>
            <td>19.5</td>
            <td>T-test</td>
            <td class="risk-low">0.41</td>
            <td><span class="risk-badge low">Not Significant</span></td>
            <td>Maintain current schedule</td>
          </tr>
          <tr>
            <td>16:45 – 17:00</td>
            <td>9.2</td>
            <td>12.6</td>
            <td>Z-test</td>
            <td class="risk-moderate">0.03</td>
            <td><span class="risk-badge moderate">Significant</span></td>
            <td>Pre-emptively shift load to avoid grid draw</td>
          </tr>
          <tr>
            <td>19:00 – 19:15</td>
            <td>0.6</td>
            <td>0.5</td>
            <td>T-test</td>
            <td class="risk-low">0.62</td>
            <td><span class="risk-badge low">Not Significant</span></td>
            <td>Maintain current schedule</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="deviation-note">
      <strong>On the significance thresholds:</strong> The p &lt; 0.05 threshold for flagging a scheduling adjustment was chosen to balance responsiveness against false positives — a lower threshold (e.g. p &lt; 0.10) would have triggered too many low-confidence schedule changes, eroding operational trust in the predictive model, while a higher bar (e.g. p &lt; 0.01 only) would have missed genuine but moderate generation shifts. The two-tier structure (p &lt; 0.01 for immediate action, p &lt; 0.05 for next-cycle scheduling) was calibrated against the observed variance distribution in the 15-minute interval dataset.
    </div>

    <!-- PYTHON CODE BLOCK -->
    <p class="table-caption" style="margin-top:1.8rem;">Python Predictive Scheduling Engine — Core Function</p>
    <div class="code-block">
      <pre><span class="c-cm"># ── Predictive Load Scheduling Engine ───────────────────────</span>
<span class="c-cm"># Applies hypothesis testing to 15-minute generation intervals</span>
<span class="c-cm"># to determine whether observed deviation from baseline</span>
<span class="c-cm"># warrants a predictive scheduling action.</span>

<span class="c-kw">import</span> numpy <span class="c-kw">as</span> np
<span class="c-kw">from</span> scipy <span class="c-kw">import</span> stats

<span class="c-kw">def</span> <span class="c-fn">evaluate_interval</span>(observed: <span class="c-fn">float</span>, baseline_mean: <span class="c-fn">float</span>,
                       baseline_std: <span class="c-fn">float</span>, sample_size: <span class="c-fn">int</span>) -&gt; <span class="c-fn">dict</span>:
    <span class="c-str">"""
    Evaluates a single 15-minute generation interval against
    the historical baseline using a Z-test, and classifies the
    result into an operational action tier.
    Args:
        observed      : float  observed generation (MW) for interval
        baseline_mean : float  historical mean generation (MW)
        baseline_std  : float  historical std deviation (MW)
        sample_size   : int    number of historical intervals in baseline
    Returns:
        dict with z-score, p-value, tier, and required action.
    """</span>
    standard_error = baseline_std <span class="c-op">/</span> np.sqrt(sample_size)
    z_score = (observed <span class="c-op">-</span> baseline_mean) <span class="c-op">/</span> standard_error
    p_value = <span class="c-num">2</span> <span class="c-op">*</span> (<span class="c-num">1</span> <span class="c-op">-</span> stats.norm.cdf(<span class="c-fn">abs</span>(z_score)))

    <span class="c-kw">if</span> p_value <span class="c-op">&lt;</span> <span class="c-num">0.01</span>:
        <span class="c-kw">return</span> {
            <span class="c-str">"p_value"</span> : p_value,
            <span class="c-str">"tier"</span>    : <span class="c-str">"ACT_NOW"</span>,
            <span class="c-str">"action"</span>  : <span class="c-str">"Trigger predictive equipment startup/shutdown immediately"</span>
        }
    <span class="c-kw">elif</span> p_value <span class="c-op">&lt;</span> <span class="c-num">0.05</span>:
        <span class="c-kw">return</span> {
            <span class="c-str">"p_value"</span> : p_value,
            <span class="c-str">"tier"</span>    : <span class="c-str">"SCHEDULE_ADJUSTMENT"</span>,
            <span class="c-str">"action"</span>  : <span class="c-str">"Flag interval for predictive scheduling next cycle"</span>
        }
    <span class="c-kw">else</span>:
        <span class="c-kw">return</span> {
            <span class="c-str">"p_value"</span> : p_value,
            <span class="c-str">"tier"</span>    : <span class="c-str">"NO_ACTION"</span>,
            <span class="c-str">"action"</span>  : <span class="c-str">"Maintain schedule — log for trend monitoring"</span>
        }


<span class="c-kw">def</span> <span class="c-fn">supply_demand_gap</span>(supply_series: <span class="c-fn">list</span>, demand_series: <span class="c-fn">list</span>) -&gt; <span class="c-fn">dict</span>:
    <span class="c-str">"""
    Computes the variance between solar supply and operational
    demand across matched intervals, returning the aggregate
    misalignment used for the leadership business case.
    """</span>
    supply = np.array(supply_series)
    demand = np.array(demand_series)
    delta = demand <span class="c-op">-</span> supply

    <span class="c-kw">return</span> {
        <span class="c-str">"mean_gap_mw"</span>      : <span class="c-fn">float</span>(np.mean(delta)),
        <span class="c-str">"total_misaligned_mwh"</span>: <span class="c-fn">float</span>(np.<span class="c-fn">sum</span>(delta[delta <span class="c-op">&gt;</span> <span class="c-num">0</span>]) <span class="c-op">*</span> <span class="c-num">0.25</span>),  <span class="c-cm"># 15-min intervals → MWh</span>
        <span class="c-str">"recommendation"</span>      : <span class="c-str">"Restructure shift hours toward peak solar generation windows"</span>
    }</pre>
    </div>

    <div class="deviation-note">
      <strong>Why hypothesis testing rather than a fixed threshold rule?</strong> A fixed-threshold rule (e.g. "act if generation drops more than 1 MW below average") would treat every deviation of that size identically, regardless of how typical that level of fluctuation actually is for a given time of day. Hypothesis testing instead asks whether the deviation is large relative to the plant's own historical variance at that interval — meaning a 1 MW swing during a normally volatile morning ramp is treated very differently from the same swing during a normally stable midday plateau. This made the predictive triggers specific to the plant's actual behaviour rather than an arbitrary round-number rule.
    </div>

    <div class="placeholder">
      <div class="ph-icon">📈</div>
      <p class="ph-tag">Suggested Visual — Generation vs. Baseline Time Series</p>
      <p class="ph-desc">A line chart overlaying actual 15-minute generation output against the statistical baseline band, with flagged intervals (p &lt; 0.05 and p &lt; 0.01) highlighted along the timeline. This is the direct output of the <code>evaluate_interval()</code> function and the clearest visual demonstration of how the predictive model identifies actionable moments.</p>
    </div>

  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       3 HEADLINE RESULTS
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="trio-h">
    <p class="sec-label"><span class="sec-num">10</span> Headline Results</p>
    <h2 id="trio-h">Three Numbers That Tell the Story</h2>
    <div class="results-trio">
      <div class="result-cell">
        <div class="result-big">4M</div>
        <div class="result-unit">PKR — Predictive Savings</div>
        <p class="result-desc">Operational cost reduction secured by moving equipment startup from a reactive to a hypothesis-tested predictive model across the plant's 15-minute generation intervals</p>
      </div>
      <div class="result-cell">
        <div class="result-big">2.25M</div>
        <div class="result-unit">PKR — Gap Identified</div>
        <p class="result-desc">Efficiency gap surfaced through variance analysis of supply-vs-demand forecasting, quantifying misalignment between solar availability and operational scheduling</p>
      </div>
      <div class="result-cell">
        <div class="result-big">6.25M</div>
        <div class="result-unit">PKR — Total Impact</div>
        <p class="result-desc">Combined financial impact of the predictive model and the gap-recovery business case presented to senior leadership for operational restructuring</p>
      </div>
    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       KEY FINDINGS & LEARNING OUTCOMES
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="findings-h">
    <p class="sec-label"><span class="sec-num">11</span> Key Findings &amp; Learning Outcomes</p>
    <h2 id="findings-h">What Statistically Grounding an Operational Schedule Actually Teaches You</h2>
    <div class="findings-grid">

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>Not Every Fluctuation Deserves a Response</h3>
        <p>Before hypothesis testing was applied, the temptation in reactive scheduling was to respond to every observed dip or spike in generation. The Z-test and T-test results showed that the majority of interval-to-interval variation fell well within normal stochastic range — and reacting to it would have produced more operational churn than benefit. The discipline of statistical significance testing is as much about knowing when *not* to act as when to act.</p>
      </div>

      <div class="finding-card blue-accent">
        <span class="find-pill learn">Learning</span>
        <h3>Predictive Value Comes From the Baseline, Not Just the Test</h3>
        <p>The hypothesis test itself is only as useful as the baseline it's compared against. Building an accurate, time-of-day-aware baseline from the historical 15-minute interval data was the most time-consuming part of the project — but it's what allowed the same absolute deviation to be correctly interpreted as significant during a stable period and insignificant during a naturally volatile one.</p>
      </div>

      <div class="finding-card amber-accent">
        <span class="find-pill design">Design</span>
        <h3>The Two Savings Figures Came From Two Different Questions</h3>
        <p>The 4M PKR predictive-startup savings answered "when should we act on this specific interval?" — a question about timing. The 2.25M PKR gap-recovery figure answered a structurally different question: "is our overall schedule aligned with our overall generation profile?" — a question about long-run alignment. Keeping these as two distinct analyses, rather than collapsing them into one model, made each easier to validate and easier to explain to leadership separately.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>Morning Ramp Windows Carried the Highest Concentration of Significant Deviations</h3>
        <p>Across the evaluated intervals, the early-morning ramp-up period consistently produced the highest proportion of statistically significant (p &lt; 0.05) results — reflecting the genuinely higher variability of irradiance conditions during sunrise transitions compared to the relative stability of midday peak generation. This gave operations a concrete window to prioritise for predictive scheduling attention.</p>
      </div>

      <div class="finding-card blue-accent">
        <span class="find-pill learn">Learning</span>
        <h3>A Business Case Needs a Number Leadership Can Act On, Not Just a Finding</h3>
        <p>Identifying the 2.25M PKR gap was only half the work. Translating "supply and demand are misaligned" into a specific, actionable recommendation — restructure shift hours to align with peak solar generation — was what made the variance analysis land as a business case rather than an academic observation. Quantification matters, but quantification paired with a concrete operational recommendation is what gets acted on.</p>
      </div>

      <div class="finding-card">
        <span class="find-pill find">Finding</span>
        <h3>15-Minute Resolution Was the Right Granularity — Not the Finest Possible</h3>
        <p>Finer-resolution data was technically available, but at sub-minute granularity the noise-to-signal ratio increased to the point where hypothesis tests would have flagged far more intervals as "significant" simply due to instrument and atmospheric micro-fluctuations. The 15-minute interval struck the balance between capturing genuine operational patterns and avoiding a model that was statistically "correct" but operationally unusable due to excessive false positives.</p>
      </div>

    </div>
  </section>

  <div class="divider"></div>


  <!-- ════════════════════════════════════════════════════════════
       PROJECT CONTEXT
  ════════════════════════════════════════════════════════════ -->
  <section class="section" aria-labelledby="context-h">
    <p class="sec-label"><span class="sec-num">12</span> Project Context</p>
    <h2 id="context-h">Scope, Setting &amp; Deliverables</h2>

    <p>
      This project was carried out within renewable energy operations, focused on a 21 MW solar power plant. The work combined statistical analysis of historical generation data with direct engagement with operational scheduling practices, culminating in both a deployed predictive model and a formal business case presented to senior leadership. Each card below represents a distinct, delivered component.
    </p>

    <div class="context-grid">
      <div class="context-card">
        <span class="ctx-icon">📊</span>
        <h3>Analytical Approach</h3>
        <p>Time Series Analysis applied to 15-minute generation intervals, with Z-tests and T-tests used to determine the statistical significance of observed deviations from baseline.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">☀️</span>
        <h3>Asset</h3>
        <p>A 21 MW solar power plant — generation data covering the full intraday profile from morning ramp-up through midday peak to evening decline.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">⚡</span>
        <h3>Operational Outcome</h3>
        <p>Transitioned equipment startup and shutdown from a reactive model to a predictive, statistically validated scheduling protocol — securing 4M PKR in savings.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">📐</span>
        <h3>Variance Analysis</h3>
        <p>Supply-vs-demand forecasting comparison identifying a 2.25M PKR efficiency gap between solar availability and operational shift scheduling.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">🗣️</span>
        <h3>Stakeholder Communication</h3>
        <p>Findings compiled into a formal business case and presented directly to senior leadership, recommending operational hour restructuring to maximise free solar energy use.</p>
      </div>
      <div class="context-card">
        <span class="ctx-icon">✅</span>
        <h3>Outcome</h3>
        <p>Combined predictive and gap-recovery impact formally quantified at 6.25M PKR.</p>
        <span class="outcome-pill">6.25M PKR Total Savings</span>
      </div>
    </div>

  </section>

</main>


<!-- ════════════════════════════════════════════════════════════
     FOOTER
════════════════════════════════════════════════════════════ -->
<footer class="site-footer">
  <p>
    Renewable Energy Operations &nbsp;·&nbsp;
    Sustainability &amp; Predictive Analytics &nbsp;·&nbsp;
    Energy-Efficient Resource Scheduling &nbsp;·&nbsp;
    <a href="/">← Back to Portfolio</a>
  </p>
</footer>


</body>
</html>
