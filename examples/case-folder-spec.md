# Example Case Folder Spec

This repository does not include real clinical cases.

Use the following neutral folder pattern when preparing a local test case:

```text
sample-case/
├── notes/
│   ├── admission-summary.md
│   └── timeline-notes.md
├── reports/
│   ├── pathology-report.pdf
│   ├── endoscopy-report.pdf
│   └── discharge-summary.pdf
├── imaging/
│   ├── 2026-01-15-ct/
│   ├── 2026-02-10-mri/
│   └── 2026-03-02-followup-ct/
├── rough-deck/
│   └── rough-outline.pptx
└── literature/
    └── topic-notes.md
```

Recommended naming rules:

- keep dates in `YYYY-MM-DD`
- group images by examination session
- separate endoscopy and pathology source materials when possible
- include a rough PPT only if it helps preserve the original clinical logic

Minimum information the skill needs to finish well:

- general status and chief complaint
- key diagnostic examinations
- stage or disease assessment
- treatment sequence
- core teaching point
