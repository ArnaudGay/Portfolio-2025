<template>
  <section id="contact" class="contact">
    <div class="container">
      <div ref="contactContent" class="contact-content fade-in" :class="{ visible: isVisible }">
        <h2>Contact</h2>
        <div class="contact-grid">
          <div class="contact-info">
            <h3>Coordonnées</h3>
            <ul class="contact-links">
              <li>
                <a href="mailto:arnogay@gmail.com" class="contact-link">
                  <span class="link-icon">✉️</span>
                  arnogay@gmail.com
                </a>
              </li>
              <li>
                <a href="https://linkedin.com/in/arnaud-gay-159634193/" target="_blank" class="contact-link">
                  <span class="link-icon">🔗</span>
                  LinkedIn
                </a>
              </li>
              <li>
                <a href="https://github.com/ArnaudGay" target="_blank" class="contact-link">
                  <span class="link-icon">💻</span>
                  GitHub
                </a>
              </li>
            </ul>
          </div>

          <div class="contact-form">
            <h3>Discutons-en !</h3>
            <form @submit.prevent="handleSubmit" class="form">
              <div class="form-group">
                <label for="name">Nom</label>
                <input
                  type="text"
                  id="name"
                  v-model="form.name"
                  required
                  placeholder="Votre nom"
                >
              </div>

              <div class="form-group">
                <label for="email">Email</label>
                <input
                  type="email"
                  id="email"
                  v-model="form.email"
                  required
                  placeholder="Votre email"
                >
              </div>

              <div class="form-group">
                <label for="message">Message</label>
                <textarea
                  id="message"
                  v-model="form.message"
                  required
                  placeholder="Votre message"
                  rows="5"
                ></textarea>
              </div>

              <button type="submit" class="submit-button" :disabled="isSubmitting">
                {{ isSubmitting ? 'Envoi en cours...' : 'Envoyer' }}
              </button>
            </form>
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
const contactContent = ref(null);
const isSubmitting = ref(false);

const form = ref({
  name: '',
  email: '',
  message: ''
});

onMounted(() => {
  useIntersectionObserver(
    contactContent,
    ([{ isIntersecting }]) => {
      if (isIntersecting) {
        isVisible.value = true;
      }
    },
    { threshold: 0.1 }
  );
});

const handleSubmit = async () => {
  isSubmitting.value = true;
  // TODO: Implement form submission logic
  await new Promise(resolve => setTimeout(resolve, 1000)); // Simulate API call
  isSubmitting.value = false;
  form.value = { name: '', email: '', message: '' };
};
</script>

<style lang="scss" scoped>
.contact {
  background-color: var(--color-secondary);
  color: var(--color-text);

  .contact-content {
    max-width: 1000px;
    margin: 0 auto;
  }

  h2 {
    color: var(--color-primary-light);
    text-align: center;
    margin-bottom: var(--spacing-xl);
  }

  .contact-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: var(--spacing-xl);
  }

  .contact-info {
    h3 {
      color: var(--color-primary);
      margin-bottom: var(--spacing-lg);
    }

    .contact-links {
      list-style: none;
      
      li {
        margin-bottom: var(--spacing-md);
      }

      .contact-link {
        color: var(--color-text);
        text-decoration: none;
        display: flex;
        align-items: center;
        gap: var(--spacing-sm);
        transition: var(--transition-fast);

        &:hover {
          color: var(--color-accent);
        }

        .link-icon {
          font-size: 1.2rem;
        }
      }
    }
  }

  .contact-form {
    h3 {
      color: var(--color-primary);
      margin-bottom: var(--spacing-lg);
    }

    .form {
      display: flex;
      flex-direction: column;
      gap: var(--spacing-md);
    }

    .form-group {
      display: flex;
      flex-direction: column;
      gap: var(--spacing-xs);

      label {
        font-weight: 500;
        color: var(--color-primary);
      }

      input,
      textarea {
        padding: var(--spacing-sm);
        border: 1px solid var(--color-background);
        border-radius: 8px;
        background-color: var(--color-background);
        transition: var(--transition-fast);

        &:focus {
          outline: none;
          border-color: var(--color-accent);
          box-shadow: 0 0 0 2px rgba(255, 51, 102, 0.1);
        }
      }
    }

    .submit-button {
      background-color: var(--color-accent);
      color: var(--color-secondary);
      border: none;
      padding: var(--spacing-sm) var(--spacing-lg);
      border-radius: 50px;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition-fast);
      margin-top: var(--spacing-md);

      &:hover:not(:disabled) {
        transform: translateY(-2px);
        box-shadow: 0 4px 12px rgba(255, 51, 102, 0.3);
      }

      &:disabled {
        opacity: 0.7;
        cursor: not-allowed;
      }
    }
  }
}

@media (max-width: 768px) {
  .contact {
    .contact-grid {
      grid-template-columns: 1fr;
    }
  }
}
</style> 