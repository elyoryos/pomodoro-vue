1. Interfaz de Usuario (UI)
La aplicación constará de una única pantalla centrada con los siguientes elementos visuales:

Cabecera: Título de la aplicación (ej. "Pomodoro Vue").

Temporizador: Un reloj digital grande en formato MM:SS (minutos y segundos).

Controles: Tres botones principales: "Iniciar", "Pausar" y "Reiniciar".

Indicador de Estado: Un texto dinámico que indique si estamos en "Tiempo de Trabajo" o "Tiempo de Descanso".

Gestor de Tareas: Un campo de entrada de texto (input) y un texto debajo que muestre la "Tarea actual".

2. Estados y Comportamiento Visual
La aplicación tendrá dos estados principales que afectarán al diseño visual (fondo o colores de los elementos):

Estado de Trabajo: Duración de 25 minutos. El tema visual utilizará colores que fomenten la concentración (por ejemplo, tonos rojizos o anaranjados suaves).

Estado de Descanso: Duración de 5 minutos. El tema visual cambiará automáticamente a colores relajantes (por ejemplo, tonos verdes o azulados).

3. Comportamiento Funcional (Lógica)

Botón "Iniciar": Al pulsarlo, el temporizador comenzará una cuenta atrás restando 1 segundo cada vez. Si ya está en marcha, este botón se desactivará o se ocultará para evitar errores.

Botón "Pausar": Detiene la cuenta atrás en el segundo exacto en el que se pulsa. El usuario puede reanudar pulsando "Iniciar" de nuevo.

Botón "Reiniciar": Detiene el temporizador y devuelve el contador a 25:00, restableciendo el estado a "Estado de Trabajo".

Transiciones de tiempo: Cuando la cuenta atrás del "Estado de Trabajo" llegue a 00:00, la aplicación pasará automáticamente al "Estado de Descanso" y el temporizador se ajustará a 05:00 (esperando a que el usuario pulse Iniciar). Cuando acabe el descanso, volverá al modo trabajo a 25:00.

Input de Tarea: El usuario podrá escribir en un campo de texto en qué está trabajando. Al pulsar "Enter" o al perder el foco, el texto se guardará en la pantalla como la tarea activa actual.