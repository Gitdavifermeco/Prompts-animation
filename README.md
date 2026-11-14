# Prompts de animación

Repositorio de prompts largos para que un agente de código reproduzca animaciones y efectos web, más una skill que genera prompts nuevos a partir de una referencia y mejora con los que se aprueban.

## Estructura

- `animaciones/`: un `.md` por prompt, con el texto exacto y una cabecera (nombre, fecha, tipo, aprobado, origen).
- `skill/promptanimation/`: la skill de Claude Code.
  - `SKILL.md`: comandos y flujos.
  - `references/envelope.md`: sobre fijo común a todos los prompts.
  - `references/formula.md`: fórmula de la sección ANIMATION SPECIFICATION.
  - `references/quality-checklist.md`: lista de calidad.
  - `references/learned-patterns.md`: patrones aprendidos de prompts aprobados.
  - `CHANGELOG.md`: registro de mejoras.

## Prompts guardados

- `carrusel-lente-liquida`: carrusel de portfolio con lente de cristal líquido (Three.js, postprocesado, dispersión RGB).
- `carrusel-latas-3d`: carrusel 3D de latas de producto (Three.js, GLTF, apertura de 4,5 s).

## Uso

- `/promptanimation <referencia>`: genera un prompt a partir de una captura, vídeo, URL o texto.
- `/promptanimation accept <prompt>`: guarda el prompt, lo marca como aprobado y propone mejoras a la skill. Nada cambia en la skill hasta que se confirme el diff.

## Instalar la skill en otro equipo

En PowerShell, desde la raíz del repo:

```powershell
New-Item -ItemType Junction -Path "$HOME\.claude\skills\promptanimation" -Target "$PWD\skill\promptanimation"
```
