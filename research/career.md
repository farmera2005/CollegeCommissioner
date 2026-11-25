# Commissioner Career System — research notes (as of 2026-11-25)

Owner: career-people agent. Files: `data/commissioners.json`, `data/commissioner_history.json`,
`data/search_firms.json`, `data/career_paths.json`, `data/media_outlets.json`.

> **Research limits:** the shared web-search budget ran out mid-pass, and WebFetch could not reach
> ProPublica or philanthropy.org, so no 990 PDFs were read directly. Facts confirmed in this pass
> carry no flag. Facts taken from background knowledge carry `"confidence": "low"` (record level) or
> `lowConfidenceFields` (field level). Pay figures come from news reports of 990s, mostly USA
> Today/ESPN/On3, not the filings themselves.

## File shapes

- **commissioners.json**: an array. Uses the brief's fields plus `status` (`current` | `outgoing` |
  `interim`), `sinceDate`, `lowConfidenceFields`, and, for Yormark, `departureDate`/`nextRole`.
  `compensation[].year` is the calendar year the pay was earned. The 990 for a fiscal year reports
  the W-2 for the calendar year that ends inside it. `suggestedAI` holds six 1-20 values and one
  `rationale` line. `organization` uses conference IDs plus `ncaa` and `college-sports-commission`.
- **commissioner_history.json**: an array of `{id, conference, outgoing, incoming, date, effective?,
  year, reason, outgoingDestination, notes, sources}`. `date` is the announcement or hire date and
  `effective` is the start date. `reason` uses the brief's enum (retired, fired, resigned, poached,
  mutual) plus `interim` (an interim tenure ending) and `new-conference`.
- **search_firms.json**: an array of `{id, name, hq, specialty, keyPeople, notableSearches[{search, year,
  result}], notes, sources}`.
- **career_paths.json**: an object with `asOf`, `attributeKeys` (the game's 10 attributes in camelCase),
  `nonTraditionalHireTrend`, `backgroundProfiles[]` (each `startingAttributes` entry is a
  `[min,max]` range on the 1-20 scale), `exitDestinations[]`, `compensationRanges[]`,
  `contractNorms`, `performanceBonuses[]`, `buyoutsAndSeverance[]` and `sources`.
- **media_outlets.json**: an array of `{id, name, type, reporters[{name, beat, knownFor}], credibility
  (1-10, how accurate the outlet's in-game rumors are), sources}`.

## How commissioners are hired

- **Who decides:** the board of presidents and chancellors. A small executive or search committee of
  three to seven presidents runs the process, and the full board then votes, usually unanimously in
  public. Examples: the Big Ten committee was chaired by Maryland's Darryll Pines
  ([HuntScanlon](https://huntscanlon.com/turnkeyzrg-assists-big-ten-conference-in-recruiting-seventh-commissioner/)).
  The Big 12's was Schovanec, Livingstone and Girod
  ([Big 12](https://big12sports.com/news/2022/4/21/big-12-conference-retains-turnkeyzrg-for-commissioner-search.aspx)).
  The Pac-12's 2021 search was chaired by Oregon's Michael Schill. The AAC's was chaired by ECU's
  Philip Rogers. The NCAA's was chaired by Baylor's Linda Livingstone.
- **Search firms:** **TurnkeyZRG** ran every Power-conference commissioner search from 2020 to 2023.
  That covers the ACC/Phillips search (as Turnkey Search), Pac-12/Kliavkoff, Big 12/Yormark (chosen
  through an RFP) and Big Ten/Petitti. It also ran the NCAA/Baker search and AAC/Pernetti in 2024.
  The firm's chairman is Len Perna. The Mountain West's 2022 search likely used **Parker Executive
  Search**, which posts the Nevarez placement on its site, but this is unconfirmed. No firm has been
  named yet for the open Big 12 search (2026-27).
- **Timeline:** the usual gap from vacancy to hire is 3-5 months. The Pac-12 took about 4 months in
  2021 and looked at 200+ candidates. The ACC ran from August to December 2020. The Big Ten ran from
  January to April 2023. The AAC ran from December 2023 to April 2024. Departures are usually
  announced 3-6 months before they take effect: Yormark announced on Oct. 30, 2026 and leaves on
  Jan. 31, 2027 ([ESPN](https://www.espn.com/college-sports/story/_/id/50327726/commissioner-brett-yormark-leaving-big-12-january)).
- **Stakeholder input:** the NCAA interviewed more than 300 stakeholders before recruiting
  ([NCAA](https://www.ncaa.org/news/2022/12/15/media-center-ncaa-announces-governor-charlie-baker-to-be-next-president.aspx)).
  Front-runners can fall away late. Clemson's Jim Clements was the presumptive ACC choice until his
  board kept him ([CBS](https://www.cbssports.com/college-football/news/acc-hires-northwestern-ad-jim-phillips-as-commissioner-replacing-the-retiring-john-swofford)).
- **The non-traditional wave:** the run of outsider hires was Warren (NFL, 2019), Kliavkoff (MGM,
  2021), Yormark (Roc Nation, 2022), Petitti (MLB, 2023) and Brosnan (MLB, Big East, 2026). Two
  counter-signals: after Kliavkoff failed, the Pac-12 promoted its deputy Teresa Gould, and Big 12
  chair Doug Girod has said he does not want a "Yormark twin" and does want "campus experience".

## How commissioners are evaluated and extended

- Boards extend commissioners after big wins or to keep them through the next media cycle:
  - Petitti got 5 more years, through June 2033. The Big Ten's TV deal ends in 2030.
  - Gould got 5 years, through 2030-31, timed to the Pac-12's grant of rights and media deal.
  - Yormark got 3 years, through 2030, "first crack at the next TV deal".
- Boards also extend commissioners to block poaching. Phillips got 3 years in April 2023 while he was
  a Big Ten target ([CBS](https://www.cbssports.com/college-football/news/acc-commissioner-jim-phillips-to-sign-three-year-extension-after-being-a-target-to-lead-big-ten)).
- Contract terms are almost never disclosed. Pay surfaces 18-24 months later in the Form 990.
- No commissioner contract in public reporting includes bonus clauses, but the bonuses show up in the
  filings:
  - Kevin Warren: a **$5.75M media-rights bonus**
    ([Sportico](https://www.sportico.com/leagues/college-sports/2025/big-ten-kevin-warren-bonus-jim-delany-1234851527/)).
  - Petitti: $500K in 2023.
  - Kliavkoff: $500K in 2022.

## How commissioners are ousted

- **Dan Beebe, Big 12 (2011):** forced out by the board after Nebraska, Colorado and Texas A&M left.
  Chuck Neinas served as interim, and Bowlsby was hired in 2012. (low confidence: background knowledge)
- **John Marinatto, Big East (2012):** resigned under pressure after the ACC and Big 12 raids.
  (low confidence)
- **Larry Scott, Pac-12 (2021):** "mutual" exit announced in January 2021, a year early, with
  roughly $1.5M severance
  ([On3](https://www.on3.com/news/former-pac-12-commissioner-larry-scott-reportedly-received-1-5-million-severance-package)).
  The criticism centered on Pac-12 Network distribution and spending.
- **George Kliavkoff, Pac-12 (2024):**
  - The board was then only the presidents of Oregon State and Washington State.
  - The "mutual" separation and contract settlement were announced in mid-February 2024. His last day
    was Feb. 29.
  - The board named deputy commissioner Teresa Gould on Feb. 19, effective March 1, on a two-year
    deal.
  - Terms were undisclosed at the time. The 990 later showed **$6.1M paid in 2024, $5M of it
    severance**, and $15.6M over his whole tenure. In effect this was a negotiated buyout of about
    2.3 remaining years on his five-year deal
    ([Spokesman](https://www.spokesman.com/stories/2024/feb/13/after-the-fall-pac-12-officially-moving-on-from-co/),
    [Spokesman](https://www.spokesman.com/stories/2024/feb/19/pac-12-names-teresa-gould-commissioner-as-washingt),
    [B/R](https://bleacherreport.com/articles/10109296-report-pac-12-commissioner-george-kliavkoff-part-ways-agree-to-contract-settlement)).
  - Root cause: in August 2023 he pitched an Apple streaming deal, and eight schools left within days.
- **The pattern:** fired commissioners almost always leave as "mutual" or "resigned". A formal firing
  vote is rare, and the severance is negotiated.

## Pay trend

| Person | Conference | Year / basis | Total pay | Source |
|---|---|---|---|---|
| Yormark | Big 12 | FY2024-25 (calendar 2024) | $5.6M | [USA Today via Rumsey](https://x.com/_DavidRumsey/status/2060387719964987535) |
| Sankey | SEC | calendar 2024 | $4.83M ($4.7M base) | |
| Phillips | ACC | calendar 2024 | $4.7M | |
| Petitti | Big Ten | calendar 2024 | $4.5M | |
| Phillips | ACC | 2022 | $2.8M | |
| Gould | Pac-12 | 2024 | $1.5M | |
| Nevarez | MWC | calendar 2023 | $1.16M | |
| Southland and America East commissioners | | | $0.3-0.4M | |
| Baker | NCAA | first year | about $3.4M (low confidence) | |

- P4 pay rose roughly 70% from 2022 to 2024.
- The biggest single-year payouts are exit packages:
  - Bowlsby: $17.2M, including $12.26M for the three years left on his contract
    ([ESPN](https://africa.espn.com/college-sports/story/_/id/40205947/big-12-paid-ex-commissioner-bob-bowlsby-172m-final-year)).
  - Delany: $5.82M in bonuses and deferred pay, plus $600K in consulting, still being paid in
    FY2024-25.

## Changes in 2025-26, verified

| Conference | Change | Dates |
|---|---|---|
| **Big 12** | Yormark leaves to be CEO of Milan Sports & Entertainment (RedBird) | Announced 2026-10-30, effective 2027-01-31; search under way |
| **Big East** | Ackerman retired; Tim Brosnan succeeded her | Announced 2026-04-20; Brosnan named about 2026-08-10, started 2026-09-01 |
| **A-10** | McGlade retired; Dan Leibovitz succeeded her | Leibovitz named 2026-03-18, started 2026-05-04 |
| **NEC** | Noreen Morris stepped down; Ron Ratner is interim | Effective 2026-09-01 |
| **Pac-12** | Gould extended through 2030-31 | June 2026 |
| **Big Ten** | Petitti extended through June 2033 | 2026-08-26 |
| **MWC** | Nevarez extended through 2030-12-31 | December 2025 |
| **Big 12** | Yormark extended through 2030 (since superseded by his exit) | May 2025 |

No change was found for the SEC, ACC, C-USA (MacLeod), Sun Belt (Gill), MAC (Steinbrecher), AAC
(Pernetti) or WCC (Stu Jackson). This rests on searches that came up empty, so it is not exhaustive.

## Corrections to the brief

1. **The Big 12 commissioner seat is effectively open.** Yormark resigned on Oct. 30, 2026, effective
   Jan. 31, 2027, to become CEO of a RedBird-backed holding company in Milan. The board is searching
   now. Seed this as a live storyline at game start.
2. **Val Ackerman is no longer Big East commissioner.** She retired on Aug. 31, 2026. **Tim
   Brosnan**, an ex-MLB executive, took over on Sept. 1, 2026.
3. **The A-10 commissioner is Dan Leibovitz**, since May 4, 2026. Bernadette McGlade retired.
4. **The American hired Tim Pernetti in 2024, not 2023.** Aresco's retirement was announced in
   December 2023. Pernetti was selected on April 2, 2024 and started June 3, 2024.
5. **Petitti's extension through June 2033 is confirmed.** It is five years, announced Aug. 26,
   2026, with a unanimous vote of the Council of Presidents and Chancellors.
6. **Sankey's contract runs through at least 2028.** It was extended in July 2023, after an August
   2021 extension through 2026. No newer extension was found.
7. **Phillips' contract runs "into 2029".** This comes from a three-year extension in April 2023.
   There was no 2025-26 extension.
8. **Yormark's May 2025 extension through 2030 is now moot.**
9. **Pat Forde is at Sports Illustrated, not Yahoo.** He moved in 2020.
10. **John Ourand is at Puck, not SBJ.** He moved in 2024.
11. **Nicole Auerbach is believed to be at NBC Sports, not The Athletic.** Low confidence.
12. **Brett McMurphy is kept at Action Network.** A move to On3 was not confirmed.
13. **Pay estimates:** "Phillips ~$4M?" is close; the reported figure is $4.7M for calendar 2024.
    "Sankey ~$3M+" is too low; he made $4.8M. The highest-paid active P4 commissioner was Yormark.
14. **Kliavkoff did leave with a buyout,** structured as a negotiated settlement worth $5M in
    severance. The board vote that installed Gould was announced on Feb. 19, 2024.

## Game-model implications

- **Hot-seat triggers.** Each has a suggested weight in the probability that the board opens a review.

  | Trigger | Weight |
  |---|---|
  | A member school announces it is leaving | +25 each; +40 for a flagship |
  | Media-rights renewal comes in more than 15% below peer conferences per school | +30 (the Kliavkoff and Scott pattern) |
  | Public revolt by members, e.g. litigation over the grant of rights | +20 (the FSU/Clemson pressure on the ACC) |
  | Scandal or integrity event | +15 to +35 |
  | Two consecutive years of falling distributions | +15 |

- **Review cadence.** The board reviews the commissioner every year after the fiscal year closes,
  around July or August.
  - Score the review on: revenue growth versus peers (40%), stability of membership (25%), relations
    with presidents (15%), CFP and NCAA policy wins (10%) and public image (10%).
  - Outcomes by score band:

    | Score | Outcome |
    |---|---|
    | 70 or above | Extension of 3-5 years, offered at one to three years into the term |
    | 40-70 | Status quo |
    | Below 40 | Hot seat |
    | Below 25 for two straight reviews | "Mutual" separation |

- **Extension AI.** When a media deal is within 3 years of expiring, the board strongly prefers to
  extend an incumbent with a good record past the expiry, as with Petitti and Gould. When an outside
  offer lands, the board makes a retention extension 60% of the time if the score is 60 or higher,
  as with Phillips in 2023.
- **Buyout norms.** Use a severance of 50-100% of remaining base salary, typically paid as a lump
  sum. Kliavkoff got about $5M on roughly $3.7M a year with about 2.3 years left, which is near
  60%. Bowlsby's retirement payout covered 100% of his three remaining years. Firing "for cause" is
  rare, so the default should be a negotiated buyout.
- **Poaching.** Commissioners from pro leagues and media have a 10-15% yearly chance of getting a
  significant outside offer once they are past year 3. Warren left after about 3.3 years and
  Yormark after about 4.5. A conference's own deputies and former ADs have a 3% chance, mostly of
  lateral moves such as WCC to MWC or WAC to Sun Belt.
- **Search events.**
  - A search lasts 3-5 months.
  - Firm options: TurnkeyZRG (expensive, broad slate with lots of outsiders), Parker (G6 and
    mid-major), or in-house (fast, insider slate).
  - Board preference swings after a failure. After an outsider fails, insider candidates get +30%
    weight. After a long-serving insider retires, outsider candidates get +20%.
  - The search can lose its front-runner late (the Clements case) with a 15% chance.
- **Pay bands for new hires.** Set base pay by tier, then add a premium for outsiders:

  | Tier | Base pay | Outsider premium |
  |---|---|---|
  | P4 | $3.5-5.5M | +10-20% |
  | Rebuilt Pac-12 | $1.2-1.8M | |
  | G6 | $0.7-1.3M | |
  | Big East, WCC, A-10 | $0.5-1.5M | |
  | FCS and low-major | $0.25-0.45M | |

  Add an optional media-deal bonus of 1-1.5 times base, following the Warren model.
- **Media-outlet credibility.**
  - Use the 1-10 `credibility` value as the probability that a rumor proves true, with diminishing
    returns.
  - Tier-1 insiders such as Thamel, Dellenger and Sportico should be right about 85-90% of the time.
  - McMurphy and Canzano are bold but sometimes early, at about 70%.
  - Aggregators and message boards should be right 20-30% of the time.
  - Rights-holder outlets such as ESPN and FOX get a small spin bias toward their partner leagues.
