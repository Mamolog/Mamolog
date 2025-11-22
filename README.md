<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <title>ADVICE · Telegram Mini App</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="color-scheme" content="light dark" />
  <meta name="theme-color" content="#000000" />
  <style>
    :root {
      --color-bg-app: #f5f5f5;
      --color-bg-app-alt: #ededed;
      --color-surface: #ffffff;
      --color-surface-soft: #f7f7f7;
      --color-text-main: #050505;
      --color-text-soft: #7a7a7a;
      --color-text-muted: #9b9b9b;
      --color-border-subtle: #e1e1e1;
      --color-border-strong: #c8c8c8;
      --color-focus-ring: #000000;
      --radius-m: 14px;
      --radius-card: 18px;
      --radius-pill: 999px;
      --space-xs: 4px;
      --space-s: 8px;
      --space-m: 12px;
      --space-l: 16px;
      --space-xl: 24px;
      --space-2xl: 32px;
      --font-sans: system-ui, -apple-system, BlinkMacSystemFont, "SF Pro Text", "Inter", "Roboto", sans-serif;
      --font-size-xs: 11px;
      --font-size-s: 12px;
      --font-size-m: 13px;
      --font-size-l: 14px;
      --font-size-xl: 16px;
      --shadow-soft: 0 10px 30px rgba(0, 0, 0, 0.08);
      --shadow-card: 0 18px 46px rgba(0, 0, 0, 0.11);
      --motion-fast: 140ms;
      --motion-medium: 240ms;
      --motion-slow: 380ms;
      --easing-standard: cubic-bezier(0.2, 0.0, 0.2, 1);
      --easing-decelerate: cubic-bezier(0.0, 0.0, 0.0, 1);
      --easing-accelerate: cubic-bezier(0.4, 0.0, 1, 1);
      --z-intro: 60;
      --z-header: 20;
      --z-bottom-nav: 30;
    }
    body.theme-dark {
      --color-bg-app: #0f1114;
      --color-bg-app-alt: #15181d;
      --color-surface: #161a20;
      --color-surface-soft: #1c2027;
      --color-text-main: #f4f6fb;
      --color-text-soft: #c5cada;
      --color-text-muted: #9aa2b5;
      --color-border-subtle: #252b35;
      --color-border-strong: #343c49;
      --color-focus-ring: #5be37d;
      background: radial-gradient(circle at top, #0f1114 0, #12151a 55%, #0d0f13 100%);
      color: var(--color-text-main);
    }
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
    @keyframes scaleInOvershoot {
      0% {
        transform: scale(0.92);
        opacity: 0;
      }
      70% {
        transform: scale(1.03);
        opacity: 1;
      }
      100% {
        transform: scale(1);
      }
    }
    @keyframes introLogoLeave {
      0% {
        transform: translateY(0) scale(1);
        opacity: 1;
        letter-spacing: 0.28em;
        filter: blur(0);
      }
      60% {
        transform: translateY(-12px) scale(1.03);
        opacity: 0.7;
        letter-spacing: 0.38em;
      }
      100% {
        transform: translateY(22px) scale(0.94);
        opacity: 0;
        letter-spacing: 0.08em;
        filter: blur(4px);
      }
    }
    @keyframes introHelloIn {
      0% {
        opacity: 0;
        transform: translateY(18px) scale(0.96);
        letter-spacing: 0.18em;
      }
      60% {
        opacity: 1;
        transform: translateY(-2px) scale(1.02);
        letter-spacing: 0.10em;
      }
      100% {
        opacity: 1;
        transform: translateY(0) scale(1);
        letter-spacing: 0.06em;
      }
    }
    @keyframes chatBubbleIn {
      from {
        opacity: 0;
        transform: translateY(10px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    @keyframes locatorSweep {
      0% {
        transform: translateX(-120%);
      }
      100% {
        transform: translateX(120%);
      }
    }
    @keyframes locatorPulse {
      0% {
        transform: scale(0.4);
        opacity: 0.35;
      }
      60% {
        opacity: 0.15;
      }
      100% {
        transform: scale(1.6);
        opacity: 0;
      }
    }
    @keyframes corePulse {
      0% {
        transform: translate(-50%, -50%) scale(0.3);
        opacity: 0.0;
      }
      25% {
        transform: translate(-50%, -50%) scale(1.05);
        opacity: 1;
      }
      55% {
        transform: translate(-50%, -50%) scale(0.9);
        opacity: 0.95;
      }
      100% {
        transform: translate(-50%, -50%) scale(1.12);
        opacity: 0;
      }
    }
    @keyframes rippleWaveAdvanced {
      0% {
        transform: translate(-50%, -50%) scale(0.4);
        opacity: 0.9;
        border-width: 2px;
      }
      40% {
        opacity: 0.6;
      }
      80% {
        transform: translate(-50%, -50%) scale(3.0);
        opacity: 0.25;
        border-width: 1px;
      }
      100% {
        transform: translate(-50%, -50%) scale(3.6);
        opacity: 0;
        border-width: 1px;
      }
    }
    @keyframes typingBlink {
      0%,
      60%,
      100% {
        opacity: 0.3;
        transform: translateY(0);
      }
      30% {
        opacity: 1;
        transform: translateY(-1px);
      }
    }
    * {
      box-sizing: border-box;
    }
    html,
    body {
      margin: 0;
      padding: 0;
      height: 100%;
    }
    body {
      font-family: var(--font-sans);
      background: radial-gradient(circle at top, #ffffff 0, #f5f5f5 55%, #ebebeb 100%);
      color: var(--color-text-main);
      -webkit-font-smoothing: antialiased;
      text-rendering: optimizeLegibility;
    }
    button {
      font-family: inherit;
      cursor: pointer;
    }
    input,
    select {
      font-family: inherit;
    }
    :focus-visible {
      outline: 2px solid var(--color-focus-ring);
      outline-offset: 2px;
    }
    .app-shell {
      min-height: 100vh;
      max-width: 540px;
      margin: 0 auto;
      padding: var(--space-m);
      padding-bottom: 80px;
      display: flex;
      flex-direction: column;
      opacity: 1;
      transition: opacity var(--motion-medium) var(--easing-standard);
    }
    .app-shell--hidden {
      opacity: 0;
      pointer-events: none;
    }
    main#app-main {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: var(--space-l);
      animation: fadeInSoft var(--motion-medium) var(--easing-standard);
    }
    /* ---------- INTRO ---------- */
    .intro-root {
      position: fixed;
      inset: 0;
      background: radial-gradient(circle at 30% 20%, rgba(255, 255, 255, 0.18), transparent 42%),
        radial-gradient(circle at 70% 70%, rgba(91, 227, 125, 0.14), transparent 48%),
        rgba(8, 10, 14, 0.6);
      color: var(--color-text-main);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: var(--z-intro);
      backdrop-filter: blur(30px) saturate(1.35);
      transition: opacity var(--motion-medium) var(--easing-standard), transform var(--motion-medium) var(--easing-standard), background var(--motion-medium) var(--easing-standard), backdrop-filter var(--motion-medium) var(--easing-standard);
    }
    .intro-root.intro-overlay {
      pointer-events: none;
      background: radial-gradient(circle at 20% 30%, rgba(255, 255, 255, 0.15), transparent 36%),
        radial-gradient(circle at 80% 70%, rgba(91, 227, 125, 0.18), transparent 46%),
        rgba(8, 10, 14, 0.22);
      backdrop-filter: blur(34px) saturate(1.4);
    }
    .intro-root.intro-overlay .intro-screen {
      pointer-events: none;
      background: rgba(255, 255, 255, 0.82);
      border: 1px solid rgba(0, 0, 0, 0.06);
      box-shadow: 0 26px 70px rgba(0, 0, 0, 0.22);
      color: var(--color-text-main);
    }
    body.theme-dark .intro-root.intro-overlay .intro-screen {
      background: rgba(20, 24, 30, 0.9);
      border-color: var(--color-border-strong);
      box-shadow: 0 28px 70px rgba(0, 0, 0, 0.48);
    }
    body.theme-dark .intro-root {
      background: radial-gradient(circle at 30% 20%, rgba(91, 227, 125, 0.16), transparent 40%),
        radial-gradient(circle at 70% 70%, rgba(62, 111, 255, 0.2), transparent 52%),
        rgba(8, 10, 14, 0.74);
      color: var(--color-text-main);
      backdrop-filter: blur(32px) saturate(1.35);
    }
    .intro-root.intro-water {
      background: rgba(255, 255, 255, 0.78);
      backdrop-filter: blur(28px) saturate(1.35);
    }
    body.theme-dark .intro-root.intro-water {
      background: rgba(8, 10, 14, 0.82);
      backdrop-filter: blur(32px) saturate(1.45);
    }
    .intro-root.intro-hidden {
      opacity: 0;
      pointer-events: none;
      transform: translateY(6px);
    }
    .intro-screen {
      max-width: 460px;
      width: 100%;
      padding: var(--space-2xl) var(--space-l);
      text-align: center;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      animation: fadeInSoft var(--motion-medium) var(--easing-decelerate);
      position: relative;
      color: var(--color-text-main);
    }
    .intro-title-main {
      font-size: 32px;
      font-weight: 900;
      letter-spacing: 0.32em;
      text-transform: uppercase;
      padding: 10px 0;
      display: inline-block;
      color: var(--color-text-main);
    }
    .intro-title-main.intro-logo-leave {
      animation: introLogoLeave 0.45s var(--easing-accelerate) forwards;
    }
    .intro-hello {
      font-size: 28px;
      font-weight: 800;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      animation: introHelloIn 0.5s var(--easing-decelerate);
      color: var(--color-text-main);
    }
    .intro-question-label {
      font-size: 17px;
      font-weight: 600;
      margin-bottom: var(--space-l);
    }
    .intro-stars-row {
      display: inline-flex;
      justify-content: center;
      gap: 10px;
      position: relative;
    }
    .intro-stars-row::after {
      content: "";
      position: absolute;
      left: -6px;
      right: -6px;
      bottom: -8px;
      height: 1px;
      background: var(--color-text-main);
      opacity: 0.14;
    }
    .intro-star {
      background: transparent;
      border: none;
      padding: 0;
      font-size: 30px;
      line-height: 1;
      color: var(--color-text-main);
      opacity: 0.25;
      transform-origin: center bottom;
      transition: opacity var(--motion-fast) var(--easing-standard), transform var(--motion-fast) var(--easing-standard), text-shadow var(--motion-fast) var(--easing-standard);
    }
    .intro-star:hover {
      opacity: 0.45;
      transform: translateY(-1px) scale(1.05);
    }
    .intro-star--active {
      opacity: 1;
      transform: translateY(-2px) scale(1.18);
      text-shadow: 0 0 0 var(--color-text-main), 0 6px 16px rgba(0, 0, 0, 0.45);
    }
    body.theme-dark .intro-star--active {
      text-shadow: 0 0 0 var(--color-text-main), 0 6px 16px rgba(91, 227, 125, 0.35);
    }
    .attention-panel-slot {
      width: 100%;
      margin-top: var(--space-xl);
      opacity: 0;
      transform: translateY(8px);
      transition: opacity var(--motion-medium) var(--easing-standard), transform var(--motion-medium) var(--easing-standard);
    }
    .attention-panel-slot--visible {
      opacity: 1;
      transform: translateY(0);
    }
    .attention-panel {
      border: 1px solid var(--color-border-strong);
      border-radius: var(--radius-card);
      padding: var(--space-l);
      background: var(--color-surface);
      text-align: left;
      box-shadow: var(--shadow-soft);
    }
    .attention-panel-title {
      font-size: var(--font-size-l);
      font-weight: 600;
      margin-bottom: var(--space-s);
    }
    .attention-panel-sub {
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
      margin-bottom: var(--space-m);
      line-height: 1.4;
    }
    .attention-options {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: var(--space-m);
    }
    .attention-option {
      border-radius: var(--radius-pill);
      border: 1px dashed var(--color-border-strong);
      padding: 6px 12px;
      font-size: var(--font-size-s);
      background: var(--color-surface-soft);
      color: var(--color-text-main);
      transition: background var(--motion-fast) var(--easing-standard), border-color var(--motion-fast) var(--easing-standard), transform var(--motion-fast) var(--easing-standard);
    }
    .attention-option--selected {
      background: var(--color-text-main);
      color: var(--color-bg-app);
      border-color: var(--color-text-main);
      transform: translateY(-1px);
    }
    .intro-dialog {
      width: 100%;
      max-width: 420px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .intro-dialog-bubble {
      max-width: 90%;
      padding: 12px 16px;
      border-radius: 20px;
      font-size: var(--font-size-m);
      line-height: 1.5;
      opacity: 0;
      transform: translateY(10px);
      transition: opacity var(--motion-medium) var(--easing-standard), transform var(--motion-medium) var(--easing-standard);
      box-shadow: 0 10px 26px rgba(0, 0, 0, 0.08);
      position: relative;
      overflow: hidden;
    }
    .intro-dialog-bubble--bot {
      align-self: flex-start;
      background: var(--color-surface);
      border: 1px solid var(--color-border-subtle);
      color: var(--color-text-main);
    }
    .intro-dialog-bubble--user {
      align-self: flex-end;
      background: var(--color-bg-app-alt);
      color: var(--color-text-main);
      border: 1px solid var(--color-border-strong);
    }
    .intro-dialog-bubble--visible {
      opacity: 1;
      transform: translateY(0);
    }
    .intro-dialog-meta {
      font-size: var(--font-size-xs);
      text-transform: uppercase;
      letter-spacing: 0.12em;
      color: var(--color-text-soft);
      margin-bottom: 4px;
    }
    .intro-dialog-bubble::after {
      content: "";
      position: absolute;
      inset: 0;
      border-radius: 20px;
      pointer-events: none;
      background: linear-gradient(135deg, rgba(255, 255, 255, 0.4), rgba(255, 255, 255, 0));
      opacity: 0.45;
      mix-blend-mode: screen;
    }
    .intro-actions {
      margin-top: 18px;
      display: flex;
      justify-content: center;
    }
    .intro-actions button[disabled] {
      opacity: 0.35;
      pointer-events: none;
    }
    .menu-hero {
      border-radius: var(--radius-card);
      padding: var(--space-l);
      background: linear-gradient(135deg, #0ea5e9, #7c3aed);
      color: #f8fafc;
      box-shadow: var(--shadow-card);
      margin-bottom: var(--space-m);
    }
    .menu-hero-title {
      font-size: 22px;
      font-weight: 900;
      margin: 0 0 6px;
    }
    .menu-hero-sub {
      font-size: var(--font-size-m);
      opacity: 0.92;
      margin-bottom: 8px;
    }
    .menu-hero-row {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      align-items: center;
    }
    /* ---------- HEADER ---------- */
    .c-header {
      margin-bottom: var(--space-l);
      padding: 10px 14px;
      border-radius: var(--radius-pill);
      background: var(--color-surface);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--shadow-soft);
      display: flex;
      align-items: center;
      justify-content: space-between;
      animation: fadeInSoft var(--motion-medium) var(--easing-standard);
      z-index: var(--z-header);
    }
    .c-header-left {
      display: flex;
      align-items: center;
      gap: var(--space-m);
    }
    .avatar {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      background: #000;
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: var(--font-size-s);
      font-weight: 600;
    }
    .c-header-title-main {
      font-size: 14px;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
    }
    .c-header-title-sub {
      font-size: 11px;
      color: var(--color-text-soft);
      white-space: nowrap;
      max-width: 200px;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    .c-header-pill {
      font-size: 11px;
      padding: 4px 10px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-strong);
      background: var(--color-surface-soft);
      display: inline-flex;
      align-items: center;
      gap: 6px;
      white-space: nowrap;
    }
    .c-header-pill-dot {
      width: 7px;
      height: 7px;
      border-radius: 50%;
      border: 1px solid #000;
    }
    .c-card {
      border-radius: var(--radius-card);
      background: var(--color-surface);
      border: 1px solid var(--color-border-subtle);
      padding: 14px 16px;
      box-shadow: var(--shadow-card);
      animation: scaleInOvershoot var(--motion-medium) var(--easing-standard);
    }
    .c-card--flat {
      box-shadow: none;
      border-radius: var(--radius-m);
    }
    .c-card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: var(--space-s);
    }
    .c-card-title {
      font-size: var(--font-size-l);
      font-weight: 600;
    }
    .c-card-sub {
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
    }
    .c-badge {
      font-size: var(--font-size-xs);
      padding: 3px 8px;
      border-radius: var(--radius-pill);
      background: var(--color-surface-soft);
      border: 1px solid var(--color-border-subtle);
      color: var(--color-text-soft);
    }
    .section-title {
      font-size: var(--font-size-m);
      font-weight: 600;
      margin-bottom: var(--space-xs);
    }
    .section-sub {
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
      margin-bottom: var(--space-s);
      line-height: 1.5;
    }
    .c-button {
      border-radius: var(--radius-pill);
      padding: 10px 14px;
      font-size: var(--font-size-m);
      font-weight: 600;
      border: 1px solid #000;
      background: #000;
      color: #fff;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      white-space: nowrap;
      transition: transform var(--motion-fast) var(--easing-standard), box-shadow var(--motion-fast) var(--easing-standard);
    }
    .c-button--secondary {
      background: #fff;
      color: #000;
    }
    .c-button:active {
      transform: translateY(1px) scale(0.98);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }
    .c-field {
      width: 100%;
      border-radius: 12px;
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface);
      padding: 10px 12px;
      font-size: var(--font-size-m);
      color: var(--color-text-main);
    }
    .c-field::placeholder {
      color: var(--color-text-muted);
    }
    [data-role="sleep-wake-time"] {
      max-width: 240px;
      width: 100%;
    }
    .chips-row {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: var(--space-xs);
    }
    .chip {
      font-size: var(--font-size-xs);
      padding: 4px 9px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface-soft);
      color: var(--color-text-muted);
    }
    .chip--locator {
      position: relative;
      overflow: hidden;
      border-color: rgba(0, 255, 153, 0.45);
      background: rgba(0, 255, 153, 0.12);
      color: #066a3c;
      box-shadow: inset 0 0 0 1px rgba(0, 255, 153, 0.2);
      font-weight: 600;
      z-index: 0;
    }
    .chip--locator::before,
    .chip--locator::after {
      content: "";
      position: absolute;
      pointer-events: none;
    }
    .chip--locator::before {
      inset: -40%;
      border-radius: 50%;
      border: 1px solid rgba(0, 255, 153, 0.35);
      animation: locatorPulse 2.8s infinite ease-out;
      z-index: -1;
    }
    .chip--locator::after {
      inset: 0;
      background: linear-gradient(120deg, transparent 0%, rgba(0, 255, 153, 0.0) 40%, rgba(0, 255, 153, 0.6) 50%, rgba(0, 255, 153, 0.0) 60%, transparent 100%);
      animation: locatorSweep 2.2s linear infinite;
      opacity: 0.65;
      z-index: -1;
    }
    /* attention card */
    .attention-card {
      margin-top: var(--space-m);
    }
    .attention-chat {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-top: var(--space-s);
    }
    .attention-chat--intro .attention-bubble {
      opacity: 0;
      transform: translateY(8px);
      animation: chatBubbleIn var(--motion-medium) var(--easing-standard) forwards;
      animation-delay: calc(var(--bubble-index, 0) * 140ms);
    }
    .attention-bubble {
      border-radius: 18px;
      padding: 12px 16px;
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface);
      box-shadow: 0 18px 38px rgba(0, 0, 0, 0.08);
    }
    .attention-bubble--note {
      align-self: center;
      border-style: dashed;
      box-shadow: none;
      background: var(--color-surface-soft);
      color: var(--color-text-soft);
      font-size: var(--font-size-s);
    }
    .attention-bubble-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      font-size: var(--font-size-s);
      margin-bottom: 6px;
    }
    .attention-item-title {
      font-weight: 600;
      font-size: var(--font-size-m);
    }
    .attention-bubble-score {
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
    }
    .attention-chips {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }
    .attention-chip {
      border-radius: var(--radius-pill);
      background: var(--color-surface-soft);
      border: 1px dashed var(--color-border-strong);
      padding: 5px 10px;
      font-size: var(--font-size-xs);
      color: var(--color-text-main);
    }
    /* bottom nav */
    .c-bottom-nav {
      position: fixed;
      left: 50%;
      bottom: 10px;
      transform: translateX(-50%);
      width: 100%;
      max-width: 540px;
      padding: 6px 10px;
      z-index: var(--z-bottom-nav);
      opacity: 1;
      transition: opacity var(--motion-medium) var(--easing-standard);
    }
    .c-bottom-nav.app-shell--hidden {
      opacity: 0;
      pointer-events: none;
    }
    .c-bottom-nav-inner {
      background: var(--color-surface);
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--shadow-soft);
      display: flex;
      align-items: center;
      justify-content: space-around;
      padding: 4px;
    }
    .bottom-nav-item {
      flex: 1;
      border-radius: var(--radius-pill);
      padding: 6px 4px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 2px;
      font-size: var(--font-size-xs);
      color: var(--color-text-muted);
    }
    .bottom-nav-item--active {
      background: var(--color-surface-soft);
      color: var(--color-text-main);
    }
    .bottom-nav-dot {
      width: 18px;
      height: 18px;
      border-radius: 50%;
      border: 1px solid var(--color-border-subtle);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 11px;
    }
    .bottom-nav-dot--accent {
      border-color: #000;
      background: #000;
      color: #fff;
    }
    /* chat */
    .chat-window {
      display: flex;
      flex-direction: column;
      gap: 8px;
      max-height: 420px;
      min-height: 220px;
      overflow-y: auto;
      padding-right: 4px;
      margin-bottom: var(--space-s);
      padding: 14px;
      border-radius: 18px;
      border: 1px solid rgba(126, 133, 155, 0.35);
      background: linear-gradient(145deg, rgba(96, 165, 250, 0.12), rgba(59, 130, 246, 0.06)),
        radial-gradient(circle at 22% 18%, rgba(125, 211, 252, 0.18), transparent 38%),
        var(--color-surface);
      box-shadow: 0 24px 50px rgba(0, 0, 0, 0.18);
    }
    .chat-message {
      max-width: 80%;
      padding: 12px 14px;
      border-radius: 16px;
      font-size: var(--font-size-s);
      line-height: 1.4;
      word-break: break-word;
      overflow-wrap: anywhere;
      box-shadow: 0 18px 32px rgba(0, 0, 0, 0.18);
    }
    .chat-message--user {
      align-self: flex-end;
      border-bottom-right-radius: 6px;
      background: linear-gradient(120deg, #2563eb, #7c3aed);
      color: #f8fafc;
      border: 1px solid rgba(124, 58, 237, 0.35);
    }
    .chat-message--bot {
      align-self: flex-start;
      border-bottom-left-radius: 6px;
      background: linear-gradient(135deg, rgba(255, 255, 255, 0.92), rgba(226, 232, 240, 0.92));
      border: 1px solid var(--color-border-subtle);
    }
    .chat-meta {
      font-size: var(--font-size-xs);
      color: var(--color-text-muted);
      margin-bottom: 2px;
    }
    .typing-indicator {
      display: inline-flex;
      gap: 3px;
    }
    .typing-dot {
      width: 4px;
      height: 4px;
      border-radius: 999px;
      background: #7a7a7a;
      animation: typingBlink 1s infinite;
    }
    .typing-dot:nth-child(2) {
      animation-delay: 0.15s;
    }
    .typing-dot:nth-child(3) {
      animation-delay: 0.3s;
    }
    .chat-hero {
      display: grid;
      gap: 10px;
      grid-template-columns: 1fr;
      padding: var(--space-m);
      margin-bottom: var(--space-m);
      border-radius: var(--radius-card);
      background: linear-gradient(120deg, #4338ca, #8b5cf6);
      color: #fff;
      box-shadow: var(--shadow-card);
    }
    @media (min-width: 520px) {
      .chat-hero {
        grid-template-columns: 1.2fr 1fr;
      }
    }
    .chat-hero-title {
      font-size: 22px;
      font-weight: 900;
      margin: 0 0 6px;
    }
    .chat-hero-sub {
      opacity: 0.9;
      font-size: var(--font-size-m);
      line-height: 1.5;
    }
    .chat-hero-side {
      display: flex;
      flex-direction: column;
      gap: 8px;
      align-items: flex-start;
    }
    .chat-pill {
      padding: 8px 12px;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(255, 255, 255, 0.3);
      background: rgba(255, 255, 255, 0.12);
      color: #fff;
      font-weight: 700;
      font-size: var(--font-size-s);
      backdrop-filter: blur(4px);
    }
    .chat-quick-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 8px;
      margin-bottom: var(--space-m);
    }
    @media (min-width: 520px) {
      .chat-quick-grid {
        grid-template-columns: repeat(3, minmax(0, 1fr));
      }
    }
    .chat-quick-card {
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-m);
      padding: 10px;
      background: var(--color-surface-soft);
      font-size: var(--font-size-s);
      display: flex;
      flex-direction: column;
      gap: 6px;
      box-shadow: var(--shadow-soft);
    }
    .chat-quick-title {
      font-weight: 700;
      font-size: var(--font-size-m);
    }
    .row {
      display: flex;
      align-items: center;
      gap: var(--space-m);
      justify-content: space-between;
    }
    .row--stack-m {
      flex-direction: column;
      align-items: stretch;
    }
    @media (min-width: 420px) {
      .row--stack-m {
        flex-direction: row;
      }
    }
    .back-row {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 12px;
    }
    .back-button {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 8px 12px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-strong);
      background: var(--color-surface-soft);
      color: var(--color-text-main);
      font-weight: 600;
      font-size: var(--font-size-m);
      cursor: pointer;
      box-shadow: var(--shadow-soft);
    }
    .back-button span {
      font-size: 16px;
      line-height: 1;
    }
    /* QUALITY CARD / INDEX */
    .quality-card {
      position: relative;
      overflow: hidden;
      background: radial-gradient(circle at top right, rgba(0, 0, 0, 0.06), transparent 55%), var(--color-surface);
    }
    body.theme-dark .quality-card {
      background: radial-gradient(circle at top right, rgba(91, 227, 125, 0.16), transparent 55%), var(--color-surface);
    }
    .quality-card-top {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      gap: var(--space-l);
    }
    .quality-main-meta {
      flex: 1;
      min-width: 0;
    }
    .quality-score-block {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      gap: 4px;
    }
    .life-score-main {
      font-size: 30px;
      font-weight: 800;
      margin-bottom: 0;
    }
    .life-score-caption {
      font-size: var(--font-size-xs);
      color: var(--color-text-soft);
    }
    .life-score-pill {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      font-size: 11px;
      padding: 4px 9px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-strong);
      background: var(--color-surface-soft);
    }
    body.theme-dark .life-score-pill {
      border-color: #5be37d;
    }
    .quality-thermo {
      margin-top: var(--space-m);
    }
    .quality-thermo-track {
      width: 100%;
      height: 10px;
      border-radius: var(--radius-pill);
      background: var(--color-bg-app-alt);
      overflow: hidden;
      position: relative;
    }
    body.theme-dark .quality-thermo-track {
      background: #10141b;
    }
    .quality-thermo-fill {
      position: absolute;
      inset: 0;
      transform-origin: left center;
      transform: scaleX(var(--quality-score, 0));
      background: linear-gradient(90deg, #ef4444 0%, #f97316 35%, #facc15 65%, #22c55e 100%);
      transition: transform var(--motion-medium) var(--easing-standard);
    }
    .quality-thermo-labels {
      display: flex;
      justify-content: space-between;
      font-size: var(--font-size-xs);
      color: var(--color-text-muted);
      margin-top: 4px;
    }
    .quality-description {
      margin-top: var(--space-m) !important;
    }
    .quality-actions {
      margin-top: var(--space-m);
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }
    .quality-state-badge {
      margin-top: 8px;
      font-size: var(--font-size-xs);
      padding: 4px 8px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface-soft);
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }
    .quality-state-badge--good {
      border-color: #16a34a;
      background: rgba(22, 163, 74, 0.16);
      color: #065f46;
    }
    .quality-state-badge--ok {
      border-color: #f59e0b;
      background: rgba(245, 158, 11, 0.16);
      color: #92400e;
    }
    .quality-state-badge--bad {
      border-color: #ef4444;
      background: rgba(239, 68, 68, 0.18);
      color: #7f1d1d;
    }
    .quality-state-badge--neutral {
      opacity: 0.85;
    }
    /* history */
    .lifeline-card {
      margin-top: var(--space-l);
      padding-bottom: 24px;
    }
    .lifeline-header-row {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      gap: 4px;
      margin-bottom: var(--space-s);
    }
    .lifeline-label-main {
      font-size: var(--font-size-m);
      font-weight: 600;
    }
    .lifeline-label-sub {
      font-size: var(--font-size-xs);
      color: var(--color-text-muted);
    }
    .lifeline-percentile {
      font-size: var(--font-size-xs);
      padding: 3px 8px;
      border-radius: var(--radius-pill);
      border: 1px dashed var(--color-border-subtle);
      color: var(--color-text-soft);
      margin-top: 6px;
    }
    .lifeline-track {
      display: flex;
      align-items: flex-end;
      gap: 6px;
      margin-top: var(--space-s);
      padding-top: 2px;
    }
    .lifeline-day {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;
      min-width: 0;
    }
    .lifeline-bar {
      width: 100%;
      height: 40px;
      border-radius: var(--radius-pill);
      background: var(--color-surface-soft);
      border: 1px solid var(--color-border-subtle);
      position: relative;
      overflow: hidden;
    }
    .lifeline-bar-inner {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      border-radius: inherit;
      background: linear-gradient(180deg, var(--bar-color-start, #000) 0%, var(--bar-color-end, #111) 100%);
      transform-origin: bottom;
      transition: transform var(--motion-medium) var(--easing-standard), opacity var(--motion-medium) var(--easing-standard);
    }
    .lifeline-bar--placeholder {
      background: transparent;
      border-style: dashed;
    }
    .lifeline-bar--placeholder .lifeline-bar-inner {
      display: none;
    }
    .lifeline-day-score {
      font-size: 11px;
      color: var(--color-text-soft);
    }
    .lifeline-day-label {
      font-size: var(--font-size-xs);
      color: var(--color-text-muted);
      white-space: nowrap;
    }
    .lifeline-day-label--placeholder {
      opacity: 0.45;
    }
    .lifeline-actions {
      display: flex;
      gap: 8px;
      margin-top: var(--space-m);
      flex-wrap: wrap;
    }
    .history-panel {
      margin-top: 12px;
      border: 1px dashed var(--color-border-subtle);
      border-radius: var(--radius-m);
      padding: var(--space-m);
      background: var(--color-surface);
    }
    .history-panel h4 {
      margin: 0 0 8px;
      font-size: var(--font-size-m);
    }
    .history-content {
      display: grid;
      grid-template-columns: 1fr;
      gap: 12px;
    }
    @media (min-width: 480px) {
      .history-content {
        grid-template-columns: 1fr 1.2fr;
      }
    }
    .history-list {
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .history-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 12px;
      border-radius: var(--radius-m);
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface-soft);
      text-align: left;
      gap: 10px;
    }
    .history-row--active {
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.18);
    }
    .history-row-title {
      font-weight: 600;
      font-size: var(--font-size-m);
    }
    .history-row-sub {
      font-size: var(--font-size-xs);
      color: var(--color-text-muted);
    }
    .history-row-score {
      font-weight: 700;
      font-size: var(--font-size-l);
    }
    .history-detail {
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-m);
      padding: var(--space-m);
      background: var(--color-surface-soft);
      min-height: 180px;
    }
    .history-detail h5 {
      margin: 0 0 6px;
      font-size: var(--font-size-m);
    }
    .history-detail-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
      gap: 10px;
      margin-top: 10px;
    }
    .history-detail-block {
      padding: 10px;
      border-radius: var(--radius-m);
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface);
    }
    .history-detail-block-title {
      font-weight: 600;
      margin-bottom: 6px;
    }
    .history-detail-score {
      font-size: 18px;
      font-weight: 700;
      margin-bottom: 6px;
    }
    .history-reasons {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }
    .history-reason-chip {
      padding: 4px 8px;
      border-radius: var(--radius-pill);
      background: var(--color-surface);
      border: 1px solid var(--color-border-subtle);
      font-size: var(--font-size-xs);
      color: var(--color-text-soft);
    }
    .history-note {
      width: 100%;
      min-height: 70px;
      border-radius: 12px;
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface);
      padding: 10px 12px;
      font-size: var(--font-size-m);
      font-family: var(--font-sans);
      resize: vertical;
      color: var(--color-text-main);
    }
    .history-note::placeholder {
      color: var(--color-text-muted);
    }
    .history-note-row {
      margin-top: 10px;
      display: flex;
      gap: 8px;
      align-items: flex-start;
      flex-wrap: wrap;
    }
    .feature-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: var(--space-m);
    }
    .feature-card {
      border-radius: var(--radius-card);
      background: var(--color-surface);
      border: 1px solid var(--color-border-subtle);
      padding: 10px;
      display: flex;
      flex-direction: column;
      gap: 4px;
      font-size: var(--font-size-s);
      transition: transform var(--motion-fast) var(--easing-standard), box-shadow var(--motion-fast) var(--easing-standard), border-color var(--motion-fast) var(--easing-standard);
    }
    .feature-card:hover {
      transform: translateY(-2px);
      box-shadow: 0 12px 32px rgba(0, 0, 0, 0.16);
      border-color: #000;
    }
    .feature-card-title {
      font-weight: 600;
      font-size: var(--font-size-m);
    }
    .feature-card-pill {
      font-size: var(--font-size-xs);
      padding: 2px 6px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-subtle);
      color: var(--color-text-muted);
      width: fit-content;
    }
    .feature-card-footer {
      margin-top: 6px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: var(--font-size-xs);
      color: var(--color-text-soft);
    }
    /* menu cards */
    .menu-grid {
      display: grid;
      gap: var(--space-m);
      grid-template-columns: 1fr;
    }
    @media (min-width: 520px) {
      .menu-grid {
        grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      }
    }
    .menu-card {
      border-radius: var(--radius-card);
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface);
      padding: var(--space-l);
      box-shadow: var(--shadow-card);
      display: flex;
      flex-direction: column;
      gap: var(--space-s);
      position: relative;
      overflow: hidden;
    }
    .menu-card::after {
      content: "";
      position: absolute;
      inset: 0;
      pointer-events: none;
      background: radial-gradient(circle at 90% 20%, rgba(0, 0, 0, 0.06), transparent 55%);
      opacity: 0.7;
    }
    body.theme-dark .menu-card::after {
      background: radial-gradient(circle at 90% 20%, rgba(91, 227, 125, 0.15), transparent 55%);
    }
    .menu-card-title {
      font-size: 18px;
      font-weight: 700;
      letter-spacing: 0.06em;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      z-index: 1;
    }
    .menu-card-sub {
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
      z-index: 1;
      line-height: 1.5;
    }
    .menu-card-list {
      margin: 0;
      padding-left: 18px;
      color: var(--color-text-main);
      z-index: 1;
      display: grid;
      gap: 6px;
    }
    .menu-card-list li {
      font-size: var(--font-size-s);
      line-height: 1.5;
    }
    .menu-card-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      z-index: 1;
    }
    .menu-stat-chip {
      border-radius: var(--radius-pill);
      border: 1px dashed var(--color-border-strong);
      padding: 6px 10px;
      font-size: var(--font-size-xs);
      color: var(--color-text-soft);
      background: var(--color-surface-soft);
      z-index: 1;
    }
    /* sleep helpers */
    .sleep-checklist {
      border: 1px dashed var(--color-border-subtle);
      border-radius: var(--radius-m);
      padding: var(--space-m);
      background: var(--color-surface-soft);
      display: grid;
      gap: 10px;
      margin-top: 10px;
    }
    .sleep-checklist label {
      display: flex;
      align-items: flex-start;
      gap: 8px;
      font-size: var(--font-size-s);
      cursor: pointer;
      color: var(--color-text-main);
    }
    .sleep-habits {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 8px;
    }
    .sleep-habit-pill {
      padding: 6px 10px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface);
      font-size: var(--font-size-xs);
      color: var(--color-text-soft);
    }
    /* finance helpers */
    .finance-grid {
      display: grid;
      gap: var(--space-s);
      grid-template-columns: 1fr;
    }
    @media (min-width: 520px) {
      .finance-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }
    .finance-note {
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
    }
    .safety-result {
      margin-top: 10px;
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-m);
      background: var(--color-surface-soft);
      padding: var(--space-m);
    }
    .safety-progress {
      width: 100%;
      height: 10px;
      border-radius: var(--radius-pill);
      background: var(--color-bg-app-alt);
      overflow: hidden;
      margin: 8px 0;
    }
    .safety-progress-fill {
      height: 100%;
      background: linear-gradient(90deg, #22c55e, #5be37d);
      transform-origin: left;
      transition: transform var(--motion-medium) var(--easing-standard);
    }
    .sleep-hero {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: var(--space-m);
      padding: var(--space-l);
      border-radius: var(--radius-card);
      background: linear-gradient(135deg, #0b1224, #182a4d, #312e81);
      color: #e5e7eb;
      box-shadow: 0 28px 60px rgba(0, 0, 0, 0.32);
      border: 1px solid rgba(255, 255, 255, 0.06);
      margin-bottom: var(--space-m);
    }
    .sleep-hero--empty {
      background: linear-gradient(135deg, #111827, #1f2937);
    }
    .sleep-hero-label {
      text-transform: uppercase;
      letter-spacing: 0.14em;
      font-size: var(--font-size-xs);
      opacity: 0.85;
    }
    .sleep-hero-main {
      font-size: 26px;
      font-weight: 900;
      margin: 4px 0;
    }
    .sleep-hero-sub {
      font-size: var(--font-size-m);
      opacity: 0.9;
    }
    .sleep-hero-meta {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      justify-content: flex-end;
    }
    .sleep-panels {
      display: grid;
      grid-template-columns: 1fr;
      gap: var(--space-m);
      margin-bottom: var(--space-m);
    }
    @media (min-width: 520px) {
      .sleep-panels {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }
    .sleep-panel {
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-card);
      background: var(--color-surface);
      box-shadow: var(--shadow-soft);
      padding: var(--space-m);
    }
    .sleep-steps {
      display: grid;
      gap: 8px;
      margin-top: 8px;
    }
    .sleep-step {
      padding: 10px;
      border-radius: var(--radius-m);
      background: var(--color-surface-soft);
      border: 1px dashed var(--color-border-subtle);
      font-size: var(--font-size-m);
      line-height: 1.4;
    }
    .sleep-env-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 10px;
    }
    .sleep-env-chip {
      padding: 8px 10px;
      border-radius: var(--radius-pill);
      border: 1px solid var(--color-border-subtle);
      background: var(--color-surface-soft);
      font-size: var(--font-size-xs);
      color: var(--color-text-soft);
    }
    .sleep-settings {
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-card);
      padding: var(--space-m);
      background: linear-gradient(180deg, rgba(15, 23, 42, 0.04), rgba(15, 23, 42, 0));
    }
    .pill {
      padding: 8px 12px;
      border-radius: var(--radius-pill);
      background: rgba(255, 255, 255, 0.16);
      border: 1px solid rgba(255, 255, 255, 0.2);
      color: inherit;
      font-weight: 600;
      font-size: var(--font-size-s);
      backdrop-filter: blur(4px);
    }
    .pill-ghost {
      background: rgba(255, 255, 255, 0.08);
    }
    .sleep-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: var(--space-m);
    }
    @media (min-width: 560px) {
      .sleep-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }
    .sleep-panel input[type="time"],
    .sleep-panel select[data-role="sleep-noise"] {
      width: 100%;
      min-width: 0;
      font-size: var(--font-size-l);
    }
    @media (max-width: 420px) {
      .sleep-panel input[type="time"] {
        font-size: var(--font-size-m);
      }
    }
    .sleep-panel {
      border: 1px solid rgba(148, 163, 184, 0.25);
      border-radius: var(--radius-card);
      padding: var(--space-m);
      background: linear-gradient(150deg, rgba(255, 255, 255, 0.96), rgba(237, 242, 247, 0.94));
      box-shadow: 0 18px 40px rgba(15, 23, 42, 0.12);
    }
    .sleep-timeline {
      display: grid;
      gap: 10px;
      margin-top: 10px;
    }
    .sleep-timeline-row {
      display: grid;
      grid-template-columns: 80px 1fr;
      gap: 8px;
      align-items: center;
      padding: 8px 10px;
      border-radius: var(--radius-m);
      border: 1px dashed var(--color-border-strong);
      background: var(--color-surface-soft);
    }
    .sleep-timeline-time {
      font-weight: 700;
      font-size: var(--font-size-m);
    }
    .sleep-timeline-text {
      font-size: var(--font-size-s);
      color: var(--color-text-main);
      line-height: 1.5;
    }
    .sleep-list {
      margin: 10px 0 0 16px;
      padding: 0;
      display: grid;
      gap: 6px;
      color: var(--color-text-main);
    }
    .sleep-placeholder {
      min-height: 160px;
      border: 1px dashed var(--color-border-subtle);
      border-radius: var(--radius-card);
      background: var(--color-surface-soft);
    }
    .finance-hero {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: var(--space-m);
      padding: var(--space-l);
      border-radius: var(--radius-card);
      background: linear-gradient(120deg, #0ea5e9, #22c55e);
      color: #fff;
      box-shadow: var(--shadow-card);
      margin-bottom: var(--space-m);
    }
    .finance-hero-label {
      text-transform: uppercase;
      letter-spacing: 0.14em;
      font-size: var(--font-size-xs);
      opacity: 0.85;
    }
    .finance-hero-main {
      font-size: 26px;
      font-weight: 900;
      margin: 4px 0;
    }
    .finance-hero-sub {
      font-size: var(--font-size-m);
      opacity: 0.9;
    }
    .finance-hero-meta {
      display: flex;
      flex-direction: column;
      gap: 8px;
      align-items: flex-end;
    }
    .finance-panel {
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-card);
      padding: var(--space-m);
      background: var(--color-surface);
      box-shadow: var(--shadow-soft);
    }
    .finance-plan-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: var(--space-m);
      margin-top: var(--space-m);
    }
    .finance-bucket {
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-m);
      padding: 10px;
      background: var(--color-surface-soft);
    }
    .finance-bucket-top {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 6px;
    }
    .finance-bucket-label {
      font-weight: 700;
    }
    .finance-bucket-amount {
      font-weight: 800;
      font-size: var(--font-size-m);
    }
    .finance-alloc-bar {
      width: 100%;
      height: 8px;
      border-radius: var(--radius-pill);
      background: var(--color-bg-app-alt);
      overflow: hidden;
      margin-bottom: 6px;
    }
    .finance-alloc-bar span {
      display: block;
      height: 100%;
      background: linear-gradient(90deg, #6366f1, #22c55e);
    }
    .finance-bucket-desc {
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
    }
    .finance-tip {
      grid-column: 1 / -1;
      border: 1px dashed var(--color-border-strong);
      border-radius: var(--radius-m);
      padding: 10px;
      font-size: var(--font-size-s);
      background: var(--color-surface);
    }
    .finance-placeholder {
      border: 1px dashed var(--color-border-subtle);
      border-radius: var(--radius-card);
      padding: var(--space-m);
      background: var(--color-surface-soft);
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
      margin-top: var(--space-m);
    }
    .finance-actions {
      margin: 8px 0 0 16px;
      padding: 0;
      display: grid;
      gap: 6px;
      color: var(--color-text-main);
    }
    .finance-compact-form {
      display: grid;
      gap: var(--space-s);
    }
    .finance-cat-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 8px;
      margin-top: 6px;
    }
    @media (min-width: 520px) {
      .finance-cat-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }
    .finance-cat-row {
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .finance-cat-label {
      min-width: 120px;
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
    }
    .finance-cat-input {
      flex: 1;
    }
    .finance-hero-gap {
      display: flex;
      align-items: center;
      gap: 10px;
      flex-wrap: wrap;
    }
    .finance-gap-badge {
      padding: 6px 10px;
      border-radius: var(--radius-pill);
      font-weight: 700;
      font-size: var(--font-size-s);
      border: 1px solid var(--color-border-strong);
      background: var(--color-surface-soft);
    }
    .finance-gap-badge--bad {
      border-color: #ef4444;
      background: rgba(239, 68, 68, 0.18);
      color: #7f1d1d;
    }
    .finance-gap-badge--good {
      border-color: #22c55e;
      background: rgba(34, 197, 94, 0.15);
      color: #065f46;
    }
    .finance-mini-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
      gap: var(--space-s);
      margin-top: 10px;
    }
    .finance-mini-card {
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-m);
      padding: 10px;
      background: var(--color-surface);
      box-shadow: var(--shadow-soft);
    }
    .finance-mini-title {
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
      margin-bottom: 6px;
    }
    .finance-mini-value {
      font-weight: 800;
      font-size: var(--font-size-l);
    }
    .finance-reco {
      display: grid;
      gap: 10px;
      margin-top: 10px;
    }
    .finance-reco-item {
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-m);
      padding: 10px;
      background: var(--color-surface-soft);
    }
    .finance-reco-lead {
      font-weight: 600;
      margin-bottom: 6px;
    }
    .finance-reco-tips {
      display: grid;
      gap: 4px;
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
    }
    .finance-chip-row {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 6px;
    }
    .finance-chip {
      padding: 6px 10px;
      border-radius: var(--radius-pill);
      background: var(--color-surface);
      border: 1px solid var(--color-border-subtle);
      font-size: var(--font-size-xs);
      color: var(--color-text-muted);
    }
    .finance-stack {
      display: grid;
      gap: var(--space-m);
    }
    /* family */
    .family-hero {
      display: grid;
      grid-template-columns: 1fr;
      gap: 12px;
      padding: var(--space-xl);
      border-radius: var(--radius-card);
      background: linear-gradient(135deg, rgba(91, 227, 125, 0.12), rgba(120, 195, 255, 0.12)),
        radial-gradient(circle at 20% 20%, rgba(0, 0, 0, 0.04), transparent 40%);
      color: var(--color-text-main);
      box-shadow: var(--shadow-card);
      margin-bottom: var(--space-m);
      border: 1px solid var(--color-border-subtle);
    }
    @media (min-width: 560px) {
      .family-hero {
        grid-template-columns: 1.05fr 0.95fr;
      }
    }
    .family-hero-title {
      font-size: 22px;
      font-weight: 900;
      margin: 0 0 6px;
    }
    .family-hero-sub {
      font-size: var(--font-size-m);
      line-height: 1.5;
      opacity: 0.9;
    }
    .family-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      align-items: center;
      justify-content: flex-start;
    }
    .family-hero-side {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      gap: 8px;
      justify-content: center;
    }
    .family-card-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: var(--space-m);
    }
    .family-card {
      border: 1px solid var(--color-border-subtle);
      border-radius: var(--radius-card);
      background: var(--color-surface);
      padding: var(--space-m);
      box-shadow: var(--shadow-soft);
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .family-card h4 {
      margin: 0;
      font-size: var(--font-size-l);
    }
    /* game */
    .game-hero {
      border-radius: var(--radius-card);
      padding: var(--space-l);
      background: linear-gradient(135deg, #1d4ed8, #4f46e5, #9333ea);
      color: #f8fafc;
      box-shadow: var(--shadow-card);
      display: grid;
      grid-template-columns: 1.1fr 1fr;
      gap: var(--space-l);
      align-items: center;
    }
    @media (max-width: 640px) {
      .game-hero {
        grid-template-columns: 1fr;
      }
    }
    .game-hero-title {
      font-size: 26px;
      font-weight: 900;
      margin: 4px 0;
    }
    .game-hero-sub {
      font-size: var(--font-size-m);
      opacity: 0.92;
      line-height: 1.5;
    }
    .game-hero-steps {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      align-items: center;
      justify-content: flex-end;
    }
    .game-hero-step {
      padding: 8px 10px;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(255, 255, 255, 0.24);
      background: rgba(255, 255, 255, 0.12);
      color: #fff;
      font-weight: 700;
      font-size: var(--font-size-s);
      backdrop-filter: blur(4px);
    }
    .game-topic-strip {
      display: flex;
      gap: 10px;
      overflow-x: auto;
      padding: 10px 4px 2px;
    }
    .game-topic-card {
      min-width: 160px;
      border-radius: var(--radius-card);
      padding: 12px;
      background: linear-gradient(140deg, rgba(255, 255, 255, 0.94), rgba(241, 245, 249, 0.9));
      border: 1px solid var(--color-border-subtle);
      box-shadow: var(--shadow-soft);
      transition: transform var(--motion-fast) var(--easing-standard), box-shadow var(--motion-fast) var(--easing-standard);
      cursor: pointer;
    }
    .game-topic-card:hover {
      transform: translateY(-2px);
      box-shadow: 0 16px 38px rgba(0, 0, 0, 0.14);
    }
    .game-topic-card--active {
      border-color: rgba(79, 70, 229, 0.6);
      box-shadow: 0 22px 46px rgba(79, 70, 229, 0.28);
    }
    .game-topic-title {
      font-weight: 700;
      margin-bottom: 6px;
    }
    .game-topic-tagline {
      font-size: var(--font-size-s);
      color: var(--color-text-soft);
      line-height: 1.4;
      margin-top: 4px;
    }
    .game-topic-pill {
      font-size: var(--font-size-xs);
      padding: 4px 8px;
      border-radius: var(--radius-pill);
      background: rgba(79, 70, 229, 0.1);
      color: #312e81;
    }
    .game-question-card {
      margin-top: var(--space-m);
      border-radius: var(--radius-card);
      padding: var(--space-l);
      background: linear-gradient(135deg, #0f172a, #111827);
      color: #e5e7eb;
      box-shadow: var(--shadow-card);
      position: relative;
      overflow: hidden;
    }
    .game-question-card::after {
      content: "";
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at 20% 20%, rgba(59, 130, 246, 0.22), transparent 35%),
        radial-gradient(circle at 80% 10%, rgba(167, 139, 250, 0.24), transparent 30%);
      pointer-events: none;
    }
    .game-question-top {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: var(--space-m);
      position: relative;
      z-index: 1;
    }
    .game-question-title {
      font-size: 22px;
      font-weight: 800;
      margin: 0 0 6px;
    }
    .game-question-meta {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      font-size: var(--font-size-s);
      color: #cbd5e1;
    }
    .game-question-body {
      margin-top: 12px;
      font-size: var(--font-size-xl);
      line-height: 1.6;
      position: relative;
      z-index: 1;
    }
    .game-helper {
      margin-top: 10px;
      border-radius: var(--radius-m);
      padding: 12px;
      border: 1px dashed var(--color-border-subtle);
      background: var(--color-surface-soft);
    }
    .game-helper-chips {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 6px;
    }
    .game-controls {
      margin-top: var(--space-m);
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      position: relative;
      z-index: 1;
    }
    .game-answer-row {
      display: flex;
      flex-direction: column;
      gap: 8px;
      margin-top: var(--space-m);
      position: relative;
      z-index: 1;
    }
    .game-answer-input {
      border-radius: 14px;
      border: 1px solid rgba(203, 213, 225, 0.4);
      padding: 12px 14px;
      font-size: var(--font-size-m);
      background: rgba(255, 255, 255, 0.08);
      color: #e5e7eb;
    }
    .game-history {
      margin-top: var(--space-m);
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: var(--space-m);
    }
    .game-history-card {
      border-radius: var(--radius-m);
      border: 1px dashed var(--color-border-subtle);
      padding: var(--space-m);
      background: var(--color-surface);
      color: var(--color-text-main);
    }
    .family-progress {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
      font-size: var(--font-size-s);
    }
    .family-pill {
      padding: 6px 10px;
      border-radius: var(--radius-pill);
      background: var(--color-surface-soft);
      border: 1px dashed var(--color-border-subtle);
      font-weight: 600;
    }
  </style>
</head>
<body>
  <div id="intro-root" class="intro-root"></div>
  <div class="app-shell app-shell--hidden">
    <header class="c-header" id="app-header"></header>
    <main id="app-main"></main>
  </div>
  <nav class="c-bottom-nav app-shell--hidden">
    <div class="c-bottom-nav-inner" id="bottom-nav"></div>
  </nav>
  <!-- CORE / STATE / SERVICES -->
  <script>
    (function () {
      "use strict";
      const AdviceApp = (window.AdviceApp = window.AdviceApp || {});
      AdviceApp.Core = (function () {
        let _uid = 0;
        function uid(prefix) {
          _uid += 1;
          return (prefix || "id") + "-" + Date.now().toString(36) + "-" + _uid.toString(36);
        }
        function deepClone(obj) {
          if (obj == null || typeof obj !== "object") return obj;
          try {
            return structuredClone(obj);
          } catch {
            return JSON.parse(JSON.stringify(obj));
          }
        }
        function safeParseJson(raw, fallback) {
          try {
            return JSON.parse(raw);
          } catch {
            return fallback;
          }
        }
        return { uid, deepClone, safeParseJson };
      })();
      AdviceApp.EventBus = (function () {
        const listeners = Object.create(null);
        function on(ev, cb) {
          if (!listeners[ev]) listeners[ev] = [];
          listeners[ev].push(cb);
        }
        function emit(ev, payload) {
          const arr = listeners[ev];
          if (!arr) return;
          arr.slice().forEach((cb) => {
            try {
              cb(payload);
            } catch (e) {
              console.error(e);
            }
          });
        }
        return { on, emit };
      })();
      AdviceApp.State = (function (bus, Core) {
        const KEY = "advice.app.state.v1";
        const defaultState = {
          user: { id: null, name: "Гость", username: null },
          theme: "light",
          lifeScore: null,
          scoresHistory: [],
          subscription: "none",
          currentView: "home",
          lastCheckInDate: null,
          lastCheckInScores: null,
          lastCheckInReasons: null,
          historyView: { open: false, selectedDate: null },
          attention: { mind: null, sleep: null, money: null },
          chat: { messages: [], psychologistName: null, isTyping: false },
          sleep: { lastPlan: null, lastInputs: null },
          finance: { income: null, plan: null, safetyFund: null },
          game: { activeTopic: null, questionIndex: 0, answers: {} },
          usageCounters: { psychologyDays: 0, sleepDays: 0, financeMonths: 0 },
          meta: { createdAt: null, updatedAt: null, version: 1 },
        };
        let state = load();
        function load() {
          try {
            const raw = localStorage.getItem(KEY);
            if (!raw) {
              const now = new Date().toISOString();
              const base = Core.deepClone(defaultState);
              base.meta.createdAt = now;
              base.meta.updatedAt = now;
              return base;
            }
            const parsed = Core.safeParseJson(raw, null);
            if (!parsed || typeof parsed !== "object") throw new Error();
            const merged = Object.assign({}, Core.deepClone(defaultState), parsed);
            merged.meta = merged.meta || {};
            merged.meta.version = 1;
            merged.meta.updatedAt = merged.meta.updatedAt || new Date().toISOString();
            merged.meta.createdAt = merged.meta.createdAt || merged.meta.updatedAt;
            merged.finance = Object.assign({}, Core.deepClone(defaultState.finance), merged.finance || {});
            merged.game = Object.assign({}, Core.deepClone(defaultState.game), merged.game || {});
            return merged;
          } catch {
            const now = new Date().toISOString();
            const base = Core.deepClone(defaultState);
            base.meta.createdAt = now;
            base.meta.updatedAt = now;
            return base;
          }
        }
        function save() {
          try {
            localStorage.setItem(KEY, JSON.stringify(state));
          } catch {}
        }
        function notify() {
          state.meta.updatedAt = new Date().toISOString();
          save();
          bus.emit("state:changed", getState());
        }
        function getState() {
          return Core.deepClone(state);
        }
        function setState(patch) {
          state = Object.assign({}, state, patch);
          notify();
        }
        function updateSlice(key, patch) {
          state[key] = Object.assign({}, state[key] || {}, patch);
          notify();
        }
        function applyDailyCheckIn(scores, reasons, note) {
          const { mind, sleep, money } = scores || {};
          if (!mind || !sleep || !money) return;
          const avg = (Number(mind) + Number(sleep) + Number(money)) / 3;
          const today = new Date().toISOString().slice(0, 10);
          const snapshot = {
            date: today,
            scores: { mind: Number(mind), sleep: Number(sleep), money: Number(money) },
            lifeScore: avg,
            reasons: Core.deepClone(reasons || null),
            note: note || "",
          };
          const current = getState();
          const history = (current.scoresHistory || []).concat([snapshot]);
          const hv = Object.assign({}, current.historyView || {}, { selectedDate: snapshot.date });
          setState({
            lifeScore: avg,
            scoresHistory: history,
            lastCheckInDate: today,
            lastCheckInScores: snapshot.scores,
            lastCheckInReasons: snapshot.reasons,
            historyView: hv,
          });
        }
        function updateHistoryNote(date, noteText) {
          if (!date) return;
          const current = getState();
          const history = (current.scoresHistory || []).map((item) => {
            if (item.date !== date) return item;
            return Object.assign({}, item, { note: noteText || "" });
          });
          setState({ scoresHistory: history });
        }
        return { getState, setState, updateSlice, applyDailyCheckIn, updateHistoryNote };
      })(AdviceApp.EventBus, AdviceApp.Core);
      AdviceApp.Services = (function (Core) {
        const NAMES = ["Андрей", "Елена", "Алексей", "Мария", "Дмитрий", "Ольга", "Сергей", "Наталья"];
        const MIN_DELAY = 40000;
        const MAX_DELAY = 80000;
        function randInt(min, max) {
          return Math.floor(Math.random() * (max - min + 1)) + min;
        }
        function randItem(arr) {
          return arr && arr.length ? arr[randInt(0, arr.length - 1)] : null;
        }
        function randomPsychologistName() {
          return randItem(NAMES) || "Андрей";
        }
        function sendToPsychologyAI(message, ctx) {
          const psychologistName = (ctx && ctx.psychologistName) || randomPsychologistName();
          const delay = MIN_DELAY + randInt(0, MAX_DELAY - MIN_DELAY);
          return new Promise((resolve) => {
            setTimeout(() => {
              resolve({
                psychologistName,
                text: "Спасибо, что поделились. Я прочитал ваше сообщение и хочу чуть глубже понять, что происходит. Можете описать, в какие моменты ощущения особенно обостряются?",
              });
            }, delay);
          });
        }
        function buildSleepPlan(inputs) {
          const safe = Object.assign(
            { sleepWith: "alone", budgetLevel: "free", wakeTime: "07:00", noisePreference: "silence" },
            inputs || {}
          );
          const [h, m] = (safe.wakeTime || "07:00").split(":").map((n) => Number(n) || 0);
          const now = new Date();
          const wake = new Date(now);
          wake.setHours(h, m, 0, 0);
          const target = new Date(wake.getTime() - 7.5 * 60 * 60 * 1000);
          const windDown = new Date(target.getTime() - 45 * 60 * 1000);
          const pad = (n) => (n < 10 ? "0" + n : "" + n);
          const goToBed = pad(target.getHours()) + ":" + pad(target.getMinutes());
          const windDownStart = pad(windDown.getHours()) + ":" + pad(windDown.getMinutes());
          const envTip =
            safe.sleepWith === "alone"
              ? "Сделайте комнату максимально тихой и тёмной. За 30–40 минут до сна уберите яркий экран и снизьте освещение."
              : "Согласуйте с тем, кто спит рядом, простые правила: минимум света и звука за 30–40 минут до сна, без громких уведомлений.";
          const moneyTip =
            safe.budgetLevel === "free"
              ? "Фокус на бесплатных изменениях: стабильный режим, проветривание, тёплый душ перед сном, отсутствие телефона в кровати."
              : "Можно постепенно инвестировать в комфорт: подушка и матрас под вас, плотные шторы, маска для сна, беруши — всё это даёт заметный эффект.";
          const audioChoice =
            safe.noisePreference === "water"
              ? "Журчание водопада"
              : safe.noisePreference === "white"
              ? "Белый шум"
              : safe.noisePreference === "melody"
              ? "Спокойная мелодия"
              : "Тишина";
          const durationHours = 7.5;
          const chronotypeLabel = safe.wakeTime <= "06:30" ? "Жаворонок" : safe.wakeTime >= "08:30" ? "Сова" : "Универсальный";
          const timeline = [
            { label: "-60 мин", text: "Успокоить освещение, переключиться на тихие задачи." },
            { label: "-45 мин", text: "Чтение или тёплый душ, убрать телефон из спальни." },
            { label: "-20 мин", text: "Установить будильник, надеть маску/беруши, проветрить." },
            { label: "Отбой", text: `Лечь в ${goToBed}, включить выбранный звук: ${audioChoice}.` },
          ];
          const environmentChecklist = [
            "Температура 18–21°C, плотные шторы или маска.",
            "Подушка по вашей высоте, матрас без ям.",
            "Телефон на беззвучном, уведомления выключены.",
            "Бутылка воды и беруши рядом, чтобы не вставать.",
          ];
          const microHabits = [
            "5 минут дневника перед сном для разгрузки головы.",
            "2–3 минуты дыхания 4-7-8 или длинный выдох через рот.",
            "Утренний свет в течение 10 минут для фиксации ритма.",
          ];
          return {
            goToBed,
            wakeTime: safe.wakeTime,
            windDownStart,
            envTip,
            moneyTip,
            audioChoice,
            durationHours,
            chronotypeLabel,
            timeline,
            environmentChecklist,
            microHabits,
            rawInputs: Core.deepClone(safe),
          };
        }
        function buildFinancePlan(income, categories) {
          const inc = Math.max(0, Number(income) || 0);
          const cats = Object.assign(
            { housing: 0, food: 0, transport: 0, utilities: 0, debts: 0, leisure: 0, other: 0 },
            categories || {}
          );
          const parsedCats = Object.keys(cats).reduce((acc, key) => {
            acc[key] = Math.max(0, Number(cats[key]) || 0);
            return acc;
          }, {});
          const totalExpenses = Object.values(parsedCats).reduce((sum, v) => sum + v, 0);
          const gap = inc - totalExpenses;
          const overspend = inc > 0 && gap < 0;
          if (!inc) {
            return {
              income: 0,
              buckets: [],
              comment: "Укажите ежемесячный доход и разложите траты по категориям, чтобы увидеть рекомендации.",
              currentPattern: "Жильё, еда, транспорт, ЖКХ/долги, развлечения, прочее.",
              savingsRate: 0,
              essentialsRate: 0,
              lifestyleRate: 0,
              totalExpenses,
              gap,
              overspend,
              categories: parsedCats,
              recommendations: [],
            };
          }
          const recommendedCaps = {
            housing: inc * 0.35,
            food: inc * 0.2,
            transport: inc * 0.1,
            utilities: inc * 0.1,
            debts: inc * 0.15,
            leisure: inc * 0.1,
            other: inc * 0.05,
          };
          const adviceByCategory = {
            housing: [
              "Сравните текущую ставку аренды с рынком — можно пересмотреть договор или искать временно более компактный вариант.",
              "Отдельно разберите ЖКХ: что даёт основной рост — отопление, вода или электричество, где можно снизить потребление.",
            ],
            food: [
              "Переход на план меню + закупки 1–2 раза в неделю сокращает импульсивные траты.",
              "Замените часть готовой еды на простые блюда: крупы, сезонные овощи, яйца, бобовые.",
            ],
            transport: [
              "Откажитесь от такси в будни: проездной + пешие промежуточные участки дают экономию.",
              "Сгруппируйте поездки и поручения в один маршрут, чтобы не кататься лишний раз.",
            ],
            utilities: [
              "Проверьте тарифы на интернет/связь, отключите дублирующие подписки.",
              "Сократите потребление: умные лампы, экономичные режимы стирки, контроль горячей воды.",
            ],
            debts: [
              "Реструктуризация или перенос в банк с меньшей ставкой уменьшит ежемесячный платёж.",
              "Сфокусируйтесь на одном долге снежным комом, остальные платите минимально.",
            ],
            leisure: [
              "Жёсткий лимит на развлечения на неделю + кеш в конверте снижает перетраты.",
              "Ищите бесплатные альтернативы: прогулки, спорт во дворе, библиотека вместо подписок.",
            ],
            other: ["Пересмотрите мелкие регулярные траты — комиссии, дубли подписок, покупки по привычке."],
          };
          const recommendations = Object.keys(parsedCats).reduce((acc, key) => {
            const value = parsedCats[key];
            const cap = recommendedCaps[key] || 0;
            if (value <= 0) return acc;
            const overRatio = cap ? value / cap : 0;
            const isOver = overRatio > 1.05;
            const base = adviceByCategory[key] || [];
            const lead = isOver
              ? `Категория «${key}» выбивается из нормы: ${value.toLocaleString("ru-RU")} ₽ при целевом уровне до ${Math.round(cap).toLocaleString("ru-RU")} ₽.`
              : `Категория «${key}» в рамках нормы, оставьте короткий недельный лимит и контроль.`;
            acc.push({ key, text: lead, tips: base });
            return acc;
          }, []);
          const essentials = parsedCats.housing + parsedCats.food + parsedCats.transport + parsedCats.utilities + parsedCats.debts;
          const lifestyle = parsedCats.leisure + parsedCats.other;
          let save = inc - essentials - lifestyle;
          const minSave = Math.round(inc * 0.1);
          if (save < minSave) {
            const delta = minSave - save;
            const cutEss = Math.round(delta * 0.6);
            const cutLife = delta - cutEss;
            save = Math.max(0, save);
            parsedCats.housing = Math.max(0, parsedCats.housing - Math.round(cutEss * 0.35));
            parsedCats.food = Math.max(0, parsedCats.food - Math.round(cutEss * 0.25));
            parsedCats.transport = Math.max(0, parsedCats.transport - Math.round(cutEss * 0.2));
            parsedCats.leisure = Math.max(0, parsedCats.leisure - cutLife);
          }
          const buckets = [
            {
              key: "necessities",
              label: "База (жильё, еда, транспорт, ЖКХ, долги)",
              amount: essentials,
              description: "Проверяем, не превышает ли 60–65% дохода.",
            },
            {
              key: "lifestyle",
              label: "Образ жизни + прочее",
              amount: lifestyle,
              description: "Подписки, развлечения, непредвиденные траты.",
            },
            {
              key: "savings",
              label: "Сбережения / подушка",
              amount: Math.max(0, inc - essentials - lifestyle),
              description: "Цель — минимум 10% от дохода, лучше 20%.",
            },
          ];
          const ratio = buckets[2].amount / inc;
          const essentialsRate = essentials / inc;
          const lifestyleRate = lifestyle / inc;
          const comment = overspend
            ? `Траты превышают доход на ${Math.abs(gap).toLocaleString("ru-RU")} ₽. Начните с жилья/ЖКХ, еды и транспорта — там больше всего эффекта.`
            : ratio >= 0.2
            ? "Темп накоплений выше 20% — можно ускорять подушку или инвестиции."
            : "Дотяните сбережения до 10–20% за счёт оптимизации жилья, еды, транспорта и подписок.";
          return {
            income: inc,
            buckets,
            comment,
            currentPattern: "Данные разложены по категориям, продолжаем вести их раз в неделю.",
            savingsRate: ratio,
            essentialsRate,
            lifestyleRate,
            totalExpenses,
            gap,
            overspend,
            categories: parsedCats,
            recommendations,
          };
        }
      function buildSafetyFund(current, expenses, months, monthlySave) {
        const cur = Math.max(0, Number(current) || 0);
        const exp = Math.max(0, Number(expenses) || 0);
        const targetMonths = Math.max(1, Number(months) || 3);
        const monthly = Math.max(0, Number(monthlySave) || 0);
        const target = exp * targetMonths;
        const gap = Math.max(0, target - cur);
        const progress = target ? Math.min(1, cur / target) : 0;
        const monthsToGoal = monthly > 0 && gap > 0 ? Math.ceil(gap / monthly) : null;
        const status =
          target === 0
            ? "Укажите реальные траты, чтобы посчитать подушку."
            : gap === 0
            ? "Подушка собрана — можно переходить к инвестициям."
            : monthly > 0
            ? `Останется накопить ${gap.toLocaleString("ru-RU")} ₽ — это около ${monthsToGoal || 1} мес. при текущем темпе.`
            : "Добавьте сумму ежемесячного взноса, чтобы понять сроки накопления.";
        return {
          current: cur,
          expenses: exp,
          targetMonths,
          monthlySave: monthly,
          target,
          gap,
          progress,
          monthsToGoal,
          status,
        };
      }
      const GAME_TOPICS = [
        {
          key: "future",
          title: "Картина будущего",
          tagline: "Общий горизонт и смелые планы",
          accent: "#22c55e",
          base: [
            "Как вы хотите просыпаться через год?",
            "Какие города или страны хочется попробовать?",
            "Какой общий ритуал выходного хотелось бы закрепить?",
            "Какую крупную цель вы тянете в тени?",
            "Чего не должно быть в вашей жизни через год?",
            "Какой смелый эксперимент хотите провести вместе?",
            "Как выглядит ваш идеальный день через 5 лет?",
            "Что из текущих страхов хочется закрыть первым?",
            "Какой навык точно пригодится вам обоим?",
            "Какой отдых ощущается как мечта?",
          ],
        },
        {
          key: "finance_duo",
          title: "Деньги вдвоём",
          tagline: "Баланс доходов и спокойствия",
          accent: "#0ea5e9",
          base: [
            "На что сейчас уходит больше всего денег?",
            "Какую подписку вы бы убрали без боли?",
            "Как выглядит ваш безопасный минимум бюджета?",
            "Какая покупка точно стоит ожидания?",
            "Где можно заменить такси на что-то другое?",
            "Что нужно, чтобы копилка росла стабильно?",
            "Какую сумму хотите видеть в подушке через полгода?",
            "Какая финансовая ошибка вас многому научила?",
            "Что будет первым вложением в себя?",
            "Как договориться о крупных тратах?",
          ],
        },
        {
          key: "feelings",
          title: "Чувства и поддержка",
          tagline: "Как говорить и слышать друг друга",
          accent: "#ec4899",
          base: [
            "Когда вы чувствуете поддержку сильнее всего?",
            "Что помогает выдыхать после тяжёлого дня?",
            "Какие слова вас ранят, даже если сказаны в шутку?",
            "Какой жест заботы хочется получать чаще?",
            "Какая граница для вас принципиальна?",
            "Как вы рассказываете о тревоге или страхах?",
            "Что помогает мириться после конфликтов?",
            "Как бы вы описали ощущение безопасности?",
            "Что сейчас даёт больше всего энергии?",
            "Чего точно делать нельзя, если тяжело?",
          ],
        },
        {
          key: "stories",
          title: "Истории и память",
          tagline: "Лучшие моменты и новые легенды",
          accent: "#f59e0b",
          base: [
            "Какое ваше общее приключение хочется повторить?",
            "Какой момент вы бы отправили себе прошлым?",
            "Какая фраза из фильма стала вашим мемом?",
            "Когда вы смеялись до слёз последний раз?",
            "Какая случайность изменила вашу историю?",
            "Что вы забываете рассказывать о своём детстве?",
            "Какой запах сразу возвращает вас в прошлое?",
            "Какая песня — это чисто вы двое?",
            "Что из бытовухи стало легендой?",
            "Когда вы впервые почувствовали «мы»?",
          ],
        },
        {
          key: "habits",
          title: "Дела и ритм",
          tagline: "Быт без споров и больше энергии",
          accent: "#22d3ee",
          base: [
            "Какой утренний ритуал стоит закрепить?",
            "Что мешает ложиться спать вовремя?",
            "Как вы делите домашние задачи без споров?",
            "Какая привычка сделает ваши выходные лучше?",
            "Какой спортивный или wellness-ритуал попробовать?",
            "Какая мелочь экономит вам время?",
            "Как договориться об ужинах на неделю?",
            "Какая задача копится и тянет вниз?",
            "Что поможет не откладывать важное?",
            "Как вы хвалите друг друга за прогресс?",
          ],
        },
        {
          key: "home",
          title: "Дом и уют",
          tagline: "Среда, где легко отдыхать",
          accent: "#f43f5e",
          base: [
            "Что в квартире/доме точно хочется изменить?",
            "Какой уголок сделать вашим тихим местом?",
            "Как вы делите пространство, чтобы всем хватало?",
            "Что добавить, чтобы лучше спать?",
            "Какие правила по уборке работают без конфликтов?",
            "Как оптимизировать ЖКХ или связь без потери качества?",
            "Какой запах/свет вы хотите дома вечером?",
            "Какая мебель или деталь создаст уют?",
            "Как организовать хранение, чтобы не утонуть в вещах?",
            "Какой бытовой девайс окупится быстрее всего?",
          ],
        },
        {
          key: "reflection",
          title: "Рефлексия",
          tagline: "Замечать прогресс и пересобирать цели",
          accent: "#14b8a6",
          base: [
            "Чему вас научил последний конфликт?",
            "Какое качество в друг друге вы берегёте больше всего?",
            "Что бы вы изменили в своём дне, если бы могли?",
            "Когда вы в последний раз чувствовали гордость за себя?",
            "Как вы замечаете, что устали?",
            "Что помогает вам просить о помощи?",
            "Какой совет себе прошлому вы бы дали?",
            "Что хочется отпустить без сожаления?",
            "Как вы понимаете, что двигаетесь в верном направлении?",
            "Какая эмоция вам чаще всего доступна?",
          ],
        },
        {
          key: "honest",
          title: "Честно и смело",
          tagline: "Говорить о сложном без напряжения",
          accent: "#fb7185",
          base: [
            "Что вам стыдно спрашивать, но хочется?",
            "О чём вы волнуетесь, но молчите?",
            "Какая тема кажется табу, но её нужно поднять?",
            "Что бы вы изменили в интимной стороне отношений?",
            "Какой вопрос вам сложнее всего обсудить в семье?",
            "Когда вы чувствуете ревность?",
            "Что вы скрываете, чтобы не тревожить партнёра?",
            "Как вы хотите получать обратную связь о себе?",
            "Что для вас главный сигнал заботы?",
            "Какой компромисс вам дался тяжелее всего?",
          ],
        },
        {
          key: "fun",
          title: "Ирония и заряд",
          tagline: "Лёгкие вопросы, чтобы сбросить напряжение",
          accent: "#a855f7",
          base: [
            "Какой самый тупой вопрос вы слышали?",
            "Что вас смешит в бытовухе каждый раз?",
            "Какую смешную привычку вы скрываете?",
            "Какая фраза разряжает любую ссору?",
            "Какой мем идеально описывает ваш день?",
            "Что было самым странным подарком?",
            "Какой бытовой лайфхак звучит дико, но работает?",
            "С каким животным вы себя сравнили бы сегодня?",
            "Какая ваша guilty pleasure?",
            "Какой вопрос вас всегда ставит в тупик?",
          ],
        },
        {
          key: "cinema",
          title: "Фильмы и герои",
          tagline: "Истории и персонажи как зеркало",
          accent: "#38bdf8",
          base: [
            "Какой фильм вы бы показали детям первыми?",
            "Какой персонаж похож на вас?",
            "Какая сцена вас всегда растрогает?",
            "Какой саундтрек описывает ваш день?",
            "Какая история вдохновляет идти вперёд?",
            "Какой фильм вы бы сняли про себя?",
            "Кто из героев — ваш идеальный наставник?",
            "Какой сериал вы бы пересмотрели вместе?",
            "Какой антигерой вам симпатичен и почему?",
            "Какой жанр отражает ваш текущий период?",
          ],
        },
      ];
      function expandQuestions(base) {
        const patterns = [
          "— что изменится, если мы сделаем это вдвоём?",
          "— какая маленькая версия возможна уже на этой неделе?",
          "— что мешает и как это убрать?",
          "— самый смелый вариант оответа?",
        ];
        const out = [];
        base.forEach((q) => {
          out.push(q);
          patterns.forEach((addon) => {
            if (out.length < 40) out.push(`${q} ${addon}`);
          });
        });
        while (out.length < 40) {
          out.push(`Свободный раунд №${out.length + 1}: расскажите историю по теме.`);
        }
        return out.slice(0, 40);
      }
      const GAME_TOPICS_EXPANDED = GAME_TOPICS.map((topic) => Object.assign({}, topic, { questions: expandQuestions(topic.base) }));
      function getGameTopics() {
        return Core.deepClone(GAME_TOPICS_EXPANDED);
      }
      return { randomPsychologistName, sendToPsychologyAI, buildSleepPlan, buildFinancePlan, buildSafetyFund, getGameTopics };
    })(AdviceApp.Core);
    })();
  </script>
  <!-- UI COMPONENTS -->
  <script>
    (function () {
      "use strict";
      const AdviceApp = window.AdviceApp;
      const State = AdviceApp.State;
      const Services = AdviceApp.Services;
      AdviceApp.UI = (function () {
        const Components = {};
        let attentionChatAnimated = false;
        const UI_KNOWN_VIEWS = ["home", "menu", "profile", "chat", "sleep", "finance", "family", "history", "game"];
        function getQuestionLabelUI(kind) {
          switch (kind) {
            case "mind":
              return "Как вы себя чувствуете в психологическом плане?";
            case "sleep":
              return "Как прошёл ваш сон?";
            case "money":
              return "Как у вас с финансами сегодня?";
            default:
              return kind;
          }
        }
        function escapeHtml(str) {
          return (str || "").replace(/[&<>"']/g, (ch) => {
            const map = { "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#39;" };
            return map[ch] || ch;
          });
        }
        function formatDateShort(dateStr) {
          if (!dateStr) return "";
          const d = new Date(dateStr + "T00:00:00");
          if (isNaN(d.getTime())) return dateStr;
          const today = new Date();
          const todayStr = today.toISOString().slice(0, 10);
          const y = new Date();
          y.setDate(today.getDate() - 1);
          const yStr = y.toISOString().slice(0, 10);
          const iso = d.toISOString().slice(0, 10);
          if (iso === todayStr) return "сегодня";
          if (iso === yStr) return "вч.";
          const wds = ["вс", "пн", "вт", "ср", "чт", "пт", "сб"];
          return wds[d.getDay()];
        }
        function lifeMood(score) {
          if (score == null || isNaN(score)) return "Как только вы пройдёте первый чек-ин, здесь появится индекс и динамика.";
          if (score >= 4.3) return "Сейчас у вас очень высокий субъективный уровень качества жизни. Важно поддерживать этот уровень без выгорания.";
          if (score >= 3.6) return "В целом вы держитесь на хорошем уровне. Есть точки роста, и мы аккуратно подсветим, где легче всего усилить эффект.";
          if (score >= 2.7) return "Субъективно всё ощущается средне. Это нормальная точка старта, когда уже есть смысл системно работать с психикой, сном и деньгами.";
          if (score >= 1.8) return "Сейчас вам непросто. Наша задача — вытащить из минуса, стабилизировать сон и снизить нагрузку на психику.";
          return "Похоже, сейчас очень тяжёлый период. Мы будем выстраивать план максимально бережно, шаг за шагом.";
        }
        function percentileText(score) {
          if (score == null || isNaN(score)) return "";
          const p = Math.round((score / 5) * 100);
          const cl = Math.max(1, Math.min(99, p));
          return `Вы примерно в ${cl}-м перцентиле относительно собственного максимального состояния.`;
        }
        function scoreSeverity(score) {
          if (score == null || isNaN(score)) {
            return { tier: "neutral", label: "Нет оценки за сегодня", border: "var(--color-border-subtle)", bg: "rgba(148, 163, 184, 0.16)" };
          }
          const v = Number(score);
          if (v >= 4.5) {
            return { tier: "good", label: "Сильный день", border: "#16a34a", bg: "rgba(22, 163, 74, 0.20)" };
          }
          if (v >= 3.5) {
            return { tier: "ok", label: "Нормальный день", border: "#f59e0b", bg: "rgba(245, 158, 11, 0.22)" };
          }
          return { tier: "bad", label: "Тяжёлый день", border: "#ef4444", bg: "rgba(239, 68, 68, 0.24)" };
        }
        function thermoColor(score) {
          const min = 0,
            max = 5;
          const val = Math.max(min, Math.min(max, Number(score) || 0));
          const ratio = val / max;
          const r = Math.round(255 - ratio * 155);
          const g = Math.round(60 + ratio * 150);
          const color = `rgb(${r}, ${g}, 90)`;
          const darker = `rgb(${Math.max(0, r - 35)}, ${Math.max(0, g - 25)}, 70)`;
          return { start: color, end: darker };
        }
        function renderAttentionCard(s) {
          const att = s.attention || {};
          const keys = ["mind", "sleep", "money"];
          const labels = { mind: "Психика", sleep: "Сон", money: "Финансы" };
          let bubbleIndex = 1;
          const bubbles = keys
            .map((key) => {
              const slot = att[key];
              if (!slot || !slot.reasons || !slot.reasons.length) return "";
              const chips = slot.reasons.map((r) => `<span class="attention-chip">${r}</span>`).join("");
              const html = `<div class="attention-bubble" style="--bubble-index:${bubbleIndex};"> <div class="attention-bubble-header"> <div class="attention-item-title">${labels[key] || key}</div> <div class="attention-bubble-score">${slot.score || "—"} ★</div> </div> <div class="attention-chips">${chips}</div> </div>`;
              bubbleIndex += 1;
              return html;
            })
            .filter(Boolean)
            .join("");
          if (!bubbles) return "";
          const animate = !attentionChatAnimated;
          attentionChatAnimated = true;
          const introBubble = `<div class="attention-bubble attention-bubble--note" style="--bubble-index:0;"> Зафиксировали слабые места. Вернёмся к ним в рекомендациях. </div>`;
          return `<section class="c-card attention-card"> <div class="section-title">Точки внимания</div> <div class="section-sub"> Что именно тянет вниз каждое направление — мы сохранили это как переписку. </div> <div class="attention-chat ${animate ? "attention-chat--intro" : ""}"> ${introBubble} ${bubbles} </div> </section>`;
        }
        function renderBackRow() {
          return `<div class="back-row"> <button class="back-button" data-action="nav-back"><span>←</span><span>Назад</span></button> </div>`;
        }
        function renderCheckInEcho(s) {
          const scores = s.lastCheckInScores || null;
          const reasons = s.lastCheckInReasons || null;
          if (!scores) {
            return `<section class="c-card"> <div class="section-title">Ваши ответы</div> <div class="section-sub">Как только вы пройдёте опрос, здесь появятся оценки и причины.</div> </section>`;
          }
          const labels = {
            mind: "Психика",
            sleep: "Сон",
            money: "Финансы",
          };
          const rows = ["mind", "sleep", "money"]
            .map((key) => {
              const score = scores[key];
              const chips = reasons && reasons[key] && reasons[key].length
                ? reasons[key].map((r) => `<span class="chip">${r}</span>`).join("")
                : `<span class="chip">Причины не выбраны</span>`;
              return `<div class="history-row" style="gap:12px;"> <div> <div class="history-row-title">${labels[key] || key}</div> <div class="history-row-sub">${getQuestionLabelUI(key)}</div> </div> <div class="history-row-score">${score || "—"}★</div> </div> <div class="chips-row" style="margin-top:6px;">${chips}</div>`;
            })
            .join("<div style='height:8px;'></div>");
          return `<section class="c-card"> <div class="section-title">Ваши ответы</div> <div class="section-sub">Используем их, чтобы строить рекомендации в чатах, сне и финансах.</div> ${rows} </section>`;
        }
        Components.renderHeader = (s) => {
          const initials = (s.user.name || "Гость").slice(0, 1).toUpperCase();
          const sub =
            s.subscription === "pro"
              ? "PRO · психика, сон, деньги"
              : s.subscription === "standard"
              ? "STANDARD · психологическая поддержка"
              : "Демо-режим · без подписки";
          const chip = s.lifeScore != null ? `Индекс дня · ${s.lifeScore.toFixed(1)} / 5` : "Индекс дня ещё не рассчитан";
          return `<div class="c-header-left"> <div class="avatar">${initials}</div> <div> <div class="c-header-title-main">ADVICE</div> <div class="c-header-title-sub">${sub}</div> </div> </div> <div class="c-header-pill"> <span class="c-header-pill-dot"></span> <span>${chip}</span> </div>`;
        };
        Components.renderBottomNav = (s) => {
          const cv = UI_KNOWN_VIEWS.includes(s.currentView) ? s.currentView : "home";
          const item = (view, label, icon) => {
            const active = cv === view;
            return `<button class="bottom-nav-item ${active ? "bottom-nav-item--active" : ""}" data-action="nav" data-view="${view}"> <div class="bottom-nav-dot ${active ? "bottom-nav-dot--accent" : ""}">${icon}</div> <div>${label}</div> </button>`;
          };
          return `${item("home", "Главная", "●")} ${item("menu", "Меню", "⋯")} ${item("family", "Семья", "👪")} ${item("profile", "Профиль", "👤")} ;`;
        };
        Components.renderLifeLine = (s) => {
          const history = s.scoresHistory || [];
          if (!history.length) {
            return `<section class="c-card c-card--flat lifeline-card"> <div class="lifeline-header-row"> <div> <div class="lifeline-label-main">История последних дней</div> <div class="lifeline-label-sub"> Здесь появится короткая полоска по вашим чек-инам. </div> </div> </div> </section>`;
          }
          const maxSlots = 5;
          let last = history.slice(-maxSlots);
          while (last.length < maxSlots) last.unshift(null);
          const bars = last
            .map((item) => {
              if (!item) {
                return `<div class="lifeline-day"> <div class="lifeline-bar lifeline-bar--placeholder"></div> <div class="lifeline-day-score">—</div> <div class="lifeline-day-label lifeline-day-label--placeholder">—</div> </div>`;
              }
              const sVal = item.lifeScore || 0;
              const height = Math.max(8, Math.round((sVal / 5) * 100));
              const opacity = 0.3 + (sVal / 5) * 0.7;
              const colors = thermoColor(sVal);
              return `<div class="lifeline-day"> <div class="lifeline-bar"> <div class="lifeline-bar-inner" style="height:${height}%;opacity:${opacity.toFixed(2)};--bar-color-start:${colors.start};--bar-color-end:${colors.end};"></div> </div> <div class="lifeline-day-score">${sVal.toFixed(1)}</div> <div class="lifeline-day-label">${formatDateShort(item.date)}</div> </div>`;
            })
            .join("");
          return `<section class="c-card c-card--flat lifeline-card"> <div class="lifeline-header-row"> <div> <div class="lifeline-label-main">История последних дней</div> <div class="lifeline-label-sub"> Каждая колонка — ваш субъективный индекс за день. </div> <div class="lifeline-percentile"> ${percentileText(s.lifeScore) || "Продолжайте отмечаться, чтобы мы видели динамику."} </div> </div> </div> <div class="lifeline-track"> ${bars} </div> <div class="lifeline-actions"> <button class="c-button c-button--secondary" data-action="history-open-full"> Открыть историю </button> </div> </section>`;
        };
        Components.renderHistoryView = (s) => {
          const history = s.scoresHistory || [];
          const navRow = renderBackRow();
          if (!history.length) {
            return `<section class="c-card"> ${navRow} <div class="c-card-header"> <div> <div class="c-card-title">История дней</div> <div class="c-card-sub">Пока нет ни одного чек-ина.</div> </div> </div> <p class="section-sub"> Вернитесь на главную и пройдите первый опрос по психике, сну и финансам. </p> <button class="c-button c-button--secondary" data-action="history-back"> На главную </button> </section>`;
          }
          const prefs = s.historyView || {};
          const sorted = history.slice().sort((a, b) => (a.date < b.date ? 1 : -1));
          const selectedDate = prefs.selectedDate && sorted.find((h) => h.date === prefs.selectedDate) ? prefs.selectedDate : sorted[0] && sorted[0].date;
          const selected = sorted.find((h) => h.date === selectedDate);
          function reasonBlock(key) {
            if (!selected) return "";
            const slot = selected.reasons && selected.reasons[key];
            if (slot && slot.reasons && slot.reasons.length) {
              return slot.reasons.map((r) => `<span class="history-reason-chip">${r}</span>`).join("");
            }
            return `<span class="history-reason-chip">Причины не зафиксированы</span>`;
          }
          function detailBlock(title, score, key) {
            const sevBlock = scoreSeverity(score);
            return `<div class="history-detail-block" style="border-color:${sevBlock.border};background:linear-gradient(160deg, ${sevBlock.bg}, transparent 60%), var(--color-surface);"> <div class="history-detail-block-title">${title}</div> <div class="history-detail-score">${score} ★</div> <div class="history-reasons">${reasonBlock(key)}</div> </div>`;
          }
          const list = sorted
            .map((item) => {
              const sev = scoreSeverity(item.lifeScore);
              return `<button class="history-row ${item.date === selectedDate ? "history-row--active" : ""}" data-action="history-select" data-date="${item.date}" style="border-color:${sev.border};background:linear-gradient(120deg, ${sev.bg}, transparent 70%);"> <div> <div class="history-row-title">${item.date}</div> <div class="history-row-sub"> ${sev.label} · Психика ${item.scores.mind} ★ · Сон ${item.scores.sleep} ★ · Финансы ${item.scores.money} ★ </div> </div> <div class="history-row-score">${item.lifeScore.toFixed(1)}</div> </button>`;
            })
            .join("");
          const detail = selected
            ? `<div class="history-detail"> <h5>${selected.date} · ${selected.lifeScore.toFixed(1)} / 5</h5> <div class="history-detail-grid"> ${detailBlock("Психика", selected.scores.mind, "mind")} ${detailBlock("Сон", selected.scores.sleep, "sleep")} ${detailBlock("Финансы", selected.scores.money, "money")} </div> <div class="history-note-row"> <textarea class="history-note" data-role="history-note" data-date="${selected.date}" placeholder="Добавьте, почему вы так себя чувствуете именно в этот день">${escapeHtml(selected.note || "")}</textarea> <button class="c-button" data-action="history-save-note" data-date="${selected.date}"> Сохранить заметку </button> </div> </div>`
            : `<div class="history-detail">Выберите чек-ин, чтобы увидеть детали.</div>`;
          return `<section class="c-card"> ${navRow} <div class="c-card-header"> <div> <div class="c-card-title">История дней</div> <div class="c-card-sub">Все чек-ины и причины просадки по направлениям.</div> </div> <button class="c-button c-button--secondary" data-action="history-back"> На главную </button> </div> <div class="history-content"> <div> <div class="section-sub">Выберите день, чтобы увидеть детали и добавить заметку.</div> <div class="history-list">${list}</div> </div> ${detail} </div> </section>`;
        };
        Components.renderHomeView = (s) => {
          const ls = s.lifeScore;
          const lsText = ls != null ? ls.toFixed(1) : "—";
          const sev = scoreSeverity(ls);
          const norm = ls != null ? Math.max(0, Math.min(1, ls / 5)) : 0;
          const attention = renderAttentionCard(s) || "";
          const answers = renderCheckInEcho(s);
          const moodText = lifeMood(ls);
          const indexSubtitle = ls != null ? "Обновлён сегодня" : "Ещё не рассчитан";
          return `<section class="c-card quality-card"> <div class="quality-card-top"> <div class="quality-main-meta"> <div class="c-card-title">Качество вашей жизни</div> <div class="c-card-sub">Психика · Сон · Деньги</div> <div class="quality-state-badge quality-state-badge--${sev.tier}"> ${ls != null ? sev.label : "Пока нет оценки за сегодня"} </div> </div> <div class="quality-score-block"> <div class="life-score-main">${lsText}</div> <div class="life-score-caption">из 5</div> <div class="life-score-pill"> <span>Индекс дня</span><span>·</span> <span>${indexSubtitle}</span> </div> </div> </div> <div class="quality-thermo"> <div class="quality-thermo-track"> <div class="quality-thermo-fill" style="--quality-score:${norm.toFixed(2)};"></div> </div> <div class="quality-thermo-labels"> <span>ниже нормы</span> <span>выше нормы</span> </div> </div> <p class="section-sub quality-description">${moodText}</p> <div class="quality-actions"> <button class="c-button" data-action="open-feature" data-feature="chat"> Диалог с психологом </button> <button class="c-button c-button--secondary" data-action="open-feature" data-feature="family"> Поделиться с семьёй </button> </div> </section> ${answers} ${attention} ${Components.renderLifeLine(s)} <section class="c-card" style="margin-top:16px;"> <div class="section-title">Три направления</div> <div class="section-sub"> Сфокусируйтесь на том, что болит сильнее всего. Остальное подтянем постепенно. </div> <div class="feature-grid"> <div class="feature-card" data-action="open-feature" data-feature="chat"> <div class="feature-card-title">Психологическая помощь</div> <div class="feature-card-pill">Чат ИИ + подключение психолога</div> <div class="feature-card-footer"> <span>Тревога, выгорание, отношения</span><span>💬</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="sleep"> <div class="feature-card-title">Сон</div> <div class="feature-card-pill">План на сегодняшнюю ночь</div> <div class="feature-card-footer"> <span>Режим и ритуалы</span><span>🌙</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="finance"> <div class="feature-card-title">Финансы</div> <div class="feature-card-pill">Бюджет + подушка</div> <div class="feature-card-footer"> <span>Доход · Расходы</span><span>💰</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="family"> <div class="feature-card-title">Семья</div> <div class="feature-card-pill">Совместные шаги</div> <div class="feature-card-footer"> <span>Поделиться прогрессом</span><span>👪</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="game"> <div class="feature-card-title">Игра для пары</div> <div class="feature-card-pill">Карточки на 40 вопросов</div> <div class="feature-card-footer"> <span>Темы, ответы, синхрон</span><span>🎮</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="profile"> <div class="feature-card-title">Мой профиль</div> <div class="feature-card-pill">Подписка и прогресс</div> <div class="feature-card-footer"> <span>Настройки</span><span>⚙️</span> </div> </div> </div> </section>`;
        };
        Components.renderMenuView = (s) => {
          const u = s.usageCounters || { psychologyDays: 0, sleepDays: 0, financeMonths: 0 };
          const hero = `<div class="menu-hero"> <div class="menu-hero-title">Главные модули</div> <div class="menu-hero-sub">Выбирайте то, что нужно сейчас: поддержка, сон, деньги, совместные игры и семейный кабинет.</div> <div class="menu-hero-row"> <span class="chip">Психолог</span> <span class="chip">Сон</span> <span class="chip">Финансы</span> <span class="chip">Семья</span> <span class="chip">Игра</span> </div> </div>`;
          return `<section class="c-card"> ${hero} <div class="section-title">Модули</div> <div class="section-sub">Каждый модуль — отдельный экран с понятными шагами и обратной стрелкой.</div> <div class="feature-grid"> <div class="feature-card" data-action="open-feature" data-feature="chat"> <div class="feature-card-title">Психологическая помощь</div> <div class="feature-card-pill">Регулярные сессии в чате</div> <div class="feature-card-footer"> <span>Эмоции, конфликты</span><span>💬</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="sleep"> <div class="feature-card-title">Сон</div> <div class="feature-card-pill">План на ночь + ритуал</div> <div class="feature-card-footer"> <span>Ритм, тишина, шум</span><span>🌙</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="finance"> <div class="feature-card-title">Финансы</div> <div class="feature-card-pill">Категории и подушка</div> <div class="feature-card-footer"> <span>Баланс доход/расход</span><span>💰</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="family"> <div class="feature-card-title">Семья</div> <div class="feature-card-pill">Общий прогресс</div> <div class="feature-card-footer"> <span>Совместные цели</span><span>👪</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="game"> <div class="feature-card-title">Игра для пары</div> <div class="feature-card-pill">10 тем · 40 вопросов</div> <div class="feature-card-footer"> <span>Выбор тем, ответы</span><span>🎮</span> </div> </div> <div class="feature-card" data-action="open-feature" data-feature="profile"> <div class="feature-card-title">Мой профиль</div> <div class="feature-card-pill">Подписка и прогресс</div> <div class="feature-card-footer"> <span>Настройки</span><span>⚙️</span> </div> </div> </div> <div class="section-title" style="margin-top:14px;">Статистика использования</div> <div class="chips-row"> <span class="chip">Психологическая помощь · ${u.psychologyDays} дн.</span> <span class="chip">Сон · ${u.sleepDays} дн.</span> <span class="chip">Финансы · ${u.financeMonths} мес.</span> </div> </section>`;
        };
        Components.renderProfileView = (s) => {
          const sub =
            s.subscription === "pro"
              ? "PRO · полный доступ ко всем модулям"
              : s.subscription === "standard"
              ? "STANDARD · только психологическая помощь"
              : "Нет активной подписки";
          const u = s.usageCounters || { psychologyDays: 0, sleepDays: 0, financeMonths: 0 };
          const nextThemeLabel = s.theme === "dark" ? "Включить светлую тему" : "Включить тёмную тему";
          return `<section class="c-card"> ${renderBackRow()} <div class="c-card-header"> <div> <div class="c-card-title">Мой профиль</div> <div class="c-card-sub">${s.user.name || "Гость"}</div> </div> <span class="c-badge">ID: ${s.user.id || "—"}</span> </div> <div class="section-title">Подписка</div> <p class="section-sub">${sub}</p> <div class="chips-row"> <span class="chip chip--locator">Standard — 799 ₽ · психолог</span> <span class="chip chip--locator">PRO — 1399 ₽ · всё включено</span> </div> <button class="c-button" data-action="open-subscription" style="margin-top:12px;"> Управлять подпиской </button> <button class="c-button c-button--secondary" data-action="toggle-theme" style="margin-top:10px;"> ${nextThemeLabel} </button> <div class="section-title" style="margin-top:18px;">Использование сервисов</div> <div class="section-sub"> Статистика покажет, насколько стабильно вы работаете с собой. </div> <div class="chips-row"> <span class="chip">Психологическая помощь · ${u.psychologyDays} дн.</span> <span class="chip">Сон · ${u.sleepDays} дн.</span> <span class="chip">Финансы · ${u.financeMonths} мес.</span> </div> </section>`;
        };
        Components.renderChatView = (s) => {
          const chat = s.chat || { messages: [], isTyping: false };
          const navRow = renderBackRow();
          const msgs = (chat.messages || [])
            .map((m) => {
              const cls = "chat-message " + (m.sender === "user" ? "chat-message--user" : "chat-message--bot");
              const meta = m.sender === "bot" && m.author ? `<div class="chat-meta">${m.author} · психолог</div>` : "";
              return `<div>${meta}<div class="${cls}">${m.text}</div></div>`;
            })
            .join("");
          const typing = chat.isTyping
            ? `<div class="chat-message chat-message--bot"> <span class="typing-indicator"> <span class="typing-dot"></span> <span class="typing-dot"></span> <span class="typing-dot"></span> </span> </div>`
            : "";
          const quick = [
            { title: "Сжать тревогу", text: "Опиши три конкретных ситуации, где тревога сильнее всего." },
            { title: "Разобрать конфликт", text: "Дай контекст, что сказал собеседник и как ты отреагировал." },
            { title: "План на день", text: "Что минимально нужно сделать сегодня, чтобы стало легче?" },
          ]
            .map((q) => `<div class="chat-quick-card"><div class="chat-quick-title">${q.title}</div><div>${q.text}</div></div>`)
            .join("");
          const hero = `<div class="chat-hero"> <div> <div class="chat-hero-title">Поддержка в один тап</div> <div class="chat-hero-sub">Пишите большими блоками текста — чат аккуратно разложит мысли, выделит триггеры и предложит шаги.</div> </div> <div class="chat-hero-side"> <span class="chat-pill">Онлайн психолог ${chat.psychologistName || "ADVICE"}</span> <span class="chat-pill">Сохраняем переписку для прогресса</span> </div> </div>`;
          return `<section class="c-card"> ${navRow} <div class="c-card-header"> <div> <div class="c-card-title">Чат с психологом</div> <div class="c-card-sub"> ИИ-психолог с возможностью подключения живого специалиста. </div> </div> <span class="c-badge">Конфиденциально</span> </div> ${hero} <div class="chat-quick-grid">${quick}</div> <div class="chat-window" id="chat-window"> ${msgs || '<div class="section-sub">Опишите пару предложений о том, что сейчас больше всего давит или тревожит.</div>'} ${typing} </div> <div class="row row--stack-m"> <input class="c-field" placeholder="Напишите сообщение..." data-role="chat-input" /> <button class="c-button" data-action="chat-send">Отправить</button> </div> </section>`;
        };
        Components.renderSleepView = (s) => {
          const plan = s.sleep && s.sleep.lastPlan;
          const hasPlan = !!plan;
          const navRow = renderBackRow();
          const hero = hasPlan
            ? `<div class="sleep-hero"> <div> <div class="sleep-hero-label">Ночной режим</div> <div class="sleep-hero-main">${plan.goToBed} → ${plan.wakeTime}</div> <div class="sleep-hero-sub">${plan.durationHours} ч сна · ${plan.chronotypeLabel}</div> </div> <div class="sleep-hero-meta"> <div class="pill">Ритуал с ${plan.windDownStart}</div> <div class="pill pill-ghost">${plan.audioChoice}</div> </div> </div>`
            : `<div class="sleep-hero sleep-hero--empty"> <div> <div class="sleep-hero-label">Ночной режим</div> <div class="sleep-hero-main">Соберём идеальный отбой</div> <div class="sleep-hero-sub">Укажи подъём и предпочтения — настроим ритуал</div> </div> <div class="sleep-hero-meta"> <div class="pill">7,5 ч сна</div> <div class="pill pill-ghost">Тишина или белый шум</div> </div> </div>`;
          const controls = `<div class="sleep-panel"> <div class="section-title">Параметры сегодня</div> <div class="section-sub">Эти ответы дают персональный план, который можно повторять.</div> <div class="chips-row"> <button class="c-button c-button--secondary" data-action="sleep-set" data-key="sleepWith" data-value="alone">Я сплю один</button> <button class="c-button c-button--secondary" data-action="sleep-set" data-key="sleepWith" data-value="not-alone">Сплю с кем-то</button> </div> <div class="section-title" style="margin-top:14px;">Готовность вкладываться</div> <div class="section-sub">Можно строить бюджетный или продвинутый сценарий.</div> <div class="chips-row"> <button class="c-button c-button--secondary" data-action="sleep-set" data-key="budgetLevel" data-value="free">Только бесплатно</button> <button class="c-button c-button--secondary" data-action="sleep-set" data-key="budgetLevel" data-value="paid">Готов вкладываться</button> </div> <div class="section-title" style="margin-top:14px;">Время подъёма</div> <input class="c-field" type="time" value="${(s.sleep.lastInputs && s.sleep.lastInputs.wakeTime) || "07:00"}" data-role="sleep-wake-time" /> <div class="section-title" style="margin-top:14px;">Что слушать перед сном?</div> <select class="c-field" data-role="sleep-noise"> <option value="silence">Тишина</option> <option value="white">Белый шум</option> <option value="water">Журчание водопада</option> <option value="melody">Спокойная мелодия</option> </select> <button class="c-button" data-action="sleep-build-plan" style="margin-top:14px;"> Построить план на ночь </button> </div>`;
          const timeline = plan
            ? `<div class="sleep-panel"> <div class="section-title">Лестница к отбою</div> <div class="sleep-timeline"> ${plan.timeline
                .map((step) => `<div class="sleep-timeline-row"><div class="sleep-timeline-time">${step.label}</div><div class="sleep-timeline-text">${step.text}</div></div>`)
                .join("")} </div> <div class="section-title" style="margin-top:14px;">Среда для глубокого сна</div> <ul class="sleep-list"> ${plan.environmentChecklist
                .map((item) => `<li>${item}</li>`)
                .join("")} </ul> <div class="section-title" style="margin-top:12px;">Если нужно снять стресс</div> <div class="sleep-habits"> ${plan.microHabits
                .map((h) => `<span class="sleep-habit-pill">${h}</span>`)
                .join("")} </div> </div>`
            : `<div class="sleep-panel"> <div class="section-title">Лестница к отбою</div> <div class="section-sub">Заполните параметры — увидите таймлайн и чек-листы.</div> <div class="sleep-placeholder"></div> </div>`;
          const summary = plan
            ? `<div class="sleep-panel"> <div class="section-title">План на ночь</div> <p class="section-sub" style="margin:0;">Ложимся около <b>${plan.goToBed}</b>, подъем в <b>${plan.wakeTime}</b> — ${plan.durationHours} ч сна.</p> <p class="section-sub" style="margin:0;">${plan.envTip}</p> <p class="section-sub" style="margin:0;">${plan.moneyTip}</p> <p class="section-sub" style="margin:0;">Перед сном включите: <b>${plan.audioChoice}</b>.</p> </div>`
            : "";
          return `<section class="c-card"> ${navRow} <div class="c-card-header"> <div> <div class="c-card-title">Сон</div> <div class="c-card-sub">Быстрый план на ночь с ритуалом и средой</div> </div> <span class="c-badge">Сегодня</span> </div> ${hero} <div class="sleep-grid"> ${controls} ${timeline} ${summary} <div class="sleep-panel"> <div class="section-title">Чек-лист перед сном</div> <div class="section-sub">Повесьте этот чек-лист на прикроватную тумбу.</div> <div class="sleep-checklist"> <label><input type="checkbox" /> Убрать яркий экран и уведомления за 30 минут.</label> <label><input type="checkbox" /> Сделать комнату темнее и прохладнее.</label> <label><input type="checkbox" /> Лёгкая растяжка или тёплый душ, чтобы снять напряжение.</label> <label><input type="checkbox" /> Записать мысли и задачи на завтра, чтобы успокоить голову.</label> </div> </div> </div> </section>`;
        };
        Components.renderFinanceView = (s) => {
          const plan = s.finance && s.finance.plan;
          const safety = s.finance && s.finance.safetyFund;
          const progress = safety && safety.progress ? Math.min(1, Math.max(0, safety.progress)) : 0;
          const navRow = renderBackRow();
          const catList = [
            { key: "housing", label: "Жильё / аренда", placeholder: "20000" },
            { key: "utilities", label: "ЖКХ / связь", placeholder: "5000" },
            { key: "food", label: "Еда и дом", placeholder: "12000" },
            { key: "transport", label: "Транспорт", placeholder: "3000" },
            { key: "debts", label: "Долги / кредиты", placeholder: "4000" },
            { key: "leisure", label: "Развлечения", placeholder: "3000" },
            { key: "other", label: "Прочее", placeholder: "2000" },
          ];
          const heroIncome = plan && plan.income ? `${plan.income.toLocaleString("ru-RU")} ₽/мес` : "Укажите доход";
          const heroExpense = plan ? `${plan.totalExpenses.toLocaleString("ru-RU")} ₽ расходов` : "Траты не указаны";
          const gapBadge = plan
            ? `<span class="finance-gap-badge ${plan.overspend ? "finance-gap-badge--bad" : "finance-gap-badge--good"}"> ${
                plan.overspend ? "Минус в бюджете" : "Запас есть"
              } · ${plan.gap.toLocaleString("ru-RU")} ₽ </span>`
            : "";
          const hero = `<div class="finance-hero">
            <div>
              <div class="finance-hero-label">Баланс месяца</div>
              <div class="finance-hero-main">${heroIncome}</div>
              <div class="finance-hero-sub">${heroExpense}</div>
              <div class="finance-hero-gap">${gapBadge} <span class="pill pill-ghost">${plan ? Math.round((plan.savingsRate || 0) * 100) : 0}% → сбережения</span></div>
            </div>
            <div class="finance-hero-meta">
              <div class="pill">Соберите категории — покажем, где резать траты</div>
              <div class="pill pill-ghost">Подписка PRO окупается за счёт оптимизации</div>
            </div>
          </div>`;
          const categoryInputs = `<div class="finance-cat-grid">
            ${catList
              .map((cat) => {
                const val = plan && plan.categories ? plan.categories[cat.key] : "";
                return `<label class="finance-cat-row"> <span class="finance-cat-label">${cat.label}</span> <input class="c-field finance-cat-input" data-role="finance-category" data-category="${cat.key}" type="number" min="0" step="500" placeholder="${cat.placeholder}" value="${val || ""}" /> </label>`;
              })
              .join("")}
          </div>`;
          const bucketCards = plan
            ? `<div class="finance-plan-grid">
                ${plan.buckets
                  .map((b) => {
                    const width = plan.income ? Math.min(100, Math.round((b.amount / plan.income) * 100)) : 0;
                    return `<div class="finance-bucket">
                        <div class="finance-bucket-top">
                          <div class="finance-bucket-label">${b.label}</div>
                          <div class="finance-bucket-amount">${b.amount.toLocaleString("ru-RU")} ₽</div>
                        </div>
                        <div class="finance-alloc-bar"><span style="width:${width}%"></span></div>
                        <div class="finance-bucket-desc">${b.description}</div>
                      </div>`;
                  })
                  .join("")}
                <div class="finance-tip">${plan.comment}</div>
              </div>`
            : `<div class="finance-placeholder">Заполните доход и категории — разложим бюджет и покажем точки экономии.</div>`;
          const miniStats = plan
            ? `<div class="finance-mini-grid">
                <div class="finance-mini-card">
                  <div class="finance-mini-title">Сбережения</div>
                  <div class="finance-mini-value">${Math.round((plan.savingsRate || 0) * 100)}%</div>
                  <div class="finance-chip-row"><span class="finance-chip">Цель 10–20%</span></div>
                </div>
                <div class="finance-mini-card">
                  <div class="finance-mini-title">База (жильё+еда)</div>
                  <div class="finance-mini-value">${Math.round((plan.essentialsRate || 0) * 100)}%</div>
                  <div class="finance-chip-row"><span class="finance-chip">Норма до 65%</span></div>
                </div>
                <div class="finance-mini-card">
                  <div class="finance-mini-title">Образ жизни</div>
                  <div class="finance-mini-value">${Math.round((plan.lifestyleRate || 0) * 100)}%</div>
                  <div class="finance-chip-row"><span class="finance-chip">Подписки, развлечения</span></div>
                </div>
              </div>`
            : "";
          const recommendations = plan && plan.recommendations.length
            ? `<div class="finance-reco">${plan.recommendations
                .map(
                  (rec) => `<div class="finance-reco-item">
                    <div class="finance-reco-lead">${rec.text}</div>
                    <div class="finance-reco-tips">${(rec.tips || []).map((t) => `<span>• ${t}</span>`).join("")}</div>
                  </div>`
                )
                .join("")}</div>`
            : `<p class="finance-note">После расчёта появятся советы по каждой категории — жильё, еда, транспорт, ЖКХ и т.д.</p>`;
          const safetyBlock = safety
            ? `<div class="safety-result">
                <div class="c-card-title" style="margin-bottom:6px;">Подушка безопасности</div>
                <p class="section-sub" style="margin:0;">Цель: <b>${safety.target.toLocaleString("ru-RU")} ₽</b> · ${safety.targetMonths} мес. расходов.</p>
                <div class="safety-progress"><div class="safety-progress-fill" style="transform:scaleX(${progress.toFixed(2)});"></div></div>
                <p class="section-sub" style="margin:0;">${Math.round(progress * 100)}% цели · ${safety.status}</p>
              </div>`
            : `<p class="finance-note">Заполните расходы и накопления — покажем сумму подушки и срок, за который её можно закрыть.</p>`;
          const weeklyActions = `<ul class="finance-actions">
            <li>Фиксируйте траты по категориям раз в неделю, чтобы не уползали в минус.</li>
            <li>Отключите лишние подписки и пересмотрите тарифы связи/интернета.</li>
            <li>Замените будничные такси на проездной и пешие участки.</li>
            <li>Сразу после зарплаты отправляйте перевод в подушку или на долг.</li>
          </ul>`;
          return `<section class="c-card"> ${navRow}
            <div class="c-card-header">
              <div>
                <div class="c-card-title">Финансы</div>
                <div class="c-card-sub">Компактный бюджет по категориям + готовые советы</div>
              </div>
              <span class="c-badge">Месяц</span>
            </div>
            ${hero}
            <div class="finance-grid">
              <div class="finance-panel finance-stack">
                <div>
                  <div class="section-title" style="margin-top:4px;">Доход и категории</div>
                  <div class="section-sub">Укажите доход и месячные траты по блокам — покажем дефицит и где экономить.</div>
                  <div class="finance-compact-form">
                    <input class="c-field" type="number" min="0" step="1000" data-role="finance-income" placeholder="Например, 50000" value="${s.finance.income || ""}" />
                    ${categoryInputs}
                    <button class="c-button" data-action="finance-build-plan" style="margin-top:6px;"> Посчитать баланс и советы </button>
                  </div>
                </div>
                ${miniStats}
                ${bucketCards}
              </div>
              <div class="finance-panel finance-stack">
                <div>
                  <div class="section-title" style="margin-top:4px;">Советы по сокращению</div>
                  <div class="section-sub">Даем подсказки, если траты по жилью, еде или транспорту выбиваются из нормы.</div>
                  ${recommendations}
                </div>
                <div>
                  <div class="section-title" style="margin-top:12px;">Подушка безопасности</div>
                  <div class="section-sub">Рассчитаем нужную сумму и срок накопления.</div>
                  <input class="c-field" type="number" min="0" step="500" data-role="finance-safety-expenses" placeholder="Расходы в месяц, ₽" />
                  <input class="c-field" type="number" min="0" step="500" data-role="finance-safety-current" placeholder="Уже отложено, ₽" style="margin-top:8px;" />
                  <input class="c-field" type="number" min="0" step="500" data-role="finance-safety-monthly" placeholder="Готовы откладывать в месяц, ₽" style="margin-top:8px;" />
                  <select class="c-field" data-role="finance-safety-months" style="margin-top:8px;">
                    <option value="3">Цель: 3 месяца подушки</option>
                    <option value="6">Цель: 6 месяцев подушки</option>
                    <option value="9">Цель: 9 месяцев подушки</option>
                    <option value="12">Цель: 12 месяцев подушки</option>
                  </select>
                  <button class="c-button c-button--secondary" data-action="finance-calc-safety" style="margin-top:12px;"> Посчитать подушку </button>
                  ${safetyBlock}
                </div>
                <div>
                  <div class="section-title" style="margin-top:10px;">Действия на неделю</div>
                  ${weeklyActions}
                </div>
              </div>
            </div>
          </section>`;
        };
        Components.renderFamilyView = (s) => {
          const ls = s.lifeScore != null ? s.lifeScore.toFixed(1) : "—";
          const historyCount = (s.scoresHistory || []).length;
          const lastReasons = s.lastCheckInReasons || {};
          const shareChips = Object.keys(lastReasons)
            .map((k) => (lastReasons[k] && lastReasons[k].length ? lastReasons[k].slice(0, 2) : []))
            .flat()
            .slice(0, 4)
            .map((r) => `<span class="family-pill">${r}</span>`)
            .join("") || `<span class="family-pill">Добавьте причины в чек-ин, чтобы делиться ими</span>`;
          const hero = `<div class="family-hero"> <div> <div class="family-hero-title">Семья и поддержка</div> <div class="family-hero-sub">Делитесь индексом и причинами с близкими — договоритесь о шагах, которые реально помогают.</div> <div class="family-meta"> <span class="pill">Индекс: ${ls} / 5</span> <span class="pill pill-ghost">Чек-инов: ${historyCount}</span> </div> </div> <div class="family-hero-side"> <button class="c-button">Скопировать ссылку на прогресс</button> <button class="c-button c-button--secondary" data-action="open-feature" data-feature="game">Открыть игру</button> <button class="c-button c-button--secondary" data-action="open-feature" data-feature="chat">Позвать психолога</button> </div> </div>`;
          const cards = `<div class="family-card-grid"> <div class="family-card"> <h4>Совместные цели</h4> <div class="section-sub">Договоритесь о коротких шагах и закрепите ответственность.</div> <div class="family-progress"> <span>Сон: ${s.sleep && s.sleep.lastPlan ? "План обновлён" : "Нужен план"}</span> <span>Финансы: ${s.finance && s.finance.plan ? "Бюджет готов" : "Добавьте категории"}</span> </div> <div class="chips-row"> <span class="chip">30 минут без экрана перед сном</span> <span class="chip">Еженедельный разбор бюджета</span> <span class="chip">Обсудить границы отдыха</span> </div> </div> <div class="family-card"> <h4>Что показать</h4> <div class="section-sub">Коротко отправьте индекс и причины — добавьте заметку о нужной поддержке.</div> <div class="family-meta">${shareChips}</div> <div class="section-sub" style="margin-top:6px;">Добавьте заметку о том, какая поддержка вам нужна сегодня.</div> </div> </div>`;
          return `<section class="c-card"> ${renderBackRow()} <div class="c-card-header"> <div> <div class="c-card-title">Семья</div> <div class="c-card-sub">Делиться прогрессом и договариваться о совместных шагах</div> </div> <span class="c-badge">Поддержка</span> </div> ${hero} ${cards} </section>`;
        };
        Components.renderGameView = (s) => {
          const navRow = renderBackRow();
          const topics = Services.getGameTopics();
          const activeKey = (s.game && s.game.activeTopic) || (topics[0] && topics[0].key) || null;
          const activeTopic = topics.find((t) => t.key === activeKey) || topics[0] || null;
          const answers = (s.game && s.game.answers && s.game.answers[activeKey]) || [];
          const questionIndex = s.game && typeof s.game.questionIndex === "number" ? s.game.questionIndex : 0;
          const total = activeTopic ? activeTopic.questions.length : 0;
          const safeIndex = total ? Math.min(Math.max(0, questionIndex), total - 1) : 0;
          const question = activeTopic ? activeTopic.questions[safeIndex] : "Выберите тему, чтобы начать";
          const topicCards = topics
            .map((t) => {
              const active = t.key === activeKey;
              return `<button class="game-topic-card ${active ? "game-topic-card--active" : ""}" data-action="game-select-topic" data-topic="${t.key}" style="border-color:${active ? t.accent : "var(--color-border-subtle)"};"> <div class="game-topic-title">${t.title}</div> <div class="game-topic-pill" style="color:${t.accent};background:rgba(255,255,255,0.7);">${t.questions.length} вопросов</div> <div class="game-topic-tagline">${t.tagline || "Осознанный разговор"}</div> </button>`;
            })
            .join("");
          const history = answers.length
            ? `<div class="game-history">${answers
                .slice(-4)
                .reverse()
                .map(
                  (a) => `<div class="game-history-card"> <div class="section-sub" style="margin:0 0 6px;">${a.question}</div> <div class="c-card-title" style="margin:0;">${a.text || "Без ответа"}</div> </div>`
                )
                .join("")}</div>`
            : `<p class="section-sub">Отвечайте на вопросы — ответы останутся здесь для пары.</p>`;
          const hero = `<div class="game-hero"> <div> <div class="game-hero-title">Игра для пары</div> <div class="game-hero-sub">Выбирайте тему, отвечайте в своём темпе и двигайтесь вперёд осознанно. Карточки синхронны для обоих.</div> <div class="chips-row" style="margin-top:8px;"> <span class="chip">${topics.length} тем</span> <span class="chip">${total || 40} вопросов</span> <span class="chip">Ответы сохраняются</span> </div> </div> <div class="game-hero-steps"> <div class="game-hero-step">1. Выберите тему</div> <div class="game-hero-step">2. Пишите ответы вдвоём</div> <div class="game-hero-step">3. Жмите «Следующий» для новой карты</div> </div> </div>`;
          const controls = `<div class="game-controls"> <button class="c-button c-button--secondary" data-action="game-prev-question" data-topic="${activeKey}" ${safeIndex === 0 ? "disabled" : ""}>◀ Предыдущий</button> <button class="c-button" data-action="game-next-question" data-topic="${activeKey}">Следующий ▶</button> </div>`;
          const helper = `<div class="game-helper"> <div class="section-sub">Темы можно листать свайпом. После ответа нажмите «Следующий», чтобы карта изменилась у обоих.</div> <div class="game-helper-chips"> <span class="chip">Совместная игра</span> <span class="chip">Ответы сохраняются</span> <span class="chip">Можно делиться в «Семье»</span> </div> </div>`;
          return `<section class="c-card"> ${navRow} <div class="c-card-header"> <div> <div class="c-card-title">Игра</div> <div class="c-card-sub">Карточки для пар — выбирайте тему и отвечайте вместе</div> </div> <span class="c-badge">Совместно</span> </div> ${hero} <div class="section-title" style="margin-top:14px;">Темы</div> <div class="game-topic-strip">${topicCards}</div> ${helper} <div class="game-question-card" style="border-color:${activeTopic ? activeTopic.accent : "transparent"};"> <div class="game-question-top"> <div> <div class="game-question-title">${activeTopic ? activeTopic.title : "Тема"}</div> <div class="game-question-meta"> <span>Вопрос ${safeIndex + 1} из ${total || 1}</span> <span style="color:${activeTopic ? activeTopic.accent : "#6366f1"};">${activeTopic ? activeTopic.tagline : "Выберите тему"}</span> </div> </div> </div> <div class="game-question-body">${question}</div> ${controls} <div class="game-answer-row"> <textarea class="game-answer-input" data-role="game-answer" data-topic="${activeKey}" placeholder="Напишите свой ответ — он увидит его в семье/чате игры"></textarea> <div class="row row--stack-m"> <button class="c-button" data-action="game-send-answer" data-topic="${activeKey}">Отправить ответ</button> <button class="c-button c-button--secondary" data-action="nav" data-view="family">Поделиться в семье</button> </div> </div> </div> <div class="section-title" style="margin-top:18px;">Последние ответы</div> ${history} </section>`;
        };
        return { Components };
      })();
    })();
  </script>
  <!-- FEATURES / INTRO / HANDLERS -->
  <script>
    (function () {
      "use strict";
      const AdviceApp = window.AdviceApp;
      const State = AdviceApp.State;
      const Services = AdviceApp.Services;
      const UI = AdviceApp.UI;
      const Bus = AdviceApp.EventBus;
      const Core = AdviceApp.Core;
      AdviceApp.Features = (function () {
        const INTRO_SCREEN_DURATION = 1800;
        const QUESTIONS = [
          { key: "mind", label: "Как вы себя чувствуете в психологическом плане?" },
          { key: "sleep", label: "Как прошёл ваш сон?" },
          { key: "money", label: "Как у вас с финансами сегодня?" },
        ];
        const INTRO_DIALOG_MESSAGES = [
          { sender: "bot", label: "ADVICE", text: "Сигнал принят. Сохранили индекс дня и ответы по психике, сну и финансам." },
          { sender: "bot", label: "ADVICE", text: "Записали причины просадки, чтобы вернуться к ним в рекомендациях." },
          { sender: "user", label: "Вы", text: "Окей, открывайте главную." },
        ];
        const ATTENTION_REASON_LIMIT = 3;
        const ATTENTION_LIBRARY = {
          mind: {
            1: [
              "Панические атаки возвращаются",
              "Не могу встать с кровати утром",
              "Сильные конфликты с близкими",
              "Каждый день кажется безнадёжным",
              "Накатывает чувство пустоты",
              "Боюсь выходить из дома",
              "Рабочая нагрузка ломает",
              "Часто плачу без причин",
              "Нет ни одной опоры",
              "Тело реагирует болями на стресс",
            ],
            2: [
              "Много тревоги или паники",
              "Конфликты с близкими",
              "Постоянная усталость и апатия",
              "Нет ощущения смысла",
              "Тревога за здоровье",
              "Рабочие дедлайны поджимают",
              "Слишком много новостей",
              "Нет поддержки",
              "Не могу расслабиться",
              "Всё раздражает",
            ],
            3: [
              "Не могу сфокусироваться",
              "Сложно принять решения",
              "Перепады настроения",
              "Сомневаюсь в себе",
              "Нет времени на себя",
              "Боюсь будущего",
              "Мало радости",
              "Откладываю важное",
              "Слишком много общения",
              "Неясные отношения",
            ],
          },
          sleep: {
            1: [
              "Почти не сплю несколько ночей",
              "Засыпаю только к рассвету",
              "Просыпаюсь каждые 30 минут",
              "Снятся тяжёлые кошмары",
              "Ложусь спать ближе к утру",
              "Шум вокруг не даёт уснуть",
              "В комнате душно и жарко",
              "Телефон постоянно звенит",
              "Сплю по 3–4 часа максимум",
              "Просыпаюсь в панике",
            ],
            2: [
              "Просыпаюсь среди ночи",
              "Засыпаю по несколько часов",
              "Сплю рывками",
              "Слишком шумно вокруг",
              "Нет ритуала перед сном",
              "Смотрю в экран до последнего",
              "Поздно ем",
              "Пью кофе вечером",
              "Смена графиков",
              "Кошмары мешают",
            ],
            3: [
              "Чуть меньше сна чем нужно",
              "Нерегулярный подъём",
              "Переношу дела на ночь",
              "Пью много воды перед сном",
              "Нет физической активности",
              "Думаю о работе в постели",
              "Гаджеты рядом",
              "Неудобный матрас",
              "Жара или духота",
              "Слишком светло",
            ],
          },
          money: {
            1: [
              "Дохода не хватает на базовые нужды",
              "Есть просроченные платежи",
              "Регулярно беру микрозаймы",
              "Не получается закрыть кредиты",
              "Нечем платить за жильё",
              "Откладываю оплату счетов",
              "Семья зависит от одного дохода",
              "Каждый месяц ухожу в минус",
              "Пугают звонки от банков",
              "Нет финансовой подушки вовсе",
            ],
            2: [
              "Подушка меньше одного месяца",
              "Долги или кредиты давят",
              "Доход нестабильный",
              "Нужно помогать семье",
              "Не могу закрыть базовые траты",
              "Не знаю, куда уходят деньги",
              "Большие обязательные платежи",
              "Не хватает на лечение или здоровье",
              "Случайные непредвиденные расходы",
              "Постоянно беру взаймы",
            ],
            3: [
              "Хочу копить, но не получается",
              "Путаюсь в подписках",
              "Слишком много импульсивных покупок",
              "Нет понятного бюджета",
              "Не понимаю, как расти в доходе",
              "Платежи по подпискам давят",
              "Периодические большие траты",
              "Нет учёта расходов",
              "Боюсь потерять работу",
              "Отложил крупную цель",
            ],
          },
        };
        const checkinStars = { mind: 0, sleep: 0, money: 0 };
        const attentionSelections = { mind: { score: null, reasons: [] }, sleep: { score: null, reasons: [] }, money: { score: null, reasons: [] } };
        const sleepInputs = { sleepWith: null, budgetLevel: null, wakeTime: "07:00", noisePreference: "silence" };
        let introRoot = null;
        let introTimer = null;
        const KNOWN_VIEWS = ["home", "menu", "profile", "chat", "sleep", "finance", "family", "history", "game"];
        let navStack = [];
        function applyTheme(theme) {
          const body = document.body;
          if (!body) return;
          const dark = theme === "dark";
          body.classList.toggle("theme-dark", dark);
          const metaTheme = document.querySelector('meta[name="theme-color"]');
          if (metaTheme) metaTheme.setAttribute("content", dark ? "#0f1114" : "#000000");
        }
        function clearIntroTimer() {
          if (introTimer) {
            clearTimeout(introTimer);
            introTimer = null;
          }
        }
        function syncHeaderNav() {
          const s = State.getState();
          const header = document.getElementById("app-header");
          const nav = document.getElementById("bottom-nav");
          if (header) header.innerHTML = UI.Components.renderHeader(s);
          if (nav) nav.innerHTML = UI.Components.renderBottomNav(s);
        }
        function renderMain() {
          const s = State.getState();
          const main = document.getElementById("app-main");
          if (!main) return;
          let html = "";
          switch (s.currentView) {
            case "home":
              html = UI.Components.renderHomeView(s);
              break;
            case "menu":
              html = UI.Components.renderMenuView(s);
              break;
            case "profile":
              html = UI.Components.renderProfileView(s);
              break;
            case "chat":
              html = UI.Components.renderChatView(s);
              break;
            case "sleep":
              html = UI.Components.renderSleepView(s);
              break;
            case "finance":
              html = UI.Components.renderFinanceView(s);
              break;
            case "family":
              html = UI.Components.renderFamilyView(s);
              break;
            case "game":
              html = UI.Components.renderGameView(s);
              break;
            case "history":
              html = UI.Components.renderHistoryView(s);
              break;
            default:
              html = UI.Components.renderHomeView(s);
          }
          main.innerHTML = html;
          if (s.currentView === "chat") {
            const w = document.getElementById("chat-window");
            if (w) w.scrollTop = w.scrollHeight;
          }
        }
        function safeView(view) {
          if (KNOWN_VIEWS.includes(view)) return view;
          return "home";
        }
        function navigate(view, opts = {}) {
          const target = safeView(view);
          const current = State.getState().currentView;
          if (opts.resetStack) navStack = [];
          if (target === current) return;
          if (!opts.resetStack) {
            navStack.push(current);
          }
          State.setState({ currentView: target });
        }
        function goBack() {
          if (navStack.length) {
            const prev = navStack.pop();
            State.setState({ currentView: prev || "home" });
            return;
          }
          State.setState({ currentView: "home" });
        }
        function shouldAskReasons(kind, value) {
          return value > 0 && value <= 3 && !!getReasonOptions(kind, value).length;
        }
        function getReasonOptions(kind, value) {
          const map = ATTENTION_LIBRARY[kind] || {};
          return map[value] || [];
        }
        function getQuestionLabel(kind) {
          const found = QUESTIONS.find((q) => q.key === kind);
          return found ? found.label : kind;
        }
        function snapshotAttentionSelections() {
          const snap = {};
          Object.keys(attentionSelections).forEach((key) => {
            const slot = attentionSelections[key] || {};
            snap[key] = { score: slot.score, reasons: (slot.reasons || []).slice(0) };
          });
          return snap;
        }
        /* ---------- INTRO ---------- */
        function showIntroLogo() {
          clearIntroTimer();
          if (!introRoot) return;
          introRoot.classList.remove("intro-water");
          introRoot.innerHTML = `<div class="intro-screen"> <div class="intro-title-main">ADVICE</div> </div>`;
          const logo = introRoot.querySelector(".intro-title-main");
          if (logo) {
            setTimeout(() => logo.classList.add("intro-logo-leave"), INTRO_SCREEN_DURATION - 420);
          }
          introTimer = setTimeout(showIntroHello, INTRO_SCREEN_DURATION);
        }
        function showIntroHello() {
          clearIntroTimer();
          if (!introRoot) return;
          introRoot.classList.remove("intro-water");
          introRoot.innerHTML = `<div class="intro-screen"> <div class="intro-hello">Привет</div> </div>`;
          introTimer = setTimeout(() => showIntroQuestion(0), INTRO_SCREEN_DURATION);
        }
        function renderReasonSelector(kind, value, idx) {
          const screen = introRoot && introRoot.querySelector(`.intro-screen[data-question-index="${idx}"]`);
          if (!screen) return;
          const slot = screen.querySelector(".attention-panel-slot");
          if (!slot) return;
          const options = getReasonOptions(kind, value);
          if (!options.length) return;
          const selected = (attentionSelections[kind] && attentionSelections[kind].reasons) || [];
          const message = value <= 2 ? "Что тянет вниз сильнее всего?" : "Что мешает дотянуться до хорошей оценки?";
          slot.innerHTML = `<div class="attention-panel" data-kind="${kind}"> <div class="attention-panel-title">${getQuestionLabel(kind)}</div> <div class="attention-panel-sub">${message} Выберите до ${ATTENTION_REASON_LIMIT} пунктов.</div> <div class="attention-options"> ${options
            .map(
              (opt, i) =>
                `<button class="attention-option ${selected.includes(opt) ? "attention-option--selected" : ""}" data-action="intro-toggle-reason" data-kind="${kind}" data-index="${i}"> ${opt} </button>`
            )
            .join("")} </div> <button class="c-button c-button--secondary" data-action="intro-confirm-reasons" data-kind="${kind}" data-question-index="${idx}"> Готово · далее </button> </div>`;
          slot.classList.add("attention-panel-slot--visible");
        }
        function hideReasonSelector(idx) {
          const screen = introRoot && introRoot.querySelector(`.intro-screen[data-question-index="${idx}"]`);
          if (!screen) return;
          const slot = screen.querySelector(".attention-panel-slot");
          if (slot) {
            slot.innerHTML = "";
            slot.classList.remove("attention-panel-slot--visible");
          }
        }
        function showIntroQuestion(idx) {
          clearIntroTimer();
          if (!introRoot) return;
          const q = QUESTIONS[idx];
          const selected = checkinStars[q.key];
          introRoot.classList.remove("intro-water");
          introRoot.innerHTML = `<div class="intro-screen" data-question-index="${idx}"> <div class="intro-question-label">${q.label}</div> <div class="intro-stars-row" data-role="intro-stars" data-kind="${q.key}"> ${[1, 2, 3, 4, 5]
            .map(
              (v) =>
                `<button class="intro-star ${selected && v <= selected ? "intro-star--active" : ""}" data-action="intro-set-star" data-kind="${q.key}" data-value="${v}"> ★ </button>`
            )
            .join("")} </div> <div class="attention-panel-slot"></div> <div class="intro-actions"> <button class="c-button c-button--secondary" data-action="intro-next" data-question-index="${idx}" ${selected ? "" : "disabled"}> Далее </button> </div> </div>`;
          if (shouldAskReasons(q.key, selected)) {
            renderReasonSelector(q.key, selected, idx);
          }
        }
          function goToNextQuestion(idx) {
            if (idx < QUESTIONS.length - 1) {
              setTimeout(() => showIntroQuestion(idx + 1), 350);
            } else {
              // Make sure the main shell is visible before rendering the closing dialog.
              revealAppShell();
              showIntroDialog();
            }
          }
          function introNext(idx) {
            const q = QUESTIONS[idx];
            if (!q) return;
            const score = checkinStars[q.key];
            // If the score somehow isn't set on the final step, use a neutral value
            // so the flow can continue instead of freezing on the last question.
            if (!score) {
              if (idx === QUESTIONS.length - 1) {
                checkinStars[q.key] = 3;
              } else {
                return;
              }
            }
            hideReasonSelector(idx);
            goToNextQuestion(idx);
          }
        function introSetStar(kind, value, idx) {
          const val = Number(value);
          checkinStars[kind] = val;
          attentionSelections[kind] = attentionSelections[kind] || { score: null, reasons: [] };
          attentionSelections[kind].score = val;
          const row = document.querySelector(`.intro-stars-row[data-kind="${kind}"]`);
          if (row) {
            row.querySelectorAll(".intro-star").forEach((btn) => {
              const v = Number(btn.dataset.value || 0);
              btn.classList.toggle("intro-star--active", v <= val);
            });
          }
          const nextBtn = document.querySelector(`button[data-action="intro-next"][data-question-index="${idx}"]`);
          if (nextBtn) nextBtn.disabled = !val;
          if (shouldAskReasons(kind, val)) {
            attentionSelections[kind].reasons = attentionSelections[kind].reasons || [];
            renderReasonSelector(kind, val, idx);
            const screen = introRoot && introRoot.querySelector(`.intro-screen[data-question-index="${idx}"]`);
            const slot = screen && screen.querySelector(".attention-panel-slot");
            const hasPanel = slot && slot.classList.contains("attention-panel-slot--visible");
            if (!hasPanel) {
              goToNextQuestion(idx);
            }
          } else {
            attentionSelections[kind].reasons = [];
            hideReasonSelector(idx);
            goToNextQuestion(idx);
          }
        }
        function introToggleReason(kind, optionIndex, button) {
          const score = checkinStars[kind];
          if (!shouldAskReasons(kind, score)) return;
          const options = getReasonOptions(kind, score);
          const choice = options[optionIndex];
          if (!choice) return;
          const slot = attentionSelections[kind] || { score: score, reasons: [] };
          const reasons = slot.reasons ? slot.reasons.slice(0) : [];
          const existing = reasons.indexOf(choice);
          if (existing >= 0) {
            reasons.splice(existing, 1);
          } else {
            if (reasons.length >= ATTENTION_REASON_LIMIT) return;
            reasons.push(choice);
          }
          slot.reasons = reasons;
          attentionSelections[kind] = slot;
          if (button) {
            button.classList.toggle("attention-option--selected", reasons.includes(choice));
          }
        }
        function introConfirmReasons(kind, idx) {
          const slot = attentionSelections[kind] || {};
          if (!slot.score) return;
          hideReasonSelector(idx);
          goToNextQuestion(idx);
        }
        function revealAppShell() {
          const appShell = document.querySelector(".app-shell");
          const bottomNav = document.querySelector(".c-bottom-nav");
          if (appShell) appShell.classList.remove("app-shell--hidden");
          if (bottomNav) bottomNav.classList.remove("app-shell--hidden");
        }
        function showIntroDialog() {
          clearIntroTimer();
          if (!introRoot) return;
          const attentionSnap = snapshotAttentionSelections();
          State.updateSlice("attention", attentionSnap);
          State.applyDailyCheckIn(checkinStars, attentionSnap);
          navStack = [];
          State.setState({ currentView: "home" });
          revealAppShell();
          syncHeaderNav();
          renderMain();
          introRoot.classList.add("intro-water", "intro-overlay");
          introRoot.innerHTML = `<div class="intro-screen"> <div class="intro-dialog"> ${INTRO_DIALOG_MESSAGES.map(
            (msg) => `<div class="intro-dialog-bubble intro-dialog-bubble--${msg.sender}"> <div class="intro-dialog-meta">${msg.label}</div> <div>${msg.text}</div> </div>`
          ).join("")} </div> </div>`;
          requestAnimationFrame(() => {
            const bubbles = introRoot.querySelectorAll(".intro-dialog-bubble");
            bubbles.forEach((bubble, idx) => {
              setTimeout(() => bubble.classList.add("intro-dialog-bubble--visible"), idx * 420 + 140);
            });
          });
          const total = INTRO_DIALOG_MESSAGES.length * 420 + 1600;
          introTimer = setTimeout(finishIntro, total);
        }
        function finishIntro() {
          clearIntroTimer();
          if (!introRoot) return;
          introRoot.classList.add("intro-hidden");
          introRoot.classList.remove("intro-overlay");
          setTimeout(() => {
            introRoot.innerHTML = "";
          }, 350);
        }
        /* ---------- CHAT ---------- */
        function ensurePsychologistName() {
          const s = State.getState();
          if (s.chat.psychologistName) return s.chat.psychologistName;
          const name = Services.randomPsychologistName();
          State.updateSlice("chat", { psychologistName: name });
          return name;
        }
        function sendChat(text) {
          const t = (text || "").trim();
          if (!t) return;
          const s = State.getState();
          const name = ensurePsychologistName();
          const msgs = (s.chat.messages || []).concat([{ id: Core.uid("m"), sender: "user", text: t }]);
          State.updateSlice("chat", { messages: msgs, isTyping: true });
          Services.sendToPsychologyAI(t, { psychologistName: name, userId: s.user.id }).then((ans) => {
            const cur = State.getState();
            const updated = (cur.chat.messages || []).concat([{ id: Core.uid("m"), sender: "bot", text: ans.text, author: ans.psychologistName }]);
            State.updateSlice("chat", { messages: updated, isTyping: false, psychologistName: ans.psychologistName });
          });
        }
        /* ---------- SLEEP & FINANCE ---------- */
        function setSleepParam(key, val) {
          sleepInputs[key] = val;
        }
        function buildSleepPlan() {
          const wake = document.querySelector('[data-role="sleep-wake-time"]');
          const noise = document.querySelector('[data-role="sleep-noise"]');
          if (wake && wake.value) sleepInputs.wakeTime = wake.value;
          if (noise && noise.value) sleepInputs.noisePreference = noise.value;
          const plan = Services.buildSleepPlan(sleepInputs);
          State.updateSlice("sleep", { lastPlan: plan, lastInputs: Core.deepClone(sleepInputs) });
        }
        function buildFinancePlan() {
          const incEl = document.querySelector('[data-role="finance-income"]');
          const catEls = document.querySelectorAll('[data-role="finance-category"]');
          const categories = {};
          catEls.forEach((el) => {
            if (el && el.dataset && el.dataset.category) {
              categories[el.dataset.category] = el.value;
            }
          });
          const plan = Services.buildFinancePlan(incEl ? incEl.value : "", categories);
          State.updateSlice("finance", { income: plan.income, plan });
        }
        function calculateSafetyFund() {
          const expensesEl = document.querySelector('[data-role="finance-safety-expenses"]');
          const savingsEl = document.querySelector('[data-role="finance-safety-current"]');
          const monthlyEl = document.querySelector('[data-role="finance-safety-monthly"]');
          const monthsEl = document.querySelector('[data-role="finance-safety-months"]');
          const fund = Services.buildSafetyFund(
            savingsEl ? savingsEl.value : "",
            expensesEl ? expensesEl.value : "",
            monthsEl ? monthsEl.value : "",
            monthlyEl ? monthlyEl.value : ""
          );
          State.updateSlice("finance", { safetyFund: fund });
        }
        /* ---------- GAME ---------- */
        function getGameTopic(topicKey) {
          const topics = Services.getGameTopics();
          if (!topics.length) return null;
          return topics.find((t) => t.key === topicKey) || topics[0];
        }
        function selectGameTopic(topicKey) {
          const topic = getGameTopic(topicKey);
          if (!topic) return;
          State.updateSlice("game", { activeTopic: topic.key, questionIndex: 0 });
        }
        function nextGameQuestion() {
          const s = State.getState();
          const topic = getGameTopic(s.game && s.game.activeTopic);
          if (!topic) return;
          const max = Math.max(0, (topic.questions || []).length - 1);
          const currentIndex = s.game && typeof s.game.questionIndex === "number" ? s.game.questionIndex : 0;
          const next = Math.min(max, currentIndex + 1);
          State.updateSlice("game", { activeTopic: topic.key, questionIndex: next });
        }
        function prevGameQuestion() {
          const s = State.getState();
          const topic = getGameTopic(s.game && s.game.activeTopic);
          if (!topic) return;
          const currentIndex = s.game && typeof s.game.questionIndex === "number" ? s.game.questionIndex : 0;
          const prev = Math.max(0, currentIndex - 1);
          State.updateSlice("game", { activeTopic: topic.key, questionIndex: prev });
        }
        function sendGameAnswer(topicKey, text) {
          const t = (text || "").trim();
          const topic = getGameTopic(topicKey);
          if (!t || !topic) return;
          const s = State.getState();
          const idx = s.game && typeof s.game.questionIndex === "number" ? s.game.questionIndex : 0;
          const answers = Object.assign({}, (s.game && s.game.answers) || {});
          const arr = (answers[topic.key] || []).slice(0);
          arr.push({ question: topic.questions[idx] || "", text: t, index: idx });
          answers[topic.key] = arr.slice(-20);
          State.updateSlice("game", { activeTopic: topic.key, questionIndex: idx, answers });
        }
        function toggleHistoryPanel() {
          const s = State.getState();
          const open = !(s.historyView && s.historyView.open);
          const latest = s.scoresHistory && s.scoresHistory.length ? s.scoresHistory[s.scoresHistory.length - 1].date : null;
          const selected = s.historyView && s.historyView.selectedDate ? s.historyView.selectedDate : latest;
          State.updateSlice("historyView", { open, selectedDate: selected });
        }
        function selectHistoryDate(dateStr) {
          if (!dateStr) return;
          State.updateSlice("historyView", { open: true, selectedDate: dateStr });
        }
        function saveHistoryNote(dateStr) {
          if (!dateStr) return;
          const field = document.querySelector(`[data-role="history-note"][data-date="${dateStr}"]`);
          if (!field) return;
          State.updateHistoryNote(dateStr, field.value || "");
        }
        function openHistoryFull() {
          const s = State.getState();
          const history = s.scoresHistory || [];
          const latest = history.length ? history[history.length - 1].date : null;
          const prev = s.historyView || {};
          State.updateSlice("historyView", { open: true, selectedDate: prev.selectedDate || latest });
          navigate("history");
        }
        function historyBackToHome() {
          navigate("home");
        }
        function flipTheme() {
          const cur = State.getState();
          const next = cur.theme === "dark" ? "light" : "dark";
          State.setState({ theme: next });
          applyTheme(next);
        }
        /* ---------- TELEGRAM INIT (минимально) ---------- */
        function initTelegramUser() {
          try {
            const tg = window.Telegram && window.Telegram.WebApp;
            if (!tg) return;
            tg.ready && tg.ready();
            const u = tg.initDataUnsafe && tg.initDataUnsafe.user;
            if (!u) return;
            const cur = State.getState();
            State.setState({ user: { id: u.id, name: u.first_name || cur.user.name || "Гость", username: u.username || cur.user.username || null } });
          } catch (e) {
            console.warn(e);
          }
        }
        /* ---------- GLOBAL HANDLERS ---------- */
        function initHandlers() {
          document.addEventListener("click", (e) => {
            const btn = e.target.closest("[data-action]");
            if (!btn) return;
            const act = btn.dataset.action;
            switch (act) {
              case "intro-set-star": {
                const kind = btn.dataset.kind;
                const val = Number(btn.dataset.value || 0);
                const screen = btn.closest(".intro-screen");
                const idx = screen && screen.dataset.questionIndex ? Number(screen.dataset.questionIndex) : 0;
                introSetStar(kind, val, idx);
                break;
              }
              case "intro-toggle-reason": {
                const kind = btn.dataset.kind;
                const optionIndex = Number(btn.dataset.index || 0);
                introToggleReason(kind, optionIndex, btn);
                break;
              }
              case "intro-confirm-reasons": {
                const kind = btn.dataset.kind;
                const idx = Number(btn.dataset.questionIndex || 0);
                introConfirmReasons(kind, idx);
                break;
              }
              case "intro-next": {
                const idx = Number(btn.dataset.questionIndex || 0);
                introNext(idx);
                break;
              }
              case "nav":
                navigate(btn.dataset.view || "home", { resetStack: true });
                break;
              case "nav-back":
                goBack();
                break;
              case "open-feature":
                navigate(btn.dataset.feature || "home");
                break;
              case "chat-send": {
                const input = document.querySelector('[data-role="chat-input"]');
                if (!input) return;
                const text = input.value;
                input.value = "";
                sendChat(text);
                break;
              }
              case "sleep-set":
                setSleepParam(btn.dataset.key, btn.dataset.value);
                break;
              case "sleep-build-plan":
                buildSleepPlan();
                break;
              case "finance-build-plan":
                buildFinancePlan();
                break;
              case "finance-calc-safety":
                calculateSafetyFund();
                break;
              case "game-select-topic":
                selectGameTopic(btn.dataset.topic);
                break;
              case "game-next-question":
                nextGameQuestion();
                break;
              case "game-prev-question":
                prevGameQuestion();
                break;
              case "game-send-answer": {
                const topic = btn.dataset.topic;
                const input = document.querySelector(`[data-role="game-answer"][data-topic="${topic}"]`);
                const text = input ? input.value : "";
                if (input) input.value = "";
                sendGameAnswer(topic, text);
                break;
              }
              case "open-subscription":
                alert("Экран управления подпиской будет здесь.");
                break;
              case "history-open-full":
                openHistoryFull();
                break;
              case "history-back":
                historyBackToHome();
                break;
              case "history-select":
                selectHistoryDate(btn.dataset.date);
                break;
              case "history-save-note":
                saveHistoryNote(btn.dataset.date);
                break;
              case "toggle-theme":
                flipTheme();
                break;
            }
          });
          document.addEventListener("keydown", (e) => {
            if (e.key === "Enter") {
              const active = document.activeElement;
              if (active && active.getAttribute("data-role") === "chat-input") {
                e.preventDefault();
                const text = active.value;
                active.value = "";
                sendChat(text);
              }
            }
          });
        }
        function init() {
          navStack = [];
          introRoot = document.getElementById("intro-root");
          initTelegramUser();
          initHandlers();
          applyTheme(State.getState().theme);
          const initial = State.getState();
          const normalizedView = safeView(initial.currentView);
          if (normalizedView !== initial.currentView) {
            State.setState({ currentView: normalizedView });
          }
          Bus.on("state:changed", () => {
            const s = State.getState();
            applyTheme(s.theme);
            syncHeaderNav();
            renderMain();
          });
          if (introRoot) {
            const appShell = document.querySelector(".app-shell");
            const bottomNav = document.querySelector(".c-bottom-nav");
            if (appShell) appShell.classList.add("app-shell--hidden");
            if (bottomNav) bottomNav.classList.add("app-shell--hidden");
            introRoot.classList.remove("intro-hidden");
            showIntroLogo();
          }
        }
        return { init };
      })();
      document.addEventListener("DOMContentLoaded", () => {
        AdviceApp.Features.init();
      });
    })();
  </script>
</body>
</html>
