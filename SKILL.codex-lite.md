---
name: huashu-design
summary: Design-oriented HTML skill for prototypes, slide decks, motion demos, and visual exploration. Use for high-fidelity visual artifacts, not production frontend engineering.
when_to_use:
  - interactive prototype
  - app mockup
  - html slide deck
  - motion demo
  - design variations
  - visual critique
not_for:
  - production web app
  - backend integration
  - seo website
  - generic coding task
---

# Huashu Design — Codex-oriented skill entry

This skill turns HTML into a design medium.

Use it when the user wants polished visual output such as prototypes, decks, motion demos, or design explorations. Do not treat the task like generic frontend implementation unless the user explicitly wants deployable engineering.

## Core intent

You are acting as a designer who uses HTML, React, CSS, and lightweight scripts as production tools.

Depending on the task, embody the correct role:
- prototype designer
- UX / product designer
- slide designer
- motion designer
- information designer

Do not default to generic web tropes.

## First decision: classify the task

### A. Prototype / app mockup
Use for:
- iOS / Android mockups
- clickable flows
- overview boards
- product concepts

Read next:
- `references/workflow.md`
- `references/react-setup.md`
- `assets/ios_frame.jsx` or `assets/android_frame.jsx`
- `references/verification.md`

### B. Slide deck
Use for:
- pitch decks
- keynote-style presentations
- lecture slides
- HTML-based presentation systems

Read next:
- `references/slide-decks.md`
- `assets/deck_index.html`
- `assets/deck_stage.js`
- `references/editable-pptx.md`

### C. Motion / animation
Use for:
- explainers
- launch animations
- animated diagrams
- visual storytelling

Read next:
- `references/animation-pitfalls.md`
- `references/animation-best-practices.md`
- `references/animations.md`
- `references/video-export.md`
- `references/audio-design-rules.md`

### D. Design exploration / visual direction
Use for:
- “give me 3 directions”
- style recommendation
- brand expression exploration
- comparative visual studies

Read next:
- `references/design-styles.md`
- `references/design-context.md`
- `assets/showcases/INDEX.md`

### E. Design critique
Use for:
- “review this design”
- score / critique / what should improve

Read next:
- `references/critique-guide.md`

## Hard rule 1: verify real-world facts before designing around them

If the task mentions a specific product, company, device, SDK, model, launch, release, or version-sensitive technology, verify those facts first with available web/search tools.

Do not assume:
- existence
- release status
- version number
- product specs
- current brand state

If facts are unclear, say so and ask or verify before committing to a concept.

## Hard rule 2: real brand assets beat generic substitutions

When designing for a real brand or product, try to obtain:
1. logo
2. product render / product photography
3. UI screenshots if software product
4. palette
5. typography cues

Do not silently replace missing assets with generic tech visuals unless placeholders are explicitly acceptable.

## Hard rule 3: placeholder honesty

When real material is missing:
- use clearly labeled placeholders
- declare assumptions
- avoid fake numbers, fake stats, fake customer quotes, fake product claims

A clean placeholder is better than a low-quality fake implementation.

## Default workflow

1. Understand the request
2. Verify external facts if needed
3. Ask focused clarifying questions only when necessary
4. Read only the references needed for the task type
5. Draft a junior pass for non-trivial work
6. Build the full artifact
7. Validate visually
8. Export requested formats if needed

## Junior pass rule

For non-trivial work, do not jump straight into a polished final artifact.

First produce a lightweight directional pass containing:
- assumptions
- structure
- narrative or layout logic
- placeholders where content is missing

Then iterate toward the final version.

## Variation rule

When the brief is design-led or ambiguous, prefer 2–3 differentiated options rather than pretending there is one obviously correct answer.

Variation axes may include:
- information density
- typographic character
- layout rhythm
- motion language
- visual temperature

## Anti-slop rule

Avoid default AI design clichés unless the brand specifically calls for them:
- generic purple gradients
- emoji as filler iconography
- empty dashboard stats
- decorative SVG people or objects
- overused rounded-card SaaS layouts
- arbitrary accent colors invented on the spot

Every visual element should earn its place.

## Task-specific reminders

### Prototype reminders
- Ask whether the user wants overview layout or clickable flow when that distinction matters.
- Use device-frame assets rather than hand-building iPhone chrome.
- Prefer real imagery when imagery is content-bearing.
- Verify the final click-path using Playwright if possible.

### Slide reminders
- HTML slide deck is the source artifact.
- PDF or editable PPTX are derived outputs.
- If editable PPTX is required, follow `references/editable-pptx.md` from the start.
- For larger decks, establish the visual grammar on a small number of showcase slides before scaling.

### Motion reminders
- Read pitfalls before animating.
- Build with timeline logic, not random micro-interactions.
- Audio matters for polished motion exports.
- Use MP4/GIF export workflow only after the HTML motion piece is stable.

### Critique reminders
- Critique the work, not the creator.
- Provide concrete fixes.
- Prioritize issues by severity.

## Verification

Use visual validation before delivery.

Recommended tool:
```bash
python scripts/verify.py path/to/file.html
```

For decks:
```bash
python scripts/verify.py path/to/deck.html --slides 10
```

## Export helpers

Editable PPTX:
```bash
node scripts/export_deck_pptx.mjs --slides ./slides --out ./out/deck.pptx
```

Deck PDF:
```bash
node scripts/export_deck_pdf.mjs --slides ./slides --out ./out/deck.pdf
```

Animation render:
```bash
node scripts/render-video.js --in ./demo.html --out ./out/demo.mp4
```

## Output standards

Use descriptive filenames.
Preserve major iterations.
Keep task-relevant files grouped in one project folder.
Always review the visual result before handoff.

## Reading map

- `references/workflow.md` — intake and clarification
- `references/react-setup.md` — React/Babel setup rules
- `references/slide-decks.md` — deck architecture and production
- `references/editable-pptx.md` — editable PPTX constraints
- `references/animation-pitfalls.md` — avoid common motion failures
- `references/animation-best-practices.md` — motion language and pacing
- `references/design-styles.md` — style recommendation system
- `references/design-context.md` — fallback guidance when context is thin
- `references/critique-guide.md` — critique format
- `references/verification.md` — validation workflow

## Maintainer note

This file is intentionally thin.
Long-form philosophy, examples, and edge-case guidance should live in `references/` so agents can route into them on demand instead of loading everything at once.
