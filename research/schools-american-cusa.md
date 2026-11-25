# Schools: American Conference & Conference USA (2026-27)

Owner: schools-aac-cusa. Files: `data/schools/american.json` (15 records), `data/schools/cusa.json` (10 records).
As-of 2026-11-25. Record shape = SCHEMA.md `School`, plus two optional additions:
- Nested `confidence:"low"` + `note` inside `president`, `ad`, `headFootballCoach`, `headMbbCoach` and `athletics` objects when that object is uncertain.
- `lowConfidenceFields: [...]` at record level, listing scalar or object fields that are estimates. The engine can ignore it.
- Non-football school (Wichita State): `ratings.football: null`, `athletics.stadium: null`, `headFootballCoach: null`.

## Verification status (read this first)
- **Verified by web search this session:** both leagues' 2026-27 membership, the American rebrand, the JMU move (timing and fees), C-USA's 2026 departures, and Memphis's 2025 Big 12 bid.
- **Search budget ran out:** the shared 200-search limit for the turn was used up early, and WebFetch could not reach athletics sites (jmusports.com and fbschedules.com both failed to resolve, so no more hosts were tried).
- **Unverified fields:** leadership (especially Dec 2025 coaching hires), finances, US News ranks, endowments and enrollments come from model knowledge (through mid-2026). They are flagged low-confidence where it matters. Re-verify on a follow-up pass.
- **2026 results not reflected:** in-season 2026 results and any Nov 2026 firings are not in the ratings. Ratings reflect results through the 2025-26 seasons.

## Verified membership
**American Conference, 2026-27** ([ESPN realignment list](https://www.espn.com/mens-college-basketball/story/_/id/49973549/college-basketball-conference-changes-realignment), [Wikipedia](https://en.wikipedia.org/wiki/American_Conference_(NCAA)), [CBS on the rebrand](https://www.cbssports.com/college-football/news/aac-changes-name-to-american-conference-introduces-mascot-soar-as-part-of-rebranding-intiative/))
- **Branding:** "American Conference" / "The American". "Athletic" was dropped in July 2025, alongside a new mascot, "Soar".
- **Full members (13):** Charlotte, East Carolina, FAU, Memphis, North Texas, Rice, South Florida, Temple, Tulane, Tulsa, UAB, UTSA, Wichita State. Wichita State is non-football, so 12 full members play football.
- **Football-only (2):** Army (since 2024) and Navy (since 2015); both are Patriot League in other sports. That makes 14 football teams.
- **Pending:** James Madison becomes a full member on **2027-07-01**, in 17 of 18 sports; field hockey stays in the MAC.
  - Announced 2026-10-12 as "no later than July 1, 2028". In mid-Nov 2026 JMU and the Sun Belt agreed to an early exit on July 1, 2027.
  - Reported terms: about a **$23M entry fee** to the American (corporate partners) and a **$5M Sun Belt exit fee** (private donors). On3 floated up to $10M for a 2027 exit; whether the terms changed with the early-exit deal was not confirmed.
  - The timing was driven by a pending Sun Belt vote to raise its exit fee.
  - Sources: [ESPN Oct](https://www.espn.com/college-sports/story/_/id/50166450/james-madison-exit-sun-belt-join-american-conference), [ESPN Nov](https://www.espn.com/college-football/story/_/id/50534149/james-madison-moving-american-conference-2027), [JMU release](https://www.jmu.edu/news/2026/10/12-conference-announcement.shtml), [FOS](https://frontofficesports.com/article/james-madison-joins-the-american-before-sun-belt-exit-fees-rise/), [Fox](https://www.foxsports.com/stories/college-football/james-madison-american-conference-sun-belt-transition), [On3](https://www.on3.com/news/conference-realignment-21-non-power-schools-have-moved-in-three-years-and-more-changes-are-coming/).
- **2027-28 shape:** 14 full members and 15 football teams.

**Conference USA, 2026-27 (10, all-sports)**
- **Members:** Delaware, FIU, Jacksonville State, Kennesaw State, Liberty, Middle Tennessee, Missouri State, New Mexico State, Sam Houston, Western Kentucky ([ESPN](https://www.espn.com/mens-college-basketball/story/_/id/49973549/college-basketball-conference-changes-realignment)).
- **Departures, July 2026:** Louisiana Tech went to the Sun Belt after a dispute with C-USA that was settled before the league [re-issued its 2026 schedule on 2026-04-29](https://conferenceusa.com/news/2026/4/29/fb-cusa-releases-revised-2026-football-schedule.aspx). UTEP went to the Mountain West.
- **Additions:** none announced for 2027 or 2028 (searches found none).
- **Raid risk:** the Sun Belt may replace JMU, possibly with a C-USA school. The most-cited names are Liberty, WKU and MTSU, with FIU less often ([Athlon](https://athlonsports.com/college-football/expansion-realignment-whats-next-american-conference-james-madison), [The Advocate](https://www.theadvocate.com/acadiana/sports/ul_lafayette/james-madison-sun-belt-conference-american-conference/article_f7b60144-97a0-4eb8-898d-1d93344cf87f.html)).
- **Title game:** the 2026 C-USA championship game is Fri. Dec 4 on CBS Sports Network.

## Corrections to the brief
1. **JMU is joining the American** on 2027-07-01 (full member). The brief lists it only as a football reference point; it is still Sun Belt in 2026-27.
2. **Liberty never made the CFP.** It went 13-0 in 2023 and played in the **Fiesta Bowl** (a New Year's Six game; lost 45-6 to Oregon). In 2024 it went 8-4. The 2025 G6 CFP teams were **Tulane and JMU** (both made the field because ACC champion Duke was unranked).
3. **2010 alignments:**
   - **Temple:** in the **A-10 for all sports except football**, which was MAC (FBS) 2007-11. Encoded as `all:"a10", football:"mac"`.
   - **UTSA:** had no football in 2010-11 (it started 2011); Southland in all sports.
   - **Charlotte:** A-10, no football (started 2013, FBS 2015).
   - **Kennesaw State:** ASUN, no football.
   - **Army/Navy:** Patriot League in all sports, FBS independents in football.
   - **Liberty:** Big South (FCS). **Delaware:** CAA (FCS). **Jax State:** OVC (FCS). **Sam Houston:** Southland (FCS). **Missouri State:** MVC (`mvfc` for football, FCS).
   - **NMSU:** `wac-2010` (FBS).
   - **FAU/FIU/UNT/MTSU/WKU:** `sun-belt`. I used the current ID because the lineage is continuous; the history agent may prefer `sun-belt-2010`.
4. **AAU:** Rice, Tulane and **USF** (joined 2023) are AAU members. **Temple is not**, and neither is any C-USA school.
5. **Wichita State dropped football after the 1986 season.**
6. **Coaching carousel after 2025 (from memory, unverified):**
   - **Memphis:** Silverfield to Arkansas; Charles Huff hired.
   - **USF:** Golesh to Auburn; Brian Hartline hired.
   - **North Texas:** Eric Morris to Oklahoma State; Neal Brown hired.
   - **Tulane:** Sumrall to Florida; Will Hall hired.
   - **UAB:** Dilfer fired Oct 2025; permanent successor unknown.
   - All five are flagged low-confidence.
7. **Memphis donor note:** FedEx founder **Fred Smith died in June 2025** (from memory). FedEx and AutoZone ties remain, but "Fred Smith as active booster" is outdated.
8. **SCHEMA ID lists** for both leagues match verified 2026-27 membership. No ID changes needed.

## Leadership changes 2025-26 (as encoded; verify)
- **Football:** Memphis (Huff), USF (Hartline), North Texas (N. Brown), Tulane (W. Hall), UAB (Dilfer fired; Mortensen interim).
- **Men's basketball:** FAU (Jakus, 2025), USF (Hodgson, 2025), North Texas (D. Robinson, 2025), Missouri State (Cuonzo Martin returned, 2025), FIU (Ballard fired in 2025; successor not captured).
- **Presidents:** USF (Moez Limayem, 2025), FIU (Jeanette Nuñez made permanent), Delaware (Laura Carlson made permanent), NMSU (Valerio Ferme, 2025), Navy superintendent (Lt. Gen. Michael Borgschulte, 2025).
- **Uncertain status:** Tulsa president and AD, UAB president, Navy AD, MTSU president, AD and football coach, Delaware MBB coach, Sam Houston and Charlotte football coaches.

## Notable storylines (for event seeds)
- **Memphis wants a P4 seat.** In July 2025 it offered the Big 12 a package reported at over $200M: no distributions for the back end of the Big 12 TV deal, plus a removal clause if it underperformed. The Big 12 rebuffed it (expansion needs 12 of 16 votes). Memphis also floated taking basketball to the Big East. Tennessee is spending public money on its stadium and arena. ([Yahoo](https://sports.yahoo.com/college-football/breaking-news/article/memphis-proposing-lucrative-offer-to-join-big-12-but-it-lacks-support-from-conference-leadership-sources-175519540.html), [CBS](https://www.cbssports.com/college-football/news/memphis-bid-to-join-big-12-falls-short-as-conference-leaders-rebuff-200-million-proposal-from-school/))
- **USF's on-campus stadium** (about 35k seats, targeted for 2027) is its P4 credential. It still resents rival UCF getting into the Big 12 in its place.
- **Tulane's rise:** a 2022 Cotton Bowl win and a 2025 CFP bid, but it loses coaches to P4 jobs every two years (Fritz, Sumrall).
- **Texas trio (UTSA, North Texas, Rice):**
  - UTSA has the San Antonio market and is bigger after its 2025 UT Health merger.
  - North Texas has the DFW market and an 11-1 season in 2025.
  - Rice has academics and the Houston market.
  - The Texas Legislature and UT Regents add political weight. Former rival Texas State jumped to the Pac-12.
- **Service academies:** Army (football-only since 2024; 2024 American champion) and Navy (since 2015) count Army-Navy as a conference game. That game stays on CBS outside the American's ESPN deal. DoD leadership changes (the Navy superintendent was replaced in 2025) are a federal-politics lever.
- **Wichita State** is the only non-football member and is exposed in any football-driven split. A football revival is a recurring rumor.
- **Liberty** played as an independent from 2018 to 2022 with its own ESPN deal, joined C-USA in 2023, and is the most-cited Sun Belt and American candidate. Its evangelical mission and 2024 Clery fine make some presidents hesitate.
- **C-USA's survival with 10:**
  - The league lost Louisiana Tech (after a legal settlement) and UTEP in 2026.
  - Move-ups Delaware and Missouri State arrived in 2025, Kennesaw State in 2024.
  - Sam Houston, Jax State, Liberty and NMSU arrived in 2023, after the American took six C-USA schools.
  - NMSU is now geographically stranded and a natural Mountain West target.
  - WKU, MTSU and Liberty are exposed to a Sun Belt raid.
- **Florida politics:** FAU's president is a former GOP legislator and FIU's is a former Lt. Governor. The Board of Governors drives high political pressure at USF, FAU and FIU.
- **ECU's ACC dream** has backing in the NC General Assembly. **UAB** is governed by the UA System board that shut down its football in 2014.

## Game-model implications
- **Entry-fee benchmark:** a G6-to-G6 move costs about **$20-25M to enter** (JMU paid about $23M) plus a **$5-10M exit**. Model exit fees as a variable the losing league can vote to raise; that pending vote triggered JMU's move.
- **P4 buy-in offers:** Memphis-style packages (about $200M or more, deferred distributions, probationary clauses) should exist as a mechanic. Acceptance should require a supermajority (12 of 16 in the Big 12) and a market/brand threshold that Memphis did not clear in 2025.
- **Coach poaching:** G6 programs that win 10+ games should face about a 50-70% chance of losing their head coach to a P4 job that offseason. Tulane, North Texas, USF and Memphis all did in 2025. Apply a one-year football-rating dip of about 3-6 points.
- **Football-only affiliates:** Army and Navy add brand value (TV draw ~50) but no revenue share in other sports. Their federal governance replaces state political pressure (fixed ~50).
- **Non-football members:** Wichita State carries a `football:null` rating; give it a higher "orphan" risk in football-driven splits.
- **Political pressure tiers used:**
  - Florida public schools: 60-65
  - Texas publics, Memphis, UAB, ECU: 55-60
  - Other public G6 schools: 30-45
  - Private schools (Rice, Tulane, Tulsa, Liberty): 15-20
- **C-USA fragility:** at 10 members with three likely Sun Belt targets, model a high chance of C-USA losing a member each cycle. Its replacement pool is FCS move-ups such as those from the UAC, Big Sky and Southland.
- **Revenue-share spread:** American schools mostly pay partial caps of about $5-15M, with Memphis near the top. C-USA schools pay about $2-8M. Treat these as estimates; exact amounts were not verified.

## Broad sources
- **Membership:** [ESPN 2026-27 realignment](https://www.espn.com/mens-college-basketball/story/_/id/49973549/college-basketball-conference-changes-realignment), [Yahoo 2026-27 realignment](https://sports.yahoo.com/articles/conference-realignment-2026-27-lots-150000459.html), [C-USA revised 2026 schedule](https://conferenceusa.com/news/2026/4/29/fb-cusa-releases-revised-2026-football-schedule.aspx), [C-USA 2026-27 MBB preseason poll](https://conferenceusa.com/news/2026/10/8/mens-basketball-mbb-2026-27-cusa-preseason-all-conference-team-and-poll-announced.aspx)
- **JMU move:** [ESPN](https://www.espn.com/college-football/story/_/id/50534149/james-madison-moving-american-conference-2027), [JMU](https://www.jmu.edu/news/2026/10/12-conference-announcement.shtml), [Deseret](https://www.deseret.com/sports/2026/10/12/conference-realignment-james-madison-leaving-sun-belt-conference-for-american-conference/), [On3 American expansion candidates](https://www.on3.com/sites/tiger-sports-report/news/5-potential-american-conference-expansion-candidates)
- **Finances:** [USA Today NCAA finances](https://sportsdata.usatoday.com/ncaa/finances), [Knight-Newhouse](https://knightnewhousedata.org/)
- **Academics:** [AAU members](https://www.aau.edu/who-we-are/our-members), [US News national rankings](https://www.usnews.com/best-colleges/rankings/national-universities)
- **CFP:** a Yahoo headline reports the CFP announced an expanded 24-team format with ESPN. Not verified here; it belongs to the money-postseason agent.
