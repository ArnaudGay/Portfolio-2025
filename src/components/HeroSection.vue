<template>
  <section class="hero">
    <div class="container">
      <div ref="heroContent" class="hero-content fade-in" :class="{ visible: isVisible }">
        <h1>Bonjour, je suis Arnaud.<br>Chef de projet digital et futur Software Engineer.</h1>
        <p class="subtitle">
          Passionné par la technologie et la transformation digitale, je mets mes compétences en gestion de projet, marketing et développement au service de projets innovants et créatifs.
        </p><br>
        <button class="cta-button" @click="scrollToAbout">
          Découvrir mon parcours
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useIntersectionObserver } from '@vueuse/core';

const isVisible = ref(false);
const heroContent = ref(null);

onMounted(() => {
  useIntersectionObserver(
    heroContent,
    ([{ isIntersecting }]) => {
      if (isIntersecting) {
        isVisible.value = true;
      }
    },
    { threshold: 0.1 }
  );
});

const scrollToAbout = () => {
  const aboutSection = document.getElementById('about');
  if (aboutSection) {
    aboutSection.scrollIntoView({ behavior: 'smooth' });
  }
};
</script>

<style lang="scss" scoped>
.hero {
  background-color: var(--color-background);
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;

  .container {
    position: relative;
    z-index: 1;
    width: 100%;
  }

  .hero-content {
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
  }

  h1 {
    color: var(--color-primary-light);
    margin-bottom: var(--spacing-lg);
    line-height: 1.2;
    font-size: clamp(2rem, 5vw, 3.5rem);
  }

  .subtitle {
    font-size: 1.25rem;
    color: var(--color-text);
    margin-bottom: var(--spacing-xl);
    line-height: 1.6;
  }

  .cta-button {
    background-color: var(--color-primary);
    color: var(--color-background);
    border: none;
    padding: var(--spacing-sm) var(--spacing-lg);
    font-size: 1.1rem;
    border-radius: 50px;
    cursor: pointer;
    transition: var(--transition-fast);
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;

    &:hover {
      transform: translateY(-2px);
      box-shadow: var(--shadow-md);
    }
  }
}

@media (max-width: 768px) {
  .hero {
    h1 {
      font-size: 2rem;
    }

    .subtitle {
      font-size: 1rem;
    }

    .cta-button {
      padding: var(--spacing-xs) var(--spacing-md);
      font-size: 1rem;
    }
  }
}
</style> 