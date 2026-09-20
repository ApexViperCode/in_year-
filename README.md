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
    <title>IDEA ACADEMY | Next-Gen Programming & Development Hub</title>
    
    <!-- Google Fonts & Font Awesome -->
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;800;900&family=Rajdhani:wght@500;600;700&family=Fira+Code:wght@400;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --bg-main: #030107;
            --bg-card: rgba(15, 8, 25, 0.7);
            --purple-glow: #a855f7;
            --purple-dark: #581c87;
            --cyber-cyan: #00f3ff;
            --neon-pink: #ff007f;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --border-glow: rgba(168, 85, 247, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Rajdhani', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-main);
            overflow-x: hidden;
        }

        /* Particle Canvas */
        #particle-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        /* Navigation Header */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 8%;
            background: rgba(3, 1, 7, 0.85);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--border-glow);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.8rem;
            font-weight: 900;
            letter-spacing: 2px;
            color: #fff;
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
            gap: 30px;
        }

        nav a {
            color: var(--text-main);
            text-decoration: none;
            font-weight: 700;
            font-size: 1rem;
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

        .hero-text h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 3.5rem;
            line-height: 1.1;
            margin-bottom: 20px;
            background: linear-gradient(135deg, #fff 20%, var(--purple-glow), var(--cyber-cyan));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px rgba(168, 85, 247, 0.4);
        }

        .hero-text p {
            font-size: 1.25rem;
            color: var(--text-muted);
            line-height: 1.7;
            margin-bottom: 30px;
        }

        /* 3D Glass Sign-In Portal */
        .portal-wrapper {
            display: flex;
            justify-content: center;
            perspective: 1000px;
        }

        .portal-card {
            background: var(--bg-card);
            border: 2px solid var(--border-glow);
            border-radius: 24px;
            padding: 40px;
            width: 100%;
            max-width: 440px;
            backdrop-filter: blur(20px);
            box-shadow: 0 20px 50px rgba(0,0,0,0.9), 0 0 30px rgba(168,85,247,0.3);
            transform-style: preserve-3d;
            transition: transform 0.1s ease-out, box-shadow 0.3s;
        }

        .portal-card:hover {
            box-shadow: 0 25px 60px rgba(0,0,0,0.9), 0 0 50px var(--purple-glow), inset 0 0 20px rgba(0,243,255,0.2);
        }

        .portal-card h2 {
            font-family: 'Orbitron', sans-serif;
            text-align: center;
            margin-bottom: 25px;
            color: #fff;
            transform: translateZ(40px);
            text-shadow: 0 0 12px var(--purple-glow);
        }

        .input-group {
            position: relative;
            margin-bottom: 20px;
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
            background: linear-gradient(90deg, var(--purple-dark), var(--purple-glow));
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

        /* Stats Counters */
        .stats-bar {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            padding: 50px 8%;
            background: rgba(168, 85, 247, 0.03);
            border-y: 1px solid var(--border-glow);
            text-align: center;
        }

        .stat-card h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 3rem;
            color: var(--cyber-cyan);
            text-shadow: 0 0 15px var(--cyber-cyan);
        }

        .stat-card p {
            color: var(--text-muted);
            font-size: 1.1rem;
            text-transform: uppercase;
        }

        /* Section Layout Utility */
        section {
            padding: 100px 8%;
        }

        .section-title {
            text-align: center;
            font-family: 'Orbitron', sans-serif;
            font-size: 2.8rem;
            margin-bottom: 60px;
            color: #fff;
            text-shadow: 0 0 20px var(--purple-glow);
        }

        /* Scroll Animations */
        .reveal {
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease-out;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Track Grid & 3D Cards */
        .grid-3d {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 35px;
        }

        .card-3d {
            background: var(--bg-card);
            border: 1px solid var(--border-glow);
            border-radius: 20px;
            padding: 40px 30px;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .card-3d:hover {
            transform: translateY(-12px) scale(1.02);
            border-color: var(--cyber-cyan);
            box-shadow: 0 20px 40px rgba(0, 243, 255, 0.2), 0 0 30px var(--purple-glow);
        }

        .card-icon {
            font-size: 3.5rem;
            color: var(--purple-glow);
            margin-bottom: 20px;
            transition: 0.3s;
        }

        .card-3d:hover .card-icon {
            color: var(--cyber-cyan);
            transform: scale(1.1) rotate(5deg);
            filter: drop-shadow(0 0 10px var(--cyber-cyan));
        }

        .card-3d h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.6rem;
            margin-bottom: 15px;
        }

        .card-3d p {
            color: var(--text-muted);
            line-height: 1.7;
        }

        /* Terminal Simulator */
        .terminal-box {
            background: #080312;
            border: 1px solid var(--border-glow);
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 0 50px rgba(168, 85, 247, 0.2);
            max-width: 900px;
            margin: 0 auto;
        }

        .terminal-header {
            background: #140924;
            padding: 15px 20px;
            display: flex;
            gap: 10px;
            align-items: center;
        }

        .dot { width: 12px; height: 12px; border-radius: 50%; }
        .red { background: #ff5f56; }
        .yellow { background: #ffbd2e; }
        .green { background: #27c93f; }

        .terminal-body {
            padding: 30px;
            font-family: 'Fira Code', monospace;
            color: var(--cyber-cyan);
            font-size: 1.05rem;
            line-height: 1.8;
        }

        .prompt { color: var(--neon-pink); }
        .keyword { color: var(--purple-glow); font-weight: bold; }

        /* Timeline History Roadmap */
        .timeline {
            position: relative;
            max-width: 1000px;
            margin: 0 auto;
        }

        .timeline::after {
            content: '';
            position: absolute;
            width: 4px;
            background: var(--purple-glow);
            top: 0;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            box-shadow: 0 0 15px var(--purple-glow);
        }

        .timeline-item {
            padding: 20px 40px;
            position: relative;
            width: 50%;
        }

        .timeline-item.left { left: 0; text-align: right; }
        .timeline-item.right { left: 50%; }

        .timeline-content {
            padding: 30px;
            background: var(--bg-card);
            border: 1px solid var(--border-glow);
            border-radius: 16px;
        }

        /* Interactive Quiz Box */
        .quiz-container {
            max-width: 700px;
            margin: 0 auto;
            background: var(--bg-card);
            border: 1px solid var(--border-glow);
            border-radius: 20px;
            padding: 40px;
            text-align: center;
        }

        .quiz-option {
            display: block;
            width: 100%;
            padding: 15px;
            margin: 15px 0;
            background: rgba(0,0,0,0.5);
            border: 1px solid var(--border-glow);
            border-radius: 12px;
            color: #fff;
            cursor: pointer;
            font-size: 1.1rem;
            transition: 0.3s;
        }

        .quiz-option:hover {
            border-color: var(--cyber-cyan);
            background: rgba(0, 243, 255, 0.1);
        }

        /* Footer */
        footer {
            padding: 60px 8% 30px;
            background: #020005;
            border-top: 1px solid var(--border-glow);
            text-align: center;
        }

        .social-icons {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin-bottom: 25px;
        }

        .social-icons a {
            color: var(--text-main);
            font-size: 1.8rem;
            transition: 0.3s;
        }

        .social-icons a:hover {
            color: var(--cyber-cyan);
            transform: scale(1.2);
            text-shadow: 0 0 15px var(--cyber-cyan);
        }

        @media (max-width: 900px) {
            .hero { grid-template-columns: 1fr; text-align: center; }
            .hero-text h1 { font-size: 2.5rem; }
            .timeline::after { left: 31px; }
            .timeline-item { width: 100%; padding-left: 70px; padding-right: 25px; }
            .timeline-item.right { left: 0%; }
            .timeline-item.left { text-align: left; }
            nav { display: none; }
        }
    </style>
</head>
<body>

    <canvas id="particle-canvas"></canvas>

    <!-- Header -->
    <header>
        <div class="logo">
            <i class="fa-solid fa-microchip"></i> IDEA ACADEMY
        </div>
        <nav>
            <ul>
                <li><a href="#hero">Home</a></li>
                <li><a href="#tracks">Tracks</a></li>
                <li><a href="#terminal">Terminal</a></li>
                <li><a href="#roadmap">Roadmap</a></li>
                <li><a href="#quiz">Quiz</a></li>
                <li><a href="#portal">Portal</a></li>
            </ul>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="hero">
        <div class="hero-text">
            <h1>ARCHITECT THE FUTURE OF CODE</h1>
            <p>Welcome to <strong>Idea Academy</strong>. Master C++, Web Architecture, Algorithms, and System Optimization with high-level 3D interactives and professional guidance.</p>
            <button class="glow-btn" style="width: auto; padding: 18px 40px;" onclick="document.getElementById('tracks').scrollIntoView();">
                START LEARNING NOW <i class="fa-solid fa-rocket"></i>
            </button>
        </div>

        <div class="portal-wrapper" id="portal">
            <div class="portal-card" id="tiltCard">
                <h2>STUDENT ACCESS</h2>
                <form onsubmit="event.preventDefault(); alert('Authentication System Ready!');">
                    <div class="input-group">
                        <i class="fa-solid fa-user-astronaut"></i>
                        <input type="text" placeholder="Username / Student ID" required>
                    </div>
                    <div class="input-group">
                        <i class="fa-solid fa-key"></i>
                        <input type="password" placeholder="Passcode" required>
                    </div>
                    <button type="submit" class="glow-btn">
                        AUTHORIZE <i class="fa-solid fa-shield-halved"></i>
                    </button>
                </form>
            </div>
        </div>
    </section>

    <!-- Live Counter Bar -->
    <div class="stats-bar">
        <div class="stat-card">
            <h3><span class="counter" data-target="2500">0</span>+</h3>
            <p>Active Coders</p>
        </div>
        <div class="stat-card">
            <h3><span class="counter" data-target="60">0</span>+</h3>
            <p>Advanced Modules</p>
        </div>
        <div class="stat-card">
            <h3><span class="counter" data-target="99">0</span>%</h3>
            <p>Success Rate</p>
        </div>
    </div>

    <!-- Tracks Section -->
    <section id="tracks">
        <h2 class="section-title reveal">CORE CURRICULUM TRACKS</h2>
        <div class="grid-3d">
            <div class="card-3d reveal">
                <i class="fa-brands fa-html5 card-icon"></i>
                <h3>HTML5 Semantic Architecture</h3>
                <p>Build robust web skeletons, master DOM structures, and integrate modern accessibility standards.</p>
            </div>

            <div class="card-3d reveal">
                <i class="fa-brands fa-css3-alt card-icon"></i>
                <h3>CSS3 Glassmorphism & 3D</h3>
                <p>Construct deep 3D user interfaces, CSS Grid layouts, and high-performance GPU animations.</p>
            </div>

            <div class="card-3d reveal">
                <i class="fa-brands fa-js card-icon"></i>
                <h3>JavaScript ES6+ Engines</h3>
                <p>Master async programming, closures, Canvas APIs, and real-time interactive web graphics.</p>
            </div>

            <div class="card-3d reveal">
                <i class="fa-solid fa-code card-icon"></i>
                <h3>C++ High Performance</h3>
                <p>Deep dive into object-oriented programming, manual memory management, and game engines.</p>
            </div>

            <div class="card-3d reveal">
                <i class="fa-brands fa-github card-icon"></i>
                <h3>Git & Version Control</h3>
                <p>Manage code repositories, branching models, pull requests, and multi-developer collaboration.</p>
            </div>

            <div class="card-3d reveal">
                <i class="fa-solid fa-network-wired card-icon"></i>
                <h3>Full-Stack Engineering</h3>
                <p>Bridge client-side graphics with backend database management for full web deployments.</p>
            </div>
        </div>
    </section>

    <!-- Live Terminal Playground -->
    <section id="terminal" class="reveal">
        <h2 class="section-title">IDE TERMINAL ENGINE</h2>
        <div class="terminal-box">
            <div class="terminal-header">
                <div class="dot red"></div>
                <div class="dot yellow"></div>
                <div class="dot green"></div>
                <span style="color: var(--text-muted); font-size: 0.85rem; margin-left: 10px;">IdeaAcademy_Engine.cpp</span>
            </div>
            <div class="terminal-body">
                <p><span class="prompt">guest@idea-academy:~$</span> g++ -o main IdeaAcademy.cpp</p>
                <p><span class="prompt">guest@idea-academy:~$</span> ./main</p>
                <br>
                <p><span class="keyword">[SYSTEM OK]</span> Loading Idea Academy Core Modules...</p>
                <p><span class="keyword">[MODULES]</span> C++, HTML5, CSS3, JS Engine Linked Successfully.</p>
                <p style="color: #27c93f;">> Ready to execute developer journey...</p>
            </div>
        </div>
    </section>

    <!-- Roadmap Timeline -->
    <section id="roadmap">
        <h2 class="section-title reveal">ACADEMY ROADMAP</h2>
        <div class="timeline">
            <div class="timeline-item left reveal">
                <div class="timeline-content">
                    <h3>STAGE 01: Foundations</h3>
                    <p>Mastering HTML5 semantic tags, basic CSS styling, and fundamental algorithm logic in C++.</p>
                </div>
            </div>
            <div class="timeline-item right reveal">
                <div class="timeline-content">
                    <h3>STAGE 02: Interactive UI</h3>
                    <p>Building responsive web layouts, 3D CSS transformations, and DOM manipulation using JavaScript.</p>
                </div>
            </div>
            <div class="timeline-item left reveal">
                <div class="timeline-content">
                    <h3>STAGE 03: Advanced Systems</h3>
                    <p>C++ Object-Oriented design, memory pointers, dynamic arrays, and version control via GitHub.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Interactive Knowledge Quiz -->
    <section id="quiz" class="reveal">
        <h2 class="section-title">TEST YOUR KNOWLEDGE</h2>
        <div class="quiz-container">
            <h3 id="quiz-question" style="margin-bottom: 20px;">Which C++ keyword is used to allocate dynamic memory?</h3>
            <button class="quiz-option" onclick="checkAnswer(false)">alloc</button>
            <button class="quiz-option" onclick="checkAnswer(true)">new</button>
            <button class="quiz-option" onclick="checkAnswer(false)">malloc_cpp</button>
            <p id="quiz-result" style="margin-top: 15px; font-weight: bold;"></p>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="social-icons">
            <a href="#"><i class="fa-brands fa-github"></i></a>
            <a href="#"><i class="fa-brands fa-discord"></i></a>
            <a href="#"><i class="fa-brands fa-youtube"></i></a>
        </div>
        <p>&copy; 2026 Idea Academy. Built for Future Software Engineers.</p>
    </footer>

    <!-- JavaScript Scripts -->
    <script>
        // 1. 3D Tilt Portal
        const card = document.getElementById('tiltCard');
        const wrapper = document.querySelector('.portal-wrapper');

        wrapper.addEventListener('mousemove', (e) => {
            const rect = wrapper.getBoundingClientRect();
            const x = e.clientX - rect.left - rect.width / 2;
            const y = e.clientY - rect.top - rect.height / 2;
            card.style.transform = `rotateX(${-y / 10}deg) rotateY(${x / 10}deg)`;
        });

        wrapper.addEventListener('mouseleave', () => {
            card.style.transform = 'rotateX(0deg) rotateY(0deg)';
        });

        // 2. Scroll Reveal Animations
        window.addEventListener('scroll', () => {
            document.querySelectorAll('.reveal').forEach(el => {
                if (el.getBoundingClientRect().top < window.innerHeight - 100) {
                    el.classList.add('active');
                }
            });
        });

        // 3. Counter Animation
        let started = false;
        window.addEventListener('scroll', () => {
            const bar = document.querySelector('.stats-bar');
            if (bar.getBoundingClientRect().top < window.innerHeight && !started) {
                started = true;
                document.querySelectorAll('.counter').forEach(c => {
                    const target = +c.getAttribute('data-target');
                    let count = 0;
                    const update = () => {
                        count += target / 40;
                        if (count < target) {
                            c.innerText = Math.ceil(count);
                            setTimeout(update, 30);
                        } else {
                            c.innerText = target;
                        }
                    };
                    update();
                });
            }
        });

        // 4. Interactive Quiz Logic
        function checkAnswer(correct) {
            const result = document.getElementById('quiz-result');
            if (correct) {
                result.style.color = '#00f3ff';
                result.innerText = 'Correct! "new" is used for dynamic allocation in C++.';
            } else {
                result.style.color = '#ff007f';
                result.innerText = 'Incorrect. Try again!';
            }
        }

        // 5. Background Particle Engine
        const canvas = document.getElementById('particle-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function resize() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resize);
        resize();

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2 + 0.5;
                this.speedX = (Math.random() - 0.5) * 0.5;
                this.speedY = (Math.random() - 0.5) * 0.5;
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
                ctx.shadowBlur = 8;
                ctx.shadowColor = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        for (let i = 0; i < 75; i++) particles.push(new Particle());

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => { p.update(); p.draw(); });
            requestAnimationFrame(animate);
        }
        animate();
    </script>
</body>
</html>
