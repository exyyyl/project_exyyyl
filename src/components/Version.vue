<template>
  <div class="version">
    <span> v{{ version }}</span>
  </div>
</template>

<script setup lang="ts">
const version = '1.0';
</script>

<style scoped>
.version {
  font-size: 12px;
  background-color: #ffffff;
  padding: 5px 10px;
  border-radius: 5px;
  font-weight: 600;
  cursor: pointer;
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
