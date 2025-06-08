<script setup lang="ts">
import { defineProps } from 'vue';
import ParticleAnimation from './ParticleAnimation.vue';

interface Props {
  isEmpty?: boolean;
}

const props = withDefaults(defineProps<Props>(), {
  isEmpty: false
});
</script>

<template>
  <div class="layout-container">
    <div class="layout-content">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.layout-container {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  flex: 1;
  border: 1px solid #fff;
  border-radius: 10px;
  padding: 40px;
  color: #fff;
  box-sizing: border-box;
  overflow: hidden;
}

.layout-content {
  position: relative;
  z-index: 2;
  text-align: center;
}

/* Стили для пустого состояния */
.layout-container:has(.wave-container) .layout-content {
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.7;
  }
}
</style>