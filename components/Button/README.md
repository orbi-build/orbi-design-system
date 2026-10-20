# Button

One action per button; the fill tells the reader which action is the main one.

Hand-written from orbi-cloud `src/page.ts` (`.cta`, `input[type=submit]`, `button`, `.cta.secondary`, `.cta.login`) and orbi-website `public/styles.css` (`.button`, `.button-signal`, `.button-ghost`).

## Variants

| class | when | look |
|---|---|---|
| `orbi-btn` (primary) | The one thing to do in this card: 创建 Issue, 一键创建里程碑并继续, a form submit. | `accent` fill, `on-accent` label, 600 weight, `radius-control`, padding `space-2` `space-4`. Hover `accent-hover`. |
| `orbi-btn orbi-btn-secondary` | Leaving or looking: 在 GitHub 上查看, 返回, 添加仓库. Same size and weight as primary, never the same fill. | `surface-raised` ground, `success-strong` label and 1px border (product); on night, the ghost button: transparent, `line-dark` border, `ink` label. |
| `orbi-btn orbi-btn-login` | Sign in with GitHub only. | `surface-inverse` fill, `on-inverse` label. |
| `orbi-btn-text` (alone, not with `orbi-btn`) | A control that looks like text and is not part of a sentence: 「看其他 N 个示例」, 「展开全部 / 收起」, 「换一批建议」, 「管理项目（1 / 上限 1）」, the links in a release's version area. | `info` label, no ground, no border, the font and weight of the text around it. Hover and press: underline only. Focus: 2px `focus-ring`, offset 2px. |
| `orbi-btn orbi-btn-cta` | The marketing call to action (Start Cloud with GitHub) and the proof page's closing CTA. Brand surface only, once per screen. | `signal` fill, `night` label, square (`radius-none`), `size-brand-button` tall, `space-brand-button-x` side padding, 0.92rem. Hover `signal-hover`. |

## Text button, link in a sentence, or clickable row

Three things look clickable without being a filled button. Pick by where the thing sits, not by the element:

- **Link in a sentence**: the words are part of a sentence and go to another page (「交付规则 ›」, 「看这一步怎么做 ▶」, 「用 Orbi 的示例新建一个 ↗」). A plain `<a>` in `info`, underlined at rest (NN/g, Guidelines for Visualizing Links).
- **Text button `orbi-btn-text`**: it stands on its own (its own line, a link row, the right end of a heading) and either acts on this page (expand, collapse, swap a batch, open a panel) or is a minor way out that sits next to real buttons. No underline at rest; underline on hover and press.
- **Clickable row**: the whole row is one target (RepoOverviewRow, an account-menu entry). `info-soft` across the full row width on hover and press; see README, States and focus.

The element follows the behaviour, not the look: `<button type="button">` for an action on the page, `<summary>` for a disclosure (the triangle comes from the one `summary` rule), `<a>` when it navigates. A disclosure that is a text button is `<summary class="orbi-btn-text">`.

The text button sets its own `background: none` on hover and press, so a page-wide `button:hover` fill never reaches it. No state gives a text button a ground, a border or a green colour; if it needs to look heavier, it is a secondary button.

## What the consumer provides

- The element: `<a>` for navigation, `<button>`/`<input type=submit>` for form posts — the look is shared, the semantics are not (orbi-cloud #300). `font: inherit` keeps a `<button>` on the same baseline as a neighbouring `<a>` (#311).
- The label, in the page's language, verb first. External links carry a trailing ↗ on the marketing site.
- A group: wrap several in `orbi-row` (gap `space-2`; marketing CTAs use `space-brand-cta-gap`).

## Rules

- On the brand (dark) theme every button is square and 48px; on the product theme they are 6px-rounded and text-height.
- White on the product green is 4.52:1 — do not lighten `accent` or shrink the label below 16px.
- Focus: 2px `focus-ring` in product, every variant including `orbi-btn-text`; 3px `signal`, offset 4px, on the brand surface.
