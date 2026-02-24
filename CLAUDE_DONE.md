# CLAUDE_DONE.md — Revision Summary

**Agent**: Architect/Lead (Claude Opus)  
**Date**: 2026-02-24  
**Status**: ✅ Complete

---

## Changes Per Section

### 00_abstract.tex
- Rewrote for consistency with method (Haar DWT, not Laplacian)
- Tightened language, removed redundancy
- Added quantitative comparisons: 0.867 Dice vs. 0.845 SAM-Med2D, 2.1 mm HD vs. 6.1 mm
- Clean keyword list

### 01_introduction.tex
- Fully rewritten as flowing prose, no subsections
- Four paragraphs: landscape → transformers/foundation models → gap → our answer
- **Reduced contributions from 4 to 3**: merged old contribution #4 (frequency decomposition for boundary enhancement) into contribution #1 (dual-stream architecture). Now contribution #1 includes both the architectural claim AND the HD improvement numbers.
- Added TransUNet citation as CNN-transformer hybrid reference
- Updated BiomedCLIP citation to `zhang2025biomedclip` (NEJM AI 2025 venue)
- Cleaned all AI writing patterns

### 02_related_work.tex
- Maintains 4 `\paragraph{}` sections (no `\subsubsection`)
- Focus on techniques/architectures with medical context secondary
- Added TransUNet~\cite{chen2024transunet} (MIA 2024 published version)
- Kept Huang & Zhou (2025) as concurrent preprint with explicit note
- Removed all TODO comments
- Removed `wang2022frequency` (irrelevant arxiv-only)
- Each paragraph ends with clear positioning relative to our work

### 03_methodology.tex
- **No structural changes needed** — already well-structured with `\subsection` + `\paragraph{}`
- Fixed BioMedCLIP → BiomedCLIP capitalisation throughout
- All equations and notation consistent with rest of paper

### 04_experimental_setup.tex
- **Renamed section**: "Experiments" → "Dataset and Implementation Setup"
- Merged evaluation metrics into section body as `\paragraph{Evaluation Metrics.}` (was a separate `\subsection`)
- Added proper dataset citations:
  - BraTS: `\cite{menze2015brats,bakas2017brats,mehta2022qu}` (IEEE TMI 2015 + Scientific Data 2017 + QU-BraTS 2022)
  - CBIS-DDSM: `\cite{lee2017cbisddsm}` (Scientific Data 2017)
  - LUNA16: `\cite{setio2017luna16}` (Medical Image Analysis 2017)
- Used `{,}` for thousands separators in tables (LaTeX best practice)
- Trimmed metric definitions (Q1 readers know Dice/IoU)

### 05_results.tex
- **Renamed section**: "Analysis and Results" (was already this)
- **Baselines**: Converted from `\enumerate` to `\paragraph{}` entries — cleaner, more professional
- Main results table already had IoU columns — verified and kept
- Ablation table already had w/o variants as columns — verified and kept
- **Strengthened analysis**: Explained WHY each dataset shows different gains (brain: complex multi-region boundaries; breast: dense tissue ambiguity; lung: clean circular boundaries with vessel false positives)
- Removed "Notably" (banned word) from boundary quality section
- Removed em-dashes from analysis text
- Renamed "Visual Placeholders" → "Qualitative Results"

### 06_conclusion.tex
- Already split into Discussion (Section 6) + Conclusion (Section 7) ✅
- Renamed "Unexpected findings" → "Frequency-semantic dissociation" (sharper framing)
- Renamed "Why boundary quality matters clinically" → "Clinical relevance of boundary quality" 
- Removed "The central lesson is architectural" (moralising)
- Cut moralising from conclusion body
- Future work stays inline, no `\subsection{Future Work}`
- No "Broader Impact" or "Final Remarks" subsections

### reference.bib
- **Complete rewrite**: 28 clean entries, all used
- Updated BiomedCLIP: `zhang2023biomedclip` → `zhang2025biomedclip` (NEJM AI 2025)
- Updated TransUNet: `chen2021transunet` → `chen2024transunet` (MIA 2024 published)
- Updated SAM-Med2D: kept as arxiv with explicit note
- Added dataset citations: Menze 2015 (IEEE TMI), Bakas 2017 (Sci Data), Lee 2017 (Sci Data), Setio 2017 (MIA)
- Removed 11 unused entries (BiomedParse, SimCLR, focal loss, V-Net, radiomics, etc.)
- All remaining arxiv-only refs explicitly annotated

---

## New Citations Added

| Key | Venue | Why |
|-----|-------|-----|
| `zhang2025biomedclip` | NEJM AI 2025 | Updated from arxiv to published version |
| `chen2024transunet` | Medical Image Analysis 2024 | Updated from arxiv to published version |
| `menze2015brats` | IEEE TMI 2015 | BraTS challenge original citation |
| `bakas2017brats` | Scientific Data 2017 | BraTS data collection citation |
| `lee2017cbisddsm` | Scientific Data 2017 | CBIS-DDSM original citation |
| `setio2017luna16` | Medical Image Analysis 2017 | LUNA16 original citation |

---

## Decisions for Codex to Review

1. **Contribution count reduced 4→3**: Merged old #4 (frequency decomposition boundary enhancement) into #1 (dual-stream architecture). The reasoning: contribution #4's claim about Haar DWT outperforming Laplacian is really a sub-claim of the architecture design, not a standalone contribution. Codex should verify this doesn't lose important information.

2. **SAM-Med2D remains arxiv-only**: Could not find a peer-reviewed version. It's a widely cited preprint (>200 citations). Kept with explicit annotation. Codex may want to flag this for the submission checklist.

3. **TransUNet key changed from chen2021transunet to chen2024transunet**: The MIA 2024 published version has a slightly different title ("Rethinking the U-Net architecture design...") than the arxiv version. Both are standard citations. Codex should verify correctness.

4. **huang2025frequency kept**: This is labeled as a concurrent preprint in the bib. It's the weakest citation. Codex could suggest removal or replacement with a stronger frequency-domain segmentation reference.

5. **Methodology section untouched structurally**: The briefing said "consolidate subsections — reduce nesting depth" but the methodology already uses `\subsection` + `\paragraph{}` with no `\subsubsection`. Any further consolidation would hurt readability. Codex should confirm this is acceptable.

---

## Known Weaknesses to Flag

1. **Figure placeholders still present**: Figures 1 (architecture diagram references `Arch.png`), 2 (qualitative results), and 3 (activation maps) all need actual images. The paper will not compile cleanly without `Arch.png`.

2. **Experimental numbers are illustrative**: The numbers in Tables 3–7 appear to be reasonable but may not be from actual experiments. Codex should flag this for the authors to verify against real experimental results.

3. **`\cite` inside `\paragraph{}` heading** (baselines section): `\paragraph{SAM-Med2D~\cite{cheng2024sammed2d}.}` — this is valid LaTeX but some reviewers may find it unconventional. Codex could suggest moving the citation to the body text instead.

4. **Page count**: The paper with methodology section is likely 12–14 pages. LNCS format has strict page limits (typically 10–15 pages including references). Codex should verify this fits.

5. **No disclosure of interests section**: LNCS 2023+ requires a "Disclosure of Interests" section. This is missing from the paper. Needs to be added before submission.

6. **All figures/tables now cross-referenced**: Added `Fig.~\ref{fig:arch}` to methodology overview, and `Fig.~\ref{fig:qualitative}` / `Fig.~\ref{fig:activations}` to qualitative results subsection. All 6 tables and 3 figures are properly referenced in body text.
