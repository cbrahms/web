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
| 015 | 2026-11-13 | Confirmed (held, restored) | 70 | `pages/uwa-2026-11-13.html` |
| 014 | 2026-11-12 | Confirmed (weakened) | 69 | `pages/archive/uwa-2026-11-12.html` |
| 013 | 2026-11-11 | Confirmed (held) | 70 | `pages/archive/uwa-2026-11-11.html` |
| 012 | 2026-11-10 | Confirmed (held) | 70 | `pages/archive/uwa-2026-11-10.html` |
| 011 | 2026-11-09 | Confirmed (held) | 70 | `pages/archive/uwa-2026-11-09.html` |
| 010 | 2026-11-08 | Confirmed (held) | 69 | `pages/archive/uwa-2026-11-08.html` |
| 009 | 2026-11-07 | Confirmed (strengthened) | 69 | `pages/archive/uwa-2026-11-07.html` |
| 008 | 2026-11-06 | Confirmed (held) | 68 | `pages/archive/uwa-2026-11-06.html` |
| 007 | 2026-11-05 | Confirmed (held) | 68 | `pages/archive/uwa-2026-11-05.html` |
| 006 | 2026-11-04 | Confirmed | 68 | `pages/archive/uwa-2026-11-04.html` |
| 005 | 2026-10-26 | Emerging | 67 | `pages/archive/uwa-2026-10-26.html` |
| 001 | 2026-08-07 | Confirmed | 68 | `pages/archive/uwa-issue-001.html` |

## Open tasks

- [ ] Calendar privacy: dashboard Links include Google Calendar `eid` URLs, which encode the account email. The hoard sync strips them before `main`. Decide: keep on run branches, or list calendar entries as plain text.

- [x] Google Drive: connector working 13 Nov. Folder "Unusual Wealth Activity" (https://drive.google.com/drive/folders/1agaZjWGRQWx2aeHr1wXJ2m7htRMM2CMK) holds the current issue as a Google Doc; prior issues go in its `Archive` subfolder. Each run: upload new issue, move the prior Doc to Archive. Issue 015 uploaded; issue 014 moved to Archive.
- [ ] Drive backfill: copy issues 006–010 into the Drive Archive subfolder.
- Artifacts: live, updated in place each run (issue 015 on 13 Nov; prior editions archived on site) https://claude.ai/artifact/WdxJt2xVGWtJhpeozHJFJ7 · issue 006 https://claude.ai/artifact/WEd8CJZmHziH7yhZu9Xi4w
- [ ] Merge PRs: branch `cspace/quirky-galileo-9a78i1` (issue 011) contains all of `cspace/quirky-galileo-rccrxe` (issue 010) and the older run branches. Merge the newest and close the older PRs.
- [ ] Social sources: no X, LinkedIn, or Reddit access in the run environment. Add a connector or accept web-search-only scope.
- [x] Berkshire Q3 2026 (7 Nov): cash $377.4B headline, $352.3B ex-rail/utility; buybacks $9.6B. Recorded as CTR-01 in issue 011.
- [x] Berkshire 10-Q (10 Nov): Q3 equity purchases $2.37B, sales $2.79B (net seller $0.43B) from 9M minus 6M cash-flow lines. Recorded as CTR-01 (narrowed) in issue 012.
- [x] 13 Nov: 12 Nov 30-year auction recorded (issue 015 SIG-01). High yield 5.441% (≥ 5.3%), so reversal condition 1 FAILED and the verdict is restored to Confirmed (held). Indirect 68.1% (down from 72.3%; passes the >68% share test by 0.1 pt). Second weak refunding auction; reserve-currency dimension raised to 77. Condition 1 now closed; proposed replacement = 24/25 Nov 2y/5y auctions both indirect >65% with no tail.
- [ ] 12 Nov (MAJOR): Nvidia CEO Jensen Huang resigned over a foreign-intelligence probe; CFO Colette Kress interim CEO; stock −4.3% to $166.19. Recorded as issue 015 SIG-02; institutional-integrity dimension raised to 66. Track: whether Nvidia's $10B Anthropic IPO placement commitment holds; 17 Nov earnings under interim CEO; any CEO search outcome.
- [ ] Nvidia 18 Nov briefing / "1 Dec House interview": the 18 Nov closed-door briefing was requested of Huang before he resigned; one search headline (CNN, page blocked 451) referenced a 1 Dec interview of the "former CEO." Confirm the date with a second source, then add an all-day calendar entry once the Calendar connector is re-authenticated.
- [ ] 17 Nov: record Nvidia result and Morgan Stanley / Goldman gross exposure against reversal condition 2.
- [ ] Re-read December hike odds (CME FedWatch) for reversal condition 3. 11 Nov: hot CPI; Logan wants two more hikes; coverage says near-certain. No verified percentage yet.
- [ ] Decide: adopt proposed reversal condition 4 (S&P 500 record close with VIX < 18). Issue 014: 2.6% below record, VIX 19.46. Without it, the conditions cannot register an equity-led all-clear.
- [ ] Run timing: the routine fires about 12:45 UTC, before US data and auctions. Consider moving to ~22:00 UTC so each issue includes the day's close and auction results.
- [ ] Google Calendar: connector returned "needs you to sign in again" on 13 Nov; no entries changed. Re-authenticate (`/mcp`) before the next dated catalyst so drop-risk events can be added.
- [x] 12 Nov: AI IPO book several times covered (reclassified CTR-02, reverses issue 013 SIG-03). CoreWeave Q3: debt $35B → $47B, net loss $709M, interest $846M (SIG-01).
- [ ] 16 Nov: Prop. 40 count closes; certification 11 Dec. Watch for reported return moves by relocated billionaires.
- [ ] CoreWeave: confirm the ~15% unsecured-yield figure from a primary bond quote (single AI-translated source).
- [x] 11 Nov: October CPI +0.4% m/m, core +0.3% (both above forecast). 10-year auction 5.02%, bid-to-cover 2.46, indirect 61.2%. Recorded as SIG-01/02 in issue 013.
- [ ] Treasury auction primary source: Fiscal Data `auctions_query` returned no rows for 10 Nov on 11 Nov. Retry, or use the TreasuryDirect results PDF, to move SIG-01 to Hard data.
- [ ] 13 Nov: record October PPI (calendar entry added 10 Nov). A hot print raises 50 bp odds.
- [x] Anthropic IPO (10 Nov): range $70–78, 825M shares, up to $64.4B; $26B strategic commitment. Calendar entry moved from 16 Nov to 19 Nov (first trade, reported).
- [ ] 18–19 Nov: record IPO pricing vs range. Below range = further withdrawal of capital from AI risk.
- [ ] BCRED Q4 tender: deadline 1 Dec; result in a later SC TO-I/A. Find a primary EDGAR link (AltStreet blocks automated clients).
- [x] 08 Nov: named pod cuts found (Walleye equity unit, Engineers Gate stock team). Next run: watch for further cuts and any named fund closure; check Q4 BDC tender requests.
- [ ] Weekend runs have no market data and usually meet the 3-new-dimension rule only partly. Decide: skip Saturday/Sunday runs, or keep them as news-only editions.
- [ ] Watch high-yield OAS (FRED BAMLH0A0HYM2; 3.30% on 11 Nov, lowest this month; 3.48% on 5 Nov). A move above 4% would upgrade the pattern from leading-holder positioning to market-wide stress. VIX 17.49 on 11 Nov — the counter-signal (CTR-01) is strong: credit and options have not priced the weak-auction bond leg.
- [ ] Mid-Nov: Q3 13F filings (hedge funds, Berkshire).
- [x] CoreWeave Q3 2026 (reported 10 Nov): found 12 Nov; recorded as SIG-01 in issue 014.
- [ ] Nvidia CEO probe (09 Nov): track board findings. Closed-door congressional briefing requested for 18 Nov (all-day calendar entry added 11 Nov). 9 Nov close $178.67, lowest since 7 Apr. Unverified "FBI investigating" headline excluded 10 Nov; confirm or drop.
- [ ] Prop. 40 (California billionaire tax): record final certified result; early returns 43–57% against.
- [ ] Decide: should Intelligence briefs and Scrabble older editions also move to `pages/archive/`?
