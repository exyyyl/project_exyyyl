<template>
  <svg :width="size" :height="size" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <!-- PROJECTS иконка - папка с проектами -->
    <g v-if="name === 'PROJECTS'">
      <rect x="2" y="6" width="20" height="14" rx="2" :fill="color"/>
      <rect x="6" y="2" width="12" height="4" rx="1" :fill="color"/>
      <rect x="6" y="10" width="4" height="2" :fill="backgroundColor"/>
      <rect x="6" y="14" width="8" height="2" :fill="backgroundColor"/>
    </g>
    
    <!-- LAB иконка - колба -->
    <g v-else-if="name === 'LAB'">
      <rect x="9" y="2" width="6" height="8" :fill="color"/>
      <rect x="7" y="10" width="10" height="8" rx="2" :fill="color"/>
      <rect x="10" y="6" width="4" height="2" :fill="backgroundColor"/>
      <rect x="9" y="12" width="6" height="2" :fill="backgroundColor"/>
      <rect x="11" y="15" width="2" height="2" :fill="backgroundColor"/>
    </g>
    
    <!-- GAMES иконка - геймпад -->
    <g v-else-if="name === 'GAMES'">
      <rect x="4" y="8" width="16" height="8" rx="4" :fill="color"/>
      <rect x="6" y="10" width="2" height="2" :fill="backgroundColor"/>
      <rect x="10" y="10" width="2" height="2" :fill="backgroundColor"/>
      <rect x="16" y="10" width="2" height="2" :fill="backgroundColor"/>
      <rect x="14" y="12" width="2" height="2" :fill="backgroundColor"/>
      <rect x="18" y="12" width="2" height="2" :fill="backgroundColor"/>
    </g>
  </svg>
</template>

<script setup lang="ts">
interface Props {
  name: 'PROJECTS' | 'LAB' | 'GAMES';
  size?: number;
  color?: string;
  backgroundColor?: string;
}

const props = withDefaults(defineProps<Props>(), {
  size: 24,
  color: '#ffffff',
  backgroundColor: '#000000'
});
</script>

<style scoped>
svg {
  display: block;
  transition: all 0.3s ease;
}
</style> 