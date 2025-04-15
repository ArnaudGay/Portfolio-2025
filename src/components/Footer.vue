<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <p class="footer-text">Merci de ta visite !</p>
        <div class="footer-links">
          <a href="#hero" class="footer-link">Accueil</a>
          <a href="#about" class="footer-link">À propos</a>
          <a href="#skills" class="footer-link">Compétences</a>
          <a href="#experience" class="footer-link">Expériences</a>
          <a href="#project" class="footer-link">Projet</a>
          <a href="#contact" class="footer-link">Contact</a>
        </div>
        <p class="footer-copyright">
          © {{ new Date().getFullYear() }} Arnaud Gay. Tous droits réservés.
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
// No additional logic needed for now
</script>

<style lang="scss" scoped>
.footer {
  background-color: var(--color-primary);
  color: var(--color-secondary);
  padding: var(--spacing-xl) 0;
  text-align: center;

  .footer-content {
    max-width: 800px;
    margin: 0 auto;
  }

  .footer-text {
    font-size: 1.2rem;
    margin-bottom: var(--spacing-lg);
  }

  .footer-links {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: var(--spacing-md);
    margin-bottom: var(--spacing-lg);

    .footer-link {
      color: var(--color-secondary);
      text-decoration: none;
      transition: var(--transition-fast);

      &:hover {
        color: var(--color-accent);
      }
    }
  }

  .footer-copyright {
    font-size: 0.9rem;
    opacity: 0.8;
  }
}

@media (max-width: 768px) {
  .footer {
    padding: var(--spacing-lg) 0;

    .footer-links {
      flex-direction: column;
      gap: var(--spacing-sm);
    }
  }
}
</style> 