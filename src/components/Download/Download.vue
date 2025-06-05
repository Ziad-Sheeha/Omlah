<template>
  <section class="download-app-section">
    <div class="section-container">
      <h2 class="section-title">قم بتنزيل تطبيق عملة</h2>

      <div class="content-wrapper">
        <div class="left-column">
          <!-- منطقة نص QR والأيقونات -->
          <p class="qr-text">مسح للتنزيل.</p>
          <div class="qr-and-store-links">
            <div class="qr-codes">
              <!-- QR Code for Google Play -->
              <a
                href="https://play.google.com/store/apps/details?id=com.example.app"
                target="_blank"
                rel="noopener noreferrer"
              >
                <img
                  src="../../assets/Images/google.png"
                  alt="Google Play QR Code"
                  class="qr-code-img"
                  onerror="this.src='https://placehold.co/120x120/E6E6FA/000000?text=QR+GP'"
                />
              </a>
              <!-- QR Code for App Store -->
              <a
                href="https://apps.apple.com/us/app/example-app/id123456789"
                target="_blank"
                rel="noopener noreferrer"
              >
                <img
                  src="../../assets/Images/apple.png"
                  alt="App Store QR Code"
                  class="qr-code-img"
                  onerror="this.src='https://placehold.co/120x120/E6E6FA/000000?text=QR+AS'"
                />
              </a>
            </div>

            <div class="app-store-buttons">
              <a
                href="https://apps.apple.com/us/app/example-app/id123456789"
                target="_blank"
                rel="noopener noreferrer"
                class="store-button"
              >
                <img
                  src="../../assets/Images/app_store_button.png"
                  alt="Download on the App Store"
                  class="store-button-img"
                  onerror="this.src='https://placehold.co/180x60/333333/FFFFFF?text=App+Store'"
                />
              </a>
              <a
                href="https://play.google.com/store/apps/details?id=com.example.app"
                target="_blank"
                rel="noopener noreferrer"
                class="store-button"
              >
                <img
                  src="../../assets/Images/google_play_button.png"
                  alt="Get it on Google Play"
                  class="store-button-img"
                  onerror="this.src='https://placehold.co/180x60/333333/FFFFFF?text=Google+Play'"
                />
              </a>
            </div>
          </div>
        </div>

        <div class="app-mockups">
          <!-- صورة شاشة التطبيق الواحدة -->
          <img
            src="../../assets/Images/phone.png"
            alt="App Screenshot"
            class="app-screenshot main-screenshot"
            onerror="this.src='https://placehold.co/350x700/9999FF/FFFFFF?text=App+Screen'"
          />
        </div>

        <div class="right-column">
          <!-- منطقة وصف التطبيق وإحصائيات -->
          <p class="app-description">
            تحقق من الأسعار الحية، أرسل الأموال بشكل آمن، تلقى إشعارات والمزيد.
          </p>
          <p class="download-count">أكثر من 70 مليون تنزيل حول العالم</p>
          <!-- هنا يمكن إضافة تقييمات النجوم إذا أردتِ -->
          <div class="ratings">
            <div class="rating-item">
              <span class="rating-label">Google Play</span>
              <div class="stars">
                <i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i
                ><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i
                ><i class="bi bi-star-half"></i>
              </div>
            </div>
            <div class="rating-item">
              <span class="rating-label">App Store</span>
              <div class="stars">
                <i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i
                ><i class="bi bi-star-fill"></i><i class="bi bi-star-fill"></i
                ><i class="bi bi-star-fill"></i>
              </div>
            </div>
          </div>
          <!-- صور تقييمات المستخدمين -->
          <div class="user-avatars">
            <img
              src="https://placehold.co/40x40/FF6347/FFFFFF?text=U1"
              alt="User Avatar 1"
              class="avatar"
            />
            <img
              src="https://placehold.co/40x40/4682B4/FFFFFF?text=U2"
              alt="User Avatar 2"
              class="avatar"
            />
            <img
              src="https://placehold.co/40x40/3CB371/FFFFFF?text=U3"
              alt="User Avatar 3"
              class="avatar"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup></script>

<style scoped>
.download-app-section {
  direction: rtl;
  font-family: "Inter", sans-serif;
  background-color: #f0f2f5;
  padding: 80px var(--app-padding-x);
  display: flex;
  justify-content: center;
  align-items: center;
  color: #333;
  text-align: center;
  overflow: hidden;
}

.section-container {
  max-width: var(--app-max-width);
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 50px;
}

.section-title {
  font-size: 44px;
  font-weight: 800;
  color: #2c1969;
  margin-bottom: 20px;
  line-height: 1.2;
}

.content-wrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  background-image: linear-gradient(to right, #4148b4, #2c1969);
  border-radius: 20px;
  padding: 50px;
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
  color: #fff;
  gap: 30px;
  width: 100%;
}

.left-column,
.right-column {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  text-align: right;
}

.left-column {
  flex: 0.7;
  align-items: flex-start;
  text-align: left;
}

.qr-text {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 20px;
  color: rgba(255, 255, 255, 0.9);
}

.qr-and-store-links {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 20px;
}

.qr-codes {
  display: flex;
  gap: 15px;
}

.qr-code-img {
  width: 120px;
  height: 120px;
  background-color: #fff;
  border-radius: 8px;
  padding: 5px;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
}

.app-store-buttons {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.store-button {
  display: inline-block;
  transition: transform 0.3s ease;
}

.store-button:hover {
  transform: translateY(-5px);
}

.store-button-img {
  width: 180px;
  height: auto;
}

.app-mockups {
  flex: 1.2;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 500px;
}

.app-screenshot {
  width: 350px;
  height: auto;
  border-radius: 30px;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
  object-fit: contain;
  transition: transform 0.4s ease-in-out;
}

.app-screenshot:hover {
  transform: scale(1.05);
}

.right-column {
  flex: 1;
}

.app-description {
  font-size: 20px;
  font-weight: 500;
  line-height: 1.6;
  margin-bottom: 20px;
  color: rgba(255, 255, 255, 0.9);
}

.download-count {
  font-size: 22px;
  font-weight: 700;
  margin-bottom: 30px;
  color: #0aafe1;
}

.ratings {
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin-bottom: 25px;
  align-items: flex-end;
}

.rating-item {
  display: flex;
  align-items: center;
  gap: 10px;
}

.rating-label {
  font-size: 16px;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.9);
}

.stars i {
  color: #ffd700;
  font-size: 18px;
  margin-left: 2px;
}

.user-avatars {
  display: flex;
  gap: 5px;
  align-items: center;
  justify-content: flex-end;
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 2px solid #fff;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}

@media (max-width: 1200px) {
  .content-wrapper {
    flex-direction: column;
    padding: 40px;
  }

  .left-column,
  .right-column {
    flex: none;
    width: 100%;
    align-items: center;
    text-align: center;
  }

  .qr-and-store-links {
    align-items: center;
  }

  .app-mockups {
    flex: none;
    margin-top: 40px;
    margin-bottom: 20px;
    min-height: auto;
    justify-content: center;
  }

  .main-screenshot {
    transform: translateX(0) rotate(0);
    position: relative;
    top: auto;
    left: auto;
    width: 280px;
  }

  .ratings,
  .user-avatars {
    align-items: center;
    justify-content: center;
  }
}

@media (max-width: 768px) {
  .download-app-section {
    padding: 60px var(--app-padding-x);
  }

  .section-title {
    font-size: 36px;
  }

  .content-wrapper {
    padding: 30px;
    gap: 20px;
  }

  .app-description {
    font-size: 18px;
  }

  .download-count {
    font-size: 20px;
  }

  .qr-code-img {
    width: 100px;
    height: 100px;
  }

  .store-button-img {
    width: 160px;
  }

  .app-screenshot {
    width: 240px;
  }

  .stars i {
    font-size: 16px;
  }

  .avatar {
    width: 35px;
    height: 35px;
  }
}

@media (max-width: 576px) {
  .download-app-section {
    padding: 40px var(--app-padding-x);
  }

  .section-title {
    font-size: 30px;
  }

  .content-wrapper {
    padding: 20px;
  }

  .app-description {
    font-size: 16px;
  }

  .download-count {
    font-size: 18px;
  }

  .qr-code-img {
    width: 90px;
    height: 90px;
  }

  .store-button-img {
    width: 140px;
  }

  .app-screenshot {
    width: 200px;
  }

  .stars i {
    font-size: 14px;
  }

  .avatar {
    width: 30px;
    height: 30px;
  }
}
</style>
