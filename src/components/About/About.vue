<template>
  <section class="how-it-works-section py-5 text-center">
    <div class="container">
      <h2 class="section-title mb-2">كيف تبدأ؟</h2>
      <p class="section-subtitle mb-5">
        تعرّف على خطوات خدمة صرف العملات لدينا — من الزيارة وحتى استلام العملة بكل سهولة وأمان.
      </p>
      <div class="row justify-content-center">
        <!-- Step 1 -->
        <div class="col-lg-4 col-md-6 mb-4">
          <div class="step-item">
            <div class="step-icon">
              <img src="../../assets/Images/visit.png" alt="زيارة الفرع" />
            </div>
            <h5 class="step-title">زيارة الفرع</h5>
          </div>
        </div>
        
        <!-- Step 2 -->
        <div class="col-lg-4 col-md-6 mb-4">
          <div class="step-item">
            <div class="step-icon">
              <img src="../../assets/Images/deliver.png" alt="استلام التسميرة" />
            </div>
            <h5 class="step-title">استلام التسميرة</h5>
          </div>
        </div>

        <!-- Step 3 -->
        <div class="col-lg-4 col-md-6 mb-4">
          <div class="step-item">
            <div class="step-icon">
              <img src="../../assets/Images/reserve.png" alt="تسليم واستلام العملة" />
            </div>
            <h5 class="step-title">تسليم واستلام العملة</h5>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.how-it-works-section {
  background-color: #ffffff;
  direction: rtl;
}

.section-title {
  font-size: 1.8rem;
  font-weight: 700;
  color: #0f2d87;
}

.section-subtitle {
  color: #444;
  font-size: 1rem;
}

.step-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
}

.step-icon {
  width: 150px;
  height: 150px;
  border: 2px solid #0f2d87;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 15px;
  position: relative;
  background-color: #f9f9f9;
}
.step-icon {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  z-index: 1;
}

.step-item:hover .step-icon {
  transform: scale(1.1);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
  z-index: 5;
}


.step-icon img {
  max-width: 70%;
  height: auto;
}

.step-title {
  font-weight: 600;
  color: #0f2d87;
  font-size: 1.1rem;
  margin-top: 10px;
  text-align: center;
}

/* dashed line on large screens */
@media (min-width: 992px) {
  .step-item:not(:last-child)::after {
    content: "";
    position: absolute;
    top: 50%;
    right: -50%;
    width: 100%;
    height: 2px;
    border-top: 2px dashed #0f2d87; 
    transform: translateY(-50%);
    z-index: -1;
  }

}

@media (max-width: 768px) {
  .step-icon {
    width: 120px;
    height: 120px;
  }

  .step-title {
    font-size: 1rem;
  }

  .section-subtitle {
    font-size: 0.95rem;
  }
}
</style>


<script>
export default {
  name: "AppAbout",
};

</script>