<template>
  <div class="cv-viewer" v-if="isOpen">
    <div class="cv-container">
      <button class="close-button" @click="closeCV">
        <span class="close-icon">×</span>
      </button>
      <iframe :src="cvUrl" class="cv-frame"></iframe>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  isOpen: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['close'])

const cvUrl = '/assets/cv_arnaud.pdf'

const closeCV = () => {
  emit('close')
}
</script>

<style lang="scss" scoped>
.cv-viewer {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.9);
  z-index: 2000;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: var(--spacing-xl);
}

.cv-container {
  position: relative;
  width: 100%;
  max-width: 1200px;
  height: 90vh;
  background-color: var(--color-background);
  border-radius: 12px;
  box-shadow: var(--shadow-lg);
}

.close-button {
  position: absolute;
  top: var(--spacing-sm);
  right: var(--spacing-sm);
  background: none;
  border: none;
  color: var(--color-text);
  font-size: 2rem;
  cursor: pointer;
  padding: var(--spacing-xs);
  z-index: 1;
  transition: var(--transition-fast);

  &:hover {
    color: var(--color-primary-light);
    transform: scale(1.1);
  }
}

.cv-frame {
  width: 100%;
  height: 100%;
  border: none;
  border-radius: 12px;
}

@media (max-width: 768px) {
  .cv-viewer {
    padding: var(--spacing-md);
  }
}
</style> 