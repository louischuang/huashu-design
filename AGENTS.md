# AGENTS.md

This repository provides **Huashu Design**, a design-oriented skill package for agents that generate high-fidelity visual deliverables using HTML, React, CSS, and lightweight scripts.

It is intended for agents such as Codex, ChatGPT, Cursor, Claude Code, OpenClaw, or similar systems that can read repository instructions and execute local scripts.

## What this repo is for

Use this repo when the task is primarily about **visual design output created in HTML**, not production web engineering.

Typical valid tasks:
- High-fidelity interactive prototypes
- HTML slide decks and presentation pages
- Motion demos and animated explainers
- Design direction exploration with variations
- Visual review / critique of interface concepts
- iOS / Android / browser-window mockups
- HTML-to-PDF / HTML-to-PPTX export workflows

Avoid using this repo as the first choice for:
- Production frontend apps
- Backend-connected systems
- SEO websites
- CRUD dashboards meant for deployment
- General JavaScript debugging unrelated to design output

## Fast routing

Before doing any work, classify the task into one of these buckets.

### 1. Prototype / app mockup
Read first:
- `SKILL.md`
- `references/workflow.md`
- `references/react-setup.md`
- `assets/ios_frame.jsx` or `assets/android_frame.jsx`
- `references/verification.md`

Typical output:
- Self-contained HTML prototype
- Multiple screens in overview layout, or a clickable flow demo

### 2. Slide deck / presentation
Read first:
- `SKILL.md`
- `references/slide-decks.md`
- `assets/deck_index.html`
- `assets/deck_stage.js`
- `references/editable-pptx.md`

Typical output:
- Multi-page HTML slide deck
- Optional PDF export
- Optional editable PPTX export if constraints are satisfied

### 3. Animation / motion demo
Read first:
- `SKILL.md`
- `references/animation-pitfalls.md`
- `references/animation-best-practices.md`
- `references/animations.md`
- `assets/animations.jsx`
- `references/video-export.md`
- `references/audio-design-rules.md`

Typical output:
- HTML animation
- MP4 / GIF export pipeline
- BGM + SFX when appropriate

### 4. Design exploration / style recommendation
Read first:
- `SKILL.md`
- `references/design-styles.md`
- `references/design-context.md`
- `assets/showcases/INDEX.md`

Typical output:
- 3 differentiated design directions
- Optional demo variations or screenshots

### 5. Design critique / review
Read first:
- `SKILL.md`
- `references/critique-guide.md`

Typical output:
- Scored critique
- Keep / Fix / Quick wins

## Agent operating rules

### Confirm facts before design
If the task mentions a specific product, company, SDK, device, release, or post-2024 versioned technology, verify the facts first using available search/browsing tools.

Do not assume:
- whether a product exists
- whether it has launched
- current version numbers
- current specs
- current brand assets

### Prefer real brand assets over generic design substitutes
If the task involves a real brand or product, try to gather:
1. logo
2. product images or official renders
3. UI screenshots if digital product
4. color palette
5. typography references

Do not silently replace missing brand assets with generic “tech-looking” shapes unless the user explicitly accepts placeholders.

### Default to honest placeholders instead of fake content
If real content is unavailable:
- use clearly labeled placeholders
- state assumptions in the HTML/comments or response
- avoid fake metrics, fake quotes, fake product facts, and decorative junk

### Variations are usually better than one “final” answer
For ambiguous or design-led tasks, prefer producing 2–3 differentiated directions rather than pretending one option is obviously correct.

### The medium is HTML, but the artifact should not feel like a generic webpage
The repo uses HTML as a production tool. Depending on task type, embody the correct discipline:
- slide designer
- product designer
- motion designer
- prototype designer
- information designer

## Recommended execution sequence

1. Classify the task
2. Verify external facts if needed
3. Read only the task-relevant reference files
4. Ask focused clarifying questions if the brief is materially ambiguous
5. Build a junior pass first when scope is non-trivial
6. Produce the full artifact
7. Run visual verification
8. Export derivatives if requested

## Common commands

These commands may require local dependencies.

### Visual verification
```bash
python scripts/verify.py path/to/design.html
python scripts/verify.py path/to/design.html --viewports 1920x1080,375x667
python scripts/verify.py path/to/deck.html --slides 10
```

### Export deck to PDF
```bash
node scripts/export_deck_pdf.mjs --slides ./slides --out ./out/deck.pdf
```

### Export deck-stage deck to PDF
```bash
node scripts/export_deck_stage_pdf.mjs --in ./deck.html --out ./out/deck.pdf
```

### Export deck to editable PPTX
```bash
node scripts/export_deck_pptx.mjs --slides ./slides --out ./out/deck.pptx
```

### Render animation video
```bash
node scripts/render-video.js --in ./demo.html --out ./out/demo.mp4
bash scripts/convert-formats.sh ./out/demo.mp4
bash scripts/add-music.sh ./out/demo.mp4
```

## Environment expectations

This repo mixes JavaScript and Python helper scripts.

Expected tools may include:
- Node.js
- Python 3
- Playwright / Chromium
- pptxgenjs
- sharp
- pdf-lib
- ffmpeg

If the environment is missing dependencies, report that clearly and continue with the highest-value artifact you can still produce.

## Deliverable standards

Prefer descriptive filenames such as:
- `AI Product Pitch Deck.html`
- `Habit Tracker Overview Prototype.html`
- `Pocket Launch Animation v2.html`

For multi-iteration work, preserve previous versions rather than overwriting without trace.

Always validate the final HTML visually before handing it off.

## Recommended future repo improvements

This repo is strong but broad. For better agent reliability, maintainers should consider:
- keeping `SKILL.md` as a thin routing layer
- moving deep philosophy and long guidance into `references/`
- adding explicit dependency manifests (`package.json`, `requirements.txt`)
- separating core / slides-motion / prototyping into sub-skills if scope keeps growing

