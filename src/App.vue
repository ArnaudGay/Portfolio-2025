<script setup>
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ProjectSection from './components/ProjectSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import WhyMeSection from './components/WhyMeSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="app">
    <HeroSection />
    <AboutSection />
    <ProjectSection />
    <SkillsSection />
    <WhyMeSection />
    <ContactSection />
    <Footer />
    <!-- Les autres sections seront ajoutées ici -->
  </div>
</template>

<style>
@import './styles/main.scss';

.app {
  min-height: 100vh;
  overflow-x: hidden;
}
</style>
