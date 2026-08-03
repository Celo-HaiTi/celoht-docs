# Design System

> Visual identity (logo, color, typography) is owned by the Brand repository — see `COLOR_SYSTEM.md`, `TYPOGRAPHY.md`, `ICONOGRAPHY.md` at [github.com/Celo-HT/Brand](https://github.com/Celo-HT/Brand). This document covers the **application-level design system** — how those tokens are implemented in code across the dApp and website.

## Design Token Implementation

Brand-defined colors and typography (see the Brand repository) are implemented as a shared Tailwind CSS configuration used identically across the Website and dApp repositories, ensuring visual consistency without duplicated design decisions:

```javascript
// tailwind.config.js (shared base, extended per-repo as needed)
module.exports = {
  theme: {
    extend: {
      colors: {
        navy: '#1B2A4A',
        gold: '#F5A623',
        yellow: '#FCE94F',
        // Functional colors — see Brand repository COLOR_SYSTEM.md
        success: '#1E8E5A',
        warning: '#B7791F',
        error: '#C0392B',
        info: '#2B6CB0',
      },
      fontFamily: {
        heading: ['Fraunces', 'Georgia', 'serif'],
        body: ['IBM Plex Sans', '-apple-system', 'sans-serif'],
        mono: ['IBM Plex Mono', 'monospace'],
      },
    },
  },
};
```

## Component Library

CeloHT's application-level components (buttons, cards, form inputs, transaction confirmation modals) follow the interaction patterns documented in [DAPP.md](./DAPP.md) and the accessibility standard in [ACCESSIBILITY.md](./ACCESSIBILITY.md). A shared component package is planned per [ROADMAP.md](./ROADMAP.md) to avoid divergence between the Website and dApp implementations.

## Spacing & Layout Grid

- Base spacing unit: 4px, scaled in standard Tailwind increments (4, 8, 12, 16, 24, 32, 48, 64px)
- Max content width: 1200px for marketing/education pages, full-width mobile-first layout for the dApp

## Icon Implementation

Icons follow the Brand repository's `ICONOGRAPHY.md` specification (24×24 grid, 2px stroke), implemented as an SVG component library shared across repositories.

## Motion Principles

- Transitions: 150–250ms, ease-in-out, for standard UI state changes
- No motion on critical confirmation screens (transaction approval) that could obscure or delay a user's ability to read exact amounts — clarity over polish in financially consequential moments
- Respect `prefers-reduced-motion` system setting throughout

## References

- Brand repository: `COLOR_SYSTEM.md`, `TYPOGRAPHY.md`, `ICONOGRAPHY.md`
- [DAPP.md](./DAPP.md)
- [ACCESSIBILITY.md](./ACCESSIBILITY.md)
