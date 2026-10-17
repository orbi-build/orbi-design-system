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

## Article comparison matrices

An article comparison matrix has options in columns and attributes or actions
in rows. Readers compare values across a row. The delivery table's two-line
mobile grid rule applies to delivery records; use the following rules for
article comparison matrices.

At narrow widths, retain the native table and its visible column headers.
Reuse the marketing site's table scroll container and pinned first column
pattern. Allow horizontal scrolling within the article's content width, and
keep row labels pinned on an opaque paper background while other columns
scroll. Let row labels wrap naturally. Keep the existing type size and enough
column width to read complete words and results. Preserve values, order,
emphasis and footnotes.

Use column and row headers (`th scope="col"` and `th scope="row"`). Make the
scroll region keyboard-focusable with a visible focus indicator and a short,
localized horizontal-scroll hint. Arrow keys must scroll it, and Tab must let
focus leave. Short matrices use the page's natural vertical scrolling.

Every table in an article body uses this layout by default; the author
declares nothing. Article tables never use the delivery table's mobile grid or
any row-by-row stacking, which would draw a bordered box per cell inside the
article on phones. A column sizes to its content on one line up to a cap
(12.5rem on the marketing site), past which its text wraps; show the scroll
hint only while the table actually overflows its region. Use the existing brand type, spacing,
border and paper tokens. The delivery table's styling stays unchanged.
