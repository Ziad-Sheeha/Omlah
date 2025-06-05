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
  height: 100vh; /* يبقى 100% من ارتفاع الشاشة */
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  color: #fff;
  padding-top: 80px; /* بادينج علوي لترك مساحة للهيدر الثابت */
  box-sizing: border-box;
  width: 100%; /* <--- NEW: أصبح يأخذ عرض 100% */

}

/* لضمان عمل الاتجاه (RTL/LTR) بشكل صحيح */
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
  text-align: center; /* توسيط النص */
  width: 90%; /* <--- NEW: أصبح يأخذ 90% من عرض الحاوية */
  max-width: 800px; /* <--- NEW: تحديد أقصى عرض للمحتوى لضمان عدم تمدده كثيراً على الشاشات الكبيرة */
  padding: 20px;
  box-sizing: border-box;
  margin: 0 auto; /* <--- NEW: توسيط div المحتوى نفسه */
}

.main-content h1 {
  font-size: 36px; /* حجم الخط الأساسي */
  font-weight: 600;
  margin-bottom: 1rem;
  line-height: 1.2;

}

span {
  font-size: inherit;
  font-weight: inherit;
  color: #0AAFE1; /* لون أزرق مميز */
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


/* Responsive adjustments */
@media (max-width: 992px) {
  .MainSection {
    padding-top: 60px;
    height: auto;
    min-height: 70vh; /* يمكن ضبط الارتفاع الأدنى هنا */
  }

  .main-content {
    padding: 15px; /* تقليل البادينج على الشاشات المتوسطة */
  }

  .main-content h1 {
    font-size: 32px; /* تصغير حجم العنوان قليلاً */
  }

  .main-content p {
    font-size: 0.95rem; /* تصغير حجم النص العادي قليلاً */
  }
}

@media (max-width: 768px) {
  .MainSection {
    min-height: 60vh;
  }

  .main-content h1 {
    font-size: 28px; /* تصغير حجم العنوان أكثر */
  }

  .main-content p {
    font-size: 0.9rem; /* تصغير حجم النص أكثر */
  }

  .btn {
    padding: 10px 30px; /* تصغير حجم الزر */
    font-size: 14px;
  }
}

@media (max-width: 480px) {
  .MainSection {
    min-height: 50vh;
  }
  .main-content h1 {
    font-size: 24px; /* حجم العنوان على أصغر الشاشات */
  }
  .main-content p {
    font-size: 0.85rem;
  }
  .btn {
    padding: 8px 25px;
    font-size: 13px;
    width: auto; /* يفضل أن يكون مرنًا */
    max-width: 250px; /* حد أقصى لعرض الزر */
  }
}
</style>