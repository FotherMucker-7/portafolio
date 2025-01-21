<template>
  <div class="home">
    <!-- Elementos decorativos -->
    <div class="decorative-elements">
      <div class="dec-circle"></div>
      <div class="dec-square"></div>
      <div class="dec-dot"></div>
      <pre class="dec-code-line top-line">const developer = 'Pedro Silva';</pre>
      <pre class="dec-code-line bottom-line">const skills = ['Vue.js', 'Frontend', 'Support'];</pre>
    </div>

    <div class="container">
      <div class="split-layout">
        <!-- Columna Izquierda: Presentación -->
        <section class="hero-section">
          <div class="hero-content">
            <p class="hero-greeting">Hola, mi nombre es</p>
            <h1 class="hero-title">Pedro Silva</h1>
            <h2 class="hero-subtitle">Desarrollo Front-end & Soporte Técnico</h2>
            <div class="hero-actions">
              <RouterLink to="/projects" class="hero-button">Ver Proyectos</RouterLink>
              <RouterLink to="/contact" class="hero-button hero-button-outline"
                >Contactar</RouterLink
              >
            </div>
          </div>
        </section>

        <!-- Columna Derecha: Terminal -->
        <section class="terminal-section">
          <TerminalVue />
        </section>
      </div>
    </div>
  </div>
</template>

<script setup>
import TerminalVue from '@/components/TerminalVue.vue'
</script>

<style scoped>
.home {
  min-height: calc(100vh - 60px);
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
}

/* Elementos decorativos */
.decorative-elements {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  pointer-events: none;
  z-index: 0;
}

.dec-circle {
  position: absolute;
  width: 150px;
  height: 150px;
  border: 2px solid var(--color-primary);
  border-radius: 50%;
  top: 15%;
  left: 10%;
  opacity: 0.1;
  animation: float 8s ease-in-out infinite;
}

.dec-square {
  position: absolute;
  width: 100px;
  height: 100px;
  border: 2px solid var(--color-primary);
  transform: rotate(45deg);
  right: 15%;
  bottom: 20%;
  opacity: 0.1;
  animation: float 6s ease-in-out infinite reverse;
}

.dec-dot {
  position: absolute;
  width: 20px;
  height: 20px;
  background-color: var(--color-primary);
  border-radius: 50%;
  right: 25%;
  top: 30%;
  opacity: 0.1;
  animation: float 4s ease-in-out infinite;
}

.dec-code-line {
  position: absolute;
  font-family: var(--font-code);
  color: var(--color-primary);
  opacity: 0.1;
  font-size: 0.8rem;
  white-space: nowrap;
  overflow: hidden;
}

.top-line {
  top: 25%;
  right: 15%;
  animation: typing 4s steps(40) infinite;
}

.bottom-line {
  bottom: 20%;
  left: 10%;
  animation: typing 4s steps(40) infinite 2s;
}

/* Layout principal */
.split-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-xl);
  align-items: center;
  position: relative;
  z-index: 1;
}

.hero-section {
  display: flex;
  align-items: center;
}

.hero-content {
  max-width: 100%;
}

.hero-greeting {
  font-family: var(--font-code);
  color: var(--color-primary);
  margin-bottom: var(--spacing-md);
  animation: fadeIn 0.5s ease-out;
}

.hero-title {
  font-size: 4rem;
  font-weight: 700;
  margin-bottom: var(--spacing-sm);
  animation: slideUp 0.5s ease-out 0.2s both;
  background: linear-gradient(
    45deg,
    var(--color-text) 0%,
    var(--color-primary) 50%,
    var(--color-text) 100%
  );
  background-size: 200% auto;
  color: transparent;
  -webkit-background-clip: text;
  background-clip: text;
  animation: shine 8s linear infinite;
}

.hero-subtitle {
  font-size: 2.5rem;
  color: var(--color-text-secondary);
  margin-bottom: var(--spacing-lg);
  animation: slideUp 0.5s ease-out 0.3s both;
}

.hero-actions {
  display: flex;
  gap: var(--spacing-md);
  animation: slideUp 0.5s ease-out 0.4s both;
}

.hero-button {
  display: inline-block;
  padding: var(--spacing-md) var(--spacing-lg);
  font-family: var(--font-code);
  text-decoration: none;
  border-radius: 4px;
  transition: all var(--transition-short);
  position: relative;
  overflow: hidden;
}

.hero-button:first-child {
  background-color: var(--color-primary);
  color: var(--color-background);
}

.hero-button:first-child:hover {
  background-color: transparent;
  color: var(--color-primary);
  box-shadow: inset 0 0 0 2px var(--color-primary);
}

.hero-button-outline {
  box-shadow: inset 0 0 0 2px var(--color-primary);
  color: var(--color-primary);
}

.hero-button-outline:hover {
  background-color: rgba(100, 255, 218, 0.1);
}

/* Animaciones */
@keyframes float {
  0%,
  100% {
    transform: translateY(0) rotate(0deg);
  }
  50% {
    transform: translateY(-20px) rotate(5deg);
  }
}

@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

@keyframes shine {
  to {
    background-position: 200% center;
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Responsive */
@media (max-width: 1024px) {
  .split-layout {
    grid-template-columns: 1fr;
    gap: var(--spacing-lg);
  }

  .hero-section {
    text-align: center;
  }

  .hero-actions {
    justify-content: center;
  }

  .hero-title {
    font-size: 3rem;
  }

  .hero-subtitle {
    font-size: 2rem;
  }

  .dec-circle,
  .dec-square,
  .dec-dot,
  .dec-code-line {
    display: none;
  }
}

@media (max-width: 768px) {
  .hero-actions {
    flex-direction: column;
    align-items: stretch;
  }

  .hero-button {
    text-align: center;
  }
}
</style>
