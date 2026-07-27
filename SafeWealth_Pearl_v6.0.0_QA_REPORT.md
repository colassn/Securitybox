# SafeWealth Pearl v6.0.0 — QA Report

## Build checks

- HTML size: approximately 1.08 MB.
- Duplicate HTML IDs: none.
- JavaScript syntax: all five script blocks passed `node --check`.
- Existing Firebase project configuration preserved: `securitybox-f0419`.
- Existing Google Authentication and Firestore data paths preserved.
- Bootstrap icon font remains embedded in the single HTML file.

## Responsive browser checks

Tested at:

- 390 × 844 — phone
- 820 × 1180 — tablet
- 1366 × 900 — desktop

Results:

- Horizontal overflow: 0 px at every tested viewport.
- Only the active primary screen is displayed.
- Home control centre, vault goals and smart recommendations render correctly.
- 128 of 130 icon elements displayed a valid embedded glyph in the tested state; the remaining two were hidden-state icons.
- Command centre opens, searches and filters commands.
- Deposit preset sets all six note denominations to one.
- Smart transfer “approximately half” populated seven physical pieces in the seeded demo inventory.
- Accent selector changed the design system to Pearl Silver.
- Insight modules rendered 28 heat-map cells, five denomination concentration rows and four data-health indicators.
- Existing deposit denomination scroll-preservation logic remains present. In the phone test, the denomination grid fit the viewport and therefore did not require horizontal scrolling.

## Test-environment note

The sandboxed `page.set_content` browser used for QA denies direct `localStorage` access before it is mocked. That isolated sandbox warning is not produced when the HTML is opened from a normal browser file origin or deployed HTTPS origin. Core UI testing was repeated after injecting a no-op storage mock and recalculating the seeded demo data.

## Final result

**Passed for handoff.** Firebase login and live Firestore permissions still depend on the Firebase Console Authentication settings, authorised domains and Security Rules configured for the project.
