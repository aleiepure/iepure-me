<script setup lang="ts">
import { ref, computed } from 'vue';

import Home from './components/Home.vue'
import Projects from './components/Projects.vue'
import NotFound from './components/NotFound.vue'
import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'

const routes: Record<string, typeof Home | typeof NotFound> = {
  '/': Home,
  "/projects": Projects
}

const getCurrentPath = () => {
  const hash = window.location.pathname;
  console.log('Current path:', hash);
  return hash || '/';
}

const currentPath = ref<string>(getCurrentPath())

window.addEventListener('hashchange', () => {
  currentPath.value = getCurrentPath();
})

const currentView = computed(() => {
  return routes[currentPath.value] || NotFound
})

const isFooterFixed = computed(() => {
  return currentPath.value === '/';
});
</script>

<template>
  <div class="min-h-screen":class="isHomePage ? 'relative' : 'flex flex-col'">
    <NavBar :selectedPath="currentPath" />
    <main :class="isHomePage ? '' : 'flex-1'">
      <component :is="currentView" />
    </main>
    <Footer :class="isFooterFixed ? 'fixed bottom-0 left-0 right-0' : ''" />
  </div>
</template>
