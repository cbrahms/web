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

- **Design source:** no `DESIGN.md` exists in either repo. Site tokens in `index.html` are the design system until one is added.

- **Prose:** AMS. Facts, inferences, and non-claims in separate labelled paragraphs.
- **Visual:** site tokens from `index.html` (teal accent, system sans, mono for data). Define every color on bare `:root`, redefine under `prefers-color-scheme: dark` guarded by `:root:not([data-theme="light"])`, and again under `:root[data-theme="dark"]`.
- **Evidence tiers:** Hard data / Corroborated / Thin or watch. Every signal carries a conventional-read line.
- **Panic meter:** 8 dimensions, 0–100, composite = mean. At least 3 dimensions must use new evidence in a run, or the run says so.

## Unusual Wealth Activity run procedure

1. Fetch all open `cspace/*` branches and PRs. Build on the newest unmerged issue, not on `main` alone.
1a. Read the current page in `pages/` and its reversal conditions.
2. Search: insider filings, prime-broker positioning, Treasury auctions, FOMC, WGC gold, Berkshire/13F, private-credit gates, wealth-migration.
3. Exclude: market-moving political posts, single-person remarks, SEO blogs, commercially conflicted sources (hold at Thin).
4. Check every link with curl. Record 403 blockers on the page. FRED series pages time out from the run environment; pull values from `https://fred.stlouisfed.org/graph/fredgraph.csv?id=<SERIES>`.
4b. Exclude unsourced fund-failure rumors (e.g. "fund X bankrupt") unless a primary outlet or filing confirms.
4a. Include at least one counter-signal (credit spreads, VIX) so the verdict is tested against market-wide data.
5. Write `pages/uwa-YYYY-MM-DD.html`. Move the prior edition to `pages/archive/` with `git mv` and fix its back-link.
6. Update `index.html`: current card, Archive row, Links, tally line.
7. Add all-day primary-calendar events for dated catalysts that could drop a security or the market. Search first to avoid duplicates.
8. Copy artifacts to Google Drive; add Drive links under Links.
9. Notify only when the verdict is confirmed, changes, or a market event tests it (e.g. index drop above 3%).

## Issue register

| Issue | Date | Verdict | Panic | Page |
|-------|------|---------|-------|------|
| 010 | 2026-11-08 | Confirmed (held) | 69 | `pages/uwa-2026-11-08.html` |
| 009 | 2026-11-07 | Confirmed (strengthened) | 69 | `pages/archive/uwa-2026-11-07.html` |
| 008 | 2026-11-06 | Confirmed (held) | 68 | `pages/archive/uwa-2026-11-06.html` |
| 007 | 2026-11-05 | Confirmed (held) | 68 | `pages/archive/uwa-2026-11-05.html` |
| 006 | 2026-11-04 | Confirmed | 68 | `pages/archive/uwa-2026-11-04.html` |
| 005 | 2026-10-26 | Emerging | 67 | `pages/archive/uwa-2026-10-26.html` |
| 001 | 2026-08-07 | Confirmed | 68 | `pages/archive/uwa-issue-001.html` |

## Open tasks

- [ ] Google Drive: connector failed auth on 04–06 Nov and again on 08 Nov ("incompatible auth server: does not support dynamic client registration"); on 07 Nov the upload was blocked by the permission classifier. Owner action: reconnect Drive in claude.ai connector settings and allow Drive writes for this routine, then copy issues 006–010 and add links under Links.
- Artifacts: live (issue 010, prior 009 version archived on site) https://claude.ai/artifact/WdxJt2xVGWtJhpeozHJFJ7 · issue 006 https://claude.ai/artifact/WEd8CJZmHziH7yhZu9Xi4w
- [ ] Merge PRs: branch `cspace/quirky-galileo-rccrxe` (issue 010) contains all of `cspace/quirky-galileo-2cwdvz` (issue 009) and the older run branches. Merge the newest and close the older PRs.
- [ ] Social sources: no X, LinkedIn, or Reddit access in the run environment. Add a connector or accept web-search-only scope.
- [ ] Verify Berkshire Q3 2026 cash against the 10-Q on EDGAR (not found on 7 Nov).
- [ ] 12 Nov: record 30-year auction result against reversal condition 1.
- [ ] 17 Nov: record Nvidia result and Morgan Stanley / Goldman gross exposure against reversal condition 2.
- [ ] Re-read December hike odds (CME FedWatch) for reversal condition 3; last reading ~77% on 6 Nov after jobs report.
- [ ] 10 Nov: record October CPI and 10-year auction result (both on calendar).
- [x] 08 Nov: named pod cuts found (Walleye equity unit, Engineers Gate stock team). Next run: watch for further cuts and any named fund closure; check Q4 BDC tender requests.
- [ ] 16 Nov calendar entry (AI IPO roadshow) is tentative. Update or delete it when a date or postponement is announced.
- [ ] Weekend runs have no market data and usually meet the 3-new-dimension rule only partly. Decide: skip Saturday/Sunday runs, or keep them as news-only editions.
- [ ] Watch high-yield OAS (FRED BAMLH0A0HYM2; 3.48% on 5 Nov). A move above 4% would upgrade the pattern from leading-holder positioning to market-wide stress.
- [ ] Mid-Nov: Q3 13F filings (hedge funds, Berkshire).
- [ ] Decide: should Intelligence briefs and Scrabble older editions also move to `pages/archive/`?
