<template>
  <footer class="app-footer">
    <div class="footer-content-wrapper">
      <div class="footer-brand">
        <img src="../../assets/Images/logofooter.svg" alt="Omlah Exchange Co. Logo" class="company-logo" />
        <button class="cta-button">ابدأ الآن -</button>
      </div>

      <div class="footer-column">
        <h3>اتصل بنا</h3>
        <ul>
          <li><i class="bi bi-telephone-inbound"></i><span>966-11-234-5678</span></li>
          <li><i class="bi bi-envelope-check-fill"></i> <span>info@omlah.sa</span></li>
          <li class="social-icons">
            <a href="#" target="_blank" aria-label="Instagram"><i class="bi bi-instagram"></i></a>
            <a href="https://x.com/omlah2030" target="_blank" aria-label="Twitter"><i class="bi bi-twitter"></i></a>
            <a href="https://www.linkedin.com/company/omlah-exchange-co/" target="_blank" aria-label="LinkedIn"><i class="bi bi-linkedin"></i></a>
          </li>
        </ul>
      </div>

      <div class="footer-column">
        <h3>روابط سريعة</h3>
        <ul>
          <li><a href="#">الرئيسية</a></li>
          <li><a href="#">خدماتنا</a></li>
          <li><a href="#">من نحن</a></li>
          <li><a href="#">العمولات</a></li>
          <li><a href="#">تطبيق الجوال</a></li>
          <li><a href="#">الأسئلة الشائعة</a></li>
          <li><a href="#">تواصل معنا</a></li>
        </ul>
      </div>

      <div class="footer-column">
        <h3>المساعدة والدعم</h3>
        <ul>
          <li><a href="#">تسجيل حساب جديد للعملاء</a></li>
          <li><a href="#">تسجيل حساب جديد للأعمال</a></li>
          <li><a href="#">الشروط و الأحكام</a></li>
          <li><a href="#">سياسة الخصوصية</a></li>
        </ul>
      </div>
    </div>
  </footer>

  <a href="##" target="_blank" rel="noopener noreferrer" class="whatsapp-fixed-button" aria-label="WhatsApp Chat">
    <i class="bi bi-whatsapp"></i>
  </a>
</template>

<script>
</script>

<style scoped>
.app-footer {
  direction: rtl;
  font-family: 'Inter', sans-serif;
  background-color: #2c1969; 
  color: #fff;
  padding: 60px var(--app-padding-x) 40px;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}

.footer-content-wrapper {
  display: flex;
  flex-wrap: wrap; 
  justify-content: space-between;
  max-width: var(--app-max-width);
  width: 100%;
  gap: 30px; 
}

.footer-brand {
  display: flex;
  flex-direction: column;
  align-items: flex-start; 
  flex: 1 1 250px;
  margin-bottom: 20px;
  
}

.company-logo {
width: 45%;
  height: auto;
  margin-bottom: 15px;
}

.company-name {
  font-size: 18px;
  font-weight: 600;
  line-height: 1.4;
  margin-bottom: 20px;
}

.cta-button {
  background-color: #ffff; 
  color: black;
  border: none;
  border-radius: 8px;
  padding: 12px 25px;
  font-size: 16px;
  font-weight: 900;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.cta-button:hover {
  background-color: #089fd3;
}

.footer-column {
  flex: 1 1 180px;
  margin-bottom: 20px;
}

.footer-column h3 {
  font-size: 20px;
  font-weight: 700;
  margin-bottom: 25px;
  position: relative;
  padding-bottom: 10px;
}

.footer-column h3::after {
  content: '';
  position: absolute;
  right: 0;
  bottom: 0;
  width: 40px; 
  height: 3px;
  background-color: #0AAFE1;
  border-radius: 2px;
}

.footer-column ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-column ul li {
  margin-bottom: 12px;
  display: flex;
  align-items: center; 
}

.footer-column ul li a {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  font-size: 15px;
  transition: color 0.3s ease;
}

.footer-column ul li a:hover {
  color: #0AAFE1;
}

.footer-column ul li i {
  margin-left: 10px; 
  font-size: 16px;
  color: #0AAFE1;
}

.social-icons {
  display: flex;
  gap: 15px;
  margin-top: 10px;
}

.social-icons a {
  color: #fff;
  font-size: 24px;
  transition: color 0.3s ease;
}

.social-icons a:hover {
  color: #0AAFE1;
}

.whatsapp-fixed-button {
  position: fixed;
  bottom: 30px;
  right: 30px;
  background-color: #25d366; 
  color: #fff;
  border-radius: 50%;
  width: 60px;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
  z-index: 1000; 
  transition: transform 0.3s ease, background-color 0.3s ease;
  text-decoration: none; 
}

.whatsapp-fixed-button:hover {
  transform: scale(1.1);
  background-color: #1da851;
}

@media (max-width: 992px) {
  .footer-content-wrapper {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .footer-brand {
    align-items: center;
  }

  .footer-column {
    flex: 1 1 100%; 
    margin-bottom: 30px;
  }

  .footer-column h3 {
    text-align: center;
  }

  .footer-column h3::after {
    right: 50%; 
    transform: translateX(50%);
  }

  .footer-column ul {
    align-items: center;
  }
  .footer-column ul li {
    justify-content: center; 
  }

  .social-icons {
    justify-content: center;
  }

  .whatsapp-fixed-button {
    bottom: 20px;
    right: 20px;
    width: 50px;
    height: 50px;
    font-size: 25px;
  }
}

@media (max-width: 576px) {
  .app-footer {
    padding: 40px var(--app-padding-x) 20px;
  }

  .company-logo {
    width: 80px;
  }

  .company-name {
    font-size: 16px;
  }

  .cta-button {
    padding: 10px 20px;
    font-size: 14px;
  }

  .footer-column h3 {
    font-size: 18px;
  }

  .footer-column ul li a,
  .footer-column ul li span {
    font-size: 14px;
  }

  .footer-column ul li i {
    font-size: 14px;
  }

  .social-icons a {
    font-size: 20px;
  }
}
</style>