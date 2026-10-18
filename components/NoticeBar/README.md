# NoticeBar

The ① 需要你处理 block at the top of the dashboard: each item is one problem Orbi cannot solve alone, with the reason and the button that fixes it.

Hand-written from orbi-cloud `src/pages/status.ts` (`.needs-you-item`, `.needs-you-content`, `.blocked-reason`, `inlineStatusIcon()`).

## Anatomy

- Heading: `①需要你处理` (or `①操作提醒` when nothing is blocked) plus ` · N 条`, styled as a section label.
- Item `orbi-notice`: flex row, `space-3` gap, `space-4` padding, `radius-card`.
  - `orbi-notice-error`: `danger-soft` ground, 1px `danger` border, 4px `danger-strong` left rule, circled-× icon.
  - `orbi-notice-warning`: `warning-soft` ground, 1px `warning-border`, 4px `warning-strong` left rule, triangle-! icon.
  - `orbi-notice-info`: `info-soft` ground, 1px `info` border, 4px `info` left rule, circled-i icon.
- Body: a bold first line saying what is wrong (需要你处理：…), then either a plain explanation or the engine's verbatim reason in `orbi-notice-reason` (ui-mono 0.85rem, `ink-code`, wraps anywhere), then `orbi-notice-actions` (primary first, then secondary), then an optional one-line trailer.

## What the consumer provides

The kind (error or warning), the headline, the reason text, and 1–2 actions that actually repair the problem (a form post or a link to the Issue). The 20px inline SVG icons are part of the component and use `currentColor`.

## Icon and headline: one set, site-wide

Every icon that sits next to a headline uses this component's icons and this one alignment, at every level (error, warning, info) and in every place: the notice bar, the main card's headline on the status page (卡住 / 待补充 / 等批准), and any other notice. The icon sits in a box exactly one headline line tall (`1lh` of the headline's type) and is centred in it, so its centre is on the middle of the headline's first line at any type size, and stays on the first line when the headline wraps. A headline next to an icon has no top margin of its own. No page draws its own icon set or its own alignment (maintainer 2026-10-18: the main-card × sat a step above its headline; 「info 和 warning 也是一样的问题，你要一起统一修复，别打补丁」).

## Rules

- Only things the person must do go here; progress belongs in ② 正在发生.
- One problem, one place. A problem shown in ① is not drawn again anywhere on the page: the repository row marks it with its 需要你 chip only, and that repository's ② 正在发生 keeps its one-line state sentence without repeating the card, the reason or the action. Primer's banner guideline says the same: "Do not display more than one banner (full-width or otherwise) on a single page at the same time" (https://primer.style/product/components/banner/guidelines/).
- ① sits above everything because what it holds concerns the whole account. A message that concerns one section only sits next to that section instead, never in both places.
- The reason is never paraphrased when it comes from the engine — print it raw in mono.
- The action sits on its own line under the reason; a long engine sentence must never run into a button.
- `warning-border` on `warning-soft` is 2.08:1 — decorative; the 4px rule carries the signal.
