---
name: thesis-progress-review
description: "Use when reviewing a UTM MESIA master's thesis progress PDF for academic writing, thesis structure, research coherence, methodology, or technical rigor. Establishes coverage and produces an evidence-based finding register in Mexican Spanish for annotated PDF delivery."
user-invocable: false
---

# Thesis progress review

## Prerequisites

Read and follow [academic review principles](../../instructions/academic-review.instructions.md) and [reference authority](../../instructions/reference-authority.instructions.md) before reviewing. This skill owns academic assessment and the finding register; [reviewed PDF production](../reviewed-pdf/SKILL.md) owns PDF inspection, annotation, appendix generation, and output validation. Load its inspection procedure before extracting a student PDF.

## 1. Establish scope and coverage

1. Obtain a student progress PDF identified by the user. If none is identified, ask for its path. Do not mistake guidelines or sample theses for the submission. If multiple candidates exist, ask which to review.
2. Identify the topic, objectives, apparent stage, submitted chapters, declared omissions, and requested scope. Optional context includes registered objectives, advisor instructions, previous reviews, approved protocol, and verified UTM requirements. Start without unnecessary questions and disclose assumptions about the progress stage.
3. Inventory and read relevant reference documents. Record provenance, dates where available, page numbers, and authority level. List archive contents first and inspect only relevant templates without executing them.
4. Use the PDF inspection procedure to read text and inspect rendered pages. Distinguish physical PDF pages (1-based) from printed labels. Do not infer exact typography or equations from plain-text extraction alone.
5. Track pages and sections reviewed, extraction/OCR failures, visual checks, and items not assessed. Process long documents in batches while maintaining one finding register and consistent identifiers. Disclose partial coverage.

## 2. Evaluate the submitted work

Prioritize writing and thesis structure while retaining the following checks where relevant to the topic and progress stage:

- **Academic communication and structure:** chapter organization, logical progression, paragraph cohesion, Mexican Spanish grammar and accents, precise terminology, notation, abbreviations, readable figures/tables/equations, cross-references, captions, source acknowledgments, citation–bibliography consistency, and appropriate abstract content for the stage.
- **Research coherence:** problem definition, motivation, scope, research question or hypothesis where appropriate, measurable objectives, contribution, and alignment between objectives, methods, results, and conclusions.
- **State of the art:** relevant foundational and recent work, critical synthesis rather than a list of summaries, defensible research gap, fair comparison, and attribution.
- **Methodology and reproducibility:** justified design choices, assumptions, datasets/materials, equipment, software and hardware versions, experimental protocol, parameter selection, evaluation metrics, baselines, repeatability, uncertainty, and limitations.
- **Control/electronics when applicable:** model assumptions, units, sign conventions, derivations, stability claims and their conditions, sampling/discretization, saturation, noise, sensor/actuator limitations, numerical precision, computational resources, timing, and implementation evidence. Distinguish simulation from hardware validation.
- **Artificial vision/intelligent systems when applicable:** data provenance and permissions, train/validation/test separation, leakage, imbalance, preprocessing, fair baselines, metric selection, robustness, generalization, ablation studies where justified, and compute/latency constraints. Do not demand machine-learning experiments for a non-ML thesis.
- **Results and interpretation:** traceability to objectives, adequate evidence, meaningful comparisons, uncertainty/statistics where appropriate, plots with readable axes and units, limitations, and conclusions that do not exceed results. For early-stage work, assess the proposed validation plan instead.
- **Presentation:** internal consistency and useful external-guide recommendations, with explicit source labels. Do not enforce unsupported institutional formatting rules or claim measured margins, spacing, fonts, or mathematical errors without sufficient evidence.

## 3. Build the finding register

Maintain one finding register. Give each finding a stable ID such as `UTM-001` and record:

| Field | Required content |
| --- | --- |
| Location | Physical PDF page and printed label when known; section, figure/table/equation identifier; short exact excerpt or visual anchor. For an absent section, identify a related existing page and explain the absence rather than inventing a location. |
| Category | Writing, structure, methodology, technical rigor, references, or presentation. |
| Authority | External recommendation, academic/technical criterion, or verified UTM requirement, using the labels in the reference instructions. |
| Severity | **Crítica**: invalidates a central claim or essential validation. **Mayor**: substantial reasoning, structure, evidence, or reproducibility gap. **Menor**: localized clarity/presentation issue. **Sugerencia**: optional improvement. |
| Observation | What was observed, supported by the submission. |
| Rationale | Why it matters; technical reasoning or supporting guideline page/section; uncertainty if evidence is incomplete. |
| Action | A specific feasible correction or verification question; short example wording where useful. |
| Status | **Corrección del avance**, **Pendiente para una etapa posterior**, **No evaluable**, or **Requiere confirmación del asesor**, as applicable. |

Consolidate repeated issues into one finding with representative locations instead of flooding every page with duplicates. Keep strengths evidence-based and separate from corrective findings. Distinguish structural reorganization suggestions from missing future milestones.

## 4. Prepare PDF production inputs

Pass the finding register, source PDF identity, stage assumptions, coverage record, references consulted and their authority, evidence-based strengths, prioritized corrections, and next-stage milestones to the reviewed PDF production procedure. Preserve IDs and original-page references. The deliverable is a generated annotated PDF with an appended summary, not merely this register or a chat response.
