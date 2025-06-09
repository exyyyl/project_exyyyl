<script setup lang="ts">
import { ref } from 'vue';
import Version from './components/Version.vue';
import Layout from './components/Layout.vue';
import IconComponent from './components/IconComponent.vue';

const activeTab = ref('PROJECTS');

const tabs = [
  { name: 'PROJECTS', content: 'Скоро тут будут проектики' },
  { name: 'LAB', content: 'Идеи для экспериментов' },
  { name: 'GAMES', content: 'Тут когда-нибудь будут игры' }
];
</script>

<template>
  <header>
    <div class="logo"><p class="logo-text"><a href="#" @click.prevent="activeTab = 'PROJECTS'">project exyyyl</a></p>
      <Version />
    </div>

    <ul class="header-menu">
      <li v-for="tab in tabs" :key="tab.name">
        <a href="#" @click.prevent="activeTab = tab.name" :class="{ active: activeTab === tab.name }">
          {{ tab.name }}
        </a>
      </li>
    </ul>
  </header>

  <main>
    <Layout :isEmpty="true">
      <h1>{{ tabs.find(tab => tab.name === activeTab)?.content }}</h1>
    </Layout>
  </main>

  <!-- Нижнее меню для мобильных устройств -->
  <nav class="bottom-nav">
    <div 
      v-for="tab in tabs" 
      :key="tab.name"
      class="bottom-nav-item"
      :class="{ active: activeTab === tab.name }"
      @click="activeTab = tab.name"
    >
      <IconComponent 
        :name="tab.name as 'PROJECTS' | 'LAB' | 'GAMES'"
        :size="24"
        :color="activeTab === tab.name ? '#000' : '#fff'"
        :backgroundColor="activeTab === tab.name ? '#fff' : '#000'"
        class="nav-icon"
      />
      <span class="bottom-nav-label">{{ tab.name }}</span>
    </div>
  </nav>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

:global(body) {
  margin: 0;
  padding: 20px;
  box-sizing: border-box;
  font-family: 'Press Start 2P', cursive;
}

:global(#app) {
  width: 100%;
  min-height: calc(100vh - 40px);
  display: flex;
  flex-direction: column;
}

header {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 10px;
}

.logo-text {
  font-size: 24px;
  font-weight: 600;
  color: #fff;
}

.logo-text a {
  text-decoration: none;
  color: #fff;
  cursor: pointer;
  transition: opacity 0.3s;
}

.logo-text a:hover {
  opacity: 0.8;
}

.logo {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}

.header-menu {
  display: flex;
  margin-left: 20px;
  padding: 0;
  gap: 10px;
  flex-wrap: wrap;
}

.header-menu li {
  border-radius: 10px;
  list-style: none;
  font-size: 16px;
}

.header-menu li a {
  text-decoration: none;
  color: #fff;
  background-color: transparent;
  padding: 10px 20px;
  border-radius: 10px;
  transition: background-color 0.3s;
  display: block;
  touch-action: manipulation;
}

.header-menu li a.active {
  background-color: #ffffff;
  color: #000;
}

.header-menu li a:hover {
  opacity: 0.8;
}

@media (hover: none) {
  .header-menu li a:hover {
    opacity: 1;
  }
  
  .header-menu li a:active {
    opacity: 0.8;
    transform: scale(0.95);
  }
}

/* Нижнее меню */
.bottom-nav {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: #1a1a1a;
  border-top: 1px solid #fff;
  display: none; /* По умолчанию скрываем */
  z-index: 1000;
  padding: 10px 0;
}

.bottom-nav-item {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  padding: 8px;
  cursor: pointer;
  touch-action: manipulation;
  transition: all 0.3s ease;
}

.bottom-nav-item.active {
  background-color: #ffffff;
  border-radius: 8px;
  margin: 0 8px;
}

.bottom-nav-label {
  font-size: 10px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.bottom-nav-item.active .bottom-nav-label {
  color: #000;
}

.bottom-nav-item:not(.active) .bottom-nav-label {
  color: #fff;
}

.bottom-nav-item:active {
  transform: scale(0.95);
}

main {
  flex: 1;
  display: flex;
  align-items: stretch;
  justify-content: center;
  min-height: 0;
}

/* Мобильная и планшетная адаптация */
@media (max-width: 1024px) {
  :global(body) {
    padding: 10px 10px 80px 10px; /* Добавляем отступ снизу для нижнего меню */
  }

  :global(#app) {
    min-height: calc(100vh - 100px);
  }

  header {
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    gap: 15px;
  }

  .logo-text {
    font-size: 18px;
  }

  .header-menu {
    display: none; /* Скрываем обычное меню */
  }

  .bottom-nav {
    display: flex; /* Показываем нижнее меню */
  }

  main {
    margin-bottom: 0;
  }

  main h1 {
    font-size: 20px;
    line-height: 1.3;
  }
}

/* Дополнительные стили для планшетов */
@media (min-width: 769px) and (max-width: 1024px) {
  :global(body) {
    padding: 15px 15px 110px 15px; /* Увеличиваем отступ снизу для планшетов */
  }

  :global(#app) {
    min-height: calc(100vh - 140px);
  }

  .logo-text {
    font-size: 22px;
  }

  .bottom-nav {
    padding: 15px 0;
  }

  .bottom-nav-item {
    padding: 12px;
    gap: 6px;
  }

  .nav-icon {
    width: 28px !important;
    height: 28px !important;
  }

  .bottom-nav-label {
    font-size: 12px;
  }

  main h1 {
    font-size: 24px;
  }
}

@media (max-width: 480px) {
  :global(body) {
    padding: 5px 5px 70px 5px;
  }

  .logo-text {
    font-size: 16px;
  }

  .bottom-nav {
    padding: 8px 0;
  }

  .bottom-nav-item {
    padding: 6px;
    gap: 2px;
  }

  .nav-icon {
    width: 20px !important;
    height: 20px !important;
  }

  .bottom-nav-label {
    font-size: 8px;
  }

  main h1 {
    font-size: 16px;
    line-height: 1.4;
    word-break: break-word;
  }
}

</style>
