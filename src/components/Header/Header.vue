<template>
  <header class="navbar navbar-expand-lg">
  <div class="container">
        <div class="header-content">
      <div class="logo">
        <img src="../../assets/Images/logo.svg" alt="Omlah." class="logo-image" loading="lazy"/>
      </div>

      
      <div :class="['nav-wrapper', { 'open': isMenuOpen }]">
        <nav class="main-nav">
          <ul>
            <li><a href="#main" @click="isMenuOpen = false">الرئيسية</a></li>
            <li><a href="#servie" @click="isMenuOpen = false">خدماتنا</a></li>
            <li><a href="#exchange" @click="isMenuOpen = false">العملات</a></li>
            <li><a href="#" @click="isMenuOpen = false">الفروع</a></li>
            <li><a href="#howAreWe" @click="isMenuOpen = false">من نحن </a></li>
            <li><a href="#FAQ" @click="isMenuOpen = false">الأسئلة الشائعة</a></li>
          </ul>
        </nav>

        <div class="language-selector">
          <i class="bi bi-globe"></i>
        </div>

        <!-- أزرار المصادقة لسطح المكتب - تظهر هنا داخل nav-wrapper -->
        <div class="auth-buttons desktop-auth-buttons">
          <button class="btn register-btn">إنشاء حساب</button>
          <button class="btn login-btn">تسجيل دخول</button>
        </div>

        <!-- أزرار المصادقة للموبايل - تظهر داخل القائمة المنسدلة على الشاشات الصغيرة -->
        <div class="auth-buttons mobile-auth-buttons">
          <button class="btn register-btn">إنشاء حساب</button>
          <button class="btn login-btn">تسجيل دخول</button>
        </div>
      </div>

      <!-- زر الهامبرغر، يتم إظهاره وإخفائه بناءً على Media Query -->
      <button class="menu-toggle" @click="toggleMenu">
        <i class="bi bi-list"></i>
      </button>

    </div>
  </div>

  </header>
</template>

<script>
export default {
  name: 'AppHeader',
  data() {
    return {
      isMenuOpen: false 
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
      document.body.classList.toggle('no-scroll', this.isMenuOpen);
    }
  }
}
</script>

<style scoped>

body.no-scroll {
  overflow: hidden;
}

.navbar {
  background-color: #ffff;
  padding: 10px var(--app-padding-x); 
  width: 100%;
  box-sizing: border-box;
  z-index: 9999; 
  position: fixed;
  top: 0;
  left: 0;
  direction: rtl; 
}

.header-content {
  display: flex;
  justify-content: space-between; 
  align-items: center;
  width: 100%;
  max-width:auto; 
  margin: 0 auto; 
  margin-left: 0;
}

.logo .logo-image {
  height: 48px;
  width: auto;
  margin-inline-end: 20px; 
}

.nav-wrapper {
  display: flex;
  align-items: center;
  gap: 25px; 
  flex-grow: 1; 
  justify-content: flex-end; 
}

.main-nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  gap: 25px; 
}

.main-nav li a {
  text-decoration: none;
  color: #333;
  font-size: 16px;
  font-weight: 600;
  padding: 5px 0;
  position: relative;
  transition: color 0.3s ease;
}

.main-nav li a:hover {
  color: #007bff;
}

.main-nav li a.active::after {
  content: '';
  position: absolute;
  right: 0; 
  left: auto;
  bottom: -5px;
  height: 3px;
  background-color: #007bff;
  border-radius: 2px;
}

.language-selector {
  font-size: 20px;
  color: #555;
  cursor: pointer;
}

.auth-buttons.desktop-auth-buttons {
  display: flex; 
  gap: 10px; 
}
.auth-buttons.mobile-auth-buttons {
    display: none; 
}


.btn {
  padding: 10px 20px;
  letter-spacing: 0%;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 15px;
  font-weight: 600;
  transition: background-color 0.3s ease, color 0.3s ease;
  min-width: 100px;
}

.register-btn {
  background-color: #f0f0f0;
  color: #333;
  border-radius: 45px;
}

.register-btn:hover {
  background-color: #2C1969;
  color: #ffff;
}

.login-btn {
  background-color: #f0f0f0;
  color: #333;
  border-radius: 45px;
}

.login-btn:hover {
  background-color: #2C1969;
  color: #ffffff;
}

.menu-toggle {
  display: none; 
  background: none;
  border: none;
  font-size: 30px; 
  cursor: pointer;
  color: #333;
  padding: 5px;
  z-index: 10000; 
}

@media (max-width: 991px) { 
  .header-content {
    padding: 0; 
  }

  .nav-wrapper {
    display: none; 
    flex-direction: column; 
    position: fixed; 
    top: 68px; 
    width: 100%;
    height: calc(100vh - 68px);
    background-color: #ffffff;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    padding: 20px var(--app-padding-x); 
    overflow-y: auto; 
    transition: right 0.3s ease-in-out; 
    z-index: 9998;
    
    right: -100%;
    align-items: flex-end; 
    justify-content: flex-start; 
    gap: 20px; 
  }

  .nav-wrapper.open {
    display: flex; 
    right: 0; 
  }

  .main-nav ul {
    flex-direction: column; 
    text-align: right;
    width: 100%;
    gap: 10px;
  }

  .main-nav li {
    width: 100%;
  }

  .main-nav li a {
    padding: 12px 0;
    display: block; 
    font-size: 17px;
  }

  .language-selector {
    padding: 12px 0; 
    width: 100%;
    text-align: right;
    box-sizing: border-box;
  }

  .desktop-auth-buttons {
    display: none;
  }

  .mobile-auth-buttons {
    display: flex; 
    flex-direction: column; 
    gap: 10px;
    width: 100%;
    padding: 20px 0; 
    box-sizing: border-box;
  }

  .mobile-auth-buttons .btn {
    width: 100%; 
    max-width: 250px; 
    margin-right: auto; 
    margin-left: auto; 
  }

  .menu-toggle {
    display: block; 
  }
}

@media (max-width: 575px) { 
  .navbar {
    padding: 8px 10px; 
  }

  .logo .logo-image {
    height: 40px; 
  }

  .menu-toggle {
    font-size: 26px; 
  }

  .nav-wrapper {
    top: 56px; 
    height: calc(100vh - 56px);
  }

  .main-nav li a {
    font-size: 16px;
    padding: 10px 0;
  }

  .language-selector {
    font-size: 18px;
    padding: 10px 0;
  }
}


html[dir="ltr"] .navbar {
  direction: ltr; 
}
html[dir="ltr"] .header-content {
  direction: ltr; 
}
html[dir="ltr"] .logo .logo-image {
  margin-inline-end: 0; 
  margin-inline-start: 20px; 
}
html[dir="ltr"] .nav-wrapper {
  justify-content: flex-start; 
}
html[dir="ltr"] .main-nav ul {
  text-align: left; 
}
html[dir="ltr"] .main-nav li a.active::after {
  right: auto; 
  left: 0; 
}
html[dir="ltr"] .language-selector {
  text-align: left;
}

@media (max-width: 991px) {
  html[dir="ltr"] .nav-wrapper {
    left: -100%; 
    right: auto; 
    align-items: flex-start; 
    transition: left 0.3s ease-in-out; 
  }
  html[dir="ltr"] .nav-wrapper.open {
    left: 0;
  }
  html[dir="ltr"] .mobile-auth-buttons .btn {
    margin-inline-start: auto; 
    margin-inline-end: auto; 
  }
}
</style>
