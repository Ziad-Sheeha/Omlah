<template>
  <section class="currency-converter-section">
    <div class="converter-header">
      <h2 class="title">محول العملات في عملة</h2>
      <p class="subtitle">تحقق من أسعار صرف العملات الأجنبية المباشرة</p>
      <div class="separator"></div>
      <h3 class="action-title">
        تبديل <i class="bi bi-currency-exchange"></i> </h3>
    </div>

    <div class="converter-content-wrapper">
      <div class="how-it-works-card white-card">
        <h3>
          مع عملة، يمكنك تقديم طلب <br />
          لتغيير العملة في ثلاث خطوات فقط
        </h3>
        <div class="steps-list">
          <div class="step-item">
            {{ fromAmount.toFixed(2) }} {{ fromCurrency }}
          </div>
          <div class="step-item">
            {{ toAmount.toFixed(2) }} {{ toCurrency }}
          </div>
          <div class="step-item">
            {{ stepsListExchangeRateValue }}
            {{ stepsListExchangeRateCurrencyCode }}
          </div>
          <div class="step-item">
            {{ calculatedFee.toFixed(2) }} {{ fromCurrency }}
          </div>
          <div class="step-item">
            {{ calculatedTax.toFixed(2) }} {{ fromCurrency }}
          </div>
          <div class="step-item">
            {{ totalToPay.toFixed(2) }} {{ fromCurrency }}
          </div>
          <div class="step-item">
            {{ toAmount.toFixed(2) }} {{ toCurrency }}
          </div>
        </div>
        <button class="start-button">
          ابدأ <i class="bi bi-arrow-left"></i>
        </button>
      </div>

      <div class="conversion-form-card">
        <div class="input-group">
          <label for="fromAmount">الكمية</label>
          <div class="currency-input-container">
            <input
              type="number"
              id="fromAmount"
              v-model.number="fromAmount"
              @input="convertCurrency('from')"
              placeholder="0"
              min="0"
              class="currency-input"
            />
            <div class="currency-selector-display">
              <img
                :src="getSelectedCurrencyFlagUrl(fromCurrency)"
                :alt="getSelectedCurrencyName(fromCurrency)"
                class="selected-currency-flag"
              />
              <span class="selected-currency-name">{{
                getSelectedCurrencyName(fromCurrency)
              }}</span>
              <span class="selected-currency-code-display">{{
                fromCurrency
              }}</span>
            </div>
            <select
              v-model="fromCurrency"
              @change="convertCurrency('from')"
              class="currency-select"
            >
              <option
                v-for="currency in currencies"
                :key="currency.code"
                :value="currency.code"
              >
                {{ currency.name }}
              </option>
            </select>
          </div>
        </div>

        <div class="swap-row-with-label">
          <span class="action-label">إلى</span>
          <div class="swap-buy-controls">
            <span class="buy-label">شراء</span>
            <button
              @click="swapCurrencies"
              class="swap-button"
              title="تبديل العملات"
            >
              <i class="bi bi-currency-exchange"></i>
            </button>
          </div>
        </div>

        <div class="input-group">
          <label for="toAmount">الإجمالي المستلم</label>
          <div class="currency-input-container">
            <input
              type="number"
              id="toAmount"
              v-model.number="toAmount"
              @input="convertCurrency('to')"
              placeholder="0"
              min="0"
              class="currency-input"
            />
            <div class="currency-selector-display">
              <img
                :src="getSelectedCurrencyFlagUrl(toCurrency)"
                :alt="getSelectedCurrencyName(toCurrency)"
                class="selected-currency-flag"
              />
              <span class="selected-currency-name">{{
                getSelectedCurrencyName(toCurrency)
              }}</span>
              <span class="selected-currency-code-display">{{
                toCurrency
              }}</span>
            </div>
            <select
              v-model="toCurrency"
              @change="convertCurrency('to')"
              class="currency-select"
            >
              <option
                v-for="currency in currencies"
                :key="currency.code"
                :value="currency.code"
              >
                {{ currency.name }}
              </option>
            </select>
          </div>
        </div>

        <div class="details-row">
          <span class="detail-label">سعر الصرف</span>
          <span class="detail-value">{{ displayExchangeRate }}</span>
        </div>
        <div class="details-row">
          <span class="detail-label">الرسوم</span>
          <span class="detail-value">{{ displayFee }}</span>
        </div>
        <div class="details-row">
          <span class="detail-label">ضريبة</span>
          <span class="detail-value">{{ displayTax }}</span>
        </div>
        <div class="details-row total-row">
          <span class="detail-label">المجموع للدفع</span>
          <span class="detail-value">{{ displayTotalToPay }}</span>
        </div>
        <div class="details-row total-row">
          <span class="detail-label">الإجمالي المستلم</span>
          <span class="detail-value">{{ displayTotalReceived }}</span>
        </div>

        <button class="add-button">
          <i class="bi bi-plus-lg"></i>
        </button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "CurrencyConverterSection",
  data() {
    return {
      fromAmount: 100, // قيمة ابتدائية لتظهر في الكارد
      toAmount: 0,
      fromCurrency: "SAR",
      toCurrency: "USD",
      exchangeRate: 0,
      feePercentage: 0.01, // 1% fee
      taxPercentage: 0.005, // 0.5% tax
      currencies: [
        {
          code: "SAR",
          name: "ريال سعودي",
          flag: "🇸🇦",
          imageUrl: "https://flagcdn.com/24x18/sa.png", // استخدام flags.fmcdn.com
        },
        {
          code: "USD",
          name: "دولار أمريكي",
          flag: "🇺🇸",
          imageUrl: "https://flagcdn.com/24x18/us.png",
        },
        {
          code: "EUR",
          name: "يورو",
          flag: "🇪🇺",
          imageUrl: "https://flagcdn.com/24x18/eu.png",
        },
        {
          code: "GBP",
          name: "جنيه استرليني",
          flag: "🇬🇧",
          imageUrl: "https://flagcdn.com/24x18/gb.png",
        },
        {
          code: "CHF",
          name: "فرنك سويسري",
          flag: "🇨🇭",
          imageUrl: "https://flagcdn.com/24x18/ch.png",
        },
        {
          code: "CAD",
          name: "دولار كندي",
          flag: "🇨🇦",
          imageUrl: "https://flagcdn.com/24x18/ca.png",
        },
        {
          code: "AED",
          name: "درهم إماراتي",
          flag: "🇦🇪",
          imageUrl: "https://flagcdn.com/24x18/ae.png",
        },
        {
          code: "QAR",
          name: "ريال قطري",
          flag: "🇶🇦",
          imageUrl: "https://flagcdn.com/24x18/qa.png",
        },
        {
          code: "OMR",
          name: "ريال عماني",
          flag: "🇴🇲",
          imageUrl: "https://flagcdn.com/24x18/om.png",
        },
        {
          code: "KWD",
          name: "دينار كويتي",
          flag: "🇰🇼",
          imageUrl: "https://flagcdn.com/24x18/kw.png",
        },
        {
          code: "JPY",
          name: "ين ياباني",
          flag: "🇯🇵",
          imageUrl: "https://flagcdn.com/24x18/jp.png",
        },
      ],
      // Dummy exchange rates (SAR based)
      dummyExchangeRates: {
        SAR_USD: 0.2667, // 1 SAR = 0.2667 USD
        USD_SAR: 3.75, // 1 USD = 3.75 SAR
        SAR_EUR: 0.245,
        EUR_SAR: 4.08,
        SAR_GBP: 0.21,
        GBP_SAR: 4.76,
        SAR_CHF: 0.24,
        CHF_SAR: 4.16,
        SAR_CAD: 0.36,
        CAD_SAR: 2.77,
        SAR_AED: 0.977,
        AED_SAR: 1.023,
        SAR_QAR: 0.974,
        QAR_SAR: 1.026,
        SAR_OMR: 0.102,
        OMR_SAR: 9.77,
        SAR_KWD: 0.081,
        KWD_SAR: 12.34,
        SAR_JPY: 39.5,
        JPY_SAR: 0.0253,
      },
    };
  },
  computed: {
    displayExchangeRate() {
      if (this.exchangeRate === 0) return "---";
      return `1 ${this.fromCurrency} = ${this.exchangeRate.toFixed(4)} ${
        this.toCurrency
      }`;
    },
    stepsListExchangeRateValue() {
      if (this.exchangeRate === 0) return "---";
      return this.exchangeRate.toFixed(4);
    },
    stepsListExchangeRateCurrencyCode() {
      return this.toCurrency;
    },
    calculatedFee() {
      return this.fromAmount * this.feePercentage;
    },
    displayFee() {
      return `${this.calculatedFee.toFixed(2)} ${this.fromCurrency}`;
    },
    calculatedTax() {
      return this.fromAmount * this.taxPercentage;
    },
    displayTax() {
      return `${this.calculatedTax.toFixed(2)} ${this.fromCurrency}`;
    },
    totalToPay() {
      return this.fromAmount + this.calculatedFee + this.calculatedTax;
    },
    displayTotalToPay() {
      return `${this.totalToPay.toFixed(2)} ${this.fromCurrency}`;
    },
    displayTotalReceived() {
      return `${this.toAmount.toFixed(2)} ${this.toCurrency}`;
    },
  },
  watch: {
    fromCurrency: "updateExchangeRate",
    toCurrency: "updateExchangeRate",
  },
  mounted() {
    this.updateExchangeRate();
    this.convertCurrency("from");
  },
  methods: {
    updateExchangeRate() {
      const key = `${this.fromCurrency}_${this.toCurrency}`;
      const reverseKey = `${this.toCurrency}_${this.fromCurrency}`;

      if (this.dummyExchangeRates[key]) {
        this.exchangeRate = this.dummyExchangeRates[key];
      } else if (this.dummyExchangeRates[reverseKey]) {
        this.exchangeRate = 1 / this.dummyExchangeRates[reverseKey];
      } else if (this.fromCurrency === this.toCurrency) {
        this.exchangeRate = 1;
      } else {
        const sarToBaseFrom =
          this.dummyExchangeRates[`SAR_${this.fromCurrency}`] || 1;
        const sarToBaseTo =
          this.dummyExchangeRates[`SAR_${this.toCurrency}`] || 1;

        if (sarToBaseFrom && sarToBaseTo) {
          this.exchangeRate = sarToBaseTo / sarToBaseFrom;
        } else {
          this.exchangeRate = 0;
        }
      }

      this.convertCurrency("from");
    },
    convertCurrency(source) {
      if (
        this.exchangeRate === 0 ||
        isNaN(this.fromAmount) ||
        isNaN(this.toAmount) ||
        this.fromAmount < 0 ||
        this.toAmount < 0
      ) {
        if (
          source === "from" &&
          (this.fromAmount <= 0 || isNaN(this.fromAmount))
        ) {
          this.toAmount = 0;
        } else if (
          source === "to" &&
          (this.toAmount <= 0 || isNaN(this.toAmount))
        ) {
          this.fromAmount = 0;
        }
        return;
      }

      if (source === "from") {
        this.toAmount = this.fromAmount * this.exchangeRate;
      } else {
        this.fromAmount = this.toAmount / this.exchangeRate;
      }

      this.fromAmount = Math.max(0, parseFloat(this.fromAmount.toFixed(2)));
      this.toAmount = Math.max(0, parseFloat(this.toAmount.toFixed(2)));
    },
    swapCurrencies() {
      [this.fromCurrency, this.toCurrency] = [
        this.toCurrency,
        this.fromCurrency,
      ];
      [this.fromAmount, this.toAmount] = [this.toAmount, this.fromAmount];
      this.updateExchangeRate();
    },
    getSelectedCurrencyFlagUrl(code) {
      const currency = this.currencies.find((c) => c.code === code);
      return currency ? currency.imageUrl : "";
    },
    getSelectedCurrencyName(code) {
      const currency = this.currencies.find((c) => c.code === code);
      return currency ? currency.name : "";
    },
  },
};
</script>

<style scoped>
.currency-converter-section {
  direction: rtl;
  font-family: "Inter", sans-serif;
  background-color: #f0f2f5;
  padding: 60px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 40px;
}

.converter-header {
  text-align: center;
  margin-bottom: 20px;
  max-width: 800px;
}

.converter-header .title {
  font-size: 38px;
  font-weight: 700;
  color: #2c1969;
  margin-bottom: 10px;
}

.converter-header .subtitle {
  font-size: 18px;
  color: #555;
  margin-bottom: 20px;
  line-height: 1.6;
}

.converter-header .separator {
  width: 100px;
  height: 4px;
  background-color: #0aafe1;
  margin: 0 auto 20px;
  border-radius: 2px;
}

.converter-header .action-title {
  font-size: 28px;
  font-weight: 600;
  color: #2c1969;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.converter-header .action-title i {
  color: #0aafe1;
  font-size: 24px;
}

.converter-content-wrapper {
  display: flex;
  justify-content: center;
  align-items: stretch; 
  gap: 40px;
  max-width: 1200px;
  width: 100%;
}

.how-it-works-card {
  flex: 1;
  background-color: #ffffff; 
  color: #333; 
  border-radius: 15px;
  padding: 30px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  max-width: 400px;
  text-align: right;
}

.how-it-works-card h3 {
  font-size: 24px;
  font-weight: 700;
  line-height: 1.4;
  margin-bottom: 30px;
  color: #2c1969; 
}

.how-it-works-card .steps-list {
  display: flex;
  flex-direction: column;
  gap: 15px;
  margin-bottom: 40px;
  font-size: 18px;
}

.how-it-works-card .step-item {
  background-color: #f5f5f5; 
  padding: 10px 15px;
  border-radius: 8px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  gap: 10px;
  color: #444; 
}

.how-it-works-card .start-button {
  background-color: #0aafe1; 
  color: #fff; 
  border: none;
  padding: 12px 25px;
  border-radius: 30px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease, color 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: fit-content;
  margin-right: auto;
  margin-top: auto;
}

.how-it-works-card .start-button:hover {
  background-color: #089fd3; 
  color: #fff; 
}

.how-it-works-card .start-button i {
  font-size: 18px;
}

.conversion-form-card {
  flex: 2;
  background-color: #ffffff;
  border-radius: 15px;
  padding: 30px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  gap: 20px;
  max-width: 700px;
}

.input-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
  text-align: right;
}

.input-group label {
  font-size: 14px;
  color: #666;
  font-weight: 500;
}

.currency-input-container {
  display: flex;
  background-image: linear-gradient(
    to right,
    #4148b4,
    #2c1969
  );
  border-radius: 10px;
  overflow: hidden;
  position: relative;
  height: 60px;
  align-items: center;
}

.currency-input {
  background-color: transparent;
  border: none;
  color: #fff;
  padding: 10px 15px;
  padding-right: 170px;
  font-size: 24px;
  font-weight: 700;
  flex-grow: 1;
  outline: none;
  text-align: right;
  box-sizing: border-box;
}

.currency-input::placeholder {
  color: rgba(255, 255, 255, 0.7);
}

.currency-selector-display {
  position: absolute;
  right: 0;
  height: 100%;
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 0 15px;
  color: #fff;
  font-size: 16px;
  font-weight: 600;
  background-image: linear-gradient(
    to right,
    #2c1969,
    #4148b4
  );
  border-radius: 10px 0 0 10px;
  white-space: nowrap;
  z-index: 2;
  pointer-events: none;
}

.selected-currency-flag {
  width: 24px;
  height: 16px;
  border-radius: 2px;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.2);
}

.selected-currency-code-display {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.7);
  margin-right: 5px;
}

.currency-select {
  position: absolute;
  top: 0;
  right: 0;
  width: 170px;
  height: 100%;
  opacity: 0;
  cursor: pointer;
  z-index: 5;
}

.swap-row-with-label {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 10px 0;
  width: 100%;
  gap: 10px;
}

.swap-buy-controls {
  display: flex;
  align-items: center;
  gap: 10px;
}

.swap-button {
  background-color: #0aafe1;
  color: #fff;
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  font-size: 18px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  transition: background-color 0.3s ease;
  z-index: 5;
}

.swap-button:hover {
  background-color: #089fd3;
}

.buy-label {
  background-color: #e0e0e0;
  color: #333;
  padding: 8px 15px;
  border-radius: 20px;
  font-size: 14px;
  font-weight: 600;
  white-space: nowrap;
}

.action-label {
  font-size: 14px;
  color: #666;
  font-weight: 500;
  text-align: right;
  flex-grow: 1;
  margin-right: 0;
}

.details-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 0;
  border-bottom: 1px solid #eee;
  font-size: 16px;
  color: #444;
}

.details-row:last-of-type {
  border-bottom: none;
}

.details-row .detail-label {
  font-weight: 500;
  color: #666;
}

.details-row .detail-value {
  font-weight: 600;
  color: #2c1969;
}

.total-row .detail-value {
  font-size: 18px;
  font-weight: 700;
  color: #0aafe1;
}

.add-button {
  background-color: #2c1969;
  color: #fff;
  border: none;
  padding: 15px 30px;
  border-radius: 10px;
  font-size: 18px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease;
  width: 100%;
  margin-top: 20px;
}

.add-button:hover {
  background-color: #3f2a8a;
}

.add-button i {
  font-size: 20px;
}

@media (max-width: 992px) {
  .converter-content-wrapper {
    flex-direction: column;
    align-items: center;
    gap: 30px;
  }

  .how-it-works-card,
  .conversion-form-card {
    width: 100%;
    max-width: 500px;
  }

  .converter-header .title {
    font-size: 32px;
  }

  .converter-header .subtitle {
    font-size: 16px;
  }

  .converter-header .action-title {
    font-size: 24px;
  }
}

@media (max-width: 576px) {
  .currency-converter-section {
    padding: 40px 15px;
  }

  .converter-header .title {
    font-size: 28px;
  }

  .converter-header .action-title {
    font-size: 20px;
  }

  .how-it-works-card h3 {
    font-size: 20px;
  }

  .how-it-works-card .steps-list {
    font-size: 16px;
    gap: 10px;
  }

  .how-it-works-card .start-button {
    font-size: 15px;
    padding: 10px 20px;
  }

  .currency-input {
    font-size: 20px;
    padding-right: 150px;
  }

  .currency-selector-display {
    padding: 0 10px;
    gap: 5px;
  }

  .selected-currency-name {
    font-size: 14px;
  }

  .selected-currency-code-display {
    font-size: 12px;
  }

  .currency-select {
    right: 0;
    width: 150px;
  }

  .details-row,
  .total-row {
    font-size: 15px;
  }

  .total-row .detail-value {
    font-size: 16px;
  }

  .add-button {
    font-size: 16px;
    padding: 12px 25px;
  }

  .swap-row-with-label {
    flex-direction: column;
    align-items: flex-end;
  }
  .buy-label {
    margin-left: 0;
    margin-top: 10px;
  }
  .swap-buy-controls {
    width: 100%;
    justify-content: flex-end;
  }
}
</style>