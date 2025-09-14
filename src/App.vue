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
  <div class="bg-[#acdcf9] dark:bg-[#1f1848] min-h-screen">
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

<style >
  
</style>