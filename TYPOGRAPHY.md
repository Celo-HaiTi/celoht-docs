# CeloHT Typography

## Font Families

### Primary — Headings: **Fraunces**
A warm, humanist serif with character — used for headlines, section titles, and brand moments. Conveys trust and craft without feeling corporate or cold. Free and open source (SIL Open Font License), available via Google Fonts.

### Secondary — Body & UI: **IBM Plex Sans**
Highly legible at small sizes, supports an exceptionally wide range of Latin characters (important for French and Haitian Creole diacritics), and is free/open source (SIL OFL). Used for body copy, UI labels, navigation, and documentation.

### Monospace — Code: **IBM Plex Mono**
Used in documentation, code samples, and technical specs. Pairs naturally with IBM Plex Sans.

> Both families are 100% free, open source, and self-hostable — critical for a low-bandwidth, accessibility-first audience. Never substitute proprietary fonts that require licensing fees.

---

## Type Scale

| Token | Size (px / rem) | Line height | Weight | Usage |
|---|---|---|---|---|
| `display` | 56px / 3.5rem | 1.1 | Fraunces 600 | Hero headlines only |
| `h1` | 40px / 2.5rem | 1.15 | Fraunces 600 | Page titles |
| `h2` | 32px / 2rem | 1.2 | Fraunces 600 | Section headers |
| `h3` | 24px / 1.5rem | 1.3 | Fraunces 500 | Subsections |
| `h4` | 20px / 1.25rem | 1.4 | Plex Sans 600 | Card titles, minor headers |
| `body-lg` | 18px / 1.125rem | 1.6 | Plex Sans 400 | Lead paragraphs |
| `body` | 16px / 1rem | 1.6 | Plex Sans 400 | Default body text |
| `body-sm` | 14px / 0.875rem | 1.5 | Plex Sans 400 | Captions, metadata |
| `label` | 13px / 0.8125rem | 1.4 | Plex Sans 600 (uppercase, tracked) | Form labels, tags |
| `code` | 14px / 0.875rem | 1.5 | Plex Mono 400 | Inline & block code |

---

## Letter Spacing

- Headings (`h1`–`h3`): `-0.01em` (slightly tightened, per Fraunces' generous natural spacing)
- Body text: `0` (default)
- Uppercase labels: `+0.06em` (opened up for legibility at small sizes)

---

## Usage Examples

**Correct:**
> `h1` "Financial inclusion, built with community" set in Fraunces 600, Navy `#1B2A4A`, followed by `body-lg` in Plex Sans 400, Slate `#4A5568`.

**Incorrect:**
> Setting entire paragraphs in Fraunces (serif body text at length reduces legibility for low-literacy and screen-reader-assisted readers — Fraunces is for headlines only).

---

## Multilingual Considerations

CeloHT content is frequently published in **Haitian Creole**, French, and English. Requirements:

- Fonts must support full Latin Extended character sets (both Plex Sans and Fraunces do)
- Avoid all-caps for Haitian Creole body text — diacritics and accented characters can be visually distorted in some all-caps renderings
- Line height of at least 1.5 for body text to support readers using screen magnification or lower literacy reading pace

---

## Accessibility

- Minimum body text size: 16px (1rem) — never smaller for primary reading content
- Minimum contrast: see [COLOR_SYSTEM.md](./COLOR_SYSTEM.md) — all text/background pairings must meet WCAG 2.2 AA at minimum
- Never use font weight or color alone to indicate interactivity (links must be underlined or otherwise distinguished beyond color)
- Support browser/OS-level text resizing up to 200% without breaking layout

---

## Web Font Loading

```css
@import url('https://fonts.googleapis.com/css2?family=Fraunces:wght@500;600&family=IBM+Plex+Sans:wght@400;600&family=IBM+Plex+Mono:wght@400&display=swap');

:root {
  --font-heading: 'Fraunces', Georgia, serif;
  --font-body: 'IBM Plex Sans', -apple-system, sans-serif;
  --font-mono: 'IBM Plex Mono', 'Courier New', monospace;
}
```
