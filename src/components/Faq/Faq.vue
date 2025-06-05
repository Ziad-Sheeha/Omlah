<template>
  <section class="faq-section">
    <div class="faq-content-wrapper">
      <h2 class="section-title">الأسئلة الشائعة</h2>

      <div class="accordion-container">
        <div v-for="(item, index) in faqItems" :key="index" class="accordion-item">
          <button @click="toggleAccordion(index)" :aria-expanded="item.isOpen" class="accordion-header">
            <span class="question-text">{{ item.question }}</span>
            <i :class="['bi', item.isOpen ? 'bi-chevron-up' : 'bi-chevron-down']"></i>
          </button>
          <Transition name="accordion">
            <div v-if="item.isOpen" class="accordion-body">
              <p>{{ item.answer }}</p>
            </div>
          </Transition>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
const faqItems = ref([
  {
    question: 'ما هو الحد الأقصى لمبلغ التحويل؟',
    answer: ' Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quis rerum iste at nihil dolorum sequi, iusto, ab totam accusantium odit maiores quia. Iusto ut excepturi recusandae? At aliquam tempore tempora culpa magnam, eligendi animi dolorum vero veritatis, nihil nesciunt eveniet optio amet facilis, laudantium eum? Modi iusto aliquam vel mollitia.',
    isOpen: false
  },
  {
    question: 'كم يستغرق إتمام المعاملة؟',
    answer: ' Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quis rerum iste at nihil dolorum sequi, iusto, ab totam accusantium odit maiores quia. Iusto ut excepturi recusandae? At aliquam tempore tempora culpa magnam, eligendi animi dolorum vero veritatis, nihil nesciunt eveniet optio amet facilis, laudantium eum? Modi iusto aliquam vel mollitia.',
    isOpen: false
  },
  {
    question: 'ما هي المستندات المطلوبة؟',
    answer: ' Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quis rerum iste at nihil dolorum sequi, iusto, ab totam accusantium odit maiores quia. Iusto ut excepturi recusandae? At aliquam tempore tempora culpa magnam, eligendi animi dolorum vero veritatis, nihil nesciunt eveniet optio amet facilis, laudantium eum? Modi iusto aliquam vel mollitia.',
    isOpen: false
  },
  {
    question: 'هل تقدمون خدمات للشركات؟',
    answer: ' Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quis rerum iste at nihil dolorum sequi, iusto, ab totam accusantium odit maiores quia. Iusto ut excepturi recusandae? At aliquam tempore tempora culpa magnam, eligendi animi dolorum vero veritatis, nihil nesciunt eveniet optio amet facilis, laudantium eum? Modi iusto aliquam vel mollitia.',
    isOpen: false
  },
  {
    question: 'ما هي ساعات العمل؟',
    answer: ' Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quis rerum iste at nihil dolorum sequi, iusto, ab totam accusantium odit maiores quia. Iusto ut excepturi recusandae? At aliquam tempore tempora culpa magnam, eligendi animi dolorum vero veritatis, nihil nesciunt eveniet optio amet facilis, laudantium eum? Modi iusto aliquam vel mollitia.',
    isOpen: false
  }
]);

const toggleAccordion = (index) => {
  faqItems.value[index].isOpen = !faqItems.value[index].isOpen;
};
</script>

<style scoped>
.faq-section {
  direction: rtl; 
  font-family: 'Inter', sans-serif; 
  background-color: #f0f2f5;
  padding: 80px var(--app-padding-x);
  display: flex;
  justify-content: center;
  align-items: center;
}

.faq-content-wrapper {
  max-width: var(--app-max-width);
  width: 100%;
  background-color: #fff; 
  border-radius: 20px;
  padding: 40px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
}

.section-title {
  font-size: 38px;
  font-weight: 700;
  color: #2c1969;
  text-align: center;
  margin-bottom: 50px;
}

.accordion-container {
  width: 100%;
  max-width: 800px; 
  margin: 0 auto;
}

.accordion-item {
  border-bottom: 1px solid #eee;
  margin-bottom: 15px;
}

.accordion-item:last-child {
  border-bottom: none; 
  margin-bottom: 0;
}

.accordion-header {
  background-color: #fff;
  color: #2c1969;
  cursor: pointer;
  padding: 20px 25px;
  width: 100%;
  text-align: right; 
  border: none;
  outline: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 18px;
  font-weight: 600;
  transition: background-color 0.3s ease;
  border-radius: 10px; 
}

.accordion-header:hover {
  background-color: #f9f9f9;
}

.accordion-header i {
  margin-right: 15px; 
  transition: transform 0.3s ease;
  color: #0AAFE1; 
  font-size: 1.2em; 
}

.accordion-header[aria-expanded="true"] i {
  transform: rotate(180deg); 
}

.accordion-body {
  padding: 15px 25px 20px;
  background-color: #fdfdfd;
  border-top: 1px solid #eee;
  border-radius: 0 0 10px 10px; 
}

.accordion-body p {
  margin: 0;
  font-size: 16px;
  line-height: 1.7;
  color: #555;
  text-align: right; 
}


.accordion-enter-active,
.accordion-leave-active {
  transition: all 0.3s ease-out;
  max-height: 500px; 
  overflow: hidden;
}

.accordion-enter-from,
.accordion-leave-to {
  max-height: 0;
  opacity: 0;
  transform: translateY(-10px);
}

@media (max-width: 768px) {
  .faq-section {
    padding: 60px var(--app-padding-x);
  }

  .faq-content-wrapper {
    padding: 30px;
  }

  .section-title {
    font-size: 32px;
    margin-bottom: 40px;
  }

  .accordion-header {
    font-size: 16px;
    padding: 15px 20px;
  }

  .accordion-header i {
    font-size: 1.1em;
    margin-right: 10px;
  }

  .accordion-body {
    padding: 10px 20px 15px;
  }

  .accordion-body p {
    font-size: 14px;
  }
}

@media (max-width: 480px) {
  .faq-section {
    padding: 40px var(--app-padding-x);
  }

  .faq-content-wrapper {
    padding: 20px;
  }

  .section-title {
    font-size: 26px;
    margin-bottom: 30px;
  }

  .accordion-header {
    font-size: 15px;
    padding: 12px 15px;
  }

  .accordion-header i {
    font-size: 1em;
    margin-right: 8px;
  }

  .accordion-body {
    padding: 8px 15px 12px;
  }

  .accordion-body p {
    font-size: 13px;
  }
}
</style>