# Private capital in college sports

Owner: money-postseason agent. As of 2026-11-25.

> **Research caveat.** The shared web-search budget ran out before this topic could be searched. **Every record in `data/private_capital.json` is from researcher recall** (training data through mid-2026) and the brief, marked `"confidence": "low"`, with general-reference sources (Wikipedia pages for the parties). Verify each deal in a follow-up pass: amounts, dates, status, and who opposed what.

## File shape

`data/private_capital.json` is an array of `{id, parties[] (school/conference IDs + investor slugs), level ("school" | "conference" | "industry"), announced (YYYY or YYYY-MM), status ("closed" | "failed" | "talks"), amountUsd, equityOrStake, structure, strings, returnExpectations, opposition, outcome, confidence, note, sources}`.
Investor slugs: `otro-capital`, `redbird-capital`, `weatherford-capital`, `uc-investments`, `cvc-capital-partners`, `elevate`, `collegiate-sports-management-group`, `arctos-partners`, `sixth-street`, plus person slug `cody-campbell`.

## The deals (summary)

| id | Parties | Status | Size | Key strings |
|---|---|---|---|---|
| `utah-otro-capital` | Utah + Otro Capital (Alec Scheiner) | closed (Dec 2025) | undisclosed | Minority stake in **Utah Brands & Entertainment LLC**, a for-profit commercial entity. The university keeps control of athletics. |
| `big-12-redbird-weatherford` | Big 12 + RedBird/Weatherford ("Collegiate Athletic Solutions") | talks, not closed | ~$1B reported | Minority stake in a Big 12 commercial entity. Return tied to the next media cycle. |
| `big-ten-uc-investments` | Big Ten + UC Investments | **failed** (shelved late 2025 / early 2026) | ~$2.4B for ~10% of "Big Ten Enterprises" | GOR extension to ~2046 and **unequal upfront payouts**. **Michigan and USC opposed.** |
| `cvc-big-12-pac-12` | CVC + Big 12 / Pac-12 | talks, no deal | n/a | The La Liga-style model of a long-dated revenue cut. |
| `elevate-csmg-proposals` | Elevate/Velocity, CSMG ("College Sports Tomorrow") | pitches | n/a | Centralized super-league commercial company. |
| `fsu-clemson-pe-exploration` | FSU, Clemson | explored, overtaken by the March 2025 ACC settlement | n/a | Funding exit fees and litigation. |
| `arctos-college-sports` / `sixth-street-college-sports` | Arctos; Sixth Street | studied / offered structured capital | n/a | Minority-equity vs royalty/credit models. |
| `kentucky-athletics-llc` | Kentucky | restructured into an LLC (2025) | none | A precondition for outside capital. |
| `texas-tech-campbell-booster-capital` | Texas Tech + Cody Campbell | ongoing booster model | n/a | Not PE. The counterexample of a single dominant booster. |

Sources (general references, to be replaced with deal reporting): [Utah Utes](https://en.wikipedia.org/wiki/Utah_Utes), [RedBird](https://en.wikipedia.org/wiki/RedBird_Capital_Partners), [Big Ten](https://en.wikipedia.org/wiki/Big_Ten_Conference), [CVC](https://en.wikipedia.org/wiki/CVC_Capital_Partners), [Arctos](https://en.wikipedia.org/wiki/Arctos_Partners), [Sixth Street](https://en.wikipedia.org/wiki/Sixth_Street_Partners), [ACC](https://en.wikipedia.org/wiki/Atlantic_Coast_Conference).

## Themes

- **Why now.** House revenue sharing (a $20.5M cap rising ~4%/yr) plus ~$1M/yr per school in back-damage cuts created a funding gap of $10-30M per school. Media money is locked into long contracts, so schools and leagues looked at **selling a slice of future commercial revenue for cash now**.
- **Conference vs school.** Conference-level deals fail on **unanimity and equality**. Big brands (Michigan, USC) won't accept a long GOR or sell future upside, and the deals that pay brands unequally split the room. School-level deals (Utah) go through faster because a single board can approve them.
- **Structure menu.** (a) Minority equity in a commercial LLC (Utah, Big Ten Enterprises). (b) A long-dated revenue participation (CVC/La Liga). (c) Royalty or credit against media receivables (Sixth Street-style). (d) Centralized super-league equity (CSMG/Elevate).

## Corrections to the brief

1. Big Ten + UC Investments was reported at **~$2.4B** for ~10%, not ~$2B (both figures circulated). **Michigan and USC** were the named opponents, consistent with the brief's "Michigan, USC?". Low confidence.
2. No verified 2025-26 PE deal was found for **LSU, Kansas or Texas Tech**. Texas Tech's money comes from booster Cody Campbell, not PE. **Kentucky's LLC conversion** is the main other school-level structural move.
3. Big 12 + RedBird/Weatherford: **no deal had closed** as of last verified reporting (low confidence). It should not be treated as completed.

## Game-model implications

- **PE offer generator** (conference or school): `upfront = stake% × EV`, with `EV = 6-10 × annual commercial revenue` (media + sponsorship + events; lower multiples for G6). Typical stake: 5-15% (conference), 10-30% (school commercial LLC).
- **Investor return target:** 15-25% gross IRR for equity, 9-13% yield for royalty/credit. If league revenue growth undershoots, raise the investor's governance pressure (events: "investor demands cost cuts / neutral-site games / Las Vegas events / sponsorship patches").
- **Strings (tunable):** a required GOR extension of +10-20 years; 1-3 investor board seats on the commercial entity (not the presidents' board); revenue waterfall priority for the investor's share; optional "unequal upfront" (`brandWeight` 0-1) that boosts big brands' utility and hurts small schools' cohesion.
- **Vote mechanics:** conference PE deals need **unanimity** or the GOR-amendment threshold. Each president's utility = `cashNow × urgency(budget gap) - futureShareCost × discount - controlAversion - stateFlag`. Big brands have high `controlAversion` and low urgency, so they tend to oppose (the Michigan/USC pattern).
- **Risk events:** the faculty senate objects; the state legislature or attorney general reviews a public university's equity sale; the investor flips its stake; a conference media renewal comes in below the investor's model and triggers a dispute.
