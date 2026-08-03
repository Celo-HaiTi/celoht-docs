# CeloHT Iconography

## Icon Style

CeloHT icons are **line icons**, 2px stroke at 24×24px base grid, rounded caps and joins (matching the rounded, warm feel of Fraunces typography and the logo's rounded arrow). Icons are never filled solid except for status/alert icons, where fills improve at-a-glance recognition.

## Grid & Construction

- Base canvas: 24×24px
- Stroke weight: 2px at base size (scale proportionally — never keep stroke fixed at 2px when scaling the icon up or down)
- Corner radius: 2px on all rectangular elements
- Live area / padding: 2px minimum from canvas edge
- Optical sizing: at sizes below 20px, increase stroke weight slightly (2.5px) to preserve legibility

## Color Usage

- Default: CeloHT Navy `#1B2A4A` on light backgrounds, White `#FFFFFF` on dark backgrounds
- Accent icons (calls to action, highlights): CeloHT Gold `#F5A623`
- Status icons: use functional colors from [COLOR_SYSTEM.md](./COLOR_SYSTEM.md) — success, warning, error, info — always paired with a text label, never color alone

## Core Icon Set (by category)

**Education:** book-open, graduation-cap, lightbulb, chalkboard
**Agent Network:** handshake, map-pin, users, exchange-arrows (cash↔cUSD)
**Reforestation:** tree, leaf, seedling, globe
**Finance/Wallet:** wallet, qr-code, send-arrow, receive-arrow, shield-check (security)
**Governance/Community:** users-group, megaphone, vote-check, github-mark
**Navigation/UI:** chevron, menu, close, external-link, search, arrow-right

## Do

✅ Keep icons simple enough to be recognizable at 16px
✅ Pair every icon with a text label in primary UI (icons alone are not sufficient for accessibility)
✅ Use consistent stroke weight across an icon set shown together
✅ Provide `aria-label` or equivalent alt text for every icon used as a meaningful (non-decorative) element

## Don't

❌ Don't mix filled and outlined icon styles in the same interface
❌ Don't use photographic or 3D-rendered icons — they break the flat, accessible visual system
❌ Don't rely on icons alone to convey critical actions (e.g. "delete," "confirm transaction") without a text label

## Example: Agent Network Icon (cash ↔ cUSD)

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24" fill="none" stroke="#1B2A4A" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
  <path d="M4 8h12l-3-3M20 16H8l3 3"/>
</svg>
```

This "exchange arrows" icon represents the Agent Network's cash-in/cash-out function and should be used consistently anywhere this concept appears — website, dApp, educational materials.
