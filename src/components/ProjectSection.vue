<template>
  <section id="project" class="project">
    <div class="container">
      <div ref="projectContent" class="project-content fade-in" :class="{ visible: isVisible }">
        <h2>Projets</h2>
        
        <div class="project-card">
          <div class="project-header">
            <img :src="eyLogo" alt="Logo EY" class="project-logo">
            <h3>EY Fabernovel - Chef de projet application mobile</h3>
            <span class="project-date">Juin - Octobre 2024</span>
            <a href="https://fabernovel.com" target="_blank" class="project-link">
              fabernovel.com
              <span class="link-arrow">→</span>
            </a>
          </div>

          <div class="project-details">
            <div class="project-role">
              <h4>Rôle</h4>
              <p>Chef de projet en charge de la coordination entre les équipes UX/UI et développement</p>
            </div>

            <div class="project-objectives">
              <h4>Missions</h4>
              <ul>
                <li>Organisation et animation des cérémonies Scrum</li>
                <li>Coordination entre l'équipe UX/UI et les développeurs</li>
                <li>Suivi des évolutions de design et gestion des retours clients</li>
                <li>Communication des priorités aux tech leads</li>
              </ul>
            </div>
          </div>
        </div>

        <div class="project-card">
          <div class="project-header">
            <img :src="synergheticLogo" alt="Logo Synerg'hetic" class="project-logo">
            <h3>Synerg'hetic - DSI</h3>
            <span class="project-date">Mai 2024 - Mai 2025</span>
            <a href="https://synerghetic.fr" target="_blank" class="project-link">
              synerghetic.fr
              <span class="link-arrow">→</span>
            </a>
          </div>

          <div class="project-details">
            <div class="project-role">
              <h4>Rôle</h4>
              <p>Directeur des Systèmes d'Information en charge de l'infrastructure et de la sécurité</p>
            </div>

            <div class="project-objectives">
              <h4>Missions</h4>
              <ul>
                <li>Gestion de l'infrastructure et sécurité des données</li>
                <li>Conseil technique sur la faisabilité des projets</li>
                <li>Mise en place de la stack d'outils pour les intervenants</li>
              </ul>
            </div>
          </div>
          <div class="project-image">
            <img :src="mandatImage" alt="Image projet Synerg'hetic">
          </div>
        </div>

        <div class="project-card">
          <div class="project-header">
            <img :src="badierLogo" alt="Logo Laurent Badier" class="project-logo">
            <h3>Projet Hackathon – Marketing & Site pour un artiste</h3>
            <a href="https://laurentbadier.com" target="_blank" class="project-link">
              laurentbadier.com
              <span class="link-arrow">→</span>
            </a>
          </div>

          <div class="project-details">
            <div class="project-role">
              <h4>Rôle</h4>
              <p>Chef de projet, garant de la coordination entre designer, dev et client</p>
            </div>

            <div class="project-objectives">
              <h4>Objectifs</h4>
              <ul>
                <li>Moderniser l'image d'objets de déco inspirés du mobilier scolaire</li>
                <li>Attirer un public amateur de design</li>
                <li>Parcours utilisateur simple et ludique (one-page)</li>
              </ul>
            </div>

            <div class="project-results">
              <h4>Résultats</h4>
              <ul>
                <li>Site fonctionnel livré rapidement</li>
                <li>Visibilité accrue sur réseaux sociaux</li>
                <li>Ton ludique et décalé</li>
              </ul>
            </div>
          </div>
          <div class="project-image">
            <img :src="hackathonImage" alt="Image projet Hackathon">
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useIntersectionObserver } from '@vueuse/core';

// Import des images
import eyLogo from '@/assets/logo/ey-logo.jpg';
import synergheticLogo from '@/assets/logo/synerghetic-logo.svg';
import badierLogo from '@/assets/logo/logo-badier.jpg';
import mandatImage from '@/assets/images/mandat-2425.jpg';
import hackathonImage from '@/assets/images/hackaton.png';

const isVisible = ref(false);
const projectContent = ref(null);

onMounted(() => {
  useIntersectionObserver(
    projectContent,
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
.project {
  background-color: var(--color-background);
  color: var(--color-text);

  .project-content {
    max-width: 1000px;
    margin: 0 auto;
  }

  h2 {
    color: var(--color-primary-light);
    text-align: center;
    margin-bottom: var(--spacing-xl);
  }

  .project-card {
    background-color: var(--color-secondary);
    border-radius: 16px;
    padding: var(--spacing-xl);
    box-shadow: var(--shadow-lg);
    transition: var(--transition-normal);
    margin-bottom: var(--spacing-xl);
    border: 2px solid transparent;
    display: flex;
    flex-direction: column;

    &:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow-lg);
      border-color: var(--color-primary);
    }
  }

  .project-header {
    margin-bottom: var(--spacing-lg);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: var(--spacing-md);
    padding-bottom: var(--spacing-md);
    border-bottom: 1px solid var(--color-border);

    .project-logo {
      height: 40px;
      width: auto;
      margin-right: var(--spacing-md);
      flex-shrink: 0;
      object-fit: contain;
    }

    h3 {
      color: var(--color-primary);
      margin: 0;
      flex: 1;
      min-width: 300px;
      flex-grow: 1;
    }

    .project-date {
      color: var(--color-accent);
      font-weight: 500;
    }

    .project-link {
      color: var(--color-accent);
      text-decoration: none;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: var(--spacing-xs);
      transition: var(--transition-fast);

      &:hover {
        color: var(--color-primary-light);

        .link-arrow {
          transform: translateX(4px);
        }
      }

      .link-arrow {
        transition: var(--transition-fast);
      }
    }
  }

  .project-details {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: var(--spacing-lg);
    margin-top: var(--spacing-md);

    h4 {
      color: var(--color-primary-dark);
      margin-bottom: var(--spacing-sm);
      font-size: 1.1rem;
      position: relative;
      padding-left: var(--spacing-sm);

      &::before {
        content: '';
        position: absolute;
        left: 0;
        top: 50%;
        transform: translateY(-50%);
        width: 4px;
        height: 16px;
        background-color: var(--color-primary);
        border-radius: 2px;
      }
    }

    p {
      margin-bottom: var(--spacing-md);
      line-height: 1.6;
    }

    ul {
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

  .project-image {
    margin-top: var(--spacing-lg);
    width: 100%;
    max-height: 400px;
    overflow: hidden;
    border-radius: 12px;
    border: 1px solid var(--color-border);

    img {
      display: block;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
}

@media (max-width: 768px) {
  .project {
    .project-card {
      padding: var(--spacing-lg);
    }

    .project-header {
      flex-direction: column;
      align-items: flex-start;
    }

    .project-details {
      grid-template-columns: 1fr;
    }
  }
}
</style> 