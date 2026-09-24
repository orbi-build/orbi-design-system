# Tabs

Three CSS-only tabs over the delivery list — 进行中 / 评审中 / 已完成 — that work with JavaScript off.

Hand-written from orbi-cloud `src/pages/status.ts` (`DELIVERY_TABS_CSS`, Issue #301).

## Anatomy

- A visually hidden radio (`orbi-tab-radio`, opacity 0, still focusable) directly before each `<label>` in `orbi-tab-strip`.
- Labels: 0.9rem, `surface-subtle` ground, 1px `border-default`, top corners `radius-control`, margin-bottom −1px so the checked tab merges into the panel. Checked: `surface-raised`, 600 weight.
- Panels (`orbi-tab-panel`, one per tab) all stay in the DOM; the container's `:has(<radio>:checked)` shows the matching one.
- Keyboard focus moves the outline onto the label: 2px `focus-ring`, offset −2px.

## What the consumer provides

Unique radio `name` per tab set and `id`/`for` pairs; the tab title with its count in parentheses — `进行中 (2)`; the three panels. The first tab (进行中) is `checked` by default.

## Rules

- No script: switching is the native label→radio behaviour.
- The strip scrolls horizontally with its scrollbar hidden rather than wrapping; at ≤480px labels grow to `size-tap` height.
