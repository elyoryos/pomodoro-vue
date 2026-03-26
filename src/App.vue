<template>
  <div class="app-container" :class="{ 'work-mode': isWorking, 'break-mode': !isWorking }">
    <div class="pomodoro-card">
      <h1>{{ isWorking ? 'Tiempo de Trabajo' : 'Tiempo de Descanso' }}</h1>

      <div class="timer">{{ formattedTime }}</div>

      <div class="controls">
        <button @click="startTimer" :disabled="isRunning">Iniciar</button>
        <button @click="pauseTimer" :disabled="!isRunning">Pausar</button>
        <button @click="resetTimer">Reiniciar</button>
      </div>

      <div class="task-manager">
        <label for="task">Tarea actual:</label>
        <input 
          type="text" 
          id="task" 
          v-model="currentTask" 
          placeholder="¿En qué estás trabajando?" 
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

// 1. Constantes de tiempo (en segundos)
const WORK_TIME = 3;
const BREAK_TIME = 5 * 60;

// 2. Variables de estado (reactivas)
const timeLeft = ref(WORK_TIME);
const isWorking = ref(true); // true = Trabajo, false = Descanso
const isRunning = ref(false);
const currentTask = ref('');
let timerInterval = null;

// 3. Computed para dar formato de reloj (MM:SS)
const formattedTime = computed(() => {
  const minutes = Math.floor(timeLeft.value / 60);
  const seconds = timeLeft.value % 60;
  // Añade un '0' delante si es menor de 10
  return `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
});

// 4. Funciones de los botones
const startTimer = () => {
  if (!isRunning.value) {
    isRunning.value = true;
    timerInterval = setInterval(() => {
      if (timeLeft.value > 0) {
        timeLeft.value--;
      } else {
        // Al llegar a 0, cambiamos de modo
        switchMode();
      }
    }, 1000); // 1000 milisegundos = 1 segundo
  }
};

const pauseTimer = () => {
  isRunning.value = false;
  clearInterval(timerInterval);
};

const resetTimer = () => {
  pauseTimer();
  isWorking.value = true;
  timeLeft.value = WORK_TIME;
};

// 5. Función para alternar entre Trabajo y Descanso
const switchMode = () => {
  pauseTimer();
  isWorking.value = !isWorking.value; // Invierte el estado
  timeLeft.value = isWorking.value ? WORK_TIME : BREAK_TIME;
};
</script>

<style>
/* Estilos globales básicos */
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

/* Contenedor principal a pantalla completa */
.app-container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: background-color 0.5s ease; /* Transición suave de color */
}

/* Colores dinámicos para los estados */
.work-mode {
  background-color: #ff6b6b; /* Rojo suave para foco */
}

.break-mode {
  background-color: #4ecdc4; /* Verde suave para relax */
}

/* Tarjeta blanca central */
.pomodoro-card {
  background: white;
  padding: 3rem;
  border-radius: 15px;
  box-shadow: 0 10px 20px rgba(0,0,0,0.2);
  text-align: center;
  color: #333;
}

/* Estilo del reloj */
.timer {
  font-size: 6rem;
  font-weight: bold;
  margin: 1rem 0;
  font-variant-numeric: tabular-nums; /* Evita que los números salten de tamaño */
}

/* Botones */
.controls button {
  font-size: 1.2rem;
  margin: 0 0.5rem;
  padding: 0.5rem 1rem;
  cursor: pointer;
  border: none;
  border-radius: 8px;
  background-color: #333;
  color: white;
  transition: background-color 0.2s;
}

.controls button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

/* Input de tareas */
.task-manager {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.task-manager input {
  font-size: 1.1rem;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  text-align: center;
}
</style>