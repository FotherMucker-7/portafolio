<template>
  <div class="projects">
    <div class="container section">
      <header class="projects-header">
        <h1>Proyectos Destacados</h1>
        <p class="projects-subtitle">Una selección de mis trabajos recientes</p>
      </header>

      <div class="projects-grid">
        <!-- Proyecto 1 -->
        <article class="project-card slide-up-fade">
          <div class="project-header">
            <div class="project-folder-icon">📁</div>
            <div class="project-links">
              <a href="#" class="project-link" target="_blank" rel="noopener noreferrer">
                <span class="code-icon">〈/〉</span>
              </a>
              <a href="#" class="project-link" target="_blank" rel="noopener noreferrer">
                <span class="demo-icon">▶</span>
              </a>
            </div>
          </div>

          <h3 class="project-title">Sistema de Gestión de Tareas</h3>
          <p class="project-description">
            Aplicación web para la gestión de tareas y proyectos con funcionalidades de drag and
            drop, filtros avanzados y reportes en tiempo real. Implementación de autenticación y
            autorización de usuarios.
          </p>

          <ul class="project-tech-list">
            <li class="project-tech-item">Vue.js</li>
            <li class="project-tech-item">Vuex</li>
            <li class="project-tech-item">Node.js</li>
            <li class="project-tech-item">MongoDB</li>
          </ul>
        </article>

        <!-- Proyecto 2 -->
        <article class="project-card slide-up-fade">
          <div class="project-header">
            <div class="project-folder-icon">📁</div>
            <div class="project-links">
              <a href="#" class="project-link" target="_blank" rel="noopener noreferrer">
                <span class="code-icon">〈/〉</span>
              </a>
              <a href="#" class="project-link" target="_blank" rel="noopener noreferrer">
                <span class="demo-icon">▶</span>
              </a>
            </div>
          </div>

          <h3 class="project-title">Dashboard Analítico</h3>
          <p class="project-description">
            Panel de control interactivo para visualización de datos empresariales. Incluye gráficos
            dinámicos, filtros en tiempo real y exportación de reportes en múltiples formatos.
          </p>

          <ul class="project-tech-list">
            <li class="project-tech-item">Vue.js</li>
            <li class="project-tech-item">Chart.js</li>
            <li class="project-tech-item">CSS Grid</li>
            <li class="project-tech-item">REST API</li>
          </ul>
        </article>
      </div>
    </div>
  </div>
</template>

<style>
.projects-header {
  text-align: center;
  margin-bottom: var(--spacing-xl);
}

.projects-header h1 {
  color: var(--color-text);
  margin-bottom: var(--spacing-sm);
}

.projects-subtitle {
  color: var(--color-text-secondary);
  font-size: 1.1rem;
}

/* Iconos personalizados */
.code-icon,
.demo-icon {
  font-family: var(--font-code);
  font-size: 1.2rem;
}

/* Media queries */
@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }

  .project-card {
    margin-bottom: var(--spacing-lg);
  }
}
</style>
