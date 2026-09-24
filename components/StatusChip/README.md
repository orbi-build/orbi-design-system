# StatusChip

A pill with one short Chinese state word that says where a delivery or a repository stands.

Hand-written from orbi-cloud `src/page.ts` (`.chip`, `.chip.ok`, `.chip.ai-merged`, `.chip.ai-blocked`) and `src/pages/status.ts` (`statusChip()`, `.chip.awaiting-human`).

## States

| class | text in source | when |
|---|---|---|
| `orbi-chip orbi-chip-ok` | 生效中 · 开通成功 | A repository is bound and provisioned. `success` text and border. |
| `orbi-chip orbi-chip-blocked` | 受阻 · 需要你 · 开通失败 · Issues 已关闭 | The engine stopped and a person must act. `danger` text and border. |
| `orbi-chip` (queued) | 已排队 · 进行中 · 修复中 | Labelled `ai-ready` / in progress. Neutral: `border-default` border, `ink` text — work is moving, nothing to look at. |
| `orbi-chip orbi-chip-merged` | 已合并 · PR 评审中 | Merged (also the PR-opened state). Same `success` colour as ok. |
| `orbi-chip` (closed) | 已关闭 · 历史 | Closed without merge, or a historical binding. Neutral. |
| `orbi-chip orbi-chip-waiting` | 等你确认 · 等待审批 | Waiting on a human. `warning` text and border on `warning-soft`, 600 weight. |

## What the consumer provides

The state word only. One chip per delivery row: the source picks the first match in the order 等你确认 → 已合并 → 等待审批 → PR 评审中 → 受阻 → 修复中 → 进行中 → 已排队; an unknown `ai-*` label renders raw as a neutral chip so no row loses its state.

## Rules

- The word carries the state; colour only repeats it. Queued and closed share the neutral look on purpose.
- ok and merged are the same green as each other; blocked red and ok green differ mostly by hue, so the word is mandatory.
- `success` on `info-soft` (a green chip inside a selected overview row) is 4.46:1 — just under 4.5:1; kept as in source.
