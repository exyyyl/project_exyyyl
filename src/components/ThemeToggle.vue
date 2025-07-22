<template>
  <button 
    @click="toggleTheme" 
    class="theme-toggle"
    :title="isDark ? 'Переключить на светлую тему' : 'Переключить на тёмную тему'"
  >
    <Sun v-if="isDark" :size="18" />
    <Moon v-else :size="18" />
  </button>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { Sun, Moon } from 'lucide-vue-next';

const isDark = ref(true);

const toggleTheme = () => {
  isDark.value = !isDark.value;
  const root = document.documentElement;
  
  if (isDark.value) {
    root.classList.remove('light-theme');
    localStorage.setItem('theme', 'dark');
  } else {
    root.classList.add('light-theme');
    localStorage.setItem('theme', 'light');
  }
};

onMounted(() => {
  const savedTheme = localStorage.getItem('theme');
  const root = document.documentElement;
  
  if (savedTheme === 'light') {
    isDark.value = false;
    root.classList.add('light-theme');
  } else {
    isDark.value = true;
    root.classList.remove('light-theme');
  }
});
</script>

<style scoped>
.theme-toggle {
  background: none;
  border: 2px solid var(--accent-color);
  border-radius: 8px;
  padding: 8px 12px;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 44px;
  min-height: 44px;
}

.theme-toggle:hover {
  background-color: var(--accent-color);
  transform: scale(1.05);
}

.theme-toggle:active {
  transform: scale(0.95);
}

.theme-toggle svg {
  color: var(--accent-color);
  transition: color 0.3s ease;
}

.theme-toggle:hover svg {
  color: var(--bg-color);
}

@media (max-width: 480px) {
  .theme-toggle {
    padding: 6px 10px;
    min-width: 40px;
    min-height: 40px;
  }
}
</style>