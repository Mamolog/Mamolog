Просто почини код и сделай его лучше но ни вкоем случае не порть его функционал не порть его объм Ты можешь внести туда что то новое но не портить !!
<!DOCTYPE html>
<html lang="ru" data-theme="light">
<head>
  <meta charset="UTF-8" />
  <title>ADVICE · Бот-психолог в Telegram</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="color-scheme" content="light dark" />
  <meta name="theme-color" content="#050509" />

  <!-- Шрифты: максимально близко к Proxima Nova + выразительный дисплей -->
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Grotesk:wght@500;700&display=swap" rel="stylesheet" />

  <style>
    /* ------------------------------
       RESET / BASE
    ------------------------------ */

    *, *::before, *::after {
      box-sizing: border-box;
    }

    html, body {
      margin: 0;
      padding: 0;
    }

    body {
      min-height: 100vh;
      font-family: var(--font-sans);
      background: var(--color-bg-app);
      color: var(--color-text-main);
      -webkit-font-smoothing: antialiased;
      text-rendering: optimizeLegibility;
    }

    img {
      max-width: 100%;
      display: block;
    }

    button {
      font-family: inherit;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    :root {
      /* ---------- Типографика ---------- */
      --font-sans: -apple-system, BlinkMacSystemFont, "SF Pro Text", "Inter", system-ui, sans-serif;
      --font-display: "Space Grotesk", -apple-system, BlinkMacSystemFont, "SF Pro Display", system-ui, sans-serif;

      /* ---------- Цвета: светлая тема (по умолчанию) ---------- */
      --color-bg-app: #f6f6f8;
      --color-bg-elevated: #ffffff;
      --color-bg-soft: #f0f0f4;

      --color-phone-shell: #050509;
      --color-phone-screen: #0b0b11;

      --color-text-main: #050509;
      --color-text-soft: #666677;
      --color-text-softer: #9a9aac;
      --color-text-inverse: #f5f5ff;

      --color-accent: #1111ff;
      --color-accent-soft: rgba(17, 17, 255, 0.08);
      --color-accent-strong: #0000d0;

      --color-danger: #ff3366;
      --color-success: #22c55e;
      --color-warning: #ffaa33;

      --color-border-subtle: rgba(5, 5, 9, 0.06);
      --color-border-strong: rgba(5, 5, 9, 0.16);

      --color-chip-bg: rgba(5, 5, 9, 0.04);
      --color-chip-border: rgba(5, 5, 9, 0.08);

      --color-gradient-hero: radial-gradient(circle at 0% -40%, rgba(17, 17, 255, 0.16), transparent 60%),
                              radial-gradient(circle at 120% 140%, rgba(255, 51, 102, 0.14), transparent 50%);

      --color-shadow-soft: 0 18px 40px rgba(15, 15, 40, 0.18);
      --color-shadow-phone: 0 25px 70px rgba(5, 5, 20, 0.55);

      /* ---------- Размеры ---------- */
      --radius-xs: 8px;
      --radius-s: 12px;
      --radius-m: 18px;
      --radius-l: 24px;
      --radius-xl: 32px;
      --radius-2xl: 40px;
      --radius-pill: 999px;

      --space-2xs: 4px;
      --space-xs: 8px;
      --space-s: 12px;
      --space-m: 16px;
      --space-l: 24px;
      --space-xl: 32px;
      --space-2xl: 40px;
      --space-3xl: 56px;

      --header-height: 72px;
      --content-max-width: 1120px;

      /* ---------- Motion / анимации ---------- */
      --motion-fast: 140ms;
      --motion-normal: 220ms;
      --motion-slow: 380ms;

      --easing-standard: cubic-bezier(0.2, 0.7, 0.2, 1);
      --easing-soft: cubic-bezier(0.16, 0.84, 0.44, 1);
      --easing-overshoot: cubic-bezier(0.2, 1.4, 0.2, 1);

      /* ---------- Z-index слои ---------- */
      --z-header: 20;
      --z-theme-toggle: 30;
      --z-phone: 5;
      --z-phone-glow: 2;
      --z-overlay: 100;
      --z-toast: 120;
    }

    /* ---------- ТЁМНАЯ ТЕМА ---------- */

    html[data-theme="dark"] {
      --color-bg-app: #050509;
      --color-bg-elevated: #0c0c14;
      --color-bg-soft: #131320;

      --color-phone-shell: #f3f3fb;
      --color-phone-screen: #050509;

      --color-text-main: #f4f4ff;
      --color-text-soft: #b1b1c6;
      --color-text-softer: #77778a;
      --color-text-inverse: #050509;

      --color-accent: #7f7fff;
      --color-accent-soft: rgba(127, 127, 255, 0.16);
      --color-accent-strong: #a5a5ff;

      --color-danger: #ff6b8c;
      --color-success: #4ade80;
      --color-warning: #ffbf69;

      --color-border-subtle: rgba(255, 255, 255, 0.08);
      --color-border-strong: rgba(255, 255, 255, 0.16);

      --color-chip-bg: rgba(255, 255, 255, 0.04);
      --color-chip-border: rgba(255, 255, 255, 0.08);

      --color-gradient-hero: radial-gradient(circle at 0% -40%, rgba(127, 127, 255, 0.32), transparent 60%),
                              radial-gradient(circle at 120% 140%, rgba(255, 107, 140, 0.32), transparent 50%);

      --color-shadow-soft: 0 26px 60px rgba(0, 0, 0, 0.9);
      --color-shadow-phone: 0 32px 90px rgba(0, 0, 0, 0.95);
    }

    /* ------------------------------
       KEYFRAMES
    ------------------------------ */

    @keyframes fadeInSoft {
      from {
        opacity: 0;
        transform: translateY(8px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes fadeInUpBig {
      from {
        opacity: 0;
        transform: translateY(24px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes phoneFloat {
      0% {
        transform: translate3d(0, 0, 0) rotate3d(0, 1, 0, -6deg) rotate3d(1, 0, 0, 8deg);
      }
      50% {
        transform: translate3d(0, -8px, 0) rotate3d(0, 1, 0, -2deg) rotate3d(1, 0, 0, 4deg);
      }
      100% {
        transform: translate3d(0, 0, 0) rotate3d(0, 1, 0, -6deg) rotate3d(1, 0, 0, 8deg);
      }
    }

    @keyframes scaleInOvershoot {
      0% {
        opacity: 0;
        transform: scale(0.88);
      }
      60% {
        opacity: 1;
        transform: scale(1.03);
      }
      100% {
        opacity: 1;
        transform: scale(1);
      }
    }

    @keyframes chipPulse {
      0% {
        box-shadow: 0 0 0 0 rgba(17, 17, 255, 0.35);
      }
      80% {
        box-shadow: 0 0 0 18px rgba(17, 17, 255, 0);
      }
      100% {
        box-shadow: 0 0 0 0 rgba(17, 17, 255, 0);
      }
    }

    @keyframes sectionReveal {
      0% {
        opacity: 0;
        transform: translateY(32px) scale(0.98);
        filter: blur(6px);
      }
      100% {
        opacity: 1;
        transform: translateY(0) scale(1);
        filter: blur(0);
      }
    }

    @keyframes gradientShift {
      0% {
        background-position: 0% 0%;
      }
      50% {
        background-position: 100% 50%;
      }
      100% {
        background-position: 0% 0%;
      }
    }

    /* ------------------------------
       LAYOUT / PAGE SHELL
    ------------------------------ */

    .l-page {
      min-height: 100vh;
      background: radial-gradient(circle at top, rgba(255, 255, 255, 0.18), transparent 60%), var(--color-bg-app);
      background-image: var(--color-gradient-hero);
      background-size: 200% 200%;
      animation: gradientShift 22s ease-in-out infinite alternate;
    }

    .l-page-inner {
      max-width: var(--content-max-width);
      margin: 0 auto;
      padding: var(--space-l) var(--space-m) var(--space-3xl);
    }

    @media (min-width: 960px) {
      .l-page-inner {
        padding-top: var(--space-2xl);
        padding-bottom: var(--space-3xl);
      }
    }

    .l-header {
      position: sticky;
      top: 0;
      z-index: var(--z-header);
      backdrop-filter: blur(18px);
      background: linear-gradient(to bottom,
        color-mix(in srgb, var(--color-bg-app) 88%, transparent),
        color-mix(in srgb, var(--color-bg-app) 72%, transparent)
      );
      border-bottom: 1px solid var(--color-border-subtle);
    }

    .l-header-inner {
      max-width: var(--content-max-width);
      margin: 0 auto;
      padding: 10px var(--space-m);
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: var(--space-m);
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .brand-mark {
      width: 28px;
      height: 28px;
      border-radius: 10px;
      background: radial-gradient(circle at 0% 0%, #ffffff, #d0d0ff 38%, #0000d8 100%);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      color: #050509;
      font-weight: 800;
      font-family: var(--font-display);
      font-size: 14px;
      letter-spacing: 0.06em;
      box-shadow: 0 10px 25px rgba(0, 0, 40, 0.45);
    }

    html[data-theme="dark"] .brand-mark {
      background: radial-gradient(circle at 0% 0%, #ffffff, #a5a5ff 36%, #1b1bff 100%);
      color: #050509;
    }

    .brand-text-main {
      font-family: var(--font-display);
      font-size: 17px;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
    }

    .brand-text-sub {
      font-size: 11px;
      color: var(--color-text-soft);
      margin-top: 2px;
    }

    .header-right {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .header-pill {
      padding: 4px 10px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-elevated) 80%, transparent);
      font-size: 11px;
      color: var(--color-text-soft);
      display: inline-flex;
      align-items: center;
      gap: 6px;
      white-space: nowrap;
    }

    .header-pill-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: radial-gradient(circle at 0% 0%, #ffffff, var(--color-accent-strong));
      box-shadow: 0 0 0 4px rgba(17, 17, 255, 0.15);
    }

    .header-pill-label {
      font-weight: 500;
    }

    /* ------------------------------
       THEME TOGGLE (Солнце / Луна)
    ------------------------------ */

    .theme-toggle {
      position: relative;
      width: 46px;
      height: 24px;
      border-radius: 999px;
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-soft) 70%, transparent);
      display: inline-flex;
      align-items: center;
      padding: 2px;
      cursor: pointer;
      transition:
        background var(--motion-normal) var(--easing-standard),
        border-color var(--motion-normal) var(--easing-standard);
    }

    .theme-toggle-knob {
      width: 18px;
      height: 18px;
      border-radius: 999px;
      background: #ffffff;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.22);
      display: flex;
      align-items: center;
      justify-content: center;
      transform: translateX(0);
      transition:
        transform var(--motion-normal) var(--easing-soft),
        background var(--motion-normal) var(--easing-soft);
      color: #f4b000;
      font-size: 11px;
    }

    .theme-toggle-rail {
      position: absolute;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 3px 6px;
      pointer-events: none;
      font-size: 9px;
      color: var(--color-text-softer);
    }

    .theme-toggle-icon {
      opacity: 0.65;
      transition: opacity var(--motion-normal) var(--easing-standard), transform var(--motion-normal) var(--easing-standard);
    }

    .theme-toggle-icon.sun {
      transform-origin: left center;
    }

    .theme-toggle-icon.moon {
      transform-origin: right center;
    }

    html[data-theme="dark"] .theme-toggle-knob {
      transform: translateX(20px);
      background: #050509;
      color: #f9f9ff;
    }

    html[data-theme="dark"] .theme-toggle {
      background: radial-gradient(circle at 0 0, #202047, #050509);
      border-color: rgba(255, 255, 255, 0.16);
    }

    html[data-theme="dark"] .theme-toggle-icon.sun {
      opacity: 0.3;
      transform: scale(0.85);
    }

    html[data-theme="dark"] .theme-toggle-icon.moon {
      opacity: 0.9;
      transform: scale(1.1);
    }

    /* ------------------------------
       УТИЛИТЫ
    ------------------------------ */

    .u-kbd {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 2px 6px;
      border-radius: 6px;
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-elevated) 90%, transparent);
      font-size: 10px;
      font-family: var(--font-sans);
    }

    .u-pill-soft {
      border-radius: var(--radius-pill);
      padding: 4px 10px;
      font-size: 11px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      color: var(--color-text-soft);
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .u-pill-soft strong {
      font-weight: 600;
      color: var(--color-text-main);
    }

    .u-eyebrow {
      font-size: 11px;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--color-text-soft);
      font-weight: 600;
    }

    .u-h1 {
      font-family: var(--font-display);
      font-size: clamp(28px, 5vw, 40px);
      line-height: 1.1;
      letter-spacing: 0.03em;
      margin: 0;
    }

    .u-h2 {
      font-family: var(--font-display);
      font-size: clamp(20px, 3vw, 26px);
      line-height: 1.15;
      margin: 0;
    }

    .u-body-main {
      font-size: 14px;
      line-height: 1.6;
      color: var(--color-text-soft);
    }

    .u-body-small {
      font-size: 12px;
      line-height: 1.5;
      color: var(--color-text-softer);
    }

    .u-section {
      padding-top: var(--space-2xl);
      padding-bottom: var(--space-2xl);
    }

    .u-section:first-of-type {
      padding-top: var(--space-xl);
    }

    @media (min-width: 960px) {
      .u-section {
        padding-top: var(--space-3xl);
        padding-bottom: var(--space-3xl);
      }
    }

    .u-section-header {
      margin-bottom: var(--space-l);
      animation: fadeInSoft var(--motion-slow) var(--easing-soft) both;
    }

    .u-grid-hero {
      display: grid;
      grid-template-columns: minmax(0, 1.1fr);
      gap: var(--space-xl);
      align-items: center;
    }

    @media (min-width: 960px) {
      .u-grid-hero {
        grid-template-columns: minmax(0, 1.1fr) minmax(0, 0.95fr);
      }
    }

    .u-reveal {
      opacity: 0;
      transform: translateY(24px);
      filter: blur(6px);
      transition:
        opacity var(--motion-slow) var(--easing-soft),
        transform var(--motion-slow) var(--easing-soft),
        filter var(--motion-slow) var(--easing-soft);
    }

    .u-reveal.is-visible {
      opacity: 1;
      transform: translateY(0);
      filter: blur(0);
    }

    /* ------------------------------
       КОМПОНЕНТЫ: КНОПКИ / КАРТОЧКИ
    ------------------------------ */

    .c-button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      border-radius: var(--radius-pill);
      border: 1px solid transparent;
      padding: 10px 18px;
      font-size: 13px;
      font-weight: 600;
      letter-spacing: 0.02em;
      cursor: pointer;
      outline: none;
      background: var(--color-accent);
      color: #ffffff;
      box-shadow: 0 14px 30px rgba(0, 0, 60, 0.45);
      transform: translateY(0);
      transition:
        box-shadow var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard),
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        color var(--motion-fast) var(--easing-standard);
    }

    .c-button span {
      display: inline-flex;
      align-items: center;
      justify-content: center;
    }

    .c-button-icon {
      font-size: 15px;
      line-height: 1;
    }

    .c-button:hover {
      transform: translateY(-1px);
      box-shadow: 0 18px 40px rgba(0, 0, 60, 0.55);
      background: var(--color-accent-strong);
    }

    .c-button:active {
      transform: translateY(0);
      box-shadow: 0 8px 22px rgba(0, 0, 40, 0.6);
    }

    .c-button--ghost {
      background: transparent;
      color: var(--color-text-main);
      border-color: var(--color-border-subtle);
      box-shadow: none;
    }

    .c-button--ghost:hover {
      background: var(--color-chip-bg);
      border-color: var(--color-border-strong);
      box-shadow: none;
    }

    .c-button--secondary {
      background: var(--color-chip-bg);
      border-color: var(--color-chip-border);
      color: var(--color-text-main);
      box-shadow: none;
    }

    .c-button--secondary:hover {
      background: color-mix(in srgb, var(--color-chip-bg) 70%, var(--color-accent-soft));
      border-color: var(--color-border-strong);
    }

    .c-button--sm {
      padding: 7px 14px;
      font-size: 12px;
    }

    .c-card {
      position: relative;
      border-radius: var(--radius-xl);
      background: color-mix(in srgb, var(--color-bg-elevated) 94%, transparent);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--color-shadow-soft);
      padding: var(--space-l);
      overflow: hidden;
    }

    html[data-theme="dark"] .c-card {
      background: radial-gradient(circle at 0 0, rgba(127, 127, 255, 0.16), transparent 70%), var(--color-bg-elevated);
    }

    .c-card--soft {
      border-radius: var(--radius-l);
      padding: var(--space-m);
      box-shadow: none;
      background: color-mix(in srgb, var(--color-bg-elevated) 88%, transparent);
    }

    .c-badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      border-radius: var(--radius-pill);
      padding: 4px 10px;
      font-size: 11px;
      background: var(--color-accent-soft);
      color: var(--color-accent-strong);
    }

    .c-badge-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: radial-gradient(circle at 0 0, #ffffff, var(--color-accent-strong));
    }

    .c-chip {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      border-radius: var(--radius-pill);
      padding: 6px 12px;
      font-size: 12px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      color: var(--color-text-soft);
      cursor: pointer;
      transition:
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        color var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard);
    }

    .c-chip:hover {
      transform: translateY(-1px);
      border-color: var(--color-border-strong);
      color: var(--color-text-main);
    }

    .c-chip--active {
      background: var(--color-accent);
      border-color: var(--color-accent);
      color: #ffffff;
      box-shadow: 0 0 0 0 rgba(17, 17, 255, 0.4);
      animation: chipPulse 2.2s var(--easing-soft) infinite;
    }

    .c-chip-group {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    /* ------------------------------
       ПОДГОТОВКА ПОД HERO + IPHONE
       (разметка пойдёт в ЧАСТИ 2/5)
    ------------------------------ */

    .hero {
      position: relative;
      display: grid;
      grid-template-columns: minmax(0, 1.05fr);
      gap: var(--space-xl);
      align-items: center;
      margin-top: var(--space-xl);
      animation: fadeInUpBig 520ms var(--easing-soft) both;
    }

    @media (min-width: 960px) {
      .hero {
        grid-template-columns: minmax(0, 1.05fr) minmax(0, 0.95fr);
      }
    }

    .hero-copy {
      display: flex;
      flex-direction: column;
      gap: var(--space-m);
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
      margin-top: 6px;
    }

    .hero-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: var(--space-s);
    }

    /* ---------- Плейсхолдеры под будущие секции (будем наполнять далее) ---------- */

    .section-placeholder {
      border-radius: var(--radius-xl);
      border: 1px dashed color-mix(in srgb, var(--color-border-subtle) 90%, transparent);
      padding: var(--space-xl);
      text-align: center;
      font-size: 13px;
      color: var(--color-text-softer);
      margin-top: var(--space-xl);
    }
  </style>
</head>
<body class="l-page">
  <header class="l-header">
    <div class="l-header-inner">
      <div class="brand">
        <div class="brand-mark">A</div>
        <div>
          <div class="brand-text-main">ADVICE</div>
          <div class="brand-text-sub">бот-психолог внутри Telegram</div>
        </div>
      </div>
      <div class="header-right">
        <div class="header-pill">
          <span class="header-pill-dot"></span>
          <span class="header-pill-label">Работает в Telegram</span>
        </div>
        <button class="theme-toggle" type="button" id="theme-toggle">
          <div class="theme-toggle-rail">
            <span class="theme-toggle-icon sun">☀️</span>
            <span class="theme-toggle-icon moon">🌙</span>
          </div>
          <div class="theme-toggle-knob" aria-hidden="true">☀️</div>
        </button>
      </div>
    </div>
  </header>

  <main class="l-page-inner">
    <!-- HERO + IPHONE (полноценная разметка и анимации пойдут в ЧАСТИ 2/5) -->
    <section class="u-section hero" id="hero">
      <div class="hero-copy u-reveal js-reveal">
        <div class="u-eyebrow">Твой день в трёх цифрах</div>
        <h1 class="u-h1">
          Бот, с которым удобно говорить о себе
          и не терять опору в повседневности.
        </h1>
        <p class="u-body-main">
          ADVICE живёт прямо в Telegram, задаёт три понятных вопроса про психику, сон и деньги
          и помогает держать под контролем то, что чаще всего «сыпется» в повседневной жизни.
        </p>
        <div class="hero-actions">
          <a href="https://t.me/your_advice_bot" class="c-button">
            <span>Открыть бота в Telegram</span>
            <span class="c-button-icon">↗</span>
          </a>
          <button class="c-button c-button--ghost c-button--sm" type="button">
            <span>Посмотреть, как это работает</span>
          </button>
        </div>
        <div class="hero-meta">
          <div class="u-pill-soft">
            <span>Индекс дня&nbsp;<strong>от 1 до 5</strong></span>
          </div>
          <div class="u-pill-soft">
            <span>Психика · Сон · Деньги</span>
          </div>
        </div>
      </div>

      <!-- Плейсхолдер под iPhone-сцену.
           В ЧАСТИ 2/5 сюда придёт полноценный 3D-подобный телефон с экранами бота. -->
      <div class="section-placeholder u-reveal js-reveal" id="phone-scene-placeholder">
        Здесь появится интерактивный iPhone с интерфейсом бота ADVICE:
        онбординг, чат, индекс дня, модули «Сон» и «Деньги».
      </div>
    </section>

    <!-- Остальные секции (чат-скролл, индекс дня 1–5, кейс, модули, FAQ и т. д.)
         добавим и подробно оформим в следующих частях. -->
  </main>

  <script>
    // ---------------------------
    // THEME ENGINE (light/dark)
    // ---------------------------
    (function () {
      const root = document.documentElement;
      const toggle = document.getElementById('theme-toggle');
      const knob = toggle ? toggle.querySelector('.theme-toggle-knob') : null;

      function applyTheme(theme) {
        root.setAttribute('data-theme', theme);
        try {
          window.localStorage.setItem('advice_landing_theme', theme);
        } catch (e) {}
        if (knob) {
          knob.textContent = theme === 'dark' ? '🌙' : '☀️';
        }
      }

      function initTheme() {
        let saved = null;
        try {
          saved = window.localStorage.getItem('advice_landing_theme');
        } catch (e) {}

        if (saved === 'light' || saved === 'dark') {
          applyTheme(saved);
          return;
        }

        const prefersDark = window.matchMedia &&
          window.matchMedia('(prefers-color-scheme: dark)').matches;
        applyTheme(prefersDark ? 'dark' : 'light');
      }

      if (toggle) {
        toggle.addEventListener('click', () => {
          const current = root.getAttribute('data-theme') || 'light';
          const next = current === 'light' ? 'dark' : 'light';
          applyTheme(next);
        });
      }

      initTheme();
    })();

    // ---------------------------
    // SCROLL REVEAL
    // ---------------------------
    (function () {
      const revealEls = Array.from(document.querySelectorAll('.js-reveal'));

      if (!('IntersectionObserver' in window) || revealEls.length === 0) {
        revealEls.forEach(el => el.classList.add('is-visible'));
        return;
      }

      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('is-visible');
              observer.unobserve(entry.target);
            }
          });
        },
        {
          threshold: 0.18,
        }
      );

      revealEls.forEach((el) => observer.observe(el));
    })();
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="ru" data-theme="light">
<head>
  <meta charset="UTF-8" />
  <title>ADVICE · Бот-психолог в Telegram</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="color-scheme" content="light dark" />
  <meta name="theme-color" content="#050509" />

  <!-- Шрифты: максимально близко к Proxima Nova + выразительный дисплей -->
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Grotesk:wght@500;700&display=swap" rel="stylesheet" />

  <style>
    /* ------------------------------
       RESET / BASE
    ------------------------------ */

    *, *::before, *::after {
      box-sizing: border-box;
    }

    html, body {
      margin: 0;
      padding: 0;
    }

    body {
      min-height: 100vh;
      font-family: var(--font-sans);
      background: var(--color-bg-app);
      color: var(--color-text-main);
      -webkit-font-smoothing: antialiased;
      text-rendering: optimizeLegibility;
    }

    img {
      max-width: 100%;
      display: block;
    }

    button {
      font-family: inherit;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    :root {
      /* ---------- Типографика ---------- */
      --font-sans: -apple-system, BlinkMacSystemFont, "SF Pro Text", "Inter", system-ui, sans-serif;
      --font-display: "Space Grotesk", -apple-system, BlinkMacSystemFont, "SF Pro Display", system-ui, sans-serif;

      /* ---------- Цвета: светлая тема (по умолчанию) ---------- */
      --color-bg-app: #f6f6f8;
      --color-bg-elevated: #ffffff;
      --color-bg-soft: #f0f0f4;

      --color-phone-shell: #050509;
      --color-phone-screen: #050509;

      --color-text-main: #050509;
      --color-text-soft: #666677;
      --color-text-softer: #9a9aac;
      --color-text-inverse: #f5f5ff;

      --color-accent: #1111ff;
      --color-accent-soft: rgba(17, 17, 255, 0.08);
      --color-accent-strong: #0000d0;

      --color-danger: #ff3366;
      --color-success: #22c55e;
      --color-warning: #ffaa33;

      --color-border-subtle: rgba(5, 5, 9, 0.06);
      --color-border-strong: rgba(5, 5, 9, 0.16);

      --color-chip-bg: rgba(5, 5, 9, 0.04);
      --color-chip-border: rgba(5, 5, 9, 0.08);

      --color-gradient-hero: radial-gradient(circle at 0% -40%, rgba(17, 17, 255, 0.16), transparent 60%),
                              radial-gradient(circle at 120% 140%, rgba(255, 51, 102, 0.14), transparent 50%);

      --color-shadow-soft: 0 18px 40px rgba(15, 15, 40, 0.18);
      --color-shadow-phone: 0 30px 80px rgba(5, 5, 20, 0.75);

      /* ---------- Размеры ---------- */
      --radius-xs: 8px;
      --radius-s: 12px;
      --radius-m: 18px;
      --radius-l: 24px;
      --radius-xl: 32px;
      --radius-2xl: 40px;
      --radius-pill: 999px;

      --space-2xs: 4px;
      --space-xs: 8px;
      --space-s: 12px;
      --space-m: 16px;
      --space-l: 24px;
      --space-xl: 32px;
      --space-2xl: 40px;
      --space-3xl: 56px;

      --header-height: 72px;
      --content-max-width: 1120px;

      /* ---------- Motion / анимации ---------- */
      --motion-fast: 140ms;
      --motion-normal: 220ms;
      --motion-slow: 380ms;

      --easing-standard: cubic-bezier(0.2, 0.7, 0.2, 1);
      --easing-soft: cubic-bezier(0.16, 0.84, 0.44, 1);
      --easing-overshoot: cubic-bezier(0.2, 1.4, 0.2, 1);

      /* ---------- Z-index слои ---------- */
      --z-header: 20;
      --z-theme-toggle: 30;
      --z-phone: 5;
      --z-phone-glow: 2;
      --z-overlay: 100;
      --z-toast: 120;
    }

    /* ---------- ТЁМНАЯ ТЕМА ---------- */

    html[data-theme="dark"] {
      --color-bg-app: #050509;
      --color-bg-elevated: #0c0c14;
      --color-bg-soft: #131320;

      --color-phone-shell: #f3f3fb;
      --color-phone-screen: #050509;

      --color-text-main: #f4f4ff;
      --color-text-soft: #b1b1c6;
      --color-text-softer: #77778a;
      --color-text-inverse: #050509;

      --color-accent: #7f7fff;
      --color-accent-soft: rgba(127, 127, 255, 0.16);
      --color-accent-strong: #a5a5ff;

      --color-danger: #ff6b8c;
      --color-success: #4ade80;
      --color-warning: #ffbf69;

      --color-border-subtle: rgba(255, 255, 255, 0.08);
      --color-border-strong: rgba(255, 255, 255, 0.16);

      --color-chip-bg: rgba(255, 255, 255, 0.04);
      --color-chip-border: rgba(255, 255, 255, 0.08);

      --color-gradient-hero: radial-gradient(circle at 0% -40%, rgba(127, 127, 255, 0.32), transparent 60%),
                              radial-gradient(circle at 120% 140%, rgba(255, 107, 140, 0.32), transparent 50%);

      --color-shadow-soft: 0 26px 60px rgba(0, 0, 0, 0.9);
      --color-shadow-phone: 0 32px 90px rgba(0, 0, 0, 0.95);
    }

    /* ------------------------------
       KEYFRAMES
    ------------------------------ */

    @keyframes fadeInSoft {
      from {
        opacity: 0;
        transform: translateY(8px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes fadeInUpBig {
      from {
        opacity: 0;
        transform: translateY(24px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes gradientShift {
      0% {
        background-position: 0% 0%;
      }
      50% {
        background-position: 100% 50%;
      }
      100% {
        background-position: 0% 0%;
      }
    }

    @keyframes phoneFloat {
      0% {
        transform: translate3d(0, 0, 0) rotate3d(0, 1, 0, -6deg) rotate3d(1, 0, 0, 9deg);
      }
      50% {
        transform: translate3d(0, -10px, 0) rotate3d(0, 1, 0, -2deg) rotate3d(1, 0, 0, 6deg);
      }
      100% {
        transform: translate3d(0, 0, 0) rotate3d(0, 1, 0, -6deg) rotate3d(1, 0, 0, 9deg);
      }
    }

    @keyframes phoneEnter {
      from {
        opacity: 0;
        transform: translate3d(0, 40px, 0) rotate3d(0, 1, 0, -18deg) rotate3d(1, 0, 0, 24deg);
      }
      to {
        opacity: 1;
        transform: translate3d(0, 0, 0) rotate3d(0, 1, 0, -6deg) rotate3d(1, 0, 0, 9deg);
      }
    }

    @keyframes chipPulse {
      0% {
        box-shadow: 0 0 0 0 rgba(17, 17, 255, 0.35);
      }
      80% {
        box-shadow: 0 0 0 18px rgba(17, 17, 255, 0);
      }
      100% {
        box-shadow: 0 0 0 0 rgba(17, 17, 255, 0);
      }
    }

    @keyframes sectionReveal {
      0% {
        opacity: 0;
        transform: translateY(32px) scale(0.98);
        filter: blur(6px);
      }
      100% {
        opacity: 1;
        transform: translateY(0) scale(1);
        filter: blur(0);
      }
    }

    @keyframes messageSlideUp {
      from {
        opacity: 0;
        transform: translateY(12px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    /* ------------------------------
       LAYOUT / PAGE SHELL
    ------------------------------ */

    .l-page {
      min-height: 100vh;
      background-image: var(--color-gradient-hero);
      background-size: 200% 200%;
      animation: gradientShift 22s ease-in-out infinite alternate;
    }

    .l-page-inner {
      max-width: var(--content-max-width);
      margin: 0 auto;
      padding: var(--space-l) var(--space-m) var(--space-3xl);
    }

    @media (min-width: 960px) {
      .l-page-inner {
        padding-top: var(--space-2xl);
        padding-bottom: var(--space-3xl);
      }
    }

    .l-header {
      position: sticky;
      top: 0;
      z-index: var(--z-header);
      backdrop-filter: blur(18px);
      background: linear-gradient(to bottom,
        color-mix(in srgb, var(--color-bg-app) 88%, transparent),
        color-mix(in srgb, var(--color-bg-app) 72%, transparent)
      );
      border-bottom: 1px solid var(--color-border-subtle);
    }

    .l-header-inner {
      max-width: var(--content-max-width);
      margin: 0 auto;
      padding: 10px var(--space-m);
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: var(--space-m);
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .brand-mark {
      width: 28px;
      height: 28px;
      border-radius: 10px;
      background: radial-gradient(circle at 0% 0%, #ffffff, #d0d0ff 38%, #0000d8 100%);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      color: #050509;
      font-weight: 800;
      font-family: var(--font-display);
      font-size: 14px;
      letter-spacing: 0.06em;
      box-shadow: 0 10px 25px rgba(0, 0, 40, 0.45);
    }

    html[data-theme="dark"] .brand-mark {
      background: radial-gradient(circle at 0% 0%, #ffffff, #a5a5ff 36%, #1b1bff 100%);
      color: #050509;
    }

    .brand-text-main {
      font-family: var(--font-display);
      font-size: 17px;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
    }

    .brand-text-sub {
      font-size: 11px;
      color: var(--color-text-soft);
      margin-top: 2px;
    }

    .header-right {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .header-pill {
      padding: 4px 10px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-elevated) 80%, transparent);
      font-size: 11px;
      color: var(--color-text-soft);
      display: inline-flex;
      align-items: center;
      gap: 6px;
      white-space: nowrap;
    }

    .header-pill-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: radial-gradient(circle at 0% 0%, #ffffff, var(--color-accent-strong));
      box-shadow: 0 0 0 4px rgba(17, 17, 255, 0.15);
    }

    .header-pill-label {
      font-weight: 500;
    }

    /* ------------------------------
       THEME TOGGLE (Солнце / Луна)
    ------------------------------ */

    .theme-toggle {
      position: relative;
      width: 46px;
      height: 24px;
      border-radius: 999px;
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-soft) 70%, transparent);
      display: inline-flex;
      align-items: center;
      padding: 2px;
      cursor: pointer;
      transition:
        background var(--motion-normal) var(--easing-standard),
        border-color var(--motion-normal) var(--easing-standard);
    }

    .theme-toggle-knob {
      width: 18px;
      height: 18px;
      border-radius: 999px;
      background: #ffffff;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.22);
      display: flex;
      align-items: center;
      justify-content: center;
      transform: translateX(0);
      transition:
        transform var(--motion-normal) var(--easing-soft),
        background var(--motion-normal) var(--easing-soft);
      color: #f4b000;
      font-size: 11px;
    }

    .theme-toggle-rail {
      position: absolute;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 3px 6px;
      pointer-events: none;
      font-size: 9px;
      color: var(--color-text-softer);
    }

    .theme-toggle-icon {
      opacity: 0.65;
      transition: opacity var(--motion-normal) var(--easing-standard), transform var(--motion-normal) var(--easing-standard);
    }

    .theme-toggle-icon.sun {
      transform-origin: left center;
    }

    .theme-toggle-icon.moon {
      transform-origin: right center;
    }

    html[data-theme="dark"] .theme-toggle-knob {
      transform: translateX(20px);
      background: #050509;
      color: #f9f9ff;
    }

    html[data-theme="dark"] .theme-toggle {
      background: radial-gradient(circle at 0 0, #202047, #050509);
      border-color: rgba(255, 255, 255, 0.16);
    }

    html[data-theme="dark"] .theme-toggle-icon.sun {
      opacity: 0.3;
      transform: scale(0.85);
    }

    html[data-theme="dark"] .theme-toggle-icon.moon {
      opacity: 0.9;
      transform: scale(1.1);
    }

    /* ------------------------------
       УТИЛИТЫ
    ------------------------------ */

    .u-kbd {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 2px 6px;
      border-radius: 6px;
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-elevated) 90%, transparent);
      font-size: 10px;
      font-family: var(--font-sans);
    }

    .u-pill-soft {
      border-radius: var(--radius-pill);
      padding: 4px 10px;
      font-size: 11px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      color: var(--color-text-soft);
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .u-pill-soft strong {
      font-weight: 600;
      color: var(--color-text-main);
    }

    .u-eyebrow {
      font-size: 11px;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--color-text-soft);
      font-weight: 600;
    }

    .u-h1 {
      font-family: var(--font-display);
      font-size: clamp(28px, 5vw, 40px);
      line-height: 1.1;
      letter-spacing: 0.03em;
      margin: 0;
    }

    .u-h2 {
      font-family: var(--font-display);
      font-size: clamp(20px, 3vw, 26px);
      line-height: 1.15;
      margin: 0;
    }

    .u-body-main {
      font-size: 14px;
      line-height: 1.6;
      color: var(--color-text-soft);
    }

    .u-body-small {
      font-size: 12px;
      line-height: 1.5;
      color: var(--color-text-softer);
    }

    .u-section {
      padding-top: var(--space-2xl);
      padding-bottom: var(--space-2xl);
    }

    .u-section:first-of-type {
      padding-top: var(--space-xl);
    }

    @media (min-width: 960px) {
      .u-section {
        padding-top: var(--space-3xl);
        padding-bottom: var(--space-3xl);
      }
    }

    .u-section-header {
      margin-bottom: var(--space-l);
      animation: fadeInSoft var(--motion-slow) var(--easing-soft) both;
    }

    .u-grid-hero {
      display: grid;
      grid-template-columns: minmax(0, 1.1fr);
      gap: var(--space-xl);
      align-items: center;
    }

    @media (min-width: 960px) {
      .u-grid-hero {
        grid-template-columns: minmax(0, 1.1fr) minmax(0, 0.95fr);
      }
    }

    .u-reveal {
      opacity: 0;
      transform: translateY(24px);
      filter: blur(6px);
      transition:
        opacity var(--motion-slow) var(--easing-soft),
        transform var(--motion-slow) var(--easing-soft),
        filter var(--motion-slow) var(--easing-soft);
    }

    .u-reveal.is-visible {
      opacity: 1;
      transform: translateY(0);
      filter: blur(0);
    }

    .u-divider {
      height: 1px;
      border-radius: 999px;
      background: linear-gradient(to right,
        transparent,
        color-mix(in srgb, var(--color-border-subtle) 80%, transparent),
        transparent
      );
      margin: var(--space-2xl) 0;
    }

    /* ------------------------------
       КОМПОНЕНТЫ: КНОПКИ / КАРТОЧКИ
    ------------------------------ */

    .c-button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      border-radius: var(--radius-pill);
      border: 1px solid transparent;
      padding: 10px 18px;
      font-size: 13px;
      font-weight: 600;
      letter-spacing: 0.02em;
      cursor: pointer;
      outline: none;
      background: var(--color-accent);
      color: #ffffff;
      box-shadow: 0 14px 30px rgba(0, 0, 60, 0.45);
      transform: translateY(0);
      transition:
        box-shadow var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard),
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        color var(--motion-fast) var(--easing-standard);
    }

    .c-button span {
      display: inline-flex;
      align-items: center;
      justify-content: center;
    }

    .c-button-icon {
      font-size: 15px;
      line-height: 1;
    }

    .c-button:hover {
      transform: translateY(-1px);
      box-shadow: 0 18px 40px rgba(0, 0, 60, 0.55);
      background: var(--color-accent-strong);
    }

    .c-button:active {
      transform: translateY(0);
      box-shadow: 0 8px 22px rgba(0, 0, 40, 0.6);
    }

    .c-button--ghost {
      background: transparent;
      color: var(--color-text-main);
      border-color: var(--color-border-subtle);
      box-shadow: none;
    }

    .c-button--ghost:hover {
      background: var(--color-chip-bg);
      border-color: var(--color-border-strong);
      box-shadow: none;
    }

    .c-button--secondary {
      background: var(--color-chip-bg);
      border-color: var(--color-chip-border);
      color: var(--color-text-main);
      box-shadow: none;
    }

    .c-button--secondary:hover {
      background: color-mix(in srgb, var(--color-chip-bg) 70%, var(--color-accent-soft));
      border-color: var(--color-border-strong);
    }

    .c-button--sm {
      padding: 7px 14px;
      font-size: 12px;
    }

    .c-card {
      position: relative;
      border-radius: var(--radius-xl);
      background: color-mix(in srgb, var(--color-bg-elevated) 94%, transparent);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--color-shadow-soft);
      padding: var(--space-l);
      overflow: hidden;
    }

    html[data-theme="dark"] .c-card {
      background: radial-gradient(circle at 0 0, rgba(127, 127, 255, 0.16), transparent 70%), var(--color-bg-elevated);
    }

    .c-card--soft {
      border-radius: var(--radius-l);
      padding: var(--space-m);
      box-shadow: none;
      background: color-mix(in srgb, var(--color-bg-elevated) 88%, transparent);
    }

    .c-badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      border-radius: var(--radius-pill);
      padding: 4px 10px;
      font-size: 11px;
      background: var(--color-accent-soft);
      color: var(--color-accent-strong);
    }

    .c-badge-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: radial-gradient(circle at 0 0, #ffffff, var(--color-accent-strong));
    }

    .c-chip {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      border-radius: var(--radius-pill);
      padding: 6px 12px;
      font-size: 12px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      color: var(--color-text-soft);
      cursor: pointer;
      transition:
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        color var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard);
    }

    .c-chip:hover {
      transform: translateY(-1px);
      border-color: var(--color-border-strong);
      color: var(--color-text-main);
    }

    .c-chip--active {
      background: var(--color-accent);
      border-color: var(--color-accent);
      color: #ffffff;
      box-shadow: 0 0 0 0 rgba(17, 17, 255, 0.4);
      animation: chipPulse 2.2s var(--easing-soft) infinite;
    }

    .c-chip-group {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    /* ------------------------------
       HERO + IPHONE
    ------------------------------ */

    .hero {
      position: relative;
      display: grid;
      grid-template-columns: minmax(0, 1.1fr);
      gap: var(--space-xl);
      align-items: center;
      margin-top: var(--space-xl);
      animation: fadeInUpBig 520ms var(--easing-soft) both;
    }

    @media (min-width: 960px) {
      .hero {
        grid-template-columns: minmax(0, 1.1fr) minmax(0, 0.95fr);
      }
    }

    .hero-copy {
      display: flex;
      flex-direction: column;
      gap: var(--space-m);
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
      margin-top: 6px;
    }

    .hero-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: var(--space-s);
    }

    .hero-arrow {
      margin-top: var(--space-m);
      font-size: 11px;
      display: inline-flex;
      flex-direction: column;
      gap: 4px;
      color: var(--color-text-softer);
      align-items: flex-start;
    }

    .hero-arrow-icon {
      width: 16px;
      height: 24px;
      border-radius: 999px;
      border: 1px solid var(--color-border-subtle);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 12px;
      animation: fadeInSoft 1.2s var(--easing-soft) both infinite alternate;
    }

    /* ---------- iPhone сцена ---------- */

    .phone-scene {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      padding-bottom: var(--space-l);
    }

    .phone-glow {
      position: absolute;
      inset: 40px -40px -40px;
      background:
        radial-gradient(circle at 20% 0%, rgba(255, 255, 255, 0.32), transparent 55%),
        radial-gradient(circle at 80% 120%, rgba(0, 0, 0, 0.78), transparent 60%);
      filter: blur(12px);
      opacity: 0.8;
      z-index: var(--z-phone-glow);
      pointer-events: none;
    }

    html[data-theme="dark"] .phone-glow {
      background:
        radial-gradient(circle at 20% 0%, rgba(127, 127, 255, 0.6), transparent 55%),
        radial-gradient(circle at 80% 120%, rgba(0, 0, 0, 1), transparent 60%);
    }

    .phone-device {
      position: relative;
      width: min(320px, 85vw);
      border-radius: 38px;
      padding: 12px;
      background: radial-gradient(circle at 0 0, #ffffff, #d5d7e5);
      box-shadow: var(--color-shadow-phone);
      transform-origin: center;
      animation:
        phoneEnter 640ms var(--easing-soft) both,
        phoneFloat 16s ease-in-out 800ms infinite;
      z-index: var(--z-phone);
    }

    html[data-theme="dark"] .phone-device {
      background: radial-gradient(circle at 0 0, #e5e5ff, #8888b8);
    }

    .phone-inner {
      border-radius: 30px;
      background: var(--color-phone-shell);
      padding: 9px 7px 11px;
      position: relative;
    }

    .phone-notch {
      position: absolute;
      top: 6px;
      left: 50%;
      transform: translateX(-50%);
      width: 88px;
      height: 18px;
      border-radius: 999px;
      background: linear-gradient(to bottom, #050509, #151520);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
    }

    .phone-notch-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: radial-gradient(circle at 0 0, #ffffff, #777799);
      opacity: 0.9;
    }

    .phone-notch-line {
      width: 34px;
      height: 4px;
      border-radius: 999px;
      background: linear-gradient(to right, #2f2f3f, #171725);
    }

    .phone-screen {
      margin-top: 18px;
      border-radius: 26px;
      background: linear-gradient(180deg, #050509, #050509 40%, #060612 100%);
      padding: 10px 8px 12px;
      position: relative;
      overflow: hidden;
      box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.04);
    }

    html[data-theme="dark"] .phone-screen {
      background: linear-gradient(180deg, #050509, #050509 42%, #050509 100%);
    }

    .phone-statusbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 9px;
      color: #b3b3c7;
      margin-bottom: 6px;
    }

    .phone-statusbar-right {
      display: inline-flex;
      gap: 4px;
      align-items: center;
    }

    .phone-dot-pill {
      border-radius: 999px;
      padding: 2px 6px;
      border: 1px solid rgba(255, 255, 255, 0.14);
      font-size: 8px;
      display: inline-flex;
      align-items: center;
      gap: 4px;
    }

    .phone-dot-pill-dot {
      width: 3px;
      height: 3px;
      border-radius: 999px;
      background: #3cffd0;
    }

    .phone-screen-nav {
      display: flex;
      gap: 6px;
      margin-bottom: 10px;
      flex-wrap: wrap;
    }

    .phone-screen-chip {
      flex: 1 0 auto;
      padding: 4px 8px;
      border-radius: 999px;
      border: 1px solid rgba(255, 255, 255, 0.12);
      font-size: 9px;
      color: #c0c0d7;
      background: rgba(255, 255, 255, 0.02);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 4px;
      cursor: pointer;
      opacity: 0.75;
      transition:
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        opacity var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard);
    }

    .phone-screen-chip-dot {
      width: 4px;
      height: 4px;
      border-radius: 999px;
      background: #8f8fff;
    }

    .phone-screen-chip.is-active {
      border-color: #8f8fff;
      background: linear-gradient(120deg, rgba(143, 143, 255, 0.3), transparent);
      color: #ffffff;
      opacity: 1;
      transform: translateY(-1px);
    }

    .phone-screen-viewport {
      position: relative;
      border-radius: 18px;
      background: radial-gradient(circle at 0 0, rgba(143, 143, 255, 0.28), transparent 55%);
      padding: 8px 6px 10px;
      overflow: hidden;
      min-height: 172px;
    }

    .phone-screen-slide {
      position: absolute;
      inset: 0;
      padding: 2px;
      opacity: 0;
      transform: translateY(10px);
      pointer-events: none;
      transition:
        opacity var(--motion-normal) var(--easing-soft),
        transform var(--motion-normal) var(--easing-soft);
    }

    .phone-screen-slide.is-active {
      opacity: 1;
      transform: translateY(0);
      pointer-events: auto;
    }

    /* Слайды: 1) онбординг / чат, 2) индекс, 3) модули */

    .phone-chat {
      display: flex;
      flex-direction: column;
      gap: 4px;
      font-size: 10px;
    }

    .phone-msg-row {
      display: flex;
      margin-bottom: 2px;
    }

    .phone-msg-row.me {
      justify-content: flex-end;
    }

    .phone-msg {
      max-width: 84%;
      padding: 6px 8px;
      border-radius: 14px;
      line-height: 1.35;
      animation: messageSlideUp 260ms var(--easing-soft) both;
    }

    .phone-msg.bot {
      background: rgba(18, 18, 40, 0.88);
      color: #f5f5ff;
      border-bottom-left-radius: 4px;
    }

    .phone-msg.me {
      background: #f5f5ff;
      color: #050509;
      border-bottom-right-radius: 4px;
    }

    .phone-msg-meta {
      font-size: 8px;
      color: #8080a0;
      margin-top: 2px;
    }

    /* Слайд индекс дня */

    .phone-index-card {
      border-radius: 14px;
      padding: 8px;
      background: rgba(8, 8, 22, 0.88);
      color: #f5f5ff;
      font-size: 9px;
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    .phone-index-top {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      gap: 6px;
    }

    .phone-index-label {
      font-size: 9px;
      text-transform: uppercase;
      letter-spacing: 0.16em;
      color: #a9a9c8;
    }

    .phone-index-value {
      font-family: var(--font-display);
      font-size: 22px;
      font-weight: 700;
    }

    .phone-index-max {
      font-size: 10px;
      color: #c0c0dd;
    }

    .phone-index-bar {
      height: 6px;
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.08);
      overflow: hidden;
      margin-top: 4px;
      position: relative;
    }

    .phone-index-bar-fill {
      position: absolute;
      inset: 0;
      width: 60%; /* 3 из 5 */
      border-radius: inherit;
      background: linear-gradient(90deg, #ff6b8c, #ffbf69, #4ade80);
    }

    .phone-index-pills {
      display: flex;
      gap: 4px;
      margin-top: 4px;
    }

    .phone-index-pill {
      flex: 1;
      border-radius: 999px;
      padding: 3px 4px;
      text-align: center;
      font-size: 8px;
      background: rgba(255, 255, 255, 0.04);
    }

    .phone-index-pill span {
      display: block;
      font-size: 8px;
      color: #a9a9c8;
    }

    .phone-index-pill strong {
      font-size: 10px;
      color: #f5f5ff;
    }

    /* Слайд модули */

    .phone-modules {
      display: flex;
      flex-direction: column;
      gap: 5px;
      font-size: 9px;
    }

    .phone-mod {
      border-radius: 12px;
      padding: 5px 7px;
      background: rgba(10, 10, 26, 0.9);
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 6px;
    }

    .phone-mod-main {
      display: flex;
      flex-direction: column;
      gap: 1px;
    }

    .phone-mod-title {
      font-weight: 600;
    }

    .phone-mod-sub {
      color: #a9a9c8;
      font-size: 8px;
    }

    .phone-mod-pill {
      border-radius: 999px;
      padding: 3px 6px;
      background: rgba(255, 255, 255, 0.06);
      font-size: 8px;
    }

    /* ------------------------------
       СЕКЦИЯ: КАК ЭТО ОЩУЩАЕТСЯ
    ------------------------------ */

    .story {
      display: grid;
      grid-template-columns: minmax(0, 1.05fr);
      gap: var(--space-l);
      align-items: flex-start;
    }

    @media (min-width: 960px) {
      .story {
        grid-template-columns: minmax(0, 0.9fr) minmax(0, 1.1fr);
      }
    }

    .story-text {
      max-width: 480px;
    }

    .story-chat {
      border-radius: var(--radius-xl);
      background: color-mix(in srgb, var(--color-bg-elevated) 88%, transparent);
      border: 1px solid var(--color-border-subtle);
      padding: var(--space-m);
      box-shadow: var(--color-shadow-soft);
    }

    .story-chat-inner {
      max-height: 320px;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .story-msg-row {
      display: flex;
      margin-bottom: 4px;
    }

    .story-msg-row.me {
      justify-content: flex-end;
    }

    .story-msg {
      max-width: 78%;
      border-radius: 18px;
      padding: 8px 11px;
      font-size: 13px;
      line-height: 1.4;
      animation: messageSlideUp 260ms var(--easing-soft) both;
    }

    .story-msg.bot {
      background: color-mix(in srgb, var(--color-bg-soft) 80%, transparent);
      color: var(--color-text-main);
      border-bottom-left-radius: 6px;
    }

    .story-msg.me {
      background: var(--color-accent);
      color: #ffffff;
      border-bottom-right-radius: 6px;
    }

    .story-msg-label {
      font-size: 10px;
      font-weight: 600;
      margin-bottom: 4px;
      opacity: 0.7;
    }

    /* ------------------------------
       СЕКЦИЯ: ИНДЕКС ДНЯ 1–5
    ------------------------------ */

    .index-section-grid {
      display: grid;
      grid-template-columns: minmax(0, 1.1fr);
      gap: var(--space-l);
    }

    @media (min-width: 960px) {
      .index-section-grid {
        grid-template-columns: minmax(0, 1.1fr) minmax(0, 0.9fr);
      }
    }

    .index-main-card {
      border-radius: var(--radius-xl);
      padding: var(--space-l);
      background: color-mix(in srgb, var(--color-bg-elevated) 94%, transparent);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--color-shadow-soft);
    }

    .index-main-header {
      display: flex;
      justify-content: space-between;
      gap: var(--space-s);
      align-items: baseline;
      margin-bottom: var(--space-s);
    }

    .index-main-value {
      font-family: var(--font-display);
      font-size: 40px;
      font-weight: 700;
      letter-spacing: 0.04em;
    }

    .index-main-max {
      font-size: 13px;
      color: var(--color-text-soft);
    }

    .index-main-bar {
      height: 10px;
      border-radius: 999px;
      background: var(--color-bg-soft);
      position: relative;
      overflow: hidden;
    }

    .index-main-bar-fill {
      position: absolute;
      inset: 0;
      width: 60%; /* пример 3 из 5 */
      border-radius: inherit;
      background: linear-gradient(90deg, #ff6b8c, #ffbf69, #4ade80);
    }

    .index-mini-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: var(--space-s);
      margin-top: var(--space-m);
      font-size: 12px;
    }

    .index-mini-card {
      border-radius: var(--radius-m);
      border: 1px solid var(--color-border-subtle);
      padding: 10px 10px 10px;
      background: color-mix(in srgb, var(--color-bg-elevated) 92%, transparent);
    }

    .index-mini-label {
      font-size: 11px;
      color: var(--color-text-soft);
      margin-bottom: 4px;
    }

    .index-mini-value {
      font-family: var(--font-display);
      font-size: 16px;
      font-weight: 700;
    }

    .index-legend {
      margin-top: var(--space-s);
      font-size: 11px;
      color: var(--color-text-softer);
    }

    .index-pill-row {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: var(--space-xs);
    }

    .index-pill {
      border-radius: var(--radius-pill);
      padding: 3px 8px;
      font-size: 11px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      color: var(--color-text-soft);
    }

    /* ------------------------------
       СЕКЦИЯ: КЕЙС ДО/ПОСЛЕ
    ------------------------------ */

    .case-grid {
      display: grid;
      grid-template-columns: minmax(0, 1fr);
      gap: var(--space-l);
    }

    @media (min-width: 960px) {
      .case-grid {
        grid-template-columns: minmax(0, 1fr) minmax(0, 1fr);
      }
    }

    .case-card {
      border-radius: var(--radius-xl);
      padding: var(--space-l);
      background: color-mix(in srgb, var(--color-bg-elevated) 94%, transparent);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--color-shadow-soft);
      position: relative;
      overflow: hidden;
    }

    .case-pill {
      border-radius: var(--radius-pill);
      padding: 4px 10px;
      font-size: 11px;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      margin-bottom: var(--space-xs);
    }

    .case-pill--before {
      color: var(--color-danger);
      border-color: color-mix(in srgb, var(--color-danger) 40%, var(--color-chip-border));
    }

    .case-pill--after {
      color: var(--color-success);
      border-color: color-mix(in srgb, var(--color-success) 40%, var(--color-chip-border));
    }

    .case-metric-row {
      display: flex;
      gap: var(--space-s);
      margin-top: var(--space-m);
    }

    .case-metric {
      flex: 1;
      border-radius: var(--radius-m);
      border: 1px dashed var(--color-border-subtle);
      padding: 8px 10px;
      font-size: 12px;
    }

    .case-metric-label {
      font-size: 11px;
      color: var(--color-text-soft);
      margin-bottom: 4px;
    }

    .case-metric-value {
      font-family: var(--font-display);
      font-size: 18px;
      font-weight: 700;
    }

    /* ------------------------------
       СЕКЦИЯ: МОДУЛИ
    ------------------------------ */

    .modules-card {
      border-radius: var(--radius-xl);
      padding: var(--space-l);
      background: color-mix(in srgb, var(--color-bg-elevated) 94%, transparent);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--color-shadow-soft);
      display: grid;
      grid-template-columns: minmax(0, 0.95fr);
      gap: var(--space-m);
    }

    @media (min-width: 960px) {
      .modules-card {
        grid-template-columns: minmax(0, 0.9fr) minmax(0, 1.05fr);
      }
    }

    .modules-tabs {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .modules-tab {
      border-radius: var(--radius-pill);
      padding: 8px 14px;
      font-size: 13px;
      border: 1px solid var(--color-chip-border);
      background: var(--color-chip-bg);
      display: flex;
      align-items: center;
      justify-content: space-between;
      cursor: pointer;
      transition:
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard);
    }

    .modules-tab-label {
      font-weight: 600;
    }

    .modules-tab-icon {
      font-size: 14px;
    }

    .modules-tab.is-active {
      background: var(--color-accent);
      border-color: var(--color-accent);
      color: #ffffff;
      transform: translateY(-1px);
      box-shadow: 0 12px 30px rgba(0, 0, 60, 0.4);
    }

    .modules-content {
      border-radius: var(--radius-l);
      padding: var(--space-m);
      background: color-mix(in srgb, var(--color-bg-soft) 80%, transparent);
      border: 1px solid var(--color-border-subtle);
      font-size: 13px;
    }

    .modules-content-panel {
      display: none;
    }

    .modules-content-panel.is-active {
      display: block;
    }

    .modules-bullets {
      margin-top: var(--space-xs);
      font-size: 12px;
      color: var(--color-text-soft);
    }

    .modules-bullets li {
      margin-bottom: 4px;
    }

    /* ------------------------------
       FAQ
    ------------------------------ */

    .faq-grid {
      max-width: 760px;
      margin: 0;
      padding: 0;
      list-style: none;
    }

    .faq-item {
      border-radius: var(--radius-l);
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-elevated) 92%, transparent);
      margin-bottom: var(--space-s);
      overflow: hidden;
    }

    .faq-question {
      width: 100%;
      text-align: left;
      padding: 12px 14px;
      background: transparent;
      border: none;
      outline: none;
      display: flex;
      justify-content: space-between;
      align-items: center;
      cursor: pointer;
      font-size: 13px;
      font-weight: 500;
      color: var(--color-text-main);
    }

    .faq-icon {
      font-size: 18px;
      line-height: 1;
      transform: rotate(0deg);
      transition: transform var(--motion-normal) var(--easing-standard);
      color: var(--color-text-softer);
    }

    .faq-item.is-open .faq-icon {
      transform: rotate(45deg);
    }

    .faq-answer {
      max-height: 0;
      overflow: hidden;
      transition: max-height var(--motion-slow) var(--easing-soft);
      padding: 0 14px;
    }

    .faq-answer-inner {
      padding-bottom: 12px;
      font-size: 13px;
      color: var(--color-text-soft);
    }

    .faq-item.is-open .faq-answer {
      max-height: 200px;
    }

    /* ------------------------------
       CTA
    ------------------------------ */

    .cta-card {
      border-radius: var(--radius-xl);
      padding: var(--space-l);
      background: linear-gradient(135deg, var(--color-accent), var(--color-accent-strong));
      color: #ffffff;
      box-shadow: 0 22px 50px rgba(0, 0, 60, 0.7);
      text-align: center;
    }

    .cta-card h2 {
      margin: 0 0 var(--space-xs);
      font-family: var(--font-display);
      font-size: clamp(22px, 3.2vw, 28px);
    }

    .cta-card p {
      margin: 0 0 var(--space-m);
      font-size: 14px;
      opacity: 0.9;
    }

    .cta-buttons {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
    }

    .cta-secondary {
      border-radius: var(--radius-pill);
      padding: 8px 14px;
      border: 1px solid rgba(255, 255, 255, 0.5);
      font-size: 12px;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      cursor: pointer;
      background: transparent;
      color: #ffffff;
    }

    .cta-secondary span {
      display: inline-flex;
      align-items: center;
    }

    .cta-secondary-icon {
      font-size: 14px;
    }
  </style>
</head>
<body class="l-page">
  <header class="l-header">
    <div class="l-header-inner">
      <div class="brand">
        <div class="brand-mark">A</div>
        <div>
          <div class="brand-text-main">ADVICE</div>
          <div class="brand-text-sub">бот-психолог внутри Telegram</div>
        </div>
      </div>
      <div class="header-right">
        <div class="header-pill">
          <span class="header-pill-dot"></span>
          <span class="header-pill-label">Работает в Telegram</span>
        </div>
        <button class="theme-toggle" type="button" id="theme-toggle" aria-label="Переключить тему">
          <div class="theme-toggle-rail">
            <span class="theme-toggle-icon sun">☀️</span>
            <span class="theme-toggle-icon moon">🌙</span>
          </div>
          <div class="theme-toggle-knob" aria-hidden="true">☀️</div>
        </button>
      </div>
    </div>
  </header>

  <main class="l-page-inner">
    <!-- HERO + IPHONE -->
    <section class="u-section hero" id="hero">
      <div class="hero-copy u-reveal js-reveal">
        <div class="u-eyebrow">Твой день в трёх цифрах</div>
        <h1 class="u-h1">
          Бот, с которым удобно говорить о себе
          и не терять опору в повседневности.
        </h1>
        <p class="u-body-main">
          ADVICE живёт прямо в Telegram, задаёт короткие вопросы про психику, сон и деньги,
          считает индекс дня от 1 до 5 и помогает увидеть, где ты реально проседаешь.
        </p>
        <div class="hero-actions">
          <a href="https://t.me/your_advice_bot" class="c-button">
            <span>Открыть бота в Telegram</span>
            <span class="c-button-icon">↗</span>
          </a>
          <button class="c-button c-button--ghost c-button--sm" type="button" id="scroll-to-story">
            <span>Посмотреть, как это внутри</span>
          </button>
        </div>
        <div class="hero-meta">
          <div class="u-pill-soft">
            <span>Индекс дня&nbsp;<strong>от 1 до 5</strong></span>
          </div>
          <div class="u-pill-soft">
            <span>Психика · Сон · Деньги</span>
          </div>
        </div>
        <div class="hero-arrow">
          <span>Прокрути вниз, чтобы увидеть, как выглядит бот.</span>
          <div class="hero-arrow-icon">↓</div>
        </div>
      </div>

      <!-- iPhone сцена -->
      <div class="phone-scene u-reveal js-reveal">
        <div class="phone-glow"></div>
        <div class="phone-device">
          <div class="phone-inner">
            <div class="phone-notch">
              <div class="phone-notch-line"></div>
              <div class="phone-notch-dot"></div>
            </div>
            <div class="phone-screen">
              <div class="phone-statusbar">
                <span>ADVICE · онлайн</span>
                <div class="phone-statusbar-right">
                  <div class="phone-dot-pill">
                    <span class="phone-dot-pill-dot"></span>
                    <span>AI + человек</span>
                  </div>
                </div>
              </div>

              <div class="phone-screen-nav">
                <button class="phone-screen-chip is-active" data-screen="welcome" type="button">
                  <span class="phone-screen-chip-dot"></span>
                  <span>Приветствие</span>
                </button>
                <button class="phone-screen-chip" data-screen="index" type="button">
                  <span class="phone-screen-chip-dot"></span>
                  <span>Индекс дня</span>
                </button>
                <button class="phone-screen-chip" data-screen="modules" type="button">
                  <span class="phone-screen-chip-dot"></span>
                  <span>Модули</span>
                </button>
              </div>

              <div class="phone-screen-viewport">
                <!-- Слайд 1: приветствие / чат -->
                <div class="phone-screen-slide is-active" data-screen-id="welcome">
                  <div class="phone-chat">
                    <div class="phone-msg-row">
                      <div class="phone-msg bot">
                        Привет. Я ADVICE — бот, который помогает держать в фокусе психику, сон и деньги.
                        <div class="phone-msg-meta">только ты и этот чат</div>
                      </div>
                    </div>
                    <div class="phone-msg-row">
                      <div class="phone-msg bot">
                        Я задам три коротких вопроса и соберу индекс дня. Дальше сможем работать уже с деталями.
                      </div>
                    </div>
                    <div class="phone-msg-row me">
                      <div class="phone-msg me">
                        Окей, давай попробуем.
                      </div>
                    </div>
                    <div class="phone-msg-row">
                      <div class="phone-msg bot">
                        Начнём с психики. Как по ощущениям сейчас: больше про «выдерживаю» или «проседаю»?
                      </div>
                    </div>
                  </div>
                </div>

                <!-- Слайд 2: индекс дня 1–5 -->
                <div class="phone-screen-slide" data-screen-id="index">
                  <div class="phone-index-card">
                    <div class="phone-index-top">
                      <div>
                        <div class="phone-index-label">Качество дня</div>
                        <div class="phone-index-value">3,1</div>
                      </div>
                      <div class="phone-index-max">из 5 возможных</div>
                    </div>
                    <div class="phone-index-bar">
                      <div class="phone-index-bar-fill"></div>
                    </div>
                    <div class="phone-index-pills">
                      <div class="phone-index-pill">
                        <span>психика</span>
                        <strong>3,4</strong>
                      </div>
                      <div class="phone-index-pill">
                        <span>сон</span>
                        <strong>2,7</strong>
                      </div>
                      <div class="phone-index-pill">
                        <span>деньги</span>
                        <strong>3,2</strong>
                      </div>
                    </div>
                    <div class="phone-msg-meta" style="margin-top:6px;">
                      Сегодня чуть проседает сон. Я предложу небольшой план, как восстановить ресурс.
                    </div>
                  </div>
                </div>

                <!-- Слайд 3: модули -->
                <div class="phone-screen-slide" data-screen-id="modules">
                  <div class="phone-modules">
                    <div class="phone-mod">
                      <div class="phone-mod-main">
                        <div class="phone-mod-title">Психолог</div>
                        <div class="phone-mod-sub">диалог без осуждения, плюс команда специалистов</div>
                      </div>
                      <div class="phone-mod-pill">чат 24/7</div>
                    </div>
                    <div class="phone-mod">
                      <div class="phone-mod-main">
                        <div class="phone-mod-title">Сон</div>
                        <div class="phone-mod-sub">режим, ритуалы, звуки и корректировка по факту</div>
                      </div>
                      <div class="phone-mod-pill">режим под тебя</div>
                    </div>
                    <div class="phone-mod">
                      <div class="phone-mod-main">
                        <div class="phone-mod-title">Деньги</div>
                        <div class="phone-mod-sub">доход, расходы и привычка откладывать без жёсткой экономии</div>
                      </div>
                      <div class="phone-mod-pill">пошаговый план</div>
                    </div>
                  </div>
                </div>

              </div><!-- /.phone-screen-viewport -->
            </div><!-- /.phone-screen -->
          </div><!-- /.phone-inner -->
        </div><!-- /.phone-device -->
      </div><!-- /.phone-scene -->
    </section>

    <div class="u-divider"></div>

    <!-- СЕКЦИЯ: КАК ЭТО ОЩУЩАЕТСЯ ВНУТРИ БОТА -->
    <section class="u-section" id="story">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">Как это ощущается</div>
        <h2 class="u-h2">Выглядит как переписка в Telegram, но под капотом — система</h2>
        <p class="u-body-main" style="max-width: 520px; margin-top: 8px;">
          Никаких странных форм и анкет. Ты просто переписываешься с ботом, а он аккуратно
          вытаскивает важное и фиксирует динамику по трём зонам: психика, сон, деньги.
        </p>
      </div>

      <div class="story u-reveal js-reveal">
        <div class="story-text">
          <p class="u-body-main">
            Внутри ADVICE можно писать так, как ты реально думаешь и говоришь.
            Бот не требует «быть молодцом» каждый день, а трезво показывает, где ты сейчас
            и что можно сделать, чтобы стало легче.
          </p>
          <p class="u-body-main">
            Если видим, что что-то идёт не так — подключается команда живых специалистов.
            Но первый шаг всегда безопасный: просто написать в чат.
          </p>
          <div style="margin-top: var(--space-m);">
            <a href="https://t.me/your_advice_bot" class="c-button c-button--secondary">
              <span>Открыть диалог в Telegram</span>
              <span class="c-button-icon">↗</span>
            </a>
          </div>
        </div>

        <div class="story-chat">
          <div class="story-chat-inner">
            <div class="story-msg-row">
              <div class="story-msg bot">
                <div class="story-msg-label">ADVICE</div>
                Привет. Можно без формальностей — просто расскажи, что сейчас больше всего давит.
              </div>
            </div>
            <div class="story-msg-row me">
              <div class="story-msg me">
                Чувствую себя выжатым. Сон сбился, голова не отдыхает, постоянно думаю о деньгах.
              </div>
            </div>
            <div class="story-msg-row">
              <div class="story-msg bot">
                Окей, зафиксируем это и посмотрим в трёх плоскостях: психика, сон и финансы.
                Я помогу выстроить понятные опоры на каждый день.
              </div>
            </div>
            <div class="story-msg-row">
              <div class="story-msg bot">
                Сначала посчитаем индекс дня, потом покажу, откуда начать: с восстановления
                сна, с пересборки расписания или с денег.
              </div>
            </div>
            <div class="story-msg-row me">
              <div class="story-msg me">
                Звучит окей. Хочу наконец перестать «держаться на остатках».
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="u-divider"></div>

    <!-- СЕКЦИЯ: ИНДЕКС ДНЯ 1–5 -->
    <section class="u-section">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">Индекс дня</div>
        <h2 class="u-h2">Одна цифра от 1 до 5, за которой стоит реальная картина</h2>
        <p class="u-body-main" style="max-width: 520px; margin-top: 8px;">
          Каждый день ADVICE собирает индекс качества жизни: психика, сон, деньги.
          Не абстрактная «мотивация», а конкретный термометр по трём зонам, где ты можешь падать или расти.
        </p>
      </div>

      <div class="index-section-grid u-reveal js-reveal">
        <div class="index-main-card">
          <div class="index-main-header">
            <div>
              <div class="u-eyebrow" style="letter-spacing:0.2em;">Сегодня</div>
              <div class="index-main-value">3,1</div>
            </div>
            <div class="index-main-max">из 5 · нормальный, но не запасной день</div>
          </div>
          <div class="index-main-bar">
            <div class="index-main-bar-fill"></div>
          </div>
          <div class="index-mini-grid">
            <div class="index-mini-card">
              <div class="index-mini-label">Психика</div>
              <div class="index-mini-value">3,4</div>
              <div class="u-body-small">чуть напряжённо, но без красных зон</div>
            </div>
            <div class="index-mini-card">
              <div class="index-mini-label">Сон</div>
              <div class="index-mini-value">2,7</div>
              <div class="u-body-small">мало ресурса, стоит восстановиться</div>
            </div>
            <div class="index-mini-card">
              <div class="index-mini-label">Деньги</div>
              <div class="index-mini-value">3,2</div>
              <div class="u-body-small">контроль есть, но без подушки</div>
            </div>
          </div>
          <div class="index-legend">
            Каждый день индекс перезаписывается, и у тебя появляется хроника: где ты стабилен, а где
            системно проваливаешься.
          </div>
          <div class="index-pill-row">
            <div class="index-pill">1 — день на «аварийных системах»</div>
            <div class="index-pill">3 — держусь, но без большого запаса</div>
            <div class="index-pill">5 — устойчиво, можно брать сложные задачи</div>
          </div>
        </div>

        <div style="align-self:center;">
          <p class="u-body-main">
            Индекс дня — не оценка «ты молодец / не молодец», а инструмент. Если видим, что ты
            несколько дней подряд в районе 2, ADVICE мягко предложит менять режим: от сна до расходов.
          </p>
          <p class="u-body-main">
            Так формируется привычка смотреть на себя не только через задачи и дедлайны, но и через
            качество жизни.
          </p>
        </div>
      </div>
    </section>

    <div class="u-divider"></div>

    <!-- СЕКЦИЯ: КЕЙС ДО/ПОСЛЕ -->
    <section class="u-section">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">Кейс</div>
        <h2 class="u-h2">«С 1,8 до 3,9 за месяц» — пример живого пользователя</h2>
        <p class="u-body-main" style="max-width: 520px; margin-top: 8px;">
          Ниже — пример, как менялся индекс дня и ощущения человека за 30 дней
          работы с ботом. Без имён и личных деталей, только сухие цифры и факты.
        </p>
      </div>

      <div class="case-grid u-reveal js-reveal">
        <div class="case-card">
          <div class="case-pill case-pill--before">
            <span>До старта</span>
          </div>
          <p class="u-body-main">
            Частые провалы по сну, тревожность вечером, деньги — «живу от аванса до аванса».
            Иллюзия, что «всё нормально», пока не посмотрели на индекс дня.
          </p>
          <div class="case-metric-row">
            <div class="case-metric">
              <div class="case-metric-label">Средний индекс дня</div>
              <div class="case-metric-value">1,8</div>
              <div class="u-body-small">за последние 2 недели до старта</div>
            </div>
            <div class="case-metric">
              <div class="case-metric-label">Сон</div>
              <div class="case-metric-value">1,9</div>
              <div class="u-body-small">хаотичный режим, много дофамина ночью</div>
            </div>
          </div>
        </div>

        <div class="case-card">
          <div class="case-pill case-pill--after">
            <span>Через месяц</span>
          </div>
          <p class="u-body-main">
            Выровняли режим сна, поставили мягкий бюджет по категориям,
            подключили живого психолога на несколько сессий — всё внутри одного Telegram-чата.
          </p>
          <div class="case-metric-row">
            <div class="case-metric">
              <div class="case-metric-label">Средний индекс дня</div>
              <div class="case-metric-value">3,9</div>
              <div class="u-body-small">меньше «аварийных дней», больше устойчивости</div>
            </div>
            <div class="case-metric">
              <div class="case-metric-label">Фокус</div>
              <div class="case-metric-value">+2×</div>
              <div class="u-body-small">по самооценке пользователя в диалоге</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="u-divider"></div>

    <!-- СЕКЦИЯ: МОДУЛИ -->
    <section class="u-section">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">Модули</div>
        <h2 class="u-h2">Психика, сон и деньги — в одном боте, а не в трёх разных приложениях</h2>
      </div>

      <div class="modules-card u-reveal js-reveal" id="modules">
        <div class="modules-tabs">
          <button class="modules-tab is-active" data-module="mind" type="button">
            <span class="modules-tab-label">Психолог</span>
            <span class="modules-tab-icon">💬</span>
          </button>
          <button class="modules-tab" data-module="sleep" type="button">
            <span class="modules-tab-label">Сон</span>
            <span class="modules-tab-icon">🌙</span>
          </button>
          <button class="modules-tab" data-module="money" type="button">
            <span class="modules-tab-label">Финансы</span>
            <span class="modules-tab-icon">💸</span>
          </button>
        </div>

        <div class="modules-content">
          <div class="modules-content-panel is-active" data-module-panel="mind">
            <p class="u-body-main">
              Личный чат, где можно проговорить ситуации, состояния и отношения
              так, как оно есть. ADVICE отвечает сразу, а команда специалистов подключается,
              когда это действительно нужно.
            </p>
            <ul class="modules-bullets">
              <li>переписка в формате «как другу», а не как в анкете;</li>
              <li>бережные уточняющие вопросы вместо давления и оценок;</li>
              <li>если становится тяжело — переход к живому психологу.</li>
            </ul>
          </div>
          <div class="modules-content-panel" data-module-panel="sleep">
            <p class="u-body-main">
              Модуль сна помогает выстроить режим под твою жизнь, а не под абстрактные рекомендации.
              Бот смотрит на твой график, шум, привычки и собирает рабочий план.
            </p>
            <ul class="modules-bullets">
              <li>режим отхода ко сну и подъёма, который реалистично выдерживать;</li>
              <li>ритуалы перед сном, снижение дофамина и «шума» перед сном;</li>
              <li>подбор звукового окружения (тишина, шум, природа) под твой запрос.</li>
            </ul>
          </div>
          <div class="modules-content-panel" data-module-panel="money">
            <p class="u-body-main">
              Финансовый модуль не заставляет «резко экономить», а аккуратно собирает картину доходов
              и расходов и показывает, как начать откладывать и перестать жить в режиме «дожить до зарплаты».
            </p>
            <ul class="modules-bullets">
              <li>разбор дохода и ключевых статей расходов без стыда и морализаторства;</li>
              <li>план, как выйти на минимальную подушку безопасности;</li>
              <li>подсказки, где можно срезать 10–15% без ощущения тотальной экономии.</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <div class="u-divider"></div>

    <!-- FAQ -->
    <section class="u-section">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">FAQ</div>
        <h2 class="u-h2">Частые вопросы перед тем, как нажать «Открыть в Telegram»</h2>
      </div>

      <ul class="faq-grid u-reveal js-reveal">
        <li class="faq-item">
          <button class="faq-question" type="button">
            <span>Это терапия или просто бот?</span>
            <span class="faq-icon">+</span>
          </button>
          <div class="faq-answer">
            <div class="faq-answer-inner">
              ADVICE — не медицинская услуга и не замена терапии. Это бот-ассистент, который помогает
              отслеживать состояние и не терять опору в повседневности. Когда видим, что нужна более глубокая работа,
              можем аккуратно предложить перейти к живому психологу.
            </div>
          </div>
        </li>
        <li class="faq-item">
          <button class="faq-question" type="button">
            <span>Кто читает мои сообщения?</span>
            <span class="faq-icon">+</span>
          </button>
          <div class="faq-answer">
            <div class="faq-answer-inner">
              По умолчанию с тобой общается бот. Сообщения может видеть узкая команда специалистов
              ADVICE, чтобы следить за качеством и безопасностью общения. Мы не передаём переписку
              третьим лицам и аккуратно относимся к твоей приватности.
            </div>
          </div>
        </li>
        <li class="faq-item">
          <button class="faq-question" type="button">
            <span>Подписка — навсегда? Что если я решу всё «починить» за месяц?</span>
            <span class="faq-icon">+</span>
          </button>
          <div class="faq-answer">
            <div class="faq-answer-inner">
              Подписку можно остановить в любой момент, но практика показывает: люди остаются не только
              ради «починить проблему», а ради ощущения опоры. Как у Яндекс Плюса — ты подписан не на одну
              функцию, а на систему, которая держит твой день в фокусе.
            </div>
          </div>
        </li>
        <li class="faq-item">
          <button class="faq-question" type="button">
            <span>Что с оплатой и тарифами?</span>
            <span class="faq-icon">+</span>
          </button>
          <div class="faq-answer">
            <div class="faq-answer-inner">
              Сейчас оплата подписки оформляется через администратора в Telegram. Внутри бота есть
              короткое объяснение тарифов: базовый и расширенный. Ты можешь начать в ознакомочном режиме,
              а потом решить, нужен ли тебе постоянный доступ.
            </div>
          </div>
        </li>
      </ul>
    </section>

    <div class="u-divider"></div>

    <!-- CTA -->
    <section class="u-section">
      <div class="cta-card u-reveal js-reveal">
        <h2>Готов попробовать ADVICE в своём Telegram?</h2>
        <p>
          Никаких анкет и регистрации на сайтах. Просто нажми на кнопку — бот откроется
          прямо в Telegram и предложит пройти первый короткий опрос.
        </p>
        <div class="cta-buttons">
          <a href="https://t.me/your_advice_bot" class="c-button">
            <span>Открыть бота в Telegram</span>
            <span class="c-button-icon">↗</span>
          </a>
          <a href="https://t.me/your_advice_support" class="cta-secondary">
            <span class="cta-secondary-icon">👤</span>
            <span>Написать админу, если есть вопросы</span>
          </a>
        </div>
      </div>
    </section>
  </main>

  <script>
    // ---------------------------
    // THEME ENGINE (light/dark)
    // ---------------------------
    (function () {
      const root = document.documentElement;
      const toggle = document.getElementById('theme-toggle');
      const knob = toggle ? toggle.querySelector('.theme-toggle-knob') : null;

      function applyTheme(theme) {
        root.setAttribute('data-theme', theme);
        try {
          window.localStorage.setItem('advice_landing_theme', theme);
        } catch (e) {}
        if (knob) {
          knob.textContent = theme === 'dark' ? '🌙' : '☀️';
        }
      }

      function initTheme() {
        let saved = null;
        try {
          saved = window.localStorage.getItem('advice_landing_theme');
        } catch (e) {}

        if (saved === 'light' || saved === 'dark') {
          applyTheme(saved);
          return;
        }

        const prefersDark = window.matchMedia &&
          window.matchMedia('(prefers-color-scheme: dark)').matches;
        applyTheme(prefersDark ? 'dark' : 'light');
      }

      if (toggle) {
        toggle.addEventListener('click', () => {
          const current = root.getAttribute('data-theme') || 'light';
          const next = current === 'light' ? 'dark' : 'light';
          applyTheme(next);
        });
      }

      initTheme();
    })();

    // ---------------------------
    // SCROLL REVEAL
    // ---------------------------
    (function () {
      const revealEls = Array.from(document.querySelectorAll('.js-reveal'));

      if (!('IntersectionObserver' in window) || revealEls.length === 0) {
        revealEls.forEach(el => el.classList.add('is-visible'));
        return;
      }

      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('is-visible');
              observer.unobserve(entry.target);
            }
          });
        },
        {
          threshold: 0.18,
        }
      );

      revealEls.forEach((el) => observer.observe(el));
    })();

    // ---------------------------
    // HERO SCROLL BUTTON
    // ---------------------------
    (function () {
      const btn = document.getElementById('scroll-to-story');
      const target = document.getElementById('story');
      if (!btn || !target) return;
      btn.addEventListener('click', () => {
        target.scrollIntoView({ behavior: 'smooth', block: 'start' });
      });
    })();

    // ---------------------------
    // PHONE SCREEN SWITCHER
    // ---------------------------
    (function () {
      const chips = Array.from(document.querySelectorAll('.phone-screen-chip'));
      const slides = Array.from(document.querySelectorAll('.phone-screen-slide'));
      if (!chips.length || !slides.length) return;

      function activate(screenId) {
        chips.forEach(ch => {
          ch.classList.toggle('is-active', ch.dataset.screen === screenId);
        });
        slides.forEach(slide => {
          slide.classList.toggle('is-active', slide.dataset.screenId === screenId);
        });
      }

      chips.forEach(ch => {
        ch.addEventListener('click', () => {
          const screenId = ch.dataset.screen;
          if (!screenId) return;
          activate(screenId);
        });
      });
    })();

    // ---------------------------
    // MODULES TABS
    // ---------------------------
    (function () {
      const tabs = Array.from(document.querySelectorAll('.modules-tab'));
      const panels = Array.from(document.querySelectorAll('.modules-content-panel'));
      if (!tabs.length || !panels.length) return;

      function activate(moduleId) {
        tabs.forEach(tab => {
          tab.classList.toggle('is-active', tab.dataset.module === moduleId);
        });
        panels.forEach(panel => {
          panel.classList.toggle('is-active', panel.dataset.modulePanel === moduleId);
        });
      }

      tabs.forEach(tab => {
        tab.addEventListener('click', () => {
          const moduleId = tab.dataset.module;
          if (!moduleId) return;
          activate(moduleId);
        });
      });
    })();

    // ---------------------------
    // FAQ ACCORDION
    // ---------------------------
    (function () {
      const items = Array.from(document.querySelectorAll('.faq-item'));
      if (!items.length) return;

      items.forEach(item => {
        const btn = item.querySelector('.faq-question');
        if (!btn) return;
        btn.addEventListener('click', () => {
          const isOpen = item.classList.contains('is-open');
          items.forEach(i => i.classList.remove('is-open'));
          if (!isOpen) {
            item.classList.add('is-open');
          }
        });
      });
    })();
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="ru" data-theme="light">
<head>
  <meta charset="UTF-8" />
  <title>ADVICE · Бот-психолог в Telegram</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="color-scheme" content="light dark" />
  <meta name="theme-color" content="#050509" />

  <!-- Шрифты: максимально близко к Proxima Nova + выразительный дисплей -->
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Grotesk:wght@500;700&display=swap" rel="stylesheet" />

  <style>
    /* ------------------------------
       RESET / BASE
    ------------------------------ */

    *, *::before, *::after {
      box-sizing: border-box;
    }

    html, body {
      margin: 0;
      padding: 0;
    }

    body {
      min-height: 100vh;
      font-family: var(--font-sans);
      background: var(--color-bg-app);
      color: var(--color-text-main);
      -webkit-font-smoothing: antialiased;
      text-rendering: optimizeLegibility;
    }

    img {
      max-width: 100%;
      display: block;
    }

    button {
      font-family: inherit;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    :root {
      /* ---------- Типографика ---------- */
      --font-sans: -apple-system, BlinkMacSystemFont, "SF Pro Text", "Inter", system-ui, sans-serif;
      --font-display: "Space Grotesk", -apple-system, BlinkMacSystemFont, "SF Pro Display", system-ui, sans-serif;

      /* ---------- Цвета: светлая тема (по умолчанию) ---------- */
      --color-bg-app: #f6f6f8;
      --color-bg-elevated: #ffffff;
      --color-bg-soft: #f0f0f4;

      --color-phone-shell: #050509;
      --color-phone-screen: #050509;

      --color-text-main: #050509;
      --color-text-soft: #666677;
      --color-text-softer: #9a9aac;
      --color-text-inverse: #f5f5ff;

      --color-accent: #1111ff;
      --color-accent-soft: rgba(17, 17, 255, 0.08);
      --color-accent-strong: #0000d0;

      --color-danger: #ff3366;
      --color-success: #22c55e;
      --color-warning: #ffaa33;

      --color-border-subtle: rgba(5, 5, 9, 0.06);
      --color-border-strong: rgba(5, 5, 9, 0.16);

      --color-chip-bg: rgba(5, 5, 9, 0.04);
      --color-chip-border: rgba(5, 5, 9, 0.08);

      --color-gradient-hero: radial-gradient(circle at 0% -40%, rgba(17, 17, 255, 0.16), transparent 60%),
                              radial-gradient(circle at 120% 140%, rgba(255, 51, 102, 0.14), transparent 50%);

      --color-shadow-soft: 0 18px 40px rgba(15, 15, 40, 0.18);
      --color-shadow-phone: 0 30px 80px rgba(5, 5, 20, 0.75);

      /* ---------- Размеры ---------- */
      --radius-xs: 8px;
      --radius-s: 12px;
      --radius-m: 18px;
      --radius-l: 24px;
      --radius-xl: 32px;
      --radius-2xl: 40px;
      --radius-pill: 999px;

      --space-2xs: 4px;
      --space-xs: 8px;
      --space-s: 12px;
      --space-m: 16px;
      --space-l: 24px;
      --space-xl: 32px;
      --space-2xl: 40px;
      --space-3xl: 56px;

      --header-height: 72px;
      --content-max-width: 1120px;

      /* ---------- Motion / анимации ---------- */
      --motion-fast: 140ms;
      --motion-normal: 220ms;
      --motion-slow: 380ms;

      --easing-standard: cubic-bezier(0.2, 0.7, 0.2, 1);
      --easing-soft: cubic-bezier(0.16, 0.84, 0.44, 1);
      --easing-overshoot: cubic-bezier(0.2, 1.4, 0.2, 1);

      /* ---------- Z-index слои ---------- */
      --z-header: 20;
      --z-theme-toggle: 30;
      --z-phone: 5;
      --z-phone-glow: 2;
      --z-overlay: 100;
      --z-toast: 120;
    }

    /* ---------- ТЁМНАЯ ТЕМА ---------- */

    html[data-theme="dark"] {
      --color-bg-app: #050509;
      --color-bg-elevated: #0c0c14;
      --color-bg-soft: #131320;

      --color-phone-shell: #f3f3fb;
      --color-phone-screen: #050509;

      --color-text-main: #f4f4ff;
      --color-text-soft: #b1b1c6;
      --color-text-softer: #77778a;
      --color-text-inverse: #050509;

      --color-accent: #7f7fff;
      --color-accent-soft: rgba(127, 127, 255, 0.16);
      --color-accent-strong: #a5a5ff;

      --color-danger: #ff6b8c;
      --color-success: #4ade80;
      --color-warning: #ffbf69;

      --color-border-subtle: rgba(255, 255, 255, 0.08);
      --color-border-strong: rgba(255, 255, 255, 0.16);

      --color-chip-bg: rgba(255, 255, 255, 0.04);
      --color-chip-border: rgba(255, 255, 255, 0.08);

      --color-gradient-hero: radial-gradient(circle at 0% -40%, rgba(127, 127, 255, 0.32), transparent 60%),
                              radial-gradient(circle at 120% 140%, rgba(255, 107, 140, 0.32), transparent 50%);

      --color-shadow-soft: 0 26px 60px rgba(0, 0, 0, 0.9);
      --color-shadow-phone: 0 32px 90px rgba(0, 0, 0, 0.95);
    }

    /* ------------------------------
       KEYFRAMES
    ------------------------------ */

    @keyframes fadeInSoft {
      from {
        opacity: 0;
        transform: translateY(8px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes fadeInUpBig {
      from {
        opacity: 0;
        transform: translateY(24px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes gradientShift {
      0% {
        background-position: 0% 0%;
      }
      50% {
        background-position: 100% 50%;
      }
      100% {
        background-position: 0% 0%;
      }
    }

    @keyframes phoneFloat {
      0% {
        transform: translate3d(0, 0, 0) rotate3d(0, 1, 0, -6deg) rotate3d(1, 0, 0, 9deg);
      }
      50% {
        transform: translate3d(0, -10px, 0) rotate3d(0, 1, 0, -2deg) rotate3d(1, 0, 0, 6deg);
      }
      100% {
        transform: translate3d(0, 0, 0) rotate3d(0, 1, 0, -6deg) rotate3d(1, 0, 0, 9deg);
      }
    }

    @keyframes phoneEnter {
      from {
        opacity: 0;
        transform: translate3d(0, 40px, 0) rotate3d(0, 1, 0, -18deg) rotate3d(1, 0, 0, 24deg);
      }
      to {
        opacity: 1;
        transform: translate3d(0, 0, 0) rotate3d(0, 1, 0, -6deg) rotate3d(1, 0, 0, 9deg);
      }
    }

    @keyframes chipPulse {
      0% {
        box-shadow: 0 0 0 0 rgba(17, 17, 255, 0.35);
      }
      80% {
        box-shadow: 0 0 0 18px rgba(17, 17, 255, 0);
      }
      100% {
        box-shadow: 0 0 0 0 rgba(17, 17, 255, 0);
      }
    }

    @keyframes messageSlideUp {
      from {
        opacity: 0;
        transform: translateY(12px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    /* ------------------------------
       LAYOUT / PAGE SHELL
    ------------------------------ */

    .l-page {
      min-height: 100vh;
      background-image: var(--color-gradient-hero);
      background-size: 200% 200%;
      animation: gradientShift 22s ease-in-out infinite alternate;
    }

    .l-page-inner {
      max-width: var(--content-max-width);
      margin: 0 auto;
      padding: var(--space-l) var(--space-m) var(--space-3xl);
    }

    @media (min-width: 960px) {
      .l-page-inner {
        padding-top: var(--space-2xl);
        padding-bottom: var(--space-3xl);
      }
    }

    .l-header {
      position: sticky;
      top: 0;
      z-index: var(--z-header);
      backdrop-filter: blur(18px);
      background: linear-gradient(to bottom,
        color-mix(in srgb, var(--color-bg-app) 88%, transparent),
        color-mix(in srgb, var(--color-bg-app) 72%, transparent)
      );
      border-bottom: 1px solid var(--color-border-subtle);
    }

    .l-header-inner {
      max-width: var(--content-max-width);
      margin: 0 auto;
      padding: 10px var(--space-m);
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: var(--space-m);
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .brand-mark {
      width: 28px;
      height: 28px;
      border-radius: 10px;
      background: radial-gradient(circle at 0% 0%, #ffffff, #d0d0ff 38%, #0000d8 100%);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      color: #050509;
      font-weight: 800;
      font-family: var(--font-display);
      font-size: 14px;
      letter-spacing: 0.06em;
      box-shadow: 0 10px 25px rgba(0, 0, 40, 0.45);
    }

    html[data-theme="dark"] .brand-mark {
      background: radial-gradient(circle at 0% 0%, #ffffff, #a5a5ff 36%, #1b1bff 100%);
      color: #050509;
    }

    .brand-text-main {
      font-family: var(--font-display);
      font-size: 17px;
      font-weight: 700;
      letter-spacing: 0.18em;
      text-transform: uppercase;
    }

    .brand-text-sub {
      font-size: 11px;
      color: var(--color-text-soft);
      margin-top: 2px;
    }

    .header-right {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .header-pill {
      padding: 4px 10px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-elevated) 80%, transparent);
      font-size: 11px;
      color: var(--color-text-soft);
      display: inline-flex;
      align-items: center;
      gap: 6px;
      white-space: nowrap;
    }

    .header-pill-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: radial-gradient(circle at 0% 0%, #ffffff, var(--color-accent-strong));
      box-shadow: 0 0 0 4px rgba(17, 17, 255, 0.15);
    }

    .header-pill-label {
      font-weight: 500;
    }

    /* ------------------------------
       THEME TOGGLE (Солнце / Луна)
    ------------------------------ */

    .theme-toggle {
      position: relative;
      width: 46px;
      height: 24px;
      border-radius: 999px;
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-soft) 70%, transparent);
      display: inline-flex;
      align-items: center;
      padding: 2px;
      cursor: pointer;
      transition:
        background var(--motion-normal) var(--easing-standard),
        border-color var(--motion-normal) var(--easing-standard);
    }

    .theme-toggle-knob {
      width: 18px;
      height: 18px;
      border-radius: 999px;
      background: #ffffff;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.22);
      display: flex;
      align-items: center;
      justify-content: center;
      transform: translateX(0);
      transition:
        transform var(--motion-normal) var(--easing-soft),
        background var(--motion-normal) var(--easing-soft);
      color: #f4b000;
      font-size: 11px;
    }

    .theme-toggle-rail {
      position: absolute;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 3px 6px;
      pointer-events: none;
      font-size: 9px;
      color: var(--color-text-softer);
    }

    .theme-toggle-icon {
      opacity: 0.65;
      transition: opacity var(--motion-normal) var(--easing-standard), transform var(--motion-normal) var(--easing-standard);
    }

    .theme-toggle-icon.sun {
      transform-origin: left center;
    }

    .theme-toggle-icon.moon {
      transform-origin: right center;
    }

    html[data-theme="dark"] .theme-toggle-knob {
      transform: translateX(20px);
      background: #050509;
      color: #f9f9ff;
    }

    html[data-theme="dark"] .theme-toggle {
      background: radial-gradient(circle at 0 0, #202047, #050509);
      border-color: rgba(255, 255, 255, 0.16);
    }

    html[data-theme="dark"] .theme-toggle-icon.sun {
      opacity: 0.3;
      transform: scale(0.85);
    }

    html[data-theme="dark"] .theme-toggle-icon.moon {
      opacity: 0.9;
      transform: scale(1.1);
    }

    /* ------------------------------
       УТИЛИТЫ
    ------------------------------ */

    .u-kbd {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 2px 6px;
      border-radius: 6px;
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-elevated) 90%, transparent);
      font-size: 10px;
      font-family: var(--font-sans);
    }

    .u-pill-soft {
      border-radius: var(--radius-pill);
      padding: 4px 10px;
      font-size: 11px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      color: var(--color-text-soft);
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .u-pill-soft strong {
      font-weight: 600;
      color: var(--color-text-main);
    }

    .u-eyebrow {
      font-size: 11px;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--color-text-soft);
      font-weight: 600;
    }

    .u-h1 {
      font-family: var(--font-display);
      font-size: clamp(28px, 5vw, 40px);
      line-height: 1.1;
      letter-spacing: 0.03em;
      margin: 0;
    }

    .u-h2 {
      font-family: var(--font-display);
      font-size: clamp(20px, 3vw, 26px);
      line-height: 1.15;
      margin: 0;
    }

    .u-body-main {
      font-size: 14px;
      line-height: 1.6;
      color: var(--color-text-soft);
    }

    .u-body-small {
      font-size: 12px;
      line-height: 1.5;
      color: var(--color-text-softer);
    }

    .u-section {
      padding-top: var(--space-2xl);
      padding-bottom: var(--space-2xl);
    }

    .u-section:first-of-type {
      padding-top: var(--space-xl);
    }

    @media (min-width: 960px) {
      .u-section {
        padding-top: var(--space-3xl);
        padding-bottom: var(--space-3xl);
      }
    }

    .u-section-header {
      margin-bottom: var(--space-l);
      animation: fadeInSoft var(--motion-slow) var(--easing-soft) both;
    }

    .u-grid-hero {
      display: grid;
      grid-template-columns: minmax(0, 1.1fr);
      gap: var(--space-xl);
      align-items: center;
    }

    @media (min-width: 960px) {
      .u-grid-hero {
        grid-template-columns: minmax(0, 1.1fr) minmax(0, 0.95fr);
      }
    }

    .u-reveal {
      opacity: 0;
      transform: translateY(24px);
      filter: blur(6px);
      transition:
        opacity var(--motion-slow) var(--easing-soft),
        transform var(--motion-slow) var(--easing-soft),
        filter var(--motion-slow) var(--easing-soft);
    }

    .u-reveal.is-visible {
      opacity: 1;
      transform: translateY(0);
      filter: blur(0);
    }

    .u-divider {
      height: 1px;
      border-radius: 999px;
      background: linear-gradient(to right,
        transparent,
        color-mix(in srgb, var(--color-border-subtle) 80%, transparent),
        transparent
      );
      margin: var(--space-2xl) 0;
    }

    /* ------------------------------
       КОМПОНЕНТЫ: КНОПКИ / КАРТОЧКИ
    ------------------------------ */

    .c-button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      border-radius: var(--radius-pill);
      border: 1px solid transparent;
      padding: 10px 18px;
      font-size: 13px;
      font-weight: 600;
      letter-spacing: 0.02em;
      cursor: pointer;
      outline: none;
      background: var(--color-accent);
      color: #ffffff;
      box-shadow: 0 14px 30px rgba(0, 0, 60, 0.45);
      transform: translateY(0);
      transition:
        box-shadow var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard),
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        color var(--motion-fast) var(--easing-standard);
    }

    .c-button span {
      display: inline-flex;
      align-items: center;
      justify-content: center;
    }

    .c-button-icon {
      font-size: 15px;
      line-height: 1;
    }

    .c-button:hover {
      transform: translateY(-1px);
      box-shadow: 0 18px 40px rgba(0, 0, 60, 0.55);
      background: var(--color-accent-strong);
    }

    .c-button:active {
      transform: translateY(0);
      box-shadow: 0 8px 22px rgba(0, 0, 40, 0.6);
    }

    .c-button--ghost {
      background: transparent;
      color: var(--color-text-main);
      border-color: var(--color-border-subtle);
      box-shadow: none;
    }

    .c-button--ghost:hover {
      background: var(--color-chip-bg);
      border-color: var(--color-border-strong);
      box-shadow: none;
    }

    .c-button--secondary {
      background: var(--color-chip-bg);
      border-color: var(--color-chip-border);
      color: var(--color-text-main);
      box-shadow: none;
    }

    .c-button--secondary:hover {
      background: color-mix(in srgb, var(--color-chip-bg) 70%, var(--color-accent-soft));
      border-color: var(--color-border-strong);
    }

    .c-button--sm {
      padding: 7px 14px;
      font-size: 12px;
    }

    .c-card {
      position: relative;
      border-radius: var(--radius-xl);
      background: color-mix(in srgb, var(--color-bg-elevated) 94%, transparent);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--color-shadow-soft);
      padding: var(--space-l);
      overflow: hidden;
    }

    html[data-theme="dark"] .c-card {
      background: radial-gradient(circle at 0 0, rgba(127, 127, 255, 0.16), transparent 70%), var(--color-bg-elevated);
    }

    .c-card--soft {
      border-radius: var(--radius-l);
      padding: var(--space-m);
      box-shadow: none;
      background: color-mix(in srgb, var(--color-bg-elevated) 88%, transparent);
    }

    .c-badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      border-radius: var(--radius-pill);
      padding: 4px 10px;
      font-size: 11px;
      background: var(--color-accent-soft);
      color: var(--color-accent-strong);
    }

    .c-badge-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: radial-gradient(circle at 0 0, #ffffff, var(--color-accent-strong));
    }

    .c-chip {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      border-radius: var(--radius-pill);
      padding: 6px 12px;
      font-size: 12px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      color: var(--color-text-soft);
      cursor: pointer;
      transition:
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        color var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard);
    }

    .c-chip:hover {
      transform: translateY(-1px);
      border-color: var(--color-border-strong);
      color: var(--color-text-main);
    }

    .c-chip--active {
      background: var(--color-accent);
      border-color: var(--color-accent);
      color: #ffffff;
      box-shadow: 0 0 0 0 rgba(17, 17, 255, 0.4);
      animation: chipPulse 2.2s var(--easing-soft) infinite;
    }

    .c-chip-group {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    /* ------------------------------
       HERO + IPHONE
    ------------------------------ */

    .hero {
      position: relative;
      display: grid;
      grid-template-columns: minmax(0, 1.1fr);
      gap: var(--space-xl);
      align-items: center;
      margin-top: var(--space-xl);
      animation: fadeInUpBig 520ms var(--easing-soft) both;
    }

    @media (min-width: 960px) {
      .hero {
        grid-template-columns: minmax(0, 1.1fr) minmax(0, 0.95fr);
      }
    }

    .hero-copy {
      display: flex;
      flex-direction: column;
      gap: var(--space-m);
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
      margin-top: 6px;
    }

    .hero-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: var(--space-s);
    }

    .hero-arrow {
      margin-top: var(--space-m);
      font-size: 11px;
      display: inline-flex;
      flex-direction: column;
      gap: 4px;
      color: var(--color-text-softer);
      align-items: flex-start;
    }

    .hero-arrow-icon {
      width: 16px;
      height: 24px;
      border-radius: 999px;
      border: 1px solid var(--color-border-subtle);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 12px;
      animation: fadeInSoft 1.2s var(--easing-soft) both infinite alternate;
    }

    /* ---------- iPhone сцена ---------- */

    .phone-scene {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      padding-bottom: var(--space-l);
      will-change: transform;
    }

    .phone-parallax {
      position: relative;
      transition: transform 260ms var(--easing-soft);
    }

    .phone-glow {
      position: absolute;
      inset: 40px -40px -40px;
      background:
        radial-gradient(circle at 20% 0%, rgba(255, 255, 255, 0.32), transparent 55%),
        radial-gradient(circle at 80% 120%, rgba(0, 0, 0, 0.78), transparent 60%);
      filter: blur(12px);
      opacity: 0.8;
      z-index: var(--z-phone-glow);
      pointer-events: none;
    }

    html[data-theme="dark"] .phone-glow {
      background:
        radial-gradient(circle at 20% 0%, rgba(127, 127, 255, 0.6), transparent 55%),
        radial-gradient(circle at 80% 120%, rgba(0, 0, 0, 1), transparent 60%);
    }

    .phone-device {
      position: relative;
      width: min(320px, 85vw);
      border-radius: 38px;
      padding: 12px;
      background: radial-gradient(circle at 0 0, #ffffff, #d5d7e5);
      box-shadow: var(--color-shadow-phone);
      transform-origin: center;
      animation:
        phoneEnter 640ms var(--easing-soft) both,
        phoneFloat 16s ease-in-out 800ms infinite;
      z-index: var(--z-phone);
    }

    html[data-theme="dark"] .phone-device {
      background: radial-gradient(circle at 0 0, #e5e5ff, #8888b8);
    }

    .phone-inner {
      border-radius: 30px;
      background: var(--color-phone-shell);
      padding: 9px 7px 11px;
      position: relative;
    }

    .phone-notch {
      position: absolute;
      top: 6px;
      left: 50%;
      transform: translateX(-50%);
      width: 88px;
      height: 18px;
      border-radius: 999px;
      background: linear-gradient(to bottom, #050509, #151520);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
    }

    .phone-notch-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: radial-gradient(circle at 0 0, #ffffff, #777799);
      opacity: 0.9;
    }

    .phone-notch-line {
      width: 34px;
      height: 4px;
      border-radius: 999px;
      background: linear-gradient(to right, #2f2f3f, #171725);
    }

    .phone-screen {
      margin-top: 18px;
      border-radius: 26px;
      background: linear-gradient(180deg, #050509, #050509 40%, #060612 100%);
      padding: 10px 8px 12px;
      position: relative;
      overflow: hidden;
      box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.04);
    }

    html[data-theme="dark"] .phone-screen {
      background: linear-gradient(180deg, #050509, #050509 42%, #050509 100%);
    }

    .phone-statusbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 9px;
      color: #b3b3c7;
      margin-bottom: 6px;
    }

    .phone-statusbar-right {
      display: inline-flex;
      gap: 4px;
      align-items: center;
    }

    .phone-dot-pill {
      border-radius: 999px;
      padding: 2px 6px;
      border: 1px solid rgba(255, 255, 255, 0.14);
      font-size: 8px;
      display: inline-flex;
      align-items: center;
      gap: 4px;
    }

    .phone-dot-pill-dot {
      width: 3px;
      height: 3px;
      border-radius: 999px;
      background: #3cffd0;
    }

    .phone-screen-nav {
      display: flex;
      gap: 6px;
      margin-bottom: 10px;
      flex-wrap: wrap;
    }

    .phone-screen-chip {
      flex: 1 0 auto;
      padding: 4px 8px;
      border-radius: 999px;
      border: 1px solid rgba(255, 255, 255, 0.12);
      font-size: 9px;
      color: #c0c0d7;
      background: rgba(255, 255, 255, 0.02);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 4px;
      cursor: pointer;
      opacity: 0.75;
      transition:
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        opacity var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard);
    }

    .phone-screen-chip-dot {
      width: 4px;
      height: 4px;
      border-radius: 999px;
      background: #8f8fff;
    }

    .phone-screen-chip.is-active {
      border-color: #8f8fff;
      background: linear-gradient(120deg, rgba(143, 143, 255, 0.3), transparent);
      color: #ffffff;
      opacity: 1;
      transform: translateY(-1px);
    }

    .phone-screen-viewport {
      position: relative;
      border-radius: 18px;
      background: radial-gradient(circle at 0 0, rgba(143, 143, 255, 0.28), transparent 55%);
      padding: 8px 6px 10px;
      overflow: hidden;
      min-height: 172px;
    }

    .phone-screen-slide {
      position: absolute;
      inset: 0;
      padding: 2px;
      opacity: 0;
      transform: translateY(10px);
      pointer-events: none;
      transition:
        opacity var(--motion-normal) var(--easing-soft),
        transform var(--motion-normal) var(--easing-soft);
    }

    .phone-screen-slide.is-active {
      opacity: 1;
      transform: translateY(0);
      pointer-events: auto;
    }

    /* Слайды: 1) онбординг / чат, 2) индекс, 3) модули */

    .phone-chat {
      display: flex;
      flex-direction: column;
      gap: 4px;
      font-size: 10px;
    }

    .phone-msg-row {
      display: flex;
      margin-bottom: 2px;
    }

    .phone-msg-row.me {
      justify-content: flex-end;
    }

    .phone-msg {
      max-width: 84%;
      padding: 6px 8px;
      border-radius: 14px;
      line-height: 1.35;
      animation: messageSlideUp 260ms var(--easing-soft) both;
    }

    .phone-msg.bot {
      background: rgba(18, 18, 40, 0.88);
      color: #f5f5ff;
      border-bottom-left-radius: 4px;
    }

    .phone-msg.me {
      background: #f5f5ff;
      color: #050509;
      border-bottom-right-radius: 4px;
    }

    .phone-msg-meta {
      font-size: 8px;
      color: #8080a0;
      margin-top: 2px;
    }

    .phone-typing {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      font-size: 8px;
      color: #a9a9c8;
      margin-top: 3px;
    }

    .phone-typing-dot {
      width: 3px;
      height: 3px;
      border-radius: 999px;
      background: #a9a9c8;
      opacity: 0.4;
      animation: typingBlink 1.2s infinite ease-in-out;
    }

    .phone-typing-dot:nth-child(2) {
      animation-delay: 0.15s;
    }

    .phone-typing-dot:nth-child(3) {
      animation-delay: 0.3s;
    }

    @keyframes typingBlink {
      0% { opacity: 0.3; transform: translateY(0); }
      50% { opacity: 0.9; transform: translateY(-1px); }
      100% { opacity: 0.3; transform: translateY(0); }
    }

    /* Слайд индекс дня */

    .phone-index-card {
      border-radius: 14px;
      padding: 8px;
      background: rgba(8, 8, 22, 0.88);
      color: #f5f5ff;
      font-size: 9px;
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    .phone-index-top {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      gap: 6px;
    }

    .phone-index-label {
      font-size: 9px;
      text-transform: uppercase;
      letter-spacing: 0.16em;
      color: #a9a9c8;
    }

    .phone-index-value {
      font-family: var(--font-display);
      font-size: 22px;
      font-weight: 700;
    }

    .phone-index-max {
      font-size: 10px;
      color: #c0c0dd;
    }

    .phone-index-bar {
      height: 6px;
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.08);
      overflow: hidden;
      margin-top: 4px;
      position: relative;
    }

    .phone-index-bar-fill {
      position: absolute;
      inset: 0;
      width: 60%; /* 3 из 5 */
      border-radius: inherit;
      background: linear-gradient(90deg, #ff6b8c, #ffbf69, #4ade80);
    }

    .phone-index-pills {
      display: flex;
      gap: 4px;
      margin-top: 4px;
    }

    .phone-index-pill {
      flex: 1;
      border-radius: 999px;
      padding: 3px 4px;
      text-align: center;
      font-size: 8px;
      background: rgba(255, 255, 255, 0.04);
    }

    .phone-index-pill span {
      display: block;
      font-size: 8px;
      color: #a9a9c8;
    }

    .phone-index-pill strong {
      font-size: 10px;
      color: #f5f5ff;
    }

    /* Слайд модули */

    .phone-modules {
      display: flex;
      flex-direction: column;
      gap: 5px;
      font-size: 9px;
    }

    .phone-mod {
      border-radius: 12px;
      padding: 5px 7px;
      background: rgba(10, 10, 26, 0.9);
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 6px;
    }

    .phone-mod-main {
      display: flex;
      flex-direction: column;
      gap: 1px;
    }

    .phone-mod-title {
      font-weight: 600;
    }

    .phone-mod-sub {
      color: #a9a9c8;
      font-size: 8px;
    }

    .phone-mod-pill {
      border-radius: 999px;
      padding: 3px 6px;
      background: rgba(255, 255, 255, 0.06);
      font-size: 8px;
    }

    /* ------------------------------
       СЕКЦИЯ: КАК ЭТО ОЩУЩАЕТСЯ
    ------------------------------ */

    .story {
      display: grid;
      grid-template-columns: minmax(0, 1.05fr);
      gap: var(--space-l);
      align-items: flex-start;
    }

    @media (min-width: 960px) {
      .story {
        grid-template-columns: minmax(0, 0.9fr) minmax(0, 1.1fr);
      }
    }

    .story-text {
      max-width: 480px;
    }

    .story-chat {
      border-radius: var(--radius-xl);
      background: color-mix(in srgb, var(--color-bg-elevated) 88%, transparent);
      border: 1px solid var(--color-border-subtle);
      padding: var(--space-m);
      box-shadow: var(--color-shadow-soft);
    }

    .story-chat-inner {
      max-height: 320px;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }

    .story-msg-row {
      display: flex;
      margin-bottom: 4px;
    }

    .story-msg-row.me {
      justify-content: flex-end;
    }

    .story-msg {
      max-width: 78%;
      border-radius: 18px;
      padding: 8px 11px;
      font-size: 13px;
      line-height: 1.4;
      animation: messageSlideUp 260ms var(--easing-soft) both;
    }

    .story-msg.bot {
      background: color-mix(in srgb, var(--color-bg-soft) 80%, transparent);
      color: var(--color-text-main);
      border-bottom-left-radius: 6px;
    }

    .story-msg.me {
      background: var(--color-accent);
      color: #ffffff;
      border-bottom-right-radius: 6px;
    }

    .story-msg-label {
      font-size: 10px;
      font-weight: 600;
      margin-bottom: 4px;
      opacity: 0.7;
    }

    /* ------------------------------
       СЕКЦИЯ: ИНДЕКС ДНЯ 1–5
    ------------------------------ */

    .index-section-grid {
      display: grid;
      grid-template-columns: minmax(0, 1.1fr);
      gap: var(--space-l);
    }

    @media (min-width: 960px) {
      .index-section-grid {
        grid-template-columns: minmax(0, 1.1fr) minmax(0, 0.9fr);
      }
    }

    .index-main-card {
      border-radius: var(--radius-xl);
      padding: var(--space-l);
      background: color-mix(in srgb, var(--color-bg-elevated) 94%, transparent);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--color-shadow-soft);
    }

    .index-main-header {
      display: flex;
      justify-content: space-between;
      gap: var(--space-s);
      align-items: baseline;
      margin-bottom: var(--space-s);
    }

    .index-main-value {
      font-family: var(--font-display);
      font-size: 40px;
      font-weight: 700;
      letter-spacing: 0.04em;
    }

    .index-main-max {
      font-size: 13px;
      color: var(--color-text-soft);
    }

    .index-main-bar {
      height: 10px;
      border-radius: 999px;
      background: var(--color-bg-soft);
      position: relative;
      overflow: hidden;
    }

    .index-main-bar-fill {
      position: absolute;
      inset: 0;
      width: 60%; /* пример 3 из 5 */
      border-radius: inherit;
      background: linear-gradient(90deg, #ff6b8c, #ffbf69, #4ade80);
    }

    .index-mini-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: var(--space-s);
      margin-top: var(--space-m);
      font-size: 12px;
    }

    .index-mini-card {
      border-radius: var(--radius-m);
      border: 1px solid var(--color-border-subtle);
      padding: 10px 10px 10px;
      background: color-mix(in srgb, var(--color-bg-elevated) 92%, transparent);
    }

    .index-mini-label {
      font-size: 11px;
      color: var(--color-text-soft);
      margin-bottom: 4px;
    }

    .index-mini-value {
      font-family: var(--font-display);
      font-size: 16px;
      font-weight: 700;
    }

    .index-legend {
      margin-top: var(--space-s);
      font-size: 11px;
      color: var(--color-text-softer);
    }

    .index-pill-row {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: var(--space-xs);
    }

    .index-pill {
      border-radius: var(--radius-pill);
      padding: 3px 8px;
      font-size: 11px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      color: var(--color-text-soft);
    }

    /* ------------------------------
       СЕКЦИЯ: КЕЙС ДО/ПОСЛЕ
    ------------------------------ */

    .case-grid {
      display: grid;
      grid-template-columns: minmax(0, 1fr);
      gap: var(--space-l);
    }

    @media (min-width: 960px) {
      .case-grid {
        grid-template-columns: minmax(0, 1fr) minmax(0, 1fr);
      }
    }

    .case-card {
      border-radius: var(--radius-xl);
      padding: var(--space-l);
      background: color-mix(in srgb, var(--color-bg-elevated) 94%, transparent);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--color-shadow-soft);
      position: relative;
      overflow: hidden;
    }

    .case-pill {
      border-radius: var(--radius-pill);
      padding: 4px 10px;
      font-size: 11px;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: var(--color-chip-bg);
      border: 1px solid var(--color-chip-border);
      margin-bottom: var(--space-xs);
    }

    .case-pill--before {
      color: var(--color-danger);
      border-color: color-mix(in srgb, var(--color-danger) 40%, var(--color-chip-border));
    }

    .case-pill--after {
      color: var(--color-success);
      border-color: color-mix(in srgb, var(--color-success) 40%, var(--color-chip-border));
    }

    .case-metric-row {
      display: flex;
      gap: var(--space-s);
      margin-top: var(--space-m);
    }

    .case-metric {
      flex: 1;
      border-radius: var(--radius-m);
      border: 1px dashed var(--color-border-subtle);
      padding: 8px 10px;
      font-size: 12px;
    }

    .case-metric-label {
      font-size: 11px;
      color: var(--color-text-soft);
      margin-bottom: 4px;
    }

    .case-metric-value {
      font-family: var(--font-display);
      font-size: 18px;
      font-weight: 700;
    }

    /* ------------------------------
       СЕКЦИЯ: МОДУЛИ
    ------------------------------ */

    .modules-card {
      border-radius: var(--radius-xl);
      padding: var(--space-l);
      background: color-mix(in srgb, var(--color-bg-elevated) 94%, transparent);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--color-shadow-soft);
      display: grid;
      grid-template-columns: minmax(0, 0.95fr);
      gap: var(--space-m);
    }

    @media (min-width: 960px) {
      .modules-card {
        grid-template-columns: minmax(0, 0.9fr) minmax(0, 1.05fr);
      }
    }

    .modules-tabs {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .modules-tab {
      border-radius: var(--radius-pill);
      padding: 8px 14px;
      font-size: 13px;
      border: 1px solid var(--color-chip-border);
      background: var(--color-chip-bg);
      display: flex;
      align-items: center;
      justify-content: space-between;
      cursor: pointer;
      transition:
        background var(--motion-fast) var(--easing-standard),
        border-color var(--motion-fast) var(--easing-standard),
        transform var(--motion-fast) var(--easing-standard);
    }

    .modules-tab-label {
      font-weight: 600;
    }

    .modules-tab-icon {
      font-size: 14px;
    }

    .modules-tab.is-active {
      background: var(--color-accent);
      border-color: var(--color-accent);
      color: #ffffff;
      transform: translateY(-1px);
      box-shadow: 0 12px 30px rgba(0, 0, 60, 0.4);
    }

    .modules-content {
      border-radius: var(--radius-l);
      padding: var(--space-m);
      background: color-mix(in srgb, var(--color-bg-soft) 80%, transparent);
      border: 1px solid var(--color-border-subtle);
      font-size: 13px;
    }

    .modules-content-panel {
      display: none;
    }

    .modules-content-panel.is-active {
      display: block;
    }

    .modules-bullets {
      margin-top: var(--space-xs);
      font-size: 12px;
      color: var(--color-text-soft);
    }

    .modules-bullets li {
      margin-bottom: 4px;
    }

    /* ------------------------------
       FAQ
    ------------------------------ */

    .faq-grid {
      max-width: 760px;
      margin: 0;
      padding: 0;
      list-style: none;
    }

    .faq-item {
      border-radius: var(--radius-l);
      border: 1px solid var(--color-border-subtle);
      background: color-mix(in srgb, var(--color-bg-elevated) 92%, transparent);
      margin-bottom: var(--space-s);
      overflow: hidden;
    }

    .faq-question {
      width: 100%;
      text-align: left;
      padding: 12px 14px;
      background: transparent;
      border: none;
      outline: none;
      display: flex;
      justify-content: space-between;
      align-items: center;
      cursor: pointer;
      font-size: 13px;
      font-weight: 500;
      color: var(--color-text-main);
    }

    .faq-icon {
      font-size: 18px;
      line-height: 1;
      transform: rotate(0deg);
      transition: transform var(--motion-normal) var(--easing-standard);
      color: var(--color-text-softer);
    }

    .faq-item.is-open .faq-icon {
      transform: rotate(45deg);
    }

    .faq-answer {
      max-height: 0;
      overflow: hidden;
      transition: max-height var(--motion-slow) var(--easing-soft);
      padding: 0 14px;
    }

    .faq-answer-inner {
      padding-bottom: 12px;
      font-size: 13px;
      color: var(--color-text-soft);
    }

    .faq-item.is-open .faq-answer {
      max-height: 200px;
    }

    /* ------------------------------
       CTA
    ------------------------------ */

    .cta-card {
      border-radius: var(--radius-xl);
      padding: var(--space-l);
      background: linear-gradient(135deg, var(--color-accent), var(--color-accent-strong));
      color: #ffffff;
      box-shadow: 0 22px 50px rgba(0, 0, 60, 0.7);
      text-align: center;
    }

    .cta-card h2 {
      margin: 0 0 var(--space-xs);
      font-family: var(--font-display);
      font-size: clamp(22px, 3.2vw, 28px);
    }

    .cta-card p {
      margin: 0 0 var(--space-m);
      font-size: 14px;
      opacity: 0.9;
    }

    .cta-buttons {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
    }

    .cta-secondary {
      border-radius: var(--radius-pill);
      padding: 8px 14px;
      border: 1px solid rgba(255, 255, 255, 0.5);
      font-size: 12px;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      cursor: pointer;
      background: transparent;
      color: #ffffff;
    }

    .cta-secondary span {
      display: inline-flex;
      align-items: center;
    }

    .cta-secondary-icon {
      font-size: 14px;
    }
  </style>
</head>
<body class="l-page">
  <header class="l-header">
    <div class="l-header-inner">
      <div class="brand">
        <div class="brand-mark">A</div>
        <div>
          <div class="brand-text-main">ADVICE</div>
          <div class="brand-text-sub">бот-психолог внутри Telegram</div>
        </div>
      </div>
      <div class="header-right">
        <div class="header-pill">
          <span class="header-pill-dot"></span>
          <span class="header-pill-label">Работает в Telegram</span>
        </div>
        <button class="theme-toggle" type="button" id="theme-toggle" aria-label="Переключить тему">
          <div class="theme-toggle-rail">
            <span class="theme-toggle-icon sun">☀️</span>
            <span class="theme-toggle-icon moon">🌙</span>
          </div>
          <div class="theme-toggle-knob" aria-hidden="true">☀️</div>
        </button>
      </div>
    </div>
  </header>

  <main class="l-page-inner">
    <!-- HERO + IPHONE -->
    <section class="u-section hero" id="hero">
      <div class="hero-copy u-reveal js-reveal">
        <div class="u-eyebrow">Твой день в трёх цифрах</div>
        <h1 class="u-h1">
          Бот, с которым удобно говорить о себе
          и не терять опору в повседневности.
        </h1>
        <p class="u-body-main">
          ADVICE живёт прямо в Telegram, задаёт короткие вопросы про психику, сон и деньги,
          считает индекс дня от 1 до 5 и помогает увидеть, где ты реально проседаешь.
        </p>
        <div class="hero-actions">
          <a href="https://t.me/your_advice_bot" class="c-button">
            <span>Открыть бота в Telegram</span>
            <span class="c-button-icon">↗</span>
          </a>
          <button class="c-button c-button--ghost c-button--sm" type="button" id="scroll-to-story">
            <span>Посмотреть, как это внутри</span>
          </button>
        </div>
        <div class="hero-meta">
          <div class="u-pill-soft">
            <span>Индекс дня&nbsp;<strong>от 1 до 5</strong></span>
          </div>
          <div class="u-pill-soft">
            <span>Психика · Сон · Деньги</span>
          </div>
        </div>
        <div class="hero-arrow">
          <span>Прокрути вниз, чтобы увидеть, как выглядит бот.</span>
          <div class="hero-arrow-icon">↓</div>
        </div>
      </div>

      <!-- iPhone сцена -->
      <div class="phone-scene u-reveal js-reveal">
        <div class="phone-parallax">
          <div class="phone-glow"></div>
          <div class="phone-device">
            <div class="phone-inner">
              <div class="phone-notch">
                <div class="phone-notch-line"></div>
                <div class="phone-notch-dot"></div>
              </div>
              <div class="phone-screen">
                <div class="phone-statusbar">
                  <span>ADVICE · онлайн</span>
                  <div class="phone-statusbar-right">
                    <div class="phone-dot-pill">
                      <span class="phone-dot-pill-dot"></span>
                      <span>AI + человек</span>
                    </div>
                  </div>
                </div>

                <div class="phone-screen-nav">
                  <button class="phone-screen-chip is-active" data-screen="welcome" type="button">
                    <span class="phone-screen-chip-dot"></span>
                    <span>Приветствие</span>
                  </button>
                  <button class="phone-screen-chip" data-screen="index" type="button">
                    <span class="phone-screen-chip-dot"></span>
                    <span>Индекс дня</span>
                  </button>
                  <button class="phone-screen-chip" data-screen="modules" type="button">
                    <span class="phone-screen-chip-dot"></span>
                    <span>Модули</span>
                  </button>
                </div>

                <div class="phone-screen-viewport">
                  <!-- Слайд 1: приветствие / чат -->
                  <div class="phone-screen-slide is-active" data-screen-id="welcome">
                    <div class="phone-chat">
                      <div class="phone-msg-row">
                        <div class="phone-msg bot">
                          Привет. Я ADVICE — бот, который помогает держать в фокусе психику, сон и деньги.
                          <div class="phone-msg-meta">только ты и этот чат</div>
                        </div>
                      </div>
                      <div class="phone-msg-row">
                        <div class="phone-msg bot">
                          Я задам три коротких вопроса и соберу индекс дня. Дальше сможем работать уже с деталями.
                        </div>
                      </div>
                      <div class="phone-msg-row me">
                        <div class="phone-msg me">
                          Окей, давай попробуем.
                        </div>
                      </div>
                      <div class="phone-msg-row">
                        <div class="phone-msg bot">
                          Начнём с психики. Как по ощущениям сейчас: больше про «выдерживаю» или «проседаю»?
                          <div class="phone-typing">
                            <div class="phone-typing-dot"></div>
                            <div class="phone-typing-dot"></div>
                            <div class="phone-typing-dot"></div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>

                  <!-- Слайд 2: индекс дня 1–5 -->
                  <div class="phone-screen-slide" data-screen-id="index">
                    <div class="phone-index-card">
                      <div class="phone-index-top">
                        <div>
                          <div class="phone-index-label">Качество дня</div>
                          <div class="phone-index-value">3,1</div>
                        </div>
                        <div class="phone-index-max">из 5 возможных</div>
                      </div>
                      <div class="phone-index-bar">
                        <div class="phone-index-bar-fill"></div>
                      </div>
                      <div class="phone-index-pills">
                        <div class="phone-index-pill">
                          <span>психика</span>
                          <strong>3,4</strong>
                        </div>
                        <div class="phone-index-pill">
                          <span>сон</span>
                          <strong>2,7</strong>
                        </div>
                        <div class="phone-index-pill">
                          <span>деньги</span>
                          <strong>3,2</strong>
                        </div>
                      </div>
                      <div class="phone-msg-meta" style="margin-top:6px;">
                        Сегодня чуть проседает сон. Я предложу небольшой план, как восстановить ресурс.
                      </div>
                    </div>
                  </div>

                  <!-- Слайд 3: модули -->
                  <div class="phone-screen-slide" data-screen-id="modules">
                    <div class="phone-modules">
                      <div class="phone-mod">
                        <div class="phone-mod-main">
                          <div class="phone-mod-title">Психолог</div>
                          <div class="phone-mod-sub">диалог без осуждения, плюс команда специалистов</div>
                        </div>
                        <div class="phone-mod-pill">чат 24/7</div>
                      </div>
                      <div class="phone-mod">
                        <div class="phone-mod-main">
                          <div class="phone-mod-title">Сон</div>
                          <div class="phone-mod-sub">режим, ритуалы, звуки и корректировка по факту</div>
                        </div>
                        <div class="phone-mod-pill">режим под тебя</div>
                      </div>
                      <div class="phone-mod">
                        <div class="phone-mod-main">
                          <div class="phone-mod-title">Деньги</div>
                          <div class="phone-mod-sub">доход, расходы и привычка откладывать без жёсткой экономии</div>
                        </div>
                        <div class="phone-mod-pill">пошаговый план</div>
                      </div>
                    </div>
                  </div>

                </div><!-- /.phone-screen-viewport -->
              </div><!-- /.phone-screen -->
            </div><!-- /.phone-inner -->
          </div><!-- /.phone-device -->
        </div><!-- /.phone-parallax -->
      </div><!-- /.phone-scene -->
    </section>

    <div class="u-divider"></div>

    <!-- СЕКЦИЯ: КАК ЭТО ОЩУЩАЕТСЯ ВНУТРИ БОТА -->
    <section class="u-section" id="story">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">Как это ощущается</div>
        <h2 class="u-h2">Выглядит как переписка в Telegram, но под капотом — система</h2>
        <p class="u-body-main" style="max-width: 520px; margin-top: 8px;">
          Никаких странных форм и анкет. Ты просто переписываешься с ботом, а он аккуратно
          вытаскивает важное и фиксирует динамику по трём зонам: психика, сон, деньги.
        </p>
      </div>

      <div class="story u-reveal js-reveal">
        <div class="story-text">
          <p class="u-body-main">
            Внутри ADVICE можно писать так, как ты реально думаешь и говоришь.
            Бот не требует «быть молодцом» каждый день, а трезво показывает, где ты сейчас
            и что можно сделать, чтобы стало легче.
          </p>
          <p class="u-body-main">
            Если видим, что что-то идёт не так — подключается команда живых специалистов.
            Но первый шаг всегда безопасный: просто написать в чат.
          </p>
          <div style="margin-top: var(--space-m);">
            <a href="https://t.me/your_advice_bot" class="c-button c-button--secondary">
              <span>Открыть диалог в Telegram</span>
              <span class="c-button-icon">↗</span>
            </a>
          </div>
        </div>

        <div class="story-chat">
          <div class="story-chat-inner">
            <div class="story-msg-row">
              <div class="story-msg bot">
                <div class="story-msg-label">ADVICE</div>
                Привет. Можно без формальностей — просто расскажи, что сейчас больше всего давит.
              </div>
            </div>
            <div class="story-msg-row me">
              <div class="story-msg me">
                Чувствую себя выжатым. Сон сбился, голова не отдыхает, постоянно думаю о деньгах.
              </div>
            </div>
            <div class="story-msg-row">
              <div class="story-msg bot">
                Окей, зафиксируем это и посмотрим в трёх плоскостях: психика, сон и финансы.
                Я помогу выстроить понятные опоры на каждый день.
              </div>
            </div>
            <div class="story-msg-row">
              <div class="story-msg bot">
                Сначала посчитаем индекс дня, потом покажу, откуда начать: с восстановления
                сна, с пересборки расписания или с денег.
              </div>
            </div>
            <div class="story-msg-row me">
              <div class="story-msg me">
                Звучит окей. Хочу наконец перестать «держаться на остатках».
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="u-divider"></div>

    <!-- СЕКЦИЯ: ИНДЕКС ДНЯ 1–5 -->
    <section class="u-section">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">Индекс дня</div>
        <h2 class="u-h2">Одна цифра от 1 до 5, за которой стоит реальная картина</h2>
        <p class="u-body-main" style="max-width: 520px; margin-top: 8px;">
          Каждый день ADVICE собирает индекс качества жизни: психика, сон, деньги.
          Не абстрактная «мотивация», а конкретный термометр по трём зонам, где ты можешь падать или расти.
        </p>
      </div>

      <div class="index-section-grid u-reveal js-reveal">
        <div class="index-main-card">
          <div class="index-main-header">
            <div>
              <div class="u-eyebrow" style="letter-spacing:0.2em;">Сегодня</div>
              <div class="index-main-value" data-target="3.1">0,0</div>
            </div>
            <div class="index-main-max">из 5 · нормальный, но не запасной день</div>
          </div>
          <div class="index-main-bar">
            <div class="index-main-bar-fill"></div>
          </div>
          <div class="index-mini-grid">
            <div class="index-mini-card">
              <div class="index-mini-label">Психика</div>
              <div class="index-mini-value">3,4</div>
              <div class="u-body-small">чуть напряжённо, но без красных зон</div>
            </div>
            <div class="index-mini-card">
              <div class="index-mini-label">Сон</div>
              <div class="index-mini-value">2,7</div>
              <div class="u-body-small">мало ресурса, стоит восстановиться</div>
            </div>
            <div class="index-mini-card">
              <div class="index-mini-label">Деньги</div>
              <div class="index-mini-value">3,2</div>
              <div class="u-body-small">контроль есть, но без подушки</div>
            </div>
          </div>
          <div class="index-legend">
            Каждый день индекс перезаписывается, и у тебя появляется хроника: где ты стабилен, а где
            системно проваливаешься.
          </div>
          <div class="index-pill-row">
            <div class="index-pill">1 — день на «аварийных системах»</div>
            <div class="index-pill">3 — держусь, но без большого запаса</div>
            <div class="index-pill">5 — устойчиво, можно брать сложные задачи</div>
          </div>
        </div>

        <div style="align-self:center;">
          <p class="u-body-main">
            Индекс дня — не оценка «ты молодец / не молодец», а инструмент. Если видим, что ты
            несколько дней подряд в районе 2, ADVICE мягко предложит менять режим: от сна до расходов.
          </p>
          <p class="u-body-main">
            Так формируется привычка смотреть на себя не только через задачи и дедлайны, но и через
            качество жизни.
          </p>
        </div>
      </div>
    </section>

    <div class="u-divider"></div>

    <!-- СЕКЦИЯ: КЕЙС ДО/ПОСЛЕ -->
    <section class="u-section">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">Кейс</div>
        <h2 class="u-h2">«С 1,8 до 3,9 за месяц» — пример живого пользователя</h2>
        <p class="u-body-main" style="max-width: 520px; margin-top: 8px;">
          Ниже — пример, как менялся индекс дня и ощущения человека за 30 дней
          работы с ботом. Без имён и личных деталей, только сухие цифры и факты.
        </p>
      </div>

      <div class="case-grid u-reveal js-reveal">
        <div class="case-card">
          <div class="case-pill case-pill--before">
            <span>До старта</span>
          </div>
          <p class="u-body-main">
            Частые провалы по сну, тревожность вечером, деньги — «живу от аванса до аванса».
            Иллюзия, что «всё нормально», пока не посмотрели на индекс дня.
          </p>
          <div class="case-metric-row">
            <div class="case-metric">
              <div class="case-metric-label">Средний индекс дня</div>
              <div class="case-metric-value">1,8</div>
              <div class="u-body-small">за последние 2 недели до старта</div>
            </div>
            <div class="case-metric">
              <div class="case-metric-label">Сон</div>
              <div class="case-metric-value">1,9</div>
              <div class="u-body-small">хаотичный режим, много дофамина ночью</div>
            </div>
          </div>
        </div>

        <div class="case-card">
          <div class="case-pill case-pill--after">
            <span>Через месяц</span>
          </div>
          <p class="u-body-main">
            Выровняли режим сна, поставили мягкий бюджет по категориям,
            подключили живого психолога на несколько сессий — всё внутри одного Telegram-чата.
          </p>
          <div class="case-metric-row">
            <div class="case-metric">
              <div class="case-metric-label">Средний индекс дня</div>
              <div class="case-metric-value">3,9</div>
              <div class="u-body-small">меньше «аварийных дней», больше устойчивости</div>
            </div>
            <div class="case-metric">
              <div class="case-metric-label">Фокус</div>
              <div class="case-metric-value">+2×</div>
              <div class="u-body-small">по самооценке пользователя в диалоге</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <div class="u-divider"></div>

    <!-- СЕКЦИЯ: МОДУЛИ -->
    <section class="u-section">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">Модули</div>
        <h2 class="u-h2">Психика, сон и деньги — в одном боте, а не в трёх разных приложениях</h2>
      </div>

      <div class="modules-card u-reveal js-reveal" id="modules">
        <div class="modules-tabs">
          <button class="modules-tab is-active" data-module="mind" type="button">
            <span class="modules-tab-label">Психолог</span>
            <span class="modules-tab-icon">💬</span>
          </button>
          <button class="modules-tab" data-module="sleep" type="button">
            <span class="modules-tab-label">Сон</span>
            <span class="modules-tab-icon">🌙</span>
          </button>
          <button class="modules-tab" data-module="money" type="button">
            <span class="modules-tab-label">Финансы</span>
            <span class="modules-tab-icon">💸</span>
          </button>
        </div>

        <div class="modules-content">
          <div class="modules-content-panel is-active" data-module-panel="mind">
            <p class="u-body-main">
              Личный чат, где можно проговорить ситуации, состояния и отношения
              так, как оно есть. ADVICE отвечает сразу, а команда специалистов подключается,
              когда это действительно нужно.
            </p>
            <ul class="modules-bullets">
              <li>переписка в формате «как другу», а не как в анкете;</li>
              <li>бережные уточняющие вопросы вместо давления и оценок;</li>
              <li>если становится тяжело — переход к живому психологу.</li>
            </ul>
          </div>
          <div class="modules-content-panel" data-module-panel="sleep">
            <p class="u-body-main">
              Модуль сна помогает выстроить режим под твою жизнь, а не под абстрактные рекомендации.
              Бот смотрит на твой график, шум, привычки и собирает рабочий план.
            </p>
            <ul class="modules-bullets">
              <li>режим отхода ко сну и подъёма, который реалистично выдерживать;</li>
              <li>ритуалы перед сном, снижение дофамина и «шума» перед сном;</li>
              <li>подбор звукового окружения (тишина, шум, природа) под твой запрос.</li>
            </ul>
          </div>
          <div class="modules-content-panel" data-module-panel="money">
            <p class="u-body-main">
              Финансовый модуль не заставляет «резко экономить», а аккуратно собирает картину доходов
              и расходов и показывает, как начать откладывать и перестать жить в режиме «дожить до зарплаты».
            </p>
            <ul class="modules-bullets">
              <li>разбор дохода и ключевых статей расходов без стыда и морализаторства;</li>
              <li>план, как выйти на минимальную подушку безопасности;</li>
              <li>подсказки, где можно срезать 10–15% без ощущения тотальной экономии.</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <div class="u-divider"></div>

    <!-- FAQ -->
    <section class="u-section">
      <div class="u-section-header u-reveal js-reveal">
        <div class="u-eyebrow">FAQ</div>
        <h2 class="u-h2">Частые вопросы перед тем, как нажать «Открыть в Telegram»</h2>
      </div>

      <ul class="faq-grid u-reveal js-reveal">
        <li class="faq-item">
          <button class="faq-question" type="button">
            <span>Это терапия или просто бот?</span>
            <span class="faq-icon">+</span>
          </button>
          <div class="faq-answer">
            <div class="faq-answer-inner">
              ADVICE — не медицинская услуга и не замена терапии. Это бот-ассистент, который помогает
              отслеживать состояние и не терять опору в повседневности. Когда видим, что нужна более глубокая работа,
              можем аккуратно предложить перейти к живому психологу.
            </div>
          </div>
        </li>
        <li class="faq-item">
          <button class="faq-question" type="button">
            <span>Кто читает мои сообщения?</span>
            <span class="faq-icon">+</span>
          </button>
          <div class="faq-answer">
            <div class="faq-answer-inner">
              По умолчанию с тобой общается бот. Сообщения может видеть узкая команда специалистов
              ADVICE, чтобы следить за качеством и безопасностью общения. Мы не передаём переписку
              третьим лицам и аккуратно относимся к твоей приватности.
            </div>
          </div>
        </li>
        <li class="faq-item">
          <button class="faq-question" type="button">
            <span>Подписка — навсегда? Что если я решу всё «починить» за месяц?</span>
            <span class="faq-icon">+</span>
          </button>
          <div class="faq-answer">
            <div class="faq-answer-inner">
              Подписку можно остановить в любой момент, но практика показывает: люди остаются не только
              ради «починить проблему», а ради ощущения опоры. Как у Яндекс Плюса — ты подписан не на одну
              функцию, а на систему, которая держит твой день в фокусе.
            </div>
          </div>
        </li>
        <li class="faq-item">
          <button class="faq-question" type="button">
            <span>Что с оплатой и тарифами?</span>
            <span class="faq-icon">+</span>
          </button>
          <div class="faq-answer">
            <div class="faq-answer-inner">
              Сейчас оплата подписки оформляется через администратора в Telegram. Внутри бота есть
              короткое объяснение тарифов: базовый и расширенный. Ты можешь начать в ознакомочном режиме,
              а потом решить, нужен ли тебе постоянный доступ.
            </div>
          </div>
        </li>
      </ul>
    </section>

    <div class="u-divider"></div>

    <!-- CTA -->
    <section class="u-section">
      <div class="cta-card u-reveal js-reveal">
        <h2>Готов попробовать ADVICE в своём Telegram?</h2>
        <p>
          Никаких анкет и регистрации на сайтах. Просто нажми на кнопку — бот откроется
          прямо в Telegram и предложит пройти первый короткий опрос.
        </p>
        <div class="cta-buttons">
          <a href="https://t.me/your_advice_bot" class="c-button">
            <span>Открыть бота в Telegram</span>
            <span class="c-button-icon">↗</span>
          </a>
          <a href="https://t.me/your_advice_support" class="cta-secondary">
            <span class="cta-secondary-icon">👤</span>
            <span>Написать админу, если есть вопросы</span>
          </a>
        </div>
      </div>
    </section>
  </main>

  <script>
    // ---------------------------
    // THEME ENGINE (light/dark)
    // ---------------------------
    (function () {
      const root = document.documentElement;
      const toggle = document.getElementById('theme-toggle');
      const knob = toggle ? toggle.querySelector('.theme-toggle-knob') : null;

      function applyTheme(theme) {
        root.setAttribute('data-theme', theme);
        try {
          window.localStorage.setItem('advice_landing_theme', theme);
        } catch (e) {}
        if (knob) {
          knob.textContent = theme === 'dark' ? '🌙' : '☀️';
        }
      }

      function initTheme() {
        let saved = null;
        try {
          saved = window.localStorage.getItem('advice_landing_theme');
        } catch (e) {}

        if (saved === 'light' || saved === 'dark') {
          applyTheme(saved);
          return;
        }

        const prefersDark = window.matchMedia &&
          window.matchMedia('(prefers-color-scheme: dark)').matches;
        applyTheme(prefersDark ? 'dark' : 'light');
      }

      if (toggle) {
        toggle.addEventListener('click', () => {
          const current = root.getAttribute('data-theme') || 'light';
          const next = current === 'light' ? 'dark' : 'light';
          applyTheme(next);
        });
      }

      initTheme();
    })();

    // ---------------------------
    // SCROLL REVEAL
    // ---------------------------
    (function () {
      const revealEls = Array.from(document.querySelectorAll('.js-reveal'));

      if (!('IntersectionObserver' in window) || revealEls.length === 0) {
        revealEls.forEach(el => el.classList.add('is-visible'));
        return;
      }

      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('is-visible');
              observer.unobserve(entry.target);
            }
          });
        },
        {
          threshold: 0.18,
        }
      );

      revealEls.forEach((el) => observer.observe(el));
    })();

    // ---------------------------
    // HERO SCROLL BUTTON
    // ---------------------------
    (function () {
      const btn = document.getElementById('scroll-to-story');
      const target = document.getElementById('story');
      if (!btn || !target) return;
      btn.addEventListener('click', () => {
        target.scrollIntoView({ behavior: 'smooth', block: 'start' });
      });
    })();

    // ---------------------------
    // PHONE SCENE: SWITCHER + AUTOPLAY
    // ---------------------------
    (function () {
      const chips = Array.from(document.querySelectorAll('.phone-screen-chip'));
      const slides = Array.from(document.querySelectorAll('.phone-screen-slide'));
      if (!chips.length || !slides.length) return;

      const order = ['welcome', 'index', 'modules'];
      let currentIndex = 0;
      let lastUserInteraction = Date.now();
      const AUTO_DELAY = 6500;

      function activate(screenId) {
        chips.forEach(ch => {
          ch.classList.toggle('is-active', ch.dataset.screen === screenId);
        });
        slides.forEach(slide => {
          slide.classList.toggle('is-active', slide.dataset.screenId === screenId);
        });
      }

      function goToIndex(idx) {
        currentIndex = (idx + order.length) % order.length;
        activate(order[currentIndex]);
      }

      chips.forEach((ch, idx) => {
        ch.addEventListener('click', () => {
          const screenId = ch.dataset.screen;
          if (!screenId) return;
          lastUserInteraction = Date.now();
          currentIndex = order.indexOf(screenId);
          if (currentIndex < 0) currentIndex = idx;
          activate(screenId);
        });
      });

      // автопрокрутка между экранами
      setInterval(() => {
        const now = Date.now();
        if (now - lastUserInteraction < AUTO_DELAY) return;
        goToIndex(currentIndex + 1);
      }, 2000);
    })();

    // ---------------------------
    // PHONE PARALLAX
    // ---------------------------
    (function () {
      const wrapper = document.querySelector('.phone-parallax');
      const heroSection = document.getElementById('hero');
      if (!wrapper || !heroSection) return;

      const MAX_OFFSET = 22; // px

      function handleScroll() {
        const rect = heroSection.getBoundingClientRect();
        const vh = window.innerHeight || document.documentElement.clientHeight;
        if (rect.bottom < 0 || rect.top > vh) {
          wrapper.style.transform = 'translateY(0px)';
          return;
        }
        const center = rect.top + rect.height / 2;
        const norm = (center - vh / 2) / vh; // -1..1
        const offset = -norm * MAX_OFFSET;
        wrapper.style.transform = `translateY(${offset.toFixed(1)}px)`;
      }

      window.addEventListener('scroll', handleScroll, { passive: true });
      handleScroll();
    })();

    // ---------------------------
    // MODULES TABS
    // ---------------------------
    (function () {
      const tabs = Array.from(document.querySelectorAll('.modules-tab'));
      const panels = Array.from(document.querySelectorAll('.modules-content-panel'));
      if (!tabs.length || !panels.length) return;

      function activate(moduleId) {
        tabs.forEach(tab => {
          tab.classList.toggle('is-active', tab.dataset.module === moduleId);
        });
        panels.forEach(panel => {
          panel.classList.toggle('is-active', panel.dataset.modulePanel === moduleId);
        });
      }

      tabs.forEach(tab => {
        tab.addEventListener('click', () => {
          const moduleId = tab.dataset.module;
          if (!moduleId) return;
          activate(moduleId);
        });
      });
    })();

    // ---------------------------
    // FAQ ACCORDION
    // ---------------------------
    (function () {
      const items = Array.from(document.querySelectorAll('.faq-item'));
      if (!items.length) return;

      items.forEach(item => {
        const btn = item.querySelector('.faq-question');
        if (!btn) return;
        btn.addEventListener('click', () => {
          const isOpen = item.classList.contains('is-open');
          items.forEach(i => i.classList.remove('is-open'));
          if (!isOpen) {
            item.classList.add('is-open');
          }
        });
      });
    })();

    // ---------------------------
    // INDEX DAY COUNTER ANIMATION
    // ---------------------------
    (function () {
      const valueEl = document.querySelector('.index-main-value[data-target]');
      if (!valueEl || !('IntersectionObserver' in window)) return;

      const targetNumber = parseFloat(valueEl.dataset.target);
      if (!targetNumber || Number.isNaN(targetNumber)) return;

      let started = false;

      function format(num) {
        return num.toFixed(1).replace('.', ',');
      }

      function animate() {
        const duration = 1100;
        let startTs = null;

        function step(ts) {
          if (!startTs) startTs = ts;
          const progress = Math.min((ts - startTs) / duration, 1);
          const current = targetNumber * progress;
          valueEl.textContent = format(current);
          if (progress < 1) {
            requestAnimationFrame(step);
          }
        }

        requestAnimationFrame(step);
      }

      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach(entry => {
            if (entry.isIntersecting && !started) {
              started = true;
              animate();
              observer.disconnect();
            }
          });
        },
        { threshold: 0.3 }
      );

      observer.observe(valueEl);
    })();
  </script>
</body>
</html>
