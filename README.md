# One HTML Design

**[Open the archive →](https://moreani.github.io/One-HTML-Design/)**

An archive of interactive single-file websites. Every piece is one `index.html` — no libraries, no build step, no images, no network requests. Open it offline and it works.

## The pieces

| # | Piece | What it is |
|---|-------|------------|
| 01 | [Lumen](lumen/) | An optical laboratory. Drag a prism, split white light into a spectrum, focus a lens, catch a reflection, pull a rainbow out of a raindrop. |
| 02 | [Proof](reading-stone/) | A reading stone on a printed proof sheet. Drag the glass dome across the type, watch the words swell, and find the five words that are wrong. |

The root `index.html` is the gallery that links them.

## Run it

Open `index.html` in a browser. No server needed.

To serve the whole archive locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/
```

## Structure

```
index.html            the gallery
lumen/
  index.html          the piece
  PROMPT.md           the brief and notes on the optics
reading-stone/
  index.html
  PROMPT.md
```

Adding a piece: create a folder, drop in an `index.html`, add one row to the gallery.

## Notes

- Canvas 2D, CSS and vanilla JavaScript only. Lumen traces its rays in JavaScript; Proof magnifies a real DOM copy of the article and draws the glass on a canvas layer.
- Both pieces respect `prefers-reduced-motion` and keep their text in the DOM for selection and screen readers.
- Built and tested in Chrome, on desktop and mobile widths.
