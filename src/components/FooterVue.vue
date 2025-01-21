<template>
  <footer class="footer">
    <div class="container">
      <p class="footer-text">© {{ currentYear }} Pedro Silva. Todos los derechos reservados</p>
    </div>
  </footer>
</template>

<script setup>
const currentYear = new Date().getFullYear()
</script>

<style scoped>
.footer {
  padding: var(--spacing-md) 0;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  margin-top: auto;
}

.footer-text {
  color: var(--color-text-secondary);
  font-size: 0.9rem;
  text-align: center;
  font-family: var(--font-code);
}
</style>
