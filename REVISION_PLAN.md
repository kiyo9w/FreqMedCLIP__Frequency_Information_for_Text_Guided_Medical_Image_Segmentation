# FreqMedCLIP Paper Revision Plan

**Prepared by**: Architect/Lead Agent  
**Date**: 2026-02-24  
**Target**: Q1 venue (MICCAI/ECCV level)

---

## Global Principles

1. **AI writing guide compliance**: No banned words (leverage, utilize, crucial, delve, notably, etc.). No semicolons connecting clauses. No em-dashes for parentheticals. Vary sentence length. No moralizing conclusions.
2. **LaTeX correctness**: `booktabs` for tables, `\paragraph{}` instead of `\subsubsection{}` where appropriate, correct quote marks (``` `` '' ```), non-breaking spaces for numbers+units (`5~mm`).
3. **Citation hygiene**: Replace arxiv-only refs with peer-reviewed versions where possible. Add proper dataset citations (BraTS/Menze 2015 TMI, CBIS-DDSM/Lee 2017 Scientific Data, LUNA16/Setio 2017 MIA). Update BiomedCLIP to NEJM AI 2025 venue.
4. **Tone**: Senior researcher writing for peer reviewers. Every sentence earns its place. Specific over generic. Numbers over adjectives.

---

## Section-by-Section Plan

### 0. Abstract (`00_abstract.tex`)

**Current state**: Solid but mentions "Laplacian" (inconsistent with method section which uses Haar DWT). Contains good quantitative summary.

**Changes**:
- Minor polish for consistency: ensure abstract matches method (Haar DWT, not Laplacian).
- Tighten language. Remove any banned-list words.
- Ensure keyword list is clean and relevant.

**New structure**: Same single-paragraph abstract, ~150 words. No structural change needed.

---

### 1. Introduction (`01_introduction.tex`)

**Current state**: Already restructured as flowing prose with no subsections. Four numbered contributions. Generally well-written.

**Changes**:
- Trim contribution #5 (per briefing: keep 3-4 contributions). The current list has 4, which is acceptable. But contribution #4 (frequency decomposition for boundary enhancement) overlaps heavily with contribution #1 (dual-stream architecture). **Decision**: Merge contribution #4's key claim (Haar DWT outperforms Laplacian, HD numbers) into contribution #1. This tightens to 3 contributions.
- Check for banned-list words and AI patterns throughout.
- Ensure the narrative flows: landscape → gap → our answer → contributions.
- Remove any residual `\subsection` commands (none present currently).
- Verify all citations are peer-reviewed.

**New structure**: 
- Para 1: Medical segmentation dual challenge (semantic + boundary)
- Para 2: ViTs, foundation models, text-guided segmentation landscape
- Para 3: The gap—transformers suppress high-frequency, frequency methods lack semantics
- Para 4: Our answer—FreqMedCLIP, how it works
- Contributions list (3 items)

---

### 2. Related Work (`02_related_work.tex`)

**Current state**: Uses `\paragraph{}` headings (good). Four paragraphs covering ViT/foundation models, frequency-domain, dual-stream fusion, text-guided segmentation. Well-positioned.

**Changes**:
- Verify all paragraphs focus on **techniques/architectures** with medical context secondary (per briefing).
- Remove TODO comments about arxiv-only citations—resolve them instead.
- Replace `huang2025frequency` (arxiv-only) with a better peer-reviewed frequency-domain segmentation reference, or note it's a concurrent preprint.
- Replace `wang2022frequency` (arxiv-only, barely relevant) with something stronger.
- Add TransUNet citation as a key CNN-transformer hybrid reference.
- Tighten prose. Each paragraph should end with clear positioning of our work relative to that line of research.
- Check for banned-list compliance.

**New structure**: Same 4 paragraphs, tighter, better citations.

---

### 3. Methodology (`03_methodology.tex`)

**Current state**: Well-structured with `\subsection` and `\paragraph{}`. Mathematically rigorous. 8 subsections covering the full pipeline.

**Changes**:
- Per briefing: "Consolidate subsections—reduce nesting depth." Currently uses `\subsection` for major components and `\paragraph{}` for sub-components, which is already reasonable. No `\subsubsection` present.
- Minor: Check all equation formatting and consistency.
- Check that DWT notation is consistent throughout (Haar specifically).
- Verify parameter counts mentioned are consistent with other sections.
- Remove any banned-list words.
- The "Trainable components" paragraph at the end should mention total parameter count for reproducibility.

**New structure**: Keep current structure. Minor consolidation only.

---

### 4. Experimental Setup (`04_experimental_setup.tex`) — Rename to "Dataset and Implementation Setup"

**Current state**: Section titled "Experiments" with subsections "Dataset and Implementation Setup" and "Evaluation Metrics". Contains dataset table and implementation hyperparameter table. Well-structured.

**Changes**:
- **Rename section** from "Experiments" to "Dataset and Implementation Setup" (per briefing).
- **Move Baseline Methods** (currently in `05_results.tex`) — the briefing says "Move Baseline Methods out of sec4 → into sec5". Currently baselines ARE already in sec5 (subsec 5.1). So this is already done. Verify no baselines description in sec4.
- Dataset table already present (Table 1). Verify it has: Dataset | Modality | #Train | #Val | #Test | Task. ✅ Already has this.
- Implementation details table already present (Table 2). Verify it's a clean 2-col table. ✅ Already has this.
- Add proper dataset citations: BraTS needs Menze 2015 TMI + Bakas 2017, CBIS-DDSM needs Lee 2017 Scientific Data, LUNA16 needs Setio 2017 MIA.
- Remove `\subsection{Evaluation Metrics}` and merge metrics description into the setup section as a `\paragraph{Evaluation Metrics}` to reduce nesting.
- Trim evaluation metrics text—readers at Q1 venues know what Dice and IoU are. Define HD formula, state Dice and IoU briefly.

**New structure**:
```
\section{Dataset and Implementation Setup}
  \paragraph{Datasets.} (with Table)
  \paragraph{Implementation Details.} (with Table)
  \paragraph{Evaluation Metrics.} (brief, no formulas for Dice/IoU, keep HD formula)
```

---

### 5. Analysis and Results (`05_results.tex`)

**Current state**: Contains Baseline Methods (5.1), Quantitative Results (5.2) with main results table, Ablation Studies (5.3) with ablation table, Boundary Quality Analysis (5.4), Visual Placeholders (5.5), Computational Efficiency (5.6). Baseline methods already here (good).

**Changes**:
- **Main results table** (Table 3): Already has Dice AND IoU columns per dataset, plus average. ✅ Good. Check that column headers are clear with sub-columns per dataset.
- **Ablation table** (Table 4): Currently shows w/o variants as rows with delta column. Briefing wants "w/o variants as columns not rows." Restructure to make the full model a single row with delta columns—**this is already done!** The current table has `Full Model | w/o FreqEnc | w/o FFBI | w/o LFFI | w/o Dual Dec | w/o TCA` as columns. ✅ Already compliant.
- **Explain WHY results are higher**: Current text does explain mechanisms behind gains (frequency helps edges, semantic helps context, FFBI enables selective querying). Strengthen these explanations with signal-processing reasoning.
- **Figure placeholders**: Already present (Figures 2 and 3). Keep them—they're correctly marked as placeholders for actual inference outputs.
- **Baselines**: Brief description before results. Currently a numbered list with 4 baselines. Convert from `\enumerate` to `\paragraph{}` entries for each baseline (more compact, less student-report-like).
- Remove any banned-list words. Check for AI patterns.
- Trim verbose analysis—every sentence should add analytical value.
- Move UNet-CLIP description text: currently says "without explicit frequency decomposition"—clarify what conditioning it uses.

**New structure**:
```
\section{Analysis and Results}
  \subsection{Baseline Methods} (paragraph per baseline, no enumerate)
  \subsection{Quantitative Results} (Table + per-dataset analysis)
  \subsection{Ablation Studies} (Table + component analysis)
  \subsection{Boundary Quality Analysis} (Table + clinical relevance note)
  \subsection{Qualitative Results} (Placeholder figures, renamed from "Visual Placeholders")
  \subsection{Computational Efficiency} (Table + deployment note)
```

---

### 6. Discussion and Conclusion (`06_conclusion.tex`)

**Current state**: Already split into Discussion (sec 6) and Conclusion (sec 7) as separate `\section` commands. Discussion has interpretation paragraphs + limitations. Conclusion summarizes findings.

**Changes per briefing**:
- **Already split** ✅. But verify the structure matches the briefing's requirements:
  - Limitations → Discussion ✅ (already in Discussion section)
  - Future work stays brief in Conclusion body ✅
  - No `\subsection{Future Work}` ✅ (future work is inline in Conclusion)
  - Cut "Broader Impact" and "Final Remarks" subsections: Currently no such subsections exist. ✅
- **Polish Discussion paragraphs**: Strengthen the "unexpected findings" paragraph—the dissociation between HD and Dice for frequency-only baseline is a genuinely interesting finding. Frame it more sharply.
- **Tighten Conclusion**: Currently ~15 lines. Keep it tight. Remove any moralizing ("The central lesson is architectural"). Replace with direct summary of what was shown.
- **Check limitations**: Three limitations listed (resolution, diffuse boundaries, 3D extension). These are honest and appropriate. Keep.
- Remove banned-list words.

**New structure**:
```
\section{Discussion}
  \paragraph{Interpreting the performance gains.}
  \paragraph{Why boundary quality matters clinically.}
  \paragraph{Frequency-semantic dissociation.} (renamed from "Unexpected findings")
  \paragraph{Text guidance and its limits.}
  \paragraph{Limitations.}

\section{Conclusion}
  (Single block: summary + brief future directions, no subsections)
```

---

## Citation Changes

### Updates to existing entries:
1. **`zhang2023biomedclip`** → Update venue to NEJM AI 2025 (doi: 10.1056/AIoa2400640). Remove arxiv-only note.
2. **`cheng2024sammed2d`** → Remains arxiv-only; add note acknowledging this. No peer-reviewed version found.
3. **`li2023unleashing`** → Fix: this is a NeurIPS 2023 paper. Update entry type to `@inproceedings`.
4. **`huang2025frequency`** → Remains arxiv preprint. Mark clearly as concurrent work.
5. **`wang2022frequency`** → Remove entirely (barely relevant, arxiv-only, not cited in revised text).
6. **`hadi2023survey`** → Remove (Authorea preprint, not cited in paper).

### New entries to add:
7. **`menze2015brats`** — Menze et al., "The Multimodal Brain Tumor Image Segmentation Benchmark (BRATS)," IEEE TMI, 2015. Primary BraTS challenge citation.
8. **`bakas2017brats`** — Bakas et al., "Advancing The Cancer Genome Atlas glioma MRI collections with expert segmentation labels and radiomic features," Scientific Data, 2017.
9. **`lee2017cbisddsm`** — Lee et al., "A curated mammography data set for use in computer-aided detection and diagnosis research," Scientific Data, 2017.
10. **`setio2017luna16`** — Setio et al., "Validation, comparison, and combination of algorithms for automatic detection of pulmonary nodules in computed tomography images: the LUNA16 challenge," Medical Image Analysis, 2017.
11. **`chen2021transunet`** — Chen et al., "TransUNet: Transformers Make Strong Encoders for Medical Image Segmentation," arXiv 2021 (widely cited, accepted standard despite being arXiv).

### Entries to remove (unused):
12. **`zhao2024biomedparse`** — Not cited in revised text.
13. **`cheng2024interactive`** — Not cited in revised text.
14. **`li2025medvh`** — Not cited in revised text.
15. **`granstedt2025hallucinations`** — Not cited in revised text.
16. **`hadi2023survey`** — Not cited in revised text.
17. **`lambin2012radiomics`** — Not cited in revised text.
18. **`chen2020simple`** — Not cited in revised text (SimCLR).
19. **`lin2017focal`** — Not cited in revised text (focal loss).
20. **`milletari2016dice`** — Not cited in revised text (V-Net).
21. **`zhang2023learning`** — Not cited in revised text.

---

## Quality Checklist (Post-Revision)

- [ ] No `\subsection` inside Introduction
- [ ] No `\subsubsection` anywhere
- [ ] All tables use `booktabs` (`\toprule`, `\midrule`, `\bottomrule`)
- [ ] Section 4 title reads "Dataset and Implementation Setup"
- [ ] Section 5 title reads "Analysis and Results"
- [ ] Contributions reduced to 3 items
- [ ] All dataset citations are proper (not just challenge organizer papers)
- [ ] No banned-list words (leverage, utilize, crucial, delve, notably, etc.)
- [ ] No semicolons connecting independent clauses
- [ ] No em-dashes
- [ ] Abstract consistent with method (Haar DWT, not Laplacian)
- [ ] Every result number in the text matches the tables
- [ ] All TODO comments removed from .tex and .bib files
- [ ] Baseline methods section uses paragraphs, not enumerate
- [ ] Discussion + Conclusion are two separate sections
- [ ] No "Broader Impact" or "Final Remarks" subsections
- [ ] Every figure/table referenced at least once in text
