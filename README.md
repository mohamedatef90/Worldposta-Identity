# WorldPosta Identity

Static, single-file HTML pages for the WorldPosta operator platform: a long-form, deck-style product overview aimed at telecom and ISP decision-makers and technical evaluators (see `PRODUCT.md`). There is no build step, package manager, or framework; each HTML file is self-contained with inline CSS and JavaScript.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The main page, titled "WorldPosta - Operator Platform Proposal". Fixed sidebar navigation, a reading-progress indicator, an ecosystem diagram with a full-screen view, product cards that open into detail dialogs, and in-card product mockups. |
| `comparison-options.html` | Design exploration: "Eighteen ways to animate the comparison" cards. |
| `start-options.html` | Design exploration: "Get Started CTA" animation options. |
| `index.html.pre-magicblack.bak` | Backup of an earlier version of `index.html`. |
| `assets/WP icon.svg` | Icon asset. |
| `PRODUCT.md` | Audience, purpose, brand personality, and design principles. |
| `DESIGN.md` | Design system: colors, typography, and component notes. |
| `AUDIT.md` | Code-level design audit of `index.html` (dated June 28, 2026). |
| `CLAUDE.md` | Guidance for AI coding assistants working in the repo. |

## Sections of `index.html`

`intro`, `overview`, `opportunity`, `provide`, `stacks`, `cloud`, `collab`, `operations`, `about`, `security`, `operated`, `brand`, `sectors`, and `start`.

## Viewing locally

Open `index.html` in a browser, or serve the folder with any static server, for example:

```bash
python3 -m http.server 8000
```

then visit `http://localhost:8000/`. The pages load web fonts from Google Fonts, so an internet connection is needed for the intended typography.

## Design

The design system is described in `DESIGN.md` (named "WorldPosta Identity"); its colors are defined there (ink, navy, green, lime). The product brief and design principles are in `PRODUCT.md`.
