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
  <title>GitHub Style Projects</title>
  <style>
    body {
      background-color: #0d1117;
      color: #c9d1d9;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      padding: 40px;
    }

    .section-title {
      font-size: 20px;
      font-weight: 600;
      color: #f0f6fc;
      margin-bottom: 16px;
    }

    /* شبكة المشاريع: 3 أعمدة متساوية */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr); /* 3 أعمدة بالسطر الواحد */
      gap: 16px; /* التباعد المتساوي بين البطاقات */
    }

    /* كرت المشروع المستوحي من GitHub */
    .repo-card {
      background-color: #161b22;
      border: 1px solid #30363d;
      border-radius: 6px;
      padding: 16px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      transition: border-color 0.2s ease, transform 0.2s ease;
    }

    .repo-card:hover {
      border-color: #8b949e;
      transform: translateY(-2px);
    }

    .repo-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 8px;
    }

    .repo-title {
      color: #58a6ff;
      font-weight: 600;
      font-size: 14px;
      text-decoration: none;
    }

    .repo-title:hover {
      text-decoration: underline;
    }

    .badge-public {
      color: #8b949e;
      border: 1px solid #30363d;
      border-radius: 2em;
      padding: 2px 7px;
      font-size: 12px;
      font-weight: 500;
    }

    .repo-description {
      font-size: 12px;
      color: #8b949e;
      line-height: 1.5;
      margin-bottom: 16px;
      flex-grow: 1; /* لضمان تساوي ارتفاع المحتوى */
    }

    .repo-footer {
      display: flex;
      align-items: center;
      font-size: 12px;
      color: #8b949e;
    }

    .lang-dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      display: inline-block;
      margin-right: 6px;
    }

    /* ألوان اللغات الشهيرة */
    .cpp { background-color: #f34b7d; }
    .js { background-color: #f1e05a; }
    .html { background-color: #e34c26; }
    .css { background-color: #563d7c; }

    /* تجاوب الشاشة للأجهزة الصغيرة (تصبح 1 أو 2 عمود في الشاشات الصغيرة) */
    @media (max-width: 900px) {
      .projects-grid {
        grid-template-columns: repeat(2, 1fr);
      }
    }
    @media (max-width: 600px) {
      .projects-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>

  <div class="section-title">Popular Repositories</div>

  <div class="projects-grid">
    
    <!-- المشروع 1 -->
    <div class="repo-card">
      <div>
        <div class="repo-header">
          <a href="#" class="repo-title">ApexViperCode</a>
          <span class="badge-public">Public</span>
        </div>
        <p class="repo-description">Personal developer portfolio showcase and project collection repository.</p>
      </div>
      <div class="repo-footer">
        <span class="lang-dot html"></span> HTML
      </div>
    </div>

    <!-- المشروع 2 -->
    <div class="repo-card">
      <div>
        <div class="repo-header">
          <a href="#" class="repo-title">ProjectX-O</a>
          <span class="badge-public">Public</span>
        </div>
        <p class="repo-description">The classic Tic-Tac-Toe game built in C++ offering an exciting 2-player mode.</p>
      </div>
      <div class="repo-footer">
        <span class="lang-dot cpp"></span> C++
      </div>
    </div>

    <!-- المشروع 3 -->
    <div class="repo-card">
      <div>
        <div class="repo-header">
          <a href="#" class="repo-title">Snake-game</a>
          <span class="badge-public">Public</span>
        </div>
        <p class="repo-description">An engaging interactive version of the classic Snake game built in C++ with real-time score tracking.</p>
      </div>
      <div class="repo-footer">
        <span class="lang-dot cpp"></span> C++
      </div>
    </div>

    <!-- المشروع 4 -->
    <div class="repo-card">
      <div>
        <div class="repo-header">
          <a href="#" class="repo-title">in_year</a>
          <span class="badge-public">Public</span>
        </div>
        <p class="repo-description">Advanced Age Calculator project blending C++ algorithms with HTML/CSS interface.</p>
      </div>
      <div class="repo-footer">
        <span class="lang-dot cpp"></span> C++
      </div>
    </div>

    <!-- المشروع 5 -->
    <div class="repo-card">
      <div>
        <div class="repo-header">
          <a href="#" class="repo-title">Tic-Tac-Toe</a>
          <span class="badge-public">Public</span>
        </div>
        <p class="repo-description">A modern and innovative version of Tic-Tac-Toe developed with HTML, CSS, and JavaScript.</p>
      </div>
      <div class="repo-footer">
        <span class="lang-dot js"></span> JavaScript
      </div>
    </div>

    <!-- المشروع 6 -->
    <div class="repo-card">
      <div>
        <div class="repo-header">
          <a href="#" class="repo-title">Calculator</a>
          <span class="badge-public">Public</span>
        </div>
        <p class="repo-description">An advanced web calculator application built using HTML, CSS, and JavaScript with high precision.</p>
      </div>
      <div class="repo-footer">
        <span class="lang-dot html"></span> HTML
      </div>
    </div>

  </div>

</body>
</html>





