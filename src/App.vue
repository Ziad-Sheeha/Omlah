<script setup>

import Header from './components/Header/Header.vue'
  import MainSection from './components/MainSection/MainSection.vue'
  import Services from './components/services/Services.vue';
  import Start from './components/Start/Start.vue';
    import About from './components/About/About.vue';
    import Currency from './components/Currency/Currency.vue'
    import Charts from './components/Charts/Charts.vue'
    import Download from './components/Download/Download.vue'
    import Contact from './components/Contact/Contact.vue'
    import Faq from './components/Faq/Faq.vue'
    import Footer from './components/Footer/Footer.vue'

</script>

<template>
  <div id="App">
    <Header/>
    <MainSection/>
    <Services/>
    <Start/>
    <About/>
<Currency/>  
<Charts/>  
 <Download/>
  <Faq/>
  <Contact/>
  <Footer/>
  </div>
  
</template>

<style>
:root {
  --app-max-width: 1200px; 
  --app-padding-x: 20px; 
}
</style>
