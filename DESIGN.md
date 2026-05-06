---
version: alpha
name: Cartograph
description: A flat, technical design system for the GeoJSON Visual Editor. Two themes — Cartograph Night (dark, default) and Cartograph Day (light) — share tokens, type scale, and component rules. The dark theme is encoded in this YAML; the light theme is specified in the Colors section as a parallel palette the implementation applies when the IDE is in a light theme kind.

colors:
  # ===== Cartograph Night (default) =====
  # Base values are perceptually-uniform OKLCH (hue ~ 220° for cool surface neutrals,
  # ~ 200° for the teal accent), resolved to sRGB hex. Derived values use color-mix()
  # so they keep contrast when VS Code theme variables override the base palette.
  bg:               "#11191B"   # editor canvas — deep cool charcoal, faintly blue
  panel:            "#192225"   # sidebar / Inspector surface — one step lighter than bg
  panel-elevated:   "#2A383D"   # sidebar header strip + collapsed section titles — one step above panel; gives structural strips a real surface
  elev:             "#242D30"   # input fields, buttons, inset surfaces
  line:             "#415055"   # divider hairline at full opacity (use 60% alpha in CSS for actual rule)
  line-soft:        "#303D41"   # secondary/structural divider, less prominent than line
  text:             "#E0EAED"   # primary body text — passes 14.56:1 on bg
  text-mute:        "#93A1A6"   # secondary/labels — passes 6.08:1 on panel
  text-faint:       "#5D6C71"   # tertiary/hints/disabled — passes 2.97:1 on panel (large/icon only)
  accent:           "#4AC9D0"   # the single brand accent — bright teal, hydrography reference
  accent-deep:      "#007077"   # accent at lower lightness, for hover/pressed states; preserves AA with text
  accent-soft:      "#004245"   # tinted background for active rows / pressed surfaces (resolved, no alpha)
  success:          "#61D19A"
  warn:             "#F2B74A"
  danger:           "#F97770"
  map-bg:           "#111D20"   # map canvas — slightly more saturated than bg, suggests sea/sky
  readout:          "#CAD6D9"   # night resolved default for neutral inline data values; CSS derives per theme
  control-thumb:    "#515A5D"   # night resolved default for toggle knob fill; CSS derives per theme
  control-grip:     "#A2B0B4"   # night resolved default for slider grip; CSS derives per theme

typography:
  # Display: Hanken Grotesk — humanist sans, refined, deliberately not on the reflex-font list.
  # Mono:    Commit Mono       — open-source distinctive technical face for coords, hex, JSON.
  # Both load from Google Fonts. System fallbacks listed in fontFamily.

  panel-title:
    fontFamily: "Hanken Grotesk, system-ui, sans-serif"
    fontSize: 11px
    fontWeight: 500
    letterSpacing: 0.10em
    lineHeight: 1.2
    fontFeature: "'cv11'"        # disambiguating l/I — helpful in technical UI

  section-title:
    fontFamily: "Hanken Grotesk, system-ui, sans-serif"
    fontSize: 11px
    fontWeight: 500
    letterSpacing: 0.08em
    lineHeight: 1.3

  body:
    fontFamily: "Hanken Grotesk, system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 400
    lineHeight: 1.45

  label:
    fontFamily: "Hanken Grotesk, system-ui, sans-serif"
    fontSize: 11px
    fontWeight: 400
    lineHeight: 1.4

  button:
    fontFamily: "Hanken Grotesk, system-ui, sans-serif"
    fontSize: 11px
    fontWeight: 500
    lineHeight: 1.0

  readout-mono:
    fontFamily: "Commit Mono, ui-monospace, 'SF Mono', Consolas, monospace"
    fontSize: 11px
    fontWeight: 400
    letterSpacing: 0.02em
    lineHeight: 1.3

  readout-mono-sm:
    fontFamily: "Commit Mono, ui-monospace, 'SF Mono', Consolas, monospace"
    fontSize: 10px
    fontWeight: 400
    letterSpacing: 0.04em
    lineHeight: 1.2

  graticule-label:
    fontFamily: "Commit Mono, ui-monospace, monospace"
    fontSize: 9px
    fontWeight: 400
    letterSpacing: 0.04em

  json-editor:
    fontFamily: "Commit Mono, ui-monospace, monospace"
    fontSize: 11px
    fontWeight: 400
    lineHeight: 1.55

rounded:
  none: 0px
  xs: 2px      # chips, tiny indicators
  sm: 3px      # range thumbs, toggles, basemap-card swatches
  md: 4px      # the default — buttons, inputs, basemap cards, toolbar buttons
  lg: 6px      # outermost panel containers (toolbar group, JSON editor frame)

spacing:
  none: 0px
  xs: 4px      # chip padding, icon gaps inside buttons
  sm: 6px      # gap between adjacent controls in a row
  md: 8px      # default gap between sibling fields, padding inside inputs
  lg: 12px     # padding inside section bodies
  xl: 14px     # horizontal padding of the sidebar
  2xl: 18px    # vertical separation between major panel groups
  3xl: 24px

components:
  # ----- Sidebar layout -----
  sidebar:
    backgroundColor: "{colors.panel}"
    width: 320px

  sidebar-header:
    backgroundColor: "{colors.panel-elevated}"
    textColor: "{colors.text}"
    typography: "{typography.panel-title}"
    padding: 12px 14px

  section:
    backgroundColor: "{colors.panel}"
    padding: 10px 14px

  section-title:
    backgroundColor: "{colors.panel-elevated}"
    textColor: "{colors.text-mute}"
    typography: "{typography.section-title}"
    padding: 8px 14px

  # ----- Buttons -----
  button-primary:
    backgroundColor: "{colors.accent}"
    textColor: "{colors.bg}"
    rounded: "{rounded.md}"
    padding: 6px 12px
    typography: "{typography.button}"

  button-primary-hover:
    backgroundColor: "{colors.accent-deep}"
    textColor: "{colors.text}"

  button-secondary:
    backgroundColor: "{colors.elev}"
    textColor: "{colors.text}"
    rounded: "{rounded.md}"
    padding: 6px 12px
    typography: "{typography.button}"

  button-secondary-hover:
    backgroundColor: "{colors.elev}"
    textColor: "{colors.accent}"

  button-destructive:
    backgroundColor: "{colors.elev}"
    textColor: "{colors.danger}"
    rounded: "{rounded.md}"
    padding: 6px 12px
    typography: "{typography.button}"

  button-icon:
    backgroundColor: "{colors.panel}"
    textColor: "{colors.text-mute}"
    rounded: "{rounded.sm}"
    size: 26px

  button-icon-active:
    backgroundColor: "{colors.accent-soft}"
    textColor: "{colors.accent}"

  # ----- Inputs -----
  input-text:
    backgroundColor: "{colors.elev}"
    textColor: "{colors.text}"
    rounded: "{rounded.md}"
    padding: 6px 8px
    height: 28px
    typography: "{typography.readout-mono}"

  input-color:
    backgroundColor: "{colors.elev}"
    textColor: "{colors.text}"
    rounded: "{rounded.md}"
    padding: 4px 8px
    height: 26px

  input-range-track:
    backgroundColor: "{colors.line}"
    height: 2px
    rounded: "{rounded.xs}"

  input-range-fill:
    backgroundColor: "{colors.accent}"
    height: 2px
    rounded: "{rounded.xs}"

  input-range-thumb:
    backgroundColor: "{colors.control-grip}"
    height: 14px
    width: 4px
    rounded: "{rounded.xs}"

  toggle-off:
    backgroundColor: "{colors.line}"
    width: 26px
    height: 14px

  toggle-on:
    backgroundColor: "{colors.accent}"
    width: 26px
    height: 14px

  toggle-knob:
    backgroundColor: "{colors.control-thumb}"
    width: 11px
    height: 11px
    rounded: "{rounded.sm}"

  # ----- Basemap selector -----
  basemap-card:
    backgroundColor: "{colors.elev}"
    textColor: "{colors.text-mute}"
    rounded: "{rounded.md}"
    padding: 6px

  basemap-card-active:
    backgroundColor: "{colors.accent-soft}"
    textColor: "{colors.accent}"

  # ----- Map overlays -----
  map-toolbar:
    backgroundColor: "{colors.panel}"
    rounded: "{rounded.md}"
    padding: 4px

  map-pill:
    backgroundColor: "{colors.panel}"
    textColor: "{colors.text}"
    rounded: "{rounded.md}"
    padding: 4px 8px
    typography: "{typography.readout-mono-sm}"

  map-pill-accent:
    backgroundColor: "{colors.panel}"
    textColor: "{colors.accent}"

  # ----- JSON editor -----
  json-editor:
    backgroundColor: "{colors.bg}"
    textColor: "{colors.text}"
    rounded: "{rounded.md}"
    padding: 10px 12px
    typography: "{typography.json-editor}"

  json-editor-gutter:
    backgroundColor: "{colors.bg}"
    textColor: "{colors.text-faint}"
    typography: "{typography.json-editor}"
---

## Overview

Cartograph is a flat, technical design system for the GeoJSON Visual Editor — a custom editor that lives inside VS Code and turns `.geojson` files into a live map preview alongside a JSON document editor. The system commits to three ideas:

1. **Graticule.** A faint coordinate grid runs across the map canvas with monospaced corner labels. The same hairline rhythm reappears as 0.5 px section dividers in the sidebar, so the panel and the map share one visual logic.
2. **Layered flatness.** Depth is implied by hairline borders and tonal panel shifts — never by drop shadows, glow, blur, or gradients. The visual language echoes how vector tiles compose on a flat plane.
3. **Editor sympathy.** Numeric values (coordinates, hex codes, line widths, opacity percentages, JSON) are monospaced. Labels are sans. This mirrors how VS Code already separates code from chrome.

Two themes ship: **Cartograph Night** (dark, default — encoded in the YAML above) and **Cartograph Day** (light — specified in the Colors section). Both share every token name, type scale, spacing rule, and component contract; only the colour layer changes between them. The implementation reads VS Code's theme kind and applies the appropriate palette without an in-app toggle.

## Colors

The palette is built in OKLCH for perceptual uniformity, then resolved to sRGB hex for the YAML tokens. Every neutral is tinted toward the brand hue (cool blue at hue 220°) at very low chroma (0.012–0.022), so the "greys" are not actually grey — they carry a faint, intentional cool cast that creates subconscious cohesion with the teal accent. Pure black and pure white are not used.

The accent is **a single hue** — a deep oxidised teal at hue 200°, brighter in dark mode (`#4AC9D0`, L 0.77) and deeper in light mode (`#005D62`, L 0.43). The accent does almost all the semantic work in the interface: selection, active state, primary action, focus ring, slider fills. It is rare by design — roughly 60% of pixels are surface, 30% are borders and muted text, 10% are accent. The accent earns its weight by being scarce. Passive numeric values are **not** accent-coloured; they use the neutral `readout` token so hex codes, widths, and percentages do not look selected or actionable.

A four-tier surface hierarchy carries the structural language of the sidebar. From least to most prominent: `bg` (editor canvas) → `panel` (Inspector body and field rows) → `panel-elevated` (header strip and section title strips — one step *up* in Night, one step *down* in Day, since depth in light mode goes into the page) → `elev` (input fields, button faces — the "editable" surfaces). Headers and section titles read as visibly distinct strips without a border, while inputs stay clearly differentiated from chrome.

Three derived neutral tokens sit on top of the base palette:

- `readout` mixes `text` and `text-mute` for inline numeric values such as `#2563EB`, `4.0`, and `80%`.
- `control-thumb` mixes `elev` and `text` for toggle knobs, so custom VS Code themes cannot collapse the knob into a near-black or near-white toggle background.
- `control-grip` mixes `text-mute` and `text` for the slider's vertical grip. It is intentionally stronger than `text-mute` alone because the grip is small (4 × 14 px) and must read against both `accent` (left of grip) and `line` (right of grip) without a border outline.

Semantic colours (`success`, `warn`, `danger`) are reserved for system messages and validation. They are **not** decorative and must not be used to colour-code categories of features in the user's data — that is the user's job, not the chrome's.

### Cartograph Night (default — encoded in the YAML)

| Token | OKLCH | Hex | Use |
| --- | --- | --- | --- |
| `bg` | `oklch(20.5% 0.012 220)` | `#11191B` | Editor canvas background |
| `panel` | `oklch(24.5% 0.014 220)` | `#192225` | Sidebar surface, one step up from `bg` |
| `panel-elevated` | `oklch(33% 0.020 220)` | `#2A383D` | Header strip + section-title strips — clearly above `panel`, distinct from `elev` |
| `elev` | `oklch(29% 0.014 220)` | `#242D30` | Input fields, buttons, inset surfaces |
| `line` | `oklch(42% 0.020 220)` | `#415055` | Divider hairline (apply at 60% alpha in CSS) |
| `line-soft` | `oklch(35% 0.018 220)` | `#303D41` | Secondary structural divider |
| `text` | `oklch(93% 0.012 220)` | `#E0EAED` | Primary text — 14.56:1 on `bg`, 9.91:1 on `panel-elevated` |
| `text-mute` | `oklch(70% 0.018 220)` | `#93A1A6` | Labels, section names — 6.08:1 on `panel`, 4.56:1 on `panel-elevated` |
| `text-faint` | `oklch(52% 0.020 220)` | `#5D6C71` | Hints, large/icon only — 2.97:1 on `panel` |
| `accent` | `oklch(77% 0.110 200)` | `#4AC9D0` | Brand accent — 8.96:1 on `bg` |
| `accent-deep` | `oklch(48.5% 0.110 200)` | `#007077` | Accent hover/pressed state; preserves AA with primary hover text |
| `accent-soft` | `oklch(34.5% 0.060 200)` | `#004245` | Active-row tint, pressed surfaces |
| `success` | `oklch(78% 0.130 160)` | `#61D19A` | 8.56:1 on `panel` |
| `warn` | `oklch(81.5% 0.140 80)` | `#F2B74A` | 8.98:1 on `panel` |
| `danger` | `oklch(72% 0.160 25)` | `#F97770` | 6.09:1 on `panel` |
| `map-bg` | `oklch(22% 0.018 220)` | `#111D20` | Map canvas background |
| `readout` | derived | `#CAD6D9` | Inline hex/value readouts, neutral data; CSS derives per theme |
| `control-thumb` | derived | `#515A5D` | Toggle knob fill; CSS derives per theme |
| `control-grip` | derived | `#A2B0B4` | Slider vertical grip; CSS derives per theme |

### Cartograph Day (apply when `data-vscode-theme-kind="vscode-light"` or `"vscode-high-contrast-light"`)

The implementation should generate a parallel CSS variable scope (`[data-vscode-theme-kind^="vscode-light"]`) that overrides the same token names with these values. **All component definitions in the YAML continue to apply unchanged** — only the colour resolution changes.

| Token | OKLCH | Hex | Use |
| --- | --- | --- | --- |
| `bg` | `oklch(96.5% 0.005 220)` | `#F0F4F6` | Editor canvas — cool slate grey |
| `panel` | `oklch(93.5% 0.006 220)` | `#E5EAEC` | Sidebar — one tonal step down from `bg`, same hue |
| `panel-elevated` | `oklch(89.5% 0.010 220)` | `#D6DEE1` | Header strip + section-title strips — one step *down* from `panel` (depth in light mode goes into the page) |
| `elev` | `oklch(100% 0 0)` | `#FFFFFF` | Input fields — pure white reads as "blank form" |
| `line` | `oklch(77% 0.018 220)` | `#A8B7BC` | Divider hairline (apply at 80% alpha in CSS) |
| `line-soft` | `oklch(86% 0.012 220)` | `#C9D3D6` | Secondary structural divider |
| `text` | `oklch(22% 0.020 220)` | `#101D21` | Primary text — 15.56:1 on `bg`, 12.62:1 on `panel-elevated` |
| `text-mute` | `oklch(46% 0.022 220)` | `#4B5B61` | Labels — 5.83:1 on `panel`, 5.19:1 on `panel-elevated` |
| `text-faint` | `oklch(59.5% 0.022 220)` | `#718288` | Hints — 3.30:1 on `panel` (large/icon only) |
| `accent` | `oklch(43% 0.085 200)` | `#005D62` | Brand accent — 6.92:1 on `bg`, 6.31:1 on `panel` |
| `accent-deep` | `oklch(33% 0.080 200)` | `#004145` | Accent hover/pressed |
| `accent-soft` | `oklch(93% 0.025 200)` | `#D6EDEE` | Active-row tint — pale teal wash, accent reads 6.28:1 on it |
| `success` | `oklch(46% 0.110 160)` | `#006A42` | 5.51:1 on `panel` |
| `warn` | `oklch(53% 0.135 60)` | `#A25400` | 4.55:1 on `panel` |
| `danger` | `oklch(50% 0.180 25)` | `#B32228` | 5.45:1 on `panel` |
| `map-bg` | `oklch(91% 0.014 220)` | `#D8E4E8` | Map canvas — one step down from `panel`, same hue |
| `readout` | derived | `color-mix(text 72%, text-mute)` | Inline hex/value readouts, neutral data |
| `control-thumb` | derived | `color-mix(elev 76%, text)` | Toggle knob fill |
| `control-grip` | derived | `color-mix(text-mute 80%, text)` | Slider vertical grip — borderless, reads against accent fill and line track |

### Why these values

The Cartograph Day surface (`#F0F4F6`) is a cool slate grey at hue 220° — the same hue as the Night palette's neutrals, just at the opposite end of the lightness scale. The effect is IDE-native: the editor sits invisibly next to VS Code's built-in light themes rather than declaring itself with a stationery cream or a pigmented green. The chrome stays out of the user's way, and the teal accent does all the brand work.

Pure white (`#FFFFFF`) is reserved for input fields. On a cool-grey surface, white reads cleanly as "blank form / editable value" — the semantic distinction is sharper than it would be on a warm cream. The sidebar `panel` is a single tonal step (3 percentage points of OKLCH lightness) below `bg`, same hue, same chroma. That subtle step is enough to separate the Inspector from the editor canvas without a border.

The accent hue (200°) is the same in both themes — only the lightness inverts. That preserves brand identity across the theme switch: a user moving between dark and light modes sees the same teal logic, just resolved for the opposite contrast direction.

## Typography

Two families. No third.

- **Hanken Grotesk** (Google Fonts) — humanist sans for all sentence-case UI text. Chosen deliberately because it is *not* on the reflex-font reject list (Inter, IBM Plex, Space Grotesk, DM Sans, Plus Jakarta Sans, Geist, Mona Sans). Hanken has the warmth and slight quirk of a humanist face without sliding into "techy" territory; its `cv11` OpenType feature disambiguates `l` and `I`, which matters in a UI that displays property keys.
- **Commit Mono** (Google Fonts) — open-source monospace. Used wherever the value on screen is *data*: coordinates, hex codes, range readouts (line width, opacity, stroke), feature counts, file sizes, JSON, and graticule labels. Distinctive without being trendy. JetBrains Mono and Fira Code are not used.

The split is rigid: **labels are sans, numbers are mono.** A row reading "Line width 2.5" has the label in Hanken Grotesk and the value `2.5` in Commit Mono. Passive inline values use `readout`, not `accent`; the accent belongs to active state, focus, selection, and slider fill. This is not decoration — it tells the user at a glance what is editable data, what is chrome, and what is currently active.

The scale is intentionally tight. Sidebar UI lives in a 280–320 px column, so type runs from 9 px (graticule labels) up to 12 px (body), with 11 px doing most of the work. Body line-height is 1.45; readout monos are tighter at 1.2–1.3 because the values rarely wrap.

Section titles use `letter-spacing: 0.08em` and `text-transform: uppercase` to read as map-key headings rather than document headings. This is the **only** place uppercase appears in the UI; do not extend the pattern to button labels or body copy.

## Layout

The editor is a two-pane layout: a flexible map canvas on the left, a fixed 320 px Inspector sidebar on the right. The map fills available space; the sidebar does not resize.

Spatial rhythm follows a 2/4/6/8/12/14/18/24 px scale (semantic tokens `xs` through `3xl`). The 4 px scale matters because at small UI sizes, the difference between 8 px and 12 px is the difference between cramped and breathable; an 8 px-only scale is too coarse for this density.

Sections inside the sidebar are separated by 0.5 px rules in `line` colour (applied at 60% alpha in dark, 80% alpha in light — the rules need to read as hairlines, not borders). Each section has 10 px vertical and 14 px horizontal padding. The 14 px horizontal value is shared with the sidebar header, so all rows align to a single left edge throughout the panel.

Inside a section, fields are stacked with 7 px row gaps. Multi-control rows (label + range slider + readout) align baseline-to-baseline so the readout digits sit on the same horizontal line as the label.

Map overlays (toolbar, scale bar, coordinate strip, metric pills) sit inside the map area at 10–12 px insets from the map edge. They use the same `panel` background as the sidebar, applied at 88% alpha with a 6 px backdrop blur, so they read as floating instruments over the map surface. **This is the only place backdrop-filter is used in the system** — and only because the map content underneath has its own visual weight that the overlays must sit above without being opaque.

## Elevation & Depth

There is no elevation system in the conventional sense. **No drop shadows, no inset shadows, no glow, no blur for decoration.** Depth is signalled by:

1. **Tonal shift** — `bg` → `panel` → `elev` are three steps of lightness on the same hue. A button on a panel is one shade up from the panel; an input on a button row is the same `elev`.
2. **Hairlines** — 0.5 px divider rules in `line` colour at 60–80% alpha. These do the structural work that drop shadows do in other systems.
3. **One exception** — focus rings use a `box-shadow: 0 0 0 1px var(--accent)` at 2 px offset. This is functional, not decorative, and is the only `box-shadow` value permitted in the system.

Backdrop blur appears only on map overlays (toolbar, pills, scale bar). It is 6 px and never higher. It is not used elsewhere.

## Shapes

Corners are small. The default radius is 4 px (`rounded.md`); larger surfaces use 6 px (`rounded.lg`); chips and indicators use 2 px (`rounded.xs`). The toolbar group container is 6 px, the buttons inside it are 3 px — so the group reads as a unit and the buttons sit inside it without competing.

**No fully rounded pills.** No 999 px border-radius anywhere in the system. The metric pills in the map overlay are 4 px corners, not stadium-shaped. This is intentional: the editor reads as instrumental, not friendly.

**No rounded corners on single-sided borders.** Forbidden by Impeccable's design laws. The system has no single-sided coloured borders anyway — see "Do's and Don'ts."

## Components

The YAML above defines the full component contract. A few notes on how components compose, beyond what tokens alone can express:

### Section header pattern

The Inspector header strip and every collapsible section title sit on `panel-elevated` — one tonal step above `panel` in Night, one step below in Day. The strip itself does the structural work that a border would otherwise do. The header text is `text` (sentence case, panel-title typography); the section-title text is `text-mute` (uppercase, letter-spaced) with a chevron at the far right that rotates 180° on collapse. **There is no coloured marker stripe on the left.** The original design experiment used a 4 × 12 px accent stripe; that is the most overused dashboard tell in admin UIs and is forbidden by Impeccable's BAN 1. If a section needs an "active" indication, the chevron tints to `accent`. That is sufficient.

### Buttons

Three button classes: primary (`accent` fill, `bg` text — used for the Apply Changes commit action and nothing else), secondary (`elev` fill, `text` text, hover tints text to `accent`), destructive (`elev` fill, `danger` text). Use primary sparingly — only one primary button is visible at a time. The "Add point / Add line / Add polygon" feature-creation grid uses three secondary buttons of equal weight, not three primaries.

### Range sliders

Range sliders are 2 px tracks with a **4 × 14 px vertical grip** (not a circular knob, not a square nub). The grip is filled with `control-grip` and has no border — the height differential against the 2 px track does the visual work. The shape echoes a vernier scale on a survey instrument and reads correctly even at small sizes. The fill (left of grip) is `accent`; the unfilled portion (right of grip) is `line`. The numeric readout sits to the right of the slider in neutral `readout` colour and Commit Mono. The accent fill carries the active state; the value remains data, not a second accent.

### Color picker rows

A color picker row is: label on the left, a "swatch input" on the right. The swatch input is a small `elev`-background pill containing a 14 × 14 px coloured chip and a hex value in Commit Mono using `readout`. Clicking it opens the native color picker. The hex value is always shown — the user is colour-fluent, hide nothing. The hex text is neutral because the colour chip already carries the colour.

### Map overlays

Four overlays float on the map: top-left toolbar (zoom, fit, vertex-edit), top-right metric pills (feature count + file size), bottom-left coordinate readout (cursor lat/lng in OKLCH-style mono), bottom-right scale bar (mono distance label + 60 × 2 px solid bar). All four use the same translucent `panel` background. Overlays are draggable in only one place (the toolbar group); the other three are static.

### JSON editor

The raw-document editor is a Commit Mono code field with a left gutter (24 px wide) showing line numbers in `text-faint`. The gutter is separated from the code area by a 0.5 px `line-soft` rule. Syntax highlighting uses four token roles: keys (`accent`), strings (`success`), numbers (`warn`), punctuation (`text-faint`). All four colours are theme-aware and resolve from the same token names in Cartograph Day.

### Vertex-edit mode

When the user enters vertex-edit mode, the map cursor switches to crosshair and selected-feature vertices render as 6 px circles with a 1 px `accent` ring and `elev` fill. The "Edit vertices" button in the Inspector tints to `button-icon-active` (i.e. `accent-soft` background, `accent` text).

## Do's and Don'ts

These are hard rules. Violating any of them produces output that does not match Cartograph.

### DO

- **DO use VS Code theme detection** to switch between Night and Day. Read `data-vscode-theme-kind` (or the equivalent CSS API). Do not add an in-app theme toggle — the IDE owns that decision.
- **DO render numeric values in Commit Mono.** Coordinates, hex codes, range readouts, feature counts, file sizes, JSON, EPSG codes. Always.
- **DO keep passive readouts neutral.** Hex codes, line widths, stroke widths, and opacity percentages use `readout`, not `accent`.
- **DO protect tiny control handles from custom theme collapse.** Toggle knobs use `control-thumb`; slider grips use `control-grip`. Both derived tokens stay legible against any input background a custom VS Code theme might set.
- **DO pass through VS Code CSS variables as fallbacks.** Tokens should resolve as `var(--vscode-editor-background, #11191B)` etc., so users on High Contrast or custom themes inherit safe defaults.
- **DO use 0.5 px hairlines for dividers**, applied at 60% alpha in dark and 80% alpha in light.
- **DO use the accent sparingly** — one primary button visible at a time, one selected map feature highlighted at a time.
- **DO show focus rings** on every interactive element. 1 px accent ring at 2 px offset. Keyboard users must always know where they are.
- **DO respect `prefers-reduced-motion`** — disable all transitions when set. There is no decorative motion to lose.
- **DO write button labels as imperative verbs** in sentence case: "Add point", "Apply changes", "Round coordinates".

### DON'T

- **DON'T rely on inherited text colour.** Every text element in the webview must set `color` explicitly to a Cartograph token. VS Code injects its own theme variables onto host wrappers; if a header or label inherits colour from `body` or any host scope, a custom theme can flip it (e.g. white text on the new `panel-elevated` strip in Day mode). This is not theoretical — the very mockups used to design this system exhibited the bug. Always set `color` on `h4`, `label`, `span`, and any element that renders text.
- **DON'T use coloured side-stripe borders** on cards, list items, callouts, or section headers. No `border-left` greater than 1 px as an accent. (Impeccable BAN 1 — the most overused dashboard tell, and the trap the first iteration of this design fell into.)
- **DON'T use gradient text.** No `background-clip: text` with a gradient fill. (Impeccable BAN 2.)
- **DON'T use drop shadows** on cards, panels, or buttons. Depth is tonal and hairline-driven, not shadow-driven. The only `box-shadow` permitted is the 1 px focus ring.
- **DON'T use glassmorphism** anywhere except the map overlays, where backdrop blur serves a real legibility purpose. No frosted-glass cards in the sidebar.
- **DON'T use cyan-on-black neon palettes**, purple-to-blue gradients, or any other "AI dark mode" cliché. Cartograph Night's accent is teal at L 0.77 — it is not glowing, it is just visible.
- **DON'T nest cards inside cards.** Sections sit on `panel`, fields sit directly inside sections. There is no card-on-card hierarchy.
- **DON'T use bounce or elastic easing** for any motion. Real instruments decelerate smoothly; nothing in the UI should bounce.
- **DON'T use Title Case** for headings. Sentence case for everything except section titles (uppercase + letter-spaced) and EPSG codes.
- **DON'T render the same control in two places.** No mini-toolbar on the map duplicating actions that already exist in the sidebar.
- **DON'T use emoji** in UI labels, button text, or empty states. The map data may contain emoji in property values — those are user data and render as the user wrote them.
- **DON'T use icon-above-heading templates** for sidebar sections. Section titles are text only; icons appear only on buttons and the toolbar.
- **DON'T thank the user, apologise to the user, or ask the user how it went.** This is an instrument, not a host.

---

## Implementation notes

- **Token replacement.** The existing extension's `media/main.css` opens with a `:root` block defining colour and typography variables. Replace that entire block with a `:root` declaration of the YAML token names, including derived CSS variables for `readout`, `control-thumb`, and `control-grip`, plus a `[data-vscode-theme-kind^="vscode-light"]` override block carrying the Cartograph Day base values. Component selectors (`.side-panel`, `.group-header`, `.style-row`, `.json-editor`, etc.) keep their names — only the values they consume change.
- **Font loading.** Add `<link rel="preconnect">` for `fonts.googleapis.com` and load Hanken Grotesk (400, 500) and Commit Mono (400, 500). Both fonts must be added to the webview's CSP `font-src` and `style-src` allowlist.
- **Validation.** Run `npx @google/design.md lint DESIGN.md` before merging changes. The token graph should produce zero errors. Contrast warnings are expected on `text-faint` pairings — those tokens are scoped to large/icon use only and the prose documents that exception.
