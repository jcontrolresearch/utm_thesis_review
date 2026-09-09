---
name: reviewed-pdf
description: "Use when inspecting a thesis PDF, extracting page-aware text, adding Spanish review annotations, appending a printable finding summary, or validating a separate *_reviewed.pdf without changing the original. Uses local PDF processing and OCR where available."
user-invocable: false
---

# Reviewed PDF production

## Prerequisites and contract

Read and follow [academic review principles](../../instructions/academic-review.instructions.md) and [reference authority](../../instructions/reference-authority.instructions.md). Use findings grounded in the student submission; this skill renders and validates them, not fabricates them. The academic workflow is defined in [thesis progress review](../thesis-progress-review/SKILL.md).

Inputs are the student PDF, finding register with stable IDs and original-page locations, and review summary material. Output is a separate PDF alongside the input, preserving original thesis pages and adding annotations plus a readable review appendix. Student material stays local.

## 1. Inspect and extract

1. Verify that the input exists, is readable as a PDF, and is distinct from the intended output. Record filename, cryptographic hash, page count, existing annotations, available page labels, page dimensions, and document navigation where applicable.
2. If encrypted or digitally signed, explain access or signature implications. Do not bypass protections or claim signatures remain valid after annotation. Secrets must be entered through an appropriate secure mechanism, never requested in model-visible chat.
3. Use local PDF tools, such as PyMuPDF, to extract text page by page with coordinates where possible. Configure the Python environment before Python execution when environment tools are available; install missing dependencies into the selected environment, not globally. Use local OCR for scanned pages when available and disclose OCR limitations.
4. Keep physical PDF page numbers (1-based) and printed page labels distinct. Confirm a library's zero-based indexing at the boundary to avoid off-by-one annotation errors.
5. Visually inspect relevant rendered pages for equations, diagrams, plots, tables, symbols, and typography. Use images in addition to extracted text for technical conclusions; extraction does not preserve all mathematical/layout information.
6. Report unreadable pages and keep a coverage record. Do not treat extraction failures as proof that the thesis omitted content. Do not silently upload documents if local processing fails.

## 2. Choose a non-destructive output name

- Default: `<input_stem>_reviewed.pdf`, with no whitespace or newline in the extension.
- If the input stem already ends in `_reviewed`, remove that terminal suffix before composing the new name.
- If the destination exists or resolves to the input, preserve it and use `<base>_<YYYYMMDD_HHMMSS>_reviewed.pdf`. Add a collision counter before `_reviewed` if needed. Recheck the chosen destination before saving; never overwrite an existing file.
- Every final output must end in `_reviewed.pdf`. A renamed text document or a chat answer does not satisfy PDF delivery.

## 3. Add native annotations

1. Use a local PDF library capable of preserving original page content and adding standard annotations, such as PyMuPDF. Keep original pages in their original order and dimensions. Preserve existing annotations and navigation where supported; verify rather than promise preservation. Do not flatten or redact student content.
2. Add native highlight annotations and/or text-note comments anchored to verified locations. Use coordinates from the correct page, disambiguate repeated quotations, and do not highlight every occurrence automatically. For image-only or ambiguous locations, use a page-level note naming the visible target rather than inventing an exact text match.
3. Use annotation author `Revisión académica asistida por IA`. Each comment includes finding ID, severity, observation, rationale, correction, and source classification. Use restrained severity colors and textual labels so meaning does not depend on color.
4. Avoid obscuring text; place multiple note icons distinctly within page bounds. Preserve the source's existing comments and distinguish them from newly generated review annotations.

## 4. Append the review summary

Append summary pages after all original thesis pages. Label them **Resumen de revisión — no forma parte de la tesis original**. Include:

- Input identification, review date, thesis topic, progress assumptions, and review emphasis.
- Coverage and limitations, including pages/sections not assessed and relevant OCR or visual-inspection gaps.
- References consulted, their advisory status, and any verified applicable UTM requirements or unresolved guidance conflicts.
- Evidence-based strengths, prioritized corrections, and next-stage milestones.
- The complete finding register, including every new annotation's full comment and original-page references, so feedback remains readable in viewers or printed copies that hide popup comments.

Use fonts that render Spanish accents and required symbols. Paginate long summaries, wrap long text, prevent clipped text/tables, and keep appendix numbering distinct from original printed labels. Do not apply external thesis-format rules to the appendix itself.

## 5. Validate before reporting success

1. Reopen the saved output with a PDF reader/library. Confirm it is a nonempty readable PDF, the filename ends in `_reviewed.pdf`, and page count equals original pages plus appended summary pages.
2. Verify original page order and sizes, text where extractable, existing annotations, and navigation where applicable. Compare representative original-page renders with annotations disabled; report preservation limitations.
3. Confirm every finding ID appears in the appendix, every new annotation maps to its intended original page and finding, and annotations contain readable Spanish text. A review with no defensible findings may have zero new annotations; state that honestly and still append the scope/limitations summary.
4. Visually inspect annotated pages and first/last summary pages, plus dense summary pages, for legibility, bad anchors, overlapping icons, missing glyphs, and overflow. Repair issues before reporting success.
5. Recompute the source hash and verify that it is unchanged. Do not claim checks you could not perform.
6. If extraction, OCR, dependency installation, annotation, or generation is blocked, explain the specific failure and next action. Never claim to have produced or validated a PDF that does not exist. Clearly label any partial output and disclose what was not reviewed.

## Completion evidence

Return the output location, original and final page counts, number of new comments by severity, source-preservation result, validation checks performed, and limitations to the calling agent. No student PDF has been supplied or production run tested merely by installing this skill.
