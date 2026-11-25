# Schools: Big 12 & ACC (2026-27 snapshot, as of 2026-11-25)

Files: `data/schools/big-12.json` (16 records) and `data/schools/acc.json` (18 records: 17 football members plus Notre Dame).

## Method and how far to trust it

- **The shared web-search budget ran out after the first four queries**, and WebFetch could not reach outside hosts (usnews.com, on3.com and methodshop.com all failed to resolve). Most values therefore come from model knowledge, which runs to about mid-2026. Only these points were confirmed by search:
  - 2024-25 Directors' Cup: Texas 1, USC 2, Stanford 3, UNC 4, Virginia 12, Cal 24, BYU 25 ([NACDA](https://nacda.com/news/2025/6/10/directorscup-grand-valley-emory-and-cumberlands-secure-learfield-directors-cups-stanford-leads-in-division-i.aspx), [On3](https://www.on3.com/news/learfield-directors-cup-final-2025-division-i-standings-revealed), [UVA](https://virginiasports.com/news/2025/06/26/virginia-finishes-12th-in-final-learfield-directors-cup-standings), [BYU](https://byucougars.com/news/2025/6/26/byu-is-no-25-in-directors-cup-standings), [SI/Cal](https://www.si.com/college/cal/other-sports/cal-finishes-24th-in-directors-cup-standings-01jypqqgzjaw)).
  - 2026 US News: Stanford tied for #4 ([Quartz](https://qz.com/yale-harvard-princeton-best-universities-us-news)).
  - FY2024 conference revenue: Big 12 $493.8M ([Deseret](https://www.deseret.com/sports/2025/05/17/why-drop-in-revenue-big-12-conference-2024/)); ACC about $711M. Tax filings show an average ACC full-share payout of $47.1M against $39.5M in the Big 12 ([Fox Sports/AP](https://www.foxsports.com/articles/cfb/tax-filings-acc-paid-average-of-471m-to-fullshare-member-schools-big-12-paid-average-of-395m)).
  - Phoenix is DMA #12 in 2025-26, and there are 210 DMAs.
- **Each record lists its unverified fields in `lowConfidenceFields`** (an extra field beyond the schema). Records whose leadership is uncertain also carry `confidence:"low"` and a `note`. Person objects can carry their own `confidence`/`note`.
- **Applies to every record:**
  - Athletics revenue and expenses are FY2024 estimates rounded to $5M. Private schools use EADA-style estimates.
  - DMA ranks are ±2.
  - US News ranks are only verified for Stanford; Duke's #7 is moderately confident.
  - Endowments are approximate and sometimes system- or foundation-level.
  - 2025 football records marked "approx." come from memory.
  - **2026 season results, the spring-2026 MBB coaching carousel and fall-2026 in-season firings are not reflected.** Refresh these first when search is available.

## Broad sources
- Finances: [USA Today NCAA finances](https://sportsdata.usatoday.com/ncaa/finances), [Knight-Newhouse](https://knightnewhousedata.org/), [EADA](https://ope.ed.gov/athletics/) (privates).
- Academics: [US News National Universities](https://www.usnews.com/best-colleges/rankings/national-universities), [AAU members](https://www.aau.edu/who-we-are/our-members).
- Markets: Nielsen 2025-26 DMA list (secondary: [Wikipedia market list](https://en.wikipedia.org/wiki/List_of_television_stations_in_North_America_by_media_market)).
- Olympic sports: [Learfield Directors' Cup](https://nacda.com/news/2025/6/10/directorscup-grand-valley-emory-and-cumberlands-secure-learfield-directors-cups-stanford-leads-in-division-i.aspx).
- Coaches: [FBS coaches list](https://en.wikipedia.org/wiki/List_of_current_NCAA_Division_I_FBS_football_coaches), [D-I MBB coaches list](https://en.wikipedia.org/wiki/List_of_current_NCAA_Division_I_men%27s_basketball_coaches).
- Conferences: [big12sports.com](https://big12sports.com/), [theacc.com](https://theacc.com/).

## Corrections to the brief
- **Membership.** The Big 12 (16) and ACC (18, including Notre Dame) lists match the brief. No ID changes were needed.
- **Notre Dame.**
  - 2026: `{all:"acc", football:"independent"}`.
  - 2010: `{all:"big-east-2010", football:"independent"}`.
- **2010 conferences that differ from a naive reading:**
  - BYU was still in the **MWC** in 2010-11. Its football independence began in 2011.
  - Colorado was still in the **Big 12** in 2010-11; it went to the Pac-12 in 2011 and came back in 2024.
  - TCU was in the **MWC** and Utah in the **MWC**.
  - Houston, UCF and SMU were in **`cusa-2010`**.
  - Cincinnati, Louisville, Pitt, Syracuse and WVU were in **`big-east-2010`**.
  - Arizona, ASU, Cal and Stanford were in the **`pac-10`**.
- **Religious affiliation.**
  - Wake Forest is Baptist only historically; it has been independent of the Baptist State Convention since 1986.
  - Syracuse has Methodist heritage but is nonsectarian.
  - Duke's Methodist affiliation is historical.
  - Notre Dame is specifically Congregation of Holy Cross.
  - Miami and Stanford are nonsectarian.
- **AAU.**
  - Arizona State (2023) and Notre Dame (2023) are recent members.
  - Miami is believed to have joined in 2023 (unverified).
  - Florida State is **not** a member as of this snapshot (it is a stated goal; verify).
  - Syracuse left in 2011.
  - NC State, Virginia Tech, Clemson, Louisville, BC, Wake Forest, SMU, Baylor, BYU, TCU, Texas Tech, Houston, UCF, Cincinnati, K-State, Oklahoma State and WVU are non-members.
- **DMA assignments that are not the obvious big city:**
  - Morgantown is in **Clarksburg-Weston** (not Pittsburgh).
  - Manhattan, KS is in **Topeka**.
  - Stillwater is in **Oklahoma City** (low confidence).
  - Blacksburg is in **Roanoke-Lynchburg**.
  - Clemson is in **Greenville-Spartanburg-Asheville-Anderson**.
  - Provo is in **Salt Lake City**.
  - Lawrence is in **Kansas City**.
  - Boulder is in **Denver**.
- **Booster examples.** The brief's "Miami's John Ruiz era" framing is right but dated: Ruiz's peak public NIL role was 2022-24.

## Leadership changes found (2025-26 cycle)

| School | Role | Change | Confidence |
|---|---|---|---|
| Iowa State | FB | Matt Campbell to Penn State; **Jimmy Rogers** (from Washington State) | medium |
| Kansas State | FB | Chris Klieman retired; **Collin Klein** | low |
| Oklahoma State | FB | Mike Gundy fired Sept 2025; **Eric Morris** (from North Texas) | high |
| Utah | FB | Kyle Whittingham stepped down (reportedly to Michigan); **Morgan Scalley** | medium |
| Virginia Tech | FB | Brent Pry fired; **James Franklin** | high |
| Cal | FB | Justin Wilcox fired; **Tosh Lupoi** (Ron Rivera is GM) | low-medium |
| Stanford | FB | Frank Reich (interim) out; **Tavita Pritchard** | low-medium |
| Oklahoma State | President | Kayse Shrum resigned; **Jim Hess** | low |
| Virginia | President | Jim Ryan resigned June 2025; Paul Mahoney interim; **Scott Beardsley** | low |
| SMU | President | R. Gerald Turner retired; **Jay Hartzell** | low |
| NC State | Chancellor | **Kevin Howell** (2025) | high |
| West Virginia | President | **Michael Benson** (Jan 2025) | high |
| TCU | AD | Jeremiah Donati to South Carolina; **Mike Buckle** | low |
| Cal | AD | Jim Knowlton out; **Jay Larson** | low |
| Georgia Tech | AD | J Batt out; **Ryan Alpert** | low |
| Stanford | AD | **John Donahoe** (2025) | high |

2025 MBB hires carried as current (high confidence): Ross Hodge (WVU), Alex Jensen (Utah), Luke Loucks (FSU), Jai Lucas (Miami), Will Wade (NC State) and Ryan Odom (UVA).

**Low confidence after the March 2026 carousel:** Bobby Hurley (ASU), Wes Miller (Cincinnati), Jerome Tang (K-State), Earl Grant (BC), Hubert Davis (UNC), Damon Stoudamire (GT), Jeff Capel (Pitt), Adrian Autry (Syracuse), and Dave Aranda (Baylor FB). Mike Norvell (FSU FB) is also unverified for in-season 2026.

## Notable storylines

### Big 12
- **Texas Tech's billionaire model.** Regents chair Cody Campbell and the Matador Club bought a 2025 Big 12 title and CFP trip. TTU System chancellor Brandon Creighton is a former state senator, which ties the program to the Legislature. Booster influence is rated 96.
- **The Arizona pair.**
  - Arizona's university-wide deficit led to Arizona Board of Regents oversight and repayment of loans to athletics.
  - ASU (Crow, AAU 2023, Phoenix #12 DMA) is the more attractive realignment asset.
  - Both arrived in 2024. A "Four Corners" bloc with Colorado and Utah could act as one.
- **Utah and Otro Capital.** Utah set up a for-profit athletics entity with a minority private-equity stake, a first in the Power 4. It is the template for the Big 12's own private-capital talks.
- **BYU.** The no-Sunday rule is a scheduling constraint. The church acts as the governing board. AJ Dybantsa was the first-ever No. 1 recruit at BYU.
- **The revenue gap.** Cincinnati, WVU, UCF and Houston joined 2023-24 on phase-in shares. They have the smallest stadiums and budgets, and WVU's travel is the worst in the league.
- **Kansas.** Kansas basketball and the KU/K-State "pair" politics in Topeka; KU is the Big 12 school most coveted for basketball.
- **Oklahoma State.** The Pickens legacy is undercut by a 1-11 collapse (2025). Bedlam is dormant, and the Oklahoma legislature has floated bills to force it.

### ACC
- **The 2025 settlement (FSU, Clemson, ACC).**
  - Exit costs fall to about $75M from 2026 and step down each year.
  - ESPN's option runs through 2036.
  - Part of the revenue distribution is now based on brand and viewership.
  - FSU's trustees and Clemson are the likeliest first movers.
  - The fbs-conferences and legal agents own the exact fee schedule.
- **Cal and Stanford.**
  - Both receive about a 30% share for years 1-7.
  - They have cross-country travel.
  - Cal's deficit of $30M+ a year and stadium debt make it a cut-sports candidate.
  - Stanford is being run with a "business" turn: ex-Nike CEO Donahoe as AD and Andrew Luck as GM.
- **SMU.** It takes no ACC media share through 2032-33. Donors fund the gap, so booster influence is rated 90.
- **Notre Dame.**
  - Its NBC deal runs through 2029.
  - It plays five ACC football games a year.
  - It must join the ACC if it ever joins a football conference before 2036.
  - Its 2025 CFP omission renewed the independence debate.
- **UNC, Virginia and the state capitals.**
  - UNC and Virginia are the AAU flagships the Big Ten would want.
  - NC politics would block a move that strands NC State.
  - Virginia politics would block one that strands VT. The precedent is the 2003 Warner-era forcing of VT into the ACC.
  - UVA's 2025 presidential crisis adds instability on the Board of Visitors.
- **Duke vs. Mensah (2026).** Duke's suit tests whether revenue-share/NIL contracts are enforceable. It is a good event seed.
- **Miami.** The 2025 national-runner-up run makes it the ACC's top football brand alongside Clemson and FSU.
- **Rivalries with state or political stakes:** Louisville–Kentucky, Georgia Tech–Georgia, Clemson–South Carolina, FSU–Florida, Pitt–Penn State/WVU and Virginia Tech–WVU.

## Game-model implications
- **State pressure.** Use `statePoliticalPressure` ≥ 80 (UNC, NC State, Virginia, Virginia Tech, FSU) to trigger a "legislature demands package deal" event. It would apply when a Big Ten or SEC invitation splits UNC from NC State or UVA from VT. Suggested probability: 0.6 × (pressure/100).
- **Booster-funded exits.** Treat `boosterInfluence` ≥ 85 (Texas Tech, SMU, Oklahoma State) as able to self-fund exit fees or share forfeitures; SMU is the precedent. Cap it at roughly $100M per event.
- **ACC exit fees.** Model the fee as a declining schedule with FY2026 at about $75M (pull exact numbers from `conferences.json`). FSU and Clemson get a "settlement-enabled" flag that lowers the morale cost of leaving.
- **Partial-share members.** Cal, Stanford and SMU need a share multiplier: 0.3 for Cal and Stanford through 2030-31 rising to 1.0 by 2033-34, and 0 for SMU through 2032-33. This also feeds the "Cal cuts sports" event.
- **Notre Dame.** Add a contract clock (NBC through 2029) and a CFP-snub counter. Each snub raises the Big Ten-join probability.
- **Data refresh.** Every season should re-roll `football` and `mbb` from results. For example, Oklahoma State's 1-11 and Colorado's 3-9 already argue for in-season decay.

## To verify when search is available
- 2026 football results and the November 2026 CFP rankings.
- 2026 NCAA tournament seeds and results.
- The spring-2026 MBB carousel (low-confidence names above).
- Jerome Tang's status.
- FY2024 Knight-Newhouse revenue and expense figures.
- The 2026 US News ranks.
- The Miami and FSU AAU status.
- The GT, Cal and TCU ADs.
- The UVA, Oklahoma State and SMU presidents.
- The Utah–Otro deal terms.
