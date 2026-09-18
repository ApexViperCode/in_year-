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
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>Tech Stack Tooltip</title>
  <style>
    body {
      background-color: #0b0f19; /* خلفية داكنة مثل الصورة */
      color: #fff;
      font-family: sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      margin: 0;
    }

    .tech-stack-title {
      font-size: 14px;
      letter-spacing: 2px;
      color: #38bdf8;
      text-transform: uppercase;
      margin-bottom: 20px;
    }

    /* الحاوية الرئيسية للأيقونات */
    .tech-stack-container {
      display: flex;
      gap: 15px;
      flex-wrap: wrap;
    }

    /* كرت الأيقونة */
    .tech-card {
      position: relative;
      width: 60px;
      height: 60px;
      background-color: #1e293b;
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    /* صورة الأيقونة داخل الكرت */
    .tech-card img {
      width: 32px;
      height: 32px;
      /* إزالة الألوان وإضعاف الشفافية افتراضياً */
      filter: grayscale(100%) brightness(0.8);
      opacity: 0.6;
      transition: all 0.3s ease;
    }

    /* النص الذي يظهر أسفل الأيقونة (Tooltip) */
    .tech-card .tooltip {
      position: absolute;
      bottom: -30px; /* موقع النص تحت الكرت */
      background-color: #0f172a;
      color: #e2e8f0;
      font-size: 11px;
      padding: 4px 8px;
      border-radius: 6px;
      white-space: nowrap;
      opacity: 0; /* مخفي افتراضياً */
      visibility: hidden;
      transform: translateY(-5px);
      transition: all 0.3s ease;
      border: 1px solid #334155;
      pointer-events: none;
    }

    /* ---- التأثيرات عند وضع الماوس (Hover) ---- */

    /* 1. إظهار لون الأيقونة وإضاءتها */
    .tech-card:hover img {
      filter: grayscale(0%) brightness(1);
      opacity: 1;
      transform: scale(1.1); /* تكبير بسيط للأيقونة */
    }

    /* 2. تغيير خلفية الكرت عند الـ Hover */
    .tech-card:hover {
      background-color: #334155;
    }

    /* 3. إظهار اسم التقنية */
    .tech-card:hover .tooltip {
      opacity: 1;
      visibility: visible;
      transform: translateY(0);
    }
  </style>
</head>
<body>

  <div class="tech-stack-title">TECH STACK</div>

  <div class="tech-stack-container">
    <!-- بايثون -->
    <div class="tech-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python">
      <span class="tooltip">Python</span>
    </div>

    <!-- رياكت -->
    <div class="tech-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="React">
      <span class="tooltip">React</span>
    </div>

    <!-- نود جيه اس -->
    <div class="tech-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" alt="Node.js">
      <span class="tooltip">Node.js</span>
    </div>

    <!-- فيجما -->
    <div class="tech-card">
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" alt="Figma">
      <span class="tooltip">Figma</span>
    </div>
  </div>

</body>
</html>
