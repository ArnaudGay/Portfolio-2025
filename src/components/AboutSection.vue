<template>
  <section id="about" class="about">
    <div class="container">
      <div ref="aboutContent" class="about-content fade-in" :class="{ visible: isVisible }">
        <h2>À propos de moi</h2>
        <div class="about-grid">
          <div class="about-image">
            <div class="image-container">
              <!-- Remplacez src par le chemin de votre photo -->
              <img src="/profile.jpg" alt="Arnaud Gay" class="profile-image">
            </div>
          </div>
          <div class="about-text">
            <p>
              Actuellement étudiant en Programme Grande École à HETIC, je suis en formation 
              pour devenir un expert du digital. Mon parcours m'a amené à gérer des projets 
              en méthodologie agile, à coordonner des équipes internationales et à développer 
              des compétences en UX/UI, marketing et développement web.
            </p>
            <p>
              En parallèle, je suis curieux de tout : IA générative, design, data, sport, voyages.
              Cette ouverture d'esprit me permet de créer des solutions digitales qui font la différence.
            </p>
          </div>
        </div>
        <div class="qualities">
          <h3>Mes qualités</h3>
          <ul class="qualities-list">
            <li>Gestion du stress</li>
            <li>Communication efficace</li>
            <li>Esprit d'équipe</li>
            <li>Adaptabilité</li>
            <li>Curiosité intellectuelle</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useIntersectionObserver } from '@vueuse/core';

const isVisible = ref(false);
const aboutContent = ref(null);

onMounted(() => {
  useIntersectionObserver(
    aboutContent,
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
.about {
  background-color: var(--color-secondary);
  color: var(--color-text);

  .about-content {
    max-width: 1200px;
    margin: 0 auto;
  }

  h2 {
    color: var(--color-primary-light);
    text-align: center;
    margin-bottom: var(--spacing-xl);
  }

  .about-grid {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: var(--spacing-xl);
    margin-bottom: var(--spacing-xl);
  }

  .about-image {
    display: flex;
    align-items: center;
    justify-content: center;

    .image-container {
      width: 300px;
      height: 300px;
      border-radius: 50%;
      overflow: hidden;
      border: 4px solid var(--color-primary);
      box-shadow: var(--shadow-lg);
      transition: var(--transition-normal);

      &:hover {
        transform: scale(1.02);
        border-color: var(--color-primary-light);
      }

      .profile-image {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }
  }

  .about-text {
    p {
      margin-bottom: var(--spacing-md);
      font-size: 1.1rem;
      line-height: 1.8;
    }
  }

  .qualities {
    h3 {
      color: var(--color-primary-light);
      margin-bottom: var(--spacing-md);
      text-align: center;
    }

    .qualities-list {
      list-style: none;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: var(--spacing-md);

      li {
        background-color: var(--color-background);
        padding: var(--spacing-md);
        border-radius: 8px;
        text-align: center;
        font-weight: 500;
        transition: var(--transition-fast);
        display: flex;
        align-items: center;
        justify-content: center;
        min-height: 60px;

        &:hover {
          transform: translateY(-2px);
          box-shadow: var(--shadow-md);
        }
      }
    }
  }
}

@media (max-width: 768px) {
  .about {
    .about-grid {
      grid-template-columns: 1fr;
      gap: var(--spacing-lg);
    }

    .about-image {
      order: -1;
      
      .image-container {
        width: 250px;
        height: 250px;
      }
    }

    .about-text {
      p {
        font-size: 1rem;
      }
    }

    .qualities-list {
      grid-template-columns: 1fr;
    }
  }
}
</style> 