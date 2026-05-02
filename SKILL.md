---
name: case-report-ppt
description: Build surgical case report decks from a mixed case folder that may include text records, PDFs, lab reports, pathology reports, CT/MRI images, operative notes, follow-up materials, literature notes, or an existing rough PPT. Use when Codex needs to turn real clinical case materials into a structured case-report presentation, ask focused follow-up questions, generate a disease-course timeline, organize imaging and pathology slides, and output a magazine-style single-file HTML web deck using the bundled guizang presentation engine instead of a user-provided PPT template.
---

# Case Report PPT

Build a clinically coherent case-report deck from mixed source materials. Keep the medical logic from the case workflow, but render the final presentation with the bundled guizang magazine-style web PPT engine.

## Output Model

Default output is a **single-file HTML horizontal-swipe deck**, not a template-based `.pptx`.

Expected delivery:

- `ppt/index.html` generated from the bundled guizang template
- `ppt/images/` for case images and generated visuals
- an extracted case summary for review
- a missing-information checklist
- a timeline visual or timeline section
- a short note of assumptions made

If the user provides an existing PPT, treat it as a **content source** only. Do not inherit its visual template.

## Locked Capabilities

After integrating guizang, keep these capabilities as part of the skill contract. Do not silently drop them in later revisions:

- three-level typography split:
  - serif for large titles and key quotations
  - sans-serif for body text and clinical explanation
  - monospace for metadata, dates, labels, and chrome
- WebGL fluid or dispersion background:
  - visible and expressive on hero sections
  - restrained on body sections to preserve readability
- horizontal deck navigation:
  - keyboard left and right arrows
  - mouse wheel
  - touch swipe
  - bottom dots
  - ESC index behavior from the integrated template
- five preset themes only:
  - Ink Classic
  - Indigo Porcelain
  - Forest Ink
  - Kraft Paper
  - Dune
- ten supported layout families:
  - hero cover
  - act divider
  - big-number spread
  - left-text right-image
  - image grid
  - pipeline
  - suspense question
  - big quote
  - before/after comparison
  - lead-image mixed editorial layout
- optional Codex image-generation flow:
  - documentary photo
  - infographic
  - pipeline diagram
  - system relationship diagram
  - UI scene image
  - all inserted to match guizang slot ratios
- single-file HTML delivery:
  - no build step
  - no server requirement
  - open directly in a browser

## Quick Start

1. Inspect the case folder and inventory all text, image, pathology, imaging, and follow-up materials.
2. Detect whether there is:
   - enough material to build a fresh deck
   - an existing PPT worth mining for structure or wording
   - usable images that should be placed directly into `ppt/images/`
3. Build a new magazine-style web deck by default. Do not ask for or depend on a PPT template.
4. Extract the required clinical fields.
5. Ask only decision-critical follow-up questions.
6. Build the deck in disease-course order.
7. Generate the timeline near the end of the workflow.
8. Add guideline and recent-literature discussion for the teaching point.
9. QA chronology, staging, pathology wording, image captions, theme rhythm, navigation behavior, and visual overflow before finishing.

## Required Clinical Fields

Do not finalize the deck until these fields are either extracted confidently or confirmed by the user:

1. General patient status, including chief complaint and present illness
2. Key outside-hospital examination results
3. Key in-hospital tests, imaging conclusions, and endoscopic pathology when relevant
4. Stage or disease assessment
5. Admission diagnosis
6. Treatment course
7. Treatment-problem discussion points
8. Full-course timeline summary
9. Core teaching point

Label each field as:

- `high` confidence: safe to use directly
- `medium` confidence: use in draft, request confirmation
- `low` confidence: stop and ask before finalizing

If sources conflict on diagnosis, staging, pathology, timeline, or treatment sequence, drop the field to `low`.

## Follow-Up Question Policy

Ask as few questions as possible. Avoid open-ended prompts.

### Must Ask

Pause and ask when any of these are missing or conflicted:

- the main teaching point
- the current MDT or presentation question
- the authoritative stage or disease assessment
- the main reporting focus when there are multiple treatment phases
- the preferred imaging or pathology figure when several candidates exist
- whether patient-identifying information must be removed

### Extract Then Confirm

Prefer short confirmation prompts for:

- chief complaint and present illness
- outside-hospital key examinations
- in-hospital imaging conclusions
- endoscopy and pathology wording
- admission diagnosis
- treatment sequence and date anchors
- recurrence or progression timepoints
- regimen names, drug names, and operation names
- the generated full-course timeline

### Can Default

Do not block the first draft for:

- cover wording style
- one-slide versus multi-slide treatment subsections
- one-slide versus two-slide literature discussion
- default imaging grid choice
- default timeline style
- formal versus shorter section-title wording

## Narrative Order

Build the presentation around disease evolution and treatment progression, not a generic report order.

For medical case reports, prefer **one page = one clearly stated clinical question or evidence block**.
Do not compress two different discussion goals into one section just to reduce page count.

Default narrative sequence:

1. General patient status, including chief complaint and present illness
2. Key outside-hospital examination results
3. Key in-hospital tests, imaging findings, and GI endoscopy pathology when present
4. Stage or disease assessment
5. Admission diagnosis
6. Treatment course
7. Discussion of treatment difficulties, bottlenecks, or decision points
8. If there is a new treatment phase, repeat the cycle of re-check, re-analysis, re-diagnosis, treatment, and problem discussion
9. Timeline summary of the full disease course
10. Core teaching point plus guideline and recent-literature discussion

Allow repeated treatment cycles in advanced, recurrent, or multi-phase disease. Do not force everything into one linear treatment block.

When a case contains dense diagnostic material, prefer this expanded pattern:

1. general status
2. disease-onset clue
3. endoscopy
4. pathology or molecular result
5. key imaging
6. initial diagnosis
7. first MDT question

Do not merge items `3` to `7` onto one overloaded section if that harms clarity.

Place the `core case question` or `core teaching-point discussion` near the end of the deck, usually on the penultimate section after the factual disease course has already been presented.

## Presentation Engine

Use the bundled guizang web-PPT resources:

- [guizang-template.html](assets/guizang-template.html)
- [components.md](references/guizang/components.md)
- [layouts.md](references/guizang/layouts.md)
- [themes.md](references/guizang/themes.md)
- [checklist.md](references/guizang/checklist.md)
- [image-prompts.md](references/guizang/image-prompts.md)

Workflow:

1. Copy `assets/guizang-template.html` to the target `ppt/index.html`.
2. Create `ppt/images/`.
3. Replace the required title placeholder immediately.
4. Preserve the integrated typography system:
   - serif for main titles and editorial emphasis
   - sans-serif for body copy
   - monospace for chrome and metadata
5. Keep WebGL hero behavior from the integrated template:
   - stronger background visibility on hero sections
   - restrained overlays on content sections
6. Choose one bundled guizang theme preset. Do not invent custom hex colors.
7. Choose layouts from `references/guizang/layouts.md` instead of hand-authoring every section from scratch.
8. Preserve browser-native horizontal navigation from the integrated template.
9. Run the guizang checklist before delivery.

Use the user’s existing PPT only as source material for structure or wording. Do not inherit its design language.

## Theme Rule

Do not use user-provided PPT templates anymore.

Instead:

- recommend one of the guizang preset themes from `references/guizang/themes.md`
- keep one theme for the whole deck
- do not mix preset palettes
- do not accept arbitrary user-supplied hex palettes unless the user explicitly asks to override the integrated workflow

Choose the theme that best matches the case tone:

- cleaner and more formal for MDT or academic review
- more dramatic only when the case genuinely benefits from that rhythm

Do not remove any of the five preset themes from the skill inventory. The default recommendation can vary by case, but the skill should continue to support all five.

## Medical Layout Rule

Read [medical-layout-rules.md](references/medical-layout-rules.md) for the case-report-specific rules that sit on top of the guizang engine:

- imaging grouping
- pathology and endoscopy page rules
- timeline logic
- cover-image behavior
- magazine-style constraints for medical content
- optional image-generation placement rules

If a guizang layout conflicts with medical clarity, prioritize medical clarity.

When choosing page structure, keep support for all ten layout families from the integrated guizang workflow, even if a specific case uses only a subset.

## Timeline Rule

Treat the timeline as a core artifact, not an optional decoration.

Use the horizontal milestone timeline by default.

Recommend the multi-track timeline for complex oncology or recurrent-disease cases:

- one main time axis with parallel tracks
- tracks may include examination or imaging, diagnosis or staging, treatment, and response or recurrence

When a visual timeline is needed, use image generation or diagram-like composition that fits the guizang style. Keep it formal, readable, and medically precise.

## Cover Rule

If appropriate, generate a cover image based on the report title:

- keep it suitable for formal clinical or academic presentation
- match the disease topic or organ system
- fit the guizang “editorial magazine” tone rather than generic corporate slides
- use it as background or side support without hurting title readability

Fallback to a clean typography-led cover when image generation is distracting or unnecessary.

When generating supplemental visuals elsewhere in the deck, prefer the bundled `image-prompts.md` patterns and keep ratios aligned with the target layout slot.

Supported generated-visual categories include:

- documentary-style clinical atmosphere images
- infographics
- pipelines or flow diagrams
- system relationship diagrams
- UI or workspace scene images

## Guideline And Literature Rule

Include guideline and recent-literature support in the first version of the deck.

Use this section to:

- support the final teaching point
- support key treatment-decision discussion points
- compare the actual case pathway with recommended strategies

Prioritize:

1. authoritative guidelines
2. recent high-value literature

Make the distinction clear between:

- guideline recommendations
- literature evidence
- case-specific inference

Because this content is time-sensitive, verify it live during actual deck generation.

## QA

Check for:

- chronology consistency
- staging consistency
- pathology wording consistency
- duplicated section intent
- missing conclusion or teaching-point section
- mismatch between images and captions
- obvious placeholder text
- unreadably dense content
- layout overflow or crowding
- broken guizang class usage
- poor theme rhythm across consecutive sections
- missing serif/sans/mono typography separation
- broken WebGL hero/body contrast
- broken horizontal navigation behavior
- missing theme-preset consistency
- output that requires a server or build step

If imaging across different timepoints should be compared on one page, suggest that during revision rather than forcing it in the first pass.
