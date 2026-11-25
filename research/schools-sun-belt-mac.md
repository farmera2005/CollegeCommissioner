# Schools: Sun Belt & MAC (as of 2026-11-25)

Files: `data/schools/sun-belt.json` (14 records), `data/schools/mac.json` (13 records: 12 full members + Sac State football-only).

**Shape:** standard `School` schema (SCHEMA.md). Additions:
- `confidence: "low"` at record level, with `note` and `lowConfidenceFields` (an array of dotted paths).
- A nested `confidence`/`note` on any `president` / `ad` / `headFootballCoach` / `headMbbCoach` object that could not be verified.
- A coach object with `name: null` means a vacancy or successor we could not verify.

**Research limitation (important):** the shared web-search budget ran out early in this task (after about 12 searches), and WebFetch could not reach outside hosts. As a result:
- **Verified by search:** membership, realignment moves, revenue-sharing opt-in status, and the Sac State, JMU and Louisiana Tech storylines.
- **From model knowledge (through about mid-2026), flagged low:** leadership, ratings and most numbers. DMA ranks, US News ranks, endowments and athletic revenue/expenses are estimates (about FY2024 Knight-Newhouse levels), and every record lists them in `lowConfidenceFields`.
- **Re-verify first:** the 2025-26 coaching carousel.

## Verified 2026-27 membership

**Sun Belt (14, all-sports + football):**
- East: App State, Coastal Carolina, Georgia Southern, Georgia State, James Madison, Marshall, Old Dominion.
- West: Arkansas State, Louisiana, ULM, South Alabama, Southern Miss, Troy, **Louisiana Tech** (new 2026-07-01).
- Texas State left for the Pac-12 after 2025-26, paying a $5M buyout ([ESPN](https://www.espn.com/college-sports/story/_/id/45618806)).
- SBC CEOs invited Louisiana Tech, which accepted to stay at 14. It was an SBC member 1991-2001, then WAC 2001-13 and C-USA 2013-26 ([CBS](https://www.cbssports.com/college-football/news/louisiana-tech-accepts-invitation-to-sun-belt-replacing-texas-state-after-departure-to-pac-12), [The Advocate](https://www.theadvocate.com/acadiana/sports/ul_lafayette/louisiana-tech-moving-back-to-the-sun-belt-to-replace-texas-state-keep-conference-at/article_b17dbdf8-4425-4c69-bdff-018f409a4a35.html), [On3](https://www.on3.com/sites/bleed-tech-blue/news/louisiana-tech-replaces-texas-state-in-sun-belt-likely-to-play-similar-2026-slate/)).
- **Pending:** JMU leaves for the American on **2027-07-01** (see below), which drops the SBC to 13 for 2027-28. No SBC replacement had been announced as of 2026-11-25.

**MAC (12 full members + 1 football-only = 13 football teams):**
- Full members: Akron, Ball State, Bowling Green, Buffalo, Central Michigan, Eastern Michigan, Kent State, Massachusetts, Miami (OH), Ohio, Toledo, Western Michigan.
- Football-only: **Sacramento State**, on a 5-year term from 2026-07-01 ([MAC release](https://getsomemaction.com/news/2026/2/16/sacramento-state-joins-mid-american-conference-as-football-only-member.aspx), [ESPN](https://www.espn.com/college-football/story/_/id/47933760/mac-add-sacramento-state-football-only-member), [Sac State](https://hornetsports.com/news/2026/2/16/hornet-football-to-join-the-mac-in-2026.aspx)).
- Sac State fees: $18M MAC entry fee plus a $5M NCAA FBS fee.
- Sac State restrictions: ineligible for the MAC title and the postseason for its first two seasons ([Hustle Belt](https://www.hustlebelt.com/mac-football/44610/sacramento-state-to-join-mid-american-conference-as-football-only-member)).
- Sac State's other sports went to the **Big West** on 2026-07-01 ([Big West](https://bigwest.org/news/2025/6/18/sacramento-state-joins-the-big-west.aspx), [ESPN](https://www.espn.com/college-sports/story/_/id/45539731/sacramento-state-join-big-west-all-sports-football)).
- Sac State women's rowing becomes a MAC affiliate starting with the 2027 season ([Sac State](https://hornetsports.com/news/2026/9/23/womens-rowing-rowing-to-join-the-mid-american-conference-for-the-upcoming-2027-season.aspx)).
- **NIU departed** after 2025-26: football to the Mountain West, other sports to the **Horizon League** ([Wikipedia realignment summary](https://en.wikipedia.org/wiki/2021%E2%80%932026_NCAA_conference_realignment), [Eleven Warriors](https://www.elevenwarriors.com/college-football/2026/02/161577/sacramento-state-joins-mac-as-football-only-member)).
- UMass has been a full MAC member since 2025-07-01.
- No MAC full-member addition had been announced for 2027.
- The MAC's ESPN rights deal expires after 2026-27 ([S&P Global](https://www.spglobal.com/market-intelligence/en/news-insights/research/2026/09/college-football-returns-with-secure-media-deals-and-new-eras-for-pac-12-mwc)).

## Corrections to the brief
1. **JMU is leaving the Sun Belt.**
   - 2026-10-12: the Board of Visitors voted unanimously to terminate membership and apply to the American; AAC presidents voted unanimously to admit ([ESPN](https://www.espn.com/college-sports/story/_/id/50166450/james-madison-exit-sun-belt-join-american-conference), [FootballScoop](https://www.footballscoop.com/2026/10/12/james-madison-leaving-sun-belt-to-join-american), [On3](https://www.on3.com/news/james-madison-votes-to-terminate-sun-belt-membership-apply-for-american-conference/)).
   - 2026-11-19: an SBC–JMU agreement moved the exit up from 2028 to **2027-07-01**. JMU stays eligible for all SBC titles in 2026-27 ([JMU](https://jmusports.com/news/2026/11/19/administration-sun-belt-conference-james-madison-reach-agreement-on-july-1-2027-departure), [SBC](https://sunbeltsports.org/news/2026/11/19/general-sun-belt-conference-james-madison-reach-agreement-on-july-1-2027-departure.aspx), [ESPN](https://www.espn.com/college-football/story/_/id/50534149/james-madison-moving-american-conference-2027), [CBS](https://www.cbssports.com/college-football/news/james-madison-sun-belt-exit-2027-american-conference-realignment/)).
   - Costs as reported: about a $5M SBC exit fee (some reports say up to $10M) and about $23M AAC entry.
   - 17 of 18 sports move to the AAC; field hockey stays a MAC affiliate.
   - The AAC goes to 15 football members.
   - SCHEMA's 2026-27 lists stay correct, but realignment and conference files need this pending change.
2. **Sac State is football-only in the MAC, not a full member.** Its `y2026` is `{all: "big-west", football: "mac", level: "FBS"}`.
3. **NIU** split its destinations: football to the Mountain West, other sports to the Horizon League. It is not an all-sports Mountain West member.
4. **2010 alignments, with nuance:**
   - Georgia State: football debuted in 2010 as an FCS independent (CAA football from 2012); all other sports were CAA. Stored as `{all:"caa", football:"independent", level:"FCS"}`.
   - Old Dominion: football restarted in 2009 as an FCS independent (CAA football 2011-13); same encoding.
   - South Alabama: a non-football SBC member in 2010, with football on an independent transitional schedule (SBC football from 2012). Stored as `{all:"sun-belt", football:"independent", level:"FCS"}`.
   - UMass: all sports in the A-10, football in the CAA (FCS).
   - Sac State: Big Sky.
   - Marshall and Southern Miss: `cusa-2010`. Louisiana Tech: `wac-2010`.
   - Coastal Carolina: Big South. App State and Georgia Southern: SoCon. JMU: CAA.
   - Note: `independent` plus `level: "FCS"` is used for FCS independents because the schema has no FCS-independent ID.
5. **Sun Belt exit fees:** one low-quality aggregator reports the SBC moved from a flat $5M to an $8M–$18M sliding scale based on notice. This is **unverified**; the conferences agent should confirm.
6. **UC Davis**: reported moving to the Mountain West in 2026 (Sac State's Big West entry was framed as replacing it). It is not in the SCHEMA's Mountain West list; flag for schools-west / nonfbs agents. (low confidence)

## Notable storylines (for event generation)
- **SBC stability vs. predation.**
  - Commissioner Keith Gill kept the league at 14 by adding Louisiana Tech, then lost JMU, the league's richest department, to the AAC.
  - After 2027 the likely next targets are App State, Marshall and Old Dominion (brand, stadiums, and ODU's Virginia/Hampton Roads market) and Georgia Southern.
  - A possible SBC response is to raise exit fees, add a C-USA or FCS school, or go to 13.
- **Virginia politics.**
  - JMU's and ODU's FBS moves needed approval from the legislator-led Intercollegiate Athletics Review Commission.
  - Student fees fund much of both budgets (JMU about $55M), and those fees cannot fund revenue-share pay. A 2026 Deeds proposal would loosen fee limits ([Cardinal News](https://cardinalnews.org/2026/02/10/deeds-proposal-would-allow-some-of-virginias-top-football-colleges-to-raise-more-money-from-student-fees/)).
  - Cardinal News calls JMU an SBC "financial heavyweight" that will remain well funded in the AAC ([Cardinal News](https://cardinalnews.org/2026/10/21/jmu-was-a-financial-heavyweight-in-the-sun-belt-it-will-still-be-one-of-the-best-funded-in-the-american-conference-thanks-to-student-fees/)).
- **Louisiana bloc.** Louisiana, ULM and Louisiana Tech are all University of Louisiana System schools governed under the Board of Regents, which gives the SBC West three schools exposed to Louisiana budget politics.
- **Revenue sharing.**
  - The SBC, MAC and C-USA all had 100% opt-in for 2025-26 ([Sportico](https://www.sportico.com/leagues/college-sports/2025/division-i-revenue-sharing-schools-list-college-sports-1234863224/)).
  - Actual G6 payouts are a small fraction of the $20.5M cap, about $2.4M for an average SBC school by one third-party estimate ([nil-ncaa.com](https://nil-ncaa.com/sb/)).
  - JMU said it wanted to lead the SBC ([DNR](https://www.dnronline.com/sports/level/college/james_madison_university/jmu-wants-to-lead-sun-belt-in-revenue-sharing-with-athletes/article_f88a2ebd-e486-5bc3-8a18-11515f62ba14.html)).
  - Hustle Belt says reaching the cap isn't feasible for MAC schools that already run deficits ([Hustle Belt](https://www.hustlebelt.com/2025/6/11/24447187/the-house-v-ncaa-settlement-from-a-mac-point-of-view-mid-american-conference-2025-revenue-sharing)).
  - 2025-26 total across D-I: $1.77B ([ESPN](https://www.espn.com/college-sports/story/_/id/50080194/student-athletes-received-177b-revenue-sharing-pay-25-26)).
- **MAC financial strain.**
  - Heavy subsidies (EMU, Akron, Kent State, Buffalo) keep the "drop to FCS" debate alive.
  - Buffalo cut 4 sports in 2020 and EMU cut 4 in 2018 (followed by a Title IX suit).
  - Ohio's SB 1 and state budget, the Indiana budget law, and Michigan enrollment declines (CMU) all weigh on the league.
  - The MAC's ESPN deal expires after 2026-27, so a new media-rights negotiation is a near-term event.
- **MAC footprint.** UMass (full member since 2025) stretches the league to New England, and Sac State (football 2026, rowing 2027) stretches it to California. NIU's exit costs the Chicago market.
- **Sac State's FBS push.**
  - Led by President Luke Wood with donor backing, Shaquille O'Neal's involvement and Sacramento civic/political support.
  - The Pac-12 passed in 2025 ([SI](https://www.si.com/college/boise-state/football/sac12-sacked-sacramento-state-join-big-west-non-football-sports)), and the NCAA Football Oversight Committee recommended against its waiver.
  - The MAC deal is a 5-year bridge. Watch for a Pac-12/Mountain West upgrade, stadium financing, and CSU budget cuts.
- **Coaching carousel 2025-26 (reported, mostly unverified here):**
  - Bob Chesney: JMU to UCLA.
  - Charles Huff: Southern Miss to Memphis.
  - Jason Candle: Toledo to UConn.
  - Coastal Carolina changed coaches (Ryan Beard?).
  - Kent State's Mark Carney went from interim to permanent?
  - Earlier (2024-25): Tim Albin, Ohio to Charlotte; Scot Loeffler, BGSU to an NFL staff, with Eddie George hired; Bryan Hodgson, Arkansas State MBB to USF.

## Game-model implications
- **Exit mechanics template (JMU):**
  1. Board vote.
  2. Apply to the new league.
  3. Unanimous admit vote.
  4. Negotiated early exit, about 20 months from vote to move in the original plan, compressed to about 9.
- Tunables:
  - SBC exit fee $5M base (possibly $8–18M sliding by notice).
  - AAC entry about $23M; MAC entry for an FCS move-up $18M.
  - NCAA FBS reclassification fee $5M.
  - New-member postseason ban: 2 years.
- **State-approval gates:**
  - Virginia publics need a legislative commission vote for a division change.
  - UL System schools are subject to Board of Regents budget levers.
  - Map these to `statePoliticalPressure` (JMU/ODU 40-45, Louisiana schools 45, Sac State 50).
- **G6 revenue-share realism:** default G6 payout of about 10-15% of the cap ($2–3M). Allow a "spend to lead" archetype (JMU) and "minimum" archetypes (ULM, EMU, Kent State).
- **Poaching targets:** for an AAC or P4 raid on the SBC, weight brand, fan base and market. Expected order after JMU: App State ≈ Marshall > ODU > Georgia Southern > Troy/South Alabama.
- **MAC media-rights event in 2027:** the deal is up after 2026-27, so model a renewal at flat-to-modest growth with a risk of a streaming-heavy package.
- **Football-only affiliate slot:** the MAC precedent (Sac State, 5-year term, ineligible for title and postseason for 2 years) can be offered to any FCS school with a donor-funded move-up.

## Broad sources
- SBC 2026 previews: [ESPN](https://www.espn.com/college-football/story/_/id/48759931/2026-sun-belt-conference-college-football-preview-predictions-every-team), [Underdog Dynasty](https://www.underdogdynasty.com/sun-belt-conference/44735/2026-sun-belt-season-preview-west-division)
- Sportico revenue-sharing opt-in list: https://www.sportico.com/leagues/college-sports/2025/division-i-revenue-sharing-schools-list-college-sports-1234863224/
- Sac State Big Sky exit: https://nbcmontana.com/sports/sports-insider/sacramento-state-to-withdraw-from-big-sky-conference-in-2026-27 ; Big West spotlight: https://bigwest.org/news/2026/6/26/general-the-big-west-school-spotlight-sacramento-state.aspx
- Sac State MAC pros and cons: https://www.hustlebelt.com/mac-football/44628/sacramento-state-football-to-mid-american-conference-pros-and-cons-column
- Per-school identity data (colors, venues, histories): official athletics sites and Wikipedia program pages, cited in each record.
