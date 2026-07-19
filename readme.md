# Frostyard Design System

Frostyard makes **atomic, updateable operating systems** for desktops and servers, built from Debian with mkosi/snosi. A known-good base stays put; tools arrive as deliberate layers (systemd-sysexts, containers, user-space environments). Products represented:

- **frostyard.org** — the marketing/technical landing site (the primary surface this system recreates)
- **Images**: `snow` (GNOME desktop), `snowfield` (Surface hardware desktop), `cayo` (headless server), plus the shared base image
- **Tools**: `updex` (sysext manager CLI), `ChairLift` (GTK 4 desktop system workspace)

## Sources

- https://github.com/frostyard/frostyard-org — Astro source of the live example site (https://frostyard-org.bjk.workers.dev). **Ground truth for all visuals**: `src/pages/index.astro`, `src/pages/tools.astro`, `src/pages/why-atomic.astro`, `src/pages/snow.astro`, `src/layouts/ProductPage.astro`.
- https://github.com/frostyard/snosi — image build system; `artwork/hero/` (PR #442) supplied the four alpine hero backgrounds copied into `assets/hero/`.
- https://github.com/frostyard/frostyard.github.io — older docs site (Tailwind, slate/sky palette). Superseded by the frostyard-org direction; consulted for content only.

Readers with access should explore these repos to design more faithfully against the product.

## CONTENT FUNDAMENTALS

- **Tone**: calm, declarative, quietly confident. Systems-engineering plainness with a literary edge. No hype, no exclamation points, no emoji.
- **Signature move — the two-beat headline**: a short imperative pair, second beat often italicized serif: "Keep the system *boring.* Make the work interesting." / "Change the tool. *Not the ground beneath it.*" / "Keep the base still. *Move with intent.*"
- **Metaphor field**: cold/alpine/altitude. "Install software at the right altitude", "Choose the terrain", "turning the base into a snowball", "permanent sediment", "Cold systems. Clear boundaries."
- **Casing**: sentence case everywhere, including headings. Product names lowercase (`snow`, `cayo`, `updex`) except ChairLift. Eyebrows are UPPERCASE via CSS, not authored caps.
- **Person**: second person for the reader's things ("your tools arrive as deliberate layers"); the system is described in third person, often personified as calm ("the host stays deliberately uninteresting", "a desktop that holds its shape").
- **Sentences**: short. Semicolons and periods over conjunctions. Definitions by boundary: "Immutability is not a prohibition. It is a boundary…"
- **Numbers as structure**: mono `01 02 03` index markers on card/list sequences.
- **CTAs**: verb-first with a directional glyph — "Explore images ↓", "Read the build ↗", "Inspect snosi ↗". External links always get ↗.

## VISUAL FOUNDATIONS

- **Color**: near-black blue page (`--ink #06111d`) under a fixed page gradient (faint radial glow upper-right + vertical `#071a2a→#06111d`). Panels/cards are deep blue gradients (`#0f3048→#091c2d` family). Accents are cold: ice `#aee9ff`, sky `#47b8ef`, blue `#168bd0`. Text is `#edf8ff` with mist-blue mutes. **No warm colors anywhere.**
- **Type**: Inter for everything; Georgia italic only for the `<em>` beat inside display headings; ui-monospace for eyebrow-adjacent details, numbers, code. Display type is huge (up to 6.4rem) with tight negative letter-spacing (−.06 to −.075em) and line-height ≤1.
- **Eyebrow pattern**: 24px×1px sky dash + uppercase .7rem letter-spaced kicker precedes every section heading.
- **Backgrounds**: flat token gradients or the alpine hero PNGs (`assets/hero/`) — 3440×1440 ultrawide, shared ridge geometry, light always upper-right, upper-left quadrant reserved as negative space for branding. Use them full-bleed behind hero copy.
- **Borders**: 1px hairlines of `rgba(162,222,255,.18)` do all separation — section rules, card edges, list row dividers. Vertical hairlines divide grid columns (principles/facts patterns).
- **Corners**: essentially square. Tags 2px, buttons 4px, SVG nodes 3px; the only pill is the nav "Source ↗" link (100px). No shadows except soft cyan glows on decorative orbs (`box-shadow:0 0 50px #3cbdf444`).
- **Cards**: gradient fill + hairline border + generous padding; no rounding, no drop shadow. Numbered mono index top-right.
- **Buttons**: primary = cyan gradient (135deg, #5ac9f7→#1584ca) with near-black text `#02131f`; ghost = hairline border, pale text. Arrows/glyphs inside buttons render in ice.
- **Hover**: color shifts to ice (`--ice`) on links; SVG nodes brighten fill + stroke-opacity→1. No motion on hover, no scale/press effects.
- **Animation**: minimal and infrastructural — dashed "energy lines" flowing along SVG paths (stroke-dashoffset, 1.8s linear infinite), `scroll-behavior:smooth`. Honors `prefers-reduced-motion`. Nothing bounces.
- **Transparency/blur**: none. Layering is done with alpha-tinted hairlines and gradients, not backdrop blur.
- **Imagery**: cool, blue, geometric-minimal (the alpine hero set). No photography, no warm grain.
- **Layout**: 1240px max container, 32px side padding, 92px nav. Sections separated by hairlines and ~8rem vertical padding. Asymmetric two-column grids (1.2fr/.8fr etc.) with baseline-aligned ends.
- **Decorative motifs**: ❄ snowflake (brand mark), ✦ four-point flake (list bullets), diamond crystals (rotated squares with cyan glow), alpine ridgelines (crop the hero art, never redraw), dashed energy/layer lines, hex lattices + binary digits hidden in hero art.

## ICONOGRAPHY

- **No icon font and no SVG icon set** in frostyard-org. Iconography is typographic: unicode glyphs `❄` (brand snowflake), `✦` (list bullets), `↗` (external), `↓` `→` (directional). Keep it that way in new designs.
- The older docs site used Heroicons 16 solid inline; that direction is superseded — do not reintroduce an icon library without need.
- **No logo exists** in the provided sources. The brand mark is the text wordmark "❄ frostyard" (weight 720, −.04em). Do not draw a logo.
- Diagrams are hand-authored inline SVG (composition map) with mono labels — follow that pattern for new diagrams.
- No emoji, ever.

## Fonts

Inter is referenced by the source as a system/stack font; no font binaries ship in the repos. This system loads **Inter from Google Fonts** (`tokens/typography.css`) as the nearest match — if Frostyard has licensed font files, replace the import with `@font-face` rules.

## Index

- `styles.css` — global entry; imports `tokens/{colors,typography,spacing}.css`
- `assets/hero/` — 4 alpine hero/wallpaper PNGs (3440×1440) + their README
- `guidelines/` — foundation specimen cards (Colors, Type, Spacing, Brand groups)
- `components/core/` — Button, Eyebrow, Tag, SectionHeading
- `components/site/` — NavBar, SiteFooter, ImageCard
- `ui_kits/frostyard-org/` — click-through recreation of frostyard.org (home + tools + why-atomic)
- `ui_kits/docs/` — shared documentation shell, per-project content packs (snosi / updex / ChairLift)
- `ui_kits/pilothouse/` — Pilothouse admin console restyled to the Frostyard language (login, overview, sysexts, services, podman)
- `SKILL.md` — agent skill entry point

### Intentional additions
- `SectionHeading` — wraps the eyebrow+h2+lede pattern repeated on every page (direct extraction, not invention).
- `--state-ok/warn/danger` tokens — admin surfaces (Pilothouse) need state colors the marketing site never uses; hues are cold-shifted to stay in palette.
