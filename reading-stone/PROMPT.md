# Proof — A Reading Stone

The brief for this piece, kept beside `index.html`.

---

## The prompt

Design and build a single-page interactive study of a **reading stone**: the polished glass dome used to enlarge type before spectacles.

It must feel like a printed proof sheet, not a product page and not a dashboard.

### Constraints

- One file: `index.html`. All HTML, CSS, JS inside it.
- No libraries, no frameworks, no build step.
- No images, no SVG assets, no 3D models, no external fonts, no CDN, no network requests.
- Runs by opening the file directly in a browser, offline.
- Canvas 2D, CSS and vanilla JS only.

### Concept

A proofreader's sheet. The page is a printed proof of a short essay, set in a system serif on warm paper. A glass reading stone sits on it. Drag the stone across the page and the type beneath it swells — the actual reading stone's job, at the actual scale (about 1.55×).

Five words on the sheet are misspelled. Slide the stone over them and a red proof correction appears in the margin: the word, corrected. Find all five and the sheet is stamped **proof passed**.

### Visual direction

- Warm off-white paper with a faint laid-paper texture, ink near-black, one red for corrections.
- Hairline page frame, small-caps masthead, generous margins, single measured column.
- The stone is clear glass with a pale green rim, a bright specular highlight, a soft contact shadow and a caustic thrown past its far edge. No colour, no chrome, no plastic.
- Corrections are set like a proofreader's marks: a rule from the margin, then the fix in red italic.

### Interaction

- Drag the stone. It should have weight: spring toward the pointer, settle without overshoot.
- Click anywhere on the paper and the stone glides there.
- Tap the stone to make rings run across the glass, with a soft glass tone (Web Audio).
- Arrow keys move the stone; Enter taps it.
- Reveal all corrections, or reset the proof.
- The article must remain real, selectable DOM text — the magnification is a second, clipped copy.

### Technical approach

- The magnified layer is a clone of the article, scaled about the stone's centre, clipped by a soft radial mask that follows the stone. Text stays crisp and accessible.
- The glass is drawn on a full-viewport Canvas 2D layer above the magnified text: contact shadow, caustic, body gradients, TIR ring, rim, chromatic fringe, specular, tap rings.
- The stone's motion is a damped spring integrated in `requestAnimationFrame`, delta-time based.
- Proof checks run against the live bounding boxes of the five flagged words.
- `prefers-reduced-motion` removes the spring; the page still works.

### Quality bar

It should read as a printed object first and an interface second. If the typography is not convincing, the piece has failed, no matter how good the glass is.
