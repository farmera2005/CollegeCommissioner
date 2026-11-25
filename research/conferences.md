# FBS Conferences: 2026-27 research notes

Owner: fbs-conferences agent. As of **2026-11-25**.
Files: `data/conferences.json` (11 records: 10 FBS conferences + `independent`), `data/calendar.json` (65 events), this note, and `research/legal-exit-fees-gor.md`.

**Research limits.** The shared web-search budget ran out partway through, and WebFetch could not reach most outlets (network allowlist). Items confirmed by 2026 reporting carry sources and no flag. Venues, tournament sites, media-day sites, protected-rivalry lists, distribution dollars and governance thresholds that rest on pre-2026 knowledge are marked `"confidence": "low"` in the JSON. A follow-up pass should target those fields first.

## File shapes

- `conferences.json`: array of `Conference` records per SCHEMA.md. Extra optional fields: `commissioner.startDate`, `commissioner.departs` (Big 12), `commissioner.note`, `members2026.notes`, `members2026.affiliatesNote`, `football.protectedRivalriesNote`, `football.notes`, `foundedNote`, plus nested `confidence`/`note` on individual sub-objects.
  - `full` means all-sports members that play football in the league. `nonFootball` (Notre Dame in the ACC, Gonzaga in the Pac-12, Grand Canyon and UC Davis in the MWC, Wichita State in the American) is kept separate, so the total membership is `full + nonFootball`.
  - The `independent` pseudo-record lists Notre Dame and UConn under `footballOnly`.
- `calendar.json`: `{asOf, notes, events:[{id, name, month, dateOrRange, location, recurring, notes, sources, confidence?}]}`. `dateOrRange` is `YYYY-MM-DD`, `YYYY-MM-DD/YYYY-MM-DD`, or `YYYY-MM (text)` when only the month is known.

## Commissioners (2026-27)

| Conf | Commissioner | Since | Contract | Status |
|---|---|---|---|---|
| SEC | Greg Sankey | 2015 | not public | stable |
| Big Ten | Tony Petitti | May 2023 | **June 2033**; 5-yr extension, unanimous, announced 2026-08-26 ([Big Ten](https://bigten.org/article/60264/), [Fox](https://www.foxsports.com/stories/college-football/big-ten-commissioner-tony-petitti-extension-b1g)) | stable |
| Big 12 | Brett Yormark | Aug 2022 | was through 2030 ([NBC](https://www.nbcsports.com/college-football/news/big-12-commissioner-brett-yormark-receives-3-year-contract-extension-through-2030)) | **Leaving 2027-01-31** to become CEO of a RedBird/AC Milan venue-and-entertainment company ([Big 12](https://big12sports.com/news/2026/10/30/general-commissioner-brett-yormark-to-leave-big-12-conference.aspx), [Deseret](https://www.deseret.com/sports/2026/11/13/brett-yormark-has-a-new-home-in-milan/)). Search run by the Board (chair Douglas Girod, Kansas); no hire yet. |
| ACC | Jim Phillips | Feb 2021 | into 2029 (2023 extension) ([CBS](https://www.cbssports.com/college-football/news/acc-commissioner-jim-phillips-to-sign-three-year-extension-after-being-a-target-to-lead-big-ten)) | stable |
| Pac-12 | Teresa Gould | Mar 2024 | **through 2030-31**; 5-yr extension, June 2026 ([Pac-12](https://pac-12.com/news/2026/6/15/general-pac-12-board-of-directors-extends-contract-of-commissioner-teresa-gould.aspx), [ESPN](https://africa.espn.com/college-sports/story/_/id/49077989/pac-12-commissioner-teresa-gould-gets-5-year-extension)) | stable |
| Mountain West | Gloria Nevarez | Jan 2023 | **Dec 31, 2030** (Dec 2025 extension) ([WTOP/AP](https://wtop.com/news/2025/12/mountain-west-conference-extends-commissioner-gloria-nevarezs-contract-4-years-through-2030)) | stable |
| American | Tim Pernetti | Jul 2023 | not public | named in Big 12 speculation ([Heartland](https://www.heartlandcollegesports.com/2026/10/30/big-12-commissioner-candidates-replace-brett-yormark/)) |
| C-USA | Judy MacLeod | Oct 2015 | not public | wants to get back to 12 members ([FOS](https://frontofficesports.com/article/conference-usa-commissioner-seeks-to-expand-to-12-teams/)) |
| Sun Belt | Keith Gill | 2019 | not public | not re-verified (low) |
| MAC | Jon Steinbrecher | 2009 | not public | no retirement news found (low) |

## Per-conference notes

### SEC (16)
- **Nine conference games from 2026.** Each team has 3 annual opponents plus 6 rotating, and must also play one non-conference Power 4 game. Annual opponents are reviewed every 4 years (2026-29 cycle). There are no divisions. ([ESPN](https://www.espn.com/college-football/story/_/id/46355065/sec-college-football-future-schedule-release-2026-2029), [CBS](https://www.cbssports.com/college-football/news/sec-football-schedule-league-releases-every-game-for-2026-29-with-three-annual-opponents-for-each-team))
- All 24 annual pairings are in the JSON. Each team appears exactly 3 times, but some pairings are reconstructed from memory (low).
- Storylines: SEC vs Big Ten fights over CFP format (16 vs 24 teams, auto-bids); reports of a possible SEC/Big Ten breakaway ([Press Democrat mailbag, May 2026](https://www.pressdemocrat.com/2026/05/23/mailbag-breaking-down-the-pac-12-mountain-west-settlement-the-sec-big-ten-breakaway-the-poinsettia-bowl-and-more/)). Oklahoma and Texas were on reduced shares in year one.

### Big Ten (18)
- Nine games, no divisions, Flex Protect scheduling.
- Petitti's extension positions him for the post-2030 media cycle. The 2025 Big Ten Enterprises private-equity plan (UC Investments, GOR extension) stalled over Michigan/USC objections; status not re-verified.
- Pushing a 24-team CFP; the ACC backed the push in May 2026.

### Big 12 (16; unchanged)
- **Commissioner vacancy is the big 2026-27 storyline.** The next commissioner inherits media rights through 2030-31 and Yormark's PE/brand agenda.
- Texas Tech booster Cody Campbell was rumored for the job and denied it ([EssentiallySports](https://www.essentiallysports.com/ncaa-college-football-news-texas-techs-billionaire-booster-breaks-silence-after-rumrs-link-him-to-replace-departing-big-twelve-commissioner-cody-campbell-brett-yormark/)).
- AP quoted Pernetti on Memphis' "attempted move to Big 12"; date and details not verified.

### ACC (17 football + Notre Dame)
- **Settlement of March 4, 2025** ended the FSU/Clemson suits:
  - The exit fee steps down from $165M in FY2026 (see `legal-exit-fees-gor.md`).
  - A school that pays the fee leaves with its own media rights.
  - The GOR runs to 2036.
  - Revenue is split 60% by viewership ("brand initiative") and 40% equally.
- **Nine conference games from 2026** (AD vote Sept 2025). A few teams play 8 in 2026 because of existing contracts. In 2027, 16 of 17 play 9, and the odd team plays 8 plus two P4 non-conference games. Every team must play at least 10 P4 games. ([CBS](https://www.cbssports.com/college-football/news/acc-votes-to-expand-football-schedule-to-nine-conference-games-10-power-4-games-each-season))
- Phillips expects "four or five years" of stability and says the new exit-fee structure deters FSU and Clemson. Each year the fee drops makes the FSU/Clemson temptation stronger.

### Pac-12 (8 football + Gonzaga)
- Relaunched July 1, 2026: OSU and WSU plus Boise State, Colorado State, Fresno State, San Diego State and Utah State (all from the MWC), Texas State (from the Sun Belt), and Gonzaga (non-football, from the WCC). ([Pac-12](https://pac-12.com/news/2025/6/30/general-pac-12-conference-welcomes-the-addition-of-texas-state-university.aspx), [SI](https://www.si.com/college/oregon-state/football/what-teams-are-in-the-new-pac-12-in-2026-2027))
- **Exactly 8 football members, the NCAA FBS minimum.** Losing one would put FBS status at risk, which is a strong event hook.
- Gould on expansion: "I think we're at that point" ([SI](https://www.si.com/college/boise-state/football/pac-12-commissioner-on-expansion-i-think-we-re-at-that-point-01jyhf6zhkmh)). Memphis was courted as football-only in 2025.
- CBS is the primary media partner ([CBS](https://www.cbssports.com/college-football/news/cbs-sports-pac-12-extend-partnership-with-network-becoming-primary-partner-as-league-eyes-expansion/)).
- The poaching/exit-fee war with the MWC was settled in Aug 2026.

### Mountain West (10 football; 14 schools per ABQ Journal)
- Full members: Air Force, Hawaii (full from 2026), Nevada, New Mexico, San José State, UNLV, Wyoming, UTEP (from C-USA).
- Football-only: Northern Illinois ($2M entry fee; women's gymnastics too) and North Dakota State ($12.5M entry fee; FBS transition, title-game/bowl ineligible unless waived).
- Non-football: Grand Canyon (2025) and UC Davis (2026; football stays in the Big Sky). Utah Tech is an affiliate in men's soccer and baseball.
- Sources: [ABQ Journal](https://www.abqjournal.com/sports/mountain-west-conference-2026-27-here-are-the-14-schools-full-members-and-sport-specific-newcomers/3074907), [ESPN NDSU](https://www.espn.com/college-football/story/_/id/47870245/sources-north-dakota-state-joins-mountain-west-football), [NSN](https://nevadasportsnet.com/news/reporters/inside-north-dakota-state-footballs-membership-agreement-to-join-the-mountain-west), [UH](https://www.hawaii.edu/news/2026/07/01/uh-joins-mountain-west-as-full-member/).
- New in 2026-27: men's soccer and men's swimming & diving added (21 sports). The CW deal runs through 2031.

### American (14 football)
- 12 all-sports members plus Army and Navy (football-only) and Wichita State (non-football). Rebranded "American Conference" in 2025.
- **JMU joins from the Sun Belt.** The board voted Oct 12, 2026 to join "no later than July 1, 2028". AP/Fox on Nov 19, 2026 reported the move was pushed up to July 1, 2027. JMU pays a $23M entry fee and about $5M to exit the Sun Belt, both privately raised. It moved fast to beat a Sun Belt vote on higher exit fees. ([WDBJ/Gray](https://www.wdbj7.com/2026/10/12/james-madison-accepted-into-american-conference-will-leave-sun-belt-by-2028/), [Fox](https://www.foxsports.com/stories/college-football/james-madison-american-conference-sun-belt-transition), [FOS](https://frontofficesports.com/article/james-madison-joins-the-american-before-sun-belt-exit-fees-rise/))
- Perennial poaching target for the Big 12 and Pac-12 (Memphis, Tulane, USF, UTSA).

### Conference USA (10)
- Lost Louisiana Tech and UTEP on July 1, 2026. Remaining members: Delaware, FIU, Jacksonville State, Kennesaw State, Liberty, Middle Tennessee, Missouri State, New Mexico State, Sam Houston and WKU.
- **La Tech standoff.** C-USA requires 14 months' notice. La Tech sued, and the case settled in April 2026 for a reported record exit fee of more than $8M. C-USA had threatened punitive scheduling. ([WTOP/AP](https://wtop.com/ncaa-football/2026/04/louisiana-tech-clear-for-move-this-summer-to-sun-belt-after-settlement-with-conference-usa/), [FBSchedules](https://fbschedules.com/report-louisiana-tech-to-pay-record-exit-fee-to-leave-cusa-join-sun-belt/))
- MacLeod wants 12 members. The natural pool is FCS move-ups.

### Sun Belt (14)
- Louisiana Tech replaced Texas State in the West division. Divisions remain.
- JMU leaves in 2027 (or 2028), dropping the East to 6, so a replacement search is coming. The board was preparing an exit-fee increase in Oct 2026; the outcome is not verified.

### MAC (13 football)
- Sacramento State is football-only from July 1, 2026 on a 5-year term: $18M entry fee to the MAC plus a $5M NCAA reclassification fee; its other sports went to the Big West. It replaced NIU. UMass has been a full member since 2025. ([Sac State](https://hornetsports.com/news/2026/2/16/hornet-football-to-join-the-mac-in-2026.aspx), [ESPN](https://africa.espn.com/college-football/story/_/id/47933760/mac-add-sacramento-state-football-only-member))
- No divisions. Title game at Ford Field.

### Independents
- Notre Dame: ACC in other sports; plays ~5 ACC games a year; NBC deal; must join the ACC if it joins any football league before 2036.
- UConn: Big East otherwise. Perennial P4/Pac-12 candidate.

## Corrections to the brief

| Brief claim | Verdict |
|---|---|
| Tony Petitti extended through June 2033 | **True**. 5 years, unanimous, announced 2026-08-26. |
| Teresa Gould is Pac-12 commissioner | **True**. Extended June 2026 through 2030-31. |
| Big 12 unchanged at 16; Big Ten at 18 in 2026-27 | **True** for membership. **But the Big 12 commissioner is changing**: Yormark leaves 2027-01-31 and the search is open. The brief does not reflect this. |
| Pac-12 2026 lineup (OSU, WSU, Boise, CSU, Fresno, SDSU, USU, Texas State + Gonzaga non-football) | **True**. 8 football = FBS minimum. |
| Mountain West added NDSU, NIU, UTEP | **True, with detail**: NDSU and NIU are **football-only** (NIU also gymnastics); only UTEP is full. Also: **Hawaii became full** in 2026; **UC Davis** joined (non-football; add id `uc-davis`); Grand Canyon is **non-football**; Utah Tech is an affiliate. |
| Sacramento State to the MAC (football-only?) | **True**: football-only, 5-year term, from 2026. |
| Louisiana Tech to Sun Belt, leaving C-USA at 10 | **True**. Settled April 2026; effective July 1, 2026. |
| Commissioners: Nevarez (MW), Pernetti (American), MacLeod (C-USA), Gill (Sun Belt), Steinbrecher (MAC) | **True as far as found.** No 2025-26 changes except the Big 12. Gill and Steinbrecher not re-verified with 2026 sources (low). |
| ACC fee $165M FY2026, -$18M/yr to $75M, rights kept after paying | **True**. Schedule: 165 / 147 / 129 / 111 / 93, then 75 for FY2031-FY2036. |
| SEC moves to 9 games in 2026 | **True**, plus a mandatory 1 P4 non-conference game. |
| ACC 9 games | **Updated**: 9 games from 2026 for most teams (some at 8 in 2026); 16 of 17 at 9 in 2027. |
| Canonical IDs | Add `uc-davis` and `utah-tech` (MWC). JMU's future conference is `american` (2027). The American has 14 football members, not 15. |

## Game-model implications

- **Commissioner turnover event (Big 12 template).** A sitting P4 commissioner can be hired away by outside capital (Yormark to RedBird). Suggested annual chance a P4 commissioner leaves for an outside job: 3-5%, plus ~10% when their league is "stable". The search takes ~90 days, and a G6 commissioner (Pernetti-type) is a 25-35% favorite to be hired.
- **8-member FBS floor.** The Pac-12 sits exactly at the floor. Model a "membership crisis" state when football members ≤ 8: the NCAA gives a 2-year grace period, the media partner can renegotiate, and members get a free-exit window.
- **Football-only memberships are cheap glue.** Entry fees run $2M (NIU) to $18M (Sac State); NDSU paid $12.5M. Terms run about 5 years, and the school gains FBS status but carries 2 years of postseason ineligibility for FCS move-ups unless waived (allow a waiver with ~40% success).
- **Exit-fee arms race.** Leagues raise fees when a departure looks imminent, and smart schools move just before the vote (JMU). Event: "League proposes fee hike", in which members with suitors leave early with probability ~0.3.
- **Nine-game P4 standard.** All four P4 leagues play 9 games by 2026-27. The SEC and ACC also require 1 or more extra P4 non-conference games. Scheduling-policy votes happen at spring meetings (May).
- **Notice windows matter.** C-USA requires 14 months, the AAC historically 27, and the ACC roughly a June 1 deadline. A missed deadline means negotiating, which costs about 1.5-2x the base fee or forces a lawsuit.
- **Calendar hooks.** Spring meetings (May) are where formats and distributions are decided. Media days (July) are where public messaging happens. July 1 is when moves take effect. Championship weekend and CFP selection (early December) drive ratings and CFP money. The NCAA Convention (January) handles national governance.
