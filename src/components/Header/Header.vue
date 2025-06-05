
<template>
  <header class="navbar navbar-expand-lg  ">
    <div class="header-content">
      <div class="logo">
        <img src="../../assets/Images/logo.svg" alt="Omlah." class="logo-image" loading="lazy"/>
      </div>

      <div class="nav-wrapper">
        <nav class="main-nav">
          <ul>
            <li><a href="#" >الرئيسية</a></li>
            <li><a href="#">خدماتنا</a></li>
            <li><a href="#">العملات</a></li>
            <li><a href="#">الفروع</a></li>
            <li><a href="#">تطبيق الجوال</a></li>
            <li><a href="#">الأسئلة الشائعة</a></li>
          </ul>
        </nav>

        <div class="language-selector">
          <i class="bi bi-globe"></i>
        </div>
      </div>

      <div class="auth-buttons">
        <button class="btn register-btn">إنشاء حساب</button>
        <button class="btn login-btn">تسجيل دخول</button>
      </div>

      <button class="menu-toggle" @click="toggleMenu">
       <i class="bi bi-list"></i>
      </button>

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
    }
  }
}
</script>

<style scoped>

.navbar {
  background-color: #ffffff;
  padding: 10px 20px; 
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  direction: rtl;
  width: 100%;
  box-sizing: border-box;
  z-index: 9999;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 98%;
  max-width: 1400px; 
  margin: 0 auto;
}

.logo .logo-image {
  height: 48px;
  width: auto;
  margin-right: 20px; 
}

.nav-wrapper {
  display: flex;
  align-items: center;
  gap: 25px; 
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
}

.main-nav li a:hover {
  color: #007bff;
}

.main-nav li a.active::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
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

.auth-buttons {
  display: flex;
  gap: 10px;
}

.btn {
  padding: 10px 20px; 
  letter-spacing: 0%;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 15px;
  font-weight: 600;
  transition: background-color 0.3s ease;
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
  font-size: 24px;
  cursor: pointer;
  color: #333;
  padding: 5px;
}

@media (max-width: 992px) {
  .header-content {
    justify-content: space-between;
    align-items: center;
    padding: 0 15px; 
  }

  .nav-wrapper {
    display: none;
    flex-direction: column; 
    position: absolute;
    top: 68px; 
    right: 0; 
    width: 100%;
    background-color: #ffffff;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    padding: 20px 0;
    align-items: flex-end; 
  }

  .nav-wrapper.open {
    display: flex; 
  }

  .main-nav ul {
    flex-direction: column; 
    text-align: right; 
    width: 100%;
  }

  .main-nav li {
    width: 100%;
  }

  .main-nav li a {
    padding: 10px 25px; 
    display: block; 
  }

  .language-selector {
    padding: 10px 25px; 
    width: 100%;
    text-align: right;
    box-sizing: border-box;
  }

  .auth-buttons {
    display: none; 
  }

  .menu-toggle {
    display: block; 
  }
}

@media (max-width: 576px) {
  .navbar {
    padding: 8px 10px; 
  }

  .logo .logo-image {
    height: 40px; 
  }

  .menu-toggle {
    font-size: 20px; 
  }
}

</style>