<template>
  <div v-if="update" class="modal-overlay" @click="closeModal">
    <div class="modal-content" @click.stop>
      <div class="modal-header">
        <h2>{{ update.title }}</h2>
        <button class="close-btn" @click="closeModal">✕</button>
      </div>
      <div class="modal-body">
        <div class="version-badge">v{{ update.version }}</div>
        <p>{{ update.description }}</p>
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

const props = defineProps<{ update: Update | null }>();
const emit = defineEmits(['close']);

const closeModal = () => {
  emit('close');
};
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
}

.modal-content {
  background-color: var(--secondary-bg);
  border: 1px solid var(--border-color);
  border-radius: 10px;
  max-width: 500px;
  width: 90%;
  max-height: 80vh;
  overflow-y: auto;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
  transition: all 0.3s ease;
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 25px 15px 25px;
  border-bottom: 1px solid var(--border-color);
}

.modal-header h2 {
  margin: 0;
  font-size: 18px;
  color: var(--text-color);
  font-weight: 600;
}

.close-btn {
  background: none;
  border: none;
  color: var(--text-color);
  font-size: 20px;
  cursor: pointer;
  padding: 0;
  width: 24px;
  height: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 4px;
  transition: all 0.3s ease;
}

.close-btn:hover {
  background-color: var(--accent-color);
  color: var(--bg-color);
}

.modal-body {
  padding: 20px 25px 25px 25px;
}

.version-badge {
  background-color: var(--accent-color);
  color: var(--bg-color);
  padding: 6px 12px;
  border-radius: 6px;
  font-size: 12px;
  font-weight: 600;
  display: inline-block;
  margin-bottom: 15px;
  transition: all 0.3s ease;
}

.modal-body p {
  color: var(--text-color);
  font-size: 14px;
  line-height: 1.6;
  margin: 0;
}

/* Мобильная адаптация */
@media (max-width: 480px) {
  .modal-content {
    width: 95%;
    margin: 20px;
  }
  
  .modal-header {
    padding: 15px 20px 12px 20px;
  }
  
  .modal-header h2 {
    font-size: 16px;
  }
  
  .modal-body {
    padding: 15px 20px 20px 20px;
  }
  
  .modal-body p {
    font-size: 13px;
  }
}
</style> 