# IssuePickRow

One row per existing Issue the person can hand to Orbi right away: the Issue as a link on the left, 「让 Orbi 做这个」 on the right; on a phone the row stacks into two lines.

Hand-written from orbi-cloud `src/pages/status.ts` (`startPickRow()`, `.start-pick-row`, `.start-pick-title`). Used under 「选一个已有的 Issue 交给 Orbi。」/「或者选一个已有的 Issue」 in the next-step card, and for the demo repository's sample tasks.

## Anatomy

- Row: flex, title and button on one line, `space-3` gap, 0.35rem vertical padding, a 1px `border-default` top rule.
- Title: one link, `owner/name#number title`, `info` and underlined; it wraps (`overflow-wrap: anywhere`), never ellipsised — on a phone a cut title (`acme/shop#12 Fix t…`) hides which Issue the button starts (orbi-cloud #1823).
- Button: Button, 「让 Orbi 做这个」, does not shrink.

## What the consumer provides

The Issue's repository, number, title and URL, and whether this row's button is the page's one solid action.

## Rules

- At ≤480px each row stacks: line 1 the title link (wrapping as needed), line 2 the button at full width and at least `size-tap` (44px) tall; 0.5rem between them, 0.6rem vertical padding. Same treatment as the suggestion rows on that page, so every action button on a phone reads the same.
- Above 480px the row stays on one line: title left, button right.
- Only the first row's button may be solid, and only when nothing else on the page holds the one solid action (no suggestion block); every other row is `orbi-btn-secondary`.
- At most 3 rows.
