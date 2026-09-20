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
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Idea Academy | عالم البرمجة الاحترافي</title>
    <!-- Google Fonts & Font Awesome Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary-purple: #8a2be2;
            --neon-glow: #a855f7;
            --cyber-blue: #00f3ff;
            --dark-bg: #06040a;
            --card-bg: rgba(18, 10, 28, 0.65);
            --text-light: #f3f0ff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Tajawal', sans-serif;
        }

        body {
            background-color: var(--dark-bg);
            color: var(--text-light);
            overflow-x: hidden;
            min-height: 100vh;
        }

        /* خلفية النجوم والتأثيرات الفضائية */
        #canvas-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        /* القائمة العلويّة */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 8%;
            background: rgba(6, 4, 10, 0.8);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(168, 85, 247, 0.2);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 900;
            color: #fff;
            text-shadow: 0 0 10px var(--neon-glow);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo i {
            color: var(--cyber-blue);
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        nav a {
            color: var(--text-light);
            text-decoration: none;
            font-weight: 700;
            transition: all 0.3s ease;
        }

        nav a:hover {
            color: var(--cyber-blue);
            text-shadow: 0 0 8px var(--cyber-blue);
        }

        /* الحاوية الرئيسية */
        .container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            min-height: calc(100vh - 80px);
            align-items: center;
            padding: 40px 8%;
            gap: 50px;
            perspective: 1000px;
        }

        /* قسم التعريف بالأكاديمية */
        .hero-text {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .hero-text h1 {
            font-size: 3.2rem;
            font-weight: 900;
            line-height: 1.2;
            background: linear-gradient(135deg, #fff, var(--neon-glow), var(--cyber-blue));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px rgba(168, 85, 247, 0.3);
        }

        .hero-text p {
            font-size: 1.2rem;
            line-height: 1.8;
            color: #cbd5e1;
        }

        /* شبكة اللغات والتقنيات */
        .tech-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-top: 10px;
        }

        .tag {
            background: rgba(138, 43, 226, 0.15);
            border: 1px solid var(--neon-glow);
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.95rem;
            font-weight: bold;
            box-shadow: 0 0 10px rgba(168, 85, 247, 0.2);
            transition: 0.3s;
        }

        .tag:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 0 20px var(--neon-glow);
            background: var(--neon-glow);
            color: #000;
        }

        /* بطاقة تسجيل الدخول 3D Ultra Card */
        .card-wrapper {
            display: flex;
            justify-content: center;
            align-items: center;
            perspective: 1000px;
        }

        .login-card {
            background: var(--card-bg);
            border: 2px solid rgba(168, 85, 247, 0.4);
            border-radius: 24px;
            padding: 40px;
            width: 100%;
            max-width: 440px;
            backdrop-filter: blur(16px);
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.8),
                        0 0 30px rgba(138, 43, 226, 0.3),
                        inset 0 0 15px rgba(168, 85, 247, 0.2);
            transform-style: preserve-3d;
            transition: transform 0.1s ease-out, box-shadow 0.3s;
            position: relative;
        }

        .login-card:hover {
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.9),
                        0 0 45px var(--neon-glow),
                        inset 0 0 20px rgba(0, 243, 255, 0.3);
        }

        .login-card h2 {
            font-size: 2rem;
            text-align: center;
            margin-bottom: 30px;
            color: #fff;
            transform: translateZ(40px);
            text-shadow: 0 0 10px var(--neon-glow);
        }

        .input-box {
            position: relative;
            margin-bottom: 25px;
            transform: translateZ(30px);
        }

        .input-box input {
            width: 100%;
            padding: 14px 45px 14px 15px;
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(168, 85, 247, 0.4);
            outline: none;
            border-radius: 12px;
            color: #fff;
            font-size: 1rem;
            transition: 0.3s;
        }

        .input-box input:focus {
            border-color: var(--cyber-blue);
            box-shadow: 0 0 15px var(--cyber-blue);
        }

        .input-box i {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--neon-glow);
            font-size: 1.2rem;
        }

        /* زر الإضاءة الحارق الضوئي الاحترافي (Neon Glow Button) */
        .glow-btn {
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 12px;
            background: linear-gradient(90deg, var(--primary-purple), var(--neon-glow));
            color: #fff;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transform: translateZ(50px);
            transition: all 0.4s ease-in-out;
            box-shadow: 0 0 15px rgba(138, 43, 226, 0.6);
            position: relative;
            overflow: hidden;
        }

        .glow-btn:hover {
            background: linear-gradient(90deg, var(--cyber-blue), var(--neon-glow));
            color: #000;
            box-shadow: 0 0 35px var(--cyber-blue), 0 0 15px var(--neon-glow);
            transform: translateZ(60px) scale(1.03);
        }

        .glow-btn::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: rgba(255, 255, 255, 0.2);
            transform: rotate(45deg) translateY(-100%);
            transition: all 0.6s ease;
        }

        .glow-btn:hover::after {
            transform: rotate(45deg) translateY(100%);
        }

        /* responsive design */
        @media (max-width: 900px) {
            .container {
                grid-template-columns: 1fr;
                text-align: center;
            }
            .hero-text h1 {
                font-size: 2.2rem;
            }
            .tech-tags {
                justify-content: center;
            }
        }
    </style>
</head>
<body>

    <!-- خلفية النجوم المتحركة -->
    <canvas id="canvas-bg"></canvas>

    <!-- شريط التنقل العلوي -->
    <header>
        <div class="logo">
            <i class="fa-solid fa-code"></i> IDEA ACADEMY
        </div>
        <nav>
            <ul>
                <li><a href="#">الرئيسية</a></li>
                <li><a href="#">المسارات</a></li>
                <li><a href="#">المشاريع</a></li>
            </ul>
        </nav>
    </header>

    <!-- محتوى الصفحة الرئيسي -->
    <div class="container">
        <!-- قسم النص التعريفي -->
        <div class="hero-text">
            <h1>اكتسح عالم البرمجة والتطوير الاحترافي</h1>
            <p>
                مرحباً بك في <strong>Idea Academy</strong>، الأكاديمية الرائدة لتجهيز مبرمجي المستقبل! نقدم لك أحدث المناهج لتعلم لغات البرمجة وتطوير المواقع والتطبيقات والألعاب باستخدام أدوات وتقنيات احترافية حديثة.
            </p>
            <div class="tech-tags">
                <span class="tag"><i class="fa-brands fa-html5"></i> HTML5</span>
                <span class="tag"><i class="fa-brands fa-css3-alt"></i> CSS3</span>
                <span class="tag"><i class="fa-brands fa-js"></i> JavaScript</span>
                <span class="tag"><i class="fa-solid fa-code"></i> C++</span>
                <span class="tag"><i class="fa-brands fa-github"></i> Git & GitHub</span>
            </div>
        </div>

        <!-- كرت تسجيل الدخول ثلاثي الأبعاد 3D Card -->
        <div class="card-wrapper">
            <div class="login-card" id="card3d">
                <h2>تسجيل الدخول</h2>
                <form onsubmit="event.preventDefault();">
                    <div class="input-box">
                        <i class="fa-solid fa-user"></i>
                        <input type="text" placeholder="اسم المستخدم" required>
                    </div>
                    <div class="input-box">
                        <i class="fa-solid fa-lock"></i>
                        <input type="password" placeholder="كلمة المرور" required>
                    </div>
                    <button type="submit" class="glow-btn">
                        دخول للأكاديمية <i class="fa-solid fa-bolt"></i>
                    </button>
                </form>
            </div>
        </div>
    </div>

    <!-- السكريبتات للتأثيرات والتفاعل -->
    <script>
        // 1. حركة الكرت ثلاثي الأبعاد 3D Tilt Effect عند تحريك الماوس
        const card = document.getElementById('card3d');
        const wrapper = document.querySelector('.card-wrapper');

        wrapper.addEventListener('mousemove', (e) => {
            const rect = wrapper.getBoundingClientRect();
            const x = e.clientX - rect.left - rect.width / 2;
            const y = e.clientY - rect.top - rect.height / 2;

            const rotateX = (-y / 12).toFixed(2);
            const rotateY = (x / 12).toFixed(2);

            card.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
        });

        wrapper.addEventListener('mouseleave', () => {
            card.style.transform = 'rotateX(0deg) rotateY(0deg)';
        });

        // 2. خلفية النجوم المتحركة المتفاعلة (Canvas Dynamic Particles)
        const canvas = document.getElementById('canvas-bg');
        const ctx = canvas.getContext('2d');

        let particles = [];
        const particleCount = 70;

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
                ctx.shadowBlur = 10;
                ctx.shadowColor = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function initParticles() {
            particles = [];
            for (let i = 0; i < particleCount; i++) {
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
    </script>
</body>
</html>
