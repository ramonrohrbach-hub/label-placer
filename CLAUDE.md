# Swisscom AI Label Placer

Single-file browser tool, `index.html`, served by GitHub Pages from `main` / root:
https://ramonrohrbach-hub.github.io/label-placer/

## Rules
- The AI label must never be altered. The four official SVGs (see `labels/`) are embedded in `index.html` as base64 of the original bytes, each with its SHA-256. On load the page re-hashes them; export is disabled on mismatch. Never redraw, recolour or edit the SVG content. If label artwork changes, replace the base64 and hash together, from the new file.
- The label is only scaled proportionally (67 : 28). Two files have no width/height, so they are drawn through a sizing wrapper SVG that references the original unchanged.
- Keep `index.html` self-contained (no external requests); images never leave the browser.

## Behaviour
- Formats: Coreo header 1280×715, Square 1200×1200, Portrait 1200×1500, Landscape 1200×627 (label 96 px), plus Custom (shows width/height/label inputs only when selected).
- Position: Bottom right (default), Bottom left, Top right, Top left.
- Padding: 40 px from the side edge / 32 px from the top or bottom edge for every format and position; "Customize padding" checkbox reveals side and top/bottom inputs.
- Auto label: outline (Transparent_Positive on dark, Transparent_Negative on light); switches to solid (Negative on dark, Positive on light) when the background is busy (`BUSY_SD`, `BUSY_EDGE`) or outline contrast < 4.5:1.
- Contrast meter shows only the 4.5:1 minimum.
- File types: JPG, PNG, WebP, chosen next to the Download button.
- Downloads: uses the claude.ai `downloads` capability when hosted as a claude.ai artifact, a normal link elsewhere, and a "Save your image" right-click fallback when downloading is blocked.

## Testing
Open `index.html` in a browser (or Playwright against `file://`). Check: integrity message is green, each label file renders, each file type downloads with the right header bytes, no console errors, light and dark mode.
