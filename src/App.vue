<script setup lang="ts">
import { ref } from 'vue';
import Version from './components/Version.vue';
import Layout from './components/Layout.vue';

const activeTab = ref('PROJECTS');

const tabs = [
  { name: 'PROJECTS', content: 'Скоро тут будут проектики' },
  { name: 'LAB', content: 'Идеи для экспериментов' },
  { name: 'GAMES', content: 'Тут когда-нибудь будут игры' }
];
</script>

<template>
  <header>
    <div class="logo"><p class="logo-text"><a href="/">project exyyyl</a></p>
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
}

.logo-text {
  font-size: 24px;
  font-weight: 600;
  color: #fff;
}

.logo-text a {
  text-decoration: none;
  color: #fff;
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
}

.header-menu li a.active {
  background-color: #ffffff;
  color: #000;
}

main {
  flex: 1;
  display: flex;
  align-items: stretch;
  justify-content: center;
  min-height: 0;
}

</style>
