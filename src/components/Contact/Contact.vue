<template>
  <section class="contact-section">
    <div class="contact-content-wrapper">
        <div class="form-container">
        <h2 class="section-title">تواصل معنا</h2>
        <form @submit.prevent="submitForm" class="contact-form">
          <div class="form-group">
            <input type="text" id="name" v-model="form.name" placeholder="الاسم" required />
          </div>
          <div class="form-group">
            <input type="email" id="email" v-model="form.email" placeholder="البريد الإلكتروني" required />
          </div>
          <div class="form-group">
            <input type="tel" id="phone" v-model="form.phone" placeholder="رقم الجوال" required />
          </div>
          <div class="form-group">
            <textarea id="message" v-model="form.message" placeholder="اكتب رسالتك" rows="5" required></textarea>
          </div>
          <button type="submit" class="submit-button">أرسل رسالتك</button>
        </form>

        <div class="contact-info">
          <div class="info-item">
            <i class="fas fa-phone-alt"></i> <span>8001245552</span>
            <span>الجوال</span>
          </div>
          <div class="info-item">
            <i class="fas fa-envelope"></i> <span>info@omlah.com.sa</span>
            <span>الإيميل</span>
          </div>
          <div class="info-item">
            <i class="fas fa-clock"></i> <span>السبت - الجمعة</span>
            <span>8 ساعات</span>
          </div>
        </div>
      </div>
      <div class="map-container">
        <img src="../../assets/Images/map.png" alt="World Map" class="world-map-image" />
      </div>

      
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const form = ref({
  name: '',
  email: '',
  phone: '',
  message: ''
});

const submitForm = () => {
  // هنا يمكنك إضافة منطق إرسال النموذج، مثل استدعاء API
  console.log('Form Submitted:', form.value);
  alert('تم إرسال رسالتك بنجاح! (هذا مثال فقط)');
  // يمكنك مسح الحقول بعد الإرسال
  form.value = {
    name: '',
    email: '',
    phone: '',
    message: ''
  };
};
</script>

<style scoped>


.contact-section {
  direction: rtl; 
  font-family: 'Inter', sans-serif; 
  background-color: #f0f2f5; 
  padding: 80px var(--app-padding-x);
  display: flex;
  justify-content: center;
  align-items: center;
}

.contact-content-wrapper {
  display: flex;
  flex-direction: row; 
  background-color: #fff; 
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  max-width: var(--app-max-width);
  width: 100%;
  overflow: hidden; 
}

.map-container {
  flex: 1; 
  background-color: #ffff; 
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 30px;
  min-height: 500px; 
}

.world-map-image {
  width: 100%;
  height: auto;
  opacity: 0.7; 
  max-width: 500px; 
}

.form-container {
  flex: 1;
  padding: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.section-title {
  font-size: 38px;
  font-weight: 700;
  color: #2c1969;
  margin-bottom: 30px;
}

.contact-form {
  width: 100%;
  max-width: 450px; 
  margin-bottom: 30px;
}

.form-group {
  margin-bottom: 20px;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 15px 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  font-size: 16px;
  font-family: 'Inter', sans-serif;
  color: #333;
  box-sizing: border-box; 
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: #999;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: #0AAFE1;
  box-shadow: 0 0 0 3px rgba(10, 175, 225, 0.2);
  outline: none;
}

.submit-button {
  background-color: #2c1969;
  color: #fff;
  border: none;
  border-radius: 10px;
  padding: 15px 30px;
  font-size: 18px;
  font-weight: 600;
  cursor: pointer;
  width: 100%;
  max-width: 450px;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.submit-button:hover {
  background-color: #4148b4; 
  transform: translateY(-2px);
}

.contact-info {
  display: flex;
  flex-wrap: wrap; 
  justify-content: center;
  gap: 30px;
  width: 100%;
  max-width: 500px;
}

.info-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #555;
  font-size: 15px;
  line-height: 1.5;
  flex: 1 1 calc(33% - 20px); 
  min-width: 120px; 
}

.info-item i {
  font-size: 24px;
  color: #0AAFE1; 
  margin-bottom: 8px;
}

.info-item span:first-of-type {
  font-weight: 600;
  color: #333;
}

@media (max-width: 992px) {
  .contact-content-wrapper {
    flex-direction: column; 
  }

  .map-container {
    min-height: 300px; 
    padding: 20px;
  }

  .world-map-image {
    max-width: 400px;
  }

  .form-container {
    padding: 30px;
  }

  .section-title {
    font-size: 32px;
    margin-bottom: 25px;
  }

  .form-group input,
  .form-group textarea {
    font-size: 15px;
    padding: 12px 15px;
  }

  .submit-button {
    font-size: 16px;
    padding: 12px 25px;
  }

  .contact-info {
    flex-direction: column; 
    gap: 20px;
  }
}

@media (max-width: 576px) {
  .contact-section {
    padding: 50px var(--app-padding-x);
  }

  .form-container {
    padding: 20px;
  }

  .section-title {
    font-size: 28px;
    margin-bottom: 20px;
  }

  .form-group input,
  .form-group textarea {
    font-size: 14px;
    padding: 10px 12px;
  }

  .submit-button {
    font-size: 15px;
    padding: 10px 20px;
  }

  .info-item {
    font-size: 14px;
    flex: 1 1 100%; 
  }

  .info-item i {
    font-size: 20px;
  }
}
</style>