<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>הגדרת פרויקט גמר | מדעי המחשב - אלוני יצחק</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;500;600;700;800;900&family=Rubik:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #0f1117;
            --bg-card: #1a1d27;
            --bg-card-hover: #1e2231;
            --bg-input: #13151d;
            --border: #2a2d3a;
            --border-focus: #6366f1;
            --text: #e2e4eb;
            --text-dim: #8b8fa3;
            --text-muted: #5c6078;
            --accent: #6366f1;
            --accent-glow: rgba(99, 102, 241, 0.15);
            --html-color: #e34f26;
            --css-color: #264de4;
            --js-color: #f0db4f;
            --firebase-color: #ffca28;
            --green: #22c55e;
            --green-dim: rgba(34, 197, 94, 0.1);
            --orange: #f97316;
            --orange-dim: rgba(249, 115, 22, 0.1);
            --purple: #a855f7;
            --purple-dim: rgba(168, 85, 247, 0.1);
            --red: #ef4444;
            --red-dim: rgba(239, 68, 68, 0.08);
            --radius: 12px;
            --radius-sm: 8px;
            --shadow: 0 1px 3px rgba(0,0,0,0.3), 0 4px 12px rgba(0,0,0,0.2);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Heebo', sans-serif;
            background: var(--bg);
            color: var(--text);
            line-height: 1.7;
            min-height: 100vh;
        }

        /* === BACKGROUND EFFECTS === */
        .bg-grid {
            position: fixed;
            inset: 0;
            background-image:
                linear-gradient(rgba(99, 102, 241, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(99, 102, 241, 0.03) 1px, transparent 1px);
            background-size: 60px 60px;
            pointer-events: none;
            z-index: 0;
        }

        .bg-glow {
            position: fixed;
            top: -200px;
            left: 50%;
            transform: translateX(-50%);
            width: 800px;
            height: 600px;
            background: radial-gradient(ellipse, rgba(99, 102, 241, 0.08) 0%, transparent 70%);
            pointer-events: none;
            z-index: 0;
        }

        /* === LAYOUT === */
        .container {
            position: relative;
            z-index: 1;
            max-width: 860px;
            margin: 0 auto;
            padding: 2rem 1.5rem 4rem;
        }

        /* === HERO === */
        .hero {
            text-align: center;
            padding: 3rem 0 2rem;
            position: relative;
        }

        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            background: var(--accent-glow);
            border: 1px solid rgba(99, 102, 241, 0.2);
            color: var(--accent);
            padding: 0.4rem 1rem;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 500;
            margin-bottom: 1.5rem;
            font-family: 'Rubik', sans-serif;
        }

        .hero-badge .dot {
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: var(--accent);
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }

        .hero h1 {
            font-size: clamp(2rem, 5vw, 3rem);
            font-weight: 800;
            letter-spacing: -0.02em;
            background: linear-gradient(135deg, #e2e4eb 0%, #8b8fa3 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.75rem;
        }

        .hero .subtitle {
            font-size: 1.1rem;
            color: var(--text-dim);
            font-weight: 300;
            max-width: 500px;
            margin: 0 auto;
        }

        .hero .deadline {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            margin-top: 1.5rem;
            padding: 0.6rem 1.2rem;
            background: var(--red-dim);
            border: 1px solid rgba(239, 68, 68, 0.15);
            border-radius: var(--radius-sm);
            color: #fca5a5;
            font-size: 0.9rem;
            font-weight: 500;
        }

        /* === TECH STACK VISUAL === */
        .tech-stack {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin: 2.5rem 0;
            flex-wrap: wrap;
        }

        .tech-pill {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.5rem 1.2rem;
            border-radius: 50px;
            font-family: 'IBM Plex Mono', monospace;
            font-size: 0.85rem;
            font-weight: 500;
            border: 1px solid;
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .tech-pill:hover {
            transform: translateY(-2px);
        }

        .tech-pill.html {
            background: rgba(227, 79, 38, 0.08);
            border-color: rgba(227, 79, 38, 0.2);
            color: #f87171;
        }
        .tech-pill.css {
            background: rgba(38, 77, 228, 0.08);
            border-color: rgba(38, 77, 228, 0.2);
            color: #60a5fa;
        }
        .tech-pill.js {
            background: rgba(240, 219, 79, 0.06);
            border-color: rgba(240, 219, 79, 0.15);
            color: #fbbf24;
        }
        .tech-pill.firebase {
            background: rgba(255, 202, 40, 0.06);
            border-color: rgba(255, 202, 40, 0.15);
            color: #fbbf24;
        }

        .tech-dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
        }
        .html .tech-dot { background: var(--html-color); }
        .css .tech-dot { background: var(--css-color); }
        .js .tech-dot { background: var(--js-color); }
        .firebase .tech-dot { background: var(--firebase-color); }

        /* === SECTIONS === */
        .section {
            margin-bottom: 2rem;
        }

        .section-header {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            margin-bottom: 1.25rem;
            padding-bottom: 0.75rem;
            border-bottom: 1px solid var(--border);
        }

        .section-number {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 32px;
            height: 32px;
            border-radius: 8px;
            background: var(--accent-glow);
            border: 1px solid rgba(99, 102, 241, 0.2);
            color: var(--accent);
            font-size: 0.85rem;
            font-weight: 700;
            font-family: 'IBM Plex Mono', monospace;
            flex-shrink: 0;
        }

        .section-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--text);
        }

        /* === CARDS === */
        .card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 1.5rem;
            margin-bottom: 1rem;
            transition: border-color 0.2s;
        }

        .card:hover {
            border-color: rgba(99, 102, 241, 0.15);
        }

        /* === INFO BOXES === */
        .info-box {
            border-radius: var(--radius);
            padding: 1.25rem 1.5rem;
            margin-bottom: 1.5rem;
            border: 1px solid;
        }

        .info-box.tip {
            background: var(--green-dim);
            border-color: rgba(34, 197, 94, 0.15);
        }
        .info-box.tip .info-label { color: var(--green); }

        .info-box.warn {
            background: var(--orange-dim);
            border-color: rgba(249, 115, 22, 0.15);
        }
        .info-box.warn .info-label { color: var(--orange); }

        .info-box.idea {
            background: var(--purple-dim);
            border-color: rgba(168, 85, 247, 0.15);
        }
        .info-box.idea .info-label { color: var(--purple); }

        .info-box.firebase-info {
            background: rgba(255, 202, 40, 0.04);
            border-color: rgba(255, 202, 40, 0.12);
        }
        .info-box.firebase-info .info-label { color: var(--firebase-color); }

        .info-label {
            font-weight: 700;
            font-size: 0.9rem;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            gap: 0.4rem;
        }

        .info-box p, .info-box li {
            color: var(--text-dim);
            font-size: 0.95rem;
            line-height: 1.8;
        }

        .info-box ul, .info-box ol {
            padding-right: 1.2rem;
            margin-top: 0.5rem;
        }

        .info-box li {
            margin-bottom: 0.3rem;
        }

        /* === TECH EXPLAINER === */
        .tech-explain {
            display: grid;
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .tech-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 1.25rem 1.5rem;
            position: relative;
            overflow: hidden;
            transition: border-color 0.3s, transform 0.2s;
        }

        .tech-card:hover {
            transform: translateY(-1px);
        }

        .tech-card::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 4px;
            height: 100%;
        }

        .tech-card.html-card::before { background: var(--html-color); }
        .tech-card.css-card::before { background: var(--css-color); }
        .tech-card.js-card::before { background: var(--js-color); }
        .tech-card.firebase-card::before { background: var(--firebase-color); }

        .tech-card:hover.html-card { border-color: rgba(227, 79, 38, 0.3); }
        .tech-card:hover.css-card { border-color: rgba(38, 77, 228, 0.3); }
        .tech-card:hover.js-card { border-color: rgba(240, 219, 79, 0.2); }
        .tech-card:hover.firebase-card { border-color: rgba(255, 202, 40, 0.2); }

        .tech-card h3 {
            font-size: 1.05rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .tech-card h3 code {
            font-family: 'IBM Plex Mono', monospace;
            font-weight: 600;
        }

        .html-card h3 code { color: #f87171; }
        .css-card h3 code { color: #60a5fa; }
        .js-card h3 code { color: #fbbf24; }
        .firebase-card h3 code { color: #fbbf24; }

        .tech-card p {
            color: var(--text-dim);
            font-size: 0.92rem;
            line-height: 1.7;
        }

        .tech-card .analogy {
            margin-top: 0.75rem;
            padding: 0.6rem 0.9rem;
            background: rgba(99, 102, 241, 0.04);
            border-radius: var(--radius-sm);
            font-size: 0.85rem;
            color: var(--text-dim);
            border-right: 3px solid rgba(99, 102, 241, 0.2);
        }

        .tech-card .analogy strong {
            color: var(--text);
        }

        /* === FIREBASE FEATURES === */
        .firebase-features {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.75rem;
            margin-top: 1rem;
        }

        @media (max-width: 600px) {
            .firebase-features {
                grid-template-columns: 1fr;
            }
        }

        .fb-feature {
            background: rgba(255, 202, 40, 0.03);
            border: 1px solid rgba(255, 202, 40, 0.08);
            border-radius: var(--radius-sm);
            padding: 0.9rem 1rem;
        }

        .fb-feature h4 {
            font-size: 0.9rem;
            font-weight: 600;
            color: var(--firebase-color);
            margin-bottom: 0.3rem;
            font-family: 'Rubik', sans-serif;
        }

        .fb-feature h4 code {
            font-family: 'IBM Plex Mono', monospace;
            font-size: 0.8rem;
        }

        .fb-feature p {
            font-size: 0.82rem;
            color: var(--text-muted);
            line-height: 1.6;
        }

        /* === IDEAS GRID === */
        .ideas-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.75rem;
            margin-top: 1rem;
        }

        @media (max-width: 600px) {
            .ideas-grid {
                grid-template-columns: 1fr;
            }
        }

        .idea-card {
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius-sm);
            padding: 1rem 1.1rem;
            transition: border-color 0.2s, transform 0.2s;
            cursor: default;
        }

        .idea-card:hover {
            border-color: rgba(168, 85, 247, 0.25);
            transform: translateY(-1px);
        }

        .idea-card .idea-icon {
            font-size: 1.4rem;
            margin-bottom: 0.4rem;
        }

        .idea-card h4 {
            font-size: 0.95rem;
            font-weight: 600;
            margin-bottom: 0.3rem;
            color: var(--text);
        }

        .idea-card p {
            font-size: 0.82rem;
            color: var(--text-muted);
            line-height: 1.6;
        }

        .idea-card code {
            font-family: 'IBM Plex Mono', monospace;
            font-size: 0.78rem;
            color: var(--purple);
            background: var(--purple-dim);
            padding: 0.1em 0.35em;
            border-radius: 4px;
        }

        /* === FORM ELEMENTS === */
        .form-group {
            margin-bottom: 1.25rem;
        }

        .form-group:last-child {
            margin-bottom: 0;
        }

        label {
            display: block;
            font-weight: 600;
            font-size: 0.95rem;
            margin-bottom: 0.5rem;
            color: var(--text);
        }

        label .required {
            color: var(--red);
            margin-right: 0.2rem;
        }

        .label-hint {
            font-weight: 400;
            font-size: 0.82rem;
            color: var(--text-muted);
            display: block;
            margin-top: 0.15rem;
        }

        input[type="text"],
        input[type="date"],
        textarea {
            width: 100%;
            padding: 0.75rem 1rem;
            background: var(--bg-input);
            border: 1px solid var(--border);
            border-radius: var(--radius-sm);
            color: var(--text);
            font-family: 'Heebo', sans-serif;
            font-size: 0.95rem;
            transition: border-color 0.2s, box-shadow 0.2s;
            direction: rtl;
        }

        input[type="text"]:focus,
        input[type="date"]:focus,
        textarea:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px var(--accent-glow);
        }

        input::placeholder,
        textarea::placeholder {
            color: var(--text-muted);
            font-size: 0.88rem;
        }

        textarea {
            min-height: 100px;
            resize: vertical;
            line-height: 1.7;
        }

        /* === RADIO & CHECKBOX === */
        .radio-group, .checkbox-group {
            display: flex;
            flex-wrap: wrap;
            gap: 0.75rem;
            margin-top: 0.25rem;
        }

        .radio-option, .checkbox-option {
            position: relative;
        }

        .radio-option input,
        .checkbox-option input {
            position: absolute;
            opacity: 0;
            width: 0;
            height: 0;
        }

        .radio-option label,
        .checkbox-option label {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.6rem 1.1rem;
            background: var(--bg-input);
            border: 1px solid var(--border);
            border-radius: var(--radius-sm);
            cursor: pointer;
            transition: all 0.2s;
            font-weight: 400;
            font-size: 0.9rem;
        }

        .radio-option input:checked + label,
        .checkbox-option input:checked + label {
            background: var(--accent-glow);
            border-color: var(--accent);
            color: var(--accent);
        }

        .radio-option label:hover,
        .checkbox-option label:hover {
            border-color: rgba(99, 102, 241, 0.3);
        }

        .checkbox-option.firebase-check input:checked + label {
            background: rgba(255, 202, 40, 0.08);
            border-color: rgba(255, 202, 40, 0.3);
            color: var(--firebase-color);
        }

        .partner-field {
            margin-top: 0.75rem;
            display: none;
        }

        .partner-field.visible {
            display: block;
        }

        /* === SCHEDULE TABLE === */
        .schedule-table {
            width: 100%;
            border-collapse: separate;
            border-spacing: 0;
            margin-top: 0.75rem;
        }

        .schedule-table th {
            background: rgba(99, 102, 241, 0.06);
            padding: 0.7rem 1rem;
            font-weight: 600;
            font-size: 0.85rem;
            color: var(--accent);
            text-align: right;
            border-bottom: 1px solid var(--border);
        }

        .schedule-table th:first-child {
            border-radius: 0 var(--radius-sm) 0 0;
            width: 140px;
        }

        .schedule-table th:last-child {
            border-radius: var(--radius-sm) 0 0 0;
        }

        .schedule-table td {
            padding: 0.5rem;
            border-bottom: 1px solid var(--border);
            vertical-align: top;
        }

        .schedule-table td:first-child {
            padding: 0.75rem 1rem;
            font-weight: 600;
            font-size: 0.9rem;
            color: var(--text-dim);
            background: rgba(99, 102, 241, 0.02);
        }

        .schedule-table textarea {
            min-height: 60px;
            border: none;
            background: transparent;
            resize: vertical;
        }

        .schedule-table textarea:focus {
            background: var(--bg-input);
            border: 1px solid var(--accent);
        }

        /* === CHECKLIST === */
        .checklist {
            list-style: none;
            padding: 0;
        }

        .checklist li {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            padding: 0.7rem 0;
            border-bottom: 1px solid rgba(42, 45, 58, 0.5);
            font-size: 0.95rem;
            color: var(--text-dim);
            transition: color 0.2s;
        }

        .checklist li:last-child {
            border-bottom: none;
        }

        .checklist input[type="checkbox"] {
            appearance: none;
            -webkit-appearance: none;
            width: 20px;
            height: 20px;
            border: 2px solid var(--border);
            border-radius: 4px;
            cursor: pointer;
            flex-shrink: 0;
            position: relative;
            transition: all 0.2s;
        }

        .checklist input[type="checkbox"]:checked {
            background: var(--accent);
            border-color: var(--accent);
        }

        .checklist input[type="checkbox"]:checked::after {
            content: '✓';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: white;
            font-size: 12px;
            font-weight: 700;
        }

        .checklist input[type="checkbox"]:checked ~ span {
            color: var(--text);
            text-decoration: line-through;
            text-decoration-color: var(--accent);
        }

        /* === RESOURCES === */
        .resources-list {
            display: grid;
            gap: 0.5rem;
            margin-top: 0.75rem;
        }

        .resource-link {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            padding: 0.75rem 1rem;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius-sm);
            text-decoration: none;
            color: var(--text);
            font-size: 0.9rem;
            transition: all 0.2s;
        }

        .resource-link:hover {
            border-color: var(--accent);
            background: var(--bg-card-hover);
        }

        .resource-link .r-icon {
            font-size: 1.2rem;
            flex-shrink: 0;
        }

        .resource-link .r-desc {
            font-size: 0.78rem;
            color: var(--text-muted);
        }

        /* === COLLAPSIBLE === */
        .collapsible-trigger {
            display: flex;
            align-items: center;
            justify-content: space-between;
            width: 100%;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 1rem 1.25rem;
            cursor: pointer;
            color: var(--text);
            font-family: 'Heebo', sans-serif;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.2s;
            text-align: right;
            margin-bottom: 0.5rem;
        }

        .collapsible-trigger:hover {
            border-color: rgba(99, 102, 241, 0.2);
        }

        .collapsible-trigger .arrow {
            transition: transform 0.3s;
            color: var(--text-muted);
            font-size: 0.8rem;
        }

        .collapsible-trigger.open .arrow {
            transform: rotate(180deg);
        }

        .collapsible-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease;
        }

        .collapsible-content.open {
            max-height: 3000px;
        }

        /* === PRINT BUTTON === */
        .print-bar {
            display: flex;
            gap: 0.75rem;
            justify-content: center;
            margin-top: 2.5rem;
            flex-wrap: wrap;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.75rem 1.5rem;
            border-radius: var(--radius-sm);
            font-family: 'Heebo', sans-serif;
            font-size: 0.95rem;
            font-weight: 600;
            cursor: pointer;
            border: none;
            transition: all 0.2s;
        }

        .btn-primary {
            background: var(--accent);
            color: white;
        }

        .btn-primary:hover {
            background: #5558e6;
            box-shadow: 0 4px 16px rgba(99, 102, 241, 0.3);
        }

        .btn-secondary {
            background: var(--bg-card);
            color: var(--text);
            border: 1px solid var(--border);
        }

        .btn-secondary:hover {
            border-color: var(--accent);
        }

        /* === FOOTER === */
        .footer {
            text-align: center;
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid var(--border);
        }

        .footer p {
            color: var(--text-muted);
            font-size: 0.85rem;
        }

        .footer .heart {
            color: var(--red);
        }

        /* === SEPARATOR === */
        .sep {
            height: 1px;
            background: linear-gradient(to left, transparent, var(--border), transparent);
            margin: 2rem 0;
        }

        /* === PROGRESS === */
        .progress-bar {
            position: fixed;
            top: 0;
            right: 0;
            left: 0;
            height: 3px;
            background: var(--bg);
            z-index: 100;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, var(--accent), var(--purple));
            width: 0%;
            transition: width 0.3s;
        }

        /* === PRINT === */
        @media print {
            body {
                background: white;
                color: #1a1a1a;
            }
            .bg-grid, .bg-glow, .progress-bar, .print-bar {
                display: none;
            }
            .container {
                max-width: 100%;
            }
            .card, .tech-card, .info-box, .idea-card {
                background: white;
                border-color: #ddd;
                break-inside: avoid;
            }
            input[type="text"], textarea {
                border: 1px solid #ccc;
                background: #fafafa;
            }
            .hero h1 {
                -webkit-text-fill-color: #1a1a1a;
                background: none;
            }
        }
    </style>
</head>
<body>
    <div class="bg-grid"></div>
    <div class="bg-glow"></div>
    <div class="progress-bar"><div class="progress-fill" id="progressFill"></div></div>

    <div class="container">

        <!-- HERO -->
        <header class="hero">
            <div class="hero-badge">
                <span class="dot"></span>
                מגמת מדעי המחשב · אלוני יצחק · כיתה י'
            </div>
            <h1>הגדרת פרויקט גמר</h1>
            <p class="subtitle">הטופס הזה יעזור לכם לגבש את הרעיון, להבין את הטכנולוגיות, ולתכנן את הדרך להגשה</p>
            <div class="deadline">
                📅 מועד הגשה: יוני 2026
            </div>
        </header>

        <!-- TECH PILLS -->
        <div class="tech-stack">
            <div class="tech-pill html"><span class="tech-dot"></span>HTML</div>
            <div class="tech-pill css"><span class="tech-dot"></span>CSS</div>
            <div class="tech-pill js"><span class="tech-dot"></span>JavaScript</div>
            <div class="tech-pill firebase"><span class="tech-dot"></span>Firebase</div>
        </div>

        <div class="info-box warn">
            <div class="info-label">⚠️ חשוב לדעת</div>
            <p>הפרויקט חייב לכלול את <strong>כל ארבע הטכנולוגיות</strong> שמופיעות למעלה. קראו את ההסברים, גבשו רעיון, ומלאו את הטופס. העבודה <strong>אישית או בזוגות</strong> (באישור המורה).</p>
        </div>

        <div class="sep"></div>

        <!-- === PART 1: KNOW THE TECH === -->
        <section class="section">
            <div class="section-header">
                <div class="section-number">📚</div>
                <h2 class="section-title">הכירו את הטכנולוגיות</h2>
            </div>

            <div class="info-box tip">
                <div class="info-label">💡 למה דווקא אלה?</div>
                <p>אתם כבר מכירים <strong>Java</strong> — שפת תכנות חזקה. עכשיו תלמדו לבנות דברים שאנשים באמת רואים ומשתמשים בהם דרך הדפדפן. <strong>HTML</strong>, <strong>CSS</strong> ו-<strong>JavaScript</strong> הם שלושת עמודי התווך של כל אתר אינטרנט בעולם, ו-<strong>Firebase</strong> מוסיף יכולות מתקדמות בקלות.</p>
            </div>

            <div class="tech-explain">
                <div class="tech-card html-card">
                    <h3><code>HTML</code> — השלד של האתר</h3>
                    <p>HTML מגדיר <strong>מה</strong> יש בדף: כותרות, פסקאות, כפתורים, תמונות, טפסים ועוד. הוא לא עוסק ביופי — הוא עוסק במבנה.</p>
                    <div class="analogy"><strong>דוגמה מהחיים:</strong> כמו שב-Word מגדירים כותרת, פסקה ורשימה — ככה HTML מגדיר את מבנה האתר.</div>
                </div>

                <div class="tech-card css-card">
                    <h3><code>CSS</code> — העיצוב והמראה</h3>
                    <p>CSS הוא מה שגורם לאתר להיראות טוב. הוא קובע צבעים, גדלים, מיקומים ואנימציות. בלי CSS, כל אתר היה נראה כמו מסמך טקסט רגיל.</p>
                    <div class="analogy"><strong>דוגמה מהחיים:</strong> אם HTML הוא השלד של הבניין, CSS הוא הצבע, הריצוף, הרהיטים והעיצוב.</div>
                </div>

                <div class="tech-card js-card">
                    <h3><code>JavaScript</code> — ההתנהגות והלוגיקה</h3>
                    <p>JavaScript (בקיצור JS) היא שפת תכנות שרצה בדפדפן. היא מה שגורם לאתר להיות <strong>אינטראקטיבי</strong>: ללחוץ על כפתור ולראות תגובה, לשלוח טופס, לעדכן מידע בזמן אמת.</p>
                    <div class="analogy"><strong>קשר ל-Java:</strong> למרות השם הדומה, JavaScript ו-Java הן שפות שונות! אבל אם אתם מכירים Java, חלק מהתחביר יהיה מוכר — משתנים, לולאות, תנאים ופונקציות.</div>
                </div>

                <div class="tech-card firebase-card">
                    <h3><code>Firebase</code> — כוח-על מהענן</h3>
                    <p>Firebase הוא שירות <strong>חינמי של Google</strong> שמוסיף לאתר יכולות מתקדמות בלי שתצטרכו לבנות שרת. חשבו על זה ככלי קסם:</p>
                    <div class="firebase-features">
                        <div class="fb-feature">
                            <h4>🔐 <code>Authentication</code></h4>
                            <p>הרשמה וכניסה למערכת עם מייל, סיסמה, או חשבון Google</p>
                        </div>
                        <div class="fb-feature">
                            <h4>🗄️ <code>Firestore</code></h4>
                            <p>מסד נתונים בענן — שמירת הודעות, ציונים, מוצרים שנשמרים גם כשסוגרים דפדפן</p>
                        </div>
                        <div class="fb-feature">
                            <h4>📁 <code>Storage</code></h4>
                            <p>העלאת תמונות, קבצים ומדיה לענן</p>
                        </div>
                        <div class="fb-feature">
                            <h4>🌐 <code>Hosting</code></h4>
                            <p>העלאת האתר לאינטרנט כך שכולם יוכלו לגשת אליו</p>
                        </div>
                    </div>
                </div>
            </div>

            <div class="info-box firebase-info">
                <div class="info-label">🔥 בפרויקט שלכם חובה להשתמש לפחות ביכולת אחת של Firebase</div>
            </div>
        </section>

        <div class="sep"></div>

        <!-- === PART 2: IDEAS === -->
        <section class="section">
            <div class="section-header">
                <div class="section-number">💡</div>
                <h2 class="section-title">רעיונות להשראה</h2>
            </div>

            <div class="info-box idea">
                <div class="info-label">✨ לא חייבים לבחור מהרשימה — תהיו יצירתיים!</div>
            </div>

            <div class="ideas-grid">
                <div class="idea-card">
                    <div class="idea-icon">✅</div>
                    <h4>אפליקציית ניהול משימות</h4>
                    <p>יצירה, עדכון ומחיקת משימות. <code>Firestore</code> + <code>Auth</code></p>
                </div>
                <div class="idea-card">
                    <div class="idea-icon">🧠</div>
                    <h4>פלטפורמת חידונים</h4>
                    <p>יצירה ופתרון חידונים בנושאים שונים עם שמירת ציונים</p>
                </div>
                <div class="idea-card">
                    <div class="idea-icon">📝</div>
                    <h4>בלוג או פורום</h4>
                    <p>פרסום פוסטים ותגובות. <code>Auth</code> + <code>Firestore</code></p>
                </div>
                <div class="idea-card">
                    <div class="idea-icon">🛒</div>
                    <h4>חנות וירטואלית</h4>
                    <p>מוצרים, סינון, סל קניות ומעקב הזמנות</p>
                </div>
                <div class="idea-card">
                    <div class="idea-icon">🎮</div>
                    <h4>משחק אונליין</h4>
                    <p>טריוויה, זיכרון, או לוח עם טבלת שיאים מקוונת</p>
                </div>
                <div class="idea-card">
                    <div class="idea-icon">🌦️</div>
                    <h4>אפליקציית מזג אוויר / חדשות</h4>
                    <p>שליפת מידע מ-API חיצוני והצגתו בעיצוב נאה</p>
                </div>
                <div class="idea-card">
                    <div class="idea-icon">👥</div>
                    <h4>רשת חברתית מיני</h4>
                    <p>פרופילים, פוסטים ולייקים עם <code>Firebase</code></p>
                </div>
                <div class="idea-card">
                    <div class="idea-icon">📅</div>
                    <h4>מערכת הזמנות / לו"ז</h4>
                    <p>ניהול תורים, אירועים, או הזמנות לחדר</p>
                </div>
                <div class="idea-card">
                    <div class="idea-icon">💼</div>
                    <h4>תיק עבודות (Portfolio)</h4>
                    <p>אתר אישי מרשים שמציג את העבודות שלכם</p>
                </div>
                <div class="idea-card">
                    <div class="idea-icon">📐</div>
                    <h4>כלי לימודי</h4>
                    <p>תרגול מתמטיקה, אנגלית, או כל נושא עם מעקב התקדמות</p>
                </div>
            </div>
        </section>

        <div class="sep"></div>

        <!-- === PART 3: THE FORM === -->
        <form id="projectForm">

            <!-- Student Info -->
            <section class="section">
                <div class="section-header">
                    <div class="section-number">01</div>
                    <h2 class="section-title">פרטים אישיים</h2>
                </div>
                <div class="card">
                    <div class="form-group">
                        <label><span class="required">*</span> שם מלא</label>
                        <input type="text" name="fullName" placeholder="השם שלכם" required>
                    </div>
                    <div class="form-group">
                        <label>תאריך מילוי</label>
                        <input type="date" name="fillDate">
                    </div>
                    <div class="form-group">
                        <label><span class="required">*</span> עבודה בזוגות?</label>
                        <div class="radio-group">
                            <div class="radio-option">
                                <input type="radio" name="teamwork" id="solo" value="solo" checked>
                                <label for="solo">עבודה עצמאית</label>
                            </div>
                            <div class="radio-option">
                                <input type="radio" name="teamwork" id="pair" value="pair">
                                <label for="pair">עבודה בזוגות</label>
                            </div>
                        </div>
                        <div class="partner-field" id="partnerField">
                            <input type="text" name="partnerName" placeholder="שם השותף/ה">
                        </div>
                    </div>
                </div>
            </section>

            <!-- The Big Idea -->
            <section class="section">
                <div class="section-header">
                    <div class="section-number">02</div>
                    <h2 class="section-title">הרעיון הגדול</h2>
                </div>
                <div class="card">
                    <div class="form-group">
                        <label><span class="required">*</span> שם הפרויקט
                            <span class="label-hint">שם עבודה, אפשר לשנות בהמשך</span>
                        </label>
                        <input type="text" name="projectName" placeholder='לדוגמה: "QuizMaster" או "מנהל המשימות שלי"' required>
                    </div>
                    <div class="form-group">
                        <label><span class="required">*</span> תארו במשפט אחד — מה הפרויקט עושה?</label>
                        <input type="text" name="oneliner" placeholder='לדוגמה: "אתר שמאפשר לתלמידים ליצור חידונים ולשתף אותם עם חברים"' required>
                    </div>
                    <div class="form-group">
                        <label><span class="required">*</span> למי הפרויקט מיועד? (קהל היעד)</label>
                        <input type="text" name="audience" placeholder='לדוגמה: "תלמידי תיכון שרוצים לתרגל לבגרות"' required>
                    </div>
                    <div class="form-group">
                        <label><span class="required">*</span> איזו בעיה הפרויקט פותר? למה מישהו ירצה להשתמש בו?</label>
                        <textarea name="problem" placeholder="הסבירו מה הצורך שהפרויקט בא לענות עליו..." required></textarea>
                    </div>
                </div>
            </section>

            <!-- Features -->
            <section class="section">
                <div class="section-header">
                    <div class="section-number">03</div>
                    <h2 class="section-title">פיצ'רים ויכולות</h2>
                </div>
                <div class="card">
                    <div class="form-group">
                        <label><span class="required">*</span> רשמו לפחות 3 פיצ'רים מרכזיים שהפרויקט יכלול
                            <span class="label-hint">לדוגמה: 1. הרשמה והתחברות 2. יצירת חידון חדש 3. פתרון חידון וקבלת ציון 4. טבלת מובילים</span>
                        </label>
                        <textarea name="features" rows="6" placeholder="1. &#10;2. &#10;3. &#10;4. " required></textarea>
                    </div>
                </div>
            </section>

            <!-- Tech Usage -->
            <section class="section">
                <div class="section-header">
                    <div class="section-number">04</div>
                    <h2 class="section-title">שימוש בטכנולוגיות</h2>
                </div>
                <div class="card">
                    <div class="form-group">
                        <label><span class="required">*</span> אילו עמודים / מסכים יהיו באתר?</label>
                        <textarea name="pages" placeholder='לדוגמה: דף הבית, דף התחברות, דף יצירת חידון, דף פתרון חידון, דף תוצאות' required></textarea>
                    </div>

                    <div class="form-group">
                        <label><span class="required">*</span> באילו יכולות Firebase תשתמשו? (לפחות אחת)</label>
                        <div class="checkbox-group">
                            <div class="checkbox-option firebase-check">
                                <input type="checkbox" name="firebase_auth" id="fb_auth" value="auth">
                                <label for="fb_auth">🔐 Authentication</label>
                            </div>
                            <div class="checkbox-option firebase-check">
                                <input type="checkbox" name="firebase_firestore" id="fb_firestore" value="firestore">
                                <label for="fb_firestore">🗄️ Firestore</label>
                            </div>
                            <div class="checkbox-option firebase-check">
                                <input type="checkbox" name="firebase_storage" id="fb_storage" value="storage">
                                <label for="fb_storage">📁 Storage</label>
                            </div>
                            <div class="checkbox-option firebase-check">
                                <input type="checkbox" name="firebase_hosting" id="fb_hosting" value="hosting">
                                <label for="fb_hosting">🌐 Hosting</label>
                            </div>
                        </div>
                    </div>

                    <div class="form-group">
                        <label>אם בחרתם Firestore — איזה מידע תשמרו?</label>
                        <input type="text" name="dataTypes" placeholder='לדוגמה: "פרטי משתמשים, שאלות של חידונים, ציונים, תגובות"'>
                    </div>
                </div>
            </section>

            <!-- Design -->
            <section class="section">
                <div class="section-header">
                    <div class="section-number">05</div>
                    <h2 class="section-title">עיצוב ומראה</h2>
                </div>
                <div class="card">
                    <div class="form-group">
                        <label>תארו איך תרצו שהאתר ייראה</label>
                        <textarea name="design" placeholder='לדוגמה: "עיצוב נקי ומודרני, צבעים כהים, בהשראת Discord"'></textarea>
                    </div>

                    <div class="info-box tip" style="margin-top: 1rem;">
                        <div class="info-label">💡 טיפ לסקיצה</div>
                        <p>צרפו ב-repo קובץ תמונה עם סקיצה (שרטוט ביד או דיגיטלי) של <strong>לפחות 2 מסכים מרכזיים</strong>. הסקיצה לא צריכה להיות יפה — היא צריכה להיות ברורה. צרו ריבוע, חלקו לאזורים, וכתבו מה יהיה בכל אזור.</p>
                    </div>
                </div>
            </section>

            <!-- Schedule -->
            <section class="section">
                <div class="section-header">
                    <div class="section-number">06</div>
                    <h2 class="section-title">תכנון לו"ז</h2>
                </div>

                <div class="info-box warn" style="margin-bottom: 1rem;">
                    <div class="info-label">⏰ ההגשה ביוני!</div>
                    <p>תכננו את הזמן בחוכמה — עדיף להתחיל בקטן ולהוסיף, מאשר לתכנן גדול ולא לסיים.</p>
                </div>

                <div class="card" style="overflow-x: auto;">
                    <table class="schedule-table">
                        <thead>
                            <tr>
                                <th>תקופה</th>
                                <th>מה אעשה / מה אלמד</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>פברואר — מרץ</td>
                                <td><textarea name="schedule_feb" placeholder="לדוגמה: ללמוד HTML ו-CSS בסיסי, לבנות את מבנה הדפים..."></textarea></td>
                            </tr>
                            <tr>
                                <td>אפריל</td>
                                <td><textarea name="schedule_apr" placeholder="לדוגמה: להוסיף JavaScript ולחבר Firebase..."></textarea></td>
                            </tr>
                            <tr>
                                <td>מאי</td>
                                <td><textarea name="schedule_may" placeholder="לדוגמה: לסיים את כל הפיצ'רים, לתקן באגים, לעצב..."></textarea></td>
                            </tr>
                            <tr>
                                <td>יוני (הגשה)</td>
                                <td><textarea name="schedule_jun" placeholder="לדוגמה: בדיקות אחרונות, תיעוד, הגשה..."></textarea></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </section>

            <!-- Reflections -->
            <section class="section">
                <div class="section-header">
                    <div class="section-number">07</div>
                    <h2 class="section-title">שאלות ואתגרים</h2>
                </div>
                <div class="card">
                    <div class="form-group">
                        <label>מה הדבר שהכי מלהיב אתכם בפרויקט?</label>
                        <textarea name="exciting" placeholder="ספרו לנו..."></textarea>
                    </div>
                    <div class="form-group">
                        <label>מה הדבר שהכי מדאיג אתכם / נראה קשה?</label>
                        <textarea name="concerns" placeholder="אל תתביישו — כולם מרגישים ככה בהתחלה..."></textarea>
                    </div>
                    <div class="form-group">
                        <label>האם יש נושא ספציפי שתרצו שנלמד יחד בכיתה?</label>
                        <textarea name="classRequest" placeholder="לדוגמה: איך עושים התחברות עם Firebase, איך מעצבים טופס..."></textarea>
                    </div>
                </div>
            </section>
        </form>

        <div class="sep"></div>

        <!-- === RESOURCES === -->
        <section class="section">
            <button class="collapsible-trigger" onclick="toggleCollapsible(this)">
                📚 משאבים שימושיים ללמידה עצמית
                <span class="arrow">▼</span>
            </button>
            <div class="collapsible-content">
                <div class="info-box tip" style="margin-top: 0.5rem;">
                    <div class="info-label">🎓 לא צריך ללמוד הכל לבד! נלמד יחד בכיתה</div>
                </div>
                <div class="resources-list">
                    <a href="https://www.freecodecamp.org/" target="_blank" class="resource-link">
                        <span class="r-icon">🌐</span>
                        <div>
                            <strong>freeCodeCamp.org</strong>
                            <div class="r-desc">HTML & CSS — חינמי, אינטראקטיבי, באנגלית פשוטה</div>
                        </div>
                    </a>
                    <a href="https://javascript.info/" target="_blank" class="resource-link">
                        <span class="r-icon">📘</span>
                        <div>
                            <strong>javascript.info</strong>
                            <div class="r-desc">JavaScript — מדריך מקיף ומסודר</div>
                        </div>
                    </a>
                    <a href="https://firebase.google.com/docs" target="_blank" class="resource-link">
                        <span class="r-icon">🔥</span>
                        <div>
                            <strong>Firebase Docs</strong>
                            <div class="r-desc">התיעוד הרשמי של Google — מדריכים ודוגמאות</div>
                        </div>
                    </a>
                    <a href="https://www.youtube.com/results?search_query=HTML+CSS+%D7%A7%D7%95%D7%A8%D7%A1+%D7%A2%D7%91%D7%A8%D7%99%D7%AA" target="_blank" class="resource-link">
                        <span class="r-icon">🎥</span>
                        <div>
                            <strong>YouTube בעברית</strong>
                            <div class="r-desc">חפשו "קורס HTML" או "Firebase tutorial Hebrew"</div>
                        </div>
                    </a>
                    <a href="https://claude.ai" target="_blank" class="resource-link">
                        <span class="r-icon">🤖</span>
                        <div>
                            <strong>Claude / ChatGPT</strong>
                            <div class="r-desc">אל תתביישו לשאול AI שאלות! זה כלי לגיטימי ללמידה</div>
                        </div>
                    </a>
                </div>
            </div>
        </section>

        <div class="sep"></div>

        <!-- === CHECKLIST === -->
        <section class="section">
            <div class="section-header">
                <div class="section-number">✓</div>
                <h2 class="section-title">רשימת בדיקה לפני הגשה</h2>
            </div>
            <div class="card">
                <ul class="checklist">
                    <li><input type="checkbox"><span>מילאתי את כל השדות המסומנים ב-<span style="color:var(--red)">*</span></span></li>
                    <li><input type="checkbox"><span>הפרויקט שלי כולל HTML, CSS, JavaScript ו-Firebase</span></li>
                    <li><input type="checkbox"><span>סימנתי לפחות יכולת Firebase אחת</span></li>
                    <li><input type="checkbox"><span>רשמתי לפחות 3 פיצ'רים</span></li>
                    <li><input type="checkbox"><span>צירפתי סקיצה של לפחות 2 מסכים (קובץ תמונה ב-repo)</span></li>
                    <li><input type="checkbox"><span>מילאתי את טבלת לוח הזמנים</span></li>
                </ul>
            </div>
        </section>

        <!-- BUTTONS -->
        <div class="print-bar">
            <button class="btn btn-primary" onclick="window.print()">🖨️ הדפסה</button>
            <button class="btn btn-secondary" onclick="exportMarkdown()">📋 ייצוא ל-Markdown</button>
            <label class="btn btn-secondary" style="margin:0;cursor:pointer;">
                📂 טעינת Markdown
                <input type="file" accept=".md,.markdown,.txt" onchange="loadMarkdown(event)" style="display:none;">
            </label>
        </div>

        <!-- FOOTER -->
        <footer class="footer">
            <p>בהצלחה! אנחנו כאן לעזור בכל שלב 🚀</p>
            <p style="margin-top: 0.5rem;">מגמת מדעי המחשב · אלוני יצחק · <span class="heart">♥</span></p>
        </footer>

    </div>

    <script>
        // Partner field toggle
        document.querySelectorAll('input[name="teamwork"]').forEach(radio => {
            radio.addEventListener('change', () => {
                const field = document.getElementById('partnerField');
                field.classList.toggle('visible', document.getElementById('pair').checked);
            });
        });

        // Collapsible sections
        function toggleCollapsible(trigger) {
            trigger.classList.toggle('open');
            const content = trigger.nextElementSibling;
            content.classList.toggle('open');
        }

        // Progress bar based on filled fields
        function updateProgress() {
            const form = document.getElementById('projectForm');
            const requiredFields = form.querySelectorAll('[required]');
            let filled = 0;
            requiredFields.forEach(f => {
                if (f.value.trim()) filled++;
            });
            const pct = requiredFields.length ? (filled / requiredFields.length) * 100 : 0;
            document.getElementById('progressFill').style.width = pct + '%';
        }

        document.querySelectorAll('input, textarea').forEach(el => {
            el.addEventListener('input', updateProgress);
        });

        // Export to Markdown
        function exportMarkdown() {
            const form = document.getElementById('projectForm');
            const fd = new FormData(form);

            const firebaseChoices = [];
            if (document.getElementById('fb_auth').checked) firebaseChoices.push('Authentication');
            if (document.getElementById('fb_firestore').checked) firebaseChoices.push('Firestore');
            if (document.getElementById('fb_storage').checked) firebaseChoices.push('Storage');
            if (document.getElementById('fb_hosting').checked) firebaseChoices.push('Hosting');

            const md = `# הגדרת פרויקט גמר — מדעי המחשב

## פרטים אישיים
- **שם:** ${fd.get('fullName') || '___'}
- **תאריך:** ${fd.get('fillDate') || '___'}
- **עבודה:** ${fd.get('teamwork') === 'pair' ? 'בזוגות — ' + (fd.get('partnerName') || '___') : 'עצמאית'}

## הרעיון הגדול
- **שם הפרויקט:** ${fd.get('projectName') || '___'}
- **תיאור:** ${fd.get('oneliner') || '___'}
- **קהל יעד:** ${fd.get('audience') || '___'}
- **בעיה שנפתרת:** ${fd.get('problem') || '___'}

## פיצ'רים
${fd.get('features') || '___'}

## שימוש בטכנולוגיות
- **עמודים / מסכים:** ${fd.get('pages') || '___'}
- **Firebase:** ${firebaseChoices.join(', ') || 'לא נבחר'}
- **סוגי נתונים:** ${fd.get('dataTypes') || '___'}

## עיצוב
${fd.get('design') || '___'}

## לו"ז
| תקופה | תוכנית |
|--------|--------|
| פברואר–מרץ | ${fd.get('schedule_feb') || '___'} |
| אפריל | ${fd.get('schedule_apr') || '___'} |
| מאי | ${fd.get('schedule_may') || '___'} |
| יוני | ${fd.get('schedule_jun') || '___'} |

## שאלות ואתגרים
- **מלהיב:** ${fd.get('exciting') || '___'}
- **מדאיג:** ${fd.get('concerns') || '___'}
- **בקשה ללמידה בכיתה:** ${fd.get('classRequest') || '___'}
`;

            const blob = new Blob([md], { type: 'text/markdown; charset=utf-8' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `project-definition-${fd.get('fullName') || 'student'}.md`.replace(/\s+/g, '-');
            a.click();
            URL.revokeObjectURL(url);
        }

        // Load Markdown back into the form
        function loadMarkdown(event) {
            const file = event.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function(e) {
                const text = e.target.result;

                try {
                    // Helper: extract value after a bold label pattern "- **Label:** value"
                    function extract(label) {
                        const escaped = label.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
                        const re = new RegExp(`\\*\\*${escaped}:\\*\\*\\s*(.+)`, 'm');
                        const m = text.match(re);
                        return m ? m[1].trim() : '';
                    }

                    // Helper: extract a section block between two ## headings
                    function extractSection(heading) {
                        const escaped = heading.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
                        const re = new RegExp(`## ${escaped}\\n([\\s\\S]*?)(?=\\n## |$)`, 'm');
                        const m = text.match(re);
                        return m ? m[1].trim() : '';
                    }

                    // Helper: extract table cell value for a row
                    function extractTableRow(rowLabel) {
                        const escaped = rowLabel.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
                        const re = new RegExp(`\\|\\s*${escaped}\\s*\\|\\s*(.+?)\\s*\\|`, 'm');
                        const m = text.match(re);
                        return m ? m[1].trim() : '';
                    }

                    // Set simple fields
                    const setValue = (name, val) => {
                        if (!val || val === '___') return;
                        const el = document.querySelector(`[name="${name}"]`);
                        if (el) { el.value = val; }
                    };

                    setValue('fullName', extract('שם'));
                    setValue('fillDate', extract('תאריך'));
                    setValue('projectName', extract('שם הפרויקט'));
                    setValue('oneliner', extract('תיאור'));
                    setValue('audience', extract('קהל יעד'));
                    setValue('problem', extract('בעיה שנפתרת'));
                    setValue('pages', extract('עמודים / מסכים'));
                    setValue('dataTypes', extract('סוגי נתונים'));
                    setValue('exciting', extract('מלהיב'));
                    setValue('concerns', extract('מדאיג'));
                    setValue('classRequest', extract('בקשה ללמידה בכיתה'));

                    // Teamwork
                    const workVal = extract('עבודה');
                    if (workVal && workVal.startsWith('בזוגות')) {
                        document.getElementById('pair').checked = true;
                        document.getElementById('partnerField').classList.add('visible');
                        const partnerMatch = workVal.match(/בזוגות\s*—\s*(.+)/);
                        if (partnerMatch && partnerMatch[1] !== '___') {
                            setValue('partnerName', partnerMatch[1].trim());
                        }
                    } else {
                        document.getElementById('solo').checked = true;
                        document.getElementById('partnerField').classList.remove('visible');
                    }

                    // Features section (raw block, skip the "- **" lines)
                    const featuresSection = extractSection('פיצ\'רים');
                    if (featuresSection && featuresSection !== '___') {
                        setValue('features', featuresSection);
                    }

                    // Design section
                    const designSection = extractSection('עיצוב');
                    if (designSection && designSection !== '___') {
                        setValue('design', designSection);
                    }

                    // Firebase checkboxes
                    const fbVal = extract('Firebase');
                    if (fbVal && fbVal !== 'לא נבחר') {
                        document.getElementById('fb_auth').checked = fbVal.includes('Authentication');
                        document.getElementById('fb_firestore').checked = fbVal.includes('Firestore');
                        document.getElementById('fb_storage').checked = fbVal.includes('Storage');
                        document.getElementById('fb_hosting').checked = fbVal.includes('Hosting');
                        // Update checkbox visual state
                        document.querySelectorAll('.firebase-check input').forEach(cb => {
                            cb.dispatchEvent(new Event('change'));
                        });
                    }

                    // Schedule table
                    const scheduleVal = (label) => {
                        const v = extractTableRow(label);
                        return (v && v !== '___') ? v : '';
                    };
                    setValue('schedule_feb', scheduleVal('פברואר–מרץ'));
                    setValue('schedule_apr', scheduleVal('אפריל'));
                    setValue('schedule_may', scheduleVal('מאי'));
                    setValue('schedule_jun', scheduleVal('יוני'));

                    updateProgress();
                    showToast('✅ הטופס נטען בהצלחה!');
                } catch (err) {
                    console.error('Parse error:', err);
                    showToast('❌ שגיאה בטעינת הקובץ', true);
                }
            };
            reader.readAsText(file);
            // Reset file input so same file can be loaded again
            event.target.value = '';
        }

        // Toast notification
        function showToast(message, isError) {
            let toast = document.getElementById('toast');
            if (!toast) {
                toast = document.createElement('div');
                toast.id = 'toast';
                toast.style.cssText = `
                    position: fixed; bottom: 2rem; left: 50%; transform: translateX(-50%) translateY(100px);
                    padding: 0.8rem 1.5rem; border-radius: 10px; font-family: 'Heebo', sans-serif;
                    font-size: 0.95rem; font-weight: 600; z-index: 1000;
                    transition: transform 0.4s cubic-bezier(0.34, 1.56, 0.64, 1), opacity 0.4s;
                    opacity: 0; pointer-events: none;
                `;
                document.body.appendChild(toast);
            }
            toast.textContent = message;
            toast.style.background = isError ? 'var(--red)' : 'var(--accent)';
            toast.style.color = 'white';
            toast.style.boxShadow = isError
                ? '0 4px 20px rgba(239,68,68,0.4)'
                : '0 4px 20px rgba(99,102,241,0.4)';

            requestAnimationFrame(() => {
                toast.style.transform = 'translateX(-50%) translateY(0)';
                toast.style.opacity = '1';
            });

            setTimeout(() => {
                toast.style.transform = 'translateX(-50%) translateY(100px)';
                toast.style.opacity = '0';
            }, 2500);
        }

        // Initialize
        updateProgress();
    </script>
</body>
</html>
