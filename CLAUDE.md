# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static, single-file HTML marketing/identity pages for **WorldPosta's operator platform** — no build tooling, no package manager, no framework. Each `.html` file is fully self-contained (inline CSS + JS, no shared assets).

**Editing scope.** The active work target at the repo root is **`index.html`** — a product overview page with a fixed sidebar navigation, accordion product cards, and an orbit-hub diagram. Preview by opening directly in a browser or serving locally for Playwright: `python3 -m http.server <port>`.

## Sub-project: `.worldposta-provider-pitch/`

A separate pitch deck page lives in `.worldposta-provider-pitch/`. It has its own `CLAUDE.md` — **read that file first** before touching anything there. Key points from it:

- **`overview.html`** is the only editable file in that subproject. `overview_draft.html` and `presentation-F.html` are reference-only.
- Uses the **magic-black** design system (tokens, CDN libraries, motion lanes) documented in `DESIGN-SYSTEM.md`.
- Animation CDN stack: GSAP + ScrollTrigger (scroll owner), Motion (count-up / inView), anime.js v4 (SVG stroke-draw), lottie-web (medal). GSAP owns the scroll — don't add competing scroll listeners.

## Design systems — do not mix

| File | System | Canvas | Accent | Classes |
|---|---|---|---|---|
| `index.html` (root) | **legacy** | `#080E1C` | `#4A7830→#8BBF3C` | `.sec`, `.ey`, `.btn-p`, `.btn-g`, `.grad` |
| `.worldposta-provider-pitch/overview.html` | **magic-black** | `#0A1320` | `#7CB342→#A8CF38` | `.section`, `.eyebrow`, `.btn-primary`, no `.grad` |

Adding a new page: follow **magic-black** (not the root legacy system). Tokens and components are in `.worldposta-provider-pitch/DESIGN-SYSTEM.md`; the source skill is at `/Users/roaya/Downloads/skill/magic-black.skill`.

## Design context

Target audience: **telco / ISP executives** evaluating whether to run branded cloud/mail/security on their own infrastructure. Tone: **sovereign · precise · weighty**. Anti-references to avoid: generic SaaS landing pages, crypto/web3 neon, hyperscaler console clones, cheap reseller badge clutter.

Design principles and audience detail: `.worldposta-provider-pitch/.impeccable.md`.

## Playwright / headless preview

Playwright blocks `file://` URLs. Serve first:

```sh
python3 -m http.server 8080
# then navigate to http://localhost:8080/index.html
```
