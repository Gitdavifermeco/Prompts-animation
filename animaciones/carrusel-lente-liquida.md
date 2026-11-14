---
nombre: carrusel-lente-liquida
fecha: 2026-11-14
tipo: carrusel de portfolio con lente de cristal líquido (Three.js, postprocesado)
aprobado: si
origen: pegado por David
---

APPLY THIS ANIMATION TO THE PROJECT YOU CAN ACCESS

INSPECT FIRST
Before editing, inspect the workspace, framework, routes, components, styles and assets. Determine whether it is an empty/starter project or an existing product with meaningful content. A package file or framework scaffold alone does not make it an established site. Do not assume a particular coding agent or technology. If you cannot inspect the project, ask for the relevant files or project context before choosing a path.

EMPTY OR STARTER PROJECT
Build a minimal working page with this animation from scratch, using the installed stack or simple HTML/CSS/JavaScript if no stack exists. Use the supplied assets where needed. Keep the animation the focus on a clean neutral canvas; use another background only when necessary for the effect's visibility or mechanism. Do not add unrelated sections, marketing copy, captions, decorative metadata or demo chrome. Preserve text that is itself animated, essential controls and accessible names. Proceed without asking where to integrate into a nonexistent site.

EXISTING PRODUCT
Inspect how this animation could fit the existing content and interactions. Propose the specific page and component to enhance or replace, state what will change, and confirm that existing content and branding will remain. Ask one concise confirmation before editing, for example: "Apply the curved ribbon to your project gallery, keeping your nine images, logo and cream background?" If several targets fit or the effect is unsuitable, explain briefly and ask which target or alternative the user wants. Do not force it into an unrelated component. If the user has already explicitly approved that exact target and scope, proceed without asking again. Wait for confirmation when it is still needed.

PRESERVE THE EXISTING PRODUCT
Use its framework and styling conventions. Preserve typography, logo, colors, page and section backgrounds, content, images, routes, links and unrelated behavior. Reuse existing images and their count, order and labels; do not replace them with demo assets or ask whether to use supplied versus existing images. Existing assets take precedence over conflicting URLs, download instructions, fixed demo item counts and named initial selections below. Request missing inputs only if the approved effect genuinely needs them and the project has none.
Keep Canvas/WebGL backgrounds transparent or match the existing background. Preserve the absence of decoration: do not import demo floor grids, stages, captions, arrows, borders or persistent selection outlines. Accessible image names do not authorize visible captions. Keep necessary keyboard focus indicators without inventing a persistent highlighted card. Adapt geometry to the host layout while preserving the animation mechanism; do not rebuild the product.

MOTION CONTRACT AND PRIORITY
These environment and integration instructions take precedence over conflicting placement, styling and demo-content instructions below. Preserve specified durations, easing curves, scroll mappings, stagger, reversal, interaction and reduced-motion behavior. Scroll-driven motion should retain its progress mapping rather than gain an arbitrary timed autoplay. A screenshot anchors appearance, not timing. Use Canvas/WebGL only when the effect needs it. Verify responsive layout, keyboard/touch behavior, reduced motion and unaffected surrounding functionality.

ANIMATION SPECIFICATION

Build one responsive portfolio carousel section with a liquid-glass refraction effect. If the project is empty, create only this section. If integrating into an existing project, inspect its structure and confirm the page and placement first. Match existing styles and keep everything scoped to the section.

COMPOSITION
A near-black #121212 stage containing one uninterrupted horizontal row of landscape project covers, narrow 14px gaps, and small or square corners. The middle screens remain straight, crisp and readable. At the left and right, a large tilted elliptical glass lens folds and stretches the passing artwork into broad glossy ribbons. Add visible but controlled red/green/blue dispersion at the refractive rims. This is a postprocessing lens applied to a flat carousel, not a cylindrical 3D carousel, stacked cards, crossfade, or CSS blur. Use only a quiet “Scroll or drag to explore” hint below. No website navigation, artist wordmark, marketing headings, case-study panels, or decorative controls.

RENDERING
Use Three.js, an orthographic camera and two render passes. First draw the flat strip to a WebGLRenderTarget padded by .44 times viewport width and height on all sides. Then draw a fullscreen quad whose shader samples that target. Sample coordinates must account for padding: (uv * viewportResolution + padding) / (viewportResolution + 2 * padding). Padding is essential: the lens bends content beyond the viewport edges, and clamped unpadded textures produce obvious streaks or empty edges. Render three repeated copies of the project list so the padded field is always populated.

LENS
Center it at (0.5,0.5). Correct x by viewport aspect. Rotate the lens coordinates clockwise 65 degrees. Normalize by half-size (.565,1), multiplied by max(1,viewportAspect/(1440/1028)) on wide screens. The normalized radial distance defines the elliptical boundary. Lens influence fades smoothly at distance .93 to1; the middle stays undistorted. Rim strength grows from normalized distance .578 to1. Compute an aspect-correct radial direction and its perpendicular tangent. Apply a tangential displacement weighted by .55*sin(2*azimuth)+.25*sin(azimuth), rim strength, a .6 amplitude and a radius cap .7825. At the rims, sample 12 spectral taps along offset*(11*.004)*smoothstep(.55,1,distance), using Gaussian RGB weights centered at tap positions0,.5,1 with width .38. Normalize each accumulated channel by its total weight. Preserve color-space and tone-mapping output chunks. Do not add a luminous blue outline or bright glow.

CAROUSEL AND INPUT
Desktop card width is about20.5vw capped at470px, aspect1.509, gap14px. Phone width is64vw with10px gaps. Loop positions with centered modular wrapping. Keep an editable array of cover URLs. Support horizontal pointer dragging with capture and cancellation cleanup, vertical/horizontal wheel input, ArrowLeft/ArrowRight stepping, and Home reset. Use a damped target/current position with .09 frame-normalized easing. On drag release, retain a velocity impulse with .865 frame-normalized friction, then snap to the nearest card after120ms of idle. Subtly shrink cards up to7% as speed approaches60px/frame; use .25 attack and .06 release. Never open case-study panels on click.

ENTRANCE AND LIFECYCLE
Use a brief staggered rise from below, then grow the panels to their resting height and bring in the lens. When idle for1.8seconds, drift gently at .48px per60Hz frame; pause that drift on hover, canvas focus, or dragging. Stop the RAF loop while hidden, offscreen, or a same-origin parent still-active message sets active=false. Use one animation loop and clamp delta time to .05s. For reduced motion, skip entry, drift, and inertia, while explicit navigation updates immediately. Use a static horizontal image strip if WebGL fails. Dispose all meshes, textures, render targets, observers, and renderer resources on teardown. Cap DPR and padded target area to avoid excess GPU memory.

PROJECT ARTWORK
Use these existing original portfolio covers; download them and preserve their aspect ratio. Replace them with the user's projects when supplied:
https://thepromptsfactory.com/assets/portfolio-coil/forme-cover.webp
https://thepromptsfactory.com/assets/portfolio-coil/tidal-cover.webp
https://thepromptsfactory.com/assets/portfolio-coil/index-cover.webp
https://thepromptsfactory.com/assets/portfolio-coil/morph-cover.webp
https://thepromptsfactory.com/assets/portfolio-coil/maison-cover.webp
https://thepromptsfactory.com/assets/portfolio-coil/verdant-cover.webp

This is an independently implemented motion study based on the supplied Anfalova carousel reference, using different project content and no source-site branding or artwork. Validate the optical distortion during drag, all input methods, resizing, reduced motion, offscreen pause, and cleanup.
