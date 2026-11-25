# Event Engine Seeds: real-world precedents (as of 2026-11-25)

Owner: governance-politics agent. File: `data/event_seeds.json`. It contains 60 templates. Related systemic forces (bills, lawsuits, executive orders) live in `data/external_forces.json`; see `research/governance-politics.md`.

**Sourcing caveat.** Historical precedents cite Wikipedia or major-outlet pages and were not re-fetched this session: WebFetch was blocked and the shared search budget ran out. Events from 2025-26 cite the news results found during the session. Templates that rely on details not re-verified carry `"confidence": "low"` and a note.

## File shape
```
{ id, category, title,
  realPrecedents: [{ year, summary, source }],
  description,                 // generic, playable framing
  typicalChoices: [string],    // 3-5 options
  relevantAttributes: [ ... ], // from: mediaNegotiation, presidentialRelations, legalGovernance, commercial,
                               //       publicImage, crisisManagement, network, vision, integrity, stamina
  severityRange: [min, max],   // 1-5 scale (below)
  suggestedAnnualProbability,  // per conference-season, P4 baseline (notes give G6/region multipliers)
  confidence?, note?, sources: [url] }
```

### Severity scale
| Sev | Meaning | Typical stakes |
|---|---|---|
| 1 | News cycle | ±1-3 publicImage, minor PC swings |
| 2 | Regional story | One member's relationship ±10 PC, small fines |
| 3 | National story | League revenue or media value ±1-3%, a vote may be forced |
| 4 | Existential for a member | Membership, CFP bid or a leadership job at risk |
| 5 | Existential for the league | Realignment cascade, commissioner job on the line |

### Coverage (60 templates)
scandal 11 · rival-power-play 7 · officiating 4 · rogue-president 5 · political 5 · disaster 5 · tv-renegotiation 4 · ratings 4 · legal 4 · leak 3 · travel 3 · cinderella 2 · sport-dropped 2 · health 1

## Precedents covered (brief checklist)
- **Michigan sign-stealing.** Stalions (2023), Petitti's Sportsmanship-Policy suspension of Harbaugh (2023-11-10), and the NCAA's August 2025 penalties: `scandal-sign-stealing`.
- **Baylor, Penn State.** `scandal-abuse-coverup`. Includes the conference levers used: the Big 12 withholding 25% of distributions, and the Big Ten redirecting Penn State's bowl money.
- **UNC academic fraud:** `scandal-academic-fraud`.
- **Ole Miss/MSU:** `scandal-booster-recruiting-violations`.
- **Louisville and the FBI basketball case** (Auburn, Arizona, Oklahoma State, USC, LSU, Kansas, NC State): `scandal-fbi-bribery-probe`.
- **2025-26 point shaving:** `scandal-point-shaving` (indictment details low confidence). Athlete betting (Iowa/ISU, Alabama baseball): `scandal-athlete-gambling`.
- **Officiating.** Pac-12 2018 replay interference, Oregon-OU 2006, Fifth Down 1990, Michigan-OSU 2024 brawl fines, and playoff snubs (FSU 2023, TCU/Baylor 2014). No well-documented 2025 replay scandal was verified (see corrections).
- **Hurricanes.** Katrina/Tulane, Matthew (Sankey moving LSU-Florida), Irma, Helene. Plus COVID 2020 (Big Ten postponement and reversal, Warren backlash, Trump call).
- **Travel.** Stanford/Cal/SMU in the ACC, the Big Ten West Coast schools, Hawaii subsidies.
- **Rogue presidents and boards.** WSU/OSU suits, FSU/Clemson, Maryland exit fee, Arizona's Robbins finances, UCLA's Block, Maryland regents and McNair, Michigan regents vs. Big Ten private equity, and LSU 2026.
- **Rival power plays.** Texas/OU leak (Houston Chronicle, 2021-07-21), USC/UCLA (2022-06-30), the Big 12's 2023 raid, Pac-12/MWC poaching, the SEC-Big Ten duopoly, private capital, and Kiffin leaving before the CFP.
- **TV.** ESPN's ACC option, the Big 12's 2022 early extension, the ESPN-Pac-12 lowball, Apple and Pac-12 Networks, carriage blackouts.
- **Ratings booms.** Deion's Colorado, Indiana 2024-25 (2025-26 title, low confidence), Caitlin Clark.
- **Cinderellas.** UMBC, Saint Peter's, FAU, Boise State (2007 and 2024), Cincinnati 2021.
- **Sports dropped.** COVID-era cuts and reversals, Saint Francis (PA) going to D-III.
- **Legal and political.** Pavia, Bediako, Borovicanin, DeWine's order, Texas 1994, Virginia 2003, SCORE/PCSA votes, athlete activism.

## Corrections to the brief
1. **"2025 storms."** No 2025 Atlantic hurricane caused verified large-scale college disruption on the scale of Helene (2024) or Ian (2022), so the hurricane templates use 2005-2024 precedents (low confidence; not re-verified).
2. **"Temple/others"** (point shaving). Temple (Hysier Miller, 2024-25) was investigated after betting alerts. The NCAA's 2025 findings cited Fresno State, San Jose State and New Orleans players. A January 2026 federal indictment broadened it. Specific schools and counts are **not verified**.
3. **"2025 officiating controversies, Big Ten/Big 12 replay errors."** None specific was verified. The template uses durable precedents instead.
4. **Michigan follow-up.** Beyond the brief: the NCAA's August 2025 penalties, and Sherrone Moore's firing for cause in December 2025 (`scandal-coach-personal-misconduct`).
5. **New 2026 precedent not in the brief.** The **SEC's attempt to expel LSU** (vote 2026-12-03) is the defining 2026 "rogue member" template.
6. **"Schools dropping sports post-House."** Clear cases of D-I programs cutting sports specifically because of House in 2025-26 could not be verified beyond Saint Francis (PA) going to D-III. The template relies on 2020 COVID cuts as the main precedent.
7. **Cal deficit and WSU/OSU debt.** Covered generally by `rogue-president-finances` and `rogue-member-sues-conference`. Dollar figures belong in the school files (schools-west, schools-b12-acc agents).

## Game-model implications

### Attribute-modified outcomes
For each choice `c` in an event, define a success probability:
```
p(c) = clamp( base_c + Σ_a w_{c,a} * (attr_a - 50) / 100 + modifiers, 0.05, 0.95 )
```
- `w` is about 0.3-0.6 for the template's `relevantAttributes`. The first-listed attribute is primary (w about 0.6) and later ones are secondary (w about 0.3).
- **Integrity** also scales *backlash* when a cover-up choice is later exposed. Use P(exposure) = 0.25 × (1 − integrity/100) per year, with severity +1 when it comes out.
- **Stamina** sets how many severity ≥ 3 events the commissioner can handle in one season before a fatigue penalty (−10% to all p(c)). Suggested cap: 1 + stamina/30.
- **crisisManagement** shrinks the realized severity: `sevRealized = sevRolled − floor(crisisManagement/40)`, minimum `severityRange[0]`.

### Probability calibration
- `suggestedAnnualProbability` is the P4 baseline. Multipliers:
  - G6: ×2-3 for `scandal-point-shaving`, `sport-dropped-*`, `rogue-president-finances`
  - Gulf or Southeast footprint: ×1-3 for hurricane templates
  - multi-time-zone leagues: travel templates
- Generate events with a Poisson draw on each template's annual rate, spread over the season calendar (e.g., hurricanes August-October, Cinderellas in March, TV renewals in the offseason, CSC actions any time).
- **Chaining.** Some events feed `external_forces`. `rogue-member-defies-eligibility` raises the odds of a federal EO 14400 nudge, and `legal-title-ix-suit` moves the House-appeal remand odds. Some forces also spawn events: if the PCSA is enacted, cut `rival-conference-raid` to ×0.25.

### Precedent-derived commissioner levers worth implementing
- **Withhold or redirect distributions** as discipline (Big 12/Baylor 2017, Big Ten/Penn State 2012).
- **Suspend under a sportsmanship policy before the NCAA acts** (Petitti 2023). High integrity gain, lawsuit risk about 0.5, member PC −20.
- **Move or reschedule games by fiat** (Sankey and Hurricane Matthew 2016). Costs PC with the school that loses the home game.
- **File first in a friendly venue** when a member threatens to sue (ACC vs. FSU, December 2023).
- **Early media extension** to lock members in (Big 12 2022), versus **go to market** (Pac-12 2023 cautionary tale).
