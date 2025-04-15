<template>
  <section id="skills" class="skills">
    <div class="container">
      <div ref="skillsContent" class="skills-content fade-in" :class="{ visible: isVisible }">
        <h2>Compétences</h2>
        <div class="skills-grid">
          <div class="skill-category">
            <h3>Gestion de projet</h3>
            <ul class="skill-list">
              <li>Scrum (sprints, daily stand-up)</li>
              <li>Méthodologie agile</li>
              <li>Gestion d'équipe</li>
              <li>Planification stratégique</li>
            </ul>
          </div>
          
          <div class="skill-category">
            <h3>Marketing & Communication</h3>
            <ul class="skill-list">
              <li>Campagnes digitales</li>
              <li>Stratégies digitales</li>
              <li>Analyse d'audience</li>
              <li>Content marketing</li>
            </ul>
          </div>
          
          <div class="skill-category">
            <h3>Développement</h3>
            <ul class="skill-list">
              <li>Python</li>
              <li>C</li>
              <li>HTML/CSS/JS</li>
              <li>Node.js</li>
              <li>Flutter</li>
              <li>Three.js</li>
            </ul>
          </div>
          
          <div class="skill-category">
            <h3>UX/UI</h3>
            <ul class="skill-list">
              <li>Maquettes Figma</li>
              <li>Interviews utilisateurs</li>
              <li>Tests et itérations</li>
              <li>Design thinking</li>
            </ul>
          </div>
          
          <div class="skill-category">
            <h3>Data & Analytics</h3>
            <ul class="skill-list">
              <li>Suivi des KPIs</li>
              <li>Tableaux de bord</li>
              <li>Optimisation</li>
              <li>Analyse de données</li>
            </ul>
          </div>
          
          <div class="skill-category">
            <h3>IA Générative</h3>
            <ul class="skill-list">
              <li>Exploration d'outils</li>
              <li>Automatisation de tâches</li>
              <li>Prompt engineering</li>
              <li>Intégration API</li>
            </ul>
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
const skillsContent = ref(null);

onMounted(() => {
  useIntersectionObserver(
    skillsContent,
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
.skills {
  background-color: var(--color-background-alt);
  color: var(--color-text);

  .skills-content {
    max-width: 1200px;
    margin: 0 auto;
  }

  h2 {
    color: var(--color-primary-light);
    text-align: center;
    margin-bottom: var(--spacing-xl);
  }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: var(--spacing-lg);
  }

  .skill-category {
    background-color: var(--color-background);
    padding: var(--spacing-lg);
    border-radius: 12px;
    box-shadow: var(--shadow-md);
    transition: var(--transition-normal);
    border: 1px solid var(--color-border);

    &:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow-lg);
      border-color: var(--color-primary);
    }

    h3 {
      color: var(--color-primary);
      margin-bottom: var(--spacing-md);
      font-size: 1.3rem;
      text-align: center;
      padding-bottom: var(--spacing-sm);
      border-bottom: 2px solid var(--color-primary);
    }

    .skill-list {
      list-style: none;
      
      li {
        margin-bottom: var(--spacing-xs);
        padding-left: var(--spacing-sm);
        position: relative;
        transition: var(--transition-fast);

        &:hover {
          color: var(--color-primary-light);
          transform: translateX(5px);
        }

        &::before {
          content: '•';
          color: var(--color-accent);
          position: absolute;
          left: 0;
        }
      }
    }
  }
}

@media (max-width: 768px) {
  .skills {
    .skills-grid {
      grid-template-columns: 1fr;
    }

    .skill-category {
      padding: var(--spacing-md);
    }
  }
}
</style> 