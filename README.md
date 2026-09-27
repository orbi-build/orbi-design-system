# Orbi Design System

The shared tokens, type, components and brand rules for every Orbi surface: the marketing site (orbi.build, `orbi-build/orbi-website`) and the Orbi Cloud dashboard (`orbi-build/orbi-cloud`).

**How to use it (people and agents):**

- Read this README first, then the component you are about to touch: `components/<Name>/README.md` (rules) and `components/<Name>/preview.html` (reference markup; styles in `components/bundle.css`).
- Take colors, spacing, radii and type from `tokens.json`. The `light` theme is the product dashboard; the `dark` theme is the brand night surface. Do not invent new colors, radii or component styles; if a page needs something the system lacks, add it here first.
- Raw files are public: `https://raw.githubusercontent.com/orbi-build/orbi-design-system/main/<path>`, or `gh repo clone orbi-build/orbi-design-system`.

**Source of truth:** the editable system lives in Claude (Design System artifact). This repository is its exported copy; re-export and open a PR here after changing it. Values were extracted on 2026-09-24 from `orbi-website@4f1afd6` (`public/styles.css`, logos) and `orbi-cloud@c54feae` (`src/page.ts`, `src/pages/status.ts`, fonts).

---

Orbi turns a labelled GitHub Issue into a reviewed, merged pull request and a tagged release. The system has two surfaces that share one palette of names: the **brand** surface (orbi.build, the proof pages, OG images — night and paper, amber and teal) and the **product** surface (the Orbi Cloud dashboard — a quiet, GitHub-like light UI). The `light` theme is the product, the `dark` theme is the brand night.

## Content fundamentals

- Say what happened and what to do next, in that order. Dashboard copy is plain Chinese by default with an English mirror: 「Orbi 正在写代码」, 「需要你处理：里程碑 v0.6.43 不存在」, 「创建它之后 Orbi 会自己继续。」
- Address the reader as 你 / you. Orbi speaks of itself in the third person by name ("Orbi 待命中"), never "we" inside the product.
- Marketing headlines are two short declaratives: "File an Issue. Get a release." The second sentence is set in `signal`.
- State words are short and fixed: 已排队, 进行中, 受阻, 等你确认, 已合并, 已关闭. Do not invent synonyms.
- Numbers are exact and in mono where they are data (counts, timestamps, token usage, receipts).
- No emoji. The only glyphs in use are ✓ (trust line), › (row arrow), ↗ (external link), → (proof title), and the circled numerals ① ② ③ that order the dashboard's sections.
- Engine output (a blocked reason) is quoted verbatim in mono, never paraphrased.

## Color

- Product: ground `surface-page`, panels `surface-raised`, text `ink`, secondary `ink-muted`, every border `border-default`. One green (`accent`) for the primary action; `info` blue for "look here" (the next-action border, the primary card's top rule, focus, working dot); `success` / `danger` / `warning` only for state.
- Brand: ground `night` (dark theme `surface-page`) or `paper`; text `ink` on night, `paper-ink` on paper. `signal` amber is the one loud colour — the CTA, the highlighted half of a headline, focus — and `run` teal means alive / done. On paper use `signal-on-light` and `run-on-light` for text; `signal` itself is 1.56:1 there.
- Tints (`success-soft`, `warning-soft`, `danger-soft`, `info-soft`) are grounds for their own ink, never for body copy of another state.
- Failing source pairs are kept and flagged in their token notes: `border-default` on white (1.43:1, input borders), `line` on paper, `warning-border` on `warning-soft`, `success` on `info-soft` (4.46:1).

## Type

- Brand: `display` (Familjen Grotesk, 600, tight −0.055em tracking) for headlines and big numbers; `body` (Instrument Sans, 17px/1.6) for copy; `mono` (IBM Plex Mono) for labels, uppercase at 0.7rem with +0.1em tracking. Chinese uses the system CJK stack (PingFang SC, Hiragino Sans GB, Microsoft YaHei, Noto Sans CJK SC); no Chinese web font is loaded.
- Product: `ui` (system-ui) at 16px/1.6; `ui-title` 1.4rem, `ui-heading` 1.05rem, `ui-section-label` 0.8rem uppercase; `ui-mono` for counts and engine reasons.
- Familjen Grotesk 400/700 and IBM Plex Mono 400 ship as files (Latin subset, from orbi-cloud's OG-image assets). Instrument Sans and the 500/600 weights come from Google Fonts.

## Space, radius, shadow

- Product spacing is the rem ladder `space-1` … `space-6` (0.25–1.5rem); cards pad `space-5` × `space-6`.
- Brand spacing is literal: 19px button sides, 12px CTA gap, 28px panel padding, and a 72px line grid over night sections.
- Product rounds: `radius-control` 6px, `radius-card` 8px, `radius-pill` for chips. The brand never rounds (`radius-none`), except the 5px newsletter input.
- Shadows are rare: `shadow-card-primary` on the one primary card; on paper, the hard `shadow-brand-offset` under proof shots. No soft glows on product cards.

## Layout

- Dashboard: one column, `size-dashboard` (880px) max, sections in the fixed order ① 需要你处理 → ② 正在发生 → ③ 交付记录. At ≤480px tables become two-line rows and every control reaches `size-tap`.
- Marketing: `size-site` (1400px) shell, dark hero band over the paper body.

## States and focus

- Focus is always visible: 2px `focus-ring` (blue) in product, 3px `signal` offset 4px on the brand surface.
- Hover: `accent-hover` for primary buttons, `info-soft` for rows; brand buttons lift 2px.

## Iconography

- No icon set. The dashboard draws two 20px inline SVG status icons (circled × for error, triangle ! for warning) with `currentColor` at 1.7 stroke; status dots are plain circles.
- The mark: `logo-mark.svg` on light grounds, `logo-mark-on-dark.svg` on night, `favicon.svg` for tabs. See Logos.

## Not synced

- Components are hand-written static renditions (plain HTML + `components/bundle.css`), not a built library — the sources render HTML strings in TypeScript, with no component package to build.
- Instrument Sans has no files in either repo; Familjen Grotesk 500/600 and Plex Mono 500 are not in the repo either.
- Not placed: the marketing `.night` radial and linear background gradients (composite values), `clamp()` sizes (the max is recorded), the proof receipt's torn-edge radial pattern, and `badge.svg` (a third-party shields-style badge, not the brand).
- The `dark` theme values for `info`, `danger-soft` and `track` are mappings, not source values; `merged` and `scrim` have no brand value and inherit.
