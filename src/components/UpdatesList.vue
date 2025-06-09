<template>
  <div class="updates-dropdown">
    <div class="updates-header">
      <h3>Список обновлений</h3>
      <button class="close-btn" @click="closeList">✕</button>
    </div>
    <div class="updates-content">
      <div 
        v-for="update in updates" 
        :key="update.id" 
        class="update-item"
        @click="selectUpdate(update)"
      >
        <div class="update-version">v{{ update.version }}</div>
        <div class="update-title">{{ update.title }}</div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';

interface Update {
  id: number;
  version: string;
  title: string;
  description: string;
}

const props = defineProps<{ updates: Update[] }>();
const emit = defineEmits(['updateSelected', 'close']);

const selectUpdate = (update: Update) => {
  emit('updateSelected', update);
};

const closeList = () => {
  emit('close');
};
</script>

<style scoped>
.updates-dropdown {
  position: absolute;
  top: calc(100% + 5px);
  right: 0;
  background-color: #1a1a1a;
  border: 1px solid #fff;
  border-radius: 8px;
  min-width: 320px;
  z-index: 1000;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.5);
}

.updates-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px 10px 20px;
  border-bottom: 1px solid #333;
}

.updates-header h3 {
  margin: 0;
  font-size: 14px;
  color: #fff;
  font-weight: 600;
}

.close-btn {
  background: none;
  border: none;
  color: #fff;
  font-size: 16px;
  cursor: pointer;
  padding: 0;
  width: 20px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 3px;
  transition: background-color 0.3s;
}

.close-btn:hover {
  background-color: #333;
}

.updates-content {
  padding: 10px 0;
  max-height: 200px;
  overflow-y: auto;
}

.update-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 20px;
  cursor: pointer;
  transition: background-color 0.3s;
  border-bottom: 1px solid #2a2a2a;
}

.update-item:last-child {
  border-bottom: none;
}

.update-item:hover {
  background-color: #2a2a2a;
}

.update-version {
  background-color: #fff;
  color: #000;
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 10px;
  font-weight: 600;
  min-width: 40px;
  text-align: center;
}

.update-title {
  color: #fff;
  font-size: 12px;
  flex: 1;
}

/* Мобильная адаптация */
@media (max-width: 480px) {
  .updates-dropdown {
    min-width: 250px;
    right: -20px;
  }
  
  .updates-header h3 {
    font-size: 12px;
  }
  
  .update-item {
    padding: 10px 15px;
  }
  
  .update-title {
    font-size: 11px;
  }
}
</style> 