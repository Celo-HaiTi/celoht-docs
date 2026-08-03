# CeloHT Favicon Guide

## Source File

All favicons are generated from `logos/favicons/celoht-favicon-source.svg` — a simplified, high-contrast version of the icon mark, optimized for legibility at very small sizes (the bar-chart arrow is thickened and the clear space is minimized).

## Required Sizes

| File | Size | Usage |
|---|---|---|
| `favicon.ico` | 16×16, 32×32, 48×48 (multi-res ICO) | Legacy browser tab icon |
| `favicon-16x16.png` | 16×16 | Browser tab (modern) |
| `favicon-32x32.png` | 32×32 | Browser tab (retina) |
| `apple-touch-icon.png` | 180×180 | iOS home screen |
| `android-chrome-192x192.png` | 192×192 | Android home screen |
| `android-chrome-512x512.png` | 512×512 | Android splash / PWA |
| `mstile-150x150.png` | 150×150 | Windows tile |
| `safari-pinned-tab.svg` | vector, single color | Safari pinned tab (use `logos/monochrome/celoht-logo-monochrome-black.svg`) |

## How to Generate the Full Set

The source SVG is intentionally simple so it can be exported with any standard SVG-to-PNG/ICO tool. From the repository root:

```bash
# Using an SVG rasterizer (e.g. resvg, Inkscape, or an online exporter)
resvg logos/favicons/celoht-favicon-source.svg favicon-16x16.png -w 16 -h 16
resvg logos/favicons/celoht-favicon-source.svg favicon-32x32.png -w 32 -h 32
resvg logos/favicons/celoht-favicon-source.svg apple-touch-icon.png -w 180 -h 180
resvg logos/favicons/celoht-favicon-source.svg android-chrome-192x192.png -w 192 -h 192
resvg logos/favicons/celoht-favicon-source.svg android-chrome-512x512.png -w 512 -h 512
resvg logos/favicons/celoht-favicon-source.svg mstile-150x150.png -w 150 -h 150

# Combine into a multi-resolution ICO (e.g. with ImageMagick)
convert favicon-16x16.png favicon-32x32.png favicon.ico
```

> Any equivalent tool works — Inkscape CLI, `sharp` (Node.js), Pillow (Python via `cairosvg`), or a browser-based favicon generator fed the source SVG. The critical rule is: **always generate from `celoht-favicon-source.svg`**, never from the full horizontal or vertical lockup, which will not read clearly at 16×16.

## HTML Implementation

```html
<link rel="icon" type="image/x-icon" href="/favicon.ico">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="192x192" href="/android-chrome-192x192.png">
<link rel="mask-icon" href="/safari-pinned-tab.svg" color="#1B2A4A">
<meta name="theme-color" content="#1B2A4A">
<meta name="msapplication-TileColor" content="#FCE94F">
<meta name="msapplication-TileImage" content="/mstile-150x150.png">
```

## web app manifest (`site.webmanifest`)

```json
{
  "name": "CeloHT",
  "short_name": "CeloHT",
  "icons": [
    { "src": "/android-chrome-192x192.png", "sizes": "192x192", "type": "image/png" },
    { "src": "/android-chrome-512x512.png", "sizes": "512x512", "type": "image/png" }
  ],
  "theme_color": "#1B2A4A",
  "background_color": "#FCE94F",
  "display": "standalone"
}
```
