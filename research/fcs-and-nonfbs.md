# FCS & non-FBS Division I conferences (as of 2026-11-25)

Owner: nonfbs-conferences agent. Files:

| File | Shape |
|---|---|
| `data/conferences_nonfbs.json` | Array of 26 `Conference` records (SCHEMA.md). Extra keys: `recentChanges` (2022-26 moves, same shape as `pendingChanges`), `mediaDeal` (Big East only), `football.autoBid`, `football.footballMembers`, per-object `confidence`/`note`. For `D1-non-football` leagues, `members2026.nonFootball` = `full`. For football-only leagues (`mvfc`, `pioneer`, `uac`, `big-south-ovc`), `full` = football members. |
| `data/schools/fcs.json` | Array of 123 `School` records: every 2026 FCS football school except Georgetown, Butler and Villanova (covered by the Big East agent) and North Dakota State (treated as FBS/Mountain West, see below). Extra key: `conference.y2010.note`. President/AD/coaches are `null`; revenue fields are `null`. |
| `data/schools/d1-other-light.json` | Array of 82 minimal records for non-FBS, non-football D-I schools (added at the coordinator's request), excluding the coordinator's skip list. Fields: id, name, shortName, mascot, city, state, control, religious, conference.y2026 {all, football:null, level:null}, conference.y2010, ratings {mbb, wbb, olympic, brand}, confidence, note, sources. |

## IMPORTANT: verification status

I could not verify anything live. The shared WebSearch budget was used up before my first query
returned ("limit: 200 WebSearch calls per turn, shared by every agent"), and WebFetch could not
reach `en.wikipedia.org` or `ncaa.com` (DNS blocked in this session). **Everything here comes
from model knowledge (reliable to about mid-2025, patchy into 2026).** Every school record and
almost every conference record is marked `confidence: "low"`. The `sources` URLs are the
standard Wikipedia and conference-site pages where each fact can be checked. They were not
fetched. To re-verify, allow `en.wikipedia.org` in the environment network settings or start a
session with search budget left, then check the items flagged **(verify)** below first.

## Conference list (2026-27)

FCS = holds an FCS automatic-bid football league. `D1-non-football` = all other non-FBS D-I
conferences; their members' football runs through one of the FCS leagues.

| id | Conference | HQ | Commissioner (since) | Conf. | Full / FB members |
|---|---|---|---|---|---|
| `big-sky` | Big Sky | Ogden, UT | Tom Wistrcill (2017) | med | 10 / 11 FB (+Cal Poly, UC Davis FB-only) |
| `caa` | Coastal Athletic Assn / CAA Football | Richmond, VA | Joe D'Antonio (2017) | med | 13 / 13 FB |
| `ivy` | Ivy League | Princeton, NJ | Robin Harris (2009) | high | 8 / 8 |
| `meac` | MEAC | Norfolk, VA | Sonja Stills (2021) | med | 8 / 6 |
| `mvfc` | Missouri Valley Football | St. Louis, MO | Patty Viverito (1985) **(verify: retirement/successor)** | low | 9 (10 if NDSU stayed) |
| `nec` | Northeast Conference | Somerset, NJ | Noreen Morris (2010) | med | 9 / 8 FB (incl. Duquesne, RMU affiliates) |
| `big-south-ovc` | Big South–OVC Football Assn | Brentwood, TN | jointly run by the OVC/Big South (DeBauche/Montgomery) | low | 9 |
| `patriot` | Patriot League | Center Valley, PA | Jennifer Heppel (2015) | med | 10 / 9 FB (Fordham, Georgetown, Richmond*, W&M* FB-only) |
| `pioneer` | Pioneer Football League | St. Louis, MO | Patty Viverito (1991) **(verify)** | low | 11 |
| `socon` | Southern Conference | Spartanburg, SC | Michael Cragg (2023) **(verify)** | low | 10 / 9 |
| `southland` | Southland | Frisco, TX | Chris Grant (2022) | med | 12 / 10 |
| `swac` | SWAC | Birmingham, AL | Charles McClelland (2018) | high | 12 / 12 |
| `uac` | United Athletic Conference (ASUN+WAC football) | Englewood, CO | run by the WAC/ASUN offices, see WAC **(verify)** | low | 9 |
| `america-east` | America East | Cambridge, MA | Amy Huchthausen (2013) **(verify)** | low | 9 |
| `asun` | ASUN | Atlanta, GA | Jeff Bacon (2019) | low | 12 |
| `a10` | Atlantic 10 | Newport News, VA | Bernadette McGlade (2008) **(verify)** | low | 14 |
| `big-east` | Big East | New York, NY | Val Ackerman (2013) **(verify status)** | low | 11 |
| `big-south` | Big South | Charlotte, NC | Sherika Montgomery (2023) | med | 9 |
| `big-west` | Big West | Irvine, CA | Dan Butterly (2016?) | low | 12 (incl. Hawaii**, Utah Valley*) |
| `horizon` | Horizon League | Indianapolis, IN | Julie Roe Lach (2021) | high | 11 |
| `maac` | MAAC | Edison, NJ | Travis Tellitocci (2022) **(verify)** | low | 13 |
| `mvc` | Missouri Valley | St. Louis, MO | Jeff Jackson (2022) | med | 11 |
| `ovc` | Ohio Valley | Brentwood, TN | Beth DeBauche (2010) | med | 11 |
| `summit` | Summit League | Elmwood Park, IL | Josh Fenton (2017) | low | 8 (Denver* gone; NDSU non-FB) |
| `wac` | WAC | Englewood, CO | Rich Hilton (2023) **(verify)** | low | 6 |
| `wcc` | West Coast Conference | San Bruno, CA | Stu Jackson (2023) | high | 10 (Gonzaga gone; Denver* in) |

\* low-confidence 2026 move. ** Hawaii kept in the Big West (status quo). It may have moved all
sports to the Mountain West in 2026 **(verify)**.

**Big East detail.** Reconstituted in 2013 when the "Catholic 7" took the name and the Madison
Square Garden tournament. The football charter became the American (`big-east-2010` lineage).
Val Ackerman has been commissioner since 2013. She was the first WNBA president and a former NBA
executive, and trained as an attorney. Whether she is still commissioner in November 2026 is
unverified. She is in year 13, and succession talk is plausible. If a successor was named in
2025-26, replace the record. FOX has been the lead partner since 2013 (the original 12-year
deal was worth about $500M). The 2023 renewal runs through 2030-31 with FOX as primary partner
and NBCU (NBC/Peacock) and reportedly TNT Sports as secondary partners; the value is unverified.
Members: Butler, Creighton, DePaul, Georgetown, Marquette, Providence, St. John's, Seton Hall,
UConn, Villanova, Xavier. Their football plays elsewhere: UConn as an FBS independent, Villanova
in CAA (FCS), Georgetown in the Patriot League (FCS), Butler in the Pioneer League (FCS). Men's
tournament at MSG, women's at Mohegan Sun.

### Commissioner changes 2024-26

None could be confirmed this session. These are the jobs where a 2024-26 change is plausible.
Treat each as **verify** before the game uses it:
- **Big East (Ackerman)**: long tenure, possible succession.
- **A-10 (McGlade, since 2008)**: possible retirement.
- **MVFC/Pioneer (Viverito, since 1985/1991)**: reported to be near retirement. A successor, or
  the MVC's Jeff Jackson taking over football, is possible.
- **WAC/UAC**: the commissioner's identity is uncertain (Jeff Hurd led the 2021 expansion; I am
  not sure who succeeded him). A rebrand of the WAC as the UAC may also have happened.
- **SoCon**: Michael Cragg vs Jim Schaus.
- **America East and MAAC**: not re-verified.

Changes already known before 2024 that the data uses: WCC hired Stu Jackson (2023, after Gloria
Nevarez left for the Mountain West). The Big South promoted Sherika Montgomery (2023, after Kyle
Kallander). The MVC hired Jeff Jackson (2022, after Doug Elgin). The Southland hired Chris Grant
(2022). The Horizon hired Julie Roe Lach (2021).

## FCS → FBS move-ups

| School | From → To | First FBS season | Notes |
|---|---|---|---|
| James Madison | CAA → Sun Belt | 2022 | Bowl-ineligible in transition; an NCAA waiver was denied in 2023, but JMU still went to a 2023 bowl because there were not enough eligible teams. |
| Jacksonville State | ASUN → CUSA | 2023 | Went to a bowl in transition year 2 for the same reason. |
| Sam Houston | WAC → CUSA | 2023 | Exit-fee/distribution dispute with the WAC (low confidence on details). |
| Kennesaw State | ASUN (Big South FB) → CUSA | 2024 | |
| Delaware | CAA → CUSA | 2025 | Transition 2025-26. |
| Missouri State | MVFC/MVC → CUSA | 2025 | |
| Sacramento State | Big Sky → FBS independent (2025) → **MAC football-only** | 2026 | Other sports stay in the Big Sky (low confidence). |
| North Dakota State | MVFC → **Mountain West football-only** (Summit otherwise) | 2026 | **Low confidence.** The brief lists NDSU in the MWC, and I recall reports of the move, but cannot confirm it. If NDSU stayed FCS, add it to `mvfc` and `fcs.json` (rating ~35). |

No further announced FCS→FBS moves for 2027+ are known (low confidence).

**Reclassification mechanics** (verify current bylaws):
- An FCS→FBS move needs an invitation to an FBS conference (or an independent schedule
  acceptable to the NCAA).
- There is a two-year transition. In transition the school is counted as FBS for scheduling but
  is ineligible for the CFP and bowls, except when there are not enough bowl-eligible teams
  (2023 precedent).
- Legacy FBS criteria: 16+ sports, scholarship/aid minimums (rewritten after the House
  settlement as roster limits, 105 in football), and an average attendance of 15,000 once every
  two years (rarely enforced).
- Historically there was no meaningful NCAA fee for FCS→FBS moves. The 2024-25 D-I governance
  overhaul reportedly added a reclassification fee of about $5M (**low confidence**).
- D-II→D-I applicants pay a multi-million-dollar fee (reported around $2.5M) and serve a
  multi-year transition (historically 4 years) without NCAA tournament eligibility.

**D-II/D-III → D-I joiners since 2020** (useful as precedents): Bellarmine, Dixie State/Utah
Tech, Tarleton, UC San Diego, St. Thomas (straight from D-III, 2021), Lindenwood, Southern
Indiana, Texas A&M-Commerce/East Texas A&M, Queens, Stonehill (2022), Le Moyne (2023),
Mercyhurst, West Georgia (2024), New Haven (2025). UTRGV started football in 2025.

**D-I → D-III exits:** Hartford (2023). **Saint Francis (PA)** announced a move to D-III in 2025
because of costs after the House settlement. It is treated as gone for 2026-27 (low confidence
on timing).

## FCS leagues at risk

1. **MEAC (6 football members)**: at the floor. One loss threatens football viability, and its
   Celebration Bowl tie stops it from using an automatic bid.
2. **Big South–OVC (9)**: an alliance of two shrinking leagues that has already lost Kennesaw,
   Bryant and RMU. Tennessee State's institutional crisis adds risk.
3. **NEC (8, two of them affiliates)**: lowest budgets. Lost Saint Francis, Merrimack and
   Sacred Heart. It depends on Duquesne and RMU as affiliates and on recruiting D-II schools.
4. **UAC (9)**: spans Georgia to Utah. Its two parent leagues (ASUN, and a WAC of about 6
   members) are fragile, and its best programs (Tarleton, ACU) want to move up.
5. **MVFC (9)**: strong but being picked off by FBS (Missouri State, NDSU). South Dakota State
   and UND are the next targets.
6. **CAA (13)**: large but losing quality (JMU, Delaware, and possibly Richmond/W&M to the
   Patriot League).
7. **Pioneer (11)**: non-scholarship and coast-to-coast travel. Members are more likely to drop
   football than to move up.

Stable: SWAC, Ivy, Patriot (gaining), Big Sky (lost only Sac State), SoCon, Southland.

## Most realistic FBS candidates

Capacities come from the school records. Budgets are order-of-magnitude bands (low confidence;
check Knight-Newhouse/USA Today finance data).

| School | Stadium (cap.) | Approx. athletics budget | Market | Case | Main obstacle |
|---|---|---|---|---|---|
| Montana State | Bobcat Stadium (~20.8K) | $30-40M | Butte-Bozeman (small) | 2021/2024 runner-up, booster money, facility investment | Montana Regents may insist on a joint move with UM; travel |
| Montana | Washington–Grizzly (~25.2K) | $30-40M | Missoula (small) | Best FCS fan base; sells out | Small market; politics of a joint move |
| South Dakota State | Dykhouse (~19.3K) | $30-40M | Sioux Falls (~#110) | 2022-23 champion; NDSU's path is the template | Market; facilities need FBS-level upgrades |
| UC Davis | UC Davis Health (~10.7K) | $40M+ (many sports) | Sacramento (#20) | Big market, AAU, MWC interest in 2024-25 | Stadium size; UC Regents/student-fee politics |
| Idaho | Kibbie Dome (~16K) | $25-30M | Spokane DMA | Ex-FBS (1996-2017), new arena | Budget; it left FBS for cost reasons |
| Tarleton State | Memorial Stadium (~24K) | $30M+ | DFW fringe | Texas A&M System backing, ambitious | D-I only since 2020 |
| Abilene Christian | Wildcat Stadium (~12K) | $25-35M | Abilene (~#165) | Private money, new stadium | Market, size |
| Chattanooga | Finley (~20.7K) | $20-30M | Chattanooga (~#86) | Downtown stadium, UT System | Budget, attendance |
| Southern Utah | Eccles (~8.5K) | ~$20M | SLC DMA (rural) | Moved to the WAC to set up an FBS jump | Stadium, budget, results |
| Lamar | Provost Umphrey (~16K) | ~$20M | Beaumont (~#142) | Houston recruiting area; tried the WAC route in 2021 | Results, market |
| Others to model | Stephen F. Austin (UT System), UTRGV (big market, new program), Eastern Kentucky (20K stadium), Youngstown State (20.6K), North Dakota, Northern Iowa (UNI-Dome), Jackson State (60K stadium, attendance leader), NC A&T (21.5K), Villanova (Big East; turned down FBS in 2011-12), Incarnate Word (San Antonio) | | | | |

## ID conventions used (for other agents)

- `william-mary`, `north-carolina-at`, `north-carolina-central`, `alabama-am`, `florida-am`,
  `prairie-view-am`, `east-texas-am`, `texas-am-corpus-christi`: `&` is dropped, following the
  schema's `texas-am`.
- `citadel`, `mcneese`, `nicholls`, `southern` (Southern University), `utrgv`, `st-thomas` (MN),
  `southeast-missouri-state`, `grambling-state`, `arkansas-pine-bluff`, `liu`, `seattle-u`,
  `american-university` (avoids clashing with the conference id `american`),
  `boston-university`, `loyola-maryland`, `loyola-marymount`, `uic`, `iu-indianapolis`,
  `cal-baptist`, `ut-arlington`, `cal-state-bakersfield` / `-fullerton` / `-northridge`,
  `long-beach-state`, `saint-josephs`, `st-bonaventure`, `saint-peters`, `mount-st-marys`,
  `fairleigh-dickinson`, `charleston` (College of Charleston), `uncw`, `unc-greensboro`,
  `unc-asheville`, `usc-upstate`, `florida-gulf-coast`, `kansas-city`, `omaha`, `denver`,
  `saint-francis-pa` (left D-I).
- 2010 conference ids beyond the schema: `gwc` (Great West Conference, D-I, 2004-13),
  `independent-fcs`, `independent-d1`, `sun-belt` (2010 non-football members such as Denver and
  Little Rock), and D-II/NAIA/D-III leagues as `lone-star-d2`, `gulf-south-d2`, `psac-d2`,
  `ne10-d2`, `glvc-d2`, `ccaa-d2`, `pacwest-d2`, `miaa-d2`, `conference-carolinas-d2`,
  `independent-d2`, `heart-of-america-naia`, `gsac-naia`, `miac-d3`. The `level` field stays
  within the schema enum. NAIA and D-III show as `"none"` with a `y2010.note`.

## Corrections to the brief

- **North Dakota State**: the brief puts it in the Mountain West. That is consistent with my
  recollection but unverified. I kept NDSU out of `fcs.json` and out of the MVFC (in the Summit
  as a non-football member) so there is no duplicate id. The schools-west agent must include it.
- **Grand Canyon** has no football. It is a Mountain West non-football member (since 2025).
- **CAA vs CAA Football**: legally separate football operations under one umbrella. I modelled
  them as one `caa` record with `footballOnly` affiliates (Albany, Bryant, Maine, UNH, Rhode
  Island, Villanova).
- **"Big South-OVC"** is a football association, not a conference, with no commissioner of its
  own. The Big South and OVC themselves are `D1-non-football` in this data.
- **UAC vs WAC**: the UAC is the ASUN+WAC football partnership. The WAC has shrunk to about 6
  members and may have rebranded as the UAC for all sports **(verify)**.
- **Sacramento State**: MAC football-only (FBS) from 2026. Other sports stay in the Big Sky (low
  confidence).
- **UMass** left the A-10 for the MAC (all sports) in 2025. Delaware and Missouri State are FBS
  (CUSA) since 2025.
- **Richmond and William & Mary** football moved to the Patriot League in 2026 (low confidence).
  Robert Morris football is back in the NEC (low confidence).
- **Saint Francis (PA)** has left D-I for D-III, so the NEC has 8 football members including
  affiliates.
- **Gonzaga to the Pac-12** ends the WCC's main revenue source. Denver replaced it (low
  confidence).
- The brief's example "Villanova as an FCS power" is right: Villanova plays CAA football, not
  Big East football.
- 2026 FCS count: **126** football programs by this data (123 in `fcs.json` + Georgetown,
  Butler, Villanova), or 127 if NDSU stayed.

## Game-model implications

- **Move-up pipeline.**
  - Score each FCS school each season: `fbsReadiness = 0.25*facilities + 0.2*fanBase +
    0.15*boosterInfluence + 0.15*football + 0.15*marketScore(dma rank) + 0.1*brand`.
  - FBS conferences short of members (MAC, MWC, CUSA, Pac-12) invite from the top 10 when
    `fbsReadiness > ~30`.
  - Cost of moving up, all tunable:
    - NCAA reclassification fee: `5_000_000` (low confidence).
    - Entry fee to the FBS conference: $2-15M, or forgone distributions.
    - FCS exit fee: $0.5-3M plus 12-24 months' notice.
    - Operating budget: +$8-20M a year.
    - Two transition seasons with no bowls unless there is a shortage (10% chance each year).
- **Football-only FBS affiliations** (Sac State to the MAC, NDSU to the MWC, NIU to the MWC)
  are now the dominant pattern. The game should let a school be FBS in football while staying in
  a non-football D-I league (Summit, Big Sky).
- **FCS league viability.** Use ≥6 football members for an automatic bid (verify the NCAA
  bylaw). Fewer than 6 for 2 seasons means the automatic bid is lost, which triggers a scramble
  (merge, alliance, or independence). A multisport D-I conference needs at least 7 members with
  a two-year grace period. The WAC (about 6) is the live test case. Alliances
  (Big South-OVC, UAC) are the game's "merge" mechanic.
- **Down-movers.** After the House settlement, some small privates drop to D-III (Hartford,
  Saint Francis). Model a yearly 1-2% chance for schools with `brand < 10` and
  `boosterInfluence < 10`.
- **Up-movers from D-II.** About one school a year (Mercyhurst, New Haven, West Georgia). The NEC,
  ASUN and OVC absorb them.
- **Commissioner job market** (26 non-FBS + 10 FBS jobs).
  - Tiers:
    - Tier A: Big East.
    - Tier B: A-10, WCC, MVC, CAA, Big Sky, MVFC, Ivy, SWAC.
    - Tier C: the rest.
  - Rough salary bands (low confidence, check 990s):
    - Tier A: $1.5-2.5M.
    - Tier B: $0.5-0.9M.
    - Tier C: $0.25-0.5M.
  - Typical tenure is 8-15 years, so about 2-4 openings a year among the 26.
  - Backgrounds, most to least common: conference deputy, then attorney or NCAA staff, then
    former AD, then pro-league executive (Ackerman, Stu Jackson).
  - Career ladder: a Tier C commissioner moves to Tier B, or into a P4 or FBS deputy job.
- **Revenue.** For non-FBS leagues, NCAA basketball tournament units are the largest pooled
  revenue (one unit is worth about $2M paid over 6 years). Media deals, mostly ESPN+, are small
  ($0.1-1M per school). The Big East's FOX deal is the exception. Losing a multi-bid program
  (Gonzaga from the WCC) cuts unit income for years.
- **HBCU leagues.** Revenue from neutral-site classics and the Celebration Bowl means the SWAC
  and MEAC skip the FCS playoffs. Keep `autoBid: false` and add a "classic game" revenue event.

## Sources (canonical; not fetched this session)
- FCS program list: https://en.wikipedia.org/wiki/List_of_NCAA_Division_I_FCS_football_programs
- D-I institutions list: https://en.wikipedia.org/wiki/List_of_NCAA_Division_I_institutions
- D-I conferences list: https://en.wikipedia.org/wiki/List_of_NCAA_Division_I_conferences
- Conference pages and official sites are listed in each record's `sources` (e.g.
  https://bigskyconf.com, https://caasports.com, https://valley-football.org, https://www.bigeast.com,
  https://wccsports.com, https://wacsports.com).
