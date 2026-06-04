# Brand Guideline — Claude Code Skill

A Claude Code skill that walks you through creating a single-file HTML brand guideline, modeled on the **Becoming Quotient (BQ)** brand book. Produces a polished three-tab guideline (Visual Identity / Brand Strategy / Verbal Identity) and optionally publishes it to GitHub Pages.

## What you get

- **One self-contained HTML file** with a sidebar, three tab pages, sub-nav per tab, and a live-updating footer
- **Brand-safe theming** — your colors, your fonts, your palette
- **CDN-hosted images** via jsDelivr (no base64 bloat)
- **Live version counter** — pulls commit count + last-updated date from your GitHub repo
- **Optional one-click publish** to GitHub Pages via `gh` CLI

## Install

From a Claude Code session:

```
/plugin marketplace add EverythingDesign/Brand-Guidelines
/plugin install brand-guideline@everything-design-skills
```

## Use

Once installed, in any Claude Code session say:

> "create a new brand guideline"

or

```
/brand-guideline
```

The skill will ask a guided sequence of questions (brand basics → visual → strategy → verbal → publishing) and produce the HTML.

## GitHub publishing

If your `gh` CLI isn't authenticated, the skill will point you at **Saurabh — saurabh@everything.design** to get GitHub access set up.

## Reference

The skill ships with `template-reference.html` — the original BQ build — as the architectural reference. See the live version: <https://everythingdesign.github.io/Brand-Guidelines/Becoming%20Quotient/>

## Built by

[Everything Design](https://www.everything.design/) — `hello@everything.design`
