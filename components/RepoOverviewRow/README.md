# RepoOverviewRow

One line per connected repository in the multi-repo overview: status dot, name, a one-line "what is happening now", and three counts; the whole row links to that repository's detail.

Hand-written from orbi-cloud `src/pages/status.ts` (`repositoryOverview()`, `.repository-overview-*`, `.repository-state-dot`).

## Anatomy

- Grid: `minmax(0, 2fr)` name column, three count columns `minmax(3.5rem, .65fr)`, a 1.5rem › arrow; gap `space-3`; min-height 4rem; 1px `border-default` bottom rule.
- Name: a 0.65rem state dot — `needs` `danger`, `working` `info`, `done` `success`, idle `neutral` — the `owner/name` (ellipsised), and a 需要你 blocked chip when the repository needs attention.
- Headline under the name: 0.85rem `ink-muted`, one line, ellipsised, indented 1.25rem to clear the dot.
- Counts: 进行中 · 评审中 · 已完成, centred, ui-mono.
- Hover and selected (`.selected` + `aria-current="true"`): `info-soft` ground.
- Above the rows, `orbi-overview-columns` repeats the grid as a 0.8rem `ink-muted` header: 仓库 · 现在 / 进行中 / 评审中 / 已完成.

## What the consumer provides

Repository name, state (needs / working / done / idle), headline sentence, the three counts, the href, and which row is selected. Rows are sorted by attention first, then most recently updated, then name.

## Rules

- At ≤480px the header is hidden and each row stacks: name, headline, then counts inline with their labels (· 进行中 2).
- The dot is decoration (`aria-hidden`); the chip and headline carry the state in words.
