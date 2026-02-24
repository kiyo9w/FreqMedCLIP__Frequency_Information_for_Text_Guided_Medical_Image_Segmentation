# FreqMedCLIP Paper Revision — Agent Workflow Briefing

## Codebase
`/home/node/.openclaw/workspace/FreqMedCLIP/FreqMedCLIP_paper/`
- `paper.tex` + `00_abstract.tex` → `06_conclusion.tex`
- `reference.bib`, `llncs.cls` (Springer LNCS format)

## BMAD
BMAD agents at `/home/node/.openclaw/workspace/_bmad/bmm/agents/`.
Tools: perplexity search at `python3 /app/skills/perplexity-search/scripts/search.py -q "..." --labs --labs-model sonar-pro`
LaTeX skill: `/app/skills/latex/SKILL.md`

## Revision tasks (full list)

**Introduction**
- Remove all subsections. Rewrite as flowing prose: survey the landscape, cite relevant work, arrive at the gap, state contribution
- Keep contributions to 3-4 tight, defensible items — remove contribution #5
- No `\subsection` inside intro

**Related Work**
- Focus on techniques/architectures (frequency domain, dual-stream, ViT, text-guided seg) — medical context secondary
- Replace `\subsubsection` with `\paragraph{}` or bold inline
- Prefer peer-reviewed citations over arxiv

**Method**
- Consolidate subsections — reduce nesting depth
- Replace `\subsubsection` with `\paragraph{}` where possible

**Section 4 → "Dataset and Implementation Setup"**
- Merge Datasets + Implementation Details into one subsection
- Move Baseline Methods out of sec4 → into sec5
- Add dataset distribution table (Dataset | Modality | #Train | #Val | #Test | Task)
- Convert implementation details to a clean 2-col table (Parameter | Value)

**Section 5 → "Analysis and Results"**
- Bring Baseline Methods here (brief subsection before results)
- Table 2 (main results): add IoU column; clarify which dataset 0.873 belongs to; 3 sub-columns per dataset (Brain | Breast | Lung)
- Ablation table: w/o variants as columns not rows
- Explain WHY results are higher — not just that they are
- Add figure placeholders: (a) sample dataset images + inference output, (b) per-layer activations

**Conclusion → Discussion + Conclusion**
- Split into two sections
- Limitations → Discussion
- Future work stays brief in Conclusion body, no `\subsection{Future Work}`
- Cut "Broader Impact" and "Final Remarks" subsections

**Citations**
- Minimize arxiv-only citations
- Find peer-reviewed versions for key papers
- Add proper dataset citations (BraTS 2020, CBIS-DDSM, LUNA16)

## Quality bar
Q1 venue (MICCAI/ECCV level). Every sentence earns its space.
