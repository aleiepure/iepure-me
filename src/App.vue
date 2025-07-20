<script setup lang="ts">
import { ref, computed, type Component } from 'vue';

import Home from './components/Home.vue'
import Projects from './components/Projects.vue'
import NotFound from './components/NotFound.vue'
import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'

const routes: Record<string, Component> = {
  '/': Home,
  "/projects": Projects,
}

const currentPath = ref<string>(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})

const isHomePage = computed(() => {
  console.log('Current path:', currentPath.value);
  return currentPath.value === '#/';
});
</script>

<template>
  <div class="min-h-screen" :class="isHomePage ? 'relative' : 'flex flex-col'">
    <NavBar />
    <main :class="isHomePage ? '' : 'flex-1'">
      <component :is="currentView" />
    </main>
    <Footer :class="isHomePage ? 'fixed bottom-0 left-0 right-0' : ''" />
  </div>
</template>
