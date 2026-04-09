# Protocol Module — PICO/PECO Templates and Protocol Checklist

Load this module during Stage 1 of the secondary hypertension literature writing workflow.

---

## Choosing the Right Framework

| Review Type | Framework | When to Use |
|------------|-----------|-------------|
| Intervention (treatment/surgery) | **PICO** | Does treatment X improve outcome Y vs. comparator Z? |
| Diagnostic accuracy | **PICO** (with index test as I) | What is the sensitivity/specificity of test X? |
| Exposure / Risk factor | **PECO** | Is exposure E associated with outcome O in population P? |
| Prevalence | **P + O** (simplified) | What is the prevalence of secondary HTN subtype in population P? |
| Scoping review | Research questions are broader | What evidence exists on topic X? |

---

## PICO Template (Interventional / Diagnostic)

```
P — Population:
  - Hypertensive adults (define age range if relevant)
  - Confirmed [subtype] diagnosis using [specify criteria/guidelines]
  - Setting: inpatient / outpatient / community / referral center
  - Exclusions: [e.g., pregnant women, age < 18, bilateral adrenalectomy, end-stage CKD]

I — Intervention / Index Test:
  - [Specific intervention, drug, procedure, or diagnostic test]
  - Dose, duration, route of administration if relevant
  - Operator/center criteria if relevant (e.g., experienced AVS center)

C — Comparison:
  - Active comparator: [specific drug or procedure]
  - Placebo / sham procedure
  - No intervention / watchful waiting
  - Reference standard (for diagnostic studies)

O — Outcomes:
  Primary:
    - [Clinically meaningful outcome; e.g., BP reduction, biochemical cure, CV event, diagnostic accuracy]
  Secondary:
    - [List 2–4 secondary outcomes]
  Timepoints:
    - Short-term: [e.g., 3 months]
    - Long-term: [e.g., 12 months, 5 years]
  Excluded outcomes:
    - [Surrogate outcomes not pre-specified, or patient-reported outcomes without validated instrument]
```

---

## PECO Template (Observational / Exposure)

```
P — Population:
  - [Define the study population: general hypertensives, resistant HTN, specific age/sex/ethnicity]
  - Hypertension definition used (e.g., SBP ≥ 140 or DBP ≥ 90 mmHg, or ≥ 130/80 per AHA 2017)

E — Exposure:
  - [e.g., obstructive sleep apnea, drug exposure, genetic mutation, renal artery stenosis]
  - Exposure definition and measurement method

C — Comparator:
  - [Non-exposed group; e.g., no OSA, no drug use, essential hypertension]

O — Outcome:
  Primary:
    - [e.g., BP level, CV event rate, organ damage markers]
  Secondary:
    - [List 2–4 secondary outcomes]
  Timepoints: [Specify]
```

---

## Review Type Declaration Checklist

Before proceeding to Stage 2, confirm:

- [ ] Is this a **narrative review** (no formal screening, expert synthesis)?
- [ ] Is this a **scoping review** (map existing evidence, no GRADE)?
- [ ] Is this a **systematic review without meta-analysis** (formal PRISMA, narrative synthesis only)?
- [ ] Is this a **systematic review with meta-analysis** (formal PRISMA + quantitative pooling)?

**If unsure:** Default to systematic review. If quantitative pooling is not feasible, downgrade to systematic review in the title and abstract (do not call it a meta-analysis without pooled analysis).

---

## PROSPERO-Style Protocol Statement Template

```
Background: [Secondary hypertension subtype] affects approximately [X%] of hypertensive patients
and is associated with [higher CV risk / resistant hypertension / reversible cause]. Despite
[clinical importance], there is no current systematic review addressing [specific gap].

Objective: To systematically review [evidence on intervention/diagnostic test/prevalence/risk factor]
in patients with confirmed [subtype].

Methods: We will search [databases] from [date] to [date] for [study designs].
Two independent reviewers will screen titles/abstracts and full texts.
Eligible studies will be assessed for risk of bias using [tool].
We will synthesize evidence using [narrative / random-effects meta-analysis].
Certainty of evidence will be assessed using GRADE.

Registration: [PROSPERO ID if registered, or state "not registered" with reason]
```

---

## Subtype-Specific PICO Examples

### Primary Aldosteronism

```
P: Adults with confirmed PA (positive confirmatory test + adrenal CT ± AVS)
I: Unilateral adrenalectomy
C: Medical therapy with mineralocorticoid receptor antagonists (spironolactone, eplerenone)
O (primary): BP control (systolic BP < 130/80), biochemical cure (normalized ARR)
O (secondary): CV event rate, quality of life, potassium normalization, medication discontinuation
```

### Renovascular Hypertension

```
P: Adults with hemodynamically significant RAS (≥ 60% stenosis on imaging)
I: Percutaneous renal artery stenting
C: Optimized medical therapy
O (primary): BP reduction (mmHg), renal function (change in eGFR)
O (secondary): number of antihypertensives, renal replacement therapy, all-cause mortality
Timepoint: ≥ 12 months
```

### OSA and Resistant Hypertension

```
P: Adults with resistant hypertension (on ≥ 3 antihypertensives including diuretic, uncontrolled BP)
  and moderate-severe OSA (AHI ≥ 15/hr on PSG or HSAT)
I: CPAP therapy (≥ 4 hours/night for ≥ 3 months)
C: Sham CPAP or usual care
O (primary): 24-hour ambulatory BP (SBP and DBP)
O (secondary): non-dipping pattern, office BP, CV events, CPAP adherence
```
