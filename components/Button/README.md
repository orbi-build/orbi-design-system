# Button

One action per button; the fill tells the reader which action is the main one.

Hand-written from orbi-cloud `src/page.ts` (`.cta`, `input[type=submit]`, `button`, `.cta.secondary`, `.cta.login`) and orbi-website `public/styles.css` (`.button`, `.button-signal`, `.button-ghost`).

## Variants

| class | when | look |
|---|---|---|
| `orbi-btn` (primary) | The one thing to do in this card: 创建 Issue, 一键创建里程碑并继续, a form submit. | `accent` fill, `on-accent` label, 600 weight, `radius-control`, padding `space-2` `space-4`. Hover `accent-hover`. |
| `orbi-btn orbi-btn-secondary` | Leaving or looking: 在 GitHub 上查看, 返回, 添加仓库. Same size and weight as primary, never the same fill. | `surface-raised` ground, `success-strong` label and 1px border (product); on night, the ghost button: transparent, `line-dark` border, `ink` label. |
| `orbi-btn orbi-btn-login` | Sign in with GitHub only. | `surface-inverse` fill, `on-inverse` label. |
| `orbi-btn orbi-btn-cta` | The marketing call to action (Start Cloud with GitHub) and the proof page's closing CTA. Brand surface only, once per screen. | `signal` fill, `night` label, square (`radius-none`), `size-brand-button` tall, `space-brand-button-x` side padding, 0.92rem. Hover `signal-hover`. |

## What the consumer provides

- The element: `<a>` for navigation, `<button>`/`<input type=submit>` for form posts — the look is shared, the semantics are not (orbi-cloud #300). `font: inherit` keeps a `<button>` on the same baseline as a neighbouring `<a>` (#311).
- The label, in the page's language, verb first. External links carry a trailing ↗ on the marketing site.
- A group: wrap several in `orbi-row` (gap `space-2`; marketing CTAs use `space-brand-cta-gap`).

## Rules

- On the brand (dark) theme every button is square and 48px; on the product theme they are 6px-rounded and text-height.
- White on the product green is 4.52:1 — do not lighten `accent` or shrink the label below 16px.
- Focus: 2px `focus-ring` in product; 3px `signal`, offset 4px, on the brand surface.
