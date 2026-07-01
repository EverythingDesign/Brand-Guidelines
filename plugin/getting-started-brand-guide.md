# Getting Started — Building a Brand Guide with the Skill

A step-by-step guide for anyone on the team creating a new brand guideline from scratch using the **brand-guideline** Claude Code skill.

The skill produces a single self-contained HTML brand book — three tabs (Brand Strategy / Verbal Identity / Visual Identity), sidebar sub-nav, per-pane logo downloads, and a live-updating footer — modeled on the [Becoming Quotient (BQ) build](https://everythingdesign.github.io/Brand-Guidelines/Becoming%20Quotient/).

---

## 0. Prerequisites

- **Claude Code** installed and signed in.
- **GitHub access** to `EverythingDesign/Brand-Guidelines` — only needed if you're publishing to a live URL. If the `gh` CLI isn't set up on your machine, contact **Saurabh — saurabh@everything.design**.

## 1. Install the skill (one time)

In a Claude Code session:

```
/plugin marketplace add EverythingDesign/Brand-Guidelines
/plugin install brand-guideline@everything-design-skills
```

## 2. Gather the brand's materials first

Have these ready in a folder before you start — the skill will ask for them:

- **Logos** — PNG **and** SVG for each variant/color (e.g. full lockup, monogram, wordmark; in brand color / black / white).
- **Fonts** — `.otf` / `.ttf` / `.woff2` files, or Google Fonts URLs (one display font for headings, one body font).
- **Colors** — hex values for accent, background, and ink/text, plus any extended palette (name + hex pairs).
- **Photography / construction / don'ts images** (optional).
- **Copy** — brand strategy + verbal identity text. It's fine to leave a tab as a "Coming soon" placeholder and fill it later.
- **External links** for the sidebar (optional) — e.g. a shared Google Drive folder. Capture a label + URL for each.

## 3. Start the skill

In a new session, either say *"create a new brand guideline"* or run:

```
/brand-guideline
```

## 4. Answer the guided questions

The skill walks through rounds — **brand basics → visual identity → brand strategy → verbal identity → publishing**. Answer each in plain language. You can skip tabs or use placeholders where content isn't ready.

## 5. Publish (when asked)

Choose **push to GitHub** + **enable GitHub Pages** to get a live URL. The skill commits the files and returns the link. Choose **local-only** to skip publishing.

## 6. Update later

Edit the data constants in the generated HTML and re-push. The footer's version counter auto-bumps from the repo's commit count.

---

## Good to know

- **`template-reference.html`** (in `plugin/skills/brand-guideline/`) is the BQ build the skill copies its structure from. You don't edit it — the skill adapts it to the new brand.
- The **default architecture** is the BQ three-tab layout. Describe what you want in plain language and the skill adapts labels, colors, fonts, and content — but keeps the proven structure.
- Assets: raster section/photo images are CDN-hosted via jsDelivr; **logo + catchphrase files live in `logos/` and `catchphrase/` subfolders** and are referenced with same-origin paths so the per-pane PNG/SVG download buttons save directly.

## Links

- **Skill folder:** <https://github.com/EverythingDesign/Brand-Guidelines/tree/main/plugin/skills/brand-guideline>
- **Live BQ reference:** <https://everythingdesign.github.io/Brand-Guidelines/Becoming%20Quotient/>
- **Questions / GitHub access:** Saurabh — saurabh@everything.design

---

Built by [Everything Design](https://www.everything.design/) — `hello@everything.design`
