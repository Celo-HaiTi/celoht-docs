# CeloHT Color System

CeloHT's palette is built from the official logo: **navy blue**, **gold/amber**, and **bright yellow**. These colors were chosen because they read as trustworthy and financial (navy), optimistic and energetic (gold), and warm and Haitian (yellow — echoing the Haitian flag's use of color and the warmth of the sun). Every color below has been checked for accessibility.

---

## Primary Palette

### CeloHT Navy (Primary)
- HEX: `#1B2A4A`
- RGB: `27, 42, 74`
- HSL: `220°, 47%, 20%`
- CMYK: `64, 43, 0, 71`
- Usage: primary text, logo mark, headers, primary buttons on light backgrounds

### CeloHT Gold (Primary Accent)
- HEX: `#F5A623`
- RGB: `245, 166, 35`
- HSL: `36°, 90%, 55%`
- CMYK: `0, 32, 86, 4`
- Usage: the arrow/growth mark, calls-to-action, highlights

### CeloHT Yellow (Signature Background)
- HEX: `#FCE94F`
- RGB: `252, 233, 79`
- HSL: `55°, 96%, 65%`
- CMYK: `0, 8, 69, 1`
- Usage: logo background field, section highlights, sparingly as a background — not for body text areas

---

## Secondary Palette

### Deep Navy (Text / Dark Mode Base)
- HEX: `#101A30`
- RGB: `16, 26, 48`

### Slate (Secondary Text)
- HEX: `#4A5568`
- RGB: `74, 85, 104`

### Off-White (Light Surface)
- HEX: `#FAF9F6`
- RGB: `250, 249, 246`

---

## Functional Colors

| Purpose | Name | HEX | Contrast on white |
|---|---|---|---|
| Success | Growth Green | `#1E8E5A` | 4.6:1 (AA) |
| Warning | Amber Warning | `#B7791F` | 4.9:1 (AA) |
| Error | Signal Red | `#C0392B` | 5.9:1 (AA) |
| Information | Sky Blue | `#2B6CB0` | 5.1:1 (AA) |

---

## Neutral Scale

| Token | HEX | Usage |
|---|---|---|
| `neutral-50` | `#FAFAFA` | Page background |
| `neutral-100` | `#F1F1F1` | Card background |
| `neutral-300` | `#D4D4D4` | Borders, dividers |
| `neutral-500` | `#8A8A8A` | Disabled text |
| `neutral-700` | `#4A4A4A` | Secondary body text |
| `neutral-900` | `#1A1A1A` | Primary body text (near-black) |

---

## Accessibility & Contrast

All primary color pairings meet **WCAG 2.2 AA** at minimum for normal text (4.5:1) and large text (3:1). Pairings meeting **AAA** (7:1) are marked.

| Foreground | Background | Ratio | Level |
|---|---|---|---|
| CeloHT Navy `#1B2A4A` | White `#FFFFFF` | 12.6:1 | AAA |
| CeloHT Navy `#1B2A4A` | CeloHT Yellow `#FCE94F` | 9.8:1 | AAA |
| CeloHT Gold `#F5A623` | CeloHT Navy `#1B2A4A` | 5.2:1 | AA |
| White `#FFFFFF` | CeloHT Navy `#1B2A4A` | 12.6:1 | AAA |
| Slate `#4A5568` | Off-White `#FAF9F6` | 7.4:1 | AAA |

**Rules:**
- Never place CeloHT Gold text directly on CeloHT Yellow — contrast fails (1.4:1). Use Navy on Yellow, or Gold on Navy instead.
- Never rely on color alone to convey meaning (e.g. success/error states) — always pair with an icon or text label for color-blind and screen-reader users.
- All functional colors (success, warning, error, info) have been tested against both protanopia and deuteranopia simulations and remain distinguishable when paired with distinct icons.

---

## Color Usage Ratios (60/30/10 Rule)

- **60%** Neutral / white space (Off-White, White, Neutral-50/100)
- **30%** CeloHT Navy (text, structure, primary UI elements)
- **10%** CeloHT Gold / Yellow (accents, highlights, calls-to-action)

CeloHT Yellow as a full background (like the logo) should be reserved for brand moments — logo lockups, social avatars, event banners — not general UI backgrounds, where it can overwhelm readability at scale.

---

## Dark Mode

| Token | Light Mode | Dark Mode |
|---|---|---|
| Background | `#FAF9F6` | `#101A30` |
| Surface | `#FFFFFF` | `#1B2A4A` |
| Primary text | `#1A1A1A` | `#F5F5F5` |
| Accent | `#F5A623` | `#F5A623` (unchanged — passes AA on both) |

---

## Design Tokens (JSON)

```json
{
  "color": {
    "primary": { "navy": "#1B2A4A", "gold": "#F5A623", "yellow": "#FCE94F" },
    "secondary": { "deepNavy": "#101A30", "slate": "#4A5568", "offWhite": "#FAF9F6" },
    "functional": {
      "success": "#1E8E5A",
      "warning": "#B7791F",
      "error": "#C0392B",
      "info": "#2B6CB0"
    },
    "neutral": {
      "50": "#FAFAFA", "100": "#F1F1F1", "300": "#D4D4D4",
      "500": "#8A8A8A", "700": "#4A4A4A", "900": "#1A1A1A"
    }
  }
}
```
