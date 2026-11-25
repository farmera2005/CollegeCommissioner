# Revenue, distributions, CFP, NCAA units and bowls

Owner: money-postseason agent. As of 2026-11-25.

> **Research caveat.** The session's shared web-search budget ran out after the CFP, Big Ten/SEC FY2025 and bowl-rotation searches, and WebFetch could not reach ESPN, Yahoo or the CFP site. Everything about the **CFP (2024-2032), the Big Ten/SEC FY2025 distributions, the CFP revenue split, participation payments, sites and bowl rotation** comes from current search results and is well sourced. Most **pre-FY2025 conference distributions, G6 amounts, NCAA unit values, per-bowl payouts and 2026-31 bowl tie-ins** come from researcher recall and carry `"confidence": "low"`. Redo them in a follow-up pass with search enabled.

## File shapes

**`data/distributions.json`** is an array with one record per conference and fiscal year (FY2019-FY2025 for the 10 FBS leagues, plus a Pac-12 FY2026 bridge record and one Notre Dame record, 72 in total):
`{id, conference, fiscalYear (int, FY end year), fiscalYearLabel, fiscalYearEnd, totalRevenueUsd, totalDistributedUsd, perSchoolUsd (typical full share), fullShareMembers, distributionModel, partialShareNotes, notes, [maxPerSchoolUsd, minFullSharePerSchoolUsd, perSchoolIsComputed], [confidence, note], sources}`.
The SEC fiscal year ends Aug 31. All the other leagues end June 30.

**`data/cfp.json`** is an object with these keys: `asOf`, `formats[]` (one per season or era: teams, model, autoBids, atLargeBids, byes, rounds, bowls, championship, champion), `expansionDebate[]` (dated timeline), `revenueDistribution` (shares + per-school estimates), `participationPayments` (per-round ladder + conference pass-through policies), `espnContract` (base / expansion / previous), `governance` (managementCommittee, boardOfManagers, votingRules, selectionCommittee), `sites` (NY6 list, rotation by season, campus games, title-game sites) and `sources`.

**`data/ncaa_units.json`** is an object with these keys: `mensBasketballFund` (rules + unit values), `unitsByConference[]` (2021-2025 computed, 2026 null), `rollingWindowTotals`, `womensPerformanceUnits`, `otherDistributions[]`.

**`data/bowls.json`** is an array of `{id, type ("bowl" | "cfp-championship" | "conference-championship" | "neutral-site"), name, titleSponsor, city, state, [country], venue, date2026, payoutPerTeamUsd, payoutIsEstimate, payoutTier (A-D), tieIns:[{conference, pickOrder, notes}], cfpRole ("quarterfinal" | "semifinal" | "championship" | "none"), notes, [revenueNotes], [confidence, note], sources}`. There are 43 bowls (6 NY6/CFP + 36 FBS + Celebration), the CFP title game, 5 conference title games and 3 neutral-site/Las Vegas records.

## 1. Conference distributions: key facts

- **Big Ten, FY2025 (FYE 2025-06-30): a record $1.37B distributed to 18 schools**, up from ~$883M. The average across all 18 is $76.1M. Ohio State got $91.57M and Penn State $88.92M (CFP runs). Other full members got $76.01M-$79.87M, and Oregon (~$48.4M) and Washington (~$46.7M) are on phased partial shares until ~2030. Total revenue was ~$1.47B per Yahoo's tax-return reporting. ([ESPN](https://www.espn.com/college-sports/story/_/id/48651052/big-ten-distributes-record-revenue-2024-2025-fiscal-year), [CBS](https://www.cbssports.com/college-football/news/big-ten-1-37-billion-in-revenue-to-its-18-members-for-2025-fiscal-year/), [On3](https://www.on3.com/nil/news/big-ten-announces-1-37-billion-revenue-distribution-18-member-schools-fiscal-year-2024-25/), [Yahoo school-by-school](https://sports.yahoo.com/articles/ohio-state-every-big-ten-230658862.html))
- **SEC, FY2025 (FYE 2025-08-31): $1.03B+ distributed**, up from $808.4M. The 14 longer-tenured schools averaged $72.4M. Oklahoma ($2.6M) and Texas ($12.1M, or $12.6M in one outlet) got sharply reduced first-year shares. The total includes $37.4M kept by CFP/bowl participants. Tax-form revenue was ~$1.1B, with a $14.5M cash-basis deficit. ([SEC release](https://www.secsports.com/news/2026/02/sec-announces-2024-25-revenue-distribution), [SwimSwam](https://swimswam.com/sec-announces-over-1-03-billion-in-2024-2025-revenue-distribution-to-its-16-members/), [Fox](https://www.foxsports.com/articles/cfb/the-sec-is-distributing-more-than-1b-to-its-schools-for-the-202425-fiscal-year), [USA Today via AOL](https://www.aol.com/articles/sec-financial-boom-brings-revenue-223212797.html))
- **Big Ten FY2022 revenue of $845.6M** led the P5 ([CBS](https://www.cbssports.com/college-football/news/big-ten-leads-power-five-conferences-with-845-6-million-in-revenue-in-2022-fiscal-year-per-report)). Other pre-2025 figures are low-confidence recall of USA Today 990 reporting ([USA Today finances](https://sportsdata.usatoday.com/ncaa/finances), [ProPublica 990 search](https://projects.propublica.org/nonprofits/search?q=Big+Ten+Conference)).
- **The ACC no longer distributes equally.** (1) The **success initiative** pool, funded by money freed up because SMU takes no media share for 9 years and Cal/Stanford take ~30% shares, is paid out by athletic performance. (2) The **March 2025 FSU/Clemson settlement** added a brand/viewership-weighted component from 2025-26. Exact percentages were not verified.
- **Big 12**: FY2025 was the first year of the ESPN/Fox extension (~$31.7M per school per year in media). The per-school total was not verified.
- **Pac-12**: OSU and WSU ran a 2-member bridge league in FY2025-26, with Power-level CFP treatment and NCAA units still being paid out from the 12-team era (42 units in the 2021-25 window). The rebuilt 8+1 league starts FY2027.
- **Notre Dame**: NBC deal ~$50M/yr (2025-2034), a partial ACC share as a non-football member, and a fixed CFP share of ~$12.5M/yr from 2026.

## 2. College Football Playoff

| Season | Field | Access | Byes | Final |
|---|---|---|---|---|
| 2024-25 | 12 | 5 highest-ranked conf. champs + 7 at-large | Top-4 champs | Atlanta, Jan 20 2025 (Ohio State) |
| 2025-26 | 12 | same, **straight seeding** (May 22 2025) | Top-4 ranked | Miami Gardens, Jan 19 2026 (Indiana, low-confidence recall) |
| 2026-27 | 12 | **P4 champs + top G6 team** + 7 at-large. ND guaranteed a bid if top-12 | Top-4 ranked | Las Vegas, Jan 25 2027 |
| 2027-28 to 2031-32 | **24** | P4 champs + top G6 + **19 at-large** | Top 8 (host 2nd round) | New Orleans Jan 24 2028, Tampa Jan 22 2029 |

- **2026 default.** The SEC (16 teams, 5+11) and Big Ten (24 teams) deadlocked past the **2026-01-23** deadline, so the 12-team default applied ([CBS](https://www.cbssports.com/college-football/news/college-football-playoff-expansion-tabled-big-ten-sec-stalemate-12-team-format/), [ESPN](https://www.espn.com/college-football/story/_/id/47704876/sources-college-football-playoff-remain-12-teams), [NCAA.com](https://www.ncaa.com/news/football/article/2026-02-03/how-12-team-college-football-playoff-will-work-teams-schedule-bids), [CBS on the ND clause](https://www.cbssports.com/college-football/news/college-football-playoff-selection-notre-dame-mou-2026-schedule)).
- **24-team decision.** The CFP Management Committee approved it unanimously on **2026-11-09**, about 3 weeks before the Dec 1 deadline. Seeds 9-16 host 17-24, then seeds 1-8 host the second round, so 16 games are played on campus. QFs and semis rotate among the NY6. The playoff starts the first full week of December. **Power 4 title games are eliminated.** G6 title games are up to each league. ([CFP release](https://collegefootballplayoff.com/news/2026/11/9/24-team-expansion), [CFP format page](https://collegefootballplayoff.com/sports/2026/11/9/24-team-format), [NBC](https://www.nbcnews.com/sports/college-football/college-football-playoff-expanding-24-teams-2027-rcna608336), [CBS](https://www.cbssports.com/college-football/news/college-football-playoff-format-expanding-to-24-teams-for-2027-season/), [Press Democrat](https://www.pressdemocrat.com/2026/11/09/cfp-expansion-format-24-teams-calendar/), [NCAA.com](https://www.ncaa.com/news/football/article/2026-11-11/everything-know-about-24-team-college-football-playoff-bracket))
- **Money.** ESPN's base deal is **$7.8B over 6 years** (2026-27 to 2031-32, ~$1.3B/yr). The expansion adds **~$1.7B over 5 years** (2027-28 to 2031-32, ~$345M/yr) for 12 new games. ESPN gets ~$140M/yr back from the SEC, ACC and Big 12 for the canceled title games, and Fox reportedly ~$50M/yr from the Big Ten, so ESPN's net new spend is ~$205M/yr and conferences net "minimal" per-school gains. ([ESPN](https://www.espn.com/college-football/story/_/id/50433381/cfp-espn-ink-5-year-17b-deal-expand-field-sources-say), [Yahoo deal details](https://sports.yahoo.com/articles/espn-cfp-agree-24-team-171705328.html), [Yahoo per-school](https://sports.yahoo.com/articles/media-revenue-gains-cfp-expansion-173042311.html), [ESPN PR](https://espnpressroom.com/press-release/espn-secures-exclusive-media-rights-to-new-games-in-expanded-24-team-college-football-playoff/))
- **Revenue split, 2026-31.** SEC 29%, Big Ten 29%, ACC 17.25%, Big 12 14.75%, G6 ~9%, Notre Dame ~$12.5M fixed. That is ~$21-22M per SEC/Big Ten school and ~$12M per ACC/Big 12 school per year. ESPN reports the 24-team deal leaves this unchanged. ([CBS](https://www.cbssports.com/college-basketball/news/college-football-playoff-finalizes-tv-deal-beginning-in-2026-as-fbs-leaders-settle-on-revenue-distribution), [Yahoo/AP](https://sports.yahoo.com/conferences-notre-dame-agree-6-200552103.html), [BOCS](https://businessofcollegesports.com/finance/what-college-football-playoff-expansion-means-for-revenue-distribution/))
- **Participation payments (2024-26)**: $4M for making the field, +$4M for a QF, +$6M for a SF, +$6M for the final (max $20M), plus a ~$3M per-game travel allowance. All of it goes to the conference. The ACC passes 100% to the school. The SEC lets the school keep $3.0M/$3.5M/$3.75M/$4.0M by round plus travel. The Big 12 lets it keep ≥$1.9M plus travel (R1/QF) and $2.2M (SF/F). ([BOCS](https://businessofcollegesports.com/football/2025-2026-college-football-playoff-schedule-and-payouts/), [Forbes](https://www.forbes.com/sites/kristidosh/2025/12/31/which-teams-are-making-the-most-in-the-college-football-playoff/), [FOS](https://frontofficesports.com/article/acc-only-power-conference-giving-cfp-teams-100-of-payout/))
- **Sites.** 2026-27: QFs at Fiesta (Dec 30), Cotton, Peach and Rose (Jan 1); SFs at Orange (Jan 14) and Sugar (Jan 15). 2027-28: QFs at Sugar (Dec 31), Fiesta, Peach and Rose; SFs at Orange (Jan 13) and Cotton (Jan 14). **The Rose Bowl will host no semifinals in 2028-31.** Seeds 1-3 pick their QF bowl, and conference tie-ins to the Rose, Sugar and Orange are gone. ([CFP 26-27/27-28](https://collegefootballplayoff.com/news/2026/2/3/2627-2728-bowls), [CFP 2028-31](https://collegefootballplayoff.com/news/2026/7/9/2028-31-bowls), [Sugar Bowl](https://allstatesugarbowl.org/news/2026/7/9/college-football-playoff-announces-cfp-quarterfinal-and-semifinal-dates-for-the-2028-31.aspx))
- **Governance.** The Management Committee is the 10 FBS commissioners plus ND AD Pete Bevacqua. The Board of Managers is one president per conference plus ND's president; 2026 changes include UNC's Lee Roberts, Texas Tech's Lawrence Schovanec, Hawaii's Wendy Hensel and Ball State's Geoffrey Mearns ([UNC](https://www.unc.edu/posts/2026/01/22/chancellor-roberts-joins-college-football-playoff-board-of-managers/), [Hawaii](https://www.hawaii.edu/news/2026/07/14/hensel-college-football-playoff-board/), [Ball State](https://ballstatesports.com/news/2026/7/29/GEN_MearnsCFP)). Under the 2024 MOU, the SEC and Big Ten control the format "in consultation" with the others ([FOS](https://frontofficesports.com/cfp-agrees-post-2026-terms-sec-big-ten)). Selection committee chair: Hunter Yurachek. The FOS headlines about a **search for a new CFP leader** ([FOS](https://frontofficesports.com/cfp-heads-into-expansion-era-in-search-of-new-leader)) and **Mountain West commissioner stepping down after expansion** ([FOS](https://frontofficesports.com/mountain-west-commissioner-steps-down-after-cfp-expansion)) were not read in full. They are flagged for the career-people agent.

## 3. NCAA basketball units

A unit is earned for each game played in the men's tournament, the title game excluded, which makes 132 units a year. Each unit pays every year for 6 years, so the payout is a rolling sum. Units stay with the conference the school was in when it earned them, which is why the old Pac-12's units still pay OSU and WSU. A unit was worth ~$340K a year (~$2.0M over 6 years) in the mid-2020s (low confidence). The units by conference in `ncaa_units.json` were computed from 2021-2025 bracket results; the SEC's record 14-bid 2025 gave it 35 units. The **women's performance fund** began with the 2025 tournament, ~$15M in year one (low confidence). Other NCAA funds (equal conference, grant-in-aid, sports sponsorship, academic unit, SAF) are listed qualitatively.

## 4. Bowls and championship games

The 2026-27 bowl season runs Dec 12 (Celebration) / Dec 15 (Salute to Veterans, Montgomery) through the Jan 25 CFP final in Las Vegas. The new **Puerto Rico Bowl** is Dec 22 in Bayamón, approved 2026-05-08 ([Wikipedia](https://en.wikipedia.org/wiki/2026%E2%80%9327_NCAA_football_bowl_games), [CFN tie-ins](https://collegefootballnews.com/college-football/college-football-bowl-ties-affiliations-conference-2026-2027)). Three tie-ins are confirmed: Liberty (Big 12 vs SEC), Rate (Big 12 vs Big Ten), New Orleans (Sun Belt vs CUSA) and 68 Ventures (Sun Belt vs MAC). The rest follow the 2020-25 cycle. Payouts are **tiered estimates** (A $4M, B $2.75M, C $1.2M, D $0.5M per team).

**Title games.** 2026 is the last year of Power 4 title games: SEC in Atlanta, Big Ten in Indianapolis, Big 12 in Arlington, ACC in Charlotte. Their rebate values (~$140M/yr across ESPN's three, ~$50M/yr for the Big Ten on Fox) are the best public proxies for what the games were worth.

**Las Vegas** is college sports' neutral-site hub:
- Allegiant Stadium: Las Vegas Bowl, the 2021-23 Pac-12 title game, the 2027 CFP final, Vegas Kickoff Classic games and ND's Shamrock Series
- MWC tournaments at Thomas & Mack
- the old Pac-12 tournaments at T-Mobile Arena and Michelob Ultra Arena
- WCC and WAC tournaments at Orleans Arena
- the Big West tournament in Henderson

## Corrections to the brief

1. **CFP 2026-27 access rule.** The "5 highest-ranked conference champions" rule applied only in 2024-25 and 2025-26. For **2026-27** the four **P4 champions get automatic bids regardless of ranking**, plus the **highest-ranked G6 team**. Per NCAA.com and OutKick that team need not be a champion, though some outlets say "top G6 champion". **Notre Dame is guaranteed a bid if it is top-12.** Seeding is straight (top 4 get byes).
2. **2027 format: confirmed**, decided **2026-11-09** and not left pending. The field is 24 teams: P4 champions + top G6 + 19 at-large. The brief leaves out that **Power 4 championship games are eliminated** and that the top 8 seeds get byes and host the second round.
3. **ESPN ~$1.7B/5-yr: confirmed**, and it comes **on top of** the $7.8B/6-yr base deal. Net of rebates for the canceled title games, ESPN adds only ~$205M/yr, and per-school gains are small.
4. **The 16-team debate** (4-4-2-2-1(+3) vs 5+11) dominated 2025. It ended in deadlock, not a 16-team adoption. The Big Ten's 16-as-stopgap-then-24 offer was rejected in Jan 2026, and the CFP went straight from 12 to 24.
5. **Revenue split**: confirmed, more precisely **ACC 17.25%** and **Big 12 14.75%**. Notre Dame gets **~$12.5M**.
6. **Big Ten $1.37B vs SEC $1.03B: confirmed.** They are not like-for-like: the fiscal years end June 30 vs Aug 31, and the SEC figure includes $37.4M of bowl/CFP money kept by schools. Per school, the SEC averaged $72.4M against a Big Ten average of $76.1M (typical full share ~$78M, Ohio State $91.6M).
7. **The Rose Bowl will not host CFP semifinals in 2028-31**, and all NY6 conference tie-ins are gone from 2026.
8. Possible personnel changes (CFP executive director search; MWC commissioner Gloria Nevarez stepping down) are not in the brief or SCHEMA. Verify them.

## Game-model implications (suggested `/config/economy` defaults)

**Conference revenue mix (annual, FY2027 baseline)**

| Source | SEC / Big Ten (16-18 schools) | ACC / Big 12 | Typical G6 (American / MWC) |
|---|---|---|---|
| Media rights (incl. network) | 62-68% | 60-65% | 45-55% |
| CFP base share | 20-25% (~$21-22M/school) | 18-22% (~$12M/school) | 15-25% (9% pool ÷ 6 leagues ≈ $18M/league) |
| CFP/bowl participation (retained or pooled) | 3-5% | 3-5% | 2-5% |
| NCAA units + other NCAA funds | 2-3% | 3-4% | 8-15% |
| Championship game (until 2026) | 3-4% | 3-4% | 1-3% |
| Corporate sponsorship / events | 1-3% | 1-3% | 3-6% |

- **Per-school anchors (FY2025 → FY2027 projection):** Big Ten ~$78M → ~$95-100M. SEC $72.4M → ~$90-95M (CFP base ~$22M from FY2027). ACC ~$45M + success/brand pool (top brands +$5-15M). Big 12 ~$40-45M. American ~$7-8M. MWC ~$4-5M. Sun Belt ~$2-3M. MAC ~$1.5-2.5M. CUSA ~$1M. G6 and ACC/Big 12 figures are estimates.
- **CFP flow:** `confPool = Σ participationPayments + share% × netCfp`, where `netCfp ≈ $1.2B (2026-27), ≈ $1.4B from 2027-28` (base + ~$200M net expansion). Each school gets `retained(round) + (confPool - Σretained) / members`. Per-league retention ladders: ACC 100%, SEC $3-4M by round, Big 12 $1.9-2.2M floors, Big Ten mostly pooled with ~+$10-15M to deep runners.
- **Title-game removal (2027+):** remove ~$45-60M/yr of championship-game value per P4 league, add the CFP expansion share. The net should be about break-even for the P4 and slightly negative for leagues whose games drew large gates.
- **NCAA units:** `annualUnitValue ≈ $340K` growing 2-3%/yr. `payout(conf, year) = Σ_{t=year-6}^{year-1} units(conf, t) × value(year)`. Units stay with the conference if a school leaves, which makes them a realignment asset (Pac-12 lesson).
- **Bowls:** `payout ∈ {4.0, 2.75, 1.2, 0.5}M` by tier. Use an **expense ratio** of 0.8-1.1 × payout for Power bowls (travel, band, per diem, unsold tickets) and 1.0-1.5 × for G6 bowls. Leagues pool bowl revenue and pay a fixed travel allowance (~$1.5-2.5M P4, ~$0.3-0.8M G6), so a bowl trip is roughly break-even for the school and a recruiting/visibility gain.
- **Sponsorship:** conference-office sponsorship of ~$10-40M/yr for P4 and ~$1-5M for G6. The commissioner's Commercial stat should scale it (Big 12's Yormark-style properties push).
- **Distribution models to offer:** equal (SEC, legacy Big Ten), equal + newcomer phase-ins (Big Ten Oregon/UW to 2030, ACC Cal/Stanford 30% / SMU 0%), performance pool (ACC success initiative), viewership/brand-weighted (ACC from 2025-26). Each model should trade off cohesion (board utility, exit risk) against top-brand retention.

## Data gaps / follow-ups

- Pre-FY2025 P4 distributions and all G6 distributions: pull USA Today/990 data (ProPublica).
- Big 12 and ACC FY2025 per-school totals. ACC success-initiative and brand-formula percentages.
- 2026 NCAA tournament units, exact unit values by year, and the women's unit value.
- 2026-31 bowl tie-ins (esp. Alamo, Holiday, Sun, LA, Las Vegas and the new Pac-12) and actual payouts.
- CFP 2027+ participation-payment ladder. Remaining 2028-31 bowl rotation. 2030 and 2031 title sites.
