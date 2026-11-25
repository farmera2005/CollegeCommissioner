# Founding (or breaking away to form) a conference

Owner: history-founding agent. As of 2026-11-25.

## File shapes

**`data/ncaa_rules.json`** is an object. Top level: `{asOf, verificationNote, multisportConference, fbsConference, fbsSchool, reclassification, autonomy, cfpAccess, ncaaTournamentAutoBid, fcsPlayoffAutoBid, sources}`.
- Each section has an `id`, a `summary`, numeric fields (for example `minimumFootballMembers: 8` and `gracePeriod.years: 2`), descriptive text, a `gameDefault` block of tunables, `confidence` and `sources`.

**`data/precedents.json`** is an array of 16 records.
- Each record: `{id, name, years, type, summary, steps[], keyPeople[{name, role, confidence?}], money{startupCostsUsd, feesUsd, initialMediaDeal{partner, years, annualValueUsd, ...}, notes}, obstaclesAndHowSolved[{obstacle, solution}], gameModelLessons[], sources[], confidence?, note?}`.
- The 16 records:
  - Formations and collapses: the 1999 WAC split (MWC), the SWC collapse and Big 12, the 1979 Big East, the 1995 C-USA merger, the Sun Belt's 2001 football launch.
  - Raids and failed expansions: the 2003-05 ACC raid cascade, the 2010 Pac-16 failure, the 2012 MWC/C-USA merger that never happened, the 2016 Big 12 no-expansion.
  - Splits and rebuilds: the 2013 Catholic 7 split, the American's formation, the 2023-26 Pac-12 rebuild.
  - Exit litigation: FSU/Clemson v. ACC.
  - Collapse and alliance: the WAC football demise, the ASUN-WAC alliance, the UAC.
  - Concepts and pipelines: super-league ideas, the FCS move-up pipeline.

**Verification status.**
- The web-search budget ran out early in this session.
- Rule values that are widely reported carry no confidence flag: the 8-member FBS minimum, the 2-year grace period, the 7-member AQ rule with its 2-year wait, 16 sports, the invite requirement, and the $5M fee.
- Bylaw numbers are omitted.
- The attendance rule's status, financial-aid minimums, continuity-of-membership thresholds and new-conference CFP admission are flagged `low` and need an NCAA LSDBi check ([LSDBi](https://web3.ncaa.org/lsdbi/)).

## The rules that gate a new league

1. **D-I multisport conference.** At least **7 active D-I members**. The conference must sponsor men's and women's basketball plus other championships. Each member needs 14 D-I sports (16 if FBS).
2. **FBS football conference.** At least **8 FBS football members**. Football-only affiliates count.
   - A league that drops below 8 gets a **two-year grace period**. The Pac-12 used it in 2024-25 and 2025-26 with only OSU and WSU, and rebuilt to exactly 8 for 2026.
   - The MWC never fell below 8. It reached 10 in 2026 with NIU and NDSU as football-only members ([2026 MWC season](https://en.wikipedia.org/wiki/2026_Mountain_West_Conference_football_season)).
3. **NCAA basketball automatic bid.**
   - The league needs **7 core institutions**. A new league waits **two years** unless the continuity-of-membership rule applies, meaning about 6-7 schools that played together for about 5 years in a prior league.
   - The MWC (1999) and the new Big East (2013) both got their automatic bids immediately under that rule.
   - NCAA tournament revenue **units stay with the old conference**. A breakaway starts at zero unless a separation agreement says otherwise.
4. **FBS school requirements.**
   - 16 sports (6 men's or mixed, 8 women's).
   - At least 60% of games against FBS opponents, including at least 5 FBS home games.
   - Football aid at 90% of the maximum (before the House settlement), and 200 grants-in-aid or $4M in athletic aid. The Transformation Committee proposed raising this to 210 grants or $6M (low confidence).
   - The 15,000 average-attendance rule is still on the books but not enforced.
5. **Moving up from FCS.**
   - The school must have an **invitation from an FBS conference**. Liberty's 2017 waiver was the exception. Sacramento State's 2025 waiver was denied.
   - The move takes **2 transition years** with no bowls or CFP.
   - The **NCAA fee is $5M**, per 2026 reporting for NDSU and Sacramento State ([SI](https://www.si.com/college-football/north-dakota-state-football-to-pay-hefty-price-to-make-jump-to-fbs)).
6. **Autonomy / Power 4.** This is a named club created in 2014, not a status earned by meeting metrics.
   - After the House settlement, the Power 4 run the College Sports Commission.
   - The Pac-12 moved into the G6 revenue pool for the College Football Playoff from 2026-27.
7. **College Football Playoff access.** Details are in `cfp.json`.
   - **2026-27:** the four Power 4 champions plus the top-ranked G6 team receive automatic bids, and 7 teams get at-large bids.
   - **2027-2031:** the field becomes **24 teams** (decided 2026-11-09). It keeps the four Power 4 champions and one G6 bid, adds 19 at-large bids, and ends Power 4 title games ([CFP](https://collegefootballplayoff.com/news/2026/11/9/24-team-expansion)).
   - **Revenue split:** SEC 29%, Big Ten 29%, ACC 17.25%, Big 12 14.75%, G6 pool 9%, Notre Dame about $12.5M ([CBS](https://www.cbssports.com/college-basketball/news/college-football-playoff-finalizes-tv-deal-beginning-in-2026-as-fbs-leaders-settle-on-revenue-distribution)).
   - **A new FBS conference is not automatically a CFP party.** It must negotiate into the agreement, most realistically as a seventh G6 league. A Power 4-level breakaway would need a memorandum-of-understanding amendment that the SEC and Big Ten effectively control. This is inferred, low confidence.

## How real leagues were founded: the patterns

| Pattern | Example | Members at start | Time from first meeting to first game | Key enabler |
|---|---|---|---|---|
| Cohesive breakaway | MWC 1999 | 8 | ~14-18 months | Continuity (immediate automatic bid); timely notice, so no fees |
| Brand buyout | Big East 2013 | 7 + 3 | ~7 months | Traded money for the name and Madison Square Garden; FOX needed content for FS1 |
| Charter rename | American 2013 | 10 | 0 (continuing entity) | Kept the charter, reserves and automatic bid; new ESPN deal |
| Merger | C-USA 1995, Big 12 1996 | 12 | ~12-24 months | Pooled football schools; state politics |
| Football launch | Sun Belt 2001 | 7 | ~12 months | Inherited programs left homeless; football-only affiliates |
| Rebuild from a remnant | Pac-12 2024-26 | 2, then 9 | 33 months | Court win for control; 2-year grace period; poaching |
| Football-only alliance | UAC 2023 | ~9 | ~12-24 months | Two leagues jointly administer football to reach the FCS automatic bid |

Failed or abandoned attempts: the Pac-16 (2010), the MWC/C-USA merger (2012), Big 12 expansion (2016), the European Super League (2021), and the CSMG/private-equity "super league" pitches (2024-25).

## Founding checklist (in-game)

1. **Members.** Line up 8 or more FBS football schools (10 recommended) and 7 or more core basketball schools.
   - Football-only affiliates count toward 8. FCS move-ups count, but they are postseason-ineligible for 2 seasons.
   - Check for continuity: are 6 or more schools coming from the same prior league, together 5+ years?
2. **Exits.** For each member, compute bylaw fee + grant-of-rights damages + notice period.
   - Breakaways that give timely notice as a group can avoid fees (MWC 1999), or trade them for assets (Big East 2013).
   - Otherwise budget 40-60% of the claimed amount after litigation, plus legal costs.
3. **Legal entity and bylaws.** Incorporate a nonprofit. Set the board (presidents) and voting thresholds: expansion usually 3/4, bylaw changes 2/3. Write exit and grant-of-rights terms to protect the new league; the American's $10M plus 27 months' notice is a template.
4. **Name and brand.** Create one or buy one. An abandoned brand plus its marquee event (the Big East name and Madison Square Garden) can be worth more than cash.
5. **NCAA recognition.** Apply as a D-I conference (about 12 months' lead time). Confirm FBS status (8 or more members) and whether the automatic bid comes now (continuity) or after a 2-year wait.
6. **Commissioner and office.** Hire the commissioner first; the pool and costs are in `career_paths.json` and `commissioners.json`. Choose the HQ city (cost of living, airport hub, a member-neutral location).
7. **Media deal from scratch.** See `media_deals.json`. Benchmarks:
   - Basketball-only league with a strong brand: about $3-5M per school per year (Big East-FOX 2013).
   - Rebuilt G6 league: about $7-8M per football school per year (Pac-12 2026, about $68M a year in total).
   - G6 leagues generally: about $1-5M per school per year.
   - A broadcaster launching or filling a network is a demand spike to exploit (FS1 in 2013, The CW in 2024).
8. **Officiating.** Contract a crew pool, either standalone or through a shared consortium with a neighboring league. The Pac-12 and MWC used shared and western officiating arrangements.
9. **Championship sites.** Football title game at the top seed's campus (G6 default) or a neutral NFL stadium. Basketball tournament at a neutral arena, where Las Vegas and Madison Square Garden-style venues bring sponsorship.
10. **Scheduling.** Choose 8 or 9 conference games. Use scheduling alliances to fill gaps, and require poaching clauses in them.
11. **Postseason access.** Bowl tie-ins are negotiated individually with bowls. College Football Playoff membership comes through a memorandum-of-understanding amendment.
12. **Startup capital.** Cover 6-12 months of office costs, legal fees, help with members' exit fees, and a reserve against slow NCAA unit and media ramps.

### Suggested cost tunables (game estimates, not verified figures)

| Item | G6-level new league | P4-level breakaway |
|---|---|---|
| Conference office staff | 25-50 | 80-150 (excluding any network) |
| Office operating budget per year | $8-20M | $40-100M |
| Commissioner pay | $0.5-1.5M | $3-6M+ |
| Football officiating per year | $2-4M (about $15-25k per game) | $6-12M (about $35-50k per game, including replay center) |
| Legal and consulting at founding | $1-5M | $10-50M (antitrust, grant-of-rights fights) |
| Startup reserve | $10-25M | $100M+ |
| Exit-fee help for members | $0-50M (settlements) | $100M-1B+ (P4 grant-of-rights and exit schedules) |
| Media ramp | First deal 1-2 years after founding; short (3-6 years) | Needs a buyer at P4 rates; time to contract expiries (2030-36) |

Calibration anchors:
- The Pac-12 office had about 200 staff including the network before 2024, and was much smaller after.
- The early new Big East had about 25-35 staff (low confidence).
- Exit settlements: $9.8M per school (MWC 2026), $31.4M (Maryland 2014), $50M per school (Texas and Oklahoma 2023).

## Corrections to the brief

1. **The Pac-12 "poaching fee of about $55M"** was the Mountain West's claim. It settled on 2026-08-04 for about $10M each from Oregon State and Washington State, plus $49M from the five departing schools ($9.8M each).
2. **The Catholic 7 did not pay about $10M for the Big East name.** They took only about $10M of a pot of more than $100M (low confidence).
3. **The 1999 WAC split.** The "Laramie meeting" is not confirmed. The decisive meeting is more often placed near Denver International Airport in May 1998. The schools gave timely notice, so no exit fees were paid, and the Mountain West got its NCAA tournament automatic bid immediately through continuity of membership, not through a waiver (low confidence on mechanism).
4. **The attendance requirement (a 15,000 average)** is not clearly eliminated. It is unenforced, but formal repeal is unverified. Treat it as soft.
5. **The $5M reclassification fee** is real. It applies to schools moving from FCS to FBS and was paid by North Dakota State and Sacramento State in 2026. Conference entry fees now add $2-23M on top.
6. **College Football Playoff access** changed again after the brief.
   - 2026 stays at 12 teams, with automatic bids for the four Power 4 champions and the top G6 team.
   - From 2027 the field is 24 teams and Power 4 title games end.
   - The old 2024-25 rule ("five highest-ranked conference champions," which let any FBS league's champion earn a bid) no longer applies.
7. **The Pac-12** is a G6 member in College Football Playoff revenue from 2026-27, not a Power 4-equivalent. It kept full Power 5 College Football Playoff revenue only through 2025-26.

## Game-model implications

- **Founding gate checks** (all must pass before a "Launch league" action):
  - ≥8 FBS football members on the effective date, or a pre-existing grace period.
  - ≥7 basketball members.
  - A signed commissioner.
  - Bylaws approved.
  - A media deal signed, or reserves covering 2 seasons.
  - NCAA application filed at least 12 months ahead.
- **Automatic-bid clock.** If continuity applies, the bid comes in year 1. Otherwise there is a two-season wait, with no NCAA unit revenue and lower recruiting appeal.
- **Grace-period mechanic.** If football membership falls below 8, start a two-season countdown. If the league is not back at 8 when it ends, it loses FBS-conference status: no G6 champion eligibility for the College Football Playoff, bowl tie-ins void, and members free to leave without penalty.
- **Control-fight event.** When a majority of members give notice, the remainers can sue for control. Base win chance is about 0.6 if the bylaws have withdrawal-notice language. The winner keeps the name, reserves, units and College Football Playoff seat.
- **Poaching clauses.** Any scheduling alliance should let the player set a poaching penalty, declining per school taken. AI leagues demand one. Settlement typically lands at about 30-50% of the face value.
- **Brand-for-cash trade.** In separation negotiations, let factions swap a share of reserves for the name and marquee event (worth about +10-20 brand points to a basketball league).
- **Breakaway threat lever.** Power 4 leagues can threaten a breakaway to extract College Football Playoff or format concessions. Actual breakaways require ≥8 brands, financing, a media buyer, and the ability to survive political, Title IX and antitrust backlash. They should be timed to contract expiries (Big Ten 2030, College Football Playoff 2031-32, SEC 2034, ACC 2036).
- **Media-buyer demand spikes.** A broadcaster with a new network or empty inventory raises bids for a founding league by +25-50% (FOX/FS1 in 2013; The CW and USA in 2024-26).
- **Merging two leagues** carries a penalty: risk of losing units and automatic bids, plus contract renegotiation. Prefer "absorb members" over "dissolve and re-form."
- **The FCS pipeline** is the cheapest way to reach a member count. Each move-up costs the school about $5M to the NCAA, $2-25M in conference entry, and $5-15M a year in new spending, and brings two postseason-ineligible seasons.
