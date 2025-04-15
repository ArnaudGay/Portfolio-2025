<template>
  <nav class="navbar">
    <div class="container">
      <div class="navbar-content">
        <div class="navbar-logo">
          <img :src="logo" alt="Logo Arnaud Gay" class="logo">
        </div>

        <div class="navbar-links">
          <a href="#" class="nav-link">Accueil</a>
          <a href="#about" class="nav-link">À propos</a>
          <a href="#skills" class="nav-link">Compétences</a>
          <a href="#project" class="nav-link">Projets</a>
          <a href="#contact" class="nav-link">Contact</a>
        </div>

        <button @click="openCV" class="cv-button">
          Voir mon CV
          <span class="button-arrow">→</span>
        </button>
      </div>
    </div>
  </nav>

  <CVViewer :is-open="isCVOpen" @close="closeCV" />
</template>

<script setup>
import { ref } from 'vue'
import CVViewer from './CVViewer.vue'
import logo from '@/assets/logo/logo_ag.png'

const isCVOpen = ref(false)

const openCV = () => {
  isCVOpen.value = true
}

const closeCV = () => {
  isCVOpen.value = false
}
</script>

<style lang="scss" scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background-color: var(--color-background);
  border-bottom: 1px solid var(--color-border);
  z-index: 1000;
  padding: var(--spacing-md) 0;
  backdrop-filter: blur(10px);
  background-color: rgba(var(--color-background-rgb), 0.8);
  height: var(--navbar-height);

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 var(--spacing-lg);
    height: 100%;
  }

  .navbar-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 100%;
  }

  .navbar-logo {
    .logo {
      height: 40px;
      width: auto;
    }
  }

  .navbar-links {
    display: flex;
    gap: var(--spacing-lg);
    align-items: center;

    .nav-link {
      color: var(--color-text);
      text-decoration: none;
      font-weight: 500;
      transition: var(--transition-fast);
      position: relative;
      padding: var(--spacing-xs) 0;

      &:hover {
        color: var(--color-primary-light);

        &::after {
          width: 100%;
        }
      }

      &::after {
        content: '';
        position: absolute;
        bottom: 0;
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
    padding: var(--spacing-xs) var(--spacing-md);
    background-color: var(--color-primary);
    color: white;
    text-decoration: none;
    border-radius: 6px;
    transition: all 0.3s ease;
    font-weight: 500;
    border: none;
    cursor: pointer;

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
}

@media (max-width: 768px) {
  .navbar {
    padding: var(--spacing-sm) 0;

    .container {
      padding: 0 var(--spacing-md);
    }

    .navbar-content {
      flex-direction: column;
      gap: var(--spacing-md);
    }

    .navbar-links {
      flex-direction: column;
      gap: var(--spacing-md);
    }

    .cv-button {
      margin-top: var(--spacing-sm);
    }
  }
}
</style> 