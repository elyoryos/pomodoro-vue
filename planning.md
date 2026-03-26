1. Decisiones Técnicas

Framework: Vue 3. Utilizaremos la Composition API (con <script setup>) por ser el estándar moderno, más limpio y fácil de leer.

Estructura: Al ser una aplicación muy sencilla, no utilizaremos un enrutador (Vue Router) ni un gestor de estado complejo (Pinia). Toda la lógica y la interfaz residirán en un único componente principal (App.vue) para mantener el proyecto limpio y cumplir con el requisito de "cuantas menos pantallas, mejor".

Estilos: CSS puro integrado en el mismo archivo del componente. Usaremos variables CSS para cambiar dinámicamente los colores de fondo dependiendo de si el estado es "Trabajo" o "Descanso".

2. Estructura de Archivos del Proyecto
El repositorio tendrá la siguiente estructura básica (usando Vite como herramienta de construcción):

index.html (Punto de entrada)

src/App.vue (Componente principal con la interfaz y la lógica)

src/main.js (Inicialización de Vue)

Carpeta docs/ o archivos .md en la raíz (conteniendo foundations.md, specify.md y planning.md).

README.md (Documentación principal del repositorio).

3. Desglose de Tasques (Tasks)

Fase 1: Configuración inicial

[ ] Inicializar el proyecto con Vite y Vue.

[ ] Limpiar los archivos por defecto que no necesitemos.

Fase 2: Interfaz Visual (Maquetación)

[ ] Crear la estructura HTML en App.vue (Títulos, reloj, botones, input de tarea).

[ ] Añadir estilos CSS básicos y preparar las clases dinámicas para los colores de fondo (Rojo = Trabajo, Verde = Descanso).

Fase 3: Lógica de Programación (Vue.js)

[ ] Crear las variables reactivas (tiempo restante, estado actual, tarea actual).

[ ] Programar la función del temporizador (setInterval) para restar segundos.

[ ] Programar las funciones de los botones: Iniciar, Pausar, Reiniciar.

[ ] Lógica de transición automática: Pasar de Trabajo (25:00) a Descanso (05:00) al llegar a cero.

Fase 4: Revisión y Entrega

[ ] Subir el código final a GitHub.

[ ] Tomar capturas de pantalla de los diferentes estados.

[ ] Redactar el documento PDF final con todos los requisitos.