<template>
  <section id="contact" class="contact">
    <div class="container">
      <div ref="contactContent" class="contact-content" :class="{ visible: isVisible }">
        <h2>Contact</h2>
        <p>N'hésitez pas à me contacter pour discuter de vos projets ou pour toute question.</p>
        
        <div class="contact-cards">
          <a href="mailto:arnaud.gay@edu.devinci.fr" class="contact-card" target="_blank" rel="noopener noreferrer">
            <div class="card-content">
              <div class="contact-icon" v-html="emailIcon"></div>
              <h3>Email</h3>
            </div>
          </a>

          <a href="https://www.linkedin.com/in/arnaud-gay/" class="contact-card" target="_blank" rel="noopener noreferrer">
            <div class="card-content">
              <div class="contact-icon" v-html="linkedinIcon"></div>
              <h3>LinkedIn</h3>
            </div>
          </a>

          <a href="https://github.com/arnaudgay" class="contact-card" target="_blank" rel="noopener noreferrer">
            <div class="card-content">
              <div class="contact-icon" v-html="githubIcon"></div>
              <h3>GitHub</h3>
            </div>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useIntersectionObserver } from '@vueuse/core'
import emailIcon from '@/assets/icons/email.svg?raw'
import linkedinIcon from '@/assets/icons/linkedin.svg?raw'
import githubIcon from '@/assets/icons/github.svg?raw'

const isVisible = ref(false)
const contactContent = ref(null)

onMounted(() => {
  useIntersectionObserver(
    contactContent,
    ([{ isIntersecting }]) => {
      if (isIntersecting) {
        isVisible.value = true
      }
    },
    { threshold: 0.1 }
  )
})
</script>

<style lang="scss" scoped>
.contact {
  padding: var(--spacing-xl) 0;
  background-color: var(--color-background);
  position: relative;
  z-index: 1;

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 var(--spacing-lg);
  }

  .contact-content {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.6s ease, transform 0.6s ease;

    &.visible {
      opacity: 1;
      transform: translateY(0);
    }

    h2 {
      text-align: center;
      margin-bottom: var(--spacing-md);
      color: var(--color-primary);
    }

    p {
      text-align: center;
      margin-bottom: var(--spacing-xl);
      color: var(--color-text-secondary);
    }
  }

  .contact-cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: var(--spacing-lg);
    margin-top: var(--spacing-xl);
  }

  .contact-card {
    text-decoration: none;
    background-color: var(--color-background-alt);
    border-radius: 12px;
    padding: var(--spacing-lg);
    transition: var(--transition-fast);
    border: 1px solid var(--color-border);
    cursor: pointer;

    &:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow-md);
      border-color: var(--color-primary);

      .contact-icon {
        transform: scale(1.1);
        filter: brightness(1.2);
      }
    }

    .card-content {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      gap: var(--spacing-md);
    }

    .contact-icon {
      width: 48px;
      height: 48px;
      transition: transform 0.3s ease, filter 0.3s ease;
      color: var(--color-primary);
      fill: currentColor;
      display: flex;
      align-items: center;
      justify-content: center;

      :deep(svg) {
        width: 100%;
        height: 100%;
      }
    }

    h3 {
      color: var(--color-primary);
      margin: 0;
    }

    p {
      color: var(--color-text);
      margin: 0;
    }
  }
}

@media (max-width: 768px) {
  .contact {
    padding: var(--spacing-lg) 0;

    .container {
      padding: 0 var(--spacing-md);
    }

    .contact-cards {
      grid-template-columns: 1fr;
    }
  }
}
</style> 