# Commissioner — Architecture Plan

A deep, single-player management sim: you are the commissioner of an NCAA Division I
conference. Strategy, politics, money and career, Football-Manager style. Personal use
only, so real names are used throughout.

## 1. Repository layout

```
/research/            Research notes (markdown, sources cited) + SCHEMA.md
/data/                Seed data from the research pass (JSON, sourced). Read-only at runtime.
  schools/*.json      ~400 D-I schools (FBS + key non-FB full detail, FCS + other D-I light)
  conferences*.json, media_deals.json, cfp.json, bowls.json, commissioners.json, ...
/config/              Every tunable number (JSON): economy, media, sim, events, ai,
                      career, governance, legal. Balance passes only edit these.
/src/engine/          Pure TypeScript simulation. No React, no DOM, no Date.now(),
                      no Math.random(). Runs in browser, Node and a Web Worker.
/src/ui/              React + Vite app (screens, components, Zustand store).
/scripts/             Node CLIs (tsx): seed validation, balance runner, data reports.
/tests/               Vitest unit + integration tests for the engine.
```

## 2. Engine design

**State.** One serializable `GameState` (plain JSON): world (schools, conferences,
people, contracts, media deals), the player (commissioner, career, inbox), the calendar,
news, history ledgers (finances by year, membership changes, standings archive) and the
RNG state. Saving is `JSON.stringify(state)` plus a schema version for migrations.

**Determinism.** A seeded PRNG (sfc32) lives inside the state. Every random draw goes
through `rng` in the state, so the same seed plus the same player inputs gives the same
world. Each subsystem gets a forked stream (`rng.fork('season')`), so adding a draw in
one system doesn't reshuffle another.

**Turn loop.** `advanceMonth(state, config) → { state, report }`. Each month runs ordered
phases:

1. Resolve pending player actions (votes, negotiations, pitches)
2. Scripted calendar beats for that month (table below)
3. Systems tick: finance → media → season → programs → governance → realignment AI →
   legal → career → external forces → events
4. News and inbox generation from that month's emitted engine events
5. Ledger snapshots for charts

Systems talk through an **event bus of typed domain events**
(`SchoolJoinedConference`, `MediaDealSigned`, `VoteFailed`, `LeakPublished`...). News,
inbox, reputation and the history log all consume these events. No system formats text.

| Month | Scripted beats |
|---|---|
| Jan | CFP national championship, NCAA Convention (legislation votes), coaching carousel settles |
| Feb | Signing day, budget season starts |
| Mar | Conference tournaments, Selection Sunday, March Madness (NCAA units awarded) |
| Apr | Final Four, spring portal window |
| May | Spring meetings (board votes on bylaws, distribution model, expansion), commissioner review prep |
| Jun | Board annual review of the commissioner, fiscal year close |
| Jul | **Jul 1:** membership changes take effect and the fiscal year starts; distributions paid; media days |
| Aug–Nov | Football season simulated week by week, summarized monthly; rankings; hot-seat moves |
| Dec | Conference championship games, CFP selection, bowls, early signing, portal window |

**Season sim (results level).** Each program has latent strength ratings that drift.
Game win probability is a logistic of rating difference plus home field plus noise.
The engine generates full schedules from the conference format (8 or 9 games, divisions,
pods or none, protected rivals) plus non-conference games and alliance games. It tracks
standings, a CFP committee ranking model (record, strength of schedule, brand bias),
CFP selection under the configured format by year (12 teams now, then whatever format the
research shows), bowls by tie-in, a basketball NET-style rating, the 68-team bracket,
units by conference, and a simplified all-sports cup.

**Money.** Conference revenue: media deals, CFP share, NCAA units, bowls, championship
events, sponsorships, conference network and associate members. Minus conference
expenses (office, officiating, championships, legal). Distributed to schools by the
league's model: equal, tiered, performance or viewership-weighted. School budgets drive
House cap payments, coaching and facilities. Schools that can't afford the cap fall behind.

**Media valuation.** Each school has TV draw from brand, market TV homes, football rating
and fan base. Each network values a conference from the top inventory it gets (games by
window and tier), with a premium on marquee matchups, linear decline, streaming appetite
and competition between bidders. This one model powers renewal negotiations, pro-rata
clauses, and the realignment question "does adding X grow the pie per school?"

**Negotiation minigame.** An RFP or auction among interested networks, then
multi-issue offer/counter rounds. The issues are AAV, term, escalator, inventory windows,
exclusivity, streaming share, and network carriage. The network AI has a hidden reservation
value and patience. Your Media Negotiation and Commercial stats, league brand and the number
of bidders shift outcomes. Bluffing and walk-aways carry real risk.

**Governance.** Each board member (a real president) has priorities over money, academics
(AAU), geography and travel, tradition, Olympic sports and risk. Each also has a bloc and a
relationship with you. Vote probability is a logistic of their utility. You can lobby
(spend action points), trade favors (IOUs the AI remembers) and burn political capital.
Thresholds come from each league's bylaws in seed data.

**Realignment AI.** Rival commissioners are utility agents with real names and
personality vectors (aggression, caution, media savvy...). They scout accretive targets
(value added vs. per-school dilution), run secret talks (leak risk), pitch, and hold
votes on both sides. They also handle network approval and pro-rata, exit fees, damage
fees and lawsuits. Schools weigh payout, exposure, CFP access, travel and geography,
academic fit, rivalries, exit cost, GOR lock-in and state political pressure. You play the
same flow and defend with GOR extensions, bonuses and alliances. Founding a conference is
a guided wizard built on the same pieces (charter members, NCAA and FBS rules, HQ, staff,
officiating, sites, capital, media deal, CFP access).

**Events.** Data-driven templates in `/config/events/`. Each template has trigger
conditions, a base probability, attribute and trait modifiers, and choices with outcome
distributions. Your attributes, traits and reputations shift the odds. Outcomes apply
effects such as reputation, money, ratings, votes, news and legal cases.

**Career.** Contract (term, base, bonuses, buyout), a June review with a hot-seat
meter, and firing. Vacancies across all D-I conferences come from a hazard model on AI
commissioners. Search firms contact you, then you interview and get offers. Offers can be
used as leverage, you can be poached mid-contract, and you can take exits to pro leagues,
the NCAA, networks, AD jobs or retirement. Legacy score and career history are tracked.

**Action points.** Stamina sets how many meaningful actions you get each month
(meetings, calls, lobbying, scouting). Traits modify it: Micromanager gets more points
but carries burnout risk. This is the FM-style constraint on "do everything every month".

## 3. UI

React 18 + TypeScript + Vite, **Zustand** store wrapping the engine. The engine runs in a
**Web Worker** (Comlink), so "sim to date" doesn't freeze the UI. Dark, dense FM-style
theme using CSS variables.

Screens:
- Dashboard (key stats, next beats, alerts)
- Inbox and News (outlet and reporter, rumor flag)
- Conference (members, standings, finances)
- Schools (sortable or filterable table of all D-I schools) and School profile
- Board (members, blocs, pending votes)
- Media (deals, expirations, negotiation room)
- Finances (charts over time)
- Realignment (targets, talks, threats)
- Map (conference footprints)
- Postseason (CFP bracket, bowls, March Madness)
- Career (contract, reviews, offers, legacy)
- Calendar
- Settings and Saves

Libraries:
- TanStack Table for tables
- Recharts for charts
- d3-geo + us-atlas TopoJSON for the SVG map (school dots and footprint hulls)
- `idb` for IndexedDB saves with autosave every month, plus export and import of
  `.commissioner.json` save files

## 4. Data pipeline

`scripts/validate-seed.ts` checks every `/data` file against **zod** schemas, checks
referential integrity (IDs in member lists, rivals and deals) and reports coverage gaps.
Scenario builders (`scenario2026.ts`, later `scenario2010.ts`) turn seed data plus config
into an initial `GameState`. Where a real person is unknown (or later, when someone
retires), replacements are generated from a configurable name pool.

## 5. Testing & balance

- Vitest covers RNG determinism, distribution math, exit fee schedules, vote thresholds,
  CFP selection, the scheduler, the negotiation solver, save round-trips, and a full
  12-month smoke sim with a fixed seed and snapshot.
- `npm run balance -- --years 30 --runs 20 --seed 42` runs AI-only worlds and reports:
  - realignment moves per year
  - revenue spread (top vs bottom P4, P4 vs G6 ratio over time)
  - conference deaths (below 8 football members past the grace period, or dissolved)
  - commissioner turnover
  - CFP bid share by league
  - schools cutting sports

## 6. The opening world (from the research pass)

The default 2026–27 start already contains these live storylines from the real world.
Details and sources are in `research/VERIFICATION.md`.

- **CFP expands to 24 teams in 2027.** The five auto bids are the P4 champions plus the top G6
  team. P4 conference title games end after 2026, which costs leagues about $200M+ in
  title-game revenue. Notre Dame's top-12 guarantee also ends.
- **The Big 12 job is open.** Yormark leaves on Jan 31, 2027, and the board is running the search.
  This is a natural opening job for the player.
- **SEC v. LSU.** There is a federal lawsuit over pro-player eligibility, and presidents meet
  on Dec 3 about LSU's membership. Expulsion needs a 2/3 vote.
- **Protect College Sports Act.** It passed the Senate 77-22. The House can only act in the lame-duck
  session after the midterms.
- **MAC media deal.** The MAC's ESPN deal expires after 2026–27, so the negotiation is open at game start.
- **Realignment already in motion:**
  - JMU moves to the American on Jul 1, 2027, which leaves the Sun Belt at 13.
  - The Pac-12 sits at exactly 8 football members.
  - North Dakota State is in its FBS transition.
- **Big Ten private-capital deal.** The Big Ten–UC Investments deal ($2.4B for 10% of "Big Ten
  Enterprises" plus a GOR to 2046) is paused by Michigan and USC.
- **House revenue-sharing cap.** About $21.3M in 2026–27, rising 4% a year.

**Data confidence.** Membership, commissioners, CFP and top-line money figures are verified.
School-level detail is mostly model knowledge as of mid-2026 and flagged `confidence: "low"`:
leadership, budgets, ranks. The engine treats seed values as starting points.

## 7. Build phases (each playable and committed)

1. **Core:** data model, seed loading and validation, commissioner creation, monthly loop and
   calendar, basic finances, season results sim, dashboard, schools, conference and news
   shell, saves.
2. **Media & money:** media contracts and valuation, negotiation minigame, distribution
   models, CFP, bowls and NCAA units, House revenue sharing, finance charts.
3. **Politics:** boards and votes, reputation tracks, event engine and templates, news
   feed with outlets and rumors, inbox, CSC and external forces.
4. **Realignment:** AI poaching, the player's poaching flow, exit fees, GOR and lawsuits,
   defending, founding a new conference.
5. **Career:** contracts, reviews and hot seat, firing, job market, search firms,
   interviews, exits, legacy.
6. **Polish:** 2010 historical start (scripted real moves as optional "history" events),
   map view, charts, balance passes with the 30-year script, sim-to-date, Web Worker.
