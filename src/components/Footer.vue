<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-logo">
          <img src="/src/assets/logo/logo_ag.png" alt="Logo Arnaud Gay" class="logo">
        </div>
        
        <p>Merci de votre visite !</p>
        
        <div class="footer-links">
          <a href="#hero">Accueil</a>
          <a href="#about">À propos</a>
          <a href="#skills">Compétences</a>
          <a href="#experience">Expériences</a>
          <a href="#project">Projet</a>
          <a href="#contact">Contact</a>
        </div>

        <a href="assets/cv_arnaud.pdf" target="_blank" class="cv-button">
          Voir mon CV
          <span class="button-arrow">→</span>
        </a>

        <div class="footer-copyright">
          © {{ new Date().getFullYear() }} Arnaud Gay. Tous droits réservés.
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
// No additional logic needed
</script>

<style lang="scss" scoped>
.footer {
  background-color: var(--color-background-alt);
  color: var(--color-text);
  padding: var(--spacing-xl) 0;
  text-align: center;

  .footer-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-lg);
  }

  .footer-logo {
    margin-bottom: var(--spacing-md);

    .logo {
      height: 60px;
      width: auto;
    }
  }

  .footer-links {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: var(--spacing-md);
    margin: var(--spacing-md) 0;

    a {
      color: var(--color-text);
      text-decoration: none;
      transition: color 0.3s ease;

      &:hover {
        color: var(--color-primary);
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
    font-size: 0.9rem;
    color: var(--color-text-light);
  }
}

@media (max-width: 768px) {
  .footer {
    .footer-links {
      flex-direction: column;
      gap: var(--spacing-sm);
    }
  }
}
</style> 