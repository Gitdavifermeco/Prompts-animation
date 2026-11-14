---
name: promptanimation
description: Genera prompts largos y precisos para que un agente de código implemente una animación o efecto web a partir de una referencia (captura, vídeo, URL o texto), y aprende de los prompts que David aprueba. Usar con /promptanimation <referencia> para generar y /promptanimation accept <prompt> para guardar y aprobar un prompt. También cuando David pida "hazme un prompt de esta animación" o "saca el prompt de esto".
---

# promptanimation

Convierte una referencia de animación en un prompt tan detallado como los de `animaciones/`. Se mejora sola con los prompts que David aprueba.

## Rutas

- Repo: `C:\Users\david\Documents\Trabajo\Ideas\prompts`
- Prompts guardados: `<repo>\animaciones\<slug>.md`
- Esta skill: `<repo>\skill\promptanimation\` (enlazada desde `~/.claude/skills/promptanimation`)
- Referencias: `references/envelope.md`, `references/formula.md`, `references/quality-checklist.md`, `references/learned-patterns.md`

## Comandos

- `/promptanimation <referencia>`: genera un prompt nuevo.
- `/promptanimation accept <texto del prompt>`: guarda ese prompt tal cual, lo marca aprobado y lo usa para mejorar la skill.
- `/promptanimation accept` sin texto: aprueba el último prompt generado en esta conversación.

El prompt de David solo sirve para mejorar la skill si viene tras `accept`. Sin `accept` nunca aprendes de él.

## Generar un prompt

- Leer `references/formula.md`, `references/envelope.md`, `references/quality-checklist.md` y `references/learned-patterns.md`. Leer también uno o dos prompts de `animaciones/` con `aprobado: si` y tipo de efecto parecido.
- Analizar la referencia y separar lo observado, lo deducido y lo que falta:
  - Imagen o captura: mirarla.
  - URL: inspeccionar la página (HTML, CSS, JS, librerías, valores reales de duración y easing) con las herramientas de navegador o scraping disponibles.
  - Vídeo: extraer fotogramas o usar la skill `analyzing-video` si existe.
  - Texto: usarlo tal cual.
- Preguntar a David solo por valores medibles que no se pueden deducir y que cambian el resultado. Hasta cuatro preguntas por ronda, con recomendación. Si no los sabe, usar un valor razonable y anotarlo como supuesto.
- Redactar la sección ANIMATION SPECIFICATION siguiendo `formula.md`, solo con los bloques que apliquen.
- Pasar `quality-checklist.md`. Corregir hasta que pase.
- Entregar el prompt completo: contenido de `envelope.md` con `{{SPEC}}` sustituido por la especificación. En inglés, en un solo bloque de código (usar cuatro acentos graves para el cierre).
- Guardarlo en `animaciones/<slug>.md` con cabecera `aprobado: no` y `origen: generado`. Decir la ruta y listar los supuestos en pocas líneas.
- Ofrecer `/promptanimation accept` para aprobarlo.

No ejecutar el prompt generado. No inventar URLs ni assets: usar solo los que David o la referencia den.

## accept: guardar, aprobar y aprender

- Guardar el texto exacto, sin editarlo, en `animaciones/<slug>.md`, con cabecera:
  ```
  ---
  nombre: <slug>
  fecha: <AAAA-MM-DD>
  tipo: <tipo de efecto>
  aprobado: si
  origen: pegado por David
  ---
  ```
  Si `accept` aprueba un prompt generado, cambiar su cabecera a `aprobado: si`.
- Si falta el nombre, proponer un slug corto en minúsculas con guiones y pedir confirmación.
- Pasar `quality-checklist.md` al prompt. Si no pasa, decir qué falta punto por punto y no proponer cambios a la skill. El prompt queda guardado igualmente.
- Si pasa, comparar con `formula.md` y `learned-patterns.md` y extraer lo que el prompt hace mejor o de forma nueva: técnicas de redacción, bloques, constantes típicas, ítems de verificación.
- Mostrar a David el diff propuesto para `formula.md`, `quality-checklist.md` o `learned-patterns.md`. Cambiar solo lo que aporte. Si no aporta nada nuevo, decirlo y parar.
- Esperar su "sí" explícito antes de tocar ningún archivo de la skill.
- Tras el "sí": aplicar el diff, añadir una entrada en `CHANGELOG.md` con versión, fecha, prompt de origen y motivo, y subir la versión.
- No borrar reglas existentes sin decir cuáles y por qué. Mantener `formula.md` corto: fusionar patrones parecidos en vez de acumular.

## Estilo de salida

- Chat en español, breve.
- Prompts generados en inglés, con encabezados en MAYÚSCULAS sin numerar.
