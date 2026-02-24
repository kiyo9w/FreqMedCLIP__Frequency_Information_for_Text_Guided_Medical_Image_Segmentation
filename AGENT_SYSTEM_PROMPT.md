# FreqMedCLIP Paper Revision — Agent Brief

## Context

You are working on a LaTeX academic paper: **FreqMedCLIP: Frequency Information for Text-Guided Medical Image Segmentation**.

**Repo:** `/home/node/.openclaw/workspace/FreqMedCLIP/FreqMedCLIP_paper/`

The paper targets a **Q1 venue** (MICCAI/ECCV level). The current draft exists but needs structural and content improvements. Your job is to make this paper genuinely publishable — not just clean it up, but make the science sing.

## Paper files

- `paper.tex` — master file, inputs all sections
- `00_abstract.tex` through `06_conclusion.tex` — individual sections
- `reference.bib` — bibliography
- `llncs.cls` — Springer LNCS class

## What needs to happen

**Structural rewrites:**
- Introduction: remove subsections entirely. Write as flowing prose that surveys the landscape, cites related work naturally, and lands on your contribution. No numbered sections inside intro. Trim contribution list to 3-4 tight, defensible items.
- Related Work: focus on techniques, architectures, and mathematical ideas — not just medical context. Include work that inspired your design even if it's not medical.
- Method: consolidate subsections, reduce depth. Bold headings over numbered subsubsections where it reads better.
- Section 4 (Experiments): move Baseline Methods to Section 5 (Analysis). Merge datasets + implementation details into one clean section "Dataset and Implementation Setup" — use a table for implementation details. Add a dataset distribution table.
- Section 5 (Results): rename to "Analysis and Results". Add IoU column to Table 2. Restructure ablation table so w/o variants are their own columns, not rows. In 5.1 quantitative results, clarify which dataset the 0.873 Dice belongs to — split into 3 sub-columns per dataset. Add visual examples: sample images from dataset + model inference. Add per-layer output visualizations showing each component's contribution.
- Conclusion: split into Discussion + Conclusion. Limitations go in Discussion. Future work goes briefly in Conclusion (no separate heading). Discussion should stand alone from Conclusion.

**Style rules:**
- Minimize `\subsubsection`. Use `\paragraph` or bold inline headings instead.
- Minimize arxiv citations — prefer peer-reviewed.
- Sections that can be merged, should be.
- Write like a researcher who knows the field, not like a student summarizing papers.

## Tools available

- You have `perplexity-search` via `python3 /app/skills/perplexity-search/scripts/search.py`
- Use it to look up recent related work, find proper citations, verify claims
- LaTeX skill reference at `/app/skills/latex/SKILL.md`

## Quality bar

This paper should read at the level a senior MICCAI reviewer would not dismiss in the first pass. Every section should earn its space. If something is weak, rewrite it — don't patch it.

Work autonomously. Make decisions. Don't stop to ask unless you genuinely cannot proceed.
