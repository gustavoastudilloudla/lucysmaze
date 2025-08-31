# Lucy's Maze

Juego de laberinto estilo “desliza hasta chocar” hecho con Phaser 3.80.x. Controlas a Lucy por una cuadrícula, recoges monedas, evitas trampas y esquivas enemigos a medida que subes de nivel.

## Cómo Jugar
- Flechas: mueve a Lucy (izquierda, derecha, arriba, abajo). Se desliza hasta encontrar un obstáculo.
- R: reinicia cuando hay Game Over; el botón “Comenzar nuevamente” también reinicia.
- Música: botones Anterior/Siguiente/On-Off y control de volumen en la UI.
- Objetivo: recoge monedas, encuentra la salida parpadeante y sube de nivel. Desde nivel 5 aparecen enemigos.

## Ejecutar Localmente
- No hay build; es un sitio estático.

## Implementación
- Motor: Phaser `@3.80.1` desde CDN (pinned para reproducibilidad) en `index.html`.
- Render: canvas en `#game-container`; estilos en `styles.css`.
- Lógica: `script.js` contiene el juego (escena Phaser, inputs, generación de laberintos, enemigos y UI).
- Rejilla: tablero 10×10 (“cellSize” fijo). Movimiento por direcciones cardinales, con animación hasta el siguiente bloqueo.
- Generación procedural: obstáculos, monedas y trampas con probabilidades configurables (`CONFIG.MAZE_GENERATION`). Se asegura solvencia del laberinto o cae a un layout seguro.
- Progresión: puntaje por monedas; salida cambia de borde; enemigos se habilitan desde el nivel 5; item de “salvación” aparece cuando recoges >70% de las monedas del nivel.
- Audio: autodetección de pistas `bg_XXX.mp3` en `sound/bg/` (ejemplo: `bg_001.mp3`, `bg_002.mp3`, …). Playlist aleatorio, botones de control y slider de volumen.
- Optimización: mapa de colisiones O(1), throttling de input/IA, pooling de sprites y limpieza de listeners para evitar fugas.

## Estructura del Proyecto
- `index.html`: bootstrap del juego y UI básica.
- `styles.css`: estilos de la interfaz.
- `script.js`: código principal (Phaser Scene, CONFIG, lógica del juego).
- `*.png`: sprites en la raíz (jugadora, obstáculos, enemigos, salida, etc.).
- `sound/bg/bg_###.mp3`: música de fondo autodetectada.


## Breve Historia
- Nacimiento: comenzó como un prototipo simple en Javascript para probar movimiento sobre cuadrícula y sprites de mi chihuahua Lucy.
- Inspirado parcialmente/libremente en las mecanicas del juego "The tomb of mask"
- Primeros pasos: se añadió generación de laberintos, monedas, salida dinámica y contador de puntaje/nivel.
- Sonido: se incorporó música de fondo con autodetección de pistas en `sound/bg/` y controles en pantalla.
- Mejora técnica: se introdujeron optimizaciones (throttling, pooling, mapa de colisiones) y limpieza de eventos para robustez.
- Escalada: enemigos a partir del nivel 5, aparición condicionada del ítem de salvación (>70% de monedas) y refinamiento visual (colores de fondo, parpadeo de salida).

## Notas de Desarrollo
- Phaser fijado a `@3.80.x` para builds reproducibles; puedes usar `assets/vendor/phaser.js` si necesitas offline y apuntar el `script src` allí.

¡Gracias por jugar y por cualquier idea o mejora!
