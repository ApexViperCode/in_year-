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
  <title>Code Viewer & Preview</title>
  <!-- مكتبة Highlight.js لتلوين الأكواد مثل VS Code و GitHub -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.7.0/styles/atom-one-dark.min.css">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.7.0/highlight.min.js"></script>

  <style>
    body {
      background-color: #0d1117;
      color: #c9d1d9;
      font-family: Segoe UI, Tahoma, Geneva, Verdana, sans-serif;
      padding: 20px;
    }

    .section-title {
      color: #a855f7;
      border-bottom: 2px solid #3b0764;
      padding-bottom: 5px;
      margin-top: 30px;
    }

    /* حاوية الكود */
    pre {
      border-radius: 8px;
      overflow: hidden;
      border: 1px solid #30363d;
      direction: ltr; /* لعرض الكود من اليسار لليمين بشكل صحيح */
      text-align: left;
    }

    /* نافذة المعاينة / التشغيل للـ HTML & CSS */
    .preview-box {
      background-color: #161b22;
      border: 1px solid #30363d;
      border-radius: 8px;
      padding: 15px;
      margin-top: 10px;
      direction: rtl;
    }
  </style>
</head>
<body>

  <!-- 1. عرض كود C++ -->
  <h2 class="section-title">💻 C++ Code</h2>
  <pre><code class="language-cpp" id="cpp-code"></code></pre>

  <!-- 2. عرض كود HTML -->
  <h2 class="section-title">🌐 HTML Code</h2>
  <pre><code class="language-xml" id="html-code"></code></pre>

  <!-- 3. عرض كود CSS -->
  <h2 class="section-title">🎨 CSS Code</h2>
  <pre><code class="language-css" id="css-code"></code></pre>

  <!-- 4. نتيجة التشغيل والمعاينة (Run / Preview) للويب -->
  <h2 class="section-title">🚀 المعاينة المباشرة (Live Preview)</h2>
  <div class="preview-box">
    <!-- هنا يظهر ناتج تشغيل كود الـ HTML والـ CSS -->
    <button style="background: #a855f7; color: white; border: none; padding: 8px 15px; border-radius: 5px; cursor: pointer;">زر تجريبي</button>
    <p style="color: #a855f7;">هذه المعاينة المباشرة لتصميم الويب!</p>
  </div>

  <script>
    // ضع كود C++ هنا كما هو بدون أي تعديل للأقواس
    const cppText = `#include <iostream>
#include <string>
using namespace std;

int main() {
    string name = "ApexViperCode";
    cout << "Welcome to " << name << "!" << endl;
    return 0;
}`;

    // ضع كود HTML هنا كما هو
    const htmlText = `<div class="card">
    <h1>مرحباً بك</h1>
    <button>اضغط هنا</button>
</div>`;

    // ضع كود CSS هنا كما هو
    const cssText = `.card {
    background-color: #1a1625;
    color: #a855f7;
    padding: 20px;
    border-radius: 8px;
}`;

    // إسناد الأكواد لعرضها كنصوص صريحة
    document.getElementById("cpp-code").textContent = cppText;
    document.getElementById("html-code").textContent = htmlText;
    document.getElementById("css-code").textContent = cssText;

    // تفعيل التلوين التلقائي للأكواد
    hljs.highlightAll();
  </script>
</body>
</html>

