<script setup>
import {defineAsyncComponent} from 'vue';
const Navbar = defineAsyncComponent(() => import('./components/layout/Navbar.vue'));
const HeroSection = defineAsyncComponent(() => import('./components/layout/HeroSection.vue'));
const Counter = defineAsyncComponent(() => import('./components/layout/Counter.vue'));
const Services = defineAsyncComponent(() => import('./components/layout/Services.vue'));
const Skills = defineAsyncComponent(() => import('./components/layout/Skills.vue'));
const WhyMe = defineAsyncComponent(() => import('./components/layout/WhyMe.vue'));
const Project = defineAsyncComponent(() => import('./components/layout/Project.vue'));
const Contact = defineAsyncComponent(() => import('./components/layout/Contact.vue'));
const Footer = defineAsyncComponent(() => import('./components/layout/Footer.vue'));

</script>

<template>
  <div class="bg-[#acdcf9] dark:bg-[#1f1848] min-h-screen overflow-x-hidden">
    <Navbar />
    <HeroSection />
    <Counter />
    <Services />
    <Skills />
    <WhyMe />
    <Project />
    <Contact />
    <Footer />
  </div>
</template>

<style>
/* Global overflow control */
html, body {
  overflow-x: hidden !important;
  width: 100% !important;
  max-width: 100% !important;
}

* {
  box-sizing: border-box !important;
}

/* Mobile performance optimizations */
@media (max-width: 768px) {
  /* Reduce animations on mobile */
  .animate-pulse {
    animation-duration: 3s !important;
  }
  
  .animate-ping {
    animation-duration: 2s !important;
  }
  
  /* Optimize transforms */
  .group:hover .group-hover\\:scale-110 {
    transform: scale(1.05) !important;
  }
  
  .group:hover .group-hover\\:scale-105 {
    transform: scale(1.02) !important;
  }
}
</style>