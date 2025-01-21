<template>
  <div class="terminal">
    <div class="terminal-header">
      <div class="terminal-buttons">
        <div class="terminal-button close"></div>
        <div class="terminal-button minimize"></div>
        <div class="terminal-button maximize"></div>
      </div>
      <span class="terminal-title">portfolio.exe</span>
    </div>

    <div class="terminal-content" ref="terminalContent">
      <!-- Mensaje de bienvenida -->
      <div class="terminal-line">
        <span class="terminal-output">Welcome to Portfolio Terminal v1.0.0</span>
      </div>
      <div class="terminal-line">
        <span class="terminal-output">Type 'help' to see available commands</span>
      </div>

      <!-- Historial de comandos -->
      <div v-for="(entry, index) in commandHistory" :key="index" class="terminal-line">
        <template v-if="entry.type === 'command'">
          <span class="terminal-prompt">$</span>
          <span>{{ entry.content }}</span>
        </template>
        <template v-else>
          <span :class="['terminal-output', entry.status]" v-html="entry.content"></span>
        </template>
      </div>

      <!-- Línea de entrada actual -->
      <div class="terminal-line" v-show="isTerminalActive">
        <span class="terminal-prompt">$</span>
        <input
          ref="commandInput"
          v-model="currentCommand"
          class="terminal-input"
          @keyup.enter="executeCommand"
          @keyup.up="navigateHistory('up')"
          @keyup.down="navigateHistory('down')"
          spellcheck="false"
        />
        <span class="terminal-cursor" v-show="isFocused"></span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, nextTick } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const terminalContent = ref(null)
const commandInput = ref(null)
const currentCommand = ref('')
const commandHistory = ref([])
const commandBuffer = ref([])
const currentHistoryIndex = ref(-1)
const isTerminalActive = ref(true)
const isFocused = ref(false)

// Comandos disponibles
const commands = {
  download: {
    description: 'Descarga mi CV en formato PDF',
    action: () => {
      window.open('/cv-pedro-silva.pdf', '_blank')
      return {
        content: 'Iniciando descarga del CV...',
        status: 'success',
      }
    },
  },
  help: {
    description: 'Muestra la lista de comandos disponibles',
    action: () => {
      return {
        content: Object.entries(commands)
          .map(([cmd, { description }]) => `> ${cmd}: ${description}`)
          .join('<br /><br />'),
        status: 'success',
      }
    },
  },
  clear: {
    description: 'Limpia la terminal',
    action: () => {
      commandHistory.value = []
      return null
    },
  },
  about: {
    description: 'Muestra información sobre mí',
    action: () => {
      router.push('/about')
      return {
        content: 'Navegando a la sección Sobre mí...',
        status: 'success',
      }
    },
  },
  projects: {
    description: 'Muestra mis proyectos',
    action: () => {
      router.push('/projects')
      return {
        content: 'Navegando a la sección de Proyectos...',
        status: 'success',
      }
    },
  },
  contact: {
    description: 'Muestra información de contacto',
    action: () => {
      router.push('/contact')
      return {
        content: 'Navegando a la sección de Contacto...',
        status: 'success',
      }
    },
  },
  skills: {
    description: 'Lista mis habilidades técnicas',
    action: () => {
      return {
        content: `
  Frontend: Vue.js, React, JavaScript/TypeScript, HTML5, CSS3
  Backend: Node.js, Express, Python
  Otros: Git, Docker, AWS
          `.trim(),
        status: 'success',
      }
    },
  },
}

// Ejecutar comando
const executeCommand = async () => {
  const command = currentCommand.value.trim().toLowerCase()

  if (command) {
    // Agregar comando al historial
    commandHistory.value.push({
      type: 'command',
      content: command,
    })

    // Agregar al buffer para navegación
    commandBuffer.value.push(command)
    currentHistoryIndex.value = commandBuffer.value.length

    // Ejecutar comando
    if (commands[command]) {
      const result = commands[command].action()
      if (result) {
        commandHistory.value.push(result)
      }
    } else {
      commandHistory.value.push({
        type: 'output',
        content: `Command not found: ${command}. Type 'help' for available commands.`,
        status: 'error',
      })
    }

    // Limpiar entrada y scroll al fondo
    currentCommand.value = ''
    await nextTick()
    scrollToBottom()
  }
}

// Navegación en el historial
const navigateHistory = (direction) => {
  if (direction === 'up') {
    if (currentHistoryIndex.value > 0) {
      currentHistoryIndex.value--
      currentCommand.value = commandBuffer.value[currentHistoryIndex.value]
    }
  } else {
    if (currentHistoryIndex.value < commandBuffer.value.length - 1) {
      currentHistoryIndex.value++
      currentCommand.value = commandBuffer.value[currentHistoryIndex.value]
    } else {
      currentHistoryIndex.value = commandBuffer.value.length
      currentCommand.value = ''
    }
  }
}

// Scroll al fondo de la terminal
const scrollToBottom = () => {
  if (terminalContent.value) {
    terminalContent.value.scrollTop = terminalContent.value.scrollHeight
  }
}

// Eventos de foco
const handleFocus = () => {
  isFocused.value = true
}

const handleBlur = () => {
  isFocused.value = false
}

onMounted(() => {
  // Mantener el foco en el input
  if (commandInput.value) {
    commandInput.value.focus()
    commandInput.value.addEventListener('focus', handleFocus)
    commandInput.value.addEventListener('blur', handleBlur)
  }

  // Click en la terminal enfoca el input
  terminalContent.value?.addEventListener('click', () => {
    commandInput.value?.focus()
  })
})
</script>
