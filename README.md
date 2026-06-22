<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>cyberfunk · cinematic dark</title>
  <!-- font & icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #0b0b0f;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Segoe UI', 'Poppins', system-ui, sans-serif;
      padding: 1.5rem;
    }

    /* cyberfunk card — cinematic dark glow */
    .profile-card {
      position: relative;
      max-width: 780px;
      width: 100%;
      background: rgba(8, 8, 16, 0.75);
      backdrop-filter: blur(6px);
      -webkit-backdrop-filter: blur(6px);
      border: 1px solid rgba(0, 255, 255, 0.25);
      border-radius: 3.5rem 1rem 3.5rem 1rem;
      padding: 2.8rem 2.5rem;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.8), 
                  0 0 0 1px rgba(0, 255, 200, 0.2) inset,
                  0 0 30px rgba(0, 255, 200, 0.15);
      transition: box-shadow 0.3s ease;
      overflow: hidden;
      z-index: 2;
    }

    /* animated scanline / glitch overlay */
    .profile-card::before {
      content: '';
      position: absolute;
      top: -10%;
      left: -10%;
      width: 120%;
      height: 120%;
      background: repeating-linear-gradient(0deg, 
        rgba(0, 255, 200, 0.02) 0px, 
        rgba(0, 255, 200, 0.02) 2px, 
        transparent 2px, 
        transparent 8px);
      pointer-events: none;
      z-index: 0;
      animation: scanlineMove 8s linear infinite;
    }

    @keyframes scanlineMove {
      0% { transform: translateY(0); }
      100% { transform: translateY(20px); }
    }

    /* neon pulse ring — cinematic */
    .profile-card::after {
      content: '';
      position: absolute;
      top: -3px;
      left: -3px;
      right: -3px;
      bottom: -3px;
      border-radius: 3.7rem 1.2rem 3.7rem 1.2rem;
      background: conic-gradient(from 0deg, transparent, rgba(0, 255, 200, 0.2), transparent, rgba(255, 0, 200, 0.2), transparent);
      z-index: -1;
      animation: rotateGlow 12s linear infinite;
      opacity: 0.6;
    }

    @keyframes rotateGlow {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* content layer */
    .profile-content {
      position: relative;
      z-index: 3;
      display: flex;
      flex-direction: column;
      gap: 1.8rem;
    }

    /* header: avatar + title */
    .profile-header {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 1.8rem;
    }

    .avatar-wrapper {
      position: relative;
      width: 110px;
      height: 110px;
      flex-shrink: 0;
    }

    .avatar {
      width: 100%;
      height: 100%;
      border-radius: 40% 60% 40% 60% / 60% 40% 60% 40%;
      background: linear-gradient(145deg, #0d0d1a, #1a1a2e);
      border: 2px solid #00ffe0;
      box-shadow: 0 0 25px rgba(0, 255, 200, 0.4), 0 0 8px #ff00b0 inset;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3.6rem;
      color: #b0fff0;
      text-shadow: 0 0 15px #00ffe0, 0 0 30px #ff00b0;
      transition: all 0.2s ease;
      animation: avatarPulse 4s infinite alternate;
    }

    @keyframes avatarPulse {
      0% { box-shadow: 0 0 15px rgba(0, 255, 200, 0.3), 0 0 5px #ff00b0 inset; }
      100% { box-shadow: 0 0 35px rgba(0, 255, 200, 0.8), 0 0 20px #ff00b0 inset; }
    }

    .avatar i {
      filter: drop-shadow(0 0 12px #00ffe0);
    }

    .title-group {
      flex: 1;
    }

    .title-group h1 {
      font-size: 2.6rem;
      font-weight: 700;
      letter-spacing: 2px;
      background: linear-gradient(135deg, #b0fff0, #a0f0ff, #ff80c0);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      text-shadow: 0 0 30px rgba(0, 255, 200, 0.2);
      margin-bottom: 0.2rem;
      display: inline-block;
      animation: glitchText 5s infinite;
    }

    @keyframes glitchText {
      0%, 95%, 100% { transform: skew(0deg, 0deg); opacity: 1; }
      96% { transform: skew(2deg, -1deg); opacity: 0.8; }
      97% { transform: skew(-2deg, 1deg); opacity: 0.9; }
      98% { transform: skew(1deg, -0.5deg); opacity: 0.8; }
    }

    .title-group .tagline {
      font-size: 1rem;
      letter-spacing: 4px;
      color: #a0c0d0;
      text-transform: uppercase;
      border-left: 3px solid #ff00b0;
      padding-left: 14px;
      background: linear-gradient(90deg, #a0f0ff, #ff80c0);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      font-weight: 300;
      text-shadow: 0 0 20px #00ffe0;
    }

    /* bio — cyberpunk description */
    .bio {
      font-size: 1rem;
      line-height: 1.6;
      color: #c8d8e8;
      background: rgba(0, 20, 30, 0.4);
      padding: 1.2rem 1.8rem;
      border-radius: 2rem 0.5rem 2rem 0.5rem;
      border-left: 4px solid #00ffe0;
      border-right: 1px solid rgba(255, 0, 200, 0.3);
      backdrop-filter: blur(4px);
      box-shadow: 0 0 30px rgba(0, 255, 200, 0.05);
      font-weight: 300;
      letter-spacing: 0.3px;
      word-break: break-word;
      animation: flicker 6s infinite alternate;
    }

    @keyframes flicker {
      0% { opacity: 0.9; text-shadow: 0 0 3px #00ffe0; }
      100% { opacity: 1; text-shadow: 0 0 12px #ff00b0; }
    }

    .bio i {
      color: #ff00b0;
      margin-right: 6px;
    }

    /* stats grid — cyberpunk meters */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1rem;
      margin: 0.5rem 0;
    }

    .stat-item {
      background: rgba(0, 20, 30, 0.5);
      backdrop-filter: blur(4px);
      padding: 0.8rem 0.4rem;
      text-align: center;
      border-radius: 1.2rem 0.3rem 1.2rem 0.3rem;
      border: 1px solid rgba(0, 255, 200, 0.15);
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
      transition: all 0.3s ease;
    }

    .stat-item:hover {
      border-color: #ff00b0;
      box-shadow: 0 0 30px rgba(255, 0, 200, 0.2);
      transform: scale(1.02);
    }

    .stat-number {
      font-size: 2rem;
      font-weight: 700;
      background: linear-gradient(135deg, #00ffe0, #ff80c0);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      letter-spacing: 2px;
      text-shadow: 0 0 20px #00ffe0;
      animation: numberPulse 3s infinite alternate;
    }

    @keyframes numberPulse {
      0% { opacity: 0.7; text-shadow: 0 0 10px #00ffe0; }
      100% { opacity: 1; text-shadow: 0 0 30px #ff00b0; }
    }

    .stat-label {
      font-size: 0.7rem;
      text-transform: uppercase;
      letter-spacing: 2px;
      color: #a0c8d8;
      margin-top: 4px;
      border-top: 1px dashed rgba(0, 255, 200, 0.2);
      padding-top: 6px;
    }

    /* link / button grid — animated */
    .link-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 0.8rem 1.2rem;
      margin-top: 0.6rem;
    }

    .cyber-btn {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      padding: 0.7rem 1.8rem;
      background: rgba(0, 20, 30, 0.5);
      backdrop-filter: blur(8px);
      border: 1px solid rgba(0, 255, 200, 0.3);
      border-radius: 3rem 0.6rem 3rem 0.6rem;
      color: #d0f0f0;
      font-weight: 500;
      text-decoration: none;
      letter-spacing: 1.5px;
      font-size: 0.9rem;
      transition: all 0.25s ease;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
      text-transform: uppercase;
      position: relative;
      overflow: hidden;
    }

    .cyber-btn i {
      color: #00ffe0;
      font-size: 1.2rem;
      transition: 0.2s;
    }

    .cyber-btn:hover {
      background: rgba(0, 255, 200, 0.08);
      border-color: #ff00b0;
      box-shadow: 0 0 30px rgba(255, 0, 200, 0.2), 0 0 15px #00ffe0;
      transform: translateY(-3px) scale(1.02);
      color: #fff;
    }

    .cyber-btn:hover i {
      color: #ff80c0;
      transform: rotate(-8deg) scale(1.1);
    }

    /* animated glitch line (bottom) */
    .glitch-line {
      margin-top: 1.8rem;
      height: 2px;
      width: 100%;
      background: linear-gradient(90deg, transparent, #00ffe0, #ff00b0, transparent);
      animation: lineGlitch 4s infinite;
      border-radius: 100%;
      opacity: 0.6;
    }

    @keyframes lineGlitch {
      0% { transform: translateX(-100%); opacity: 0.2; }
      50% { transform: translateX(10%); opacity: 1; }
      100% { transform: translateX(100%); opacity: 0.2; }
    }

    /* responsive */
    @media (max-width: 550px) {
      .profile-card { padding: 1.8rem 1.2rem; }
      .profile-header { flex-direction: column; align-items: center; text-align: center; }
      .title-group .tagline { border-left: none; padding-left: 0; }
      .stats-grid { grid-template-columns: 1fr 1fr; }
      .stat-item:last-child { grid-column: span 2; }
      .avatar-wrapper { width: 90px; height: 90px; }
    }

    @media (max-width: 400px) {
      .stats-grid { grid-template-columns: 1fr; }
      .stat-item:last-child { grid-column: span 1; }
    }

    /* extra micro animation for icons */
    .fa-code, .fa-terminal, .fa-microchip {
      animation: iconFloat 3s ease-in-out infinite alternate;
    }
    .fa-code { animation-delay: 0.1s; }
    .fa-terminal { animation-delay: 0.7s; }
    .fa-microchip { animation-delay: 1.3s; }

    @keyframes iconFloat {
      0% { transform: translateY(0px) scale(1); }
      100% { transform: translateY(-5px) scale(1.1); }
    }

    /* tiny glitch dots */
    .glitch-dots {
      display: flex;
      justify-content: center;
      gap: 10px;
      margin-top: 5px;
    }
    .glitch-dots span {
      width: 8px;
      height: 8px;
      background: #00ffe0;
      border-radius: 50%;
      opacity: 0.2;
      animation: dotFade 2.4s infinite alternate;
    }
    .glitch-dots span:nth-child(2) { animation-delay: 0.6s; background: #ff00b0; }
    .glitch-dots span:nth-child(3) { animation-delay: 1.2s; }

    @keyframes dotFade {
      0% { opacity: 0.1; transform: scale(0.8); }
      100% { opacity: 0.9; transform: scale(1.3); }
    }
  </style>
</head>
<body>
  <div class="profile-card">
    <div class="profile-content">
      <!-- header -->
      <div class="profile-header">
        <div class="avatar-wrapper">
          <div class="avatar">
            <i class="fas fa-user-astronaut"></i>
          </div>
        </div>
        <div class="title-group">
          <h1>// CYBERFUNK</h1>
          <div class="tagline">
            <i class="fas fa-skull" style="margin-right: 6px;"></i> GHOST IN THE SHELL
          </div>
        </div>
      </div>

      <!-- bio cinematic -->
      <div class="bio">
        <i class="fas fa-quote-left"></i> 
        full-stack · neural interface · darkwave coder 
        <i class="fas fa-quote-right"></i> 
        <span style="display: inline-block; margin-left: 10px; font-size: 0.8rem; color: #ff80c0;">
          <i class="fas fa-circle" style="font-size: 0.5rem; vertical-align: middle;"></i> LIVE
        </span>
      </div>

      <!-- stats -->
      <div class="stats-grid">
        <div class="stat-item">
          <div class="stat-number">42</div>
          <div class="stat-label"><i class="fas fa-code"></i> repos</div>
        </div>
        <div class="stat-item">
          <div class="stat-number">1.2k</div>
          <div class="stat-label"><i class="fas fa-users"></i> followers</div>
        </div>
        <div class="stat-item">
          <div class="stat-number">∞</div>
          <div class="stat-label"><i class="fas fa-microchip"></i> commits</div>
        </div>
      </div>

      <!-- link buttons with animation -->
      <div class="link-grid">
        <a href="#" class="cyber-btn"><i class="fab fa-github"></i> hub</a>
        <a href="#" class="cyber-btn"><i class="fab fa-twitter"></i> feed</a>
        <a href="#" class="cyber-btn"><i class="fas fa-terminal"></i> shell</a>
        <a href="#" class="cyber-btn"><i class="fas fa-robot"></i> ai</a>
      </div>

      <!-- glitch line & dots -->
      <div class="glitch-line"></div>
      <div class="glitch-dots">
        <span></span><span></span><span></span>
      </div>

      <!-- tiny credit / vibe -->
      <div style="margin-top: 0.8rem; font-size: 0.6rem; text-align: right; color: #607080; letter-spacing: 3px; opacity: 0.5; border-top: 1px solid rgba(0,255,200,0.1); padding-top: 8px;">
        <i class="fas fa-bolt" style="color: #ff00b0;"></i> 暗黒 サイバーファンク
      </div>
    </div>
  </div>
</body>
</html>
