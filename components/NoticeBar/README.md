# NoticeBar

The ① 需要你处理 block at the top of the dashboard: each item is one problem Orbi cannot solve alone, with the reason and the button that fixes it.

Hand-written from orbi-cloud `src/pages/status.ts` (`.needs-you-item`, `.needs-you-content`, `.blocked-reason`, `inlineStatusIcon()`).

## Anatomy

- Heading: `①需要你处理` (or `①操作提醒` when nothing is blocked) plus ` · N 条`, styled as a section label.
- Item `orbi-notice`: flex row, `space-3` gap, `space-4` padding, `radius-card`.
  - `orbi-notice-error`: `danger-soft` ground, 1px `danger` border, 4px `danger-strong` left rule, circled-× icon.
  - `orbi-notice-warning`: `warning-soft` ground, 1px `warning-border`, 4px `warning-strong` left rule, triangle-! icon.
- Body: a bold first line saying what is wrong (需要你处理：…), then either a plain explanation or the engine's verbatim reason in `orbi-notice-reason` (ui-mono 0.85rem, `ink-code`, wraps anywhere), then `orbi-notice-actions` (primary first, then secondary), then an optional one-line trailer.

## What the consumer provides

The kind (error or warning), the headline, the reason text, and 1–2 actions that actually repair the problem (a form post or a link to the Issue). The 20px inline SVG icons are part of the component and use `currentColor`.

## Rules

- Only things the person must do go here; progress belongs in ② 正在发生.
- The reason is never paraphrased when it comes from the engine — print it raw in mono.
- The action sits on its own line under the reason; a long engine sentence must never run into a button.
- `warning-border` on `warning-soft` is 2.08:1 — decorative; the 4px rule carries the signal.
