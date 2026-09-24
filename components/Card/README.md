# Card

The white panel that holds one topic of the dashboard: a repository, the subscription, the model config, the usage meter.

Hand-written from orbi-cloud `src/page.ts` (`.card`) and `src/pages/status.ts` (`.card.primary`, `.metric-card`).

## Anatomy

- `orbi-card`: `surface-raised`, 1px `border-default`, `radius-card`, padding `space-5` `space-6`, `space-4` below.
- `orbi-card orbi-card-primary`: the delivery card — adds a 2px `info` top border and `shadow-card-primary`. One per page.
- Inside: an `h2` (1.05rem) or an `orbi-section-label` (uppercase, `ink-muted`, 0.8rem, +0.04em), then content; secondary lines in `orbi-muted`.

## What the consumer provides

The heading, the body and any buttons. Numbered section headings (① 需要你处理, ② 正在发生, ③ 交付记录) come from the page, not the card.

## Rules

- Cards sit on `surface-page`; never nest a card inside a card (use a table or a list).
- On a phone (≤480px) the primary card's side padding drops to 0.75rem so a delivery row keeps 332px.
- The brand surface has no rounded cards: marketing panels are square with a 1–2px `line` border on `paper` (pricing card: 2px `line`, featured: `signal`). The dark theme renders `orbi-card` square for that reason.
