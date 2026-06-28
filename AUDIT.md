# Impeccable Audit — `index.html`

**Target:** `index.html` (active root surface)
**Register:** Brand (marketing / identity page)
**Date:** Jun 28, 2026
**Method:** Code-level review against the brand register and impeccable rules. Contrast ratios verified by calculation against the `#080E1C` canvas; anti-pattern findings verified against the actual DOM (not just leftover CSS).

---

## Audit Health Score

| # | Dimension | Score | Key Finding |
|---|-----------|-------|-------------|
| 1 | Accessibility | 2 | Secondary text (`#4E6078`, `#5A7090`) ≈3:1, fails WCAG AA; no reduced-motion |
| 2 | Performance | 3 | Lean load, but duplicated inline base64 logo + ~20 blurred SVG nodes + always-on SMIL loops |
| 3 | Responsive Design | 3 | Real breakpoints + hamburger; touch targets under 44px |
| 4 | Theming | 2 | Zero tokens — every color hard-coded and repeated dozens of times |
| 5 | Anti-Patterns | 1 | Three hard-ban violations, each used site-wide |
| **Total** | | **11/20** | **Acceptable — significant work needed** |

---

## Anti-Patterns Verdict — start here

**Fail.** Despite a genuinely distinctive dark-sovereign palette (this is *not* SaaS-cream), the page trips three of the skill's explicit hard bans, and each one is used as a system, not a one-off:

1. **Gradient text on every heading.** `.grad` (`background-clip:text` + green gradient) is applied to the highlighted line of basically every section heading — overview, opportunity, provide, cloud, collab, operations, about, security, operated, sectors, start. This is a match-and-refuse ban. The "Everything connected." / "to one connected ecosystem." / "shaped around how you operate." treatment is the tell.
2. **Tiny uppercase tracked eyebrow above every section.** `.kicker` (11px, `letter-spacing:1.4px`, uppercase, with a leading rule) sits above ~11 section headings ("Why now", "The platform · NextEdge", "Why WorldPosta · Trust"…). That repeated cadence is AI grammar, not voice.
3. **Side-stripe borders.** `.note` and `.pc-hl` both use `border-left:3px solid #8BBF3C` as a colored accent on callouts — the exact banned pattern.

Secondary tells: **identical icon + heading + text card grids** (`.offer`, `.sectors`, `.adv-grid`, `.g2`) and a **system-font-only stack** (`-apple-system / Segoe UI`) chosen by reflex rather than for the "sovereign · precise · weighty" brief.

---

## Executive Summary

- **Health: 11/20 (Acceptable).** The bones are solid — clean structure, distinctive dark identity, no framework bloat — but the surface carries textbook AI tells and the foundation has no theming layer.
- **Issues by severity:** P0: 0 · P1: 5 · P2: 5 · P3: 4
- **Top issues:**
  1. Gradient text on every heading (hard ban)
  2. Repeated eyebrow scaffolding on every section (hard ban)
  3. Secondary text below WCAG AA contrast
  4. No `prefers-reduced-motion` for any of the SVG/CSS animation
  5. No design tokens — fully hard-coded color, unmaintainable

---

## Detailed Findings by Severity

### P1 — Major (fix before release)

**[P1] Gradient text across all section headings**
- **Location:** `.grad` rule (line ~40); applied in every `<section>` heading
- **Category:** Anti-Pattern (hard ban)
- **Impact:** Reads as AI-generated; gradient adds no meaning and slightly reduces legibility of the brightest text.
- **Recommendation:** Solid color (`#fff` or `#A6D154`); create emphasis through weight/scale, not fill.
- **Command:** `/impeccable typeset`

**[P1] Eyebrow/kicker on every section**
- **Location:** `.kicker` (line ~235); ~11 occurrences
- **Category:** Anti-Pattern (hard ban)
- **Impact:** Uniform reflex; signals template-generated structure.
- **Recommendation:** Keep at most one deliberate kicker; vary the section-entry cadence elsewhere (lede-first, oversized numeral only where a real sequence exists, etc.).
- **Command:** `/impeccable distill`

**[P1] Secondary text fails WCAG AA contrast**
- **Location:** `#4E6078` (`footer p`, `td:first-child`, `.oleg`, `.layer-label`) ≈ **3.0:1**; `#5A7090` (`.sb-group`) ≈ **3.7:1** — both against `#080E1C`
- **Category:** Accessibility — **WCAG 1.4.3 (AA)**
- **Impact:** Footer, sidebar group labels, and legends are hard to read. (Note: the main body muted color `#7C8EA8` ≈ 5.8:1 *passes* — the problem is the darker ramp ends only.)
- **Recommendation:** Lift the darkest text ramp toward `#7C8EA8`/`#8aa0bd` for any text-bearing element.
- **Command:** `/impeccable polish`

**[P1] No reduced-motion alternative**
- **Location:** CSS keyframes (`hb_dashB`, `hb_pulse`, lines ~385–391) and all SMIL `<animate>/<animateTransform>/<animateMotion>` in the two diagrams
- **Category:** Accessibility / Motion — **WCAG 2.3.3**
- **Impact:** Users with vestibular sensitivity get continuous looping motion with no escape.
- **Recommendation:** Add `@media (prefers-reduced-motion: reduce)` to pause CSS animations; gate/disable SMIL (e.g. set the diagrams to a static state) for that query.
- **Command:** `/impeccable animate`

**[P1] No design tokens (systemic)**
- **Location:** Entire stylesheet — `#8BBF3C`, `rgba(96,152,64,…)`, `rgba(38,54,80,.28)` repeated 40–60+ times each
- **Category:** Theming
- **Impact:** Any palette change is a find-and-replace minefield; high regression risk.
- **Recommendation:** Extract a `:root` token set (canvas, surface, ink, muted, accent ramp, border) and refactor to `var(--…)`.
- **Command:** `/impeccable extract`

### P2 — Minor

**[P2] Side-stripe border accents** — `.note`, `.pc-hl` use `border-left:3px solid`. Rewrite with a full hairline border or background tint. → `/impeccable polish`

**[P2] Touch targets under 44px** — `.sb-sub` (~26px), `.sb-link` (~34px), `.sb-toggle` (42px). Bump mobile nav padding/min-height to ≥44px. → `/impeccable adapt`

**[P2] Decorative SVGs not hidden from AT** — both diagram `<svg>`s expose stray `<text>` ("YOUR INFRASTRUCTURE", node labels) with no `role="img"`/`aria-label`. Add `aria-hidden="true"` (or a single labelled summary). → `/impeccable harden`

**[P2] Performance — runtime cost** — the WorldPosta base64 logo is embedded twice (sidebar + footer); ~20 orbit nodes each carry `filter:url(#hb_glow)`; the opportunity diagram runs many infinite SMIL loops that never idle. Reuse the logo via `<use>`/one asset, and reduce always-on motion. → `/impeccable optimize`

**[P2] Identical card grids** — four icon+heading+text grids in a row flatten the page's rhythm. Differentiate at least one (the sectors or the "what we provide" block). → `/impeccable layout`

### P3 — Polish

- **[P3] System-font reflex** — no brand typeface; a chosen display/text pairing would carry "sovereign · weighty" far better. → `/impeccable typeset`
- **[P3] Contact details not actionable** — `partners@worldposta.com` and `worldposta.com` are plain text, not `mailto:` / `https:` links.
- **[P3] No custom `:focus-visible`** — relies on UA default ring; a branded focus style would be more legible on the dark canvas.
- **[P3] Dead CSS** — large unused blocks (`nav`, `.hero`, `.orbit-*`, `.layer-stack`, `table`, `.stats`/hero-metric) inflate the file and confuse maintenance.

---

## Patterns & Systemic Issues

- **Color is hard-coded everywhere** — the single biggest structural debt; everything downstream (theming, contrast fixes, a brand refresh) is harder because of it.
- **Section construction is templated** — kicker + gradient heading + lede repeats identically per section; the sameness is what reads as machine-made.
- **Motion has no accessibility floor** — decorative animation was added without the required reduced-motion counterpart.

## Positive Findings

- **Distinctive, committed dark palette** — avoids the cream/SaaS default entirely; the green-on-deep-navy is genuine voice.
- **No framework, zero external requests** — everything inline; the page loads instantly.
- **Solid responsive skeleton** — real breakpoints, a working hamburger sidebar, reflowing grids.
- **Accessible accordion** — `aria-expanded` is correctly wired in JS, and the active-section observer is a nice touch.
- **Strong main-body contrast** — primary (`#C6D0DC`) and accent (`#8BBF3C` ≈ 8.8:1) text are well above AA.

---

## Recommended Actions (priority order)

1. **[P1] `/impeccable typeset`** — kill gradient-text on headings; rebuild emphasis with weight/scale (and consider a real brand typeface).
2. **[P1] `/impeccable distill`** — strip the per-section eyebrow scaffolding down to a deliberate cadence.
3. **[P1] `/impeccable extract`** — pull a `:root` token system so color is maintainable.
4. **[P1] `/impeccable animate`** — add `prefers-reduced-motion` handling across CSS + SVG.
5. **[P1] `/impeccable polish`** — lift the failing text ramp to AA and remove side-stripe borders.
6. **[P2] `/impeccable adapt`** — enlarge mobile touch targets to ≥44px.
7. **[P2] `/impeccable harden`** — `aria-hidden` the decorative diagrams.
8. **[P2] `/impeccable optimize`** — dedupe the inline logo, trim always-on motion + blur load.

> You can ask me to run these one at a time, all at once, or in any order you prefer.
>
> Re-run `/impeccable audit` after fixes to see your score improve.

---

## Setup note

This project has **no `PRODUCT.md`**, so this audit was run purely from the code and the brand register. Before doing design *changes* (the commands above), running `/impeccable init` once to capture the product/brand context will make every subsequent command sharper and on-voice.
