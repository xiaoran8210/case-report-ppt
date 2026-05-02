# case-report-ppt

A Codex skill for turning mixed clinical case folders into structured surgical case-report web decks.

It is designed for real-world medical presentation workflows where the source materials are incomplete, mixed-format, and often contain multiple rounds of diagnosis, treatment, pathology, imaging, and follow-up.

## Highlights

- builds magazine-style single-file HTML case decks with the bundled guizang engine
- keeps medical reasoning first, not generic slide compression
- follows a one-question-per-page clinical presentation rule
- supports CT, MRI, endoscopy, pathology, timeline, and MDT discussion pages
- preserves a fixed typography and navigation system
- adds guideline and recent-literature support near the end of the deck

## Core Capabilities

- Serif cover titles, sans-serif body text, monospace metadata hierarchy
- WebGL or dispersion-style hero background with restrained content pages
- Horizontal navigation by keyboard, wheel, touch swipe, dots, and ESC index
- Five integrated themes:
  - Ink Classic
  - Indigo Porcelain
  - Forest Ink
  - Kraft Paper
  - Dune
- Ten layout families:
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

## What The Skill Expects

Typical source folders may contain:

- rough PPT or partial PPT
- admission notes or case summaries
- PDF reports
- pathology reports
- endoscopy screenshots
- CT or MRI screenshots
- follow-up materials
- literature notes

The skill treats an existing PPT as a content source, not a visual template.

## Output Model

Expected output for a case run:

- `ppt/index.html`
- `ppt/images/`
- case summary notes
- missing-information checklist
- timeline section or timeline visual
- short note of assumptions

No build step or server is required. The final deck opens directly in a browser.

## How It Works

1. Inventory the case folder.
2. Extract the required clinical facts.
3. Ask only decision-critical follow-up questions.
4. Rebuild the case in disease-course order.
5. Split overloaded content so each page answers one clear clinical question.
6. Add timeline, MDT reflection, and literature-backed teaching points.
7. QA chronology, staging, wording, image placement, and visual overflow.

## Medical Presentation Rules

This skill favors medical clarity over compression:

- do not merge general status with disease-onset clue
- do not merge initial diagnosis with first MDT question
- do not merge operative narrative with postoperative pathology if pathology matters clinically
- keep endoscopy, pathology, and key imaging separate when they answer different questions
- place the core teaching-point discussion near the end, usually on the penultimate section

Detailed rules live in:

- `references/medical-layout-rules.md`
- `references/guizang/`

## Repository Structure

```text
case-report-ppt/
├── SKILL.md
├── README.md
├── LICENSE
├── CHANGELOG.md
├── .gitignore
├── agents/
│   └── openai.yaml
├── assets/
│   ├── guizang-template.html
│   └── motion.min.js
├── references/
│   ├── medical-layout-rules.md
│   └── guizang/
│       ├── checklist.md
│       ├── components.md
│       ├── image-prompts.md
│       ├── layouts.md
│       └── themes.md
└── examples/
    └── case-folder-spec.md
```

## Installation

Copy this repository into your local Codex skills directory as:

```text
$CODEX_HOME/skills/case-report-ppt
```

Typical local result:

```text
~/.codex/skills/case-report-ppt
```

## Usage

Invoke the skill against a case folder and let it:

- scan the materials
- recommend a deck strategy
- ask for missing critical decisions
- generate the final HTML case deck

Typical intent:

```text
Use $case-report-ppt to build a surgical case report deck from this case folder.
```

## Example Input Folder Spec

See:

- `examples/case-folder-spec.md`

This file documents a recommended neutral folder structure for reusable testing and onboarding.

## Versioning

Current published baseline:

- `v0.1.0`

See:

- `CHANGELOG.md`

## Privacy

This repository intentionally excludes:

- real patient case folders
- generated decks from real cases
- patient names or identifiers
- author names
- hospital or unit names

## License

This repository is published under the MIT License.
