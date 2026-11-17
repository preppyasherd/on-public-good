# DESIGN.md — On Public Good (orange Carbon theme)

**Version:** 0.4 · 17 Nov 2026
**Scope:** How the site should look and feel, for both the scrollytelling story and the interactive map.

This file is based on IBM's open-source **Carbon Design System** (Apache 2.0) and **IBM Plex** type (SIL OFL), with IBM's blue swapped for orange. Borrow the design language only. Never use IBM's name, logo, 8-bar wordmark, product names or imagery.

It replaces §2 "Visual identity" of the build brief (serif type, vermilion `#FF3C02`, mock-up orange `#FFA04D`) for everything except the open question in §9.

---

## 1. Principles
- **Rectangles, not pills.** Every corner is 0px: buttons, inputs, tiles, tooltips, swatches and map controls.
- **Flat.** Separate areas with background layers, not borders or shadows. Only the RTO drawer may cast a shadow.
- **Two colour systems that never mix.**
  - *UI orange* marks only what can be clicked or what is selected.
  - *Data reds* (§2.5) mark only VERS urgency on the map and in charts.
  - Don't use either one for decoration, and don't borrow one for the other's job.
- **2x grid.** Everything snaps to the 8px spacing scale.
- **Type does the work.** Use large headings in a light weight, and small, dense labels.

## 2. Colour

### 2.1 Base palette (from reference)
| Token | Hex | Use |
|---|---|---|
| `ink` | `#1C1C1E` | Primary text, top header bar, selected states, tooltip background |
| `orange` | `#FF5A1F` | Interactive: primary buttons, focus ring, active nav/tab underline, active list item marker |
| `stone` | `#D8D4CC` | Subtle borders, dividers, disabled fills |
| `paper` | `#F0EEE9` | Layer 01: tiles, cards, input fields |

### 2.2 Derived tokens
| Token | Hex | Use |
|---|---|---|
| `background` | `#FFFFFF` | Page and panel background |
| `layer-hover` | `#E6E3DC` | Hover on any row, tile or control |
| `border-strong` | `#8A857C` | Input bottom border, select chevron (3.7:1 on white) |
| `text-secondary` | `#6B665E` | Helper text, labels, captions (5.7:1 on white, 4.9:1 on paper) |
| `orange-hover` | `#E84A12` | Primary button hover |
| `orange-active` | `#C23C0C` | Primary button pressed |
| `link` | `#B83A0B` | Text links (5.8:1 on white) |
| `shell-divider` | `#3A3A3D` | Dividers inside the header bar |
| `shell-hover` | `#2A2A2D` | Hover inside the header bar |

### 2.3 Contrast rules
- On an `orange` fill, put the label in **`ink`** (5.5:1). White on `#FF5A1F` is only 3.1:1, so never use white text there below 24px.
- For orange text, always use `link` `#B83A0B`, never `#FF5A1F`.
- Focus ring: 2px `orange`, inset (`outline-offset: -2px`). As a non-text element it only needs 3:1, which it passes.

### 2.4 Dark theme (Carbon g100 equivalent)
| Token | Hex |
|---|---|
| `background` | `#1C1C1E` |
| `layer` | `#2A2A2D` |
| `layer-hover` | `#343438` |
| `border-subtle` | `#3A3A3D` |
| `border-strong` | `#6E6A64` |
| `text` | `#F0EEE9` |
| `text-secondary` | `#A8A39A` |
| `orange` | `#FF7A45` |
| `link` | `#FF8A5C` |
| `shell` | `#141416` |

The theme follows the system setting by default. A header toggle overrides it and is remembered per browser.

### 2.5 Data palette — years till VERS-eligible
**Rule:** VERS-eligible year = lease start + 70. Years till = that year − 2026.
**Ramp:** red means sooner. The same fills are used in light and dark themes.

| Band | Eligible | Fill |
|---|---|---|
| 0–10 yrs | 2027–2036 (plus any block already past 70) | `#E1001C` |
| 10–20 yrs | 2037–2046 | `#E61518` |
| 20–30 yrs | 2047–2056 | `#FB6B4B` |
| 30–40 yrs | 2057–2066 | `#FCAF93` |
| 40–50 yrs | 2067–2076 | `#FEE1D3` |
| 50–60 yrs | 2077–2086 | `#FEE8DD` |
| 60+ yrs | 2087 on | `#FFEEE6` |
| Unknown (method A) / HDB owned, rental-only (method B) | — | `#FFF5F0` |

**Swatches:** 16px square, with a 1px border (`#D9C7CE` light, `#5A5458` dark) so the pale bands stay visible.

### 2.6 Map ground and strokes
| Element | Light | Dark |
|---|---|---|
| Land (planning areas) | `#DEDAD2` | `#232326` |
| Water / map background | `#F7F6F3` | `#141416` |
| Planning-area lines | `#FFFFFF`, 0.8px | `#3A3A3D`, 0.8px |
| SERS block outline | `#1C1C1E`, 2.2px | `#000000`, 2.2px |
| Selected block outline | `#1C1C1E`, 3px | `#000000`, 3px |

- **Land must stay darker than the palest band.** On near-white land the 40+ yrs bands disappear.
- **Block outlines scale with zoom.** Each block's outline uses its own fill colour, at 2px below z12.5, 1.2px to z14, 0.5px to z15.5, and none above that.

## 3. Typography
| Family | Weights | Use |
|---|---|---|
| IBM Plex Sans | 300, 400, 600 | UI and headings |
| IBM Plex Mono | 400 | Every figure, count, year and postcode |
| IBM Plex Serif | 300, 400 + italic | Optional, long-form story text only (see §9) |

Load all three from Google Fonts.

| Token | Size / line | Weight | Tracking | Use |
|---|---|---|---|---|
| `display-01` | 42 / 50 | 300 | 0 | Story chapter openers |
| `heading-04` | 28 / 36 | 300 | 0 | Page title |
| `heading-03` | 20 / 28 | 400 | 0 | Card / block titles |
| `heading-02` | 16 / 24 | 600 | 0 | Story section headings |
| `heading-01` | 14 / 18 | 600 | .16px | Panel section headings |
| `body-01` | 14 / 20 | 400 | .16px | Default UI text |
| `body-02` | 16 / 24 | 400 | 0 | Story paragraphs |
| `label-01` | 12 / 16 | 400 | .32px | Field labels, legend ranges, captions, hints |
| `code-01` | 12 / 16 | 400 (Mono) | .32px | Numbers in tables, legends and cards |

Use sentence case everywhere ("Years till VERS-eligible", not "YEARS TILL VERS-ELIGIBLE"). Keep acronyms in capitals (HDB, VERS, SERS, RTO).

## 4. Spacing & grid
- **Spacing scale:** `2 · 4 · 8 · 12 · 16 · 24 · 32 · 40 · 48 · 64 · 80 · 96`.
- **Grid:** 16 columns with 32px gutters (16px each side of a column), and 16px outer margins on mobile.
- **Breakpoints:** sm 320 · md 672 · lg 1056 · xlg 1312 · max 1584.

**Map layout:**
- **Desktop:** 48px header, then a 384px side panel on the left and the map filling the rest.
- **Below 760px:** the map comes first at 58vh, and the panel stacks underneath. Hide the header's nav links.
- **Panel spacing:** 32px between sections, 32px above and 40px below, 16px on each side.

## 5. Components

### Shell
**Header (UI shell)**
- Bar: 48px tall, `ink` background, `paper` text.
- Left side: site name ("On Public Good") in 14/600 with 16px left padding, then a 1px `shell-divider`, then the page name in 14/400.
- Nav links: 14/400, 16px padding on each side, `shell-hover` on hover. The current link gets a 2px `orange` bar along its bottom edge.
- Right side: a 48px square theme toggle.

### Controls
**Buttons** (48px tall, or 40px small; 0 radius; left-aligned label with 16px padding, or 64px right padding when there's a trailing icon)
- **Primary:** `orange` fill, `ink` text → `orange-hover` → `orange-active`.
- **Secondary:** `ink` fill, `paper` text → `#34343A` on hover.
- **Tertiary:** 1px `ink` border, `ink` text → on hover the fill turns `ink` and the text `paper`.
- **Ghost:** text only in `link` → `layer-hover` fill on hover.

**Content switcher (segmented)**
- Box: about 40px tall (taller when segments have two lines), with a 1px `ink` border round the whole control and between segments.
- Segments: 10px × 16px padding, left-aligned `body-01`. An optional second line sits beneath in `label-01` at 75% opacity.
- States: hover is `layer-hover`; selected is an `ink` fill with `background` text.

**Inputs / select**
- Field: 40px tall, `paper` fill, a 1px `border-strong` bottom border only, 0 radius.
- Select: drop the native styling and add a 16px chevron, 12px from the right edge.
- Label: above the field in `label-01` `text-secondary`, with an 8px gap.
- Hover: `layer-hover`. Focus: the standard ring.

**Checkbox**
- Size: 16px square, coloured with `accent-color: ink`.
- Label: `body-01`, 12px gap.

**Tabs**
- Tab: 48px tall, `body-01`, sitting on a 2px `stone` baseline.
- Active tab: 2px `orange` underline and 600 weight.

### Map panel
**Legend row**
- Grid: checkbox 16 · swatch 16 · label · block count · flat count, with 12px gaps and 8px padding.
- Rows are divided by 1px `stone`, and the whole row highlights `layer-hover` on hover.
- Text: the band name is 600, the year range `label-01` `text-secondary`, and the counts `code-01` aligned right (flats in `text-secondary`).
- Under the legend, a "Showing" total row in `code-01`.

**Town ranking row**
- Grid: name 120px · bar · percentage 44px, 6px × 8px padding.
- Bar: 8px tall on a `paper` track, split into band colours, with square ends.
- States: hover is `layer-hover`. The active filter gets a `paper` fill and a 3px `orange` inset bar on the left.

**Tile / selected-block card**
- Card: `paper` fill, 16px padding, no border.
- Top edge: a 3px bar in the block's band colour.
- Title: `heading-03`. Sub-line: `label-01` `text-secondary`.
- Progress bar: 4px tall on a `stone` track, filled in the band colour, showing lease age ÷ 70.
- Details list: labels in `text-secondary`, values in `code-01`, in this order:
  1. Years till VERS-eligible
  2. VERS-eligible from
  3. Lease years remaining
  4. Lease start used
  5. Year completed
  6. Lease start (resale)
  7. Flats · storeys
- SERS tag: `ink` fill, `background` text, `code-01`, 4px × 8px padding.

**Empty state**
- Same box as the card, showing a single line of `text-secondary` ("Click a block on the map.").

### Map overlays
**Tooltip**
- Box: `#1C1C1E` fill with `#F0EEE9` text in both themes, `label-01`, 8px × 12px padding, 0 radius, no shadow.
- Format: "Blk 203 Ave 3 · 46 yrs till VERS-eligible (2072)". If the block is already past 70: "VERS-eligible now".

**Map controls**
- Zoom buttons: 40px square, `background` fill, 1px `stone` border, stacked with no gap, 16px in from the map edge.
- Attribution: `label-01` on a `background` strip, in the bottom-right corner.

### Story
**Progress bar / scroll progress**
- 4px tall `stone` track with an `orange` fill.

## 6. Motion
- **Easing:** Carbon productive, `cubic-bezier(0.2, 0, 0.38, 0.9)`.
- **Durations:** 70ms for hovers and toggles, 110ms for nav and header states, 240ms for map zoom, drawers and panels.
- **Reduced motion:** when `prefers-reduced-motion` is set, turn off all transitions.

## 7. Writing on the page
- **Name the measure:** "Years till VERS-eligible". Define it once in the intro, as lease start + 70.
- **Always include the caveat** that VERS will be offered only to selected precincts and its terms are still being worked out, so a colour never means a block will be chosen or demolished.
- **Figures:** British spelling, `en-GB` number formatting (10,763), and en dashes for ranges (2027–2036).

## 8. Do / Don't
- ✅ Use a light 300 weight for big headings, and 600 only for small headings and band names.
- ✅ Set every figure in Plex Mono with tabular numbers.
- ✅ Square everything, swatches included.
- ✅ Keep land darker than the palest data band.
- ❌ No rounded corners, gradients, glow or decorative shadows.
- ❌ No white text on orange.
- ❌ No UI orange on the map, and no data reds in the UI.
- ❌ No IBM marks, product names or photography.

## 9. Open questions
1. **Story typography.** Should long-form story text stay in Plex Sans, or switch to Plex Serif to keep the deck's editorial feel?
2. **The two top reds.** `#E1001C` and `#E61518` are almost impossible to tell apart (contrast about 1.05:1), so 0–10 and 10–20 yrs read as one band on the map. Options:
   - Keep them as they are, and let tooltips and the legend separate them.
   - Darken 0–10 yrs (for example to `#A50014`).
   - Add a pattern or outline to 0–10 yrs.
3. **Already-eligible blocks.** Blocks past 70 currently count in 0–10 yrs. Should they get their own "Eligible now" band?
4. **Dark-mode emphasis.** On dark land the pale bands are the brightest marks, which reverses the emphasis. Should dark mode get its own ramp, or should the map always use the light ground?
