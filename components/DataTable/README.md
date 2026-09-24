# DataTable

The delivery table: one row per Issue Orbi is working on, with its state chip, PR link and last update.

Hand-written from orbi-cloud `src/page.ts` (`table`, `th`, `td`, `.delivery-state-dot`) and `src/pages/status.ts` (`.delivery-table`, `deliveryRowHtml()`).

## Anatomy

- `orbi-table`: collapsed borders, full width, fixed layout. Columns 50% work · 18% status · 12% PR · 20% time.
- Cells: 1px `border-default` bottom rule, padding `space-2` `space-3`, 0.9rem, top-aligned, wrap anywhere. Headers: `ink-muted`, 600, no wrap.
- Work cell: a 6px state dot (`orbi-dot` = `success-strong`, `-blocked` = `danger-strong`, `-merged` = `merged`), the Issue number and title, then optional `orbi-cell-note` lines (queue note, usage) in 0.8rem `ink-muted`.
- Status cell: exactly one StatusChip. PR cell: `#N` link, or a muted em dash. Time: relative (3 分钟前).

## What the consumer provides

The rows, already ordered; the relative time strings; usage figures if any.

## Rules

- No row may vanish: a delivery with an unknown label still renders with the raw label as its chip.
- At ≤480px each row becomes a two-line grid (work on top; status · PR · time below) and the header is visually hidden but stays in the accessibility tree.
