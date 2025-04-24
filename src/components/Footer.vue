<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-logo">
          <img :src="logo" alt="Logo Arnaud Gay" class="logo">
        </div>
        
        <p>Merci de votre visite !</p>
        
        <div class="footer-links">
          <a href="#" class="footer-link">Accueil</a>
          <a href="#about" class="footer-link">À propos</a>
          <a href="#skills" class="footer-link">Compétences</a>
          <a href="#project" class="footer-link">Projets</a>
          <a href="#contact" class="footer-link">Contact</a>
        </div>

        <a :href="cvUrl" target="_blank" class="cv-button">
          Voir mon CV
          <span class="button-arrow">→</span>
        </a>

        <div class="footer-copyright">
          © {{ new Date().getFullYear() }} Arnaud Gay. Tous droits réservés.
        </div>
      </div>
    </div>
  </footer>

  <CVViewer :is-open="isCVOpen" @close="closeCV" />
</template>

<script setup>
import { ref } from 'vue'
import CVViewer from './CVViewer.vue'
import logo from '@/assets/logo/logo_ag.png'
import cvUrl from '@/assets/cv_arnaud.pdf'

const isCVOpen = ref(false)

const openCV = () => {
  isCVOpen.value = true
}

const closeCV = () => {
  isCVOpen.value = false
}
</script>

<style lang="scss" scoped>
.footer {
  background-color: var(--color-background);
  color: var(--color-text);
  padding: var(--spacing-xl) 0;
  margin-top: var(--spacing-xl);
  border-top: 1px solid var(--color-border);
  position: relative;
  z-index: 2;

  .container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 0 var(--spacing-lg);
  }

  .footer-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-lg);
    text-align: center;
  }

  .footer-logo {
    margin-bottom: var(--spacing-md);
    text-align: center;

    .logo {
      height: 60px;
      width: auto;
      margin: 0 auto;
    }
  }

  p {
    margin: 0;
    font-size: 1.1rem;
    color: var(--color-text);
  }

  .footer-links {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: var(--spacing-lg);
    margin-bottom: var(--spacing-md);

    .footer-link {
      color: var(--color-text);
      text-decoration: none;
      font-weight: 500;
      transition: var(--transition-fast);
      position: relative;

      &:hover {
        color: var(--color-primary-light);

        &::after {
          width: 100%;
        }
      }

      &::after {
        content: '';
        position: absolute;
        bottom: -2px;
        left: 0;
        width: 0;
        height: 2px;
        background-color: var(--color-primary-light);
        transition: var(--transition-fast);
      }
    }
  }

  .cv-button {
    display: inline-flex;
    align-items: center;
    padding: var(--spacing-sm) var(--spacing-md);
    background-color: var(--color-primary);
    color: white;
    text-decoration: none;
    border-radius: 6px;
    transition: all 0.3s ease;
    margin: var(--spacing-md) 0;
    text-align: center;
    border: none;
    cursor: pointer;
    font-weight: 500;

    &:hover {
      background-color: var(--color-primary-dark);
      transform: translateY(-2px);

      .button-arrow {
        transform: translateX(4px);
      }
    }

    .button-arrow {
      margin-left: var(--spacing-xs);
      transition: transform 0.3s ease;
    }
  }

  .footer-copyright {
    color: var(--color-text-secondary);
    font-size: 0.9rem;
    text-align: center;
  }
}

@media (max-width: 768px) {
  .footer {
    padding: var(--spacing-lg) 0;

    .container {
      padding: 0 var(--spacing-md);
    }

    .footer-links {
      flex-direction: column;
      align-items: center;
      gap: var(--spacing-md);
    }
  }
}
</style> 