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
  <title>تسجيل الدخول</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #0f0c20;
      overflow: hidden;
      position: relative;
    }

    /* خلفية متحركة */
    .background-glow {
      position: absolute;
      width: 300px;
      height: 300px;
      background: linear-gradient(135deg, #6b21a8, #a855f7);
      border-radius: 50%;
      filter: blur(80px);
      animation: float 6s ease-in-out infinite alternate;
    }

    .glow-2 {
      bottom: 10%;
      right: 15%;
      background: linear-gradient(135deg, #3b82f6, #9333ea);
      animation-delay: -3s;
    }

    @keyframes float {
      0% { transform: translate(0, 0) scale(1); }
      100% { transform: translate(30px, -40px) scale(1.1); }
    }

    /* كرت تسجيل الدخول */
    .login-card {
      position: relative;
      width: 380px;
      padding: 40px 30px;
      background: rgba(255, 255, 255, 0.05);
      backdrop-filter: blur(15px);
      border: 1px solid rgba(255, 255, 255, 0.1);
      border-radius: 16px;
      box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
      color: #fff;
      z-index: 10;
    }

    .login-card h2 {
      text-align: center;
      margin-bottom: 25px;
      font-size: 1.8rem;
      letter-spacing: 1px;
    }

    .input-box {
      margin-bottom: 20px;
    }

    .input-box label {
      display: block;
      margin-bottom: 8px;
      font-size: 0.9rem;
      color: #ccc;
    }

    .input-box input {
      width: 100%;
      padding: 12px;
      background: rgba(255, 255, 255, 0.08);
      border: 1px solid rgba(255, 255, 255, 0.2);
      border-radius: 8px;
      color: #fff;
      outline: none;
      transition: 0.3s;
    }

    .input-box input:focus {
      border-color: #a855f7;
      box-shadow: 0 0 8px rgba(168, 85, 247, 0.4);
    }

    /* مربع التحقق */
    .captcha-box {
      display: flex;
      align-items: center;
      gap: 10px;
      background: rgba(255, 255, 255, 0.05);
      padding: 10px;
      border-radius: 8px;
      margin-bottom: 20px;
      border: 1px solid rgba(255, 255, 255, 0.1);
    }

    .captcha-box input[type="checkbox"] {
      width: 18px;
      height: 18px;
      cursor: pointer;
    }

    .captcha-box label {
      font-size: 0.85rem;
      cursor: pointer;
      color: #ddd;
    }

    .btn-submit {
      width: 100%;
      padding: 12px;
      background: linear-gradient(90deg, #7e22ce, #a855f7);
      border: none;
      border-radius: 8px;
      color: #fff;
      font-weight: bold;
      font-size: 1rem;
      cursor: pointer;
      transition: 0.3s;
    }

    .btn-submit:hover {
      opacity: 0.9;
      transform: translateY(-2px);
    }

    /* واجهة البروفايل بعد التسجيل */
    .profile-card {
      display: none;
      text-align: center;
      position: relative;
      z-index: 10;
      background: rgba(255, 255, 255, 0.05);
      backdrop-filter: blur(15px);
      padding: 30px;
      border-radius: 16px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      color: white;
      width: 320px;
    }

    .avatar {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      background: #a855f7;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      margin: 0 auto 15px auto;
      border: 2px solid #fff;
    }

    .btn-logout {
      margin-top: 20px;
      padding: 8px 16px;
      background: #e11d48;
      border: none;
      border-radius: 6px;
      color: white;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <div class="background-glow"></div>
  <div class="background-glow glow-2"></div>

  <!-- نموذج تسجيل الدخول -->
  <div class="login-card" id="loginForm">
    <h2>تسجيل الدخول</h2>
    <form onsubmit="handleLogin(event)">
      <div class="input-box">
        <label>اسم المستخدم</label>
        <input type="text" id="username" required placeholder="أدخل اسمك">
      </div>
      <div class="input-box">
        <label>كلمة المرور</label>
        <input type="password" required placeholder="••••••••">
      </div>

      <div class="captcha-box">
        <input type="checkbox" id="captcha" required>
        <label for="captcha">أنا لست برنامج روبوت 🤖</label>
      </div>

      <button type="submit" class="btn-submit">دخول</button>
    </form>
  </div>

  <!-- واجهة البروفايل بعد تسجيل الدخول -->
  <div class="profile-card" id="profileCard">
    <div class="avatar" id="avatarLetter">U</div>
    <h3 id="welcomeUser">مرحباً بك</h3>
    <p style="font-size: 0.85rem; color: #aaa; margin-top: 5px;">أنت الآن مسجل الدخول</p>
    <button class="btn-logout" onclick="handleLogout()">تسجيل الخروج</button>
  </div>

  <script>
    // التحقق عند تحميل الصفحة إذا كان المستخدم مسجلاً مسبقاً
    window.onload = function() {
      const savedUser = localStorage.getItem('isLoggedIn');
      const username = localStorage.getItem('username');
      if (savedUser === 'true') {
        showProfile(username);
      }
    };

    function handleLogin(e) {
      e.preventDefault();
      const username = document.getElementById('username').value;
      
      // حفظ الحالة في المتصفح
      localStorage.setItem('isLoggedIn', 'true');
      localStorage.setItem('username', username);

      showProfile(username);
    }

    function showProfile(name) {
      document.getElementById('loginForm').style.display = 'none';
      document.getElementById('profileCard').style.display = 'block';
      document.getElementById('welcomeUser').innerText = 'مرحباً، ' + name;
      document.getElementById('avatarLetter').innerText = name.charAt(0).toUpperCase();
    }

    function handleLogout() {
      localStorage.removeItem('isLoggedIn');
      localStorage.removeItem('username');
      location.reload();
    }
  </script>

</body>
</html>











