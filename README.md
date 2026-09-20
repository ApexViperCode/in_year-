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




<!-- خلفية النقاط المتحركة -->
<canvas id="particles-canvas"></canvas>





const canvas = document.getElementById('particles-canvas');
const ctx = canvas.getContext('2d');

let particlesArray = [];
const numberOfParticles = 80; // يمكنك زيادة أو تقليل عدد النقاط من هنا

// ضبط حجم الشاشة تلقائياً
function resizeCanvas() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
}
resizeCanvas();
window.addEventListener('resize', resizeCanvas);

// إنشاء كائن النقطة (Particle)
class Particle {
    constructor() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 2 + 1; // حجم النقطة
        this.speedX = (Math.random() - 0.5) * 1.2; // سرعة الحركة الأفقية
        this.speedY = (Math.random() - 0.5) * 1.2; // سرعة الحركة العمودية
        this.color = '#a855f7'; // لون النقاط (بنفسجي نيون)
    }

    // تحريك النقطة وإعادتها عند الاصطدام بالحواف
    update() {
        this.x += this.speedX;
        this.y += this.speedY;

        if (this.x > canvas.width || this.x < 0) this.speedX = -this.speedX;
        if (this.y > canvas.height || this.y < 0) this.speedY = -this.speedY;
    }

    // رسم النقطة
    draw() {
        ctx.fillStyle = this.color;
        ctx.shadowBlur = 8;
        ctx.shadowColor = '#a855f7'; // تأثير توهج حول كل نقطة
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fill();
    }
}

// تهيئة قائمة النقاط
function init() {
    particlesArray = [];
    for (let i = 0; i < numberOfParticles; i++) {
        particlesArray.push(new Particle());
    }
}

// رسم الخطوط المترابطة بين النقاط المتقاربة
function connect() {
    let maxDistance = 120; // أقصى مسافة لربط خط بين نقطتين
    for (let a = 0; a < particlesArray.length; a++) {
        for (let b = a; b < particlesArray.length; b++) {
            let dx = particlesArray[a].x - particlesArray[b].x;
            let dy = particlesArray[a].y - particlesArray[b].y;
            let distance = Math.sqrt(dx * dx + dy * dy);

            if (distance < maxDistance) {
                // حساب درجة شفافية الخط بناءً على القرب
                let opacity = 1 - (distance / maxDistance);
                ctx.strokeStyle = `rgba(168, 85, 247, ${opacity * 0.4})`; // لون الخط البنفسجي
                ctx.lineWidth = 1;
                ctx.beginPath();
                ctx.moveTo(particlesArray[a].x, particlesArray[a].y);
                ctx.lineTo(particlesArray[b].x, particlesArray[b].y);
                ctx.stroke();
            }
        }
    }
}

// حلقة التحريك (Animation Loop)
function animate() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    
    for (let i = 0; i < particlesArray.length; i++) {
        particlesArray[i].update();
        particlesArray[i].draw();
    }
    connect();
    requestAnimationFrame(animate);
}

init();
animate();








/* ضبط خلفية النقاط لتكون خلف جميع العناصر */
#particles-canvas {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: -1; /* تجعل Canvas خلف محتوى الموقع */
  background-color: #0d0a1a; /* لون الخلفية الداكن البنفسجي */
  pointer-events: none; /* لتفادي حجب النقرات عن أزرار الموقع */
}

