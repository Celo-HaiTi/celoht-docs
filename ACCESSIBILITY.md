# Accessibility

## Standard

CeloHT targets **WCAG 2.2 Level AA** at minimum across the website and dApp, given the target audience frequently includes users with limited digital literacy, older devices, and varying ability levels — accessibility here is not a compliance checkbox, it's core to the inclusion mission.

## Visual Accessibility

- Minimum contrast ratios per the Brand repository's `COLOR_SYSTEM.md` — all text/background pairings verified AA or better
- Text resizable up to 200% without breaking layout
- No information conveyed by color alone — always paired with text or icon (see the Brand repository's `ICONOGRAPHY.md`)
- Color-blind-safe palette, verified against protanopia/deuteranopia simulation

## Screen Reader Support

- Semantic HTML throughout the dApp and website
- All meaningful icons carry `aria-label` or equivalent alt text (see the Brand repository's `ICONOGRAPHY.md#do`)
- Transaction confirmation screens are structured for clear, linear screen-reader navigation — critical given the financial stakes of these screens

## Keyboard Navigation

Full keyboard operability for all interactive elements, visible focus states, and logical tab order — particularly important for the Agent Dashboard (see [DAPP.md](./DAPP.md#dashboards)), which agents may use for extended periods.

## Cognitive Accessibility

- Plain language throughout (see the Brand repository's `VOICE_AND_TONE.md`)
- Consistent, predictable UI patterns across the dApp
- Critical actions (sending funds, confirming agent transactions) use clear, unambiguous confirmation steps — never relying on subtle UI cues alone

## Low-Bandwidth & Device Accessibility

- Offline-first design for education content and QR-based receiving (see [DAPP.md](./DAPP.md#offline-first-concepts))
- Lightweight page weight, tested against low-end Android devices and constrained data plans
- Lightweight wallet flows (Valora) that keep device and data requirements low for lower-end Android devices

## Testing

- Automated accessibility checks (axe-core) run in CI per [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#testing)
- Manual screen-reader testing before major releases
- Periodic testing with actual community members representing the target user base, not only internal QA

## Accessibility Issue Reporting

Report accessibility barriers via GitHub issue (tag `accessibility`) or contact@celoht.com. These are treated with the same priority as functional bugs, not as lower-priority enhancement requests.

## References

- Brand repository: `COLOR_SYSTEM.md`, `TYPOGRAPHY.md`, `ICONOGRAPHY.md`
- [DAPP.md](./DAPP.md#accessibility)
- [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md#testing)
