<template>
  <div class="not-found">
    <div class="container">
      <div class="not-found-content">
        <h1 class="error-code">404</h1>
        <h2 class="error-title">Página no encontrada</h2>
        <p class="error-message">La página que buscas no existe o ha sido movida.</p>
        <RouterLink to="/" class="back-button">Volver al inicio</RouterLink>
      </div>
    </div>
  </div>
</template>

<style scoped>
.not-found {
  min-height: calc(100vh - 60px);
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.not-found-content {
  max-width: 500px;
}

.error-code {
  font-size: 6rem;
  font-weight: 700;
  color: var(--color-primary);
  margin-bottom: var(--spacing-md);
  font-family: var(--font-code);
}

.error-title {
  font-size: 2rem;
  margin-bottom: var(--spacing-md);
}

.error-message {
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-xl);
}

.back-button {
  display: inline-block;
  padding: var(--spacing-md) var(--spacing-lg);
  background-color: transparent;
  border: 2px solid var(--color-primary);
  color: var(--color-primary);
  text-decoration: none;
  font-family: var(--font-code);
  border-radius: 4px;
  transition: all var(--transition-short);
}

.back-button:hover {
  background-color: rgba(100, 255, 218, 0.1);
  transform: translateY(-2px);
}
</style>
