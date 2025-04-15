<template>
  <section id="why-me" class="why-me">
    <div class="container">
      <div ref="whyMeContent" class="why-me-content fade-in" :class="{ visible: isVisible }">
        <h2>Pourquoi travailler avec moi ?</h2>
        <div class="why-me-grid">
          <div class="why-me-text">
            <p>
              Je crois en une approche à la fois humaine et data-driven de la gestion de projet. 
              Mes expériences variées que j'ai vécues m'ont appris à fédérer 
              des équipes, résoudre rapidement les problèmes et garder l'enthousiasme au centre 
              de la démarche.
            </p>
            <p>
              En tant que futur Software Engineer, je ne me contente pas de coordonner les équipes : 
              je mets aussi la main à la pâte pour mieux comprendre les défis techniques et livrer 
              des solutions solides.
            </p>
          </div>
          <div class="why-me-highlights">
            <div class="highlight-item">
              <span class="highlight-icon">🤝</span>
              <h3>Approche humaine</h3>
              <p>Fédération d'équipes et résolution de problèmes</p>
            </div>
            <div class="highlight-item">
              <span class="highlight-icon">📊</span>
              <h3>Data-driven</h3>
              <p>Décisions basées sur les données et l'analyse</p>
            </div>
            <div class="highlight-item">
              <span class="highlight-icon">💻</span>
              <h3>Technique</h3>
              <p>Compétences pratiques en développement</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useIntersectionObserver } from '@vueuse/core';

const isVisible = ref(false);
const whyMeContent = ref(null);

onMounted(() => {
  useIntersectionObserver(
    whyMeContent,
    ([{ isIntersecting }]) => {
      if (isIntersecting) {
        isVisible.value = true;
      }
    },
    { threshold: 0.1 }
  );
});
</script>

<style lang="scss" scoped>
.why-me {
  background-color: var(--color-background-alt);
  color: var(--color-text);

  .why-me-content {
    max-width: 1000px;
    margin: 0 auto;
  }

  h2 {
    color: var(--color-primary-light);
    text-align: center;
    margin-bottom: var(--spacing-xl);
  }

  .why-me-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--spacing-xl);
  }

  .why-me-text {
    p {
      font-size: 1.1rem;
      line-height: 1.8;
      margin-bottom: var(--spacing-lg);
      text-align: center;
    }
  }

  .why-me-highlights {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: var(--spacing-lg);
    margin-top: var(--spacing-xl);
  }

  .highlight-item {
    background-color: var(--color-background);
    padding: var(--spacing-lg);
    border-radius: 12px;
    text-align: center;
    transition: var(--transition-normal);
    border: 1px solid var(--color-border);

    &:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow-lg);
      border-color: var(--color-primary);
    }

    .highlight-icon {
      font-size: 2.5rem;
      margin-bottom: var(--spacing-md);
      display: block;
    }

    h3 {
      color: var(--color-primary);
      margin-bottom: var(--spacing-sm);
      font-size: 1.2rem;
    }

    p {
      color: var(--color-text);
      font-size: 1rem;
      line-height: 1.6;
    }
  }
}

@media (max-width: 768px) {
  .why-me {
    .why-me-text {
      p {
        font-size: 1rem;
      }
    }

    .why-me-highlights {
      grid-template-columns: 1fr;
    }

    .highlight-item {
      padding: var(--spacing-md);
    }
  }
}
</style> 