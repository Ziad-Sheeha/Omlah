<template>
  <section class="MainSection" id="main">
    <div class="main-content">
      <h1>بدّل
        <span>العملات</span>
        الأجنبية بسهولة وثقة</h1>

      <p>سواء كنت فردًا، شركة، أو سفارة — تقدم لك "عملة" خدمات صرافة سريعة وآمنة ومرخصة في جميع أنحاء المملكة العربية السعودية.</p>
      <div class="main-buttons">
        <button class="btn learn-more">تعرف على خدماتنا</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'MainSection'
}
</script>

<style scoped>
.MainSection {
  background-image: url('../../assets/Images/Main.jpg');
  background-size: cover;
  background-position: center;
  height: 100vh; 
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  color: #fff;
  padding-top: 80px; 
  box-sizing: border-box;
  width: 100%; 
 
}

html[dir="ltr"] .MainSection {
  direction: ltr;
}

html[dir="rtl"] .MainSection {
  direction: rtl;
}


.MainSection::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1;
}

.main-content {
  position: relative;
  z-index: 2;
  text-align: center;
  width: 90%; 
  max-width: 800px; 
  padding: 20px;
  box-sizing: border-box;
  margin: 0 auto;
}

.main-content h1 {
  font-size: 36px; 
  font-weight: 600;
  margin-bottom: 1rem;
  line-height: 1.2;
 
}

span {
  font-size: inherit;
  font-weight: inherit;
  color: #0AAFE1; 
}

.main-content p {
  font-size: 1rem;
  color: #FFFFFF;
  margin-bottom: 2rem;
  font-weight: 400;
  line-height: 1.6;
}

.btn {
  padding: 10px 50px;
  letter-spacing: 0%;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 15px;
  font-weight: 600;
  transition: background-color 0.3s ease;
}

.learn-more {
  background-color: #f0f0f0;
  color: #333;
  border-radius: 45px;
}

.learn-more:hover {
  background-color: #2C1969;
  color: #ffff;
}


@media (max-width: 992px) {
  .MainSection {
    padding-top: 60px;
    height: auto;
    min-height: 70vh;
  }

  .main-content {
    padding: 15px; 
  }

  .main-content h1 {
    font-size: 32px; 
  }

  .main-content p {
    font-size: 0.95rem; 
  }
}

@media (max-width: 768px) {
  .MainSection {
    min-height: 60vh;
  }

  .main-content h1 {
    font-size: 28px; 
  }

  .main-content p {
    font-size: 0.9rem; 
  }

  .btn {
    padding: 10px 30px; 
    font-size: 14px;
  }
}

@media (max-width: 480px) {
  .MainSection {
    min-height: 50vh;
  }
  .main-content h1 {
    font-size: 24px; 
  }
  .main-content p {
    font-size: 0.85rem;
  }
  .btn {
    padding: 8px 25px;
    font-size: 13px;
    width: auto; 
    max-width: 250px; 
  }
}
</style>