
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 420" width="800" height="420">
  <defs>
    <!-- CRT scanline pattern -->
    <pattern id="scanlines" x="0" y="0" width="800" height="4" patternUnits="userSpaceOnUse">
      <rect width="800" height="2" fill="rgba(0,0,0,0.15)"/>
      <rect y="2" width="800" height="2" fill="transparent"/>
    </pattern>

    <!-- Glow filter for green text -->
    <filter id="glow" x="-20%" y="-20%" width="140%" height="140%">
      <feGaussianBlur stdDeviation="3" result="blur"/>
      <feMerge>
        <feMergeNode in="blur"/>
        <feMergeNode in="blur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>

    <!-- Strong glow for title -->
    <filter id="strongGlow" x="-30%" y="-30%" width="160%" height="160%">
      <feGaussianBlur stdDeviation="5" result="blur"/>
      <feMerge>
        <feMergeNode in="blur"/>
        <feMergeNode in="blur"/>
        <feMergeNode in="blur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>

    <!-- Glitch clip paths -->
    <clipPath id="glitch1">
      <rect x="0" y="80" width="800" height="30"/>
    </clipPath>
    <clipPath id="glitch2">
      <rect x="0" y="160" width="800" height="20"/>
    </clipPath>
    <clipPath id="glitch3">
      <rect x="0" y="240" width="800" height="25"/>
    </clipPath>

    <style>
      @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&amp;display=swap');

      .terminal-font {
        font-family: 'Share Tech Mono', 'Courier New', monospace;
      }

      /* Background flicker */
      @keyframes flicker {
        0%   { opacity: 1; }
        2%   { opacity: 0.92; }
        4%   { opacity: 1; }
        19%  { opacity: 1; }
        21%  { opacity: 0.88; }
        23%  { opacity: 1; }
        80%  { opacity: 1; }
        82%  { opacity: 0.95; }
        84%  { opacity: 1; }
      }

      /* Cursor blink */
      @keyframes blink {
        0%, 49% { opacity: 1; }
        50%, 100% { opacity: 0; }
      }

      /* Typing reveal for prompt line */
      @keyframes typePrompt {
        from { clip-path: inset(0 100% 0 0); }
        to   { clip-path: inset(0 0% 0 0); }
      }

      /* Glitch horizontal shift */
      @keyframes glitchShift {
        0%   { transform: translateX(0); opacity: 1; }
        2%   { transform: translateX(-6px); opacity: 0.8; }
        4%   { transform: translateX(4px); opacity: 0.9; }
        6%   { transform: translateX(0); opacity: 1; }
        91%  { transform: translateX(0); opacity: 1; }
        92%  { transform: translateX(5px); opacity: 0.7; }
        93%  { transform: translateX(-3px); opacity: 0.85; }
        94%  { transform: translateX(0); opacity: 1; }
        100% { transform: translateX(0); opacity: 1; }
      }

      /* Glitch color slice - red layer */
      @keyframes glitchRed {
        0%   { transform: translateX(0); opacity: 0; }
        2%   { transform: translateX(4px); opacity: 0.6; }
        4%   { transform: translateX(-2px); opacity: 0.4; }
        6%   { transform: translateX(0); opacity: 0; }
        91%  { opacity: 0; }
        92%  { transform: translateX(-4px); opacity: 0.5; }
        93%  { transform: translateX(3px); opacity: 0.3; }
        94%  { opacity: 0; }
        100% { opacity: 0; }
      }

      /* Glitch color slice - cyan layer */
      @keyframes glitchCyan {
        0%   { transform: translateX(0); opacity: 0; }
        2%   { transform: translateX(-5px); opacity: 0.5; }
        4%   { transform: translateX(3px); opacity: 0.35; }
        6%   { transform: translateX(0); opacity: 0; }
        91%  { opacity: 0; }
        92%  { transform: translateX(5px); opacity: 0.4; }
        93%  { transform: translateX(-4px); opacity: 0.25; }
        94%  { opacity: 0; }
        100% { opacity: 0; }
      }

      /* Name fade-in + slide up */
      @keyframes nameReveal {
        0%   { opacity: 0; transform: translateY(12px); }
        100% { opacity: 1; transform: translateY(0); }
      }

      /* Subtitle slide in */
      @keyframes subtitleReveal {
        0%   { opacity: 0; transform: translateX(-20px); }
        100% { opacity: 1; transform: translateX(0); }
      }

      /* Pulse glow on border */
      @keyframes borderPulse {
        0%, 100% { stroke-opacity: 0.6; }
        50%       { stroke-opacity: 1; }
      }

      /* Scanline sweep */
      @keyframes scanSweep {
        0%   { transform: translateY(-420px); }
        100% { transform: translateY(420px); }
      }

      /* Corner blink */
      @keyframes cornerBlink {
        0%, 100% { opacity: 1; }
        50%       { opacity: 0.3; }
      }

      .screen-flicker {
        animation: flicker 5s infinite;
      }

      .name-text {
        animation: nameReveal 0.6s ease-out both, glitchShift 8s 1s infinite;
      }

      .name-red {
        animation: nameReveal 0.6s ease-out both, glitchRed 8s 1s infinite;
      }

      .name-cyan {
        animation: nameReveal 0.6s ease-out both, glitchCyan 8s 1s infinite;
      }

      .cursor {
        animation: blink 1s step-end infinite;
      }

      .prompt-line {
        animation: typePrompt 1.2s steps(20, end) 0.3s both;
      }

      .subtitle-box {
        animation: subtitleReveal 0.7s ease-out 1.5s both;
      }

      .border-main {
        animation: borderPulse 3s ease-in-out infinite;
      }

      .corner-tl { animation: cornerBlink 2s 0s infinite; }
      .corner-tr { animation: cornerBlink 2s 0.5s infinite; }
      .corner-bl { animation: cornerBlink 2s 1s infinite; }
      .corner-br { animation: cornerBlink 2s 1.5s infinite; }
    </style>
  </defs>

  <!-- === BACKGROUND === -->
  <rect width="800" height="420" fill="#0d0f0d"/>

  <!-- Screen content wrapper with flicker -->
  <g class="screen-flicker">

    <!-- Outer border frame -->
    <rect x="10" y="10" width="780" height="400" fill="none"
          stroke="#00ff41" stroke-width="1.5" stroke-opacity="0.5" class="border-main"
          rx="4"/>

    <!-- Inner border frame -->
    <rect x="18" y="18" width="764" height="384" fill="none"
          stroke="#00ff41" stroke-width="0.5" stroke-opacity="0.25" rx="2"/>

    <!-- Corner decorations TL -->
    <g class="corner-tl" fill="none" stroke="#00ff41" stroke-width="1.5">
      <line x1="10" y1="30" x2="10" y2="10"/>
      <line x1="10" y1="10" x2="30" y2="10"/>
    </g>
    <!-- Corner TR -->
    <g class="corner-tr" fill="none" stroke="#00ff41" stroke-width="1.5">
      <line x1="790" y1="30" x2="790" y2="10"/>
      <line x1="790" y1="10" x2="770" y2="10"/>
    </g>
    <!-- Corner BL -->
    <g class="corner-bl" fill="none" stroke="#00ff41" stroke-width="1.5">
      <line x1="10" y1="390" x2="10" y2="410"/>
      <line x1="10" y1="410" x2="30" y2="410"/>
    </g>
    <!-- Corner BR -->
    <g class="corner-br" fill="none" stroke="#00ff41" stroke-width="1.5">
      <line x1="790" y1="390" x2="790" y2="410"/>
      <line x1="790" y1="410" x2="770" y2="410"/>
    </g>

    <!-- === PROMPT LINE === -->
    <g class="prompt-line">
      <text x="40" y="58" class="terminal-font" font-size="15"
            fill="#00ff41" filter="url(#glow)">varun@dev:~$  whoami</text>
    </g>
    <!-- Blinking cursor after prompt -->
    <rect x="244" y="43" width="9" height="17" fill="#00ff41" class="cursor" filter="url(#glow)"/>

    <!-- === SEPARATOR LINE === -->
    <line x1="40" y1="72" x2="760" y2="72" stroke="#00ff41" stroke-opacity="0.2" stroke-width="0.8"/>

    <!-- === NAME : VARUN — Big pixel block letters using rects === -->
    <!-- We use text with a very large pixel/block font simulation -->
    <!-- VARUN -->

    <!-- Red glitch layer (behind) -->
    <text x="40" y="175" class="terminal-font name-red"
          font-size="110" font-weight="bold" letter-spacing="-2"
          fill="#ff003c" opacity="0" filter="url(#glow)"
          style="animation-delay: 0.3s">VARUN</text>

    <!-- Cyan glitch layer (behind) -->
    <text x="40" y="175" class="terminal-font name-cyan"
          font-size="110" font-weight="bold" letter-spacing="-2"
          fill="#00fff9" opacity="0" filter="url(#glow)"
          style="animation-delay: 0.3s">VARUN</text>

    <!-- Main green layer -->
    <text x="40" y="175" class="terminal-font name-text"
          font-size="110" font-weight="bold" letter-spacing="-2"
          fill="#00ff41" filter="url(#strongGlow)"
          style="animation-delay: 0.3s">VARUN</text>

    <!-- MENDRE -->
    <!-- Red glitch layer -->
    <text x="40" y="295" class="terminal-font name-red"
          font-size="110" font-weight="bold" letter-spacing="-2"
          fill="#ff003c" opacity="0" filter="url(#glow)"
          style="animation-delay: 0.6s">MENDRE</text>

    <!-- Cyan glitch layer -->
    <text x="40" y="295" class="terminal-font name-cyan"
          font-size="110" font-weight="bold" letter-spacing="-2"
          fill="#00fff9" opacity="0" filter="url(#glow)"
          style="animation-delay: 0.6s">MENDRE</text>

    <!-- Main green layer -->
    <text x="40" y="295" class="terminal-font name-text"
          font-size="110" font-weight="bold" letter-spacing="-2"
          fill="#00ff41" filter="url(#strongGlow)"
          style="animation-delay: 0.6s">MENDRE</text>

    <!-- === SUBTITLE BOX === -->
    <g class="subtitle-box">
      <!-- Box background -->
      <rect x="40" y="315" width="500" height="46" fill="#00ff41" fill-opacity="0.07"
            stroke="#00ff41" stroke-width="1" stroke-opacity="0.6" rx="2"/>
      <!-- Left accent bar -->
      <rect x="40" y="315" width="3" height="46" fill="#00ff41"/>
      <!-- Subtitle text -->
      <text x="60" y="344" class="terminal-font" font-size="16"
            fill="#00ff41" filter="url(#glow)">
        &gt; Software Developer  |  Backend Developer
      </text>
      <!-- Blinking cursor at end -->
      <rect x="508" y="328" width="8" height="16" fill="#00ff41" class="cursor"/>
    </g>

    <!-- === SCANLINE OVERLAY === -->
    <rect width="800" height="420" fill="url(#scanlines)" opacity="0.6"/>

    <!-- === SCAN SWEEP LINE (one-time boot effect) === -->
    <rect x="0" y="0" width="800" height="3"
          fill="linear-gradient(transparent, rgba(0,255,65,0.4), transparent)"
          opacity="0.5">
      <animateTransform attributeName="transform" type="translate"
                        from="0,-10" to="0,430"
                        dur="1.5s" repeatCount="1" begin="0s"/>
      <animate attributeName="opacity" values="0;0.6;0" dur="1.5s" repeatCount="1" begin="0s"/>
    </rect>

    <!-- Status line bottom -->
    <text x="40" y="402" class="terminal-font" font-size="10"
          fill="#00ff41" fill-opacity="0.4">
      [CONNECTED]  SESSION: active  ///  github.com/varunmendre
    </text>
    <text x="680" y="402" class="terminal-font" font-size="10"
          fill="#00ff41" fill-opacity="0.4">v2.4.1</text>

  </g>
</svg>
