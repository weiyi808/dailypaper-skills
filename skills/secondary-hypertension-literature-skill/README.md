# Secondary Hypertension Literature Writing Skill

A specialized, publication-grade skill for writing literature reviews and systematic reviews on secondary hypertension. Built on top of the `medical-meta-analysis-writing` methodology and `literature-review-skill` framework, with domain-specific clinical content for all major secondary hypertension subtypes.

## Covered Subtypes

- Primary Aldosteronism (PA)
- Renovascular Hypertension (RVH)
- Renal Parenchymal Hypertension
- Pheochromocytoma / Paraganglioma (PPGL)
- Cushing Syndrome
- Obstructive Sleep Apnea (OSA)
- Thyroid Disorders
- Drug-Induced Hypertension
- Coarctation of Aorta
- Monogenic Hypertension Syndromes

## Installation

### Claude Code (recommended)
```bash
git clone <repo-url> ~/.claude/skills/secondary-hypertension-literature-skill
```

### Cursor
```bash
git clone <repo-url> .cursor/rules/secondary-hypertension-literature-skill
```

### Universal (.agents path)
```bash
git clone <repo-url> ~/.agents/skills/secondary-hypertension-literature-skill
```

## Usage

Open a new session and type:

```
/secondary-hypertension-literature-skill Write a systematic review on primary aldosteronism treatment
/secondary-hypertension-literature-skill Help me draft a JAMA-style review on renovascular hypertension
/secondary-hypertension-literature-skill 帮我写一篇关于继发性高血压的文献综述
```

## Workflow Stages

1. **Topic Framing** — PICO/PECO construction, review type declaration
2. **Search Strategy** — Database selection, MeSH terms, Boolean logic
3. **PRISMA Screening** — Title/abstract + full-text screening with exclusion logging
4. **Data Extraction + RoB** — Standardized extraction, RoB tool routing
5. **Evidence Synthesis + GRADE** — Meta-analysis or narrative synthesis, certainty assessment
6. **Manuscript Drafting** — JAMA-style front matter, IMRAD body
7. **Submission Audit** — PRISMA checklist, reviewer simulation, cover letter

## File Structure

```
secondary-hypertension-literature-skill/
├── SKILL.md                                  # Main skill — invoke with /secondary-hypertension-literature-skill
├── README.md                                 # This file
├── references/
│   ├── sh-subtypes-knowledge.md             # Clinical knowledge base for each subtype
│   ├── protocol-module.md                   # PICO/PECO templates and protocol checklist
│   ├── search-strategy-templates.md         # Subtype-specific MeSH terms + Boolean logic
│   ├── grade-synthesis-guide.md             # GRADE rules, SoF table template
│   ├── manuscript-writing-guide.md          # JAMA-style templates for each section
│   ├── rob-routing.md                       # Risk-of-bias tool selection decision tree
│   └── submission-audit-checklist.md        # Pre-submission PRISMA + statistical audit
└── assets/
    ├── prisma-flow-template.md              # PRISMA 2020 flow diagram data entry
    └── data-extraction-sheet.md            # Standardized data extraction form
```

## Methodology Anchors

- **Reporting:** PRISMA 2020
- **Synthesis:** Cochrane Handbook principles
- **RoB tools:** RoB 2 (RCTs), ROBINS-I (NRSI), NOS (observational), QUADAS-2 (diagnostic)
- **Certainty:** GRADE framework
- **Manuscript style:** JAMA

## License

MIT
