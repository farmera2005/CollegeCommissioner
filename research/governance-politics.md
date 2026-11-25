# Governance, Politics and External Forces (as of 2026-11-25)

Owner: governance-politics agent. Files: `data/governance.json`, `data/external_forces.json`,
`data/event_seeds.json` (shape documented in `research/events.md`).

**Method and limits.** Facts from late 2025 and 2026 come from web searches run on 2026-11-25. WebFetch could not reach outside hosts (DNS blocked), and the shared web-search budget ran out partway through, so these were **not** verified: MWC and AAC board chairs, the NCAA D-I Board and Cabinet chairs, the CFP executive director and the 2026-27 format, the Bediako outcome, and details of the January 2026 point-shaving indictment. Each is marked `"confidence": "low"`. Everything before 2025 comes from well-documented history (Wikipedia and major-outlet links).

## File shapes

### `governance.json` (object)
```
{ asOf, notes,
  conferenceBoards: [{ id, conference, boardName, chair{id,name,school,title,since}, viceChair?, previousChair?,
                       executiveCommittee?, commissioner{id,name,since,contractThrough?,notes?},
                       votingRules{admission, admissionFraction, membershipTermination?, terminationFraction?, notes},
                       votingBlocs:[{id,name,members[schoolIds],interests,cohesion 0-1,leverage 0-1,notes?}],
                       adCouncil{name,structure}, recentGovernanceEvents[{date,event}], sources }],
  ncaa:{ president, boardOfGovernors, d1BoardOfDirectors, d1Cabinet, d1Council, convention, autonomy{2014,2022-23,2024-26},
         rules2025_26:[{id,summary,sources}], litigationPosture, sources },
  collegeSportsCommission:{ ceo, foundingConferences, nilGo{operator,launched,threshold,standard,stats[]},
         participationAgreement, arbitration[], enforcementFramework, enforcementActions2025_26[], conferenceLevelEnforcement[], sources },
  cfpGovernance:{ boardOfManagers, managementCommittee{members[]}, executiveDirector, mou2024, format, sources },
  sources }
```
`cohesion` (how reliably the bloc votes together) and `leverage` (how much the bloc moves the outcome) are **design estimates** for the voting model, not sourced facts.

### `external_forces.json` (array)
`{ id, type: legislation|lawsuit|executive-action|regulatory|labor, name, status, timeline[{date,event}], summary, stakeholders[], gameImpact{mechanic, probabilities{}, effects{}, commissionerLevers?}, confidence?, note?, sources[] }`, 34 records. Probabilities are tunable design estimates, made from the current status.

## Key findings

### Federal legislation: the brief is out of date
- **SCORE Act (H.R. 4312)** advanced through the House Education & Workforce and Energy & Commerce committees in July 2025. House leaders pulled it from the floor hours before a December 2025 vote ([The Hill](https://thehill.com/policy/sports-gaming/5884675-score-act-house-cbc-ncaa/)), then Speaker Johnson canceled a second vote in May 2026. The CBC opposed it, co-sponsors Figures and Bynum withdrew, and Reps. Roy and Donalds objected ([FOS](https://frontofficesports.com/as-score-act-vote-gets-canceled-a-new-college-sports-bill-may-emerge/), [Sportico](https://www.sportico.com/law/analysis/2026/score-act-vote-congress-ncaa-rules-1234899628/)). **Effectively dead.**
- **Protect College Sports Act of 2026 (S. 4668 / H.R. 9137)** is the Cruz-Cantwell-Schmitt-Coons compromise, introduced late May 2026. Commerce Committee 19-9, cloture 70-21 (2026-09-22), and **passed the Senate 77-22 on 2026-09-28** ([Senate Commerce](https://www.commerce.senate.gov/press/rep/release/senate-overwhelmingly-passes-protect-college-sports-act/), [ESPN](https://www.espn.com/college-sports/story/_/id/50056206/us-senate-votes-77-22-pass-protect-college-sports-act), [NPR](https://www.npr.org/2026/09/28/nx-s1-5977851/protect-college-sports-act-senate-bill-vote)). Main terms:
  - conditional antitrust safe harbor (tied to staying under the cap) for the NCAA, conferences, schools and the CSC ([Sportico](https://www.sportico.com/leagues/college-sports/2026/protect-college-sports-act-senate-passes-antitrust-1234945916/), [Norton Rose](https://www.nortonrosefulbright.com/en/knowledge/publications/4cbfd2a0/protect-college-sports-act-update-the-senate-passes-the-protect-college-sports-act))
  - national NIL standard that preempts state laws, effectively endorsing NIL Go; agents register with a state, fees capped at 5%
  - 5-year eligibility and one free transfer
  - **neutral on employee status** (Sec. 122), with a 24-member study commission ([Cozen](https://www.cozen.com/news-resources/publications/2026/protect-college-sports-act-of-2026-s-4668-the-bill-passed-the-senate-so-what-comes-next-), [Swimming World](https://www.swimmingworldmagazine.com/news/news/a-new-deal-for-college-sports-how-the-protect-college-sports-act-would-work/))
  - Title IX savings clause and a ban on cutting women's or Olympic sports
  - **P4 membership cap of 20** (raised from 19 by the Moody amendment), and **a school moving between P4 leagues must spend 3 years as an independent**, a rule that expires 6 years after enactment ([Yahoo exclusive](https://sports.yahoo.com/articles/exclusive-fsu-miami-clemson-unc-200833994.html), [Cardinal News](https://cardinalnews.org/2026/10/03/the-protect-college-sports-act-set-out-to-stabilize-conference-membership-but-the-acc-is-still-at-risk-of-being-picked-apart/))
  - The retention or Olympic fund figures conflict: Husch Blackwell says $22.5M plus $5M, Sportico says a cap effectively up to $48.8M ([Husch Blackwell](https://www.huschblackwell.com/newsandinsights/executive-summary-protect-college-sports-act-of-2026-september-17-2026-amendment)).
- **House status.** Scalise has scheduled floor action for **the week of 2026-12-08** on a revised text: a 22-school cap, and schools with $50M+ media revenue may not use student fees for athletics ([ESPN](https://www.espn.com/college-sports/story/_/id/50545220/protect-college-sports-act-revised-donald-trump-voices-support), [WaPo](https://www.washingtonpost.com/sports/2026/11/20/congress-college-sports/816f43ce-e547-11f1-a99e-b3e3805c6b8b_story.html), [CBS](https://www.cbssports.com/college-football/news/house-gop-protect-college-sports-act/)). Republicans hold a 218-214 lame-duck majority. Government funding runs out 12/11, and the last scheduled day is 12/17. **Democrats swept the 2026-11-03 midterms**, and FOS calls the bill's chances "nearly nonexistent" ([FOS](https://frontofficesports.com/article/college-sports-bill-in-peril-after-democrats-sweep-midterm-elections/), [Bloomberg Gov](https://news.bgov.com/bloomberg-government-news/college-sports-bills-chances-in-congress-dwindle-after-midterms)). Any House amendment sends it back to the Senate, and if it lapses it must be reintroduced in a more athlete-friendly Congress.
- **ACC exit lobby.** FSU, Miami, Clemson and UNC asked Congress for a 22-school cap and no independence period. Miami president Joe Echevarria: "You cannot lock us into a conference" ([Yahoo](https://sports.yahoo.com/college-football/article/college-football-realignment-protect-college-sports-act-bill-drama-miami-president-acc-sec-big-ten-122659182.html)).

### Executive branch
- **EO 14322 "Saving College Sports" (2025-07-24)** directs agencies (Labor, NLRB, DOJ, FTC) on athlete status and litigation, bans third-party pay-for-play, and protects women's and Olympic sports ([UCSB text](https://www.presidency.ucsb.edu/documents/executive-order-14322-saving-college-sports), [WH fact sheet](https://www.whitehouse.gov/fact-sheets/2025/07/fact-sheet-president-donald-j-trump-saves-college-sports)). The Saban and Cody Campbell commission idea from May 2025 was replaced by this order.
- **EO 14400 "Urgent National Action to Save College Sports" (2026-04-03)**: Sections 3-6 took effect 2026-08-01. It calls for a five-year participation limit, a bar on former pros returning, and transfer limits "subject to court orders", and it links federal grant and contract "responsibility" determinations to NCAA-rule compliance ([WH text](https://www.whitehouse.gov/presidential-actions/2026/04/urgent-national-action-to-save-college-sports/), [Wikipedia](https://en.wikipedia.org/wiki/Executive_Order_14400), [Bricker](https://www.bricker.com/insights/publications/a-new-presidential-executive-order-to-save-college-sports-why-it-matters-for-campus-decision-makers-now)). Morgan Lewis: the White House "may have reached the end of its authorities."

### NCAA
- President **Charlie Baker** (since 2023-03-01).
- **5-in-5 age-based eligibility** adopted unanimously by the **D-I Cabinet on 2026-06-23**. Mandatory for 2027-28 enrollees, optional for current athletes. Waivers largely gone. The HS class of 2022 is excluded ([PBS/AP](https://www.pbs.org/newshour/nation/ncaa-panel-approves-new-eligibility-rules-giving-division-i-athletes-5-years-to-play-5-seasons), [SportsRecruits](https://sportsrecruits.com/resources/ncaa-eligibility-and-rules/age-based-eligibility-model)).
- That exclusion led to **Ohio Gov. DeWine's EO 2026-04D (2026-10-13)** and the **NCAA's federal suit against DeWine** (S.D. Ohio), with the Ohio Supreme Court stepping into *Borovicanin v. NCAA* ([ESPN](https://www.espn.com/college-sports/story/_/id/50196596/ncaa-sues-ohio-gov-eligibility-order-5th-year-athletes), [Sportico](https://www.sportico.com/law/analysis/2026/ncaa-sues-dewine-says-eligibility-order-unconstitutional-1234952392/)).
- Governance has moved from the old ADs-led D-I Council to the **D-I Cabinet**. The 2014 autonomy grant to the "Power 5" (65 schools plus ND) is the base for today's P4 autonomy and the House-settlement rulebook.

### College Sports Commission
- **CEO Bryan Seeley** (ex-MLB EVP for legal and investigations; named May 2025) ([ESPN](https://www.espn.com/college-sports/story/_/id/45468012/mlb-exec-bryan-seeley-ceo-new-college-sports-commission)). Formed by the P4.
- **NIL Go (Deloitte)** launched 2025-06-11 and reviews third-party deals of $600 or more for "valid business purpose" and fair market value. The first report's $79.8M was corrected to $35.4M (6,090 deals) ([FOS](https://frontofficesports.com/nil-go-corrects-its-data-from-80m-in-deals-cleared-to-35m-blames-deloitte/)). By mid-2026: about $355M cleared and nearly $90M rejected ([ESPN](https://africa.espn.com/college-sports/story/_/id/49308194/nil-clearinghouse-rejected-90m-deals)). FOS on 11/22 said more than 1,000 deals worth $56M had been rejected, which conflicts with ESPN.
- **Participation agreement.** Schools waive suits, accept arbitration and accept CSC penalties. It is active only if all 68 sign. **The Big 12 was the first fully signed conference (May 2026)**. It is still not universal, and some state AGs object ([ESPN](https://www.espn.com/college-football/story/_/id/48913026/big-12-first-power-conference-full-csc-participation), [Mondaq](https://www.mondaq.com/unitedstates/sport/1772728/uniformity-or-uncertainty-the-college-sports-commissions-effort-to-implement-university-participation-standards)).
- **Arbitration.** The CSC beat Nebraska football players (2026-05-11) ([KOLN](https://www.1011now.com/2026/05/12/college-sports-commission-wins-key-nil-arbitration-case-brought-by-nebraska-football-players/)), and a Georgia matter was decided 2026-06-10.
- **Enforcement.** An August 2026 memo described long-term cap-evasion investigations. In October, 5-10 P4 programs were under inquiry. On 11/11 there were more than a dozen active cases, a staff of 30, and **no penalties yet** ([ESPN](https://www.espn.com/college-football/story/_/id/50142371/reports-watchdog-eyes-nil-violations-5-10-power-4-schools), [FootballScoop](https://www.footballscoop.com/2026/10/08/5-10-power-four-programs-including-playoff-contenders-reportedly-under-investigation-for-nil-related-violations)).
- **Conferences moving faster than the CSC.** The SEC adopted standardized contracts and is circulating a tiered roster-spend "luxury tax" (under 1% above about $50.5M, up to 10% above $70.5M) ([Yahoo](https://sports.yahoo.com/articles/sec-proposed-cap-policy-league-001851563.html)). The Big Ten reportedly set a combined $49M limit on 10/28 (low confidence).

### Conference boards (2026-27)
| Conf | Board chair | Notes |
|---|---|---|
| SEC | Donde Plowman (Tennessee), Exec. Committee president 2025-27 ([UTK](https://chancellor.utk.edu/2025/06/30/plowman-begins-term-as-sec-executive-committee-president/)) | Admission needs 3/4. **Termination needs 2/3 of the other 15**, with an LSU vote on **2026-12-03** ([ESPN](https://www.espn.com/college-football/story/_/id/49869481/sec-files-amendment-authority-expel-lsu-conference), [CBS](https://cbssports.com/college-football/news/sec-lsu-expulsion-vote-rj-luis-will-wade-lane-kiffin)) |
| Big Ten | Pamela Whitten (Indiana), reported August 2026 (low). Darryll Pines (Maryland) chaired through about June 2026 ([Big Ten](https://bigten.org/article/60116/)) | Petitti extended to June 2033, unanimous, 2026-08-26 ([NFP](https://www.nationalfootballpost.com/big-ten-extends-contract-of-commissioner-tony-petitti-to-2033)). $2.4B UC Investments deal paused by Michigan and USC ([ESPN](https://www.espn.com/college-sports/story/_/id/47003108/opposition-michigan-usc-pauses-24b-big-ten-deal)) |
| Big 12 | Douglas Girod (Kansas) | **Yormark leaving 2027-01-31**, national search under way, Cody Campbell rumored ([KCTV](https://www.kctv5.com/2026/10/30/big-12-commissioner-brett-yormark-step-down-january-2027/), [FOS](https://frontofficesports.com/article/brett-yormark-stepping-down-as-big-12-commissioner-after-4-years/)) |
| ACC | Tim Sands (Virginia Tech). Vice chair Joan Gabel (Pitt) ([ACC](https://theacc.com/news/2026/7/27/general-acc-announces-2026-27-conference-leadership.aspx)) | Admission 3/4 (2023 vote was 12-3). FSU and Clemson settled March 2025 |
| Pac-12 | Kelly Damphousse (Texas State). Vice chair Amy Parsons (Colorado State). One-year rotation ([TXST](https://news.txst.edu/accolades-and-achievements/2026/txst-president-kelly-damphousse-named-pac-12-board-of-directors-chair.html)) | Gould extended through 2030-31 ([Pac-12](https://pac-12.com/news/2026/6/15/general-pac-12-board-of-directors-extends-contract-of-commissioner-teresa-gould.aspx)). Rebuilt league live 2026-07-01 |
| MWC | not verified | Nevarez. Litigation with the Pac-12 and its departing schools |
| AAC | not verified | Pernetti |

### State-level forces
Members now escape conference discipline through **home-state courts, AGs and governors**: Louisiana courts and AG Liz Murrill shielding LSU, Ohio's governor's order, and state anti-enforcement and NIL laws (TN, TX, LA, AR and others) that conflict with CSC agreements. History shows legislatures dictating realignment: Texas 1994 (Baylor and Texas Tech into the Big 12), Virginia 2003 (VT into the ACC), Texas and Oklahoma hearings in 2021, WA and OR outrage in 2023, Florida and NC in 2023-24 ([SWC](https://en.wikipedia.org/wiki/Southwest_Conference), [2021-24 realignment](https://en.wikipedia.org/wiki/2021%E2%80%932024_NCAA_conference_realignment)).

### Labor and lawsuits
- *Johnson v. NCAA*: the Third Circuit (2024-07-11) said athletes can be FLSA employees and remanded the case ([opinion](https://www2.ca3.uscourts.gov/opinarch/221223p.pdf)). Still unresolved.
- Dartmouth union: NLRB regional ruling February 2024 and a 13-2 vote, then the petition was withdrawn 2024-12-31 ([NLRB case](https://www.nlrb.gov/case/01-RC-325633)). Dormant.
- *House v. NCAA*: approved 2025-06-06. Title IX objectors' appeals are pending (low confidence on status).
- Prediction markets (Kalshi, Polymarket, Robinhood) offer college contracts nationwide, and the NCAA is pushing the CFTC to restrict them (2026 status low confidence).

## Corrections to the brief
1. **"SCORE Act status in House/Senate."** SCORE never reached a floor vote (pulled in December 2025 and May 2026). The live vehicle is the **Senate-passed Protect College Sports Act (77-22, 2026-09-28)**, with a House lame-duck vote planned for the week of 12/8 and poor odds after the Democratic midterm sweep.
2. **"Tuberville/Manchin PROTECT, Cruz bill."** PROTECT (2024) died with the 118th Congress. Cruz's draft became the PCSA. "College Athlete Protection Act" is not a live bill. The relevant names are SCORE, PCSA and Steube's EO-codification bill.
3. **"White House commission / Saban."** The Saban and Campbell commission was floated (May 2025) and shelved. Instead there were **two** EOs: 14322 (July 2025) and **14400 (April 2026)**. The brief misses the second.
4. **"Five-in-five debates."** It is no longer a debate. The **D-I Cabinet adopted 5-in-5 on 2026-06-23**, effective 2027-28.
5. **NCAA "D-I Council."** Legislative authority now sits mainly with the **D-I Cabinet**. The Council is historical.
6. **Missing from the brief.** **SEC v. LSU** (federal suit filed 2026-09-03; **expulsion vote 2026-12-03**), **Big 12 commissioner Brett Yormark leaving 2027-01-31**, **Petitti extended to 2033**, Gould extended to 2031, the **NCAA suing Ohio's governor**, and the **PCSA's 20/22-member cap and 3-year independence penalty** (the most important realignment constraint for the game).
7. **"Big Ten-Big East antitrust? CFP antitrust?"** No such suits were found. The relevant antitrust items are the PCSA safe harbor, Alston, House, and transfer-rule litigation. Pac-12 v. MWC is a contract and restraint fight over poaching penalties.
8. **Brief's faction list.** Add the **Michigan-USC private-capital veto bloc** (Big Ten) and the **FSU/Miami/Clemson/UNC PCSA lobby** (ACC). The "Magnificent Seven" (2023) is still the right label for the wider ACC dissident group. The FSU/Clemson litigation was settled in March 2025.
9. **Revenue-share cap.** $20.5M in 2025-26. Reported as about $21.5M-$21.6M in 2026-27 (sources vary).

## Game-model implications

### 1. Political capital (PC) mechanic
- The commissioner has a **PC pool (0-100)** for each constituency: `presidents` (one score per member), `ADs`, `media partners`, `Washington`, and one per footprint state.
- PC is **earned** by delivering revenue, winning CFP bids, handling crises well, and backing a member in a fight with the NCAA or CSC.
- PC is **spent** on forcing votes, punishing members, lobbying Congress or legislatures, and overruling ADs.
- **Suggested deltas:** a successful vote you sponsored gives +3 per member who voted yes and -5 per member on the losing side. Disciplining a member costs -15 with that member and -4 with its bloc, and gains +3 with rival blocs. A public fight with a governor costs -10 with that state and +5 with presidents if you win in court.
- PC decays 10% per year toward 50 (relationships fade). President turnover (about 15% per member per year in 2026, `federal-pressure-on-universities`) resets that member's PC to 50 ± `presidentialRelations` / 5.

### 2. Voting-bloc model
- Each school has a base disposition on an issue (from its interests). Bloc membership pulls toward the bloc leader with weight `cohesion`.
- `P(yes_i) = sigmoid( base_i + cohesion_b * (leaderStance_b) + 0.03 * (PC_i - 50) + 0.02 * (presidentialRelations - 50) + issueSpecific )`
- Then apply thresholds from `votingRules`: admission 0.75 (SEC/ACC), termination 0.667 of the other members (SEC), and unanimity for private-capital-style deals (Big Ten precedent: **one holdout kills the deal about 70% of the time**).
- Leagues avoid votes that might fail. Give the commissioner a **"whip count" preview** (accuracy scales with `network`), and let a failed public vote cost -10 PC with every member.

### 3. Rogue-member escalation ladder (SEC v. LSU template)
1. Private warning
2. Fine or withheld distribution (Big 12's 25% Baylor withholding, 2017)
3. Federal suit (needs `legalGovernance`)
4. Termination vote (2/3)

At each step, roll for a state-court shield, an AG stepping in, or a federal (EO 14400) funding nudge. Suggested: P(member backs down) = 0.35 + 0.1 × step + 0.004 × (legalGovernance - 50) − 0.15 if the member's statePoliticalPressure is above 70.

### 4. Legislative tracker
Run the PCSA as a state machine across game-weeks: `Senate-passed → House floor (p=0.15 Dec-2026) → Senate concurrence (0.5) → enacted`. If it lapses, `reintroduced 2027` with an athlete-friendlier tilt (P(employee/CB language) = 0.35).

If enacted:
- hard conference cap of 20/22
- a 3-year independence penalty for P4-to-P4 moves (set the P4 raid probability to 0.25x for 6 years)
- CSC penalties hold up in court about 1.6x more often
- shield-law defiance about 0.2x
- cutting Olympic sports is prohibited

### 5. Enforcement credibility meter
A global "CSC credibility" value of 0-100, starting at about 35 because no penalties have been issued yet. It rises when penalties are upheld and falls when the CSC loses arbitrations or courts. Conference-level cap policies (SEC luxury tax, Big Ten combined limit) let a commissioner **substitute league enforcement** when the CSC is weak, at a PC cost with high spenders.

### 6. Calendar hooks for the 2026-27 start
- 2026-12-03: SEC LSU vote
- Week of 2026-12-08: PCSA House vote
- 2027-01-03: new Congress
- 2027-01-31: Yormark leaves, Big 12 vacancy (an NPC commissioner change or a player job opening)
- 2027-08: 5-in-5 becomes mandatory for new enrollees
