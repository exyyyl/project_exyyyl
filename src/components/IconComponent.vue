<template>
  <component 
    :is="iconComponent" 
    :size="size" 
    :color="color"
    :class="{ 'icon-active': isActive }"
  />
</template>

<script setup lang="ts">
import { computed } from 'vue';
import { FolderOpen, FlaskConical, Gamepad2 } from 'lucide-vue-next';

interface Props {
  name: 'PROJECTS' | 'LAB' | 'GAMES';
  size?: number;
  color?: string;
  backgroundColor?: string;
  isActive?: boolean;
}

const props = withDefaults(defineProps<Props>(), {
  size: 24,
  color: 'var(--text-color)',
  backgroundColor: 'transparent',
  isActive: false
});

const iconComponent = computed(() => {
  switch (props.name) {
    case 'PROJECTS':
      return FolderOpen;
    case 'LAB':
      return FlaskConical;
    case 'GAMES':
      return Gamepad2;
    default:
      return FolderOpen;
  }
});
</script>

<style scoped>
svg {
  display: block;
  transition: all 0.3s ease;
}

.icon-active {
  transform: scale(1.1);
}
</style> 