<template>
  <div id="app">
    <Header @open-register="showRegister = true" />

    <!-- Your main sections -->
    <Hero />
    <Services />
    <HowItWorks />
    <Pricing />
    <FAQ />
    <Footer />

    <!-- Register Modal -->
    <Register v-if="showRegister" @close="showRegister = false" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Services from './components/Services.vue'
import HowItWorks from './components/HowItWorks.vue'
import Pricing from './components/Pricing.vue'
import FAQ from './components/FAQ.vue'
import Footer from './components/Footer.vue'
import Register from './pages/Register.vue'

const showRegister = ref(false)
</script>
