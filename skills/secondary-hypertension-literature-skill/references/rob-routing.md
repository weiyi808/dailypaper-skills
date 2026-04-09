# Risk-of-Bias Tool Routing — Secondary Hypertension Reviews

Load this module during Stage 4. Select the correct RoB tool based on study design.

---

## Tool Selection Decision Tree

```
What is the study design?
│
├── Randomized Controlled Trial (RCT)
│   └── Use: RoB 2 (Cochrane Risk of Bias tool, version 2)
│
├── Non-randomized study of interventions (NRSI)
│   (e.g., controlled before-after, interrupted time series, comparative cohort)
│   └── Use: ROBINS-I (Risk Of Bias in Non-randomized Studies of Interventions)
│
├── Observational study — Cohort or Case-Control
│   └── Use: Newcastle-Ottawa Scale (NOS)
│       - Cohort NOS: 3 domains (Selection, Comparability, Outcome)
│       - Case-control NOS: 3 domains (Selection, Comparability, Exposure)
│
├── Cross-sectional / Prevalence study
│   └── Use: JBI Critical Appraisal Checklist for Prevalence Studies (10 items)
│
├── Diagnostic Accuracy Study
│   └── Use: QUADAS-2 (Quality Assessment of Diagnostic Accuracy Studies, version 2)
│       - 4 domains: Patient selection, Index test, Reference standard, Flow and timing
│
└── Case Series (≥ 5 cases)
    └── Use: JBI Critical Appraisal Checklist for Case Series (10 items)
        Note: Case series are at high risk of bias by design; GRADE certainty will be Very Low
```

---

## RoB 2 — Key Domains for Secondary Hypertension RCTs

| Domain | Common Issues in Secondary HTN Trials |
|--------|--------------------------------------|
| D1: Randomization | Many trials in this domain have unclear allocation concealment |
| D2: Deviations from intended interventions | Open-label designs are common (adrenalectomy, stenting) — analyze ITT |
| D3: Missing outcome data | Lost to follow-up with RAAS inhibitor withdrawal |
| D4: Measurement of outcome | BP outcomes: self-reported vs. ABPM vs. office — blinding of outcome assessment matters |
| D5: Selection of reported result | Selective reporting of short-term vs. long-term BP outcomes |

**Judgment:** RoB 2 produces a judgment per domain and an overall judgment (Low / Some Concerns / High) per outcome.

---

## ROBINS-I — Key Domains for Surgical vs. Medical Comparisons

Particularly relevant for: adrenalectomy vs. MRA in PA; renal artery stenting vs. medical therapy.

| Domain | Common Issues |
|--------|--------------|
| Pre-intervention: Confounding | Indication bias — who gets surgery is not random; sicker patients may get medical tx |
| Pre-intervention: Selection of participants | Inclusion based on post-treatment workup creates selection bias |
| At intervention: Classification of interventions | AVS result used to classify PA subtype but AVS not always done |
| Post-intervention: Deviations from intended interventions | Crossover between surgical and medical arms common |
| Post-intervention: Missing data | Follow-up loss higher in older PA studies |
| Post-intervention: Measurement of outcomes | BP measurement method varies (office vs. ABPM) |
| Post-intervention: Selection of the reported result | Outcomes selected post-hoc; cure definitions not standardized |

---

## NOS — Newcastle-Ottawa Scale for Observational Studies

### Cohort Studies (maximum 9 stars)

**Selection (4 stars):**
1. Representativeness of exposed cohort ★
2. Selection of non-exposed cohort ★
3. Ascertainment of exposure ★
4. Demonstration that outcome of interest was not present at start ★

**Comparability (2 stars):**
5. Comparability of cohorts on basis of design or analysis ★★ (key confounders adjusted)

**Outcome (3 stars):**
6. Assessment of outcome ★
7. Follow-up long enough for outcomes to occur ★
8. Adequacy of follow-up ★

**Threshold for "low risk":** ≥ 7 stars

---

## QUADAS-2 — Diagnostic Accuracy Studies

Most relevant for: ARR sensitivity/specificity for PA, metanephrine sensitivity for PPGL, AHI diagnostic threshold for OSA.

| Domain | Key Signaling Questions | Secondary HTN–Specific Issues |
|--------|------------------------|-------------------------------|
| Patient selection | Consecutive enrollment? Avoided inappropriate exclusions? | Many PA studies exclude hypokalemic patients — spectrum bias |
| Index test | Interpreted without reference standard knowledge? | ARR threshold varies across labs; assay standardization needed |
| Reference standard | Classified correctly? | AVS gold standard for PA; not always used consistently |
| Flow and timing | Appropriate interval between index and reference? | Captopril challenge timing affects ARR results |

---

## Reporting RoB in the Manuscript

- Present RoB summary in a figure (traffic-light plot for RoB 2; bar chart for NOS distribution)
- Always describe RoB findings in the Results section before synthesis
- Do NOT omit high-RoB studies from meta-analysis; instead, run sensitivity analysis excluding them
- In the Discussion, acknowledge RoB limitations and link explicitly to GRADE certainty downgrades
