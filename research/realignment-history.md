# Realignment history, 2010-2026

Owner: history-founding agent. As of 2026-11-25.

## File shapes

**`data/alignment_2010.json`** is an object:
- Top-level keys: `{season:"2010-11", asOf:"2010-08-01", fbsSchoolCount:120, conventions, conferences[], independents[], independentsNotes, fcsSchoolsThatLaterMovedUp[], fcsSchoolsThatMovedDown[], otherNotableSchools2010[], lineage[], sources[]}`.
- Each conference record: `{id, name, shortName, hq{city,state}, bcsAQ, commissioner{id,name,since,background,backgroundNote}, footballMembers[], allSportsMembers[], nonFootballMembers[], footballOnly[], mediaDeals[{partner,years,annualValueUsd,totalValueUsd,notes}], divisions?, pendingAtAsOf?, notes, sources}`.
- `allSportsMembers` means full members whose football also plays in the league.
- The 11 conferences are `sec`, `big-ten` (11), `big-12` (12), `acc`, `big-east-2010` (8 football + 8 non-football), `pac-10`, `mountain-west` (9), `wac-2010` (9), `cusa-2010` (12), `mac` (13, including Temple football-only) and `sun-belt` (9 + 3 non-football).
- Independents: Notre Dame, Army and Navy.
- `fcsSchoolsThatLaterMovedUp` lists 19 schools, each `{id, conference2010, allSports2010, fbsEntry, fbsConference}`.

**`data/realignment_timeline.json`** is an array of 141 records.
- Each record: `{id, type, wave, school, from, to, fromFootball?, sportScope, announced, effective, status, reversed?, exitFeePaidUsd, entryFeeOrForgoneShares, legalAction, keyActors[], notes, sources[], confidence?, note?}`.
- `type`: `move` | `lineage` | `founding` | `scheduling-agreement` | `affiliation` | `program-event`.
- `status`: `completed` | `reversed` | `pending` | `ended`.
- `wave`: `2010-14` | `2015-20` | `2021-26`.
- A split move gets two records, for example BYU football to `independent` plus BYU's other sports to `wcc`.
- **ID rule.** `from` and `to` use the conference id valid the day before `effective`. The `lineage` records give the switch dates:
  - `pac-10` becomes `pac-12` on 2011-07-01.
  - `big-east-2010` becomes `american` on 2013-07-01.
  - `wac-2010` becomes `wac` on 2013-07-01.
  - `cusa-2010` becomes `cusa` on 2013-07-01.
  - `wac` becomes `uac` on 2026-07-01.
- Examples: Pitt left `big-east-2010` (2013), while Rutgers and Louisville left `american` (2014).
- `fcs-independent` is an ad-hoc slug.

**Verification status.** The shared web-search budget ran out after 7 queries. Two fetch hosts were also unreachable: `en.wikipedia.org` and `jmusports.com` would have to be allowed in the session's network settings.
- 2010-2023 records come from researcher knowledge, with Wikipedia and conference pages as reference sources. Exact announcement days and dollar figures that were not certain carry `confidence:"low"`.
- 2024-2026 records were checked against this session's search results and against data already verified by other agents in `conferences.json`, `cfp.json` and `media_deals.json` (MWC settlement, La Tech fee, NDSU and Sac State fees, JMU).

## Narrative

### Before 2010: the template
- The SWC collapsed into the Big 12 in 1994-96 because Texas politics forced Baylor and Texas Tech into the deal ([SWC](https://en.wikipedia.org/wiki/Southwest_Conference)).
- The WAC grew to 16 teams, then split in 1999 to form the Mountain West ([MWC](https://en.wikipedia.org/wiki/Mountain_West_Conference)).
- The ACC raided the Big East in 2003-05, setting off a four-level backfill: Big East ← C-USA ← WAC/MAC ← Sun Belt ([ACC](https://en.wikipedia.org/wiki/Atlantic_Coast_Conference)). See `precedents.json`.

### Wave 1, 2010-14: TV networks and BCS AQ status
- **Spark.** Jim Delany's Dec 2009 Big Ten expansion study, plus the Big Ten Network's carriage economics.
- **June 2010.** Colorado took the Pac-10 invitation (06-10). Nebraska took the Big Ten's and Boise State took the MWC's (06-11). Larry Scott's "Pac-16" died when Texas stayed on 06-14, after Dan Beebe promised a richer Fox deal and allowed the Longhorn Network. Utah followed Colorado (06-17) ([Pac-12](https://en.wikipedia.org/wiki/Pac-12_Conference), [Big 12](https://en.wikipedia.org/wiki/Big_12_Conference)).
- **Aug 2010.** The MWC pre-empted a WAC-BYU deal by taking Fresno State and Nevada (08-18). BYU went independent with an ESPN deal and put its other sports in the WCC (08-31).
- **2011: the Big 12 and Big East.** The Longhorn Network grievance pushed Texas A&M (09-25) and Missouri (11-06) to the SEC, each forfeiting about $12.4M. Pitt and Syracuse went to the ACC (09-18, $7.5M each to leave in 2013). WVU sued its way to the Big 12 for $20M (10-28). TCU dropped its Big East commitment for the Big 12 (10-10) ([Big East 1979-2013](https://en.wikipedia.org/wiki/Big_East_Conference_(1979%E2%80%932013))).
- **Dec 2011 - Feb 2012: the Big East goes national.** It added Boise State and SDSU (football-only), plus Houston, SMU and UCF, then Navy football and Memphis. That set off C-USA's raid of the Sun Belt and WAC, and the WAC's football collapse (football ended after the 2012 season) ([WAC](https://en.wikipedia.org/wiki/Western_Athletic_Conference), [C-USA](https://en.wikipedia.org/wiki/Conference_USA)).
- **Sept 2012: the ACC answers.** It added Notre Dame in all sports except football, with 5 ACC football games a year, and raised its exit fee to 3x the operating budget (about $52M).
- **Nov 2012: Big Ten and ACC.** Maryland left for the Big Ten (11-19) and settled with the ACC for $31.4M in 2014. Rutgers followed (11-20; $11.5M), and the ACC replaced Maryland with Louisville (11-28).
- **Dec 2012 - Mar 2013: the Big East splits.** The Catholic 7 voted to leave (12-15) and kept the Big East name and Madison Square Garden. The football schools kept the charter and became the American (renamed 04-03). Boise State (12-31) and SDSU (2013-01-17) reversed and stayed in the MWC ([Big East](https://en.wikipedia.org/wiki/Big_East_Conference), [American](https://en.wikipedia.org/wiki/American_Conference_(NCAA))).
- **2013-14 backfill.** The Sun Belt added App State, Georgia Southern, Georgia State and Texas State, plus Idaho and NMSU as football-only members. C-USA took WKU, Charlotte, ODU and others. The MAC took UMass for football.
- **The wave ends.** The ACC's April 2013 grant of rights froze the P5, and the CFP replaced BCS AQ status in 2014.

### Quiet years, 2015-20: small moves
- **Done in these years:** Coastal Carolina joined the Sun Belt (2016/17).
- The Sun Belt dropped Idaho and NMSU football. Idaho fell to FCS (2018).
- **Independence and basketball moves:** Liberty became an FBS independent through an NCAA waiver (2018). UMass went independent (2016). Wichita State joined the American (2017). UConn returned to the Big East for $17M (2020).
- **The Big 12's no-go:** its 2016 expansion "beauty contest" ended with no additions because pro-rata TV clauses made new members too expensive.

### Wave 2, 2021-26: P4 consolidation and G6 reshuffle
- **July 2021.** Texas and Oklahoma joined the SEC. They paid $100M combined to leave early, in 2024 ([reduced settlements](https://www.cbssports.com/college-football/news/reduced-settlements-for-texas-oklahoma-joining-sec-early-leave-big-12-ads-kind-of-dumbfounded)).
- **Big 12 backfill (2021-09-10).** BYU, Cincinnati, Houston and UCF joined. Cincinnati, Houston and UCF paid the American $18M each.
- **G6 chain reaction (Oct-Nov 2021).**
  - The American took six C-USA schools: Charlotte, FAU, North Texas, Rice, UAB and UTSA.
  - The Sun Belt took Marshall, ODU and Southern Miss from C-USA (litigation forced a 2022 start) plus JMU.
  - C-USA took Liberty, NMSU, Jacksonville State and Sam Houston, then Kennesaw State, Delaware and Missouri State ([2021-26 realignment](https://en.wikipedia.org/wiki/2021%E2%80%932026_NCAA_conference_realignment), [Missouri State](https://news.missouristate.edu/2024/05/10/missouri-state-accepts-invitation-to-join-conference-usa/)).
- **The Pac-12 collapses (2022-23).**
  - USC and UCLA left for the Big Ten (2022-06-30).
  - In 2023 Colorado left on 07-27. Oregon, Washington, Arizona, ASU and Utah left on 08-04 after the Apple streaming offer. Cal and Stanford left on 09-01; they joined the ACC on about 30% shares, with SMU taking no media share for 9 years.
- **The two-school Pac-12.** Oregon State and Washington State won control in court ([WA Supreme Court](https://www.cbssports.com/college-football/news/washington-state-oregon-state-remain-in-control-of-pac-12-as-washington-supreme-court-denies-review-request)). They used the NCAA's two-year FBS grace period and played a football schedule against the MWC.
- **The Pac-12 rebuilds (2024-26).** It poached five MWC schools in Sept 2024 and added Texas State and Gonzaga in mid-2025 ([Texas State](https://pac-12.com/news/2025/6/30/general-pac-12-conference-welcomes-the-addition-of-texas-state-university.aspx)).
- **The MWC rebuilds.**
  - It added UTEP, UC Davis (non-football) and Grand Canyon (2025, non-football).
  - NIU joined for football only ([ESPN](https://www.espn.com/college-sports/story/_/id/43324617/northern-illinois-join-mountain-west-football-only-26)), and Hawaii became a full member ([UH](https://www.hawaii.edu/news/2026/07/01/uh-joins-mountain-west-as-full-member/)).
  - On 2026-02-09 it added NDSU for football only ([NDSU](https://www.ndsu.edu/news/2026-02-09-ndsu-joining-mountain-west-conference)).
- **The MWC settlement (2026-08-04).** The five departing schools paid $49M ($9.8M each). OSU and WSU paid about $10M each on the poaching claim ([Sportico](https://www.sportico.com/leagues/college-sports/2026/mountain-west-five-schools-settlement-payment-amount-1234942167/), [OPB](https://opb.org/article/2026/08/05/pac-12-mountain-west-conferences-finalize-settlement-over-poaching-and-exit-fees)).
- **More 2025-26 moves.**
  - Louisiana Tech sued its way out of C-USA and paid a record fee of more than $8M to join the Sun Belt in 2026 ([WTOP](https://wtop.com/ncaa-football/2026/04/louisiana-tech-clear-for-move-this-summer-to-sun-belt-after-settlement-with-conference-usa/)).
  - The MAC replaced NIU with Sacramento State as a football-only member ($18M; [Hornet Sports](https://hornetsports.com/news/2026/2/16/hornet-football-to-join-the-mac-in-2026.aspx)).
  - On 2026-10-12, JMU accepted the American's invitation: $23M entry fee, about $5M Sun Belt exit, effective 2027 per AP/Fox, or "no later than 2028" per the board resolution ([FOS](https://frontofficesports.com/article/james-madison-joins-the-american-before-sun-belt-exit-fees-rise/)).

## Timeline (FBS-relevant, abridged; full detail in JSON)

| Announced | School(s) | From → To | Effective | Fee / terms |
|---|---|---|---|---|
| 2010-06-10 | Colorado | Big 12 → Pac-12 | 2011 | ~$6.9M forfeited |
| 2010-06-11 | Nebraska | Big 12 → Big Ten | 2011 | ~$9.3M forfeited |
| 2010-06-11 | Boise State | WAC → MWC | 2011 | — |
| 2010-06-17 | Utah | MWC → Pac-12 | 2011 | phased shares |
| 2010-08-18 | Fresno State, Nevada | WAC → MWC | 2012 | WAC buyout dispute |
| 2010-08-31 | BYU | MWC → Ind. (FB) + WCC | 2011 | ESPN 8-yr |
| 2010-11-29 | TCU | MWC → Big East (reversed 2011-10-10) | — | $5M to Big East |
| 2010-12-10 | Hawaii | WAC → MWC (FB) + Big West | 2012 | — |
| 2011-04-20 | UMass | CAA → MAC (FB) | 2012 | — |
| 2011-09-18 | Pitt, Syracuse | Big East → ACC | 2013 | $7.5M each |
| 2011-09-25 | Texas A&M | Big 12 → SEC | 2012 | ~$12.4M |
| 2011-10-10 | TCU | MWC → Big 12 | 2012 | — |
| 2011-10-28 | West Virginia | Big East → Big 12 | 2012 | $20M (litigated) |
| 2011-11-06 | Missouri | Big 12 → SEC | 2012 | ~$12.4M |
| 2011-12-07 | Houston, SMU, UCF; Boise, SDSU (FB) | C-USA/MWC → Big East | 2013 | Boise and SDSU reversed |
| 2012-01/03 | Navy (FB, 2015), Memphis, Temple | → Big East/American | 2012-15 | — |
| 2012 spring | Charlotte, FIU, FAU, UNT, MTSU, La Tech, UTSA, ODU | → C-USA | 2013 | — |
| 2012-05 | Utah State, SJSU → MWC; Texas State, Georgia State → Sun Belt | WAC/CAA → | 2013 | — |
| 2012-09-12 | Notre Dame | Big East → ACC (non-FB, 5 games) | 2013 | — |
| 2012-11-19/20 | Maryland, Rutgers | ACC/Big East → Big Ten | 2014 | $31.4M / $11.5M |
| 2012-11-27/28 | Tulane, ECU → American; Louisville → ACC | | 2014 | ~$11M (UofL) |
| 2012-12-15 | Catholic 7 (+Butler, Creighton, Xavier 2013-03-20) | Big East → new Big East | 2013 | name + MSG for cash |
| 2013 spring | App State, Ga Southern, Idaho/NMSU (FB) → Sun Belt; WKU → C-USA; Tulsa → American | | 2014 | — |
| 2014-03 | UMass | MAC → Ind. | 2016 | — |
| 2015 | Coastal Carolina | Big South → Sun Belt | 2016/17 | — |
| 2016 | Idaho → Big Sky (FCS); NMSU → Ind. | Sun Belt → | 2018 | — |
| 2017 | Liberty → FBS Ind.; Wichita State → American | | 2017-18 | NCAA waiver |
| 2019-06-27 | UConn | American → Big East + FB Ind. | 2020 | $17M |
| 2021-07-30 | Texas, Oklahoma | Big 12 → SEC | 2024 | $100M combined |
| 2021-09-10 | BYU, Cincinnati, Houston, UCF | → Big 12 | 2023 | $18M each (AAC 3) |
| 2021-10-21 | Charlotte, FAU, UNT, Rice, UAB, UTSA | C-USA → American | 2023 | — |
| 2021-10/11 | Marshall, ODU, Southern Miss, JMU | → Sun Belt | 2022 | litigated |
| 2021-11-05 | Liberty, NMSU, JSU, Sam Houston | → C-USA | 2023 | — |
| 2022-06-30 | USC, UCLA | Pac-12 → Big Ten | 2024 | UCLA pays Cal |
| 2023-07-27 | Colorado | Pac-12 → Big 12 | 2024 | $2.5M bonus |
| 2023-08-04 | Oregon, Washington → Big Ten; Arizona, ASU, Utah → Big 12 | | 2024 | partial B1G shares |
| 2023-09-01 | Cal, Stanford, SMU | → ACC | 2024 | 30% shares / 0% for 9 yrs |
| 2023-10-25 | Army | Ind. → American (FB) | 2024 | — |
| 2023 | Kennesaw State, Delaware | → C-USA | 2024 / 2025 | — |
| 2024-02-29 | UMass | Ind. → MAC (full) | 2025 | — |
| 2024-05-10 | Missouri State | MVC/MVFC → C-USA | 2025 | — |
| 2024-09-12/24 | Boise, CSU, Fresno, SDSU, Utah State | MWC → Pac-12 | 2026 | $49M total (settled 2026-08-04) |
| 2024-10-31 | UTEP | C-USA → MWC | 2026 | ~$8M |
| 2024-12-10 | UC Davis | Big West → MWC (non-FB) | 2026 | — |
| 2025-01 | Grand Canyon (non-FB, 2025); NIU (FB) | → MWC | 2025 / 2026 | NIU $2M entry |
| 2025-06-30 | Texas State | Sun Belt → Pac-12 | 2026 | — |
| 2025-07 | Gonzaga | WCC → Pac-12 (non-FB) | 2026 | — |
| 2025-07-15 | Louisiana Tech | C-USA → Sun Belt | 2026 | >$8M (litigated) |
| 2026-02-09 | North Dakota State | MVFC → MWC (FB) | 2026 | $12.5M + $5M NCAA |
| 2026-02-16 | Sacramento State | Big Sky → MAC (FB) + Big West | 2026 | $18M + $5M NCAA |
| 2026-10-12 | James Madison | Sun Belt → American | 2027 (≤2028) | $23M entry, ~$5M exit |

## Price list of exits, 2010-2026 (what leaving actually cost)

- **P5/P4 leaving a P-league:**
  - The SEC, Big Ten and Pac-12 (pre-2024) had no explicit exit fee.
  - Big 12 exits cost forfeited distributions: about $7-12M in 2010-11, and $50M per school for Texas and Oklahoma in 2021-23.
  - ACC: $31.4M for Maryland (claimed $52.2M). Under the 2025 settlement the fee is now $165M, declining to $75M.
- **Leaving the old Big East / American:** $5-20M (Pitt and Syracuse $7.5M each, WVU $20M, Rutgers $11.5M, UConn $17M, the AAC trio $18M each).
- **Leaving a G5:** $2-10M historically. A late-notice departure from the MWC was billed about $17-38M per school, and the five settled at $9.8M each. La Tech paid more than $8M to C-USA (a record).
- **Entry costs are rising fast:** NIU $2M, NDSU $12.5M, Sac State $18M, JMU $23M. FCS move-ups also pay the $5M NCAA fee.
- **Forgone shares are the P4 entry price:**
  - Cal and Stanford take about 30% shares for 7 years, and SMU takes 0% for 9 years.
  - Oregon and Washington take reduced shares (roughly half).
  - Nebraska, Maryland and Rutgers were phased in over about 6 years.

## Corrections to the brief

1. **The MWC 2026 roster is missing UC Davis.**
   - UC Davis joined as a non-football member on 2026-07-01; its football stays in the Big Sky ([UC Davis](https://ucdavisaggies.com/news/2024/12/10/athletics-uc-davis-to-join-mountain-west-conference-in-2026-27)).
   - NDSU is confirmed: football-only, announced 2026-02-09 (the brief had it with a "?").
   - Grand Canyon joined on 2025-07-01, a year before the others (low confidence).
   - Hawaii is a full member but keeps several sports in the Big West.
2. **Sacramento State's non-football sports went to the Big West, not the Big Sky.** It is a 5-year football-only MAC member and is postseason-ineligible until 2028.
3. **James Madison is leaving the Sun Belt for the American.** The move was announced 2026-10-12 and takes effect 2027 (board text: "no later than 2028"). The brief's Sun Belt list is right for 2026-27, but add a pending change.
4. **"Catholic 7 bought the name for about $10M"** is roughly right but inverted. They received only about $10M of a ~$100M+ reserve (forgoing most of their share) in exchange for the name and MSG; they did not write a $10M check. Low confidence.
5. **The "~$55M poaching fee" was the MWC's claim, not the outcome.**
   - The 2026-08-04 settlement: about $10M each from OSU and WSU on the poaching claim, plus $49M from the five departing schools.
   - About $69-70M in total went to the MWC.
6. **The 1999 WAC split's "Laramie meeting" is unverified.** The decisive secret meeting is more often placed at or near Denver International Airport (May 1998). Wyoming's president is cited as a ringleader. Low confidence either way.
7. **The 2010 Big East had 16 full members (8 football + 8 non-football),** not 8 football plus a few non-football members. Notre Dame played football as an independent.
8. **The 2010 MAC had 13 football members,** including Temple as football-only (A-10 in other sports). The 2010 Sun Belt had 9 football members plus Denver, Little Rock and South Alabama in other sports.
9. **Army and Navy are not FBS independents in 2026.** Both are American football-only members (Navy since 2015, Army since 2024). Only Notre Dame and UConn are independents.
10. **The American's name** has been "American Conference" since its 2025 rebrand. The id stays `american`.
11. **The WAC rebranded as the United Athletic Conference (multisport) on 2026-07-01** (low confidence). The canonical id `uac` now covers the all-sports league, not only the football alliance.

## Game-model implications

- **Wave cadence.** Major waves came in 1990-96, 2003-05, 2010-14 and 2021-26, about every 6-10 years and each lasting 3-5 years. In between there are 1-4 smaller moves a year (FCS move-ups, single G5 swaps). Suggested tunables:
  - `majorWaveBaseProbPerYear` = 0.08, rising to 0.35 within 3 years of a P4 media-rights expiry or a CFP-contract reset.
  - `minorMovesPerYear` ~ Poisson(λ=2.5).
- **Triggers.** Weight them roughly as follows:
  - Media-deal expiry or a new network launch (BTN 2007, SECN 2014, FS1 2013): 0.35.
  - Anchor-school grievance (unequal revenue, the Longhorn Network): 0.2.
  - Postseason-format change (BCS AQ, CFP 2014, 12-team CFP 2024, 24-team CFP 2027): 0.2.
  - Legal/financial shock (House settlement, NIL): 0.15.
  - Leadership change: 0.1.
  - Model the next likely window around the Big Ten's 2030 media expiry, the end of the CFP contract (2031-32), the SEC's 2034 deal and the ACC's 2036 grant of rights.
- **Cascades.** One P4 move should generate AI backfill at each lower tier within 6-18 months (P4 ← AAC/MWC ← C-USA/Sun Belt ← FCS). Each raided league attempts a replacement with probability of about 0.9 if it falls below 10 football members, and about 0.6 otherwise.
- **Exit pricing formula.**
  - Exit cost = bylaw fee (G6 ≈ 1-2x the annual distribution; P4 = forfeited distributions or the ACC schedule) + grant-of-rights damages + poaching penalties.
  - Litigation settles at 40-60% of the claim after 6-18 months, with $1-10M in legal costs per side.
  - Notice periods are 12-27 months. Paying a premium (1.5-2x) lets a school leave a year early.
- **Entry pricing.** In P4 leagues, newcomers take 0-50% shares for 5-10 years. In G6 leagues, entry fees run $2-25M plus $5M to the NCAA for FCS move-ups, and some newcomers accept no initial distributions.
- **Reversals happen.** Boise State and SDSU (2012-13) and TCU (2011) reversed. Give AI schools a "buyer's remorse" check when the target league loses its value (AQ status, TV money) before the effective date.
- **Control fights.** When a majority of a league's members give notice, run a "who controls the charter" event (the 2023 OSU/WSU precedent). The winners keep cash, NCAA units, the CFP seat and the name.
- **Political overrides.** High `statePoliticalPressure` schools can force package deals (Baylor and Texas Tech in 1994, Virginia Tech in 2003) or block moves. UC Regents conditioned UCLA's move on payments to Cal.
- **Data use.**
  - Start a 2010 game from `alignment_2010.json`.
  - Replay `realignment_timeline.json` as scripted history, or use it as a probability prior: who moved, when, at what price.
  - Treat `pending` records (JMU) as in-game news at the 2026 start.
