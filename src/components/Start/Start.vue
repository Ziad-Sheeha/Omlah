<template>
  <section class="about-us-section py-5 text-white">
    <div class="container">
      <div class="row align-items-center">

        <!-- Image -->
        <div class="col-lg-6 col-md-12 text-center">
          <img
            src="../../assets/Images/about.jpg"
            alt="قاعة أو اجتماع"
            class="img-fluid about-image rounded"
          />
        </div>
        <!-- Text -->
        <div class="col-lg-6 col-md-12 mb-4 mb-lg-0 text-end">
          <h2 class="section-title mb-3">من نحن؟</h2>
          <p class="about-description">
            شركة عملة للصرافة (شركة شخص واحد) تُعد من الشركات الرائدة في صرف العملات الأجنبية داخل المملكة العربية السعودية، بخبرة تمتد منذ عام 2015 وشبكة فروع تغطي مناطق مختلفة. <br /><br />
            على مدى السنوات، تلبي الشركة احتياجات العملاء والأطراف التجارية بأسعار تنافسية وتوفر جميع العملات، مع الالتزام التام بتعليمات البنك المركزي السعودي في مكافحة غسل الأموال وتمويل الإرهاب.
          </p>
        </div>

        
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-us-section {
  background-color: #0f2d87; 
  direction: rtl;
}

.section-title {
  font-size: 1.8rem;
  font-weight: 700;
  color: white;
}

.about-description {
  font-size: 1.05rem;
  line-height: 1.9;
  color: #ffffff;
}

.about-image {
  border: 3px solid #00aaff;
  max-width: 100%;
  height: auto;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.15);
}

@media (max-width: 767px) {
  .about-description {
    text-align: center;
  }

  .section-title {
    text-align: center;
  }
}
</style>
