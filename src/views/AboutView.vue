<template>
  <div class="about">
    <div class="container section">
      <div class="about-content">
        <!-- Encabezado -->
        <header class="about-header">
          <h1 class="fade-in">Pedro Silva Rojas</h1>
          <h2 class="subtitle slide-up">
            Soporte Técnico, Atención al Cliente y Desarrollo Front-end
          </h2>
        </header>

        <!-- Perfil Profesional -->
        <section class="profile-section">
          <h3>Perfil Profesional</h3>
          <p>
            Con más de 7 años de experiencia en soporte técnico, servicio al cliente y ventas en
            empresas del sector tecnológico y telecomunicaciones. Especializado en brindar
            asistencia técnica y resolver consultas de usuarios, con experiencia en sistemas de pago
            electrónico y servicios de telecomunicaciones. Actualmente ampliando competencias con
            estudios en desarrollo front-end.
          </p>
        </section>

        <!-- Experiencia -->
        <section class="experience-section">
          <h3>Experiencia Profesional</h3>
          <div class="timeline">
            <!-- Trabajo actual -->
            <div class="timeline-item">
              <div class="timeline-date">2024 - Presente</div>
              <div class="timeline-content">
                <h4>Desarrollo Front-end Trainee v2.0</h4>
                <p class="timeline-company">Linares y compañía ltda.</p>
                <ul>
                  <li>HTML5, CSS3, JavaScript</li>
                  <li>Desarrollo web responsive</li>
                </ul>
              </div>
            </div>

            <!-- SumUp -->
            <div class="timeline-item">
              <div class="timeline-date">2021 - 2022</div>
              <div class="timeline-content">
                <h4>Soporte Técnico vía WhatsApp</h4>
                <p class="timeline-company">SumUp</p>
                <ul>
                  <li>
                    Gestioné soporte técnico y comercial vía WhatsApp para usuarios de sistemas de
                    pago.
                  </li>
                  <li>Mantuve un índice de satisfacción del cliente superior al 90%.</li>
                </ul>
              </div>
            </div>

            <!-- Entel -->
            <div class="timeline-item">
              <div class="timeline-date">2018</div>
              <div class="timeline-content">
                <h4>Ejecutivo Atención al Cliente</h4>
                <p class="timeline-company">Entel Call Center</p>
                <ul>
                  <li>
                    Gestioné llamadas de emergencia de clientes empresa sanitaria Aguas Nuevas.
                  </li>
                  <li>
                    Reconocido por mantener la calma y profesionalismo en situaciones de alta
                    presión.
                  </li>
                </ul>
              </div>
            </div>

            <!-- Más experiencia -->
            <div class="timeline-item">
              <div class="timeline-date">2016 - 2017</div>
              <div class="timeline-content">
                <h4>Ejecutivo Back Office</h4>
                <p class="timeline-company">Atento Chile VTR</p>
                <ul>
                  <li>Resolví solicitudes por reclamos técnicos/comerciales de clientes VTR.</li>
                  <li>
                    Segunda línea de atención al cliente. Alto índice de resolución vía correo
                    electrónico.
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </section>

        <!-- Habilidades -->
        <section class="skills-section">
          <h3>Habilidades</h3>
          <div class="skills-grid">
            <div class="skills-category">
              <h4>Técnicas</h4>
              <ul>
                <li>HTML5 y CSS3</li>
                <li>JavaScript, Vue.js</li>
                <li>Soporte Técnico de Sistemas de Pago</li>
                <li>Microsoft Office Suite</li>
                <li>Adobe Photoshop</li>
              </ul>
            </div>
            <div class="skills-category">
              <h4>Blandas</h4>
              <ul>
                <li>Resolución de Problemas</li>
                <li>Comunicación Efectiva</li>
                <li>Trabajo en Equipo</li>
                <li>Gestión del Tiempo</li>
                <li>Atención al Detalle</li>
              </ul>
            </div>
          </div>
        </section>

        <!-- CV Download -->
        <section class="cv-section">
          <a href="/cv-pedro-silva.pdf" target="_blank" class="cv-download-btn"> Descargar CV </a>
        </section>
      </div>
    </div>
  </div>
</template>

<style>
.about-content {
  max-width: 800px;
  margin: 0 auto;
  padding-top: var(--spacing-xl);
}

.about-header {
  text-align: center;
  margin-bottom: var(--spacing-xl);
}

.subtitle {
  color: var(--color-text-secondary);
  font-size: 1.2rem;
  margin-top: var(--spacing-sm);
}

section {
  margin-bottom: var(--spacing-xl);
}

h3 {
  color: var(--color-primary);
  margin-bottom: var(--spacing-lg);
}

/* Timeline */
.timeline {
  position: relative;
  padding-left: 2rem;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--color-primary);
  opacity: 0.3;
}

.timeline-item {
  position: relative;
  margin-bottom: var(--spacing-xl);
  padding-left: var(--spacing-lg);
}

.timeline-item::before {
  content: '';
  position: absolute;
  left: -5px;
  top: 0;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: var(--color-primary);
}

.timeline-date {
  color: var(--color-primary);
  font-family: var(--font-code);
  font-size: 0.9rem;
  margin-bottom: var(--spacing-sm);
}

.timeline-content h4 {
  color: var(--color-text);
  margin-bottom: var(--spacing-sm);
}

.timeline-company {
  color: var(--color-text-secondary);
  font-size: 0.9rem;
  margin-bottom: var(--spacing-sm);
}

/* Skills Grid */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--spacing-lg);
}

.skills-category h4 {
  color: var(--color-primary);
  margin-bottom: var(--spacing-md);
}

.skills-category ul {
  list-style: none;
}

.skills-category li {
  position: relative;
  padding-left: var(--spacing-md);
  margin-bottom: var(--spacing-sm);
}

.skills-category li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: var(--color-primary);
}

/* CV Download Button */
.cv-section {
  text-align: center;
  margin-top: var(--spacing-xl);
}

.cv-download-btn {
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

.cv-download-btn:hover {
  background-color: rgba(100, 255, 218, 0.1);
  transform: translateY(-2px);
}

/* Responsive */
@media (max-width: 768px) {
  .about-content {
    padding: var(--spacing-lg);
  }

  .timeline {
    padding-left: 1rem;
  }

  .timeline-item {
    padding-left: var(--spacing-md);
  }
}
</style>
