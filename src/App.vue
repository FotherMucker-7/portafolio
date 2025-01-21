<template>
  <div class="app">
    <NavigationVue />
    <main>
      <RouterView v-slot="{ Component }">
        <Transition name="page" mode="out-in">
          <component :is="Component" />
        </Transition>
      </RouterView>
    </main>
    <FooterVue />
  </div>
</template>

<script setup>
import { RouterView } from 'vue-router'
import NavigationVue from './components/NavigationVue.vue'
import FooterVue from './components/FooterVue.vue'
</script>

<style>
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  padding-top: 60px; /* Espacio para la navegación fija */
}

main {
  position: relative;
  z-index: 1;
  flex: 1;
}

/* Transiciones entre páginas */
.page-enter-active,
.page-leave-active {
  transition:
    opacity 0.3s ease,
    transform 0.3s ease;
}

.page-enter-from {
  opacity: 0;
  transform: translateX(20px);
}

.page-leave-to {
  opacity: 0;
  transform: translateX(-20px);
}
</style>
