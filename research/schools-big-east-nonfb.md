# Schools: Big East + key non-FBS basketball brands

As of 2026-11-25. Owner: schools-nonfb agent.

**Files**
- `data/schools/big-east.json`: 11 records (all Big East members, UConn included). Schema: `School` (SCHEMA.md).
- `data/schools/other-d1.json`: 12 records (see "Group B selection").

**Extra fields beyond the School schema** (the engine can ignore them):
- `lowConfidenceFields`: an array of dotted field paths that are best estimates.
- `note`: a record-level verification caveat.
- `athletics.note` / `athletics.arena.secondary`: a second home arena (MSG, Xfinity Mobile Arena, XL Center, Climate Pledge).
- `confidence` + `note` inside person objects (`president`, `ad`, `head*Coach`) when the Nov 2026 status is unverified.

## Verification status (read first)

The web-search budget for this turn, which all agents share, ran out after about 14 searches. `en.wikipedia.org` and `www.bigeast.com` also do not resolve from this session, so WebFetch failed. They would need to be added to the session's network allowlist.

What that means for the data:
- The facts below marked **verified** came from 2026 sources.
- Everything else comes from knowledge that runs to about mid-2026 and is flagged in `lowConfidenceFields`.
- These fields are approximate for every school: enrollment, endowment, US News rank, Nielsen DMA rank and athletics revenue/expenses. The money figures are order-of-magnitude EADA/Knight-Newhouse-style estimates, not filed numbers. The money-postseason or nonfbs agents should overwrite them if they pull EADA.

### Verified 2026 facts
- **Val Ackerman retired.** She announced in April 2026 and her last day was Aug 31, 2026 ([Big East](https://www.bigeast.com/news/2026/4/20/general-big-east-commissioner-val-ackerman-announces-retirement.aspx)).
- **Tim Brosnan is the 6th Big East commissioner.** He was announced Aug 10, 2026 and started Sept 1, 2026. He is a former MLB COO who helped launch MLB Network and the World Baseball Classic, a Georgetown alumnus and a Fordham Law graduate ([NBC Sports](https://www.nbcsports.com/big-east/news/tim-brosnan-named-sixth-big-east-commissioner-will-succeed-val-ackerman-in-september), [Georgetown](https://www.georgetown.edu/news/tim-brosnan-big-east-commissioner/), [ESPN](https://africa.espn.com/college-sports/story/_/id/49507446/source-former-mlb-executive-tim-brosnan-head-big-east), [UConn](https://uconnhuskies.com/news/2026/8/10/general-big-east-names-tim-brosnan-as-commissioner)).
- **The Big East still has 11 full members** as of its Sept 2026 history page ([Big East history](https://www.bigeast.com/sports/2026/9/10/BE_history_090926.aspx)).
- **Senators lobbied for SLU and Dayton.** On Jan 14, 2026, U.S. Sens. Eric Schmitt (R-MO) and Jon Husted (R-OH) wrote to Ackerman urging the Big East to add Saint Louis and Dayton. The letter cites SLU's $20M, 25,000 sq ft basketball facility (2024) and both schools' basketball-first fit ([letter PDF](https://www.schmitt.senate.gov/wp-content/uploads/2026/01/1.13-Signed-Big-East-Letter.pdf), [Schmitt release](https://www.schmitt.senate.gov/media/press-releases/senators-schmitt-husted-call-for-big-east-conference-membership-for-saint-louis-university-university-of-dayton/), [Husted release](https://www.husted.senate.gov/media/press-releases/husted-urges-big-east-to-consider-university-of-dayton-for-membership)).
  - Dayton President Eric Spina and AD Neil Sullivan replied with thanks but made no commitment ([WHIO](https://www.whio.com/news/local/ud-leaders-respond-sen-husteds-request-that-big-east-conference-consider-adding-new-member/HA7P2NNZD5F35OPRAES2O2CMLA/)).
  - No Big East response or expansion vote was found.
- **UConn football is still an FBS independent in 2026.** Jason Candle (formerly Toledo) is in his first season. Jim Mora left after 2025 to become head coach at Colorado State ([UConn coaches](https://uconnhuskies.com/sports/football/coaches), [UConn 2026 roster](https://uconnhuskies.com/sports/football/roster/2026)).
- **2026 men's title game:** No. 1 Michigan beat No. 2 UConn 69-63 on Apr 6, 2026 in Indianapolis. It was Alex Karaban's final game. UConn had won 19 straight NCAA games past the second round ([UConn](https://uconnhuskies.com/news/2026/4/6/mens-basketball-huskies-fall-in-national-title-game), [CBS](https://www.cbsnews.com/news/ncaa-mens-basketball-championship-michigan-uconn-2026-march-madness/)).
- **2026 women's tournament:** Undefeated UConn lost 62-48 to South Carolina in the national semifinal on Apr 3, 2026, which ended a 54-game win streak. UCLA beat South Carolina 79-51 for the title ([UConn](https://uconnhuskies.com/news/2026/4/3/womens-basketball-huskies-fall-to-south-carolina-at-final-four), [UCLA](https://uclabruins.com/news/2026/4/5/womens-basketball-captures-2026-ncaa-title)).
- **Butler's president:** James Danko's contract was extended through at least Aug 2026, with one-year renewal options. No successor announcement was found ([Indy Chamber](https://indychamber.com/2023/04/26/butler-university-trustees-extend-president-james-dankos-contract-for-three-years/)).

## 2026-27 membership lists

**Big East (11 full members, unchanged since UConn returned in 2020):** Butler, Creighton, DePaul, Georgetown, Marquette, Providence, St. John's, Seton Hall, UConn, Villanova, Xavier.
- None of them plays football in the Big East.
- Football homes:
  - UConn: FBS independent.
  - Georgetown: Patriot League (FCS).
  - Villanova: CAA Football (FCS).
  - Butler: Pioneer League (FCS, non-scholarship).
- Commissioner: Tim Brosnan (since Sept 1, 2026).

**WCC 2026-27 (9 full members):** Loyola Marymount, Pacific, Pepperdine, Portland, Saint Mary's, San Diego, San Francisco, Santa Clara, Seattle U.
- **Gonzaga** left for the Pac-12 on July 1, 2026, as a non-football member.
- **Oregon State and Washington State** ended their 2024-26 WCC affiliate memberships and returned to the Pac-12 as full members.
- **Seattle U** joined from the WAC on July 1, 2025.
- **Saint Mary's** stays. No Pac-12 or MW invitation was found.
- Any further WCC additions for 2026-27 (for example, speculation about Denver) are **unverified**. The nonfbs-conferences agent should confirm.

**A-10 2026-27 (14):** Davidson, Dayton, Duquesne, Fordham, George Mason, George Washington, La Salle, Loyola Chicago, Rhode Island, Richmond, St. Bonaventure, Saint Joseph's, Saint Louis, VCU. UMass left for the MAC in 2025. *(Moderate confidence.)*

**MVC 2026-27 (11):** Belmont, Bradley, Drake, Evansville, Illinois State, Indiana State, Murray State, Northern Iowa, Southern Illinois, UIC, Valparaiso. Missouri State left for CUSA in 2025. *(Moderate confidence.)*

## Group B selection (12 schools) and why

| School | Why it's included |
|---|---|
| Dayton, Saint Louis | Named in the Jan 2026 senators' letter; the consensus top Big East expansion candidates. |
| VCU, Loyola Chicago | Recurring Big East and AAC expansion names. VCU's public status is the main objection; Loyola would double up on Chicago. |
| George Mason | Washington DMA public school. Model for federal/state politics events (2025 DEI findings against its president). |
| Saint Joseph's | Philadelphia Jesuit school, part of the A-10's core. Low-probability Big East candidate. |
| Saint Mary's, San Francisco, Santa Clara | The WCC core after Gonzaga. Saint Mary's is the realignment wildcard. |
| Seattle U | 2025 WCC entrant (Seattle DMA). |
| Drake, Bradley | MVC anchors after the league lost Loyola (2022) and Missouri State (2025). Drake keeps losing coaches to P4 schools. |

Excluded per the brief: Gonzaga, Wichita State and Grand Canyon (other agents).

## Leadership changes (2025-26 vs. older baselines)

- **Big East commissioner:** Ackerman to Brosnan (verified).
- **UConn football:** Mora to Jason Candle (verified).
- **2025 men's basketball hires, still in place as of mid-2026:**
  - Villanova: Kevin Willard (Neptune fired).
  - Xavier: Richard Pitino (Sean Miller left for Texas).
  - VCU: Phil Martelli Jr. (Ryan Odom left for Virginia).
  - Drake: Eric Henderson (Ben McCollum left for Iowa).
  - Saint Joseph's: Steve Donahue (Billy Lange left for the Knicks staff).
- **Marquette president:** Kimo Ah Yun succeeded Michael Lovell, who stepped away for illness in 2024.
- **Not verifiable for Nov 2026, all flagged low:**
  - Butler: president (Danko).
  - Georgetown: president (Groves).
  - Villanova: president (Donohue).
  - Saint Louis: president (Pestello).
  - VCU: president (Rao).
  - George Mason: president (Washington).
  - Hot-seat men's basketball coaches: Kim English (Providence), Ed Cooley (Georgetown), Thad Matta (Butler), Shaheen Holloway (Seton Hall), Shaka Smart (Marquette).
  - Rising coaches who could have moved after 2025-26: Tony Skinn (GMU) and Josh Schertz (SLU).
  - Most athletic directors outside UConn, DePaul, Georgetown, Providence, Xavier and Dayton.

## Storylines

- **Catholic 7 history.** On Dec 15, 2012, Georgetown, Villanova, St. John's, Seton Hall, Providence, Marquette and DePaul split from the football schools. They kept the Big East name and the MSG tournament, and added Butler, Creighton and Xavier in 2013. The old football Big East's charter became the American (`big-east-2010` lineage). UConn returned in 2020 after paying the AAC about $17M.
- **Media.** FOX has been the anchor partner since 2013. The 2023 extension runs through 2030-31 and added more partners (NBC/Peacock and reportedly TNT). *(Low confidence; the media-rights agent should confirm in `media_deals.json`.)*
- **The MSG Big East tournament** is the league's crown jewel and anchors St. John's and the New York brand.
- **UConn's P4 ambitions.**
  - The Big 12 studied UConn in 2023-24, but its presidents declined to expand.
  - The Big Ten and ACC are not interested unless the ACC breaks up.
  - Football independence costs UConn conference media money and bowl tie-ins, makes scheduling hard and deepens the department's subsidy (about $30-40M a year).
  - Gov. Ned Lamont and lawmakers champion a P4 move. The state owns Rentschler Field and the XL Center through the CRDA.
  - Jim Mora's move to Colorado State shows UConn's coaching vulnerability.
  - UConn is the Big East's main existential risk: losing it would drop the league's top TV draw.
- **Georgetown's decline.** Its last NCAA bid was 2021. Patrick Ewing was fired in 2023, and Ed Cooley's rebuild from 2023 is unresolved. The new commissioner being a Georgetown alumnus is an internal-politics hook.
- **St. John's spending.** Pitino plus Mike Repole made St. John's the league's NIL and revenue-sharing spending leader. It won the 2025 Big East regular season and tournament.
- **WCC after Gonzaga.** The WCC loses its NCAA-unit engine and TV draw. Saint Mary's becomes the flagship, and the league backfills with lower-revenue schools like Seattle U.
- **A-10 instability.** The league lost UMass (2025) after earlier losses of Butler, Xavier and Temple (2012-13). Its best brands (Dayton, VCU, SLU) are openly courted, and members are now lobbying through U.S. senators.

## Corrections to the brief

1. **Commissioner.** Val Ackerman is no longer Big East commissioner. Tim Brosnan (ex-MLB, `pro-league-exec` background) took over on Sept 1, 2026.
2. **UConn football coach.** It is Jason Candle (2026), not Jim Mora.
3. **2026 titles.** UConn men were 2026 national runner-up (they won in 2023 and 2024, not 2025). UConn women won in 2025 but lost the 2026 national semifinal; UCLA won the 2026 women's title.
4. **Saint Mary's.** No evidence it is leaving the WCC; only Gonzaga left for the Pac-12. OSU and WSU's WCC affiliation ended in 2026.
5. **Seattle U conference ID.** Its 2010 home was "D-I independent (non-football)". The data uses `independent` with a `note`, but in SCHEMA `independent` means FBS independents. **Suggestion:** add a `di-independent` historical ID.
6. **UConn's DMA** is Hartford & New Haven (about #32), not New York. Its NYC and Boston reach shows up in `brand`, not `dma`.
7. **AAU.** No school in either file is an AAU member (UConn included).
8. **US News categories.** Butler, Xavier, Providence, Drake, Bradley and Saint Joseph's are Regional Universities, so `usNewsRank` is null per the schema. Butler, Providence and Xavier have long been #1 or top-10 in their regions.
9. **Senators' letter.** Federal lawmakers (Sens. Schmitt and Husted, Jan 2026) lobbied a private conference directly. The brief has no mechanic for federal-level political pressure on non-FBS leagues.

## Game-model implications

- **Big East expansion scoring (suggested weights):**

  | Factor | Weight |
  |---|---|
  | Catholic/private fit | 0.25 |
  | MBB rating | 0.25 |
  | New DMA | 0.20 |
  | Fan base/attendance | 0.15 |
  | Dilution penalty (per-school media share must not fall) | 0.15 |

  Rough candidate attractiveness: SLU 0.62, Dayton 0.60, VCU 0.35 (public penalty), Loyola Chicago 0.30, Gonzaga about 0.25 (travel; other agents), Saint Joseph's 0.12. The vote threshold is unverified (assume a supermajority). With 11 members and no football, expansion happens mainly as a *response* to losing UConn or a media-partner incentive.
- **UConn departure event:**
  - Base annual P4 invite probability: 5%.
  - Raise it to 20-35% if an ACC breakup, a Big 12 media reset, or a P4 need for basketball inventory occurs.
  - UConn accepts at about 95%.
  - The Big East responds with a replacement shortlist of Dayton, SLU, then VCU.
  - Football independence costs UConn a tunable `independentFbsDragUsd` (about $10-15M a year in subsidy pressure).
  - Connecticut `statePoliticalPressure` 82: legislature or governor events can fund football (stadium/XL Center bonds) or pressure the university to cut losses.
- **Senators' letter as an event seed.** It is low-compliance pressure on a private league: add +5 to +10 "political attention" to the targeted schools' candidacy and a small reputational cost to the commissioner for ignoring it. A newly hired commissioner (Brosnan) gets a honeymoon modifier, for example 1 season of +10 member-trust.
- **Booster arms race.** St. John's `boosterInfluence` 85 (Repole) should drive intra-league NIL escalation events. For schools sharing a DMA with St. John's (Seton Hall), roster retention rolls are -X when the rival outspends them.
- **Coach poaching.** Recent mid-major and Big East losses (Drake twice, VCU, Xavier and the Saint Joseph's coach leaving for the NBA) suggest a 20-30% annual poach chance for any coach with 2+ straight NCAA bids at a non-P4 school.
- **WCC post-Gonzaga revenue shock.** Cut the WCC's NCAA-unit and media value by about 40-60% from 2026-27. Raise the chance that Saint Mary's or Santa Clara is courted by the Pac-12/MW as non-football members (event-driven, no invite yet).

## Shared sources
- Big East: [history](https://www.bigeast.com/sports/2026/9/10/BE_history_090926.aspx), [Ackerman retirement](https://www.bigeast.com/news/2026/4/20/general-big-east-commissioner-val-ackerman-announces-retirement.aspx)
- Expansion commentary (older, speculative): [The Hoya](https://thehoya.com/23109938/sports/ramblers-flyers-zags-unpacking-potential-big-east-expansion/)
- EADA: [ope.ed.gov/athletics](https://ope.ed.gov/athletics/). Knight-Newhouse: [knightnewhousedata.org](https://knightnewhousedata.org/)
- Conferences: [WCC](https://wccsports.com/), [A-10](https://atlantic10.com/), [MVC](https://mvc-sports.com/)
