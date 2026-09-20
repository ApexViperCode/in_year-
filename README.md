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
    <title>IDEA ACADEMY | Future-Ready Coding Excellence</title>
    
    <!-- Google Fonts & Font Awesome Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;900&family=Rajdhani:wght@500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --bg-dark: #040208;
            --purple-glow: #a855f7;
            --purple-deep: #6b21a8;
            --cyber-cyan: #00f3ff;
            --glass-bg: rgba(18, 10, 28, 0.65);
            --border-glow: rgba(168, 85, 247, 0.35);
            --text-main: #f3f0ff;
            --text-muted: #94a3b8;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Rajdhani', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-main);
            overflow-x: hidden;
        }

        /* Dynamic Particle Canvas */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        /* Header Navigation */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 8%;
            background: rgba(4, 2, 8, 0.85);
            backdrop-filter: blur(15px);
            border-bottom: 1px solid var(--border-glow);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.8rem;
            font-weight: 900;
            color: #fff;
            letter-spacing: 2px;
            text-shadow: 0 0 15px var(--purple-glow);
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo i {
            color: var(--cyber-cyan);
            filter: drop-shadow(0 0 8px var(--cyber-cyan));
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 35px;
        }

        nav a {
            color: var(--text-main);
            text-decoration: none;
            font-weight: 700;
            font-size: 1.1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: 0.3s;
        }

        nav a:hover {
            color: var(--cyber-cyan);
            text-shadow: 0 0 10px var(--cyber-cyan);
        }

        /* Hero Section */
        .hero {
            display: grid;
            grid-template-columns: 1fr 1fr;
            min-height: calc(100vh - 80px);
            align-items: center;
            padding: 60px 8%;
            gap: 50px;
            perspective: 1200px;
        }

        .hero-content h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 3.5rem;
            line-height: 1.1;
            margin-bottom: 20px;
            background: linear-gradient(135deg, #fff 30%, var(--purple-glow), var(--cyber-cyan));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px rgba(168, 85, 247, 0.3);
        }

        .hero-content p {
            font-size: 1.25rem;
            color: var(--text-muted);
            line-height: 1.7;
            margin-bottom: 30px;
        }

        /* 3D Glass Sign-In Card */
        .card-wrapper {
            display: flex;
            justify-content: center;
            perspective: 1000px;
        }

        .login-card {
            background: var(--glass-bg);
            border: 2px solid var(--border-glow);
            border-radius: 24px;
            padding: 45px 35px;
            width: 100%;
            max-width: 420px;
            backdrop-filter: blur(20px);
            box-shadow: 0 20px 50px rgba(0,0,0,0.8), 0 0 30px rgba(168,85,247,0.25);
            transform-style: preserve-3d;
            transition: transform 0.1s ease-out, box-shadow 0.3s;
        }

        .login-card:hover {
            box-shadow: 0 25px 60px rgba(0,0,0,0.9), 0 0 50px var(--purple-glow), inset 0 0 20px rgba(0,243,255,0.2);
        }

        .login-card h2 {
            font-family: 'Orbitron', sans-serif;
            text-align: center;
            margin-bottom: 30px;
            color: #fff;
            transform: translateZ(40px);
            text-shadow: 0 0 12px var(--purple-glow);
        }

        .input-group {
            position: relative;
            margin-bottom: 22px;
            transform: translateZ(30px);
        }

        .input-group input {
            width: 100%;
            padding: 15px 15px 15px 45px;
            background: rgba(0, 0, 0, 0.6);
            border: 1px solid rgba(168, 85, 247, 0.4);
            outline: none;
            border-radius: 12px;
            color: #fff;
            font-size: 1rem;
            transition: 0.3s;
        }

        .input-group input:focus {
            border-color: var(--cyber-cyan);
            box-shadow: 0 0 15px var(--cyber-cyan);
        }

        .input-group i {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--purple-glow);
            font-size: 1.2rem;
        }

        .glow-btn {
            width: 100%;
            padding: 16px;
            border: none;
            border-radius: 12px;
            background: linear-gradient(90deg, var(--purple-deep), var(--purple-glow));
            color: #fff;
            font-family: 'Orbitron', sans-serif;
            font-size: 1rem;
            font-weight: 700;
            cursor: pointer;
            transform: translateZ(50px);
            transition: all 0.4s ease;
            box-shadow: 0 0 20px rgba(138, 43, 226, 0.6);
            letter-spacing: 1px;
        }

        .glow-btn:hover {
            background: linear-gradient(90deg, var(--cyber-cyan), var(--purple-glow));
            color: #000;
            box-shadow: 0 0 40px var(--cyber-cyan), 0 0 20px var(--purple-glow);
            transform: translateZ(60px) scale(1.02);
        }

        /* Stats Section */
        .stats-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            padding: 40px 8%;
            background: rgba(168, 85, 247, 0.05);
            border-y: 1px solid var(--border-glow);
            text-align: center;
        }

        .stat-box h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.8rem;
            color: var(--cyber-cyan);
            text-shadow: 0 0 15px var(--cyber-cyan);
        }

        .stat-box p {
            color: var(--text-muted);
            font-size: 1.1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* General Section Layout */
        .section-title {
            text-align: center;
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            margin-bottom: 60px;
            color: #fff;
            text-shadow: 0 0 20px var(--purple-glow);
        }

        /* Scroll Reveal Animation Utility */
        .reveal {
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease-out;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Tech Tracks Grid */
        .tracks-section {
            padding: 100px 8%;
        }

        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 35px;
        }

        .3d-card {
            background: var(--glass-bg);
            border: 1px solid var(--border-glow);
            border-radius: 20px;
            padding: 35px;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .3d-card:hover {
            transform: translateY(-12px) scale(1.02);
            border-color: var(--cyber-cyan);
            box-shadow: 0 15px 35px rgba(0, 243, 255, 0.2), 0 0 25px var(--purple-glow);
        }

        .card-icon {
            font-size: 3rem;
            color: var(--purple-glow);
            margin-bottom: 20px;
            transition: 0.3s;
        }

        .3d-card:hover .card-icon {
            color: var(--cyber-cyan);
            transform: scale(1.1) rotate(5deg);
            filter: drop-shadow(0 0 10px var(--cyber-cyan));
        }

        .3d-card h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5rem;
            margin-bottom: 12px;
        }

        .3d-card p {
            color: var(--text-muted);
            line-height: 1.6;
        }

        /* Code Showcase Interactive Section */
        .interactive-section {
            padding: 100px 8%;
            background: rgba(6, 3, 12, 0.8);
        }

        .code-window {
            background: #0d0814;
            border: 1px solid var(--border-glow);
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 0 40px rgba(168, 85, 247, 0.25);
        }

        .code-header {
            background: #170d24;
            padding: 15px 20px;
            display: flex;
            gap: 10px;
            align-items: center;
        }

        .dot { width: 12px; height: 12px; border-radius: 50%; }
        .dot-red { background: #ff5f56; }
        .dot-yellow { background: #ffbd2e; }
        .dot-green { background: #27c93f; }

        .code-content {
            padding: 30px;
            font-family: 'Courier New', Courier, monospace;
            color: var(--cyber-cyan);
            font-size: 1.1rem;
            line-height: 1.8;
            overflow-x: auto;
        }

        .code-keyword { color: var(--purple-glow); font-weight: bold; }
        .code-string { color: #f1fa8c; }

        /* Footer */
        footer {
            padding: 50px 8% 30px;
            background: #020104;
            border-top: 1px solid var(--border-glow);
            text-align: center;
            color: var(--text-muted);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin-bottom: 25px;
        }

        .social-links a {
            color: var(--text-main);
            font-size: 1.5rem;
            transition: 0.3s;
        }

        .social-links a:hover {
            color: var(--cyber-cyan);
            transform: translateY(-50%) scale(1.2);
            text-shadow: 0 0 15px var(--cyber-cyan);
        }

        /* Responsive */
        @media (max-width: 900px) {
            .hero { grid-template-columns: 1fr; text-align: center; }
            .hero-content h1 { font-size: 2.5rem; }
            nav { display: none; }
        }
    </style>
</head>
<body>

    <!-- Background Canvas -->
    <canvas id="bg-canvas"></canvas>

    <!-- Navigation Bar -->
    <header>
        <div class="logo">
            <i class="fa-solid fa-cube"></i> IDEA ACADEMY
        </div>
        <nav>
            <ul>
                <li><a href="#hero">Home</a></li>
                <li><a href="#tracks">Tracks</a></li>
                <li><a href="#code">Playground</a></li>
                <li><a href="#login">Sign In</a></li>
            </ul>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="hero">
        <div class="hero-content">
            <h1>DOMINATE THE DIGITAL REALM</h1>
            <p>Welcome to <strong>Idea Academy</strong> — the ultimate launchpad for elite developers. Master modern Web Development, C++, algorithm optimization, and software architecture using next-gen interactive tools.</p>
            <button class="glow-btn" style="width: auto; padding: 18px 40px;" onclick="document.getElementById('tracks').scrollIntoView();">
                EXPLORE COURSES <i class="fa-solid fa-arrow-right"></i>
            </button>
        </div>

        <div class="card-wrapper" id="login">
            <div class="login-card" id="tiltCard">
                <h2>ACADEMY ACCESS</h2>
                <form onsubmit="event.preventDefault();">
                    <div class="input-group">
                        <i class="fa-solid fa-user"></i>
                        <input type="text" placeholder="Username / Student ID" required>
                    </div>
                    <div class="input-group">
                        <i class="fa-solid fa-lock"></i>
                        <input type="password" placeholder="Password" required>
                    </div>
                    <button type="submit" class="glow-btn">
                        INITIALIZE SESSION <i class="fa-solid fa-bolt"></i>
                    </button>
                </form>
            </div>
        </div>
    </section>

    <!-- Live Counter Section -->
    <div class="stats-section">
        <div class="stat-box">
            <h3><span class="counter" data-target="1500">0</span>+</h3>
            <p>Active Students</p>
        </div>
        <div class="stat-box">
            <h3><span class="counter" data-target="45">0</span>+</h3>
            <p>Pro Modules</p>
        </div>
        <div class="stat-box">
            <h3><span class="counter" data-target="99">0</span>%</h3>
            <p>Satisfaction</p>
        </div>
    </div>

    <!-- Learning Tracks Section -->
    <section class="tracks-section" id="tracks">
        <h2 class="section-title reveal">ELITE LEARNING TRACKS</h2>
        <div class="grid-container">
            <div class="3d-card reveal">
                <i class="fa-brands fa-html5 card-icon"></i>
                <h3>HTML5 & Modern DOM</h3>
                <p>Learn semantic structuring, dynamic DOM manipulation, and modern web standards from the ground up.</p>
            </div>

            <div class="3d-card reveal">
                <i class="fa-brands fa-css3-alt card-icon"></i>
                <h3>Advanced CSS3 & 3D</h3>
                <p>Master Flexbox, CSS Grid, 3D Canvas Transforms, Glassmorphism, and custom Neon animations.</p>
            </div>

            <div class="3d-card reveal">
                <i class="fa-brands fa-js card-icon"></i>
                <h3>JavaScript ES6+</h3>
                <p>Unlock asynchronous programming, dynamic canvas particle engines, and modern JS frameworks.</p>
            </div>

            <div class="3d-card reveal">
                <i class="fa-solid fa-code card-icon"></i>
                <h3>C++ System Programming</h3>
                <p>Deep dive into object-oriented design, memory management, data structures, and game algorithms.</p>
            </div>

            <div class="3d-card reveal">
                <i class="fa-brands fa-github card-icon"></i>
                <h3>Git & GitHub Mastery</h3>
                <p>Manage codebases like a pro, collaborate with open-source workflows, and deploy live repositories.</p>
            </div>

            <div class="3d-card reveal">
                <i class="fa-solid fa-laptop-code card-icon"></i>
                <h3>Full-Stack Architecture</h3>
                <p>Combine frontend designs with backend efficiency to create scalable modern web applications.</p>
            </div>
        </div>
    </section>

    <!-- Interactive Code Showcase Section -->
    <section class="interactive-section reveal" id="code">
        <h2 class="section-title">THE ARCHITECTURE OF IDEAS</h2>
        <div class="code-window">
            <div class="code-header">
                <div class="dot dot-red"></div>
                <div class="dot dot-yellow"></div>
                <div class="dot dot-green"></div>
                <span style="color: var(--text-muted); font-size: 0.9rem; margin-left: 10px;">IdeaAcademy.cpp</span>
            </div>
            <div class="code-content">
                <p><span class="code-keyword">#include</span> &lt;iostream&gt;</p>
                <p><span class="code-keyword">using namespace</span> std;</p>
                <br>
                <p><span class="code-keyword">int</span> main() {</p>
                <p style="padding-left: 20px;"><span class="code-keyword">string</span> academy = <span class="code-string">"Idea Academy"</span>;</p>
                <p style="padding-left: 20px;">cout &lt;&lt; <span class="code-string">"Unlocking potential at "</span> &lt;&lt; academy &lt;&lt; endl;</p>
                <p style="padding-left: 20px;"><span class="code-keyword">return</span> 0;</p>
                <p>}</p>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="social-links">
            <a href="#"><i class="fa-brands fa-github"></i></a>
            <a href="#"><i class="fa-brands fa-discord"></i></a>
            <a href="#"><i class="fa-brands fa-youtube"></i></a>
        </div>
        <p>&copy; 2026 Idea Academy. Engineered for Greatness.</p>
    </footer>

    <!-- JavaScript Interactions -->
    <script>
        // 1. 3D Tilt Card Effect
        const card = document.getElementById('tiltCard');
        const wrapper = document.querySelector('.card-wrapper');

        wrapper.addEventListener('mousemove', (e) => {
            const rect = wrapper.getBoundingClientRect();
            const x = e.clientX - rect.left - rect.width / 2;
            const y = e.clientY - rect.top - rect.height / 2;

            card.style.transform = `rotateX(${-y / 10}deg) rotateY(${x / 10}deg)`;
        });

        wrapper.addEventListener('mouseleave', () => {
            card.style.transform = 'rotateX(0deg) rotateY(0deg)';
        });

        // 2. Scroll Reveal Animation
        window.addEventListener('scroll', revealOnScroll);

        function revealOnScroll() {
            const reveals = document.querySelectorAll('.reveal');
            for (let i = 0; i < reveals.length; i++) {
                const windowHeight = window.innerHeight;
                const elementTop = reveals[i].getBoundingClientRect().top;
                const elementVisible = 150;

                if (elementTop < windowHeight - elementVisible) {
                    reveals[i].classList.add('active');
                }
            }
        }
        revealOnScroll();

        // 3. Counter Animation
        const counters = document.querySelectorAll('.counter');
        let counterStarted = false;

        window.addEventListener('scroll', () => {
            const statsSection = document.querySelector('.stats-section');
            const position = statsSection.getBoundingClientRect().top;
            if(position < window.innerHeight && !counterStarted) {
                counterStarted = true;
                counters.forEach(counter => {
                    const target = +counter.getAttribute('data-target');
                    let count = 0;
                    const speed = target / 50;
                    const updateCount = () => {
                        count += speed;
                        if(count < target) {
                            counter.innerText = Math.ceil(count);
                            setTimeout(updateCount, 30);
                        } else {
                            counter.innerText = target;
                        }
                    };
                    updateCount();
                });
            }
        });

        // 4. Particle Background Engine
        const canvas = document.getElementById('bg-canvas');
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
                this.speedX = (Math.random() - 0.5) * 0.6;
                this.speedY = (Math.random() - 0.5) * 0.6;
                this.color = Math.random() > 0.5 ? '#a855f7' : '#00f3ff';
            }

            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                if (this.x < 0 || this.x > canvas.width) this.speedX *= -1;
                if (this.y < 0 || this.y > canvas.height) this.speedY *= -1;
            }

            draw() {
                ctx.fillStyle = this.color;
                ctx.shadowBlur = 10;
                ctx.shadowColor = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        for (let i = 0; i < 80; i++) particles.push(new Particle());

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => { p.update(); p.draw(); });
            requestAnimationFrame(animate);
        }
        animate();
    </script>
</body>
</html>
