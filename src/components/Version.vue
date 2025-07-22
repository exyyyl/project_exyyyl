<template>
  <div class="version" @click="toggleUpdates">
    <span> v{{ version }}</span>
  </div>
</template>

<script setup lang="ts">
import { defineEmits } from 'vue';

const version = '1.02';
const emit = defineEmits(['toggleUpdates']);

const toggleUpdates = () => {
  emit('toggleUpdates');
};
</script>

<style scoped>
.version {
  font-size: 12px;
  background-color: var(--accent-color);
  color: var(--bg-color);
  padding: 5px 10px;
  border-radius: 5px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.version:hover {
  opacity: 0.8;
}

/* Мобильная адаптация */
@media (max-width: 480px) {
  .version {
    font-size: 10px;
    padding: 4px 8px;
    border-radius: 4px;
  }
}

</style>
