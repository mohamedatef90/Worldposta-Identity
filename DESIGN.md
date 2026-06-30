---
name: WorldPosta Identity
description: Operator-grade platform identity for sovereign telco/ISP cloud infrastructure
colors:
  ink: "#0a1320"
  ink2: "#0d1b2b"
  navy: "#13263a"
  green: "#7cb342"
  lime: "#a8cf38"
  lime-pale: "#cde9a2"
  deep: "#5d9842"
  fog: "#c5d2e2"
  fog2: "#8497ae"
  fog3: "#5a6c82"
  white: "#ffffff"
  # Scoped accents — NOT general accents. Each appears only inside the one
  # component that must distinguish multiple entities. See §2 "The Scoped Accent Exception."
  cloud-blue: "#6aa0d6"        # CloudEdge stream in the NextEdge/CloudEdge comparison
  cloud-blue-deep: "#3e6fa8"   # CloudEdge edge/icon tint
  ad-teal: "#3fa796"           # dashboard chart series / 2nd co-editor
  ad-gold: "#d8b24c"           # dashboard chart series / 3rd co-editor
typography:
  display:
    fontFamily: "Space Grotesk, -apple-system, system-ui, sans-serif"
    fontSize: "clamp(28px, 4vw, 50px)"
    fontWeight: 700
    lineHeight: 1.08
    letterSpacing: "-0.02em"
  body:
    fontFamily: "Inter, -apple-system, system-ui, sans-serif"
    fontSize: "clamp(15px, 1.4vw, 17px)"
    fontWeight: 400
    lineHeight: 1.7
  label:
    fontFamily: "JetBrains Mono, ui-monospace, SFMono-Regular, monospace"
    fontSize: "11px"
    fontWeight: 400
    letterSpacing: "1.4px"
rounded:
  pill: "100px"
  card: "12px"
  card-lg: "20px"
  focus: "4px"
spacing:
  section: "88px"
  gap-lg: "64px"
  gap-md: "32px"
  gap-sm: "16px"
components:
  button-primary:
    backgroundColor: "linear-gradient(120deg, #7cb342, #a8cf38)"
    textColor: "{colors.ink}"
    rounded: "{rounded.card}"
    padding: "14px 24px"
  button-ghost:
    backgroundColor: "rgba(255,255,255,0.03)"
    textColor: "{colors.white}"
    rounded: "{rounded.card}"
    padding: "14px 24px"
  eyebrow:
    backgroundColor: "rgba(124,179,66,0.08)"
    textColor: "{colors.lime}"
    rounded: "{rounded.pill}"
    padding: "7px 16px"
---

# Design System: WorldPosta Identity

## 1. Overview

**Creative North Star: "The Control Room"**

This is infrastructure-grade visual language. The surface evokes a darkened operations centre: deep navy-black canvases, precise monospace annotations, and a single sovereign green that appears only where authority speaks. Every element carries operational weight — nothing is decorative, everything signals capability or ownership.

The design explicitly rejects SaaS-landing warmth, crypto neon excess, and hyperscaler console clones. Rounded-everything friendliness, pricing-tier grids, smiley stock photography, and startup badge clutter are forbidden. The target reader is a telco executive in an evaluation meeting — they need to feel they are looking at infrastructure, not a product tour.

Motion is restrained: entrances confirm context, never distract. Spacing is generous and deliberate; density lives only inside data-dense components (dashboards, tables). The accent green `#a8cf38` is the single voice of emphasis — it is rare, which is why it commands attention when it appears.

**Key Characteristics:**
- Deep navy-black canvas (`#0a1320`) with subtle tonal layering (`#0d1b2b`, `#13263a`)
- One accent: sovereign green gradient (`#7cb342 → #a8cf38`), used sparingly
- Space Grotesk display + Inter body — authoritative geometric paired with legible humanist
- JetBrains Mono for all operational labels, kickers, and data annotations
- Cards and surfaces use 12px radius (confident, not playful); pills for tags only

## 2. Colors: The Sovereign Spectrum

A near-monochromatic dark system with a single controlled accent. The palette communicates: this is a data centre, not a consumer app.

### Primary
- **Sovereign Green** (`#7cb342`): The anchor of the accent gradient. Used on large text spans, icon fills, and gradient starts.
- **Lime Signal** (`#a8cf38`): The high-visibility end of the accent gradient. Used on active states, kicker dots, focus rings, and gradient ends. The color that says "live" and "owned."
- **Lime Pale** (`#cde9a2`): For gradient text tails and very sparse accent whispers. Never used as body text.

### Neutral
- **Deep Ink** (`#0a1320`): Primary canvas. The darkest surface — body background and full-bleed sections.
- **Surface Ink** (`#0d1b2b`): Card and panel backgrounds. One tonal step above the canvas.
- **Navy Surface** (`#13263a`): Elevated surface for modals and layered cards. The third tier of depth.
- **Fog** (`#c5d2e2`): Primary body text on dark. Hits WCAG AA at all tested sizes.
- **Fog Mid** (`#8497ae`): Secondary text, subtitles, supporting copy.
- **Fog Deep** (`#5a6c82`): Tertiary text, metadata, disabled states.
- **White** (`#ffffff`): Headlines, hero text, and high-emphasis labels only.

### Named Rules
**The One Accent Rule.** The green gradient is the only accent in the system. No other hue reaches saturation. Competing accents are prohibited — they dilute sovereignty.

**The Fog Hierarchy Rule.** Body copy uses `#c5d2e2` (Fog), not white. White is for headlines only. Using white for body text flattens hierarchy and burns contrast budget.

**The Scoped Accent Exception.** The One Accent Rule governs *page-level* emphasis. Inside a single component that must encode multiple distinct entities, a small, named set of scoped accents is permitted — and only there:
- **Comparison dual-accent.** When two offerings sit side by side (the `#stacks` NextEdge/CloudEdge consoles), NextEdge keeps the sovereign green and CloudEdge takes **Cloud Blue** (`#6aa0d6`). The pairing is meaningful — green = compute-native, blue = network-secured — not decorative. Two accents maximum, one per side.
- **Data / presence series.** Dashboard charts and multi-user presence (Atrium donut, co-editing cursors) may use **`#3fa796` teal** and **`#d8b24c` gold** alongside the green to separate series or collaborators. These are scoped tokens declared locally on the component, never global.
- **Product-screenshot palettes.** Light product mockups (below) carry their real product brand colors and are exempt from this system entirely.

A scoped accent must never leak into page chrome, headings, buttons, kickers, or links — those stay sovereign green.

## 3. Typography

**Display Font:** Space Grotesk (with -apple-system, system-ui, sans-serif fallback)
**Body Font:** Inter (with -apple-system, system-ui, sans-serif fallback)
**Label/Mono Font:** JetBrains Mono (with ui-monospace, SFMono-Regular, monospace fallback)

**Character:** Space Grotesk's geometric precision telegraphs authority; its slightly technical feel fits infrastructure without becoming cold. Inter provides long-form legibility. JetBrains Mono marks operational data, kickers, and annotations as belonging to the machine layer — not human marketing.

### Hierarchy
- **Display / H2** (700, `clamp(28px, 4vw, 50px)`, 1.08 leading, -0.02em tracking): Section headlines. White text. Always paired with a `.ey` kicker above.
- **H3 / Card Title** (600, 18–20px, 1.4 leading): Product card headings and feature cluster titles.
- **Body / Lede** (400, `clamp(15px, 1.4vw, 17px)`, 1.7 leading): Narrative copy. Fog (`#c5d2e2`). Max width 640px (≈65ch).
- **Supporting Body** (400, 13.5–15px, 1.65 leading): Secondary card copy, feature descriptions.
- **Label / Kicker** (400, 11px mono, 1.4px tracking, uppercase): All `.ey` eyebrow pills, data annotations, sidebar group headers. Lime accent on dark backgrounds.

### Named Rules
**The Mono Mark Rule.** Operational context — "Connected source," "AZ count," "Suite read-only," any kicker label — uses JetBrains Mono. It is the typographic signal that something belongs to the infrastructure layer, not the marketing layer.

**The Gradient Text Exception.** `.grad` applies a gradient `background-clip: text` to headline spans. This is a single purposeful exception for display text only. It is prohibited on body copy, labels, or any text smaller than 18px.

## 4. Elevation

The system is flat-by-default, using tonal layering (`#0a1320 → #0d1b2b → #13263a`) rather than shadows to establish depth. Shadows appear only as purposeful exceptions — the accent glow on primary buttons and the panel drop shadow on the Atrium dashboard.

### Shadow Vocabulary
- **Accent Glow** (`0 8px 24px rgba(124, 179, 66, 0.28)`): Primary button resting state. Communicates energy without lifting off the surface.
- **Lime Dot Pulse** (`0 0 10px #A8CF38`): Used on `.ey-dot` and live-status indicators. Reinforces "active" and "live."
- **Panel Deep** (`0 44px 90px rgba(4,10,22,.62)`): Atrium dashboard panel. Large-scale depth for immersive data components only.

### Named Rules
**The Flat-By-Default Rule.** Surfaces rest flush. No ambient shadows on cards. Tonal layering communicates hierarchy; shadows appear only as state feedback (button press, modal open, live-indicator glow).

## 5. Components

### Buttons
- **Shape:** Gently rounded (12px radius — confident, not playful)
- **Primary (`.btn-p`):** Sovereign green gradient background (`#7cb342 → #a8cf38`), deep ink text (`#0a1320`), accent glow shadow. Padding 14px/24px. Font-weight 600, 15px.
- **Ghost (`.btn-g`):** Near-transparent background (`rgba(255,255,255,0.03)`), white text, `rgba(198,208,220,0.2)` border. Hover lifts border to `rgba(198,208,220,0.4)`.
- **Focus:** 2px solid `#a8cf38` outline, 3px offset, 4px radius. Global rule on `:focus-visible`.

### Eyebrow / Kicker (`.ey`)
- Pill shape (100px radius), `rgba(124,179,66,0.08)` background, `rgba(124,179,66,0.4)` border.
- JetBrains Mono, 11px, 1.4px tracking, lime (`#a8cf38`) text. 7px lime dot with glow.
- Used once per section as a section identifier, never stacked.

### Cards (`.pc-card`, product cards)
- 14px radius. Background `#0d1b2b`. Border `rgba(38,54,80,0.28)`.
- Hover state: border shifts to lime-tinted `rgba(124,179,66,0.2)`.
- Internal padding: 28px. Product card body uses 13.5–15px Inter at `#c5d2e2`.

### Layer Stack (`.layer-stack`)
- 20px radius container. Tonal fill per layer: hardware `rgba(8,14,24,0.9)`, software `linear-gradient(135deg, rgba(28,52,28,0.85), rgba(16,36,48,0.9))`, services lighter overlay.
- Subtle accent edge: `rgba(124,179,66,0.25)` separator between layers.

### Sidebar Navigation
- Fixed left rail, `#0a1320` background. Active link: lime accent on left + lime text. Hover: subtle lift.

### Atrium Dashboard (`.adash`)
- Full-width UI mockup component. 11px base font. `#0d1b2b` canvas, `rgba(13,27,43,.85)` panels.
- KPI cards with count-up animation. Scoped local tokens: `--ad-gold: #D8B24C`, `--ad-teal: #3FA796`.
- Used only as product visual inside the Atrium card modal.

### Product-screenshot mockups (`.office-dash`, `.drv-dash`, `.sso-dash`, …)
- Illustrative renderings of real product UIs, shown inside a product-card modal. **Deliberately light-surfaced** (`#fff` / `#eceef2`, ~10px radius) because they depict actual screens — a sanctioned exception to the dark canvas and the One Accent Rule.
- Carry authentic product brand colors where the product demands it: Word `#2B579A`, Excel `#217346`, PowerPoint `#C43E1C`; Drive/Google-style greys.
- **Co-editing presence** uses three distinct identity colors — green (you), `--ad-teal` (#3FA796), `--ad-gold` (#D8B24C) — for cursors, name flags, and avatars.
- `office-dash` is **interactive**: a tab strip switches Word / Excel / PowerPoint panes (each its own ribbon, surface, status bar, URL). Because the card content is cloned into the modal, switching is handled by a **delegated `document` click listener**, not per-element handlers.

### Signal-path comparison consoles (`.vs-con`, in `#stacks`)
- Two console windows side by side (traffic-light chrome + URL), comparing **NextEdge** (green) and **CloudEdge** (`#6aa0d6` blue) under a shared heading.
- Structure: window chrome → **head title bar** (`.vs-con-head`, the product name — "the main head") → body of stacked technology layers (`.vs-node`, each with a mono `tier` label + name) wired to a vertical connector.
- A `.vs-packet` dot travels the connector top→bottom on a loop (the request flowing down the stack); nodes fade in on `.vs-stage.in`. Surfaces use `--ink2`/`--navy`; both halves collapse to one column under 860px.

### Full-screen diagram overlay (`.eco-overlay` / `.eco-zoom-panel`)
- Expands a complex diagram to a 90vw × 90vh panel on the dark-glass backdrop (mirrors the product modal's language: blurred backdrop, lime-accent border + close button).
- Opens with a **clone of the source SVG** (no asset duplication; vector scales crisply). Closes on ×, backdrop click, or Esc; body scroll locks while open; focus moves to the close button and returns to the trigger.
- Trigger is `.eco-expand` — a mono "Full screen" pill pinned to the diagram's top-right; icon-only under 600px.

## 6. Do's and Don'ts

### Do:
- **Do** use `#c5d2e2` (Fog) for all body copy on dark — not white. White is reserved for headlines.
- **Do** use JetBrains Mono for kickers, data labels, operational annotations, and sidebar group headers.
- **Do** keep the accent green gradient (`#7cb342 → #a8cf38`) as the only saturated color in any layout.
- **Do** respect section vertical rhythm: 88px padding (`padding: 88px 0` on `.sec`).
- **Do** use tonal layering (ink → ink2 → navy) to establish depth before reaching for shadows.
- **Do** limit `.grad` gradient-clip text to display headlines of 18px or larger.
- **Do** respect `prefers-reduced-motion` on all animations.
- **Do** test every text element for WCAG AA contrast (≥4.5:1 body, ≥3:1 large).
- **Do** wire interactivity inside cloneable content (product-card visuals) with **delegated `document` listeners**, so it survives being cloned into the detail modal.
- **Do** drive reveals with an `IntersectionObserver` that toggles an `.in` class; let CSS own the transition. One reveal observer per family, no competing scroll listeners.
- **Do** clone (not move) a source node when mirroring it into an overlay, and restore focus to the trigger on close.

### Don't:
- **Don't** use generic SaaS landing-page patterns: pricing tiers, smiley stock photos, badge clutter, rounded-everything, or startup warmth.
- **Don't** use crypto/web3 neon: glowing gradients, neon-on-black excess, hype language.
- **Don't** clone hyperscaler consoles (AWS/Azure look) — the point is owning your own stack.
- **Don't** add cheap-reseller signals: discount banners, noisy layouts, badge stacking.
- **Don't** introduce a second accent hue. The sovereign green is the only saturated color.
- **Don't** use gradient `background-clip: text` on body copy or labels — display only, and never below 18px.
- **Don't** use shadows as a default depth mechanism. Tonal layering first; shadows only for state feedback.
- **Don't** use `border-left` greater than 1px as a colored stripe accent on cards or list items.
- **Don't** stack multiple `.ey` eyebrow kickers in the same section — one per section maximum.
- **Don't** use white text for body paragraphs. Fog (`#c5d2e2`) provides hierarchy separation from headlines.
- **Don't** let a scoped accent (Cloud Blue, teal, gold) escape its component into page chrome, buttons, kickers, headings, or links — those stay sovereign green.

## 7. Interaction & Motion Patterns

The page is read top-to-bottom, so motion's job is to **confirm context on arrival**, not to entertain. Three patterns recur:

- **Scroll-reveal.** An `IntersectionObserver` adds `.in` to a section/visual as it enters; CSS transitions opacity/transform from a resting offset. Stagger children with a `--n` (or `--i`) custom property feeding `transition-delay`. Examples: `.eco-vis.in`, `.vs-stage.in`.
- **Ambient loop.** A single small element loops to imply liveness — the `.vs-packet` travelling a connector, the Atrium count-ups, the live-dot pulse. One looping element per component; keep it quiet.
- **Clone-safe controls.** Product-card mockups are cloned into the modal, so their controls (office tab-switch, `cmp-vis` slider) use **delegated listeners on `document`** keyed by class. Per-element handlers would silently die on the clone.

**Overlays.** Two patterns share one visual language (blurred dark backdrop, lime-accent border, × close, Esc + backdrop-click to dismiss, body-scroll lock, focus to close → return to trigger): the **product-card modal** (`.pc-overlay`) and the **full-screen diagram view** (`.eco-overlay`, a 90vw × 90vh panel holding a cloned SVG).

**Reduced motion.** Every animation above is wrapped so `@media (prefers-reduced-motion: reduce)` drops it to the resting state — reveals show immediately, loops stop or hide, transitions are removed. This is a hard requirement, not a nicety.

## 8. Build Constraints

- `index.html` is **fully self-contained**: inline `<style>` and `<script>`, no external assets, fonts-via-CDN, framework, or build step. Tokens live in `:root`.
- Preview with `python3 -m http.server <port>` then open `http://localhost:<port>/index.html` (Playwright blocks `file://`).
- Keep this `DESIGN.md` and the `:root` token block in sync — when you add a scoped accent or component, document it here so design-lint recognizes it as intentional rather than drift.
