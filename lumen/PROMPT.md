# LUMEN — The Light Laboratory

The build prompt for this piece. Kept alongside `index.html` so the study can be reproduced, forked, or argued with.

---

## The prompt

You are an award-winning creative developer, interaction designer, computational graphics engineer and expert in vanilla JavaScript, HTML5 Canvas, CSS and SVG.

Build a visually extraordinary, fully interactive optical laboratory as ONE standalone HTML file.

The finished experience should feel like an Awwwards-quality interactive digital artwork, not a conventional educational website.

### 1. Absolute technical restrictions

These requirements are non-negotiable:

- Output exactly ONE file: `index.html`.
- All HTML, CSS and JavaScript must be contained in that file.
- No external JavaScript libraries.
- No React, Vue, Three.js or WebGL libraries.
- No image files of any kind.
- No SVG image assets.
- No 3D models.
- No external fonts.
- No CDN dependencies.
- No external stylesheets.
- No network requests.
- No backend.
- No build process.
- No Node.js required to run the website.
- No AI image or video generation.

Allowed technologies: HTML5, CSS3, vanilla JavaScript, Canvas 2D API, inline SVG markup, CSS transforms, CSS gradients, Web Audio API.

Use only procedurally generated graphics. The final website must work by opening `index.html` directly in Chrome, even without an internet connection.

### 2. Visual target

Website name: LUMEN. Tagline: "Play with Light."

Create a cinematic black-background optical laboratory.

- Near-black charcoal background.
- Elegant ivory typography.
- Refined serif headings using system fonts.
- Minimal navigation.
- Extremely polished controls.
- Soft optical highlights.
- Subtle reflections.
- Beautiful rainbow dispersion.
- No generic dashboard styling.

The centrepiece must be a large, realistically illustrated triangular glass prism produced entirely through Canvas drawing.

A bright white beam of light enters from the left, refracts through the prism and emerges as a beautiful rainbow.

Use layered procedural drawing techniques — gradients, paths, highlights, transparency and animated light effects — to give the prism apparent depth and volume. The illustration must not be static. It must respond dynamically to the user's interactions.

### 3. Page layout

Desktop:

- Header: LUMEN | Lab | Experiments | Gallery | About | Sound
- Left hero: "Play / with Light."
- Description: "An interactive exploration of the invisible rules that shape everything we see."
- Main area: a large interactive optical workbench.
- Bottom toolbar: LIGHT | PRISM | LENS | MIRROR | WATER
- Right-side floating properties panel, shown when an object is selected.
- Primary canvas fills most of the viewport.

Make the design responsive to mobile screens.

### 4. Core interactive engine

Implement a true 2D optics simulation with a reusable ray-tracing engine:

- Ray origin, direction, intensity, wavelength.
- Reflection, refraction, surface normals.
- Ray-object intersections, multiple object interactions, maximum bounce limits.

Use Snell's law for refraction. Use the law of reflection for mirrors. Use wavelength-dependent refractive indices for a basic dispersion simulation.

All calculations performed in JavaScript. Never use a static rainbow image or a fixed decorative effect that ignores the object's physical orientation.

### 5. Interactive objects

**A. Triangular prism** — drag to move, rotate with an on-screen handle, adjust refractive index, change material, reset orientation. Premium translucent look: glass transparency, edge highlights, internal gradients, procedural reflections, soft shadows, apparent thickness. As it rotates, the incoming light must refract and the outgoing rainbow must change direction.

**B. Light source** — draggable; change beam angle, brightness, beam width; switch white or monochromatic light; select wavelength. Beam drawn procedurally.

**C. Convex lens** — transparent biconvex lens with a physically motivated 2D thin-lens approximation; adjustable focal length; rays converge according to configuration.

**D. Concave lens** — diverging version; light spreads as it passes through.

**E. Mirror** — sleek reflective surface; drag, rotate; reflected direction responds to mirror angle.

**F. Water droplet** — glossy circle; representative ray paths through its boundary; refraction and internal reflection; physically motivated simplifications for rainbows.

### 6. Workbench interactions

Select tools; add optical elements; move objects; rotate objects; delete objects; reset the scene; zoom the workbench; pause animations; toggle ray-path visibility; switch between experiment presets. Support multiple objects simultaneously. Consistent pointer-interaction system with correct coordinate conversion for zooming and resizing.

### 7. Five built-in experiments

1. Split White Light
2. Reflection Playground
3. Focus the Beam
4. Make a Rainbow
5. Optical Puzzle

Each loads a different functional configuration, with a compact explanation panel and a meaningful interactive goal.

### 8. Visual polish

Procedurally generate: glass edge highlights, optical dispersion, rainbow beam trails, soft illumination, light halos, mirror reflections, subtle animated background particles, depth-like shadows, smooth selection outlines, precision drag handles. Layered Canvas drawing, smooth rAF animation, devicePixelRatio-aware rendering. Avoid flashy effects that obscure actual ray behaviour.

### 9. Gallery and export

Save scenes to localStorage, restore them, export a PNG from the canvas, reset to the default scene. No backend. Store configuration data, not images.

### 10. Responsiveness

Desktop: immersive full-viewport laboratory with elegant floating controls.

Mobile: compact toolbar, touch-friendly handles, collapsible properties panel, adapted scene framing. Support mouse, touch and trackpad.

### 11. Performance

Smooth rAF rendering; conditional redraw where practical; efficient intersections; reasonable ray counts; cached gradients and reusable geometry; adaptive rendering quality; no unnecessary allocations inside the render loop.

### 12. Educational information

Dynamically calculated readouts for the selected object — refractive index, incident and refraction angles, wavelength, mirror angles, focal length and whether a lens converges or diverges. Short, accessible explanations. Never display invented numerical measurements.

### 13. Code quality

Inside the single file, organise code into labelled sections: document structure, CSS design system, application state, vector mathematics, optical physics, geometry and intersections, canvas rendering, object interactions, UI controls, experiments and presets, persistence and export, main animation loop. Descriptive functions, sensible abstraction, no minification, comments on important optics calculations.

### 14. Testing

Open `index.html` locally. Test prism drag and rotation, dynamic dispersion, light-source controls, lens focusing, mirror reflection, water refraction, multiple objects, scene reset, preset loading, localStorage, PNG export, mobile layout and the browser console.

### 15. Quality standard

The result must look like an exceptional interactive digital exhibition. Avoid ordinary rectangular dashboards, generic button-heavy layouts, cartoon-looking glass, flat static illustrations, fake physics, nonfunctional controls, placeholder UI, unnecessary onboarding and external dependencies.

The first screen must be visually stunning. The visitor should immediately understand that they can interact with light.

### 16. Final deliverable

Create `index.html` — one self-contained, readable, functional, visually polished file. Verify it exists, validate the JavaScript, open it in a browser, test the interactive features, fix problems, and report what works and any known limitations.

Prioritise: visual excellence, genuine interactivity, physically meaningful behaviour, performance, code quality.

---

## Notes on this build

- WebGL is not used; the glass, beams and dispersion are Canvas 2D plus a JavaScript ray tracer.
- White light is traced as 19 spectral samples (415–695 nm). Each has its own refractive index via a Cauchy approximation, so the fan appears because the rays genuinely diverge.
- The prism starts tilted so the beam enters near 46°, which keeps the second face below the critical angle. The default fan is about 12° wide; rolling the prism toward upright widens it past 16°, which is the first experiment's goal.
- Droplet rainbows come from one internal reflection. The reflected branch is deliberately amplified for visibility — a stated, physically motivated simplification.
- The lens is a thin-lens approximation: the transverse slope changes by `−u/f` at the lens plane; rays arriving from behind get the mirrored sign.
- Five goals are checked from live ray data, not scripted: spectrum spread, target hits, beam energy at the target, and focal-point coincidence.
