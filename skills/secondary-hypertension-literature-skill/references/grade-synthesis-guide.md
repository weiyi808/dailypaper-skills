# GRADE Synthesis Guide — Secondary Hypertension Reviews

Load this module during Stage 5 (Evidence Synthesis and GRADE).

---

## When to Use Quantitative Synthesis (Meta-Analysis)

Pool studies only when ALL of the following are true:
- ≥ 2 studies address sufficiently similar PICO (population, intervention, outcome, timepoint)
- Effect measures are compatible (e.g., both report mean BP difference with SD)
- Clinical heterogeneity is acceptable (not just statistical)
- Pooling is pre-specified in the protocol

**Do NOT pool** if:
- Studies use different diagnostic criteria for the secondary hypertension subtype
- Follow-up durations are incompatible
- Treatment co-interventions differ substantially across studies
- I² > 75% and source of heterogeneity cannot be explained

---

## Statistical Synthesis Defaults

| Parameter | Default Choice | Reason |
|-----------|---------------|--------|
| Model | Random-effects (DerSimonian-Laird or REML) | Expected clinical heterogeneity across secondary HTN subtypes |
| Effect measure (continuous BP) | Mean Difference (MD) or Standardized MD | Comparable BP units across studies |
| Effect measure (binary events) | Risk Ratio (RR) or Odds Ratio (OR) | State which and justify |
| Heterogeneity statistic | I², τ², prediction interval | Report all three |
| Publication bias | Funnel plot + Egger's test | Only if ≥ 10 studies |

**I² interpretation (GRADE-aligned):**
- 0–40%: Might not be important
- 30–60%: Moderate heterogeneity
- 50–90%: Substantial heterogeneity
- 75–100%: Considerable heterogeneity
- **Always report prediction interval** alongside I² — it is more informative

---

## GRADE Certainty Domains

Apply GRADE to each pre-specified primary outcome:

### Downgrade Reasons

| Domain | Threshold for Downgrade |
|--------|------------------------|
| **Risk of bias** | Most evidence is at serious or high RoB |
| **Inconsistency** | Unexplained I² > 50% OR wide prediction interval crossing null |
| **Indirectness** | Population, intervention, comparator, or outcome differs materially from review question |
| **Imprecision** | Wide CI crossing minimal important difference (MID); optimal information size (OIS) not reached |
| **Publication bias** | Asymmetric funnel plot + Egger p < 0.1; OR only small industry-funded trials available |

### Upgrade Reasons (observational evidence only)

| Domain | Threshold for Upgrade |
|--------|-----------------------|
| Large effect | RR > 2 or < 0.5 with low RoB |
| Dose-response | Clear gradient between exposure/treatment intensity and outcome |
| All plausible confounders would strengthen the finding | (rarely invoked) |

### Certainty Ratings

| Rating | Meaning |
|--------|---------|
| ⊕⊕⊕⊕ **High** | Further research unlikely to change our confidence |
| ⊕⊕⊕○ **Moderate** | Further research likely to change our confidence |
| ⊕⊕○○ **Low** | Further research very likely to change our confidence |
| ⊕○○○ **Very low** | Any estimate of effect is uncertain |

---

## Secondary Hypertension–Specific GRADE Challenges

### Common reasons for Low / Very Low certainty in this domain

1. **Non-standardized diagnostic criteria**: Different studies use different ARR thresholds for PA, different AHI cutoffs for OSA, or different BP definitions for resistant hypertension. Indirectness ↓↓.

2. **Small sample sizes**: Many RCTs in secondary hypertension (especially rare subtypes like PPGL, Cushing, monogenic) have < 50 participants. Imprecision ↓↓.

3. **Open-label design**: Blinding is impossible for surgical vs. medical comparisons (adrenalectomy vs. MRA; stenting vs. medical therapy). Risk of bias ↓.

4. **Surrogate outcomes**: BP reduction is a surrogate for CV events; use it but state it is a surrogate.

5. **Short follow-up**: Many trials < 12 months; long-term outcomes unknown. Indirectness ↓.

**Always state these limitations explicitly in the GRADE table footnotes and in the Discussion.**

---

## Summary of Findings (SoF) Table Template

```
Outcome | N studies | N participants | Relative effect (95% CI) | Absolute effect | Certainty
--------|-----------|---------------|--------------------------|-----------------|----------
[Primary outcome] | [n] | [N] | [RR/OR/MD] (95% CI) | [per 1000 patients] | [⊕⊕○○ Low]
[Secondary outcome 1] | | | | | 
[Secondary outcome 2] | | | | |
```

**Footnotes must include:**
- Reason for each certainty downgrade (e.g., "a. Downgraded one level for serious risk of bias: most studies open-label")
- MID used for imprecision assessment (e.g., "b. MID for SBP = 5 mmHg; CI includes values below MID")

---

## Narrative Synthesis (When Meta-Analysis Not Justified)

Use when studies are too heterogeneous to pool:

**Allowed approaches:**
- Harvest plot (direction of effect per study, grouped by subgroup)
- Direction-of-effect table (positive / negative / null per study)
- Vote-counting (only as supplement, never as primary synthesis method)

**Forbidden approaches:**
- Saying "most studies showed improvement" without specifying proportions
- Informal averaging of reported p-values
- Ignoring high-RoB studies without documenting the decision

---

## Minimum Reporting Checklist for Synthesis Section

- [ ] State whether pooling was pre-specified or post-hoc
- [ ] Report effect estimate + 95% CI for each pooled outcome
- [ ] Report I², τ², and prediction interval
- [ ] Report number of studies and participants per outcome
- [ ] Report publication bias assessment method and result
- [ ] Apply GRADE to each primary outcome
- [ ] Produce Summary of Findings table for primary outcome(s)
- [ ] Distinguish pre-specified from exploratory analyses
