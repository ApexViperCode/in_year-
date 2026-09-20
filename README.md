​⏳ Age Calculator
​An interactive tool that calculates your exact age in years, months, and days based on your birth date. This project combines fast C++ logic with a modern, responsive web interface built using HTML and CSS.
​Features
​High Precision: Accurately calculates your age broken down into years, months, and days.
​Sleek Interface: Clean, user-friendly design for an intuitive experience.
​Fast Performance: Reliable computation powered by C++.

​Built With
​C++: Handles backend processing and calculation logic.
​HTML5: Structures the user interface and input fields.
​CSS3: Styles the application with a clean, modern look.

​How It Works
​Input your birth details (day, month, and year) into the designated fields.
​The application computes the difference between the current date and your date of birth.
​The exact age breakdown appears instantly on the display.



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Apex Portal - Sign In</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;900&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }

    body {
      min-height: 100vh;
      background: #05020a;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
      position: relative;
    }

    /* خلفية الشبكة والجزيئات */
    #canvas {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
    }

    .glow-orb {
      position: absolute;
      width: 450px;
      height: 450px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(147, 51, 234, 0.35) 0%, rgba(0, 0, 0, 0) 70%);
      filter: blur(50px);
      z-index: 2;
      animation: pulse 8s infinite alternate ease-in-out;
    }

    .glow-orb-2 {
      right: 10%;
      bottom: 10%;
      background: radial-gradient(circle, rgba(79, 70, 229, 0.25) 0%, rgba(0, 0, 0, 0) 70%);
      animation-delay: -4s;
    }

    @keyframes pulse {
      0% { transform: scale(1) translate(0, 0); }
      100% { transform: scale(1.2) translate(30px, -30px); }
    }

    /* كرت تسجيل الدخول الرئيسي */
    .container {
      position: relative;
      z-index: 10;
      width: 420px;
      padding: 50px 40px;
      background: rgba(15, 7, 28, 0.65);
      backdrop-filter: blur(25px);
      -webkit-backdrop-filter: blur(25px);
      border: 1px solid rgba(168, 85, 247, 0.25);
      border-radius: 24px;
      box-shadow: 0 0 50px rgba(147, 51, 234, 0.2), 
                  inset 0 0 15px rgba(168, 85, 247, 0.1);
      transform-style: preserve-3d;
      transition: transform 0.2s ease, box-shadow 0.3s ease;
    }

    .container:hover {
      border-color: rgba(168, 85, 247, 0.5);
      box-shadow: 0 0 60px rgba(147, 51, 234, 0.35), 
                  inset 0 0 20px rgba(168, 85, 247, 0.2);
    }

    .title {
      font-family: 'Orbitron', sans-serif;
      color: #fff;
      font-size: 2rem;
      text-align: center;
      margin-bottom: 8px;
      letter-spacing: 2px;
      text-shadow: 0 0 10px rgba(168, 85, 247, 0.8);
    }

    .subtitle {
      color: #a78bfa;
      font-size: 0.85rem;
      text-align: center;
      margin-bottom: 35px;
      letter-spacing: 1px;
    }

    .input-group {
      position: relative;
      margin-bottom: 25px;
    }

    .input-group input {
      width: 100%;
      padding: 14px 18px;
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(168, 85, 247, 0.3);
      border-radius: 12px;
      outline: none;
      color: #fff;
      font-size: 0.95rem;
      transition: 0.3s;
    }

    .input-group label {
      position: absolute;
      left: 18px;
      top: 50%;
      transform: translateY(-50%);
      color: #8b5cf6;
      font-size: 0.9rem;
      pointer-events: none;
      transition: 0.3s;
    }

    .input-group input:focus,
    .input-group input:valid {
      border-color: #c084fc;
      background: rgba(168, 85, 247, 0.08);
      box-shadow: 0 0 15px rgba(168, 85, 247, 0.3);
    }

    .input-group input:focus ~ label,
    .input-group input:valid ~ label {
      top: -10px;
      left: 12px;
      font-size: 0.75rem;
      padding: 0 6px;
      background: #0f071c;
      color: #c084fc;
      border-radius: 4px;
    }

    /* مربع التحقق الروبوت */
    .captcha-container {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: rgba(255, 255, 255, 0.02);
      border: 1px solid rgba(168, 85, 247, 0.2);
      padding: 12px 16px;
      border-radius: 12px;
      margin-bottom: 30px;
    }

    .captcha-left {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .captcha-left input[type="checkbox"] {
      appearance: none;
      width: 22px;
      height: 22px;
      border: 2px solid #8b5cf6;
      border-radius: 6px;
      cursor: pointer;
      position: relative;
      transition: 0.2s;
    }

    .captcha-left input[type="checkbox"]:checked {
      background: #a855f7;
      border-color: #a855f7;
      box-shadow: 0 0 10px #a855f7;
    }

    .captcha-left input[type="checkbox"]:checked::after {
      content: '✓';
      position: absolute;
      color: white;
      font-size: 14px;
      font-weight: bold;
      left: 4px;
      top: -1px;
    }

    .captcha-label {
      color: #ddd;
      font-size: 0.85rem;
      user-select: none;
    }

    .captcha-icon {
      font-size: 1.4rem;
      filter: drop-shadow(0 0 5px #a855f7);
    }

    /* زر الساين إن */
    .btn-signin {
      width: 100%;
      padding: 14px;
      background: linear-gradient(135deg, #7e22ce, #a855f7);
      border: none;
      border-radius: 12px;
      color: #fff;
      font-family: 'Orbitron', sans-serif;
      font-size: 1rem;
      font-weight: 700;
      letter-spacing: 1px;
      cursor: pointer;
      transition: 0.3s;
      box-shadow: 0 0 20px rgba(168, 85, 247, 0.4);
    }

    .btn-signin:hover {
      background: linear-gradient(135deg, #9333ea, #c084fc);
      box-shadow: 0 0 30px rgba(168, 85, 247, 0.8);
      transform: translateY(-2px);
    }

    /* واجهة البروفايل */
    .profile-box {
      display: none;
      text-align: center;
      animation: fadeIn 0.5s ease-in-out forwards;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }

    .profile-avatar {
      width: 90px;
      height: 90px;
      margin: 0 auto 20px;
      border-radius: 50%;
      background: linear-gradient(135deg, #a855f7, #3b82f6);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'Orbitron', sans-serif;
      font-size: 2.5rem;
      color: #fff;
      box-shadow: 0 0 25px rgba(168, 85, 247, 0.6);
      border: 2px solid rgba(255, 255, 255, 0.8);
    }

    .welcome-text {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.4rem;
      color: #fff;
      margin-bottom: 8px;
    }

    .status-badge {
      display: inline-block;
      padding: 4px 12px;
      background: rgba(34, 197, 94, 0.15);
      border: 1px solid #22c55e;
      color: #4ade80;
      border-radius: 20px;
      font-size: 0.75rem;
      margin-bottom: 25px;
    }

    .btn-logout {
      width: 100%;
      padding: 12px;
      background: transparent;
      border: 1px solid #ef4444;
      color: #ef4444;
      border-radius: 12px;
      font-weight: 600;
      cursor: pointer;
      transition: 0.3s;
    }

    .btn-logout:hover {
      background: #ef4444;
      color: #fff;
      box-shadow: 0 0 20px rgba(239, 68, 68, 0.5);
    }
  </style>
</head>
<body>

  <canvas id="canvas"></canvas>
  <div class="glow-orb"></div>
  <div class="glow-orb glow-orb-2"></div>

  <div class="container" id="cardContainer">
    <!-- Form -->
    <div id="loginForm">
      <h1 class="title">WELCOME</h1>
      <p class="subtitle">Access your academy dashboard</p>
      
      <form onsubmit="executeLogin(event)">
        <div class="input-group">
          <input type="text" id="userInput" required autocomplete="off">
          <label>Username</label>
        </div>

        <div class="input-group">
          <input type="password" required autocomplete="off">
          <label>Password</label>
        </div>

        <div class="captcha-container">
          <div class="captcha-left">
            <input type="checkbox" id="botCheck" required>
            <label for="botCheck" class="captcha-label">I'm not a robot</label>
          </div>
          <div class="captcha-icon">🤖</div>
        </div>

        <button type="submit" class="btn-signin">SIGN IN</button>
      </form>
    </div>

    <!-- Profile View -->
    <div class="profile-box" id="profileBox">
      <div class="profile-avatar" id="userInitial">A</div>
      <h2 class="welcome-text" id="displayUser">User</h2>
      <div class="status-badge">● Authenticated</div>
      <button class="btn-logout" onclick="executeLogout()">LOG OUT</button>
    </div>
  </div>

  <script>
    // Particle Background
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');
    let particles = [];

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    class Particle {
      constructor() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 2 + 0.5;
        this.speedX = (Math.random() - 0.5) * 0.8;
        this.speedY = (Math.random() - 0.5) * 0.8;
        this.color = `rgba(${168 + Math.random() * 50}, 85, 247, ${Math.random() * 0.5 + 0.2})`;
      }
      update() {
        this.x += this.speedX;
        this.y += this.speedY;
        if (this.x > canvas.width) this.x = 0;
        if (this.x < 0) this.x = canvas.width;
        if (this.y > canvas.height) this.y = 0;
        if (this.y < 0) this.y = canvas.height;
      }
      draw() {
        ctx.fillStyle = this.color;
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    function initParticles() {
      particles = [];
      for (let i = 0; i < 90; i++) {
        particles.push(new Particle());
      }
    }

    function animateParticles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      particles.forEach(p => {
        p.update();
        p.draw();
      });
      requestAnimationFrame(animateParticles);
    }
    initParticles();
    animateParticles();

    // 3D Card Effect
    const card = document.getElementById('cardContainer');
    document.addEventListener('mousemove', (e) => {
      const xAxis = (window.innerWidth / 2 - e.pageX) / 30;
      const yAxis = (window.innerHeight / 2 - e.pageY) / 30;
      card.style.transform = `rotateY(${xAxis}deg) rotateX(${yAxis}deg)`;
    });

    // Login Logic & LocalStorage
    window.onload = () => {
      const auth = localStorage.getItem('academy_auth');
      const name = localStorage.getItem('academy_user');
      if (auth === 'true' && name) {
        showProfileUI(name);
      }
    };

    function executeLogin(e) {
      e.preventDefault();
      const username = document.getElementById('userInput').value;
      localStorage.setItem('academy_auth', 'true');
      localStorage.setItem('academy_user', username);
      showProfileUI(username);
    }

    function showProfileUI(name) {
      document.getElementById('loginForm').style.display = 'none';
      document.getElementById('profileBox').style.display = 'block';
      document.getElementById('displayUser').innerText = name;
      document.getElementById('userInitial').innerText = name.charAt(0).toUpperCase();
    }

    function executeLogout() {
      localStorage.removeItem('academy_auth');
      localStorage.removeItem('academy_user');
      location.reload();
    }
  </script>
</body>
</html>









