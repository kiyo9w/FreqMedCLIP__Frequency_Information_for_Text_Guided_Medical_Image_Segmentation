# CODEX Critique of `REVISION_PLAN.md`

## Overall assessment
The plan is organized, concrete, and substantially aligned with the workflow briefing. It correctly captures the major structural edits (Section 4/5 reframing, contribution tightening, discussion vs conclusion split, table requirements, citation cleanup). It is stronger than a typical high-level revision checklist.

However, several weaknesses remain for a Q1-standard execution:
1. It overstates current compliance in multiple places ("already done") before verification from source files.
2. It introduces non-briefing constraints ("banned words" list, stylistic prohibitions) without evidence those are venue requirements.
3. Some citation decisions are risky or inaccurate (e.g., treating TransUNet arXiv as acceptable while simultaneously pushing peer-reviewed replacements).
4. It lacks an explicit verification protocol mapping briefing tasks to exact file-level edits and line-level acceptance criteria.

---

## What the plan gets right
- **Strong section-by-section structure**: clear mapping to all major manuscript files (`00`–`06`).
- **Correct macro-level architecture**:
  - Intro as flowing prose with tighter contributions.
  - Related Work with technique-first orientation.
  - Reduced nesting in Method.
  - Section 4 as dataset + implementation setup.
  - Section 5 as analysis + results with baselines included.
  - Discussion/Conclusion split retained and refined.
- **Tables and figures awareness**:
  - Explicit checks for dataset distribution + implementation parameter tables.
  - Main results and ablation restructuring acknowledged.
  - Figure placeholders retained intentionally.
- **Citation hygiene focus**:
  - Identifies need to reduce arXiv-only references.
  - Explicitly adds canonical dataset citations (BraTS/CBIS-DDSM/LUNA16).
- **Quality checklist included**: useful for downstream QA pass.

---

## Weak / missing / structurally wrong

### 1) Premature compliance assumptions
The plan repeatedly marks items as already compliant (✅) before an implementation audit. This is unsafe in revision planning.
- Risk: creates false confidence and missed defects.
- Fix: convert all ✅ claims into "to verify" checks with concrete pass/fail criteria.

### 2) "Banned words" policy is non-standard and potentially harmful
The plan imposes lexical bans (e.g., "crucial", "notably") and punctuation bans as hard constraints. This can produce unnatural writing and is not equivalent to "human, high-quality style."
- Risk: over-sanitized prose that sounds formulaic.
- Fix: replace with evidence-based style criteria: precision, concision, claim-evidence alignment, and syntactic variety.

### 3) Citation strategy inconsistent with its own principle
The plan says "prefer peer-reviewed over arXiv" but then explicitly keeps some arXiv references without mitigation plan.
- Example: `chen2021transunet` is listed as arXiv; there are journal/extended variants and many peer-reviewed alternatives for hybrid transformer segmentation.
- Fix: for each arXiv citation, provide either:
  1) peer-reviewed replacement, or
  2) explicit justification why arXiv is necessary and low-risk.

### 4) Missing reproducibility and statistical-rigor checks
For Q1 venues, the plan should include:
- run count / seed policy,
- variance reporting (mean ± std where applicable),
- fair baseline protocol (same data split, augmentation, backbone scale),
- statistical support for claims (even lightweight).
Currently absent.

### 5) No explicit cross-file consistency matrix
Claims in abstract/introduction/results/discussion can drift. Plan lacks a "single source of truth" table for key numbers and claims.
- Fix: add a consistency matrix: metric values, datasets, table IDs, and text references.

### 6) Missing LaTeX compile-gate in the plan
The plan mentions LaTeX correctness but not mandatory compile checks.
- Fix: include explicit build cycle (`pdflatex/bibtex/pdflatex/pdflatex`) and zero-warning targets for unresolved refs/cites.

### 7) Limited risk management for figure placeholders
Plan keeps placeholders but does not specify standardized captions describing intended content and evaluation purpose.
- Fix: captions should include what is shown, comparison target, and why it supports claim.

---

## Section-specific suggestions

### Abstract
- Keep one paragraph, but add a **claim-to-number** integrity pass:
  - every quantitative claim must map to one table value.
- Avoid method-detail overload (e.g., too many module names) in abstract.

### Introduction
- Good decision to compress contributions.
- Ensure contributions are **non-overlapping** and each has one measurable validation statement.
- Add one sentence clarifying clinical significance beyond metric deltas.

### Related Work
- Keep architecture-first framing.
- End each paragraph with one sentence: "what is still missing" and "how our method addresses it".
- Replace weak or non-essential arXiv citations where feasible.

### Methodology
- Current plan says "minor consolidation only"; this may be insufficient.
- Add explicit checks for:
  - notation reuse consistency,
  - symbol definitions before first use,
  - computational complexity/parameterization summary,
  - potential ambiguity in module ordering.

### Section 4 (Dataset + Implementation)
- Good table requirements.
- Add split provenance and preprocessing details (normalization/resizing/cropping) in concise form.
- Clarify whether metrics are computed per-slice or per-volume for each dataset.

### Section 5 (Analysis + Results)
- Main and ablation table targets are good.
- Add a **failure-case subsection** or paragraph: where method underperforms and why.
- If claiming superiority, include margin context (absolute + relative gains) and practical relevance.

### Discussion + Conclusion
- Good split.
- Discussion should explicitly separate:
  - mechanistic interpretation,
  - boundary-clinical relevance,
  - limitations/threats to validity.
- Conclusion should avoid introducing new claims not shown in results.

### Citation/Bibliography
- Add a pass for duplicate entries and dangling bib keys.
- Ensure venue/year/DOI fields are complete for core citations.
- For any remaining arXiv-only reference, include rationale in related-work wording (e.g., "concurrent preprint").

---

## Scientific claims needing stronger support
1. **"Frequency decomposition improves boundary precision"**
   - Should be supported with boundary-specific metrics and qualitative evidence tied to error modes.
2. **"Text guidance improves cross-dataset robustness"**
   - Needs explicit cross-domain evidence and not only aggregate averages.
3. **"Performance gains arise from semantic-frequency complementarity"**
   - Requires ablation interpretation beyond additive score changes (interaction evidence preferred).
4. **Any claim of clinical relevance**
   - Must avoid overreach unless linked to clinically meaningful endpoint interpretation.

---

## Recommended plan upgrade (execution-ready)
Before implementation, add three artifacts:
1. **Task-to-file traceability matrix** (briefing item → file/section → acceptance check).
2. **Claim-evidence matrix** (major sentence-level claims → supporting table/figure/citation).
3. **Compile & QA gate** (build success, no unresolved refs/cites, table/figure references complete).

This will materially reduce revision risk and raise the manuscript to a true Q1 review standard.