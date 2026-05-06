# PRODUCT.md

> Strategic and brand-voice context for the GeoJSON Visual Editor.
> Read this before any design work. The visual tokens live in `DESIGN.md`;
> this file tells you *who* the work is for and *why* it should feel a particular way.

---

## Product

A custom editor for VS Code that makes `.geojson` files first-class spatial documents instead of raw JSON. The user opens a `.geojson` file and gets a live map preview, geometry styling, label control, vertex editing, and a JSON editor — all in a single webview that replaces the default text editor.

The product is a developer tool, not a consumer mapping app. It sits inside an IDE, alongside Python pipelines, Power BI exports, GIS scripts, and shell windows. It must feel like an authoritative tool — closer to QGIS or a survey instrument than to Google Maps.

---

## Audience

GIS analysts, transport planners, urban-data engineers, and software developers who work with spatial data day-to-day. They:

- Live in VS Code. They expect IDE-grade behaviour: keyboard accessible, fast, no marketing surfaces.
- Read coordinates, hex codes, EPSG numbers, and feature counts as fluently as they read English. Numbers should be precise and monospaced.
- Care about precision over polish. A 0.5° offset in a graticule label is a bug, not a stylistic detail.
- Are colour-fluent. They will edit fill and stroke values directly. The app's chrome must not compete with the colours of their data.
- Work in two modes: long focused sessions on dark themes (analysis, late-night work) and shorter daytime sessions on light themes (cartographic work, presentations). The product must serve both registers equally well.

---

## Job to be done

> *"Open a GeoJSON file, see what's in it on a map, fix it, and save it — without leaving the IDE."*

The interface should disappear into that loop. Every interaction is in service of: see the data, change the data, write the data back to disk.

---

## Brand personality (three words)

**Measured. Layered. Annotated.**

- **Measured** — every number shown is real and precise. No approximations, no rounded-for-display values without a way to see the truth. The interface respects that the user is working with surveyed data.
- **Layered** — the app is a stack of map layers. Depth is implied by hairline borders and tonal panel shifts, not by drop shadows or glassmorphism. The visual language echoes how vector tiles compose on a flat plane.
- **Annotated** — sections, fields, and readouts carry quiet labels in monospace. Like the legend on a topographic map, the chrome explains itself without raising its voice.

These three words steer every micro-decision. When in doubt: would a topographic surveyor in 1965 have approved of this UI element? If yes, it's probably right.

---

## Reference points

- The graticule and corner labels of a USGS topographic map sheet
- The legend panel of QGIS
- The status bar of a Bloomberg terminal (information density without decoration)
- The marginalia of a marine chart (sounding labels, scale bars)
- VS Code's own sidebar — for rhythm and chrome conventions, not aesthetics

## Anti-references — explicitly NOT this

- Mapbox Studio's marketing-coloured chrome
- Consumer mapping apps (Google Maps, Apple Maps) — too friendly, too rounded, too glossy
- "Modern SaaS dashboard" aesthetics: purple-blue gradients, rounded card grids, big metric tiles
- Glowing cyan-on-black "data viz" themes — the AI dark-mode reflex
- Glassmorphism, neumorphism, or any other depth-by-effect treatment
- Decorative motion. Map data already moves when you pan and zoom; the chrome must not
- Marketing copy, "welcome" surfaces, empty-state illustrations, or any ornament that suggests this is a product to sell rather than a tool to use

---

## Aesthetic direction

The design system is named **Cartograph** and ships in two themes:

- **Cartograph Night** — dark theme, dominant register. Used for sustained sessions inside dark VS Code workspaces. A bright teal accent (borrowed from hydrography on topographic maps) does almost all the semantic work.
- **Cartograph Day** — light theme, paired register. Used for daytime cartographic work and presentations. A deeper oxidised teal carries the same accent role at a higher contrast against a paper-cream sidebar.

Both themes share token names, type scales, and component rules. Switching between them is a matter of swapping the colour layer; layout, density, typography, and component structure are identical.

The accent is a single hue. It is rare, and it earns its rarity. The 60-30-10 rule applies: roughly 60% surface, 30% borders and muted text, 10% accent. When everything is teal, nothing is teal.

---

## Theme selection — rule

The extension reads VS Code's `data-vscode-theme-kind` attribute (or equivalent) and applies Cartograph Night for `vscode-dark` and `vscode-high-contrast`, Cartograph Day for `vscode-light` and `vscode-high-contrast-light`. There is no in-app theme toggle — the IDE owns that decision.

---

## Voice and copy

- Sentence case for everything. No Title Case headings, no ALL CAPS UI labels except for two specific patterns: (1) section titles (uppercased, letter-spaced — they read as map-key headings), and (2) coordinate-reference codes like `EPSG:4326`.
- Numeric readouts are monospaced. Always. Coordinate strings, hex codes, line-width values, opacity percentages, byte counts, feature counts.
- Button labels are verbs in the imperative: "Add point", "Apply changes", "Round coordinates". Never "Click to add a point".
- Empty states explain what the next action is, not what the absence is. "Select a feature on the map to edit its properties." — not "No feature selected."
- Errors are specific. "Invalid GeoJSON: feature 12 has 3 coordinates, expected 2." — not "Something went wrong."
- Never apologise to the user. Never thank the user.

---

## Accessibility — non-negotiable

- All text token pairs in `DESIGN.md` clear WCAG AA (4.5:1 for body, 3:1 for large/icon).
- Focus states are visible on every interactive element. The accent colour at full opacity, used as a 1px ring offset 1px from the element border, is the standard pattern.
- Every range slider, color picker, and toggle is keyboard operable.
- Tooltips do not replace labels. Labels are always rendered.
- Reduced-motion users get all transitions disabled — there is no decorative motion to lose.

---

## Differentiation

What someone should remember about this editor, in one sentence:

> *"It feels like a survey instrument, not a webview."*

Every design decision in `DESIGN.md` is in service of that sentence.
