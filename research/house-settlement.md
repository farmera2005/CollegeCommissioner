# House settlement and athlete revenue sharing

Owner: money-postseason agent. As of 2026-11-25.

> **Research caveat.** The shared web-search budget ran out before this topic could be searched. `data/house_settlement.json` is built from researcher recall (through mid-2026) and the brief, with the [House v. NCAA](https://en.wikipedia.org/wiki/House_v._NCAA) Wikipedia article as the main reference. The following are **well established**: the final approval date (2025-06-06), the $20.5M year-1 cap, the $2.576B back damages, the Deloitte "NIL Go" clearinghouse with its $600 reporting threshold, CSC CEO Bryan Seeley, and the football (105) and basketball (15) roster limits. The rest is `"confidence": "low"`.

## File shape

`data/house_settlement.json` is an object with these keys:
- `case`: court, judge, dates, term, appeals
- `cap`: basis, escalator, scholarshipCredit, `byYear[]` from 2025-26 to 2034-35, where years 4-10 are model projections
- `rosterLimits.bySport[]`: `{sport, limit, priorScholarships}`
- `backDamages`: total, components, athlete allocation, `funding[]` by payer pct, per-school annual hit
- `optIn`: deadline, meaning, count (null), opt-out examples
- `nilGo`: operator, $600 threshold, rules
- `collegeSportsCommission`: CEO, role, participation agreement, `enforcementActionsToDate[]`
- `financialStrain.examples[]`
- `titleIX.issues[]` and `allocationExamples[]`
- `sources`

## Key facts

- **Approval.** Judge Claudia Wilken (N.D. Cal.) gave final approval on **2025-06-06**. Revenue sharing started **2025-07-01** and runs for 10 years (through 2034-35). Objectors (Title IX, walk-ons) appealed to the Ninth Circuit. The appeal outcome as of Nov 2026 was not verified.
- **Cap.** It is set at 22% of average P4 "shared revenue" (media + tickets + sponsorship): **$20.5M in 2025-26**, **+4%/yr in years 2-3** (2026-27 ≈ **$21.32M**, 2027-28 ≈ $22.17M), and **recalculated in year 4 (2028-29) and year 7 (2031-32)**. Up to $2.5M of added scholarships counts toward it. The out-years in the JSON assume ~6%/yr P4 revenue growth (2028-29 ≈ $24.5M, 2034-35 ≈ $32.6M).
- **Back damages.** **$2.576B** over 10 years (~$278M/yr), about **$2.8B** with fees. Broadcast-NIL damages are split **75% football / 15% men's basketball / 5% women's basketball / 5% other**. Funding (low confidence): NCAA 41%, P4 conferences 24%, G5 10%, FCS 14%, non-football D-I 11%, mostly through reduced NCAA distributions. That works out to roughly ~$1M/yr per P4 school, ~$450K per G6 school and ~$300K per FCS or non-football school.
- **Roster limits** replace scholarship caps for opted-in schools: football 105, MBB/WBB 15, baseball 34, softball 25, soccer 28, volleyball 18, and others. Designated Student-Athletes are grandfathered.
- **Opt-in** (deadline 2025-03-01). All P4 schools and Notre Dame opted in, as did most G6 schools; many FCS and non-football schools opted in mainly for roster flexibility. The Ivy League stayed out. The exact count was not verified (roughly 300+).
- **NIL Go (Deloitte).** Athletes must report third-party deals of **$600 or more**. Deals from associated entities (collectives, boosters) are tested for a **valid business purpose** and a **range of compensation**, with appeals to arbitration.
- **College Sports Commission.** CEO **Bryan Seeley**, formerly MLB's enforcement chief, since June 2025. It was set up by the four P4 conferences. The binding participation agreement faced state AG and school pushback, and its rollout was delayed in late 2025. Known actions: guidance and deal rejections aimed at collective pay-for-play. **No major public sanctions were confirmed** in the researcher's data.
- **Strain.** Most G6 schools pay **well below the cap** (budgets of roughly $1-10M). P4 schools fund the cap with ticket "talent fees" (Tennessee), staff layoffs (USC, Stanford) and deficits (Cal, on a reduced ACC share). Saint Francis (PA) is moving from D-I to D-III. A list of sports dropped since 2024 was **not compiled**.
- **Title IX.** The 75/15/5/5 back-pay split was challenged and overruled at approval, then appealed. Most schools mirror that split for forward revenue sharing. The Biden-era Department of Education guidance (Jan 2025) treating revenue share as Title IX athletic aid was rescinded in Feb 2025.

## Corrections to the brief

1. Cap escalator: the brief's "4% annual increases + reset every 3 years" is **consistent** with the term sheet as recalled. The resets fall in **years 4 and 7** (2028-29, 2031-32), and **2026-27 = ~$21.3M**. Low confidence pending verification.
2. Back damages are **$2.576B** in the settlement itself. "$2.8B" includes fees and costs.
3. "Opting in" ≠ paying the full cap. Many opted-in schools pay a fraction, so the game should model opt-in and pay level separately.

## Game-model implications

- **Cap path:** `cap[2025]=20.5M`. `cap[y]=cap[y-1]×1.04`, except reset years `y ∈ {2028, 2031}`, where `cap = 0.22 × avgP4SharedRevenue[y-2]`. Expose `capGrowth=0.04`, `resetShare=0.22`, `resetYears=[4,7]` in `/config/economy`.
- **School pay level:** `pay = min(cap, f(budgetSurplus, boosterInfluence, ambition))`. Defaults: P4 85-100% of cap (most pay 100%); G6 5-40% (American top tier ~20-40%, MAC/CUSA ~5-15%); FCS opt-ins ~0-5%. Each ~10% of cap underpaid should cost about -1 to -2 rating points per year in football/MBB recruiting.
- **Allocation:** default `{football: 0.75, mbb: 0.15, wbb: 0.05, other: 0.05}`. Allocations that favor women's sports raise the Title IX risk score less and help Olympic ratings and reputation, but pull down football and MBB.
- **Back-damage drag:** subtract the per-school hit from NCAA distributions for 2025-26 through 2034-35 (P4 ~$1.0M, G6 ~$0.45M, FCS/non-FB ~$0.3M).
- **Budget-stress model:** when `expenses + revShare > revenue + reserves + donor capacity`, the school first raises fees, then lays off staff, then cuts Olympic sports (lowest-attendance men's sports first, constrained by Title IX), and finally considers a division drop. Seed events from this.
- **CSC enforcement events:** NIL Go rejects a collective deal (common); arbitration win or loss; a CSC investigation leads to a fine or roster-spot penalty (rare); a state passes a law shielding its schools, creating conflict with the CSC (governance-politics hook); Ninth Circuit ruling on the Title IX appeal (one-time event, 2026-27 window).
- **Roster limits:** football 105 sets roster-cost scaling. Olympic-sport roster cuts generate negative press and Title IX complaints.
