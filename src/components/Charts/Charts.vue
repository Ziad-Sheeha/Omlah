<template>
  <section class="chart-section">
    <h2 class="section-title">الرسوم البيانية</h2>

    <div class="chart-controls">
      <div class="time-range-buttons">
        <button
          v-for="range in timeRanges"
          :key="range.value"
          :class="{ active: selectedTimeRange === range.value }"
          @click="selectTimeRange(range.value)"
        >
          {{ range.label }}
        </button>
      </div>

      <div class="currency-selectors">
        <div class="currency-select-wrapper">
          <select v-model="fromCurrency" @change="updateChartData">
            <option
              v-for="currency in currencies"
              :key="currency.code"
              :value="currency.code"
            >
              {{ currency.name }} ({{ currency.code }})
            </option>
          </select>
          <div class="selected-currency-display">
            <img
              :src="getSelectedCurrencyFlagUrl(fromCurrency)"
              :alt="getSelectedCurrencyName(fromCurrency)"
              class="currency-flag"
            />
            <span>{{ getSelectedCurrencyName(fromCurrency) }}</span>
          </div>
        </div>
        <span class="compare-text">قارن بين عملتين</span>
        <div class="currency-select-wrapper">
          <select v-model="toCurrency" @change="updateChartData">
            <option
              v-for="currency in currencies"
              :key="currency.code"
              :value="currency.code"
            >
              {{ currency.name }} ({{ currency.code }})
            </option>
          </select>
          <div class="selected-currency-display">
            <img
              :src="getSelectedCurrencyFlagUrl(toCurrency)"
              :alt="getSelectedCurrencyName(toCurrency)"
              class="currency-flag"
            />
            <span>{{ getSelectedCurrencyName(toCurrency) }}</span>
          </div>
        </div>
      </div>
    </div>

    <div class="chart-container">
      <LineChart :data="chartData" :options="chartOptions" :key="chartKey" />
    </div>
  </section>
</template>

<script>
import { Line as LineChart } from 'vue-chartjs';
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  LineElement,
  CategoryScale,
  LinearScale,
  PointElement,
  Filler 
} from 'chart.js';

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  LineElement,
  CategoryScale,
  LinearScale,
  PointElement,
  Filler
);

const ALL_CURRENCIES = [
  { code: "SAR", name: "ريال سعودي", imageUrl: "https://placehold.co/24x16/007A3D/FFFFFF?text=SA" },
  { code: "USD", name: "دولار أمريكي", imageUrl: "https://placehold.co/24x16/3C3B6E/FFFFFF?text=US" },
  { code: "EUR", name: "يورو", imageUrl: "https://placehold.co/24x16/003399/FFD700?text=EU" },
  { code: "GBP", name: "جنيه استرليني", imageUrl: "https://placehold.co/24x16/00247D/FFFFFF?text=GB" },
  { code: "CHF", name: "فرنك سويسري", imageUrl: "https://placehold.co/24x16/D52B1E/FFFFFF?text=CH" },
  { code: "CAD", name: "دولار كندي", imageUrl: "https://placehold.co/24x16/FF0000/FFFFFF?text=CA" },
  { code: "AED", name: "درهم إماراتي", imageUrl: "https://placehold.co/24x16/007321/FFFFFF?text=AE" },
  { code: "QAR", name: "ريال قطري", imageUrl: "https://placehold.co/24x16/800000/FFFFFF?text=QA" },
  { code: "OMR", name: "ريال عماني", imageUrl: "https://placehold.co/24x16/DC143C/FFFFFF?text=OM" },
  { code: "KWD", name: "دينار كويتي", imageUrl: "https://placehold.co/24x16/007A3D/FFFFFF?text=KW" },
  { code: "JPY", name: "ين ياباني", imageUrl: "https://placehold.co/24x16/BC002D/FFFFFF?text=JP" },
];

const DUMMY_HISTORICAL_RATES = {
  'SAR_USD': {
    '1_day': Array.from({ length: 24 }, (_, i) => 0.2667 + (Math.random() - 0.5) * 0.0002).map(val => parseFloat(val.toFixed(4))),
    '7_days': Array.from({ length: 7 }, (_, i) => 0.2667 + (Math.random() - 0.5) * 0.0005).map(val => parseFloat(val.toFixed(4))),
    '30_days': Array.from({ length: 30 }, (_, i) => 0.2667 + (Math.random() - 0.5) * 0.0005).map(val => parseFloat(val.toFixed(4))),
    '90_days': Array.from({ length: 90 }, (_, i) => 0.2667 + (Math.random() - 0.5) * 0.001).map(val => parseFloat(val.toFixed(4))),
  },
  'USD_SAR': {
    '1_day': Array.from({ length: 24 }, (_, i) => 3.75 + (Math.random() - 0.5) * 0.005).map(val => parseFloat(val.toFixed(4))),
    '7_days': Array.from({ length: 7 }, (_, i) => 3.75 + (Math.random() - 0.5) * 0.008).map(val => parseFloat(val.toFixed(4))),
    '30_days': Array.from({ length: 30 }, (_, i) => 3.75 + (Math.random() - 0.5) * 0.008).map(val => parseFloat(val.toFixed(4))),
    '90_days': Array.from({ length: 90 }, (_, i) => 3.75 + (Math.random() - 0.5) * 0.015).map(val => parseFloat(val.toFixed(4))),
  },
  'SAR_EUR': {
    '1_day': Array.from({ length: 24 }, (_, i) => 0.245 + (Math.random() - 0.5) * 0.0003).map(val => parseFloat(val.toFixed(4))),
    '7_days': Array.from({ length: 7 }, (_, i) => 0.245 + (Math.random() - 0.5) * 0.0007).map(val => parseFloat(val.toFixed(4))),
    '30_days': Array.from({ length: 30 }, (_, i) => 0.245 + (Math.random() - 0.5) * 0.0007).map(val => parseFloat(val.toFixed(4))),
    '90_days': Array.from({ length: 90 }, (_, i) => 0.245 + (Math.random() - 0.5) * 0.0015).map(val => parseFloat(val.toFixed(4))),
  },
  'EUR_SAR': {
    '1_day': Array.from({ length: 24 }, (_, i) => 4.08 + (Math.random() - 0.5) * 0.008).map(val => parseFloat(val.toFixed(4))),
    '7_days': Array.from({ length: 7 }, (_, i) => 4.08 + (Math.random() - 0.5) * 0.01).map(val => parseFloat(val.toFixed(4))),
    '30_days': Array.from({ length: 30 }, (_, i) => 4.08 + (Math.random() - 0.5) * 0.01).map(val => parseFloat(val.toFixed(4))),
    '90_days': Array.from({ length: 90 }, (_, i) => 4.08 + (Math.random() - 0.5) * 0.02).map(val => parseFloat(val.toFixed(4))),
  },
  'USD_EUR': {
    '1_day': Array.from({ length: 24 }, (_, i) => 0.92 + (Math.random() - 0.5) * 0.003).map(val => parseFloat(val.toFixed(4))),
    '7_days': Array.from({ length: 7 }, (_, i) => 0.92 + (Math.random() - 0.5) * 0.005).map(val => parseFloat(val.toFixed(4))),
    '30_days': Array.from({ length: 30 }, (_, i) => 0.92 + (Math.random() - 0.5) * 0.005).map(val => parseFloat(val.toFixed(4))),
    '90_days': Array.from({ length: 90 }, (_, i) => 0.92 + (Math.random() - 0.5) * 0.008).map(val => parseFloat(val.toFixed(4))),
  },
  'EUR_USD': {
    '1_day': Array.from({ length: 24 }, (_, i) => 1.087 + (Math.random() - 0.5) * 0.005).map(val => parseFloat(val.toFixed(4))),
    '7_days': Array.from({ length: 7 }, (_, i) => 1.087 + (Math.random() - 0.5) * 0.007).map(val => parseFloat(val.toFixed(4))),
    '30_days': Array.from({ length: 30 }, (_, i) => 1.087 + (Math.random() - 0.5) * 0.007).map(val => parseFloat(val.toFixed(4))),
    '90_days': Array.from({ length: 90 }, (_, i) => 1.087 + (Math.random() - 0.5) * 0.01).map(val => parseFloat(val.toFixed(4))),
  },
};


export default {
  name: "ChartSection",
  components: {
    LineChart, 
  },
  data() {
    return {
      currencies: ALL_CURRENCIES,
      fromCurrency: "SAR",
      toCurrency: "USD",
      selectedTimeRange: "1_day",

      timeRanges: [
        { label: "يوم واحد", value: "1_day" },
        { label: "7 أيام", value: "7_days" },
        { label: "30 يوم", value: "30_days" },
        { label: "90 يوم", value: "90_days" },
      ],
      chartData: {
        labels: [],
        datasets: [],
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          title: {
            display: false,
          },
          tooltip: {
            mode: 'index',
            intersect: false,
            callbacks: {
                label: function(context) {
                    let label = context.dataset.label || '';
                    if (label) {
                        label += ': ';
                    }
                    if (context.parsed.y !== null) {
                        label += new Intl.NumberFormat('ar-EG', { minimumFractionDigits: 4, maximumFractionDigits: 4 }).format(context.parsed.y);
                    }
                    return label;
                }
            }
          },
          legend: {
            display: true,
            position: 'top',
            labels: {
              font: {
                family: 'Inter, sans-serif',
                size: 14,
              },
              color: '#333',
            },
            rtl: true, 
            textDirection: 'rtl',
          }
        },
        scales: {
          x: {
            grid: {
              display: false, 
            },
            ticks: {
              color: '#666',
              font: {
                family: 'Inter, sans-serif',
              },
            },
          },
          y: {
            grid: {
              color: '#e7e7e7', 
            },
            ticks: {
              callback: function (value) {
                return value.toFixed(4); 
              },
              color: '#666',
              font: {
                family: 'Inter, sans-serif',
              },
            },
          },
        },
        animation: {
            duration: 750, 
            easing: 'easeInOutQuad'
        },
    
      },
      chartKey: 0,
    };
  },
  mounted() {
    this.updateChartData(); 
  },
  methods: {
    getSelectedCurrencyFlagUrl(code) {
      const currency = this.currencies.find((c) => c.code === code);
      return currency ? currency.imageUrl : "";
    },
    getSelectedCurrencyName(code) {
      const currency = this.currencies.find((c) => c.code === code);
      return currency ? currency.name : "";
    },
    selectTimeRange(range) {
      this.selectedTimeRange = range;
      this.updateChartData(); 
    },
    generateChartCategories(range) {
      const today = new Date();
      const categories = [];
      let numPoints;

      switch (range) {
        case '1_day':
          numPoints = 24; 
          for (let i = 0; i < numPoints; i++) {
            categories.push(`${i}:00`); 
          }
          break;
        case '7_days':
          numPoints = 7;
          for (let i = 0; i < numPoints; i++) {
            const d = new Date(today);
            d.setDate(today.getDate() - (numPoints - 1 - i));
            categories.push(d.toLocaleDateString('ar-EG', { month: 'short', day: 'numeric' }));
          }
          break;
        case '30_days':
          numPoints = 30;
          for (let i = 0; i < numPoints; i++) {
            const d = new Date(today);
            d.setDate(today.getDate() - (numPoints - 1 - i));
            categories.push(d.toLocaleDateString('ar-EG', { month: 'short', day: 'numeric' }));
          }
          break;
        case '90_days':
          numPoints = 90;
          for (let i = 0; i < numPoints; i++) {
            const d = new Date(today);
            d.setDate(today.getDate() - (numPoints - 1 - i));
            categories.push(d.toLocaleDateString('ar-EG', { month: 'short', day: 'numeric' }));
          }
          break;
        default:
          numPoints = 1;
          categories.push(today.toLocaleDateString('ar-EG', { day: 'numeric', month: 'numeric' }));
      }
      return categories;
    },
    getExchangeRateData(from, to, range) {
        const key = `${from}_${to}`;
        const reverseKey = `${to}_${from}`;

        if (DUMMY_HISTORICAL_RATES[key] && DUMMY_HISTORICAL_RATES[key][range]) {
            return DUMMY_HISTORICAL_RATES[key][range];
        }

        if (DUMMY_HISTORICAL_RATES[reverseKey] && DUMMY_HISTORICAL_RATES[reverseKey][range]) {
            return DUMMY_HISTORICAL_RATES[reverseKey][range].map(rate => 1 / rate);
        }

        const numDataPoints = this.generateChartCategories(range).length;
        const avgRate = 0.5; 
        return Array.from({ length: numDataPoints }, () => avgRate + (Math.random() - 0.5) * 0.01).map(val => parseFloat(val.toFixed(4)));
    },
    updateChartData() {
        const labels = this.generateChartCategories(this.selectedTimeRange);
        const rates = this.getExchangeRateData(this.fromCurrency, this.toCurrency, this.selectedTimeRange);

        this.chartData = {
            labels: labels,
            datasets: [
                {
                    label: `${this.getSelectedCurrencyName(this.fromCurrency)} مقابل ${this.getSelectedCurrencyName(this.toCurrency)}`,
                    backgroundColor: 'rgba(10, 175, 225, 0.3)',
                    borderColor: '#0aafe1', 
                    pointBackgroundColor: '#0aafe1',
                    pointBorderColor: '#fff',
                    pointHoverBackgroundColor: '#fff',
                    pointHoverBorderColor: '#0aafe1',
                    data: rates,
                    tension: 0.3, 
                    fill: true, 
                },
            ],
        };
        this.chartKey++; 
    },
  },
};
</script>

<style scoped>
.chart-section {
  direction: rtl;
  font-family: "Inter", sans-serif;
  background-color: #ffffff;
  padding: 40px 20px;
  margin: 20px auto;
  max-width: 1200px;
  border-radius: 15px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 30px;
}

.section-title {
  font-size: 32px;
  font-weight: 700;
  color: #2c1969;
  text-align: center;
  margin-bottom: 20px;
}

.chart-controls {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  flex-wrap: wrap-reverse; 
  gap: 20px;
}

.time-range-buttons {
  display: flex;
  background-color: #f0f2f5;
  border-radius: 10px;
  overflow: hidden;
  flex-grow: 1; 
  max-width: 400px; 
  margin-left: auto; 
}

.time-range-buttons button {
  flex: 1;
  padding: 10px 15px;
  border: none;
  background-color: transparent;
  color: #555;
  font-size: 15px;
  font-weight: 500;
  cursor: pointer;
  transition: background-color 0.3s ease, color 0.3s ease;
  white-space: nowrap;
}

.time-range-buttons button.active {
  background-image: linear-gradient(
    to left,
    #4148b4,
    #2c1969
  ); 
  color: #fff;
  font-weight: 600;
}

.time-range-buttons button:hover:not(.active) {
  background-color: #e0e0e0;
}

.currency-selectors {
  display: flex;
  align-items: center;
  gap: 15px;
  flex-grow: 1; 
  justify-content: flex-end; 
}

.currency-select-wrapper {
  position: relative;
  background-color: #f0f2f5;
  border-radius: 10px;
  overflow: hidden;
  height: 45px;
  display: flex;
  align-items: center;
  width: 180px; 
}

.currency-select-wrapper select {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  cursor: pointer;
  z-index: 2; 
}

.selected-currency-display {
  position: absolute;
  top: 0;
  right: 0; 
  height: 100%;
  width: 100%; 
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 0 15px;
  color: #333;
  font-size: 15px;
  font-weight: 600;
  pointer-events: none; 
  background-color: transparent; 
  border-radius: 10px;
  justify-content: flex-end; 
}

.currency-flag {
  width: 24px;
  height: 16px;
  border-radius: 2px;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.1);
  margin-right: 5px; 
}

.compare-text {
  font-size: 16px;
  color: #666;
  white-space: nowrap;
}

.chart-container {
  width: 100%;
  height: 350px; 
  background-color: #f9f9f9;
  border-radius: 10px;
  padding: 20px;
  box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.05);
}

@media (max-width: 992px) {
  .chart-controls {
    flex-direction: column;
    align-items: center;
    gap: 25px;
  }
  .time-range-buttons {
    width: 100%;
    max-width: none;
    margin: 0; 
  }
  .currency-selectors {
    flex-direction: column;
    gap: 15px;
    width: 100%;
    align-items: center;
    justify-content: center; 
  }
  .currency-select-wrapper {
    width: 80%; 
    max-width: 250px;
  }
  .section-title {
    font-size: 28px;
  }
}

@media (max-width: 576px) {
  .chart-section {
    padding: 30px 15px;
    margin: 15px auto;
  }
  .section-title {
    font-size: 24px;
  }
  .time-range-buttons {
    flex-wrap: wrap; 
    justify-content: center;
    gap: 5px; 
  }
  .time-range-buttons button {
    font-size: 14px;
    padding: 8px 12px;
  }
  .currency-select-wrapper {
    width: 100%;
    max-width: 200px;
  }
  .selected-currency-display {
    font-size: 14px;
    padding: 0 10px;
  }
  .compare-text {
    font-size: 15px;
  }
  .chart-container {
    padding: 10px;
    height: 300px; 
  }
}
</style>