# Fórmula base de la especificación

Sacada de los prompts aprobados en `animaciones/`. Un prompt final es: sobre fijo (`envelope.md`) + una sección ANIMATION SPECIFICATION. Esta fórmula describe solo esa sección.

## Reglas de estilo

- Escribir en inglés. El chat con David va en español.
- Encabezados en MAYÚSCULAS, sin numerar ("COMPOSITION", no "1. COMPOSITION").
- Prosa densa, sin relleno ni lenguaje de marketing. Cada frase aporta un dato o una restricción.
- Números con unidad: colores en hex, medidas en px/vw/svh, tiempos en s o ms, ángulos en grados o PI.
- Fórmulas con nombre y escritas explícitamente (por ejemplo `power4Out(p)=1-(1-clamp(p,0,1))^5`). Nunca "suave" o "natural" sin constante.
- Negaciones explícitas: decir qué NO es el efecto ("not a cylindrical 3D carousel, not CSS blur") y qué se elimina de la fuente.
- Prioridades escritas: qué manda cuando dos reglas chocan.
- Límites y topes: DPR máximo, área de textura máxima, delta de tiempo máximo.
- Fallos previstos: si un asset falla, si WebGL falla.
- Nunca inventar URLs. Usar solo las que David o la referencia den. Sin assets, pedir los que falten o especificar placeholders generados en local.
- Si la referencia es una web real, cerrar con una nota de estudio independiente: contenido distinto, sin marca ni arte de la web original.

## Bloques de la especificación

Usar solo los que apliquen al efecto, en este orden.

OBJETIVO
Una o dos frases: qué se construye, que es autocontenido y de una sola sección, qué se elimina de la fuente (navegación, eslóganes, titulares, vídeo de campaña) y cuáles son los únicos controles permitidos. Si es un proyecto vacío, crear solo esta sección. Si es existente, inspeccionar y confirmar la ubicación. Reservar la altura antes de cargar (por ejemplo 100svh).

COMPOSITION
Fondo del escenario con color exacto, disposición, tamaños, huecos, esquinas. Qué queda recto y legible y qué se deforma. Texto permitido (una pista discreta como máximo). Lista de elementos prohibidos.

MEDIA
Archivos de entrada con URL base, nombres exactos y rol de cada uno. Regla de no sustituir arte original. Regla de fallo: informar de la URL exacta que falle.

RENDERING
Librería y versión de cargadores. Cámara (tipo, FOV, planos, posición, ajuste por aspecto). Renderer (tone mapping, exposición, espacio de color, transparencia, antialias, tope de DPR). Pasadas de render y render targets con relleno. Materiales con color, metalness, roughness y mapas. Luces con posición, objetivo, ángulo, intensidad.

MECANISMO
El corazón matemático del efecto: coordenadas, transformaciones, pesos, número de muestras, constantes. Escrito con fórmulas y valores, sin adjetivos. Si hay generación procedural (texturas, geometría), describir el algoritmo columna a columna o paso a paso.

MOTION
Posición objetivo/actual con amortiguación (constante y fórmula), snap, inercia, fricción, límites de dt. Ecuaciones por elemento (posición, rotación, escala) en función del índice y la posición. Influencia del ratón o del scroll con sus coeficientes.

ENTRANCE
Línea de tiempo de apertura con duración total, funciones de easing definidas, desfases y rampas (valor inicial y final de cada magnitud: cámara, luz, espaciado).

INPUT
Cada método con su umbral y constante: arrastre (umbral en px, delta, lanzamiento, ventana de tiempo), rueda (throttle, zoom del navegador intacto), teclado, botones, puntos de navegación, clic con raycasting. Gesto horizontal detectado tras N px y panning vertical táctil nativo preservado.

LIFECYCLE
Un solo bucle RAF y delta limitado. Arranque tras decodificar imágenes y fuentes. Pausa y reanudación con estado preservado. Reinicio sin recargar. Suspender oculto o fuera de pantalla. Deriva en reposo con sus condiciones de pausa. Reduced motion respetado en vivo. Fallback si WebGL falla. Limpieza completa de listeners, observers, geometrías, materiales, texturas, render targets y RAF.

ACCESIBILIDAD
Etiquetas, estado pressed, anillos de foco claros, anuncio del elemento seleccionado solo cuando cambia.

VERIFICACIÓN
Viewports concretos (por ejemplo 1440 escritorio, 390 móvil táctil, 820 tablet), métodos de entrada, pausa y reinicio, reduced motion, sin desbordes, assets ausentes, llamadas externas en tiempo de ejecución.

NOTA DE INDEPENDENCIA
Solo si la referencia es una web real: estudio de movimiento implementado de forma independiente, sin marca ni arte de la fuente.
