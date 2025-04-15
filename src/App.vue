<script setup>
import Navbar from './components/Navbar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectSection from './components/ProjectSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="app">
    <Navbar />
    <main>
      <HeroSection />
      <AboutSection />
      <SkillsSection />
      <ProjectSection />
      <ContactSection />
    </main>
    <Footer />
    <!-- Les autres sections seront ajoutées ici -->
  </div>
</template>

<style lang="scss">
@use './styles/main.scss';

.app {
  min-height: 100vh;
  background-color: var(--color-background);
  color: var(--color-text);
}
</style>
