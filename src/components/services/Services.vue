<template>
  <section class="services py-5">
    <div class="container">
      <h2 class="text-center mb-2 section-title">خدماتنا</h2>

      <div class="container text-center">
        <div class="row justify-content-center">
          <div class="col-lg-4 col-md-6 mb-4">
            <div class="card services-card h-100">
              <div class="card-body">
                <i class="bi bi-lock"></i>

                <h4 class="card-title service-title">العملات المتداولة</h4>
                <p class="card-text service-description">
                  نوفر جميع العملات العالمية بأسعار محدثة يوميًا لتلبية احتياجات
                  الأفراد والشركات.
                </p>
              </div>
            </div>
          </div>

          <div class="col-lg-4 col-md-6 mb-4">
            <div class="card services-card h-100">
              <div class="card-body">
                <i class="bi bi-hand-thumbs-up"></i>

                <h4 class="card-title service-title">شراء العملات الاجنبية</h4>
                <p class="card-text service-description">
                  نقدّم خدمة شراء العملات بأسعار تنافسية وسرعة في التنفيذ عبر
                  فروعنا المنتشرة.
                </p>
              </div>
            </div>
          </div>

          <div class="col-lg-4 col-md-6 mb-4">
            <div class="card services-card h-100">
              <div class="card-body">
                <i class="bi bi-file-earmark-text"></i>

                <h4 class="card-title service-title">بيع العملات الاجنبية</h4>
                <p class="card-text service-description">
                  بيع العملات الأجنبية بأمان وموثوقية، مع التزام بأفضل الأسعار
                  المتاحة في السوق.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "AppServices",
};
</script>

<style scoped>
.services {
  background-color: #f9fafd; 
}

.section-title {
  font-weight: bold;
  margin-bottom: 2rem;
  color: #1e1e6f;
}

.services-card {
  border: none;
  background: #fff;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  border-radius: 12px;
  padding: 2rem 1.5rem;
}

.services-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
}

.services-card i {
  font-size: 2.5rem;
  color: #4b3cc2;
  margin-bottom: 1rem;
  display: block;
}

.service-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: #1e1e6f;
  margin-bottom: 0.75rem;
}

.service-description {
  font-size: 1rem;
  color: #444;
  line-height: 1.7;
}

@media (max-width: 768px) {
  .service-card .service-number {
    font-size: 2.8rem;
    top: 15px;
    right: unset; 
    left: 50%; 
    transform: translateX(-50%);
  }

  .service-card .service-number-right,
  .service-card .service-number-center,
  .service-card .service-number-left {
    right: unset;
    left: 50%;
    transform: translateX(-50%);
  }

  .service-card .service-icon {
    width: 50px;
    height: 50px;
  }

  .service-card .service-title {
    font-size: 1.4rem;
  }

  .service-card .service-description {
    font-size: 0.95rem;
  }
}
</style>
