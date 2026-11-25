# Verification Pass (2026-11-25)

## How the research went
Thirteen agents researched in parallel. They shared one web-search budget (about 200
queries per turn across every agent), and that budget ran out partway through. The
network policy also blocks fetching most sites, including Wikipedia and ESPN. So:

- **Membership, commissioners, CFP format and the big money figures** were checked
  against live sources, either by the agents or by this verification pass.
- **School-level detail** comes largely from model knowledge (up to about mid-2026):
  leadership, budgets, US News ranks, DMA ranks and endowments. Every such record carries
  `confidence: "low"` and/or a `lowConfidenceFields` list. The engine treats seed values as
  starting points, and leadership changes after the start date are simulated anyway.

## High-impact facts checked against live sources in this pass

| Claim | Result | Sources |
|---|---|---|
| CFP expands to 24 teams in 2027 (P4 champs + top G6 + 19 at-large); P4 title games end after 2026; ESPN ~5-yr deal | **Confirmed.** Announced 2026-11-09. Rounds 1–2 are on campus, QF/SF are at bowls, and the first 24-team final is Jan 24, 2028 in New Orleans. Notre Dame's top-12 guarantee ends in 2027. | [Chicago Sun-Times](https://chicago.suntimes.com/college-sports/2026/11/09/college-football-playoff-expands-to-24-teams-eliminating-league-title-games), [FBSchedules](https://fbschedules.com/college-football-playoff-officially-expanding-to-24-teams-in-2027/), [ABC7](https://abc7.com/post/cfp-24-team-format-what-need-know-new-playoff/20027109/) |
| Brett Yormark leaving the Big 12 | **Confirmed.** Announced 2026-10-30, effective 2027-01-31. He becomes CEO of Milan Sports & Entertainment (RedBird-backed). The Big 12 board is running the search. | [Front Office Sports](https://frontofficesports.com/article/brett-yormark-stepping-down-as-big-12-commissioner-after-4-years/), [KCTV5](https://www.kctv5.com/2026/10/30/big-12-commissioner-brett-yormark-step-down-january-2027/), [Deseret News](https://www.deseret.com/sports/2026/11/13/brett-yormark-has-a-new-home-in-milan/) |
| Tim Brosnan succeeded Val Ackerman at the Big East | **Confirmed.** Named Aug 2026 and started 2026-09-01. Former MLB COO. | [NBC Sports](https://www.nbcsports.com/big-east/news/tim-brosnan-named-sixth-big-east-commissioner-will-succeed-val-ackerman-in-september), [ESPN](https://africa.espn.com/college-sports/story/_/id/49507446/source-former-mlb-executive-tim-brosnan-head-big-east) |
| Protect College Sports Act passed the Senate 77-22 | **Confirmed.** Passed 2026-09-28; Cruz/Cantwell bill. The House can only act in the lame-duck session. | [OPB/NPR](https://www.opb.org/article/2026/09/29/senate-passes-protect-college-sports-act-bill-s-future-unclear/), [Axios](https://www.axios.com/2026/09/29/protect-college-sports-act-nil-senate), [Texas Tribune](https://www.texastribune.org/2026/09/28/ted-cruz-college-sports-bill-passes-senate-nil-ncaa/) |
| SEC v. LSU (pro-player eligibility); possible expulsion | **Confirmed and live.** The SEC sued LSU, Lane Kiffin and LSU leaders in federal court (N.D. Ala.) in Sept 2026. A Sept 10 meeting ended with no vote. A second threat followed over RJ Luis (basketball): a Baton Rouge state-court injunction made him eligible, and the SEC set a **Dec 3, 2026** presidents' meeting on LSU's membership. Expulsion needs 2/3 and is seen as unlikely. | [WAFB](https://www.wafb.com/2026/09/03/sec-sues-lsu-lane-kiffin-former-nfl-player-fight-escalates/), [ABC News](https://abcnews.com/Sports/wireStory/southeastern-conference-new-federal-court-filing-threatening-kick-138395642), [CBS Sports](https://www.cbssports.com/college-football/news/sec-lsu-expulsion-vote-rj-luis-will-wade-lane-kiffin/), [ESPN](https://www.espn.com/college-football/story/_/id/50522883/judge-questions-lsu-claims-sec-hallucinated-citations) |
| JMU to the American | **Confirmed.** Announced 2026-10-12, then moved up to 2027-07-01. Reported costs: $5M Sun Belt exit and a $23M American entry fee, both privately funded. Sun Belt drops to 13. | [FBSchedules](https://fbschedules.com/james-madison-to-officially-join-american-conference-in-2027/), [Front Office Sports](https://frontofficesports.com/article/james-madison-joins-the-american-before-sun-belt-exit-fees-rise/) |
| North Dakota State to the Mountain West, football only | **Confirmed.** Joined 2026-07-01 as the 10th football member. Pays $5M to the NCAA and ~$12M to the MWC. Ineligible for CFP and bowls in 2026–27. Other sports stay in the Summit. | [NDSU](https://www.ndsu.edu/mountain-west), [ESPN](https://africa.espn.com/college-football/story/_/id/47870245/sources-north-dakota-state-joins-mountain-west-football) |
| UC Davis to the Mountain West, non-football | **Confirmed.** 2026-07-01. Football stays in the Big Sky (FCS). | [UC Davis](https://ucdavisaggies.com/news/2024/12/10/athletics-uc-davis-to-join-mountain-west-conference-in-2026-27), [CBS Sports](https://www.cbssports.com/college-basketball/news/uc-davis-to-join-mountain-west-aggies-join-conference-in-all-sports-except-football-starting-in-2026) |
| Sacramento State: Big West in other sports, MAC football-only | **Confirmed.** Left the Big Sky in 2026; Big West in all sports but football. | [ESPN](https://www.espn.com/college-sports/story/_/id/45539731/sacramento-state-join-big-west-all-sports-football), [CBS Sports](https://www.cbssports.com/college-football/news/sacramento-state-withdraws-from-big-sky-as-hornets-move-forward-with-risky-bet-on-future-fbs-football-success) |
| Gloria Nevarez remains MWC commissioner | **Confirmed.** Extended through 2030-12-31 (Dec 2025). | [Fox Sports](https://www.foxsports.com/articles/cfb/mountain-west-conference-extends-commissioner-gloria-nevarezs-contract-4-years-through-2030) |
| Big Ten–UC Investments private capital deal | **Paused** 2025-11-17 after Michigan and USC objected. The deal was $2.4B for a 10% stake in "Big Ten Enterprises" plus a GOR extension to 2046. UC said it won't sign without unanimity. No 2026 revival found. | [ESPN](https://africa.espn.com/college-sports/story/_/id/47003108/opposition-michigan-usc-pauses-24b-big-ten-deal), [Eleven Warriors](https://www.elevenwarriors.com/the-big-ten/2025/11/159589/big-ten-s-2-4-billion-private-equity-deal-with-uc-investments-on-hold-due-to-opposition-from-michigan-usc) |
| MAC–ESPN deal | **Confirmed it expires after 2026–27.** It was a 13-yr, ~$100M deal from 2014. No successor found, so it is **an open negotiation at game start**. | [ESPN Press Room](https://espnpressroom.com/press-release/espn-and-mid-american-conference-extend-exclusive-multi-platform-agreement-through-2026-27/), [WOUB](https://woub.org/2014/08/19/mac-espn-extend-rights-deal-through-2027/) |
| Pac-12 media value | **Undisclosed.** CBS (primary, through 2030–31), The CW (66 events/yr, 2026–31) and USA Network (22 FB games/yr, 5 yrs). Estimates run **$7–10M per school per year**. | [CBS Sports](https://www.cbssports.com/college-football/news/cbs-sports-pac-12-extend-partnership-with-network-becoming-primary-partner-as-league-eyes-expansion), [Spokesman-Review](https://www.spokesman.com/stories/2025/nov/15/mailbag-grading-the-pac-12s-media-rights-deals) |
| CFP executive director | **Rich Clark**, still in the role in 2026. | [CFP](https://collegefootballplayoff.com/news/2026/7/13/frick.aspx), [CBS Sports](https://www.cbssports.com/college-football/news/college-football-playoff-hires-air-forces-richard-clark-as-executive-director-to-replace-bill-hancock) |
| House cap 2026–27 | **~$21.3M** (+4% from $20.5M), projected to reach ~$32.9M by 2034–35. | [Inside the Loud House](https://insidetheloudhouse.com/syracuse-will-pay-its-athletes-the-maximum-amount-allowed-21-3-million-next-season), [Legion Report](https://legionreport.com/house-settlement-explained/) |

Confirmed by agents with sources (see their notes):
- Petitti extended to June 2033 (2026-08-26)
- Gould extended to 2030–31
- SEC moves to 9 conference games in 2026
- ACC exit-fee schedule: $165M in FY2026, then −$18M/yr down to $75M
- Pac-12/MWC litigation settled 2026-08-04
- Big Ten FY2025 distribution $1.37B vs. SEC $1.03B
- CFP revenue shares: SEC and Big Ten 29% each, ACC 17.25%, Big 12 14.75%

## Data integrity fixes applied
- **Removed duplicate school records** (the full-detail record wins):
  - `uc-davis`, `dayton` and `drake` from `fcs.json`
  - `saint-josephs` and `seattle-u` from `d1-other-light.json`
- **Football-only leagues** (`mvfc`, `big-south-ovc`, `pioneer`, `uac`): members moved to
  `footballOnly` and the leagues flagged `footballOnlyConference: true`.
- **Big Sky:** removed Sacramento State.
- **Big West:**
  - removed Hawaii and UC Davis
  - added Sacramento State
- **Horizon:** added Northern Illinois.
- **Added pseudo-conference** `independent-fcs` (Merrimack, Sacred Heart).
- **Rival IDs fixed:**
  - `appalachian-state` → `app-state`
  - `grambling` → `grambling-state`
  - dropped `tuskegee` (D-II)
- **Commissioners updated** in `conferences_nonfbs.json`:
  - Big East: Tim Brosnan
  - A-10: Dan Leibovitz
  - NEC: Ron Ratner (interim)
- **Coverage after fixes:**
  - 364 unique D-I schools; 138 FBS football programs in 2026
  - every member ID resolves to a school record, except `johns-hopkins` (Big Ten lacrosse
    affiliate, intentionally omitted)

## Known remaining gaps (accepted for Phase 1)
- G6 and pre-FY2025 distributions are estimates.
- Bowl payouts and 2026–31 tie-ins are partly estimated.
- Private-capital deal terms are low confidence, except the Big Ten/UC deal above.
- School finances, endowments, US News and DMA ranks are low confidence.
- Most 2026 in-season results are not captured; ratings reflect the start of the 2026 season.
- 2010-era presidents and ADs are not collected. The historical start will use real 2010
  commissioners plus generated campus leaders until a Phase 6 research pass.
