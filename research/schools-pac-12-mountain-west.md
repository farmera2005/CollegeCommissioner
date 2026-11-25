# Schools — Pac-12 & Mountain West (2026-27)

Owner: schools-west agent. Files: `data/schools/pac-12.json` (9 records), `data/schools/mountain-west.json` (12 records).
As of 2026-11-25.

**Shape:** arrays of `School` records exactly per `research/SCHEMA.md`. Three small additions the engine can ignore:
- `confidence: "low"` + `note` can sit **inside sub-objects** (`athletics`, `president`, `ad`, coaches) to flag the specific uncertain fact without marking the whole record low-confidence.
- Record-level `note` lists which numeric fields are approximate.
- Non-football schools have `ratings.football: null`, `headFootballCoach: null`, `conference.*.football: null`, `level: "none"`.

## Research limits (read first)
The web-search budget for this run was used up after **6 searches**, all spent on membership verification. WebFetch could not resolve the primary-source hosts (pac-12.com, abqjournal.com). So:
- **Membership (below) is verified** against search results from the leagues, the schools, ESPN, SI and the NCAA.
- **Leadership, finances, enrollment, US News ranks, endowments and DMA ranks come from my training knowledge (through about mid-2026) and were not re-checked.** Anything I was unsure of carries `confidence:"low"`. Finance figures are approximations of FY2024 Knight-Newhouse/USA Today data. DMA ranks are approximate Nielsen 2024-26 positions, within ±3 or so.
- 2025 football and 2025-26 basketball results are mostly described only loosely in `ratingNotes`. A follow-up pass with search should re-verify every field marked `confidence:"low"`.

## Broad sources
- Pac-12 relaunch release (seven new full members, 12 affiliates): https://pac-12.com/news/2026/6/30/general-the-new-pac-12-conference-officially-launches-with-the-addition-of-seven-full-time-members.aspx · Gonzaga's copy of it: https://gozags.com/news/2026/7/1/gonzaga-athletics-the-new-pac-12-conference-officially-launches-with-the-addition-of-seven-full-time-members
- Pac-12 member explainers: https://www.statesman.com/sports/college/article/pac-12-texas-state-2026-members-22323653.php · https://www.si.com/college/oregon-state/football/what-teams-are-in-the-new-pac-12-in-2026-2027
- Texas State admission: https://pac-12.com/news/2025/6/30/general-pac-12-conference-welcomes-the-addition-of-texas-state-university.aspx · https://frontofficesports.com/pac-12-rebuild-nears-completion-with-2026-texas-state-addition/ · https://www.si.com/college/gonzaga/basketball/pac-12-welcomes-texas-state-to-conference-01jz0xq0fs3r
- Pac-12 wrestling affiliates: https://pac-12.com/news/2026/3/31/pac-12-wrestling-strengthens-its-membership-with-the-additions-of-air-force-northern-colorado-north-dakota-state-and-south-dakota-state.aspx · https://gobison.com/news/2026/4/1/ndsu-wrestling-to-join-pac-12-conference-as-affiliate-member.aspx
- Mountain West membership: https://themw.com/sports/2026/5/28/this-is-mountain-west.aspx · https://sports.yahoo.com/articles/see-mountain-west-conference-realignment-104520403.html · https://www.denver7.com/sports/college-sports/mountain-west-conference-pauses-expansion-as-it-negotiates-media-deals
- NDSU to the MWC: https://www.espn.com/college-football/story/_/id/47870245/sources-north-dakota-state-joins-mountain-west-football · https://www.ncaa.com/news/football/article/2026-02-09/10-things-know-about-north-dakota-states-move-fbs · https://www.ndsu.edu/news/mountain-west-football-opponents-set-2026
- NIU: https://www.espn.com/college-sports/story/_/id/43324617/northern-illinois-join-mountain-west-football-only-26 · https://niuhuskies.com/news/2025/2/27/general-niu-sports-moving-to-horizon-league-in-2026-27.aspx
- UC Davis: https://www.espn.com/college-sports/story/_/id/42899713/uc-davis-join-mountain-west-some-sports-not-football
- Hawaii full membership: https://www.espn.com/college-sports/story/_/id/41814799/hawaii-join-mountain-west-full-member-july-2026
- Finances (FY2024 baseline): https://sportsdata.usatoday.com/ncaa/finances · https://knightnewhousedata.org/

## Verified 2026-27 membership

### Pac-12: 9 full members (all launched July 1, 2026)
| School | Type | Note |
|---|---|---|
| `oregon-state`, `washington-state` | full | holdovers ("Pac-2") |
| `boise-state`, `colorado-state`, `fresno-state`, `san-diego-state` | full | announced Sept 2024 |
| `utah-state` | full | announced Sept/Oct 2024 |
| `gonzaga` | full, **non-football** | announced Oct 2024; no football since 1941 |
| `texas-state` | full | admitted June 30, 2025; paid the Sun Belt about $5M; the needed 8th football school |

- 8 football members and 9 basketball members.
- **12 affiliate members across five Olympic sports.** Wrestling has 9 teams: Oregon State plus affiliates Air Force, Cal Poly, CSU Bakersfield, Little Rock, Northern Illinois, Northern Colorado, North Dakota State and South Dakota State. I could not get the other four affiliates (men's soccer and others).
- Softball comes back for 2027 with 7 schools.
- **No 2027+ members have been announced.**

### Mountain West: 10 full members, 2 football-only, plus affiliates
| School | Type | Note |
|---|---|---|
| `air-force`, `nevada`, `new-mexico`, `san-jose-state`, `unlv`, `wyoming` | full | holdovers |
| `hawaii` | full (new July 1, 2026) | was football-only 2012-26, other sports in the Big West |
| `utep` | full (new July 1, 2026) | from C-USA |
| `grand-canyon` | full, non-football (since July 1, 2025) | from the WAC |
| `uc-davis` | full, non-football (new July 1, 2026) | from the Big West; football stays FCS Big Sky |
| `northern-illinois` | football-only (2026) | other sports in the Horizon League; women's gymnastics is an MWC affiliate; wrestling is a Pac-12 affiliate |
| `north-dakota-state` | football-only (2026) | other sports in the Summit League; wrestling is a Pac-12 affiliate; FBS transition |

- 10 football members, so each team plays 8 conference games and misses one opponent.
- Other affiliates: Utah Tech (baseball, men's soccer) and Colorado College (women's soccer).
- In 2026 the MWC said it was **pausing expansion** while it negotiates media deals. **No 2027+ members have been announced.**
- **NDSU eligibility:** it plays a full MWC schedule but cannot play in the MWC title game or the CFP until **2028**. It can reach a bowl only as a backfill, and sources disagree on even that. Entry costs: a $12.5M MWC entry fee, confirmed by AD Matt Larsen, plus about $5M to the NCAA.

## Corrections to the brief
1. **UC Davis is a Mountain West full member for 2026-27 (non-football) and was missing from the brief.** I added a `uc-davis` record. Its football is Big Sky (FCS), so it may also appear in `data/schools/fcs.json`; dedupe by id.
2. **North Dakota State is football-only in the MWC.** Its other sports remain in the **Summit League**, not the Horizon League; one search summary got this wrong. Its **wrestling moved from the Big 12 to the Pac-12** as an affiliate. In the record: `conference.y2026 = {all:"summit", football:"mountain-west", level:"FBS"}`, and it is postseason-ineligible until 2028.
3. **NIU's other sports did go to the Horizon League:** 14 sports, $1.4M entry fee paid over six years. Gymnastics is an MWC affiliate and wrestling is a Pac-12 affiliate. In the record: `y2026.all = "horizon"`.
4. **Hawaii became a full MWC member on July 1, 2026.** It was football-only before.
5. **Grand Canyon joined the MWC in 2025-26, a year before the rest.** In 2010 it was in D-II's PacWest (slug `pacwest`), not just generic "D-II".
6. **Gonzaga and Texas State are full Pac-12 members** as expected. Texas State was a later add (June 2025) to reach the NCAA's 8-football-school minimum.
7. **UC Davis 2010 slugs:** football was in the Great West (slug `great-west`, defunct) and other sports in the `big-west`.
8. **The MWC 2010 slug:** I used `mountain-west` rather than a `-2010` slug, because the conference is the same entity even though the 2010 roster included BYU, Utah and TCU.
9. **SCHEMA canonical list:** add `uc-davis` to the Mountain West list. `northern-illinois` and `north-dakota-state` should be marked football-only.

## Leadership changes found in 2025-26
These are mostly from my training knowledge and were not re-checked:
- **WSU:** President Elizabeth Cantwell (2025, from Utah State); AD Anne McCoy (2025); football coach Jimmy Rogers left for Iowa State in Dec 2025, with Kirby Moore believed hired (low confidence).
- **Utah State:** President Cantwell left, then interim Alan L. Smith, then believed Brad Mortensen (low confidence). AD Jerry Bovee made permanent (low confidence).
- **Oregon State:** football coach Trent Bray believed dismissed in 2025, with JaMarcus Shephard believed hired (low confidence).
- **Colorado State:** football coach Jay Norvell fired in Nov 2025, with Jim Mora believed hired (low confidence). MBB coach Niko Medved left for Minnesota and Ali Farokhmanesh took over (2025).
- **Hawaii:** President Wendy Hensel (2025).
- **Wyoming:** Ed Seidel's contract was not extended; Kevin Carman is interim president (low confidence).
- **Men's basketball coaching changes in 2025:**
  - UNLV: Josh Pastner.
  - New Mexico: Eric Olen, after Richard Pitino left for Xavier.
  - Air Force: Joe Scott is believed out; I could not confirm a successor, so the name is `null`.

## Notable storylines (event seeds)
- **Pac-12 collapse and rebuild.** Ten schools left in 2023-24. OSU and WSU sued and won control of the board (WA Supreme Court declined review, Dec 2023). They used the NCAA's two-year grace period, a 2024-25 MWC football scheduling deal, and WCC affiliation for other sports.
  - The rebuild started with Boise State, Colorado State, Fresno State and SDSU (Sept 2024), then Utah State, then Gonzaga (Oct 2024), then Texas State (June 2025).
  - The commissioner is Teresa Gould. The CFP treats the Pac-12 as a G6 conference.
- **Exit and poaching fees.** The scheduling agreement contained a **poaching penalty**: the Pac-12 owed the MWC escalating fees per school it took, reported in the tens of millions (about $43M for five; low confidence).
  - Each departing school also owed MWC exit fees of about 2× the annual distribution, roughly $17-19M each (low confidence).
  - Both leagues sued (2024), and the MWC also pursued Utah State over grant-of-rights claims. Settlement terms were not verified here; see the `legal-exit-fees-gor` research.
- **SDSU's 2023 brinkmanship.** SDSU sent a June 2023 letter about possibly leaving. The MWC treated it as a withdrawal notice; SDSU disputed that, then backed down. This is a model for an "exit notice gambit" event.
- **Gonzaga** turned down Big 12 and Big East interest and took a full, non-football Pac-12 deal. It is the league's NCAA-unit engine and also its biggest flight risk if basketball money disappoints.
- **Loyalists:** Air Force, Hawaii (upgraded to full member), UNLV, Nevada, New Mexico, SJSU and Wyoming stayed in the MWC. UNLV was the most courted; reports say it received retention incentives (low confidence).
- **UNLV and Allegiant Stadium.** UNLV plays in the NFL Raiders' publicly financed stadium. The 2024 Matthew Sluka NIL dispute is a model for an NIL-broken-promise event.
- **SJSU volleyball (2024).** Opponents forfeited over a transgender athlete, the MWC was sued, and the issue drew federal Title IX attention. This is a model for a culture-war / federal-intervention event.
- **Utah State (2024).** Coach Blake Anderson and AD Diana Sabau were fired over Title IX reporting, and litigation followed. This is a model for a compliance-scandal event.
- **NDSU's FBS jump (Feb 2026).** Costs were a $12.5M MWC fee plus about $5M to the NCAA. It is postseason-ineligible until 2028 and leaves the Dakota Marker and Nickel Trophy rivalries behind. It is a future full-member target for the MWC or a poaching target for the Pac-12.
- **Grand Canyon** was formerly for-profit and converted to nonprofit in 2018. The Education Department disputed that and fined it about $37.7M in 2023. President Brian Mueller is also CEO of Grand Canyon Education. These suit accreditation and regulatory events.
- **Political actors:**
  - Washington and Oregon legislatures (WSU, OSU).
  - The CSU system and chancellor (SDSU, Fresno, SJSU budgets).
  - The Texas legislature and university systems (Texas State, UTEP).
  - The Wyoming legislature.
  - Hawaii's legislature (stadium, travel).
  - Nevada's NSHE (UNR's president Brian Sandoval is a former governor).
  - The ND Board of Higher Education (NDSU).
  - Federal DoD/Congress (Air Force).
- **Rivalries cut by realignment** are pressure points for scheduling events: Border War (CSU–Wyoming), Ram-Falcon (CSU–Air Force), Bridger's Rifle (USU–Wyoming), Valley Trophy (Fresno–SJSU), SDSU–UNLV basketball, and the I-35 rivalry (Texas State–UTSA).

## Game-model implications
- **Leaguewide comparison:** the Pac-12 and MWC are near-peers.
  - Pac-12 average football rating is about 33 vs about 27 for the MWC football schools. Boise State (50) is the only top-G6 brand, and UNLV (42) is the MWC's.
  - Basketball favors the Pac-12: Gonzaga 82, SDSU 68, USU 60 and Boise 55, against the MWC's New Mexico 55 and GCU 50.
  - Starting media value should rank Pac-12 > MWC by a modest margin (about 1.2-1.5×), not P4-like.
- **Poaching risk weights.** Highest are Boise State, UNLV, SDSU and Gonzaga, as P4 or cross-league targets, then NDSU after 2028. Model each holdover with a loyalty stat; Air Force and Hawaii should be high because of structural constraints (travel and federal control).
- **Exit fee formula seed:** about 2× the annual conference distribution, plus a counterparty poaching penalty that declines per school taken.
- **NDSU-style FBS transition mechanic:**
  - entry fee $12.5M plus NCAA fee about $5M;
  - two-year postseason ban;
  - booster influence above 50 lowers the approval barrier.
- **Non-football full members** (Gonzaga, GCU, UC Davis) should count toward basketball NCAA units and media inventory but not toward the 8-football-school FBS minimum. Texas State's admission is the precedent for "we need one more football school."
- **Hybrid memberships:** state-political-pressure values of 55-70 (Texas State, Wyoming, NDSU, Hawaii, WSU, OSU) mean the legislature or board must approve moves. Make it a probabilistic veto or delay.
- **Revenue-share mechanic:** in the House settlement, G6 schools opted in but share well below the cap. A per-school `revShareSpend` starting at about 15-40% of the cap fits this group; it needs verification.
