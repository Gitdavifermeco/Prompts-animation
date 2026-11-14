# Lista de calidad

Se usa en dos momentos: antes de entregar un prompt generado, y para decidir si un prompt aprobado con `accept` puede mejorar la skill.

## Obligatorios (si falla uno, el prompt no pasa)

- Objetivo en una o dos frases: qué se construye, alcance de una sola sección, qué se elimina de la fuente.
- Valores medibles: todo valor visual o de movimiento lleva número y unidad. Sin "suave", "rápido" o "grande" sin cifra.
- Mecanismo descrito con fórmulas o algoritmo, no solo con el resultado visual.
- Ciclo de vida: arranque, pausa, fuera de pantalla, reduced motion, limpieza.
- Verificación: viewports y casos concretos a comprobar.

## Deseables (el prompt debe cumplir al menos 80% de la lista completa)

- Negaciones explícitas: qué NO es el efecto.
- Easing y rampas definidos con su fórmula y valores inicial y final.
- Stack y parámetros de renderer o cámara cuando hay WebGL o 3D.
- Cada método de entrada con su umbral y constante.
- Topes de rendimiento: DPR, memoria de texturas, un solo RAF, límite de delta.
- Fallos previstos: asset caído y WebGL fallido.
- Accesibilidad: etiquetas, foco, anuncio de selección.
- Prioridades escritas cuando dos reglas pueden chocar.
- Sin relleno de marketing y sin numerar secciones.
- Sin URLs inventadas.
- Coherente con el sobre: no contradice `envelope.md`.

## Resultado

- Pasa: todos los obligatorios y al menos 80% del total.
- No pasa: decir qué falta, punto por punto, y no proponer cambios a la skill.
