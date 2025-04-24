<template>
  <nav class="navbar">
    <div class="container">
      <div class="navbar-content">
        <div class="navbar-logo">
          <img :src="logo" alt="Logo Arnaud Gay" class="logo">
        </div>

        <button class="burger-menu" @click="toggleMenu" :class="{ 'active': isMenuOpen }">
          <span></span>
          <span></span>
          <span></span>
        </button>

        <div class="navbar-links" :class="{ 'active': isMenuOpen }">
          <a href="#" class="nav-link" @click="closeMenu">Accueil</a>
          <a href="#about" class="nav-link" @click="closeMenu">À propos</a>
          <a href="#skills" class="nav-link" @click="closeMenu">Compétences</a>
          <a href="#project" class="nav-link" @click="closeMenu">Projets</a>
          <a href="#contact" class="nav-link" @click="closeMenu">Contact</a>
          <a :href="cvUrl" target="_blank" class="cv-button" @click="closeMenu">
            Voir mon CV
            <span class="button-arrow">→</span>
          </a>
        </div>
      </div>
    </div>
  </nav>

  <CVViewer :is-open="isCVOpen" @close="closeCV" />
</template>

<script setup>
import { ref } from 'vue'
import CVViewer from './CVViewer.vue'
import logo from '@/assets/logo/logo_ag.png'
import cvUrl from '@/assets/cv_arnaud.pdf'

const isCVOpen = ref(false)
const isMenuOpen = ref(false)

const openCV = () => {
  isCVOpen.value = true
  isMenuOpen.value = false
}

const closeCV = () => {
  isCVOpen.value = false
}

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
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

  .burger-menu {
    display: none;
    flex-direction: column;
    justify-content: space-between;
    width: 30px;
    height: 21px;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
    z-index: 10;

    span {
      width: 100%;
      height: 3px;
      background-color: var(--color-text);
      border-radius: 3px;
      transition: all 0.3s ease;
    }

    &.active {
      span:nth-child(1) {
        transform: translateY(9px) rotate(45deg);
      }
      span:nth-child(2) {
        opacity: 0;
      }
      span:nth-child(3) {
        transform: translateY(-9px) rotate(-45deg);
      }
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

    .burger-menu {
      display: flex;
    }

    .navbar-links {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      height: 100vh;
      background-color: var(--color-background);
      flex-direction: column;
      padding: calc(var(--navbar-height) + var(--spacing-lg)) var(--spacing-lg);
      gap: var(--spacing-lg);
      transform: translateY(-100%);
      opacity: 0;
      transition: all 0.3s ease;
      pointer-events: none;
      z-index: 999;

      &.active {
        transform: translateY(0);
        opacity: 1;
        pointer-events: auto;
      }

      .nav-link {
        font-size: 1.2rem;
        padding: var(--spacing-sm) 0;
      }

      .cv-button {
        margin-top: var(--spacing-lg);
        padding: var(--spacing-sm) var(--spacing-lg);
        font-size: 1.1rem;
      }
    }
  }
}
</style> 