# Search Strategy Templates — Secondary Hypertension Subtypes

Load the relevant subtype section when constructing the PubMed / Embase / CENTRAL search strings for Stage 2.

---

## General Rules

- Always combine MeSH terms (controlled vocabulary) with free-text synonyms using OR
- Combine population terms AND subtype terms AND (intervention / diagnostic / outcome terms if needed)
- Do NOT restrict with outcome terms in the initial search
- Export and deduplicate before screening
- Document: database name, date searched, number of hits, deduplication method

---

## 1. Primary Aldosteronism

### PubMed MeSH + Free Text
```
("Hyperaldosteronism"[MeSH] OR "Primary aldosteronism"[tiab] OR "Primary hyperaldosteronism"[tiab]
OR "Conn syndrome"[tiab] OR "Conn's syndrome"[tiab] OR "aldosterone-producing adenoma"[tiab]
OR "aldosteronoma"[tiab] OR "bilateral adrenal hyperplasia"[tiab])
AND
("Hypertension"[MeSH] OR "hypertension"[tiab] OR "high blood pressure"[tiab])
```

### Intervention-specific additions
- Adrenalectomy: `"Adrenalectomy"[MeSH] OR "adrenalectomy"[tiab] OR "surgical treatment"[tiab]`
- MRA therapy: `"Mineralocorticoid Receptor Antagonists"[MeSH] OR "spironolactone"[tiab] OR "eplerenone"[tiab] OR "finerenone"[tiab]`
- Diagnosis: `"Aldosterone to Renin Ratio"[tiab] OR "ARR"[tiab] OR "adrenal vein sampling"[tiab] OR "AVS"[tiab]`

### Embase equivalents
- `'primary aldosteronism'/exp` OR `'Conn syndrome':ab,ti` OR `'hyperaldosteronism':ab,ti`

---

## 2. Renovascular Hypertension

### PubMed
```
("Hypertension, Renovascular"[MeSH] OR "renovascular hypertension"[tiab]
OR "renal artery stenosis"[tiab] OR "renal artery obstruction"[tiab]
OR "fibromuscular dysplasia"[tiab] OR "atherosclerotic renal artery stenosis"[tiab])
AND
("Hypertension"[MeSH] OR "hypertension"[tiab])
```

### Intervention-specific additions
- Stenting: `"Stents"[MeSH] OR "renal artery stent"[tiab] OR "percutaneous transluminal renal angioplasty"[tiab] OR "PTRA"[tiab]`
- Medical therapy: `"Antihypertensive Agents"[MeSH] OR "RAAS inhibitor"[tiab] OR "ACE inhibitor"[tiab] OR "ARB"[tiab]`

---

## 3. Renal Parenchymal Hypertension

### PubMed
```
("Renal Insufficiency, Chronic"[MeSH] OR "chronic kidney disease"[tiab] OR "CKD"[tiab]
OR "renal parenchymal disease"[tiab] OR "glomerulonephritis"[tiab] OR "nephrosclerosis"[tiab])
AND
("Hypertension"[MeSH] OR "hypertension"[tiab] OR "blood pressure"[tiab])
```

---

## 4. Pheochromocytoma / Paraganglioma

### PubMed
```
("Pheochromocytoma"[MeSH] OR "pheochromocytoma"[tiab] OR "phaeochromocytoma"[tiab]
OR "Paraganglioma"[MeSH] OR "paraganglioma"[tiab] OR "chromaffin tumor"[tiab]
OR "PPGL"[tiab] OR "catecholamine-secreting tumor"[tiab])
AND
("Hypertension"[MeSH] OR "hypertension"[tiab] OR "blood pressure"[tiab])
```

### Diagnostic additions
- `"metanephrine"[tiab] OR "normetanephrine"[tiab] OR "catecholamines"[MeSH]`
- `"MIBG"[tiab] OR "metaiodobenzylguanidine"[tiab] OR "Ga-68 DOTATATE"[tiab] OR "PET"[tiab]`

---

## 5. Cushing Syndrome

### PubMed
```
("Cushing Syndrome"[MeSH] OR "Cushing's syndrome"[tiab] OR "Cushing syndrome"[tiab]
OR "hypercortisolism"[tiab] OR "ACTH-dependent"[tiab] OR "cortisol excess"[tiab]
OR "Cushing disease"[tiab])
AND
("Hypertension"[MeSH] OR "hypertension"[tiab] OR "blood pressure"[tiab])
```

---

## 6. Obstructive Sleep Apnea and Hypertension

### PubMed
```
("Sleep Apnea, Obstructive"[MeSH] OR "obstructive sleep apnea"[tiab] OR "OSA"[tiab]
OR "sleep-disordered breathing"[tiab] OR "apnea-hypopnea index"[tiab])
AND
("Hypertension"[MeSH] OR "resistant hypertension"[tiab] OR "blood pressure"[tiab]
OR "ambulatory blood pressure"[tiab])
```

### CPAP additions
`"Continuous Positive Airway Pressure"[MeSH] OR "CPAP"[tiab] OR "positive airway pressure"[tiab]`

---

## 7. Drug-Induced Hypertension

Customize with the specific drug class of interest. Example for NSAIDs:

### PubMed
```
("Anti-Inflammatory Agents, Non-Steroidal"[MeSH] OR "NSAIDs"[tiab] OR "ibuprofen"[tiab]
OR "naproxen"[tiab] OR "COX-2 inhibitor"[tiab] OR "celecoxib"[tiab])
AND
("Hypertension"[MeSH] OR "blood pressure"[tiab] OR "hypertension"[tiab])
```

---

## 8. Combined Secondary Hypertension (Broad Scoping)

Use when the review covers secondary hypertension in general:

### PubMed
```
("Hypertension, Secondary"[MeSH] OR "secondary hypertension"[tiab]
OR "identifiable hypertension"[tiab] OR "secondary cause of hypertension"[tiab]
OR "treatable hypertension"[tiab] OR "secondary etiology of hypertension"[tiab])
```

---

## Database-Specific Notes

| Database | Controlled Vocabulary | Free Text Fields | Notes |
|----------|----------------------|-----------------|-------|
| PubMed | MeSH Terms | [tiab] = title + abstract | Use [MeSH:noexp] to exclude subheadings if needed |
| Embase | Emtree | :ab,ti | Use '/exp' for explosion |
| CENTRAL | MeSH | Free text | Limited to RCTs and controlled trials |
| Web of Science | — | TS= (topic) | No controlled vocabulary; rely on synonyms |

---

## Recommended Date Range

- For most secondary hypertension reviews: **2000 to present** (modern diagnostic guidelines emerged post-2000)
- For historical prevalence questions: **1990 to present**
- For molecular/genetic subtypes: **2010 to present** (most genetic data is recent)

Always document exact search date for reproducibility.
