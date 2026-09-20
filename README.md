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
  <title>Academy Dashboard</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
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
      color: #fff;
      position: relative;
      overflow-x: hidden;
    }

    /* شريط العلوي Top Navigation Bar */
    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 15px 40px;
      background: rgba(15, 7, 28, 0.7);
      backdrop-filter: blur(15px);
      border-bottom: 1px solid rgba(168, 85, 247, 0.2);
      position: relative;
      z-index: 100;
    }

    .brand-logo {
      font-family: 'Orbitron', sans-serif;
      font-size: 1.5rem;
      color: #a855f7;
      text-shadow: 0 0 10px rgba(168, 85, 247, 0.5);
    }

    /* زاوية البروفايل Profile Section */
    .profile-wrapper {
      position: relative;
    }

    .profile-trigger {
      width: 48px;
      height: 48px;
      border-radius: 50%;
      border: 2px solid #a855f7;
      cursor: pointer;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #1a0b2e;
      box-shadow: 0 0 12px rgba(168, 85, 247, 0.4);
      transition: 0.3s;
    }

    .profile-trigger:hover {
      box-shadow: 0 0 20px rgba(168, 85, 247, 0.8);
      transform: scale(1.05);
    }

    .profile-trigger img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    /* الواجهة المنسدلة Dropdown Card */
    .profile-dropdown {
      position: absolute;
      top: 60px;
      right: 0;
      width: 280px;
      background: rgba(15, 7, 28, 0.95);
      backdrop-filter: blur(20px);
      border: 1px solid rgba(168, 85, 247, 0.3);
      border-radius: 16px;
      padding: 20px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.7), 0 0 20px rgba(168, 85, 247, 0.2);
      display: none;
      flex-direction: column;
      align-items: center;
      gap: 15px;
      animation: fadeIn 0.3s ease-in-out forwards;
    }

    .profile-dropdown.active {
      display: flex;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .dropdown-avatar {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      border: 2px solid #a855f7;
      overflow: hidden;
      background: #1a0b2e;
    }

    .dropdown-avatar img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .user-name-display {
      font-size: 1.1rem;
      font-weight: 600;
      color: #fff;
    }

    .dropdown-btn {
      width: 100%;
      padding: 10px;
      background: rgba(168, 85, 247, 0.1);
      border: 1px solid rgba(168, 85, 247, 0.4);
      color: #c084fc;
      border-radius: 8px;
      font-size: 0.85rem;
      font-weight: 600;
      cursor: pointer;
      transition: 0.3s;
      text-align: center;
    }

    .dropdown-btn:hover {
      background: #a855f7;
      color: #fff;
      box-shadow: 0 0 15px rgba(168, 85, 247, 0.5);
    }

    .btn-logout-dropdown {
      border-color: rgba(239, 68, 68, 0.4);
      color: #ef4444;
      background: rgba(239, 68, 68, 0.1);
    }

    .btn-logout-dropdown:hover {
      background: #ef4444;
      color: #fff;
      box-shadow: 0 0 15px rgba(239, 68, 68, 0.5);
    }

    /* إخفاء مخرج اختيار الملفات */
    #imageInput {
      display: none;
    }

    /* محتوى الصفحة الرئيسية */
    .main-content {
      padding: 80px 40px;
      text-align: center;
    }

    .main-content h1 {
      font-family: 'Orbitron', sans-serif;
      font-size: 2.5rem;
      margin-bottom: 15px;
      color: #c084fc;
    }
  </style>
</head>
<body>

  <!-- Navigation Bar -->
  <nav class="navbar">
    <div class="brand-logo">IDEA ACADEMY</div>
    
    <div class="profile-wrapper">
      <!-- Profile Avatar Button -->
      <div class="profile-trigger" id="profileTrigger">
        <img id="navAvatarImg" src="" alt="Avatar">
      </div>

      <!-- Profile Settings Dropdown -->
      <div class="profile-dropdown" id="profileDropdown">
        <div class="dropdown-avatar">
          <img id="dropdownAvatarImg" src="" alt="Avatar">
        </div>
        <div class="user-name-display" id="dropdownUserName">User</div>
        
        <!-- Action Buttons -->
        <button class="dropdown-btn" onclick="triggerFileInput()">Upload Photo</button>
        <button class="dropdown-btn" onclick="changeUsername()">Change Name</button>
        <button class="dropdown-btn btn-logout-dropdown" onclick="logout()">Sign Out</button>

        <!-- Hidden File Input -->
        <input type="file" id="imageInput" accept="image/*" onchange="uploadImage(event)">
      </div>
    </div>
  </nav>

  <!-- Page Body -->
  <div class="main-content">
    <h1 id="welcomeTitle">Welcome Back</h1>
    <p style="color: #a78bfa;">You have successfully accessed the main portal.</p>
  </div>

  <script>
    // الصورة الافتراضية (Default Avatar)
    const defaultAvatar = "data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23a855f7'><path d='M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 4c1.93 0 3.5 1.57 3.5 3.5S13.93 13 12 13s-3.5-1.57-3.5-3.5S10.07 6 12 6zm0 14c-2.03 0-3.8-.85-5.05-2.2.03-1.67 3.37-2.58 5.05-2.58 1.67 0 5.02.91 5.05 2.58C15.8 19.15 14.03 20 12 20z'/></svg>";

    // التحقق عند تحميل الصفحة
    window.onload = function() {
      const auth = localStorage.getItem('academy_auth');
      const user = localStorage.getItem('academy_user');
      const savedAvatar = localStorage.getItem('academy_avatar');

      if (auth !== 'true') {
        window.location.href = "login.html"; // إعادة التوجيه لصفحة تسجيل الدخول إن لم يسجل بعد
      } else {
        updateUI(user, savedAvatar || defaultAvatar);
      }
    };

    // التبديل بين إظهار وإخفاء القائمة المنسدلة
    const trigger = document.getElementById('profileTrigger');
    const dropdown = document.getElementById('profileDropdown');

    trigger.addEventListener('click', (e) => {
      e.stopPropagation();
      dropdown.classList.toggle('active');
    });

    document.addEventListener('click', () => {
      dropdown.classList.remove('active');
    });

    dropdown.addEventListener('click', (e) => {
      e.stopPropagation();
    });

    // تحديث عناصر الواجهة
    function updateUI(name, avatarSrc) {
      document.getElementById('dropdownUserName').innerText = name;
      document.getElementById('welcomeTitle').innerText = "Welcome Back, " + name;
      document.getElementById('navAvatarImg').src = avatarSrc;
      document.getElementById('dropdownAvatarImg').src = avatarSrc;
    }

    // فتح File Explorer اختيار صورة
    function triggerFileInput() {
      document.getElementById('imageInput').click();
    }

    // رفع وتحويل الصورة إلى Base64 للحفظ بـ localStorage
    function uploadImage(event) {
      const file = event.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = function(e) {
          const imageData = e.target.result;
          localStorage.setItem('academy_avatar', imageData);
          const currentUser = localStorage.getItem('academy_user');
          updateUI(currentUser, imageData);
        };
        reader.readAsDataURL(file);
      }
    }

    // تغيير اسم المستخدم
    function changeUsername() {
      const newName = prompt("Enter your new name:");
      if (newName && newName.trim() !== "") {
        localStorage.setItem('academy_user', newName.trim());
        const currentAvatar = localStorage.getItem('academy_avatar') || defaultAvatar;
        updateUI(newName.trim(), currentAvatar);
      }
    }

    // تسجيل الخروج
    function logout() {
      localStorage.removeItem('academy_auth');
      window.location.href = "login.html";
    }
  </script>
</body>
</html>

























<div class="profile-wrapper">
  <!-- أيقونة البروفايل الدائرية -->
  <div class="profile-trigger" id="profileTrigger">
    <img id="navAvatarImg" src="" alt="Avatar">
  </div>

  <!-- القائمة المنسدلة للتحكم -->
  <div class="profile-dropdown" id="profileDropdown">
    <div class="dropdown-avatar">
      <img id="dropdownAvatarImg" src="" alt="Avatar">
    </div>
    <div class="user-name-display" id="dropdownUserName">User</div>
    
    <button class="dropdown-btn" onclick="triggerFileInput()">Upload Photo</button>
    <button class="dropdown-btn" onclick="changeUsername()">Change Name</button>
    <button class="dropdown-btn btn-logout-dropdown" onclick="logout()">Sign Out</button>

    <input type="file" id="imageInput" accept="image/*" onchange="uploadImage(event)">
  </div>
</div>




































.profile-wrapper {
  position: relative;
}

.profile-trigger {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  border: 2px solid #a855f7;
  cursor: pointer;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #1a0b2e;
  box-shadow: 0 0 12px rgba(168, 85, 247, 0.4);
  transition: 0.3s;
}

.profile-trigger:hover {
  box-shadow: 0 0 20px rgba(168, 85, 247, 0.8);
  transform: scale(1.05);
}

.profile-trigger img, .dropdown-avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.profile-dropdown {
  position: absolute;
  top: 60px;
  right: 0;
  width: 260px;
  background: rgba(15, 7, 28, 0.95);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(168, 85, 247, 0.3);
  border-radius: 16px;
  padding: 20px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.7);
  display: none;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  z-index: 1000;
}

.profile-dropdown.active {
  display: flex;
}

.dropdown-avatar {
  width: 75px;
  height: 75px;
  border-radius: 50%;
  border: 2px solid #a855f7;
  overflow: hidden;
  background: #1a0b2e;
}

.user-name-display {
  font-size: 1rem;
  font-weight: 600;
  color: #fff;
}

.dropdown-btn {
  width: 100%;
  padding: 8px;
  background: rgba(168, 85, 247, 0.1);
  border: 1px solid rgba(168, 85, 247, 0.4);
  color: #c084fc;
  border-radius: 8px;
  font-size: 0.85rem;
  cursor: pointer;
  transition: 0.3s;
}

.dropdown-btn:hover {
  background: #a855f7;
  color: #fff;
}

.btn-logout-dropdown {
  border-color: rgba(239, 68, 68, 0.4);
  color: #ef4444;
  background: rgba(239, 68, 68, 0.1);
}

.btn-logout-dropdown:hover {
  background: #ef4444;
  color: #fff;
}

#imageInput {
  display: none;
}

















 const defaultAvatar = "data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23a855f7'><path d='M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 4c1.93 0 3.5 1.57 3.5 3.5S13.93 13 12 13s-3.5-1.57-3.5-3.5S10.07 6 12 6zm0 14c-2.03 0-3.8-.85-5.05-2.2.03-1.67 3.37-2.58 5.05-2.58 1.67 0 5.02.91 5.05 2.58C15.8 19.15 14.03 20 12 20z'/></svg>";

window.onload = function() {
  const auth = localStorage.getItem('academy_auth');
  const user = localStorage.getItem('academy_user');
  const savedAvatar = localStorage.getItem('academy_avatar');

  // إذا لم يسجل الدخول، يتم تحويله لصفحة login.html
  if (auth !== 'true') {
    window.location.href = "login.html";
  } else {
    updateUI(user, savedAvatar || defaultAvatar);
  }
};

const trigger = document.getElementById('profileTrigger');
const dropdown = document.getElementById('profileDropdown');

trigger.addEventListener('click', (e) => {
  e.stopPropagation();
  dropdown.classList.toggle('active');
});

document.addEventListener('click', () => {
  dropdown.classList.remove('active');
});

dropdown.addEventListener('click', (e) => {
  e.stopPropagation();
});

function updateUI(name, avatarSrc) {
  document.getElementById('dropdownUserName').innerText = name;
  document.getElementById('navAvatarImg').src = avatarSrc;
  document.getElementById('dropdownAvatarImg').src = avatarSrc;
}

function triggerFileInput() {
  document.getElementById('imageInput').click();
}

function uploadImage(event) {
  const file = event.target.files[0];
  if (file) {
    const reader = new FileReader();
    reader.onload = function(e) {
      const imageData = e.target.result;
      localStorage.setItem('academy_avatar', imageData);
      updateUI(localStorage.getItem('academy_user'), imageData);
    };
    reader.readAsDataURL(file);
  }
}

function changeUsername() {
  const newName = prompt("Enter your new name:");
  if (newName && newName.trim() !== "") {
    localStorage.setItem('academy_user', newName.trim());
    const currentAvatar = localStorage.getItem('academy_avatar') || defaultAvatar;
    updateUI(newName.trim(), currentAvatar);
  }
}

function logout() {
  localStorage.removeItem('academy_auth');
  window.location.href = "login.html";
}






