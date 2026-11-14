# Patrones aprendidos

Cada patrón es una técnica de redacción que hace mejores a los prompts. Se añaden solo con aprobación de David (ver `SKILL.md`, flujo accept). Formato: patrón, por qué funciona, de qué prompt sale.

## Semilla inicial (2026-11-14)

Fuentes: `animaciones/carrusel-lente-liquida.md` y `animaciones/carrusel-latas-3d.md`.

- Prioridad escrita. El sobre dice que sus reglas mandan sobre las de la especificación cuando chocan, y que los activos existentes mandan sobre las URLs de demostración. Evita que el agente destruya un proyecto real. Fuente: ambos.
- Explicar por qué una pieza es esencial. "Padding is essential: ... clamped unpadded textures produce streaks". El agente no la quita por simplificar. Fuente: lente líquida.
- Fórmula escrita en línea. Coordenadas de muestreo, pesos gaussianos y easing salen con su expresión, no con una descripción. Fuente: ambos.
- Negación del falso parecido. "Not a cylindrical 3D carousel, stacked cards, crossfade, or CSS blur." Cierra las interpretaciones erróneas más probables. Fuente: lente líquida.
- Lista de elementos a eliminar de la fuente (navegación, eslóganes, titulares, campaña) y lista cerrada de controles permitidos. Fuente: latas 3D.
- Regla de fallo con mensaje exacto: "If a URL fails, report that exact URL". Hace verificables los errores de descarga. Fuente: latas 3D.
- Línea de tiempo con funciones definidas. Duración total, función de easing con su fórmula y rampas con valor inicial y final por magnitud. Fuente: latas 3D.
- Constantes con normalización por fotograma ("frame-normalized easing", "per 60Hz frame") para que el movimiento no dependa de la tasa de refresco. Fuente: lente líquida.
- Umbrales de gesto: horizontal tras 8px, panning vertical táctil nativo preservado, zoom de pellizco del navegador intacto. Fuente: ambos.
- Ciclo de vida completo en una sola frase: bucle RAF único, delta limitado, pausa oculto o fuera de pantalla, reduced motion en vivo, fallback sin WebGL, limpieza de todo recurso GPU. Fuente: ambos.
- Verificación como lista de viewports (1440, 390, 820) y casos (arrastre, rueda, teclado, pausa, reduced motion, desbordes, assets ausentes). Fuente: latas 3D.
- Nota de independencia cuando la referencia es una web real: contenido distinto, sin marca ni arte de la fuente. Fuente: lente líquida.
- Tope explícito de recursos: DPR máximo y área máxima del render target. Fuente: ambos.
