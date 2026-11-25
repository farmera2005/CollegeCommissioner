# Schools: SEC (16) and Big Ten (18), 2026-27

Files: `data/schools/sec.json` (16 records) and `data/schools/big-ten.json` (18 records). Both follow the `School` schema in `research/SCHEMA.md`, and both pass `JSON.parse`.

## Status and limitations (read first)

- **No live verification this pass.** The shared web-search budget (200 calls per turn, across all agents) was used up before this agent started. Direct fetches to `en.wikipedia.org` and `www.espn.com` were blocked by the session network allowlist. Every record was compiled from model knowledge, which runs to about mid-2026.
- **Not captured:** anything after about June 2026. That includes 2026 football results through November, fall 2026 firings, the spring 2026 men's basketball coaching carousel, and 2026 presidential or AD appointments.
- **Allowing `en.wikipedia.org` (or raising `CLAUDE_CODE_MAX_WEB_SEARCHES_PER_SESSION`) and re-running a verification pass is recommended.**
- **How uncertainty is marked:**
  - Each record has `lowConfidenceFields` (dotted paths) and a record-level `note`.
  - Leadership objects carry their own `confidence: "low"` and `note` where uncertain.
  - `athletics.confidence: "low"` flags money figures recalled rather than re-read.
- **Extension fields** (`lowConfidenceFields`, nested `confidence`/`note`, `athletics.confidence`) are additive, so loaders can ignore them.
- **One deliberate null:** Illinois `president.name` is `null`, because the chancellor seat is believed vacated (see corrections).

## Field-level sources (apply to all records)

| Field | Source | Notes |
|---|---|---|
| `athletics.revenueUsd/expensesUsd` | USA Today / Knight-Newhouse NCAA finances DB: https://sports.usatoday.com/ncaa/finances ; https://knightnewhousedata.org | FY2024 rounded estimates. Private schools (Vanderbilt, Northwestern, USC) are absent from the DB; their values are EADA-style estimates (https://ope.ed.gov/athletics/). Public-school "revenue" includes institutional subsidies (matters for Rutgers, Maryland, UCLA). |
| `athletics.revShare*` | House v. NCAA settlement (approved June 6 2025, Judge Wilken). Cap $20.5M in 2025-26, +4%/yr, so about $21.3M in 2026-27. | Every SEC and Big Ten school opted in and publicly committed to the full cap. "Verify" is noted for deficit schools (Maryland, Rutgers, UCLA, Washington, Northwestern). |
| `usNewsRank` | U.S. News Best National Universities: https://www.usnews.com/best-colleges/rankings/national-universities | Values are from the 2025/2026 editions as recalled, ±5 ranks. All flagged low. |
| `aau` | AAU member list: https://www.aau.edu/who-we-are/our-members | High confidence. |
| `dma` | Nielsen Local TV Market Universe Estimates (2025-26): https://www.nielsen.com | Ranks recalled from 2024-25/2025-26 lists, ±3 for mid/small markets. Top-20 markets are reliable. |
| `endowmentUsd` | NACUBO-Commonfund Study of Endowments (FY2024): https://www.nacubo.org | Rounded. Some figures are system-level (Texas = UT System incl. PUF $47B; Texas A&M = System + foundations ~$20B; Missouri, Tennessee, Nebraska, Illinois, Minnesota = system/foundation), as stated in each record's note. |
| `ratings.olympic` | Learfield Directors' Cup: https://nacda.com | Tiered from recalled recent finishes. Texas won the last five straight (2020-21 through 2024-25). |
| Stadium / arena capacity | Official athletics sites (URLs in each record) | Capacities in flux: Beaver Stadium (renovation), Memorial Stadium MO (renovation), FirstBank (rebuild done 2025), Ryan Field (new 2026), Indiana Memorial Stadium (south end zone). |
| Leadership | School and athletics sites in each record's `sources` | 2025-26 changes are listed below. |

## Leadership changes found (2025-26 cycle)

**Football (10 new head coaches, all hired Oct to Dec 2025):**

| School | Change |
|---|---|
| LSU | Kelly fired Oct 26 (~$54M buyout, disputed). **Lane Kiffin** hired |
| Ole Miss | Kiffin left Nov 30. **Pete Golding** promoted and took Ole Miss to the CFP semifinal |
| Florida | Napier fired. **Jon Sumrall** (Tulane) hired |
| Auburn | Freeze fired. **Alex Golesh** (USF) hired |
| Arkansas | Pittman fired Sept. **Ryan Silverfield** (Memphis) hired |
| Kentucky | Stoops out (~$37M). **Will Stein** (Oregon OC) hired |
| Penn State | Franklin fired Oct 12 (~$49M). **Matt Campbell** (Iowa State) hired |
| Michigan | Moore fired for cause Dec 10. **Kyle Whittingham** (Utah) hired |
| Michigan State | Smith fired. **Pat Fitzgerald** hired (low confidence) |
| UCLA | Foster fired Sept. **Bob Chesney** (JMU) hired |

- Retained after losing seasons: Fickell (Wisconsin), Locksley (Maryland), Beamer (South Carolina).

**Men's basketball:**
- Steven Pearl replaced the retiring Bruce Pearl at Auburn (Sept 2025).
- The 2025 carousel produced these coaches, now in their second year: Sean Miller (Texas), Bucky McMillan (Texas A&M), Buzz Williams (Maryland), Darian DeVries (Indiana), Ben McCollum (Iowa), Niko Medved (Minnesota).
- **The spring 2026 carousel is not captured.** Hot-seat coaches, flagged low: McMahon (LSU), Moser (OU), Paris (SC), Jans (MSU), Rhoades (PSU), Diebler (OSU), Collins (NU), Pikiell (Rutgers), Sprinkle (UW).

**Athletic directors:**
- LSU: Woodward pushed out Oct 2025 under pressure from Gov. Landry. Verge Ausberry took over.
- Recent hires, all low confidence on dates: Roger Denny (OU), Laird Veatch (Mizzou), J Batt (MSU), Keli Zinn (Rutgers), Mark Jackson (NU), Jim Smith (MD), Jeremiah Donati (SC).

**Presidents and chancellors:**

| School | Status |
|---|---|
| Texas A&M | Welsh resigned Sept 2025. Interim Tommy Williams; System Chancellor Glenn Hegar |
| Texas | Jim Davis succeeded Hartzell, who left for SMU |
| Florida | Interim Donald Landry, after the BOG rejected Santa Ono |
| Michigan | Interim Domenico Grasso, after Ono left |
| Northwestern | Interim Henry Bienen, after Schill resigned |
| USC | Interim Beong-Soo Kim, after Folt left |
| Rutgers | William Tate IV arrived from LSU |
| LSU | Wade Rousse |
| Washington | Robert J. Jones, from Illinois, succeeding Cauce (low) |
| Wisconsin | Possible Mnookin departure (low) |

## Corrections to the brief

1. **Canonical IDs are correct.** SEC = 16, Big Ten = 18, exactly as listed in SCHEMA. No membership corrections for 2026-27.
2. **AAU:**
   - Nebraska is the only non-AAU Big Ten member (17 of 18 are members); it was voted out in 2011.
   - SEC AAU members: Florida, Missouri, Texas, Texas A&M, Vanderbilt (5 of 16).
3. **2010 lineage:**
   - Texas, Texas A&M, Oklahoma, Missouri and Nebraska are coded `big-12` (same legal entity; 12 members then).
   - Oregon, Washington, USC and UCLA are coded `pac-10`.
   - Maryland is coded `acc`.
   - Rutgers is coded `big-east-2010` (the football Big East whose charter became the American).
4. **The schema's example Ohio State record is fine.** Its 66,000 enrollment is all campuses; OSU is kept at that figure for consistency with the example. Other schools use main-campus headcount (Penn State 49k University Park, Rutgers 44k New Brunswick).
5. **The brief's "Michigan sign-stealing aftermath" has been superseded.**
   - The NCAA ruling (Aug 2025): no postseason ban and no vacated 2023 title, but large fines (est. $20M+, including forfeited postseason revenue), a 10-year show-cause for Harbaugh, and a suspension for Moore.
   - Moore was then fired for cause in Dec 2025 over an unrelated misconduct case.
6. **Indiana, not a blue blood, is the reigning national champion** (16-0 in 2025, Heisman for Fernando Mendoza). The Big Ten has now won three straight titles (Michigan 2023, Ohio State 2024, Indiana 2025).
7. **Northwestern stadium:** the new ~$862M Ryan Field (35,000) was scheduled to open for the 2026 season. The 2024-25 seasons were played at the lakefront Martin Stadium. Opening not verified.
8. **The 2026 SEC football schedule is 9 games with three protected opponents** (approved 2025). Protected pairs are recorded in notes where recalled; the conferences agent owns the authoritative list.
9. **The Illinois/Washington leadership swap** (Robert J. Jones to UW president, 2026) is believed correct but unverified. Illinois `president.name` is therefore `null`. If wrong, set Illinois back to Jones and UW to Cauce or an interim.

## Notable storylines (for event seeds)

**SEC**
- **Governor as athletic director (LSU).**
  - Gov. Jeff Landry publicly undercut AD Scott Woodward, who was then forced out, and shaped the Kiffin hire.
  - The Kelly buyout dispute, Woodward's exit and Kiffin's deal (~$13M/yr) create budget stress.
- **Poaching mid-postseason (Ole Miss).** Kiffin left before the CFP; Ole Miss barred him from coaching the playoff and promoted Golding, who reached the semis. Template for a "coach leaves before the bowl" event.
- **Texas vs. Texas A&M politics.**
  - The rivalry returned in 2024 after legislative pressure.
  - Welsh's 2025 resignation followed state lawmakers' pressure.
  - The Schlossnagle defection (2024) is a grievance.
  - Both campuses sit under Abbott- and Patrick-aligned regents.
- **Florida governance chaos.** Sasse resigned (2024), the Board of Governors rejected Ono (2025), Landry is interim. DeSantis appointees decide. Napier was fired (third straight fired coach).
- **Booster-driven buyouts.**
  - Fisher (A&M, $76.8M, 2023), Kelly (~$54M), Franklin (~$49M, PSU), Stoops (~$37M), Napier (~$21M), Freeze (~$16M).
  - Suggested mechanic: buyout size scales with `boosterInfluence`.
- **State laws vs. the NCAA (Tennessee).** The AG Skrmetti lawsuit (2024 NIL injunction) and the state direct-pay law. Danny White's ticket "talent fee" (fans fund revenue share). The Iamaleava holdout is the player-leverage archetype.
- **Kentucky basketball.** Calipari's 2024 defection to Arkansas, Pope's expensive roster, and UK athletics' 2025 conversion to an LLC structure (recalled; verify).
- **Vanderbilt's investment bet.** The only private SEC school has made a ~$300M+ facilities push and gone from 2-10 (2023) to 10 wins (2025). Pavia's NCAA lawsuit is a precedent. Low state pressure, top academics.
- **Oklahoma's SEC transition costs.** Reduced phase-in shares, dormant Bedlam (legislators grumble), and a planned Norman arena district.
- **Auburn's political wildcard.** Bruce Pearl retired and is considering politics (2026 Senate chatter). Gov. Ivey is ex officio board president of both Auburn and Alabama.
- **Dawn Staley (South Carolina)** is the most powerful women's basketball voice, with three titles since 2017.

**Big Ten**
- **Private capital and GoR extension fight.**
  - The late-2025 "Big Ten Enterprises" proposal: about $2B+ from UC Investments (the University of California's investment office) for an equity stake, tied to extending the grant of rights to about 2046.
  - Michigan and USC objected and the plan stalled. That makes them a veto bloc vs. Ohio State and Commissioner Petitti.
  - Owned by money-postseason / private-capital agents; flagged here for school-level `notes`.
- **Michigan's fall.** The sign-stealing penalties, then Moore's for-cause firing and arrest (Dec 2025), then Whittingham at 66. An interim president, and elected regents.
- **Penn State's ~$49M Franklin buyout.** Paired with the $700M Beaver Stadium renovation, campus closures, and annual 2/3-vote state appropriation fights in Harrisburg.
- **Have-nots: Rutgers and Maryland.** Structural deficits, advances on Big Ten distributions, NJ/MD legislative scrutiny. Washington, UCLA and Wisconsin are a squeezed middle with projected deficits.
- **UCLA under the UC Regents.**
  - The Cal subsidy obligation (~$10M/yr) and travel-mitigation mandates.
  - The federal research-funding freeze (2025).
  - The Rose Bowl lease dispute over a possible SoFi move (verify).
  - Highest state-intervention score in the Big Ten (78).
- **USC/UCLA/Oregon/Washington travel complaints.** Olympic-sport cross-country travel and academic-impact reports. A natural "West Coast pod" or scheduling-reform event.
- **Oregon: Phil Knight.** Booster score 98 (the archetype). Oregon State was left behind; the Pac-12 rebuild.
- **Northwestern rebuild and politics.** The hazing scandal (2023) and Fitzgerald settlement, the stadium rebuild with Evanston zoning, Schill's resignation, and the federal-funding settlement.
- **Indiana's worst-to-first.** Cignetti's ~$93M extension, a donor surge, and state control of the IU board (2025 budget law).
- **Nebraska academic status.** The sole non-AAU member, a potential lever if the Big Ten ever ties membership to academics.

## Game-model implications

- **Ratings are calibrated to the start of the 2026 season.** The engine should apply 2026 in-season results itself rather than trust `football` as of Nov 2026.
- **Suggested coaching-buyout model:**
  - `buyoutUsd ≈ remainingYears × annualSalary × 0.6–0.9`
  - Probability of firing after a sub-.500 season = `0.15 + 0.004 × boosterInfluence + 0.003 × fanBase`, capped at 0.85. This reproduces 2025: LSU, Penn State, Florida, Auburn, Arkansas and Kentucky fired; Wisconsin and Maryland kept.
- **State-intervention events:**
  - Trigger chance per season = `statePoliticalPressure / 400`. LSU (95) gives about 24%; Northwestern (15) about 4%.
  - Effects: AD removal, forced rivalry scheduling (Texas/A&M, Bedlam, Apple Cup, Clemson/SC), presidential vetoes.
- **Revenue-share stress:**
  - Define `stress = (revShareCap + scholarships) / (revenueUsd − subsidies)`.
  - Rutgers, Maryland, UCLA and Washington should hit deficit-driven events (cut sports, borrow from the conference, seek private equity).
  - Texas, Ohio State, Michigan, Georgia and Alabama should not.
- **Veto blocs in conference votes:**
  - Big Ten: Michigan + USC vs. private capital.
  - SEC: Texas, A&M and OU are politically constrained (state legislatures must be "consulted" before any exit).
  - Vanderbilt is an academic-prestige swing vote.
- **The AAU flag** should weigh on Big Ten expansion votes. Candidates without AAU membership take a penalty; the precedent is Nebraska's 2011 expulsion.
