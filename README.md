# Swisscom AI Label Placer

Browser tool that crops an image to a Swisscom format and places the official AI label in a corner, then exports JPG, PNG or WebP.

Open `index.html` in any browser, or use the GitHub Pages site. Images never leave the browser.

## Label artwork

The four official label files are in `labels/`. `index.html` embeds them byte-for-byte and checks their SHA-256 hashes on load; export is disabled if they don't match. The label is only scaled proportionally (67 : 28), never redrawn or recoloured.

## Formats

| Format | Size | Label width |
|---|---|---|
| Coreo header | 1280 × 715 px | 96 px |
| Square | 1200 × 1200 px | 96 px |
| Portrait | 1200 × 1500 px | 96 px |
| Landscape | 1200 × 627 px | 96 px |
| Custom | any | any |

The label goes bottom right by default; it can also be placed bottom left, top right or top left. Padding is 40 px from the side edge and 32 px from the top or bottom edge for every format and position, and can be customized.

## Auto label choice

Auto uses the outline label (white on dark, navy on light). It switches to the solid label when the area behind the label is busy, or when the outline would fall below 4.5:1 contrast.
