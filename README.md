# case-report-ppt

A Codex skill for building surgical case-report presentations from mixed clinical source folders.

## What It Does

- ingests mixed case materials such as notes, PDFs, pathology reports, imaging screenshots, and rough decks
- asks only decision-critical follow-up questions
- reorganizes content in disease-course order
- preserves medical clarity with a one-question-per-page rule
- outputs a guizang-style single-file HTML web deck
- supports timeline generation, imaging grouping, pathology sections, and literature-backed discussion

## Output Model

Expected outputs for a case run:

- `ppt/index.html`
- `ppt/images/`
- case summary notes
- missing-information checklist
- timeline section or timeline visual

## Included Skill Assets

- `SKILL.md`
- `agents/openai.yaml`
- `assets/guizang-template.html`
- `assets/motion.min.js`
- `references/medical-layout-rules.md`
- `references/guizang/*.md`

## Privacy

This repository intentionally excludes:

- real patient case folders
- generated decks from real cases
- patient names or identifiers
- author names
- hospital or unit names

## Notes

The skill is designed for local Codex usage and assumes the bundled guizang-style HTML template workflow.
