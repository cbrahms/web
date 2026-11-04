# The Magpie's Hoard

Static dashboard of reports published from Claude sessions. Entry point: `index.html`.

## Layout

| Path | Contents |
|------|----------|
| `index.html` | Dashboard. Sections: Unusual Wealth Activity (current), Archive, Links, Intelligence briefs, Scrabble, One-offs. |
| `pages/` | Current edition of each report. |
| `pages/archive/` | Superseded editions. Back-link points to `../../index.html`. |
| `style/README.md` | Aircraft Manual Style (AMS). Governs all report prose. |

## Standards

- **Prose:** AMS. Facts, inferences, and non-claims in separate labelled paragraphs.
- **Visual:** site tokens from `index.html` (teal accent, system sans, mono for data). Define every color on bare `:root`, redefine under `prefers-color-scheme: dark` guarded by `:root:not([data-theme="light"])`, and again under `:root[data-theme="dark"]`.
- **Evidence tiers:** Hard data / Corroborated / Thin or watch. Every signal carries a conventional-read line.
- **Panic meter:** 8 dimensions, 0–100, composite = mean. At least 3 dimensions must use new evidence in a run, or the run says so.

## Unusual Wealth Activity run procedure

1. Read the current page in `pages/` and its reversal conditions.
2. Search: insider filings, prime-broker positioning, Treasury auctions, FOMC, WGC gold, Berkshire/13F, private-credit gates, wealth-migration.
3. Exclude: market-moving political posts, single-person remarks, SEO blogs, commercially conflicted sources (hold at Thin).
4. Check every link with curl. Record 403 blockers on the page.
5. Write `pages/uwa-YYYY-MM-DD.html`. Move the prior edition to `pages/archive/` with `git mv` and fix its back-link.
6. Update `index.html`: current card, Archive row, Links, tally line.
7. Add all-day primary-calendar events for dated catalysts that could drop a security or the market. Search first to avoid duplicates.
8. Copy artifacts to Google Drive; add Drive links under Links.
9. Notify only when the verdict is confirmed or changes.

## Issue register

| Issue | Date | Verdict | Panic | Page |
|-------|------|---------|-------|------|
| 006 | 2026-11-04 | Confirmed | 68 | `pages/uwa-2026-11-04.html` |
| 005 | 2026-10-26 | Emerging | 67 | `pages/archive/uwa-2026-10-26.html` |
| 001 | 2026-08-07 | Confirmed | 68 | `pages/archive/uwa-issue-001.html` |

## Open tasks

- [ ] Google Drive: connector fails auth (no dynamic client registration). Reconnect, then copy `pages/uwa-2026-11-04.html` and add the link under Links.
- [ ] Social sources: no X, LinkedIn, or Reddit access in the run environment. Add a connector or accept web-search-only scope.
- [ ] Verify Berkshire Q3 cash against the 10-Q on EDGAR.
- [ ] 12 Nov: record 30-year auction result against reversal condition 1.
- [ ] 17 Nov: record Nvidia result and Morgan Stanley gross exposure against reversal condition 2.
- [ ] Mid-Nov: Q3 13F filings (hedge funds, Berkshire).
- [ ] Decide: should Intelligence briefs and Scrabble older editions also move to `pages/archive/`?
