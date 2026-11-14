---
nombre: carrusel-latas-3d
fecha: 2026-11-14
tipo: carrusel 3D de producto (Three.js, GLTF)
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

Build only this self-contained full-screen 3D product carousel in the existing framework. Preserve host navigation, routes, typography and unrelated sections. The section should reserve 100svh before loading. Use the original Celsius cans and a dark charcoal radial-gradient stage; remove slogans, navigation, product headings, platforms, campaign video and all other source-site sections. Native previous/next, six flavor dots, pause and replay are the only controls.

MEDIA: fetch these public inputs and save them locally. Base URL: https://thepromptsfactory.com/assets/celsius-carousel/
Model can.glb; environment studio.hdr; metalness map metal.avif. For each slug orange, peach-vibe, arctic-vibe, tropical-vibe, watermelon, kiwi-guava, fetch SLUG.png and SLUG-back.png. These are the original front/back package photographs. Never substitute package art. If a URL fails, report that exact URL.

Use Three.js GLTFLoader and HDRLoader. Model mesh names are Shell, Top, Bottom; preserve the model geometry and UVs, multiply each mesh scale.z by 1.15. Build 24 clones repeating six flavors, spacing 3.5. ACESFilmicToneMapping exposure .72, SRGB output, transparent antialiased renderer, DPR capped at 1.5. Perspective camera FOV20, near .1, far200, position(0,0,29); multiply camera Z by1.08 for aspect<.8. Use PMREM from supplied HDR. Metal material color0xaaaaaa, metalness .9, roughness .2, sheen .8, clearcoat1, metalnessMap metal.avif, environment intensity3. Label material color0xd3d3d3, metalness .12, roughness .62, sheen .05, clearcoat .12, clearcoatRoughness .3, environment intensity .35. Add two white spotlights: positions(0,3.5,0) targeting(0,0,1), and(0,-3,2) targeting(0,0,1.8), distance8, angle PI/4, penumbra1, decay .1, final intensity25 each.

Generate a2048x1603 canvas texture per flavor with background #f7f7f5. For every texture column x, distance=x/2048-center; subtract round(distance) for wrap. Front center=.5, back center=0. When abs(distance)<=.245, sample source image column(.5+sin(distance*2PI)*.5)*photo.width clamped to bounds. Front samples vertical .035 through .965 of photograph, back full height. Draw each sampled column into one full-height texture column. Set canvas texture SRGB, anisotropy8.

Let position ease toward target using damping1-exp(-10*dt), dt capped .05 seconds. When not dragging, snap target to round(target/3.5)*3.5. For each clone i, x=wrap(i*3.5-position,-42,42). ratio=clamp(1440/sectionWidth,1,2.4). Once the opening completes, set position(x,sin(x*.25*ratio),-abs(x)-.2), rotation(-PI/9,x*.5-PI/9,PI/16), scale1.2. Each direct mesh child rotation.z=can.rotation.y*.6. Center influence=clamp(1-abs(x)/3.5,0,1). Smooth mouse coordinates relative to section center with the same damping; add smoothX/1280*.2*influence to yaw and smoothY/1280*.2*influence to pitch.

Opening timeline lasts4.5seconds. power4Out(p)=1-(1-clamp(p,0,1))^5. q=power4Out((elapsed-2)/2.5). spacing=lerp(10,1,q), wave=q. Use canX=x*spacing, y=sin(canX*.25*ratio*wave), z=(-abs(x)-.2)*wave; rotation(-PI/9*wave,(canX*.5-PI/9)*wave,PI/16*wave). Add child spin PI/9*(1-q)*influence. Camera Z=lerp(25,29,power4Out((elapsed-1)/2.5)). Light ramps from0 to30 using power4Out(elapsed/2.5), then toward50 from elapsed2 via q; each spotlight uses half this value and angle PI/4*(2-q).

Drag reduces target by horizontal pointer delta*.02; release adds throw -lastDelta*.16 if last move occurred within100ms, then snaps. Detect horizontal gesture after8px and retain native vertical touch panning. Previous/next and arrow keys move target by3.5; flavor dots take the shortest wrapped route. Clicking a neighboring can uses raycasting to step left/right. Wheel steps with a280ms throttle, preserving browser pinch zoom. Announce selected flavor only when its index changes.

Await image decoding and document.fonts.ready before starting. Pause freezes the entire timeline and clock; resume preserves state. Replay resets elapsed, selection, pointer and entrance without reloading. Suspend RAF when hidden or offscreen. Respect reduced motion live: skip entrance and immediately apply selection. Buttons need clear focus rings, accessible labels and pressed state. Release observers, event listeners, GPU textures/materials/geometries, PMREM and RAF on unmount. Verify1440 desktop,390 touch phone,820 tablet, native drag/swipe/wheel/keys, pause/replay, reduced motion, no overflow, missing assets or external runtime calls.
