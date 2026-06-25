---
name: brand-guideline
description: Create a single-file HTML brand guideline (Visual Identity + Brand Strategy + Verbal Identity tabs) with the BQ-style three-tab layout, sidebar sub-nav, footer with live version counter, and optional GitHub Pages publishing. Trigger when the user says "create brand guideline", "new brand guidelines", "set up brand book", "brand identity site", or wants a multi-section single-page brand doc like the BQ (Becoming Quotient) one.
---

# Brand Guideline Builder

Produce a single self-contained HTML file with three tabs — **Visual Identity**, **Brand Strategy**, **Verbal Identity** — matching the BQ Brand Guidelines architecture (see `template-reference.html` in this skill folder for a working example).

The output is **one HTML file** that:
- Sidebar with three icon tabs (lightbulb / megaphone / eye) and inline sub-nav per tab
- Tab order is **Brand Strategy, Verbal Identity, Visual Identity** — and **Brand Strategy is the default landing tab** (the page boots to it when there's no URL hash)
- Visual Identity rendered natively in the page; its sub-sections run **01 Logo · 02 Catchphrase · 03 Typography · 04 Colour · 05 Image treatment · 06 Construction · 07 Don'ts**
- Brand Strategy + Verbal Identity rendered in iframes via inlined JS Blob URLs (keeps styles/IDs isolated)
- Raster section images served from a GitHub CDN (jsDelivr) — NOT embedded as base64. Logo + catchphrase assets are committed as real files in `logos/` and `catchphrase/` subfolders and referenced via **same-origin relative paths** (so the per-pane download buttons save directly)
- Each logo and catchphrase preview pane carries its own **PNG + SVG download buttons** in the top-right corner
- **No italics anywhere** — a global `i, em { font-style:normal }` reset plus no `font-style:italic` declarations
- Unified footer: `<Brand> Brand Guidelines    Branding Partner: Everything Design` + live version (GitHub commit count) + last-updated date

---

## Phase 1: Gather requirements

Before writing anything, ask the user the questions below. Use the `AskUserQuestion` tool, grouped into 2–4 questions per round. Wait for answers; don't assume.

### Round 1 — Brand basics
1. **Brand name** (used in title, sidebar, footer) — e.g. "Becoming Quotient", "BQ"
2. **Short tagline / sub-label** for sidebar (under the logo) — e.g. "Brand guideline"
3. **Which tabs to include?** — `Visual Identity`, `Brand Strategy`, `Verbal Identity` (any combination; default = all three). If a tab is excluded, drop its sidebar entry entirely.

### Round 2 — Visual identity (skip if tab excluded)
4. **Primary brand color (hex)** — accent / active state — e.g. `#022781`
5. **Background color (hex)** — page bg — e.g. `#F7F6F2`
6. **Ink / text color (hex)** — primary text — e.g. `#1A1A1A`
7. **Display font** (headings) — e.g. `P22 Mackinac`. Ask if they have it as a `.otf`/`.ttf`/`.woff2` file, a Google Fonts URL, or want a fallback only.
8. **Body font** (paragraphs / UI) — e.g. `Indivisible`. Same options.
9. **Logo files** — ask user to provide the logo image(s) — file paths or URLs, **PNG + SVG for each**. For BQ the set is TM (full lockup), Shorthand (bq monogram), and Expanded (wordmark), each in Blue / Black / White. These get committed to a `logos/` subfolder and power the per-pane PNG/SVG download buttons.
10. **Construction & don'ts images** — optional reference shots for "logo construction" + "what not to do" sections.
11. **Extended palette swatches** — list of name + hex pairs beyond the primary.

### Round 3 — Brand strategy (skip if tab excluded)
12. **Core concept** — what is the brand belief? (1–2 sentences)
13. **Brand belief** — the strategic foundation (1 sentence)
14. **Brand narrative** — the story the brand tells (2–3 sentences)
15. **Brand purpose** — why the brand exists
16. **Brand vision** — the world it's building
17. **Brand mission** — what it does
18. **Customer transformation** — from → to states for each key audience
19. **Brand manifesto** — the long stanza-form belief piece
20. **Tone of voice pairs** — e.g. "Measured, not inflated" with one-line explainers

### Round 4 — Verbal identity (skip if tab excluded)
21. **Voice principles** — 3–5 short rules
22. **Tone modes** — situational tone variants
23. **Style choices** — punctuation, capitalisation, oxford comma, etc.
24. **Sentence structure** — short/long, active/passive rules
25. **Sample lines** — 5–10 brand-aligned reference lines
26. **Microcopy** — buttons, errors, empty states
27. **Word choices** — preferred / avoided word lists

### Round 5 — Publishing
28. **Push to GitHub?** Yes / No / Local-only
29. If yes: **target repo** (`org/repo`) and **folder name** inside it (e.g. "Becoming Quotient")
30. If yes: **enable GitHub Pages** for the live URL? (recommended yes)

If the user can't answer some content questions (Brand Strategy / Verbal Identity often), offer a "Coming soon" placeholder for that tab — the layout still works (see how BQ originally shipped with only Visual content and placeholder tabs for the others in `template-reference.html`).

---

## Phase 2: Build the file

Use `template-reference.html` in this skill folder as the architectural reference. **Do not blindly copy** — adapt the:
- CSS `:root` vars (`--bg`, `--ink`, `--accent`, font families)
- Sidebar logo image
- Tab labels, sub-nav `SECTIONS_BY_TAB` arrays
- Data constants inside each tab's `<script>` block (`LOGOS` + `LOGO_TREATMENTS` + `CATCHPHRASES` for visual marks, `S` for strategy, `V` for verbal, etc.)

Key implementation rules learned from the BQ build:

1. **Image hosting**: Never embed raster images as base64 — file gets huge. Save them as files, push to the GitHub repo. Two hosting modes:
   - **Section/photo images** (construction, don'ts, image-treatment) — link via jsDelivr: `https://cdn.jsdelivr.net/gh/{org}/{repo}@main/{folder}/{filename}` (URL-encode spaces as `%20`)
   - **Logo + catchphrase assets** — commit as real files into `{folder}/logos/` and `{folder}/catchphrase/` with web-safe names (`TM-Logo_Blue.svg`, `Stacked-Closed_Blue.png`, …) and reference them via **same-origin relative paths** (`logos/TM-Logo_Blue.svg`). Same-origin is required so the per-pane download buttons force a real save instead of opening the file. Provide both PNG and SVG for each.
1a. **Per-pane download buttons**: every logo and catchphrase preview card has a `.dl-pair` in its top-right with two `.logo-dl-btn` links (PNG + SVG) pointing at the same-origin files. Don't use a separate bottom "download strip" — the per-pane buttons replace it.
1b. **No italics**: keep the global `i, em { font-style:normal }` reset and never add `font-style:italic` (or `<i>`/`<em>` for styling). Emphasis is done with weight/colour, not slant.
1c. **Section + tab order**: nav tabs run Brand → Verbal → Visual with Brand as the default landing tab. Visual sub-sections run Logo → Catchphrase → Typography → Colour → Image treatment → Construction → Don'ts. Keep `SECTIONS_BY_TAB`, the `sec-num` labels, and the section block order all in sync.
2. **Iframe isolation**: Brand Strategy + Verbal Identity content lives inside iframes loaded via JS Blob URLs. This avoids ID/CSS collisions between the three docs. The orchestrator injects a `FRAME_SHIM` that hides the standalone doc's sidebar and adds the unified footer.
3. **Single tab orchestrator**: Only the merged shell may have `SECTIONS_BY_TAB`, `TAB_META`, `showTab`, `renderSubNav`. If you copy from a standalone doc's script, **strip** any duplicate definitions — they cause silent parse errors that break the page (font injection won't run).
4. **Brand fonts**: Inject via `@font-face` from a `FONTS = {...}` object with base64-encoded font URIs, then apply with CSS vars. The user must provide the font files; otherwise fall back to the closest system font (e.g. Georgia for serif display, system-ui for sans body) and note this clearly to the user.
5. **Unified footer** (all tabs):
   ```
   <Brand> Brand Guidelines              Branding Partner: Everything Design
   v1.<N> · Last updated <Date> · <relative-time>
   ```
   Version `N` = total commit count of the repo (fetched live via GitHub API `Link` header trick). Last-updated = latest commit's `author.date`. Relative time ticks every 30s. Fall back to "today" if API fails.
6. **Footer goes in three places**: native at end of Visual tab, injected via `FRAME_SHIM` into Brand iframe, injected via `FRAME_SHIM` into Verbal iframe. Hide the inner doc's own footer with `.content > .footer{display:none}`.
7. **No version tags outside the footer**: don't show `v1.0` in the sidebar header or side-foot — those drift out of sync.
8. **Match the brand palette, not reference mockups**: if the user shares a Figma/screenshot with off-brand colours (e.g. orange in an otherwise blue brand), use the brand palette from their CSS vars / token list, not the mockup colours. See `feedback-bq-brand-style` memory.

Generate the file as `<brand-slug>-brand-guidelines.html` in `~/Downloads/` (or the user's preferred output path).

---

## Phase 3: Publish to GitHub (if requested)

If user chose to push to GitHub:

1. **Check `gh` auth**: `gh auth status`. If not authenticated, instruct:
   > "GitHub CLI isn't authenticated on this machine. Please reach out to **Saurabh** at **saurabh@everything.design** to get connected, then re-run this skill."
2. **Verify repo access**: `gh repo view {org}/{repo}`. If repo doesn't exist, ask user if they want a new one created (`gh repo create`). If repo exists but is private, ask user if they want it made public (CDN won't work otherwise) — or use a separate public assets repo.
3. **Clone, add files**:
   - Create the `<folder-name>/` directory
   - Add the merged HTML as both `index.html` (for GitHub Pages root rendering) and `<brand-slug>-brand-guidelines.html` (clearly named for direct download)
   - Add section/photo images to the folder root; add logo + catchphrase PNG/SVG files into `<folder-name>/logos/` and `<folder-name>/catchphrase/` (referenced via same-origin relative paths so the download buttons work)
4. **Commit + push**:
   - Use a clear commit message like "Add <Brand> brand guidelines"
   - Author: use `git -c user.email=... -c user.name=...` if local git is unconfigured
5. **Enable GitHub Pages** if requested:
   ```bash
   gh api -X POST /repos/{org}/{repo}/pages -f "source[branch]=main" -f "source[path]=/"
   ```
   Poll status until "built" (typically ~30s). Verify the live URL returns 200.
6. **Report back**: give the user:
   - Repo URL: `https://github.com/{org}/{repo}/tree/main/{folder}`
   - Direct file URL: `https://github.com/{org}/{repo}/blob/main/{folder}/<brand-slug>-brand-guidelines.html`
   - **Live page URL** (GitHub Pages): `https://{org-lower}.github.io/{repo}/{folder}/` (spaces → `%20`)
   - CDN image base: `https://cdn.jsdelivr.net/gh/{org}/{repo}@main/{folder}/`

### GitHub not connected fallback

If `gh auth status` returns "not logged in" or the user explicitly says GitHub isn't set up, output exactly:

> The brand guideline HTML file is ready locally at `<path>`. To publish it to GitHub so the team can access it via a live URL and the images load from a CDN, please contact **Saurabh – saurabh@everything.design** to get GitHub access set up. Once connected, re-run this skill and choose "Push to GitHub".

---

## Phase 4: Wrap up

After publishing (or skipping publish), summarise:
- Local file path
- Live URL (if published)
- How to update content later (edit data constants in the HTML and re-push — the footer's version counter will auto-bump)
- Any tabs that shipped as "Coming soon" placeholders the user should fill in later

---

## Reference file

`template-reference.html` (same folder as this SKILL.md) is the working BQ build. Use it for:
- Exact CSS vars + responsive breakpoints
- Sidebar markup + SVG icons (eye/lightbulb/megaphone)
- Orchestrator JS (`showTab`, `renderSubNav`, FRAME_SHIM, live footer fetch)
- Data-constant shapes (`S`, `V`, `LOGOS`, `LOGO_TREATMENTS`, `CATCHPHRASES`, `CONSTRUCTION`, etc.)
- The `dlBtns()` helper + `.logo-dl-btn`/`.dl-pair` markup for per-pane PNG/SVG downloads

When the user wants different icons or tab names, change the labels in the sidebar + `TAB_META` + `SECTIONS_BY_TAB`, but keep the orchestration intact.
