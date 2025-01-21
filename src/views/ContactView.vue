<template>
  <div class="contact">
    <div class="container section">
      <div class="contact-content">
        <!-- Encabezado -->
        <header class="contact-header">
          <h1>Contacto</h1>
          <p class="contact-subtitle">¿Interesado en trabajar juntos? ¡Conversemos!</p>
        </header>

        <!-- Información de contacto -->
        <section class="contact-info">
          <div class="contact-card">
            <div class="contact-card-icon">📧</div>
            <h3>Email</h3>
            <a href="mailto:pedromsilvar.20@gmail.com" class="contact-link">
              pedromsilvar.20@gmail.com
            </a>
          </div>

          <div class="contact-card">
            <div class="contact-card-icon">📱</div>
            <h3>Teléfono</h3>
            <a href="tel:+56967557569" class="contact-link"> +56 9 6755 7569 </a>
          </div>

          <div class="contact-card">
            <div class="contact-card-icon">📍</div>
            <h3>Ubicación</h3>
            <p class="contact-text">Puente Alto, Santiago</p>
          </div>
        </section>

        <!-- Notificación -->
        <div
          v-if="notification.show"
          :class="['notification', `notification-${notification.type}`]"
        >
          {{ notification.message }}
        </div>

        <!-- Formulario de contacto -->
        <section class="contact-form-section">
          <h2>Envíame un mensaje</h2>

          <form class="contact-form" @submit.prevent="handleSubmit">
            <div class="form-group">
              <label for="name">Nombre</label>
              <input
                type="text"
                id="name"
                v-model="formData.name"
                required
                placeholder="Tu nombre"
              />
            </div>

            <div class="form-group">
              <label for="email">Email</label>
              <input
                type="email"
                id="email"
                v-model="formData.email"
                required
                placeholder="tu@email.com"
              />
            </div>

            <div class="form-group">
              <label for="message">Mensaje</label>
              <textarea
                id="message"
                v-model="formData.message"
                required
                placeholder="¿En qué puedo ayudarte?"
                rows="5"
              ></textarea>
            </div>

            <button type="submit" class="submit-button">Enviar mensaje</button>
          </form>
        </section>

        <!-- Disponibilidad -->
        <section class="availability-section">
          <div class="availability-card">
            <h3>Disponibilidad</h3>
            <p>Modalidad: Híbrido/Remoto</p>
            <p>Disponibilidad inmediata</p>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
  name: '',
  email: '',
  message: '',
})

const notification = ref({
  show: false,
  message: '',
  type: '',
})

const showNotification = (message, type) => {
  notification.value = {
    show: true,
    message,
    type,
  }

  // Ocultar la notificación después de 3 segundos
  setTimeout(() => {
    notification.value.show = false
  }, 3000)
}

const handleSubmit = async () => {
  // Validación básica
  if (!formData.value.name || !formData.value.email || !formData.value.message) {
    showNotification('Por favor, completa todos los campos', 'error')
    return
  }

  try {
    // Aquí simularemos el envío (reemplazar con tu lógica real de envío)
    await new Promise((resolve) => setTimeout(resolve, 1000))

    // Mostrar éxito
    showNotification('¡Mensaje enviado con éxito!', 'success')

    // Reiniciar formulario
    formData.value = {
      name: '',
      email: '',
      message: '',
    }
  } catch {
    showNotification('Hubo un error al enviar el mensaje. Por favor, intenta nuevamente.', 'error')
  }
}
</script>

<style>
.contact-content {
  max-width: 800px;
  margin: 0 auto;
  padding-top: var(--spacing-xl);
}

.contact-header {
  text-align: center;
  margin-bottom: var(--spacing-xl);
}

.contact-subtitle {
  color: var(--color-text-secondary);
  font-size: 1.2rem;
  margin-top: var(--spacing-sm);
}

/* Tarjetas de información de contacto */
.contact-info {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: var(--spacing-lg);
  margin-bottom: var(--spacing-xl);
}

.contact-card {
  background: rgba(45, 45, 45, 0.3);
  border-radius: 8px;
  padding: 20px 10px;
  text-align: center;
  transition: transform var(--transition-medium);
}

.contact-card:hover {
  transform: translateY(-5px);
}

.contact-card-icon {
  font-size: 2rem;
  margin-bottom: var(--spacing-sm);
}

.contact-card h3 {
  color: var(--color-primary);
  margin-bottom: var(--spacing-sm);
}

.contact-link {
  color: var(--color-text);
  text-decoration: none;
  transition: color var(--transition-short);
}

.contact-link:hover {
  color: var(--color-primary);
}

.contact-text {
  color: var(--color-text);
}

/* Formulario de contacto */
.contact-form-section {
  margin-top: var(--spacing-xl);
  background: rgba(45, 45, 45, 0.3);
  padding: var(--spacing-xl);
  border-radius: 8px;
}

.contact-form-section h2 {
  text-align: center;
  margin-bottom: var(--spacing-lg);
  color: var(--color-primary);
}

.contact-form {
  display: grid;
  gap: var(--spacing-md);
}

.form-group {
  display: grid;
  gap: var(--spacing-sm);
}

.form-group label {
  color: var(--color-text);
  font-family: var(--font-code);
  font-size: 0.9rem;
}

.form-group input,
.form-group textarea {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 4px;
  padding: var(--spacing-sm);
  color: var(--color-text);
  font-family: var(--font-main);
  transition: all var(--transition-short);
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--color-primary);
  background: rgba(255, 255, 255, 0.1);
}

.submit-button {
  background: transparent;
  color: var(--color-primary);
  border: 2px solid var(--color-primary);
  padding: var(--spacing-md);
  border-radius: 4px;
  font-family: var(--font-code);
  cursor: pointer;
  transition: all var(--transition-short);
}

.submit-button:hover {
  background: rgba(100, 255, 218, 0.1);
  transform: translateY(-2px);
}

/* Sección de disponibilidad */
.availability-section {
  margin-top: var(--spacing-xl);
}

.availability-card {
  background: rgba(45, 45, 45, 0.3);
  border-radius: 8px;
  padding: var(--spacing-lg);
  text-align: center;
}

.availability-card h3 {
  color: var(--color-primary);
  margin-bottom: var(--spacing-md);
}

.availability-card p {
  color: var(--color-text);
  margin-bottom: var(--spacing-sm);
}

/* Notificaciones */
.notification {
  position: fixed;
  top: 20px;
  right: 20px;
  padding: var(--spacing-md) var(--spacing-lg);
  border-radius: 4px;
  animation: slideIn 0.3s ease forwards;
  z-index: 1000;
}

.notification-success {
  background-color: rgba(39, 201, 63, 0.9);
  color: white;
}

.notification-error {
  background-color: rgba(255, 95, 86, 0.9);
  color: white;
}

@keyframes slideIn {
  from {
    transform: translateX(100%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

/* Responsive */
@media (max-width: 768px) {
  .contact-content {
    padding: var(--spacing-lg);
  }

  .contact-form-section {
    padding: var(--spacing-lg);
  }
}
</style>
