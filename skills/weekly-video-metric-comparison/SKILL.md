---
name: weekly-video-metric-comparison
description: Use when a weekly Amazon video-advertising XLSX is missing the 图1 or CP:CV metric-comparison block, green benchmark markers, or requests mention 补齐视频指标对比, 补图1, CP-CV, or 绿色标记.
---

# Weekly Video Metric Comparison

## Purpose

Add only the seven-column current-metric mirror and its six benchmark-based green markers. Preserve the uploaded workbook and use its existing parent-ASIN six-month baseline fields.

**REQUIRED SUB-SKILL:** Use `spreadsheets:Spreadsheets` for workbook inspection, editing, rendering, and verification.

Read [references/comparison-rules.md](references/comparison-rules.md) before editing.

## Workflow

1. Import and render the relevant main-detail sheet before editing. Identify fields by the combination of top-level group header and metric header; column letters in the reference are evidence, not a reusable lookup method.
2. Find the actual campaign data rows from populated anchor fields such as campaign name, parent ASIN, or source spend. Never trust a worksheet dimension, whole-column filter, or million-row used range as the data boundary.
3. Use an existing intended blank CP:CV block when it is safe. Otherwise place the seven columns after the last metric block and before conclusion/visual-analysis fields. Do not overwrite nonblank user content; stop and report the conflict.
4. Write formulas that mirror the current campaign metrics in this order: Spend, CPC, CTR, CVR, ACOS, 5-second view rate, completion rate.
5. Add native conditional formatting only to the six efficiency/rate columns over actual data rows. Spend is display-only and is never green.
6. Match the workbook's local borders, alignment, widths, number formats, and two-row header style. Use `#92D050` for green when no established equivalent rule is available.
7. Save one sibling XLSX named `<source>_补齐视频指标对比.xlsx`. Never overwrite the source.
8. Reopen and verify representative rows, formulas, conditional-format ranges, and visual rendering. Newly introduced formula errors must be zero.

## Fixed Boundaries

- Operate only on the user-confirmed first worksheet for this recurring workflow. If the required source or benchmark fields are absent there, stop and report the missing fields; do not inspect another worksheet.
- Do not calculate a new six-month baseline, create a helper baseline sheet, average weeks, or exclude periods. The workbook already contains the required comparison fields.
- Do not calculate differences, percentage changes, or percentage-point changes. The output cells display the current metric values.
- Do not perform video viewing, visual diagnosis, optimization decisions, or write visual-analysis columns.
- Do not manually paint current results green; use conditional formatting so later recalculation updates the color.
- Do not fill formulas or formatting to full columns or Excel's maximum row.
- Do not convert numeric values or percentages to text.

## Completion Report

Report the output file, edited sheet, actual row range, formulas added, conditional-format rules added, unresolved header conflicts, and newly introduced formula-error count.
