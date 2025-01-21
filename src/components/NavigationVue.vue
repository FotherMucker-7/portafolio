<template>
  <nav :class="['nav-container', { scrolled: isScrolled }]">
    <div class="container nav-content">
      <RouterLink to="/" class="nav-logo"> {"<YourName />"} </RouterLink>

      <button
        class="nav-mobile-button"
        @click="toggleMobileMenu"
        aria-label="Toggle navigation menu"
      >
        ☰
      </button>

      <ul :class="['nav-links', { active: isMobileMenuOpen }]">
        <li v-for="link in navigationLinks" :key="link.path">
          <RouterLink :to="link.path" class="nav-link" @click="isMobileMenuOpen = false">
            {{ link.name }}
          </RouterLink>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { RouterLink } from 'vue-router'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const navigationLinks = [
  { name: 'Inicio', path: '/' },
  { name: 'Proyectos', path: '/projects' },
  { name: 'Sobre mí', path: '/about' },
  { name: 'Contacto', path: '/contact' },
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

// Evento para cerrar el menú móvil al hacer click fuera
const handleClickOutside = (event) => {
  const nav = event.target.closest('.nav-container')
  if (!nav && isMobileMenuOpen.value) {
    isMobileMenuOpen.value = false
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  document.addEventListener('click', handleClickOutside)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  document.removeEventListener('click', handleClickOutside)
})
</script>
