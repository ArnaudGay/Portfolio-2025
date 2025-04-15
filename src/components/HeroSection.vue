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
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  padding: var(--spacing-xl) 0;
  background-color: var(--color-background);

  .container {
    position: relative;
    z-index: 2;
    max-width: 800px;
    text-align: center;
    padding: 0 var(--spacing-lg);
  }

  .hero-content {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.6s ease, transform 0.6s ease;

    &.visible {
      opacity: 1;
      transform: translateY(0);
    }

    h1 {
      font-size: clamp(2.5rem, 5vw, 4rem);
      font-weight: 700;
      margin-bottom: var(--spacing-md);
      line-height: 1.2;
      background: linear-gradient(135deg, var(--color-primary), var(--color-primary-light));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      max-width: 100%;
      word-wrap: break-word;
    }

    p {
      font-size: clamp(1.1rem, 2vw, 1.25rem);
      line-height: 1.6;
      margin-bottom: var(--spacing-lg);
      color: var(--color-text-secondary);
      max-width: 100%;
      word-wrap: break-word;
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
        background-color: var(--color-primary-dark);
      }
    }
  }

  .hero-buttons {
    display: flex;
    gap: var(--spacing-md);
    justify-content: center;
    flex-wrap: wrap;
    
  }

  .hero-background {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 1;
    opacity: 0.1;
    background: radial-gradient(circle at center, var(--color-primary) 0%, transparent 70%);
  }
}

@media (max-width: 768px) {
  .hero {
    padding: var(--spacing-lg) 0;

    .container {
      padding: 0 var(--spacing-md);
    }

    .hero-content {
      h1 {
        font-size: clamp(2rem, 4vw, 3rem);
      }

      p {
        font-size: clamp(1rem, 1.8vw, 1.1rem);
      }

      .cta-button {
        padding: var(--spacing-xs) var(--spacing-md);
        font-size: 1rem;
      }
    }

    .hero-buttons {
      flex-direction: column;
      align-items: center;
    }
  }
}
</style> 