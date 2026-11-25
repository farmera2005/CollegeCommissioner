# Media Rights — "the heart of the game"

As of **2026-11-25**. Owner: media-rights agent. Files: `data/media_deals.json` (44),
`data/broadcasters.json` (14), `data/conference_networks.json` (9), `data/sponsors.json` (20).

> **Research caveat.** Partway through this pass, the shared web-search budget (200 searches
> per turn, shared by all agents) ran out, and WebFetch could not reach any outside host. The
> items checked this session were: the Pac-12 (CBS/CW/USA), Mountain West 2026, MAC/C-USA
> terms, the ACC option, Big 12 terms, SEC $300M/$710M, Big Ten terms and the title-game
> buyback, the Big Ten private-capital pause, the CFP $7.8B deal and the 24-team addendum,
> and Yormark's exit. Everything else comes from prior knowledge (to about mid-2026) and is
> marked `"confidence": "low"`. Several low-confidence records cite a Wikipedia article as a
> pointer only. A follow-up pass should re-verify them, along with 2026-season viewership.

## File shapes

- **media_deals.json**: `{id, conference, partner, coPartners[], status (active|expired|never-signed), packageId, packageAnnualValueUsd, rightsDescription, startYear, endYear, firstSeason, lastSeason, lastFootballSeason, annualValueUsd, totalValueUsd, escalator, inventory[], exclusivity, proRataClause, proRataNotes?, renegotiationTriggers[], networkLinked, confidence?, note, sources[]}`.
  **Year convention:** `startYear` is the fall year of the first season. `endYear` is the
  spring year of the last academic year covered, so Big Ten 2029-30 has `endYear` 2030. Use
  `lastFootballSeason` for football (2029). `packageAnnualValueUsd` is the conference's total
  across all partners in that cycle, and is the field the engine should use for income.
  `annualValueUsd` is the per-partner value, null when the split is undisclosed. Historical
  deals (`status: "expired"`/`"never-signed"`) are included for 2010-start saves and
  precedents.
- **broadcasters.json**: `{id, name, parent, linear[], streaming[], currentCollegeProperties[], keyExecs[{name,title}], appetite, recentBids[{year,property,result,note}], confidence?, note, sources[]}`.
  New IDs: `versant` (USA Network, spun off from NBCU; alias `usa`) and `kiswe`.
- **conference_networks.json**: `{id, name, conference, type, owners[{entity,stakePct}], partners[], launched, shutDown, status, streaming, estimatedSubscribers, estimatedRevenueUsd, perSchoolContribution, carriageFeeNotes, notes, confidence?, sources[]}`.
- **sponsors.json**: `{id, name, parent, category, knownCollegeDeals[{property, role, since, through, valueUsd}], notes, confidence?, sources[]}`.

## Per-conference deal summaries (2026-27)

| Conf | Partners | Term (last season) | Value | Notes |
|---|---|---|---|---|
| **SEC** | ESPN/ABC only | 2033-34 | ~$300M/yr top tier + legacy SEC Network deal ≈ **$710M/yr** all-in | ESPN took CBS's package from 2024, about 5.5x CBS's $55M ([SMW](https://www.sportsmediawatch.com/2020/12/sec-espn-deal-official-abc-replacing-cbs/), [FOS](https://frontofficesports.com/espn-wants-more-sec-games-but-conference-eyes-a-bigger-payday)). Pro rata amendment for Texas/OU. Sankey says the deal is undervalued vs the Big Ten ([AA](https://awfulannouncing.com/espn/greg-sankey-sec-media-rights-deal-undervalued.html)). |
| **Big Ten** | FOX (noon), CBS (3:30), NBC (prime)/Peacock, BTN | 2029-30 | ">$7B"/7 yrs ≈ $1.1B/yr (FOX ~$400M, CBS ~$350M, NBC ~$350M) | Back-loaded ([Bloomberg via BNN](https://www.bnnbloomberg.ca/big-ten-sets-college-record-with-1-billion-a-year-broadcast-deal-1.1807434), [CBS](https://www.cbssports.com/college-football/news/big-ten-reaches-seven-year-media-rights-deal-with-cbs-fox-and-nbc-for-football-basketball-through-2029-30)). FOX bought NBC's 2026 title game for $45-55M ([On3](https://www.on3.com/news/report-fox-to-buy-back-big-ten-2026-championship-game-from-nbc-for-45-55-million/)). The UC Investments $2.4B "Big Ten Enterprises" plan (grant of rights to 2046) is paused ([FOS](https://frontofficesports.com/uc-investments-says-big-ten-deal-is-off-until-schools-can-agree/)). |
| **Big 12** | ESPN + FOX | 2030-31 | $2.28B/6 yrs for 12 schools ≈ $380M/yr (~$31.7M/school). Pro rata puts 16 schools at ≈ **$507M/yr** (derived) | Signed Oct 2022, about 18 months before the window opened ([ESPN](https://www.espn.com/college-football/story/_/id/34910144/big-12-nears-six-year-228b-tv-extension-deal-espn-fox)). Pro rata clause in both contracts ([AA](https://awfulannouncing.com/ncaa/big-12s-new-media-rights-deals-reportedly-contain-pro-rata-clause-in-case-of-future-expansion.html)). **Yormark leaves Jan 31, 2027** for RedBird's Milan Sports & Entertainment ([ESPN](https://www.espn.com/college-sports/story/_/id/50327726/commissioner-brett-yormark-leaving-big-12-january)). |
| **ACC** | ESPN (incl. ACC Network); CW sublicense | 2035-36 | Undisclosed (original 2012 deal $3.6B/15 yrs) | ESPN exercised its option Jan 30, 2025, ahead of the Feb 1 deadline. Phillips called it a "look-in" ([ESPN PR](https://espnpressroom.com/us/press-releases/2025/01/acc-and-espn-announce-long-term-renewed-commitment/), [On3](https://www.on3.com/news/acc-commissioner-jim-phillips-publicly-addresses-conferences-extension-with-espn)). Pro rata paid for Cal, Stanford and SMU, which took reduced shares (low confidence). |
| **Pac-12 (rebuilt)** | CBS (primary) + The CW + USA Network | 2030-31 | Undisclosed; projected $7-10M/school ($56-80M total) | CBS (June 2025): ≥3 football and ≥3 men's basketball games on CBS plus both title games ([FOX/AP](https://www.foxsports.com/articles/cfb/rebuilding-pac12-reaches-deal-with-cbs-for-its-football-and-mens-basketball-games)). CW: 13 football / 35 MBB / 15 WBB ([CBS](https://www.cbssports.com/college-football/news/pac-12-secures-long-term-media-rights-deal-with-the-cw-as-conference-gains-more-momentum-ahead-of-expansion)). USA: 22 football games ([ESPN](https://www.espn.com/college-sports/story/_/id/46953746/pac-12-signs-tv-deal-usa-sports-2030-31)). Octagon advised ([Pac-12](https://pac-12.com/news/2024/11/19/general-pac-12-conference-selects-octagon-to-lead-media-rights-strategy-for-its-new-era.aspx)). Every home game is on linear TV. |
| **Mountain West** | CBS + FOX + The CW + Kiswe (DTC) | 2031-32 (CW 2030-31) | Undisclosed (old deal: $270M/6 yrs) | Feb 3, 2026: CBS 15 football games + lead basketball; FOX 12 games + MW title game every year; CW 13; paid Kiswe app from July 2026 ([FBS](https://fbschedules.com/mountain-west-announces-new-media-rights-deal-with-cbs-fox-the-cw/), [AA](https://awfulannouncing.com/college-football/mountain-west-inks-media-rights-deals-cbs-fox-cw.html)). |
| **American** | ESPN | 2031-32 | ~$1B/12 yrs (~$83M/yr) | ESPN kept the value whole through the 2023 membership churn (low). |
| **C-USA** | CBS (Tier 1: 18 football + title game + 18 MBB) + ESPN (midweek + streaming) | 2027-28 | Undisclosed | ([C-USA](https://conferenceusa.com/news/2022/11/10/general-conference-usa-announces-multimedia-rights-deal.aspx)). No extension found. |
| **Sun Belt** | ESPN | ~2030-31 (low) | Undisclosed | |
| **MAC** | ESPN (CBSSN sublicense) | **2026-27, expiring** | ~$100M/13 yrs (low) | Steinbrecher (Nov 2025) expected a new deal "within 6-18 months" and would not promise midweek games after 2026 ([Forbes](https://www.forbes.com/sites/timcasey/2025/11/11/how-the-mid-american-conference-and-espn-made-maction-mid-week-football-popular/)). No new deal confirmed. |
| **Notre Dame** | NBC/Peacock | 2034 season | ~$50M/yr (low) | One Peacock-exclusive game a year. |
| **Big East** | FOX (primary) + TNT + NBC/Peacock | 2030-31 | Undisclosed (old FOX deal ~$500M/12 yrs) | low |
| **WCC** | ESPN (+ CBSSN history) | unknown | unknown | Gonzaga leaves for the Pac-12 in 2026. low |
| **A-10** | CBS + ESPN + USA | 2030-31 | Undisclosed | low |
| **CFP** | ESPN (+ TNT sublicense) | 2031-32 | $7.8B/6 yrs ($1.3B/yr) + **24-team addendum $1.7B/5 yrs (~$345M/yr)** | See below. |
| **NCAA** | CBS/TNT (men's), ESPN (women's + 39 championships) | 2032 | $8.8B/8 yrs (~$1.1B/yr); $920M/8 yrs (~$115M/yr; WBB ~$65M) | low |

### The 24-team CFP (announced Nov 9, 2026) changes the media landscape

- The field becomes 24 teams from 2027-28: the Power 4 champions (decided by each league), the
  top Group of 6 team, and 19 at-large teams. Seeds 1-8 get byes, and seeds 9-24 play 16
  first-round games on campus. The 2028 title game is Jan 24 in New Orleans
  ([CFP](https://collegefootballplayoff.com/news/2026/11/9/24-team-expansion),
  [FOX](https://www.foxsports.com/stories/college-football/college-football-playoff-expanding-24-teams-heres-what-you-need-know)).
- **Power 4 conference championship games are eliminated.** ESPN pays about $1.7B over 5 years
  (about $345M a year), recovers about $140M a year it spent on the SEC, ACC and Big 12 title
  games, and can sublicense 6 of the 12 new games
  ([ESPN](https://www.espn.com/college-football/story/_/id/50433381/cfp-espn-ink-5-year-17b-deal-expand-field-sources-say),
  [On3](https://www.on3.com/news/college-football-playoff-media-rights-deal-espn-clears-path-expansion-24-teams-cfp/)).
- Conferences lose an estimated $225-300M a year of title-game revenue. One estimate has the net
  new money at about $125M, and another puts incremental distributions at $80-100M each for the
  SEC and Big Ten and $50-70M each for the ACC and Big 12
  ([Forbes](https://www.forbes.com/sites/kevin-sweeney/2026/11/11/the-cfps-24-team-expansion-raises-new-financial-questions-for-college-football/),
  [Yahoo](https://sports.yahoo.com/articles/cfp-expanding-24-teams-big-195954646.html)).
- FOX loses the 2027 and 2029 Big Ten title games, and CBS loses 2028. No compensation has
  been reported, which leaves a renegotiation flashpoint in the game.
- G6 title games (Pac-12 on CBS, MW on FOX, American, Sun Belt, C-USA, MAC) are not
  affected, so they stay valuable "championship" inventory.

## How deals are structured

- **Tiers.** Tier 1 is broadcast first pick, Tier 2 is cable, and Tier 3 is school-retained
  rights (Longhorn Network, Sooner Sports TV). Since about 2012 most leagues pool all tiers
  through a **grant of rights** (GoR). GoR length tracks network launches: ACC to 2036 for
  the ACC Network, SEC to 2034 for the SEC Network.
- **Windows** are the real product. The main ones are FOX's noon "Big Noon Saturday" (Big Ten
  and Big 12), the 3:30 broadcast slot (CBS Big Ten, ABC "SEC on ABC"), primetime (ABC
  Saturday Night Football, NBC "Big Ten Saturday Night"), Friday night (FOX/FS1, ESPN),
  weeknights (MACtion Tuesday/Wednesday in November, C-USA midweek in October, Sun Belt
  Tuesday/Thursday), streaming-only (Peacock exclusives, ESPN streaming, Kiswe), and
  holidays (Black Friday games on CBS/NBC).
- **Inventory picks.** Partners draft games weekly, usually 6-12 days out, with
  "first pick" or "top pick" order rotating between multi-partner deals (ESPN/FOX alternate
  in the Big 12).
- **Conference networks** earn per-subscriber carriage fees, much higher in-footprint
  (about $1+ per month) than outside it (pennies to about $0.30). That is why footprint
  expansion into big markets (Rutgers/NY, Maryland/DC, USC/UCLA/LA) was worth paying for.
  The owner matters: ESPN owns the SEC Network and ACC Network, while BTN is about 61% FOX and
  39% Big Ten. Pac-12 Networks, 100% conference-owned with no distributor, failed.
- **Pro rata clauses** (Big 12, ACC, SEC) automatically raise rights fees when members are
  added. The networks pay about one average share per new school, but incumbents can
  still cut newcomers' shares (Cal, Stanford, SMU), creating a pool to redistribute.
- **Membership-change and reduction clauses** (G6, e.g. the American 2023) let networks
  renegotiate when brands leave.
- **Look-ins and options**: ESPN's 2025 ACC option, the Big 12's early renewal before the
  window opened, and exclusive negotiating windows (Big 12's was set for 2024).
- **Sublicensing and resale**: ESPN to The CW (ACC) and TNT (CFP); ESPN to CBSSN (MAC); NBC's
  title game sold back to FOX. Under the Big Ten model, BTN holds licensing rights, which
  gives FOX a veto over its rivals' resales.

## Cord-cutting and the streaming shift

- **Pay-TV decline** (prior knowledge, low confidence): from about 100M+ pay-TV homes around
  2012 to about 68M by end-2024 including virtual MVPDs (vMVPDs, e.g. YouTube TV), and roughly
  48-50M on traditional cable/satellite. Traditional pay TV falls about 6-7% a year; with
  vMVPDs the net fall is about 3-5% a year. ESPN's linear reach is about 65-66M homes, down
  from about 100M in 2011.
- **ESPN direct-to-consumer**: the flagship "ESPN" app tier (Unlimited, $29.99 a month)
  launched **Aug 21, 2025**, with ESPN+ rebranded as Select. **FOX One** ($19.99) launched
  the same day, and an ESPN + FOX One bundle followed in fall 2025. The **Venu Sports** joint
  venture (ESPN, FOX and WBD; $42.99) was enjoined after Fubo sued (Aug 2024) and abandoned on
  Jan 10, 2025. Disney then combined Hulu + Live TV with Fubo.
- **Carriage fights** are now a game risk: the Disney/YouTube TV blackout (Oct 30 to Nov 14,
  2025) took ESPN, ABC, SEC Network and ACC Network off about 10M homes in the middle of the
  season.
- **Corporate churn among bidders**: Skydance took over Paramount (Aug 2025). NBCU spun
  off its cable networks as Versant (USA, Golf; about Jan 2026). WBD's sale process (a
  Netflix deal in Dec 2025, then a Paramount takeover reported in early 2026; verify)
  could put CBS and TNT, the NCAA tournament partners, under one owner. Fewer independent
  bidders means less leverage for conferences.
- **Streaming entrants**:
  - Amazon has NFL Thursday Night Football plus a Black Friday NFL game since 2023, and the
    NBA from 2025. It bid for the Big Ten in 2022 and dropped out of the Pac-12 talks.
  - Netflix buys events (NFL Christmas, about 24M viewers per game in 2024; WWE Raw), not
    full seasons.
  - YouTube has NFL Sunday Ticket and a free 2025 NFL Brazil game.
  - Apple has MLS (10 years, about $2.5B; Season Pass folded into Apple TV from 2026 and
    reportedly ending early) and U.S. F1 from 2026.
  - Peacock-exclusive games (the Big Ten, and an NFL wild-card game in 2024 with about 23M
    viewers) proved that streaming-only exclusives can drive sign-ups.
  - So far no streamer holds a full FBS conference package. College has relied on
    broadcast networks plus Peacock and ESPN streaming.

## Viewership (brand / TV-draw anchors)

Prior knowledge unless linked; treat as low confidence.
- The Big Ten and SEC are the clear top two conferences by average audience. FOX's Big Noon
  Saturday is the most-watched weekly window, and the Big 12 and ACC trail well behind.
- 2025 Week 1: Texas at Ohio State (FOX, noon) drew about 16.6M, a record for an early-season
  game (low).
- CFP title games: Michigan vs Washington (Jan 2024) about 25.0M; Ohio State vs Notre Dame
  (Jan 20, 2025) about 22.1M; Indiana vs Miami (Jan 19, 2026) — audience not verified.
- Measurement inflation: Nielsen counted more out-of-home viewing from Feb 2025, and "Big
  Data + Panel" became the official currency in Sept 2025. Both lift sports audiences
  about 5-15% against older years, so adjust when comparing.
- Basketball: the 2025 men's final (Florida vs Houston, CBS) about 18.1M. Women's finals:
  2024 (South Carolina vs Iowa) about 18.9M, 2025 about 8.5M without Caitlin Clark.
- **Gap:** 2026-season figures (Week 1, Big Noon averages, conference rankings) could not be
  researched this session.

## Pac-12's failed 2023 deal (Kliavkoff)

George Kliavkoff (commissioner 2021-24) passed on early extension talks in 2022, before
USC and UCLA left. He then ran a slow process in which Amazon dropped out and ESPN and FOX
were lukewarm. He finally brought presidents (Aug 2023) a streaming-first **Apple TV**
proposal: pay tied to subscriber thresholds, a reported base of about $20-23M per school,
and little linear TV. Colorado had already left for the Big 12 (July 27, 2023). After the
Aug 4 meeting, Oregon and Washington went to the Big Ten and Arizona, Arizona State and Utah
to the Big 12. Pac-12 Networks closed in 2024. Oregon State and Washington State rebuilt the
league under **Teresa Gould** with Octagon as advisor, adding Boise State, Colorado State,
Fresno State, San Diego State, Utah State, Texas State and Gonzaga for 2026, and a
three-network linear deal (CBS/CW/USA). Lessons for the game: delay, few bidders, and
contingent streaming money destroy leverage. A guaranteed linear floor beats speculative
upside. (Details from prior knowledge; `pac-12-apple-2023` in media_deals.)

## How negotiations are run

- **Commissioner-led, consultant-advised.** Kevin Warren's 2022 Big Ten deal ran a true
  auction (FOX, CBS, NBC, ESPN, Amazon); ESPN walked away from about $380M a year rather than
  overpay. Greg Sankey's 2020 SEC deal was a one-bidder upgrade: ESPN bid early and CBS
  declined to match. Brett Yormark's 2022 Big 12 deal was a pre-emptive renewal with
  incumbents about 18 months before the window, locking in +73% before the Pac-12 could go
  to market. Jim Phillips' 2025 ACC "look-in" got the option exercised but no new money
  disclosed.
- **Advisors**: Octagon (rebuilt Pac-12, 2024-25). The brief's names (Chris Bevilacqua of
  Bevilacqua Helfant Ventures, who advised Larry Scott's 2011 Pac-12 deal; Navigate; Bob
  Thompson, ex-FOX Sports Networks) are plausible archetypes, but their 2025-26 assignments
  were **not verified**. Treat "media consultant" as a hireable role.
- **Next cycles**: the Big Ten (2029-30 expiry; window about 2027-29), the Big 12 (Yormark's
  successor inherits 2030-31 planning; [FOS](https://frontofficesports.com/big-12-to-start-media-rights-negotiations-early)),
  the MAC (now) and C-USA (2027-28). The industry expects a "modest" next cycle and "no
  windfall" ([Yahoo/ESPN](https://sports.yahoo.com/articles/espn-no-one-expecting-financial-220044474.html)).

## Sponsorship notes

- The CFP and NY6 bowls are carried by blue-chip title sponsors (Allstate Sugar, Capital One
  Orange, Goodyear Cotton, Vrbo Fiesta, Chick-fil-A Peach, Rose presented by Prudential)
  plus CFP partners (AT&T, Dr Pepper, Capital One/Discover, Allstate, Goodyear).
- The NCAA's Corporate Champions are AT&T, Capital One and Coca-Cola.
- Conference title-game presenting sponsors (Dr Pepper for SEC/Big 12/ACC; formerly
  Discover for the Big Ten and 76 for the Pac-12) lose their property in 2027.
- **Gap:** conference-level sponsorship revenue figures and the Big 12's named partners under
  Yormark could not be verified. As a rough model range (low), league-office sponsorship
  revenue is about $10-40M a year for P4 and about $1-5M for G6, far below school-level
  multimedia rights (Learfield/Playfly).

## Corrections to the brief

1. **CFP is going to 24 teams in 2027-28 and Power 4 title games are eliminated** (Nov 9,
   2026), with ESPN adding about $1.7B over 5 years. This is not in the brief and changes
   conference media inventory.
2. **The rebuilt Pac-12's partners are CBS (primary), The CW and USA Network (Versant)**,
   all through 2030-31. FOX is not involved. Financials were not disclosed (projected
   $7-10M per school).
3. **The Mountain West's partners are CBS + FOX + The CW + Kiswe** (Feb 3, 2026), not just
   CBS/FOX. The deals run through 2031-32, except The CW through 2030-31.
4. **ACC option**: ESPN exercised it on **Jan 30, 2025**, before the Feb 1, 2025 deadline, in
   the 2024-25 year. The brief said "2025-26". The option kept the 2027-28 to 2035-36 years.
5. Expirations confirmed: Big Ten 2029-30 (last football season 2029); Big 12 2030-31; SEC
   2033-34; ACC 2035-36; American 2031-32. **The MAC expires after 2026-27 with no announced
   replacement**, and C-USA after 2027-28.
6. **Brett Yormark is leaving the Big 12** (effective Jan 31, 2027) for RedBird Capital.
7. **Mark Shapiro is not a FOX executive.** He is President/COO of TKO Group. Fox Corp's
   President & COO is John Nallen, and FOX Sports is run by Eric Shanks.
8. **USA Network is no longer NBC.** It belongs to Versant (spun off about Jan 2026), so it uses
   broadcaster id `versant`.
9. **FOX holds the 2026 Big Ten Championship Game**, bought back from NBC for $45-55M
   (April 2026).
10. The SEC "~$300M/yr" figure is only the top-tier package; ESPN's all-in SEC spend is
    about $710M a year.

## Game-model implications (suggested tunables)

- **Linear decline**: traditional pay-TV homes −6%/yr and total pay TV including vMVPDs
  −3.5%/yr (2026-2032). Broadcast reach stays flat at about 120M homes. A cable-only window
  loses about 4%/yr of reach; broadcast and streaming-simulcast windows do not.
- **Conference-network revenue** = in-footprint subs × $1.10/mo × 12 plus out-of-footprint
  subs × $0.20/mo × 12. The conference's share is 100% for its own network but needs a
  distribution partner, or carriage is capped at about 25% of potential (the Pac-12 Network
  lesson). In a JV the conference gets its equity share (39% for BTN). An ESPN-owned network
  pays a share via the rights fee.
- **Viewership to rights fee** (calibrated on the Big Ten, the 2024 SEC top tier and the Big
  12): value per game ≈ $3.0-3.5M per 1M average viewers in broadcast windows, about $1.5-2M
  per 1M on cable, and about $0.5-1M per 1M for midweek or streaming-only. Annual package
  ≈ Σ windows × games × viewers × rate × competition multiplier × exclusivity premium
  (1.0-1.15).
- **Competition multiplier**:
  - 1 serious bidder = 0.75 (Pac-12 2023, MAC)
  - 2 bidders = 1.0 (Big 12 2022, SEC 2020)
  - 3 = 1.2
  - 4+ incl. a streamer = 1.35-1.45 (Big Ten 2022)
  - Each bidder has a college budget and open windows (FOX noon, CBS 3:30, ABC 3:30/prime,
    NBC prime, CW Saturday, USA). A bidder with no open window cannot bid above
    sublicense value.
  - Consolidation events (Paramount and WBD) remove a bidder.
- **Renewal step-ups for calibration**:
  - SEC top tier ×5.5 (2020)
  - Big Ten ×2.5 (2022)
  - Big 12 +73% (2022)
  - CFP ×2.8 (2024), then +27% for the 24-team format (2026)
  - Pac-12: $250M/yr down to about $60-80M (8 schools)
  - MW: $45M/yr, then undisclosed
  - Next-cycle baseline 0-3%/yr real growth; "no windfall".
- **Streaming offers**: about 20-40% higher headline value but 30-60% of it contingent on
  subscribers (Apple), with a −10 to −20 brand-exposure penalty for streaming-only. AI
  presidents should reject a deal with less than about 50% guaranteed money unless the
  alternative is collapse.
- **Pro rata**: P4 deals with the clause pay the average share per added school. The
  commissioner chooses the newcomer's share (30-100%), and the gap funds a redistribution
  pool (ACC model). G6 deals without the clause trigger renegotiation, about −10% per lost
  brand school.
- **Look-in events**: e.g. "ESPN option decision" (ACC 2025), "partner wants more games
  for the 9th conference game" (SEC 2026), "title game eliminated: negotiate compensation
  with FOX/CBS" (Big Ten 2027), "network resells your game" (NBC → FOX).
- **Negotiation minigame**: hire an advisor (Octagon-type; +5-10% value, fee about 1-2%).
  Choose early renewal (certainty, about −10% vs market) or wait for the window (variance
  plus a competition bonus). Delay has a 'Kliavkoff risk': each month without a deal adds
  a member-defection probability.

## Notable gaps / low-confidence items

- Big East, WCC, A-10, Sun Belt, American, Notre Dame and NCAA deal values and terms;
  BTN/SEC Network/ACC Network subscriber and revenue numbers; Big Ten per-network split;
  TNT's CFP sublicense terms; the ACC's current value.
- MAC's post-2027 deal (it may have been announced after my last data); MW and Pac-12
  dollar values.
- 2026-season viewership; conference sponsorship revenue; exec titles (ESPN's Durant and
  Dawson, CBS's Weinberg, CW's Miller, NBC's Cordella); Disney CEO succession; WBD sale status.
