 <template>
  <section class="MainSection">
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
  width: 1200PX; 

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
  max-width: 1000px; 
  padding: 20px;
  box-sizing: border-box; 
}

.main-content h1 {
  font-size: 36px;
  font-weight: 600;
  margin-bottom: 1rem;
  text-align: center;
  width: 100%; 
  margin: auto; 
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


@media (max-width: 768px) {
  .MainSection {
    padding-top: 60px; 
    height: auto; 
    min-height: 60vh;
  }

  .main-content h1 {
    font-size: 38px; 
  }

  .main-content p {
    font-size: 1rem; 
  }

  

  .btn {
    width: 90%; 
    max-width: 300px; 
  }
}

@media (max-width: 480px) {
  .main-content h1 {
    font-size: 30px;
  }
}
</style>
