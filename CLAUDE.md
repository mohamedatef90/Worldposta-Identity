# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static, single-file HTML marketing/identity pages for **WorldPosta's operator platform** — no build tooling, no package manager, no framework. Each `.html` file is fully self-contained (inline CSS + JS, no shared assets).

**Editing scope.** The active work target at the repo root is **`index.html`** — a long-form product overview with a fixed sidebar nav, a right-side reading-progress spine, a hub-and-spoke hero ecosystem diagram, a layered-planes "what we provide" diagram, accordion **product cards that open into a detail modal** (`.pc-overlay`/`.pc-dialog`, content cloned in), and a set of bespoke in-card product mockups. Preview by serving locally for Playwright: `python3 -m http.server <port>` (Playwright blocks `file://`).

**Sections** (`<section class="psec" id="…">`): `overview · opportunity · provide · stacks · cloud · collab · operations · about · security · operated · brand · sectors · start`.

**In-card product mockups** (`.pc-visual …`): `io-dash`, `drv-dash`, `meet-dash`, `sso-dash`, `office-dash`, `billing-dash`, `nextedge-dash`, `watch-dash`, `pc-visual--adash` (Atrium), and `cmp-vis` (a drag image-comparison slider). These are self-contained illustrative UIs shown inside the product-card modal.

**Recently built (this stream of work):**
- **`office-dash`** — a browser mockup in the *Online Office Apps* card with switchable **Word / Excel / PowerPoint** views (tab strip → swaps ribbon, surface, status bar, URL), live co-editing cursors/presence, a spreadsheet with formula bar + cell selections, and a slide-deck view with a chart.
- **Ecosystem full-screen view** — a `Full screen` control (`.eco-expand`) on the hero diagram opens `.eco-overlay` → `.eco-zoom-panel` (90vw × 90vh) holding a **clone of the hero SVG**. Esc / backdrop / × to close; focus moves to close and returns to trigger.
- **`#stacks` — "The platform · Virtualization stacks"** — side-by-side **signal-path consoles** (`.vs-con` / `.vs-node` / `.vs-packet`) comparing **NextEdge** (green) and **CloudEdge** (blue): a head title bar, technology layers, and a packet that travels the connector on a loop. NextEdge = Hypervisor (KVM · Citrix · VMware) → OVS → Firewall integration; CloudEdge = VMware → NSX → Firewall integration.

## Sub-project: `.worldposta-provider-pitch/`

A separate pitch deck page lives in `.worldposta-provider-pitch/`. It has its own `CLAUDE.md` — **read that file first** before touching anything there. Key points from it:

- **`overview.html`** is the only editable file in that subproject. `overview_draft.html` and `presentation-F.html` are reference-only.
- Uses the **magic-black** design system (tokens, CDN libraries, motion lanes) documented in `DESIGN-SYSTEM.md`.
- Animation CDN stack: GSAP + ScrollTrigger (scroll owner), Motion (count-up / inView), anime.js v4 (SVG stroke-draw), lottie-web (medal). GSAP owns the scroll — don't add competing scroll listeners.

## Design systems — do not mix

| File | System | Canvas | Accent | Classes |
|---|---|---|---|---|
| `index.html` (root) | **Control Room** (see `DESIGN.md`) | `#0a1320` | `#7cb342→#a8cf38` | `.psec`, `.kicker`, `.btn-p`, `.btn-g`, `.grad` |
| `.worldposta-provider-pitch/overview.html` | **magic-black** | `#0A1320` | `#7CB342→#A8CF38` | `.section`, `.eyebrow`, `.btn-primary`, no `.grad` |

**`DESIGN.md` (repo root) is the authoritative design system for `index.html`** — tokens, type, components, do's/don'ts. Read it before any visual change here. The two systems share the same dark canvas and sovereign-green accent but use different class names and components; don't import classes from one into the other. Tokens live in the `:root` of `index.html` (`--ink`, `--ink2`, `--navy`, `--green`, `--lime`, `--fog`/`--fog2`/`--fog3`, `--display`/`--body`/`--mono`, `--ease`).

The sub-project's own system is documented in `.worldposta-provider-pitch/DESIGN-SYSTEM.md`; the source skill is at `/Users/roaya/Downloads/skill/magic-black.skill`.

## Interaction & motion conventions (index.html)

- **Modal/clone-safe interactivity.** Product cards clone their content into the detail modal, so any in-mockup interactivity (office tab-switch, comparison slider) is wired with **delegated listeners on `document`**, keyed off a class — never per-element handlers that would be lost on the clone.
- **Scroll-reveal.** Sections/visuals reveal via `IntersectionObserver` that adds an `.in` class (e.g. `.vs-stage.in`, `.eco-vis.in`); CSS does the transition. Don't add competing scroll listeners.
- **Reduced motion is mandatory.** Every animation (packet loops, scroll reveals, count-ups, caret blinks) must no-op or fall to the resting state under `@media (prefers-reduced-motion: reduce)`.
- **Product-screenshot mockups are a sanctioned exception** to the dark canvas: `office-dash`/`drv-dash`/`sso-dash` render authentic *light* product UIs (and real Office/Google brand colors) because they depict real screens. Keep them visually accurate; they don't follow the dark-surface or one-accent rules.
- **Scoped multi-entity accents** (teal/gold for collaborators, blue for the CloudEdge comparison) are allowed only inside the specific component that needs to distinguish entities — see `DESIGN.md` §2 "The Scoped Accent Exception." Never promote them to a general page accent.
- **Keep `index.html` self-contained** — inline CSS/JS, no external assets or build step.

## Design context

Target audience: **telco / ISP executives** evaluating whether to run branded cloud/mail/security on their own infrastructure. Tone: **sovereign · precise · weighty**. Anti-references to avoid: generic SaaS landing pages, crypto/web3 neon, hyperscaler console clones, cheap reseller badge clutter.

Design principles and audience detail: `.worldposta-provider-pitch/.impeccable.md`.

## Playwright / headless preview

Playwright blocks `file://` URLs. Serve first:

```sh
python3 -m http.server 8080
# then navigate to http://localhost:8080/index.html
```
