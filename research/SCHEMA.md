# Seed Data Schema & Research Conventions

All research agents follow this file. The game engine loads `/data/**/*.json` directly, so
**field names, IDs and units must match exactly**.

## General rules

- "As of" date for all current facts: **2026-11-25** (the 2026–27 season is in progress).
- Money: whole US dollars (`165000000`, not `"$165M"`). Years: integers. Dates: `YYYY-MM-DD`.
- Every JSON record carries `"sources": ["https://..."]` (1+ URLs). Prefer primary sources
  (conference/school releases, 990s, court filings) then major outlets (ESPN, The Athletic,
  Front Office Sports, Sportico, CBS, Yahoo, USA Today, On3, Athlon, AP).
- If a fact is uncertain or could not be verified, still give your best value and add
  `"confidence": "low"` (default is high, omit the field) plus a short `"note"`.
- Unknown values → `null`, never invented filler.
- Each JSON file is either an array of records or an object with a top-level `"asOf"` and
  data keys. Validate with:
  `node -e "JSON.parse(require('fs').readFileSync('<file>','utf8'))"`
- Research markdown (`/research/*.md`): concise notes with inline source links, a
  **"Corrections to the brief"** section where reality differs from the design brief, and a
  **"Game-model implications"** section with suggested mechanics/tunable numbers.

## Canonical IDs

IDs are lowercase hyphenated slugs. **Use these exact IDs** in every file (member lists,
rivals, realignment timelines, etc.). For schools not listed, build a slug from the common
short name (e.g. `north-dakota-state`, `montana-state`, `south-dakota-state`).

### Conference IDs
`sec`, `big-ten`, `big-12`, `acc`, `pac-12`, `mountain-west`, `american`, `cusa`, `sun-belt`,
`mac`, `independent` (FBS independents), `big-east`, `wcc`, `a10`, `big-sky`, `caa`, `mvfc`
(Missouri Valley Football), `mvc` (Missouri Valley, non-football), `socon`, `southland`,
`swac`, `meac`, `ivy`, `patriot`, `nec`, `pioneer`, `big-south-ovc` (football), `big-south`,
`ovc`, `uac` (United Athletic Conference, football), `asun`, `wac`, `summit`, `horizon`,
`maac`, `america-east`, `big-west`, `atlantic-sun`→use `asun`. Historical only:
`pac-10`, `wac-2010`, `big-east-2010` (the pre-2013 football-playing Big East whose charter
became the American), `cusa-2010`, etc. Use `<id>-2010` whenever a 2010 conference's
membership/identity differs enough that lineage matters; describe lineage in notes.

### FBS school IDs (2026–27)
- SEC: `alabama`, `arkansas`, `auburn`, `florida`, `georgia`, `kentucky`, `lsu`,
  `mississippi-state`, `missouri`, `oklahoma`, `ole-miss`, `south-carolina`, `tennessee`,
  `texas`, `texas-am`, `vanderbilt`
- Big Ten: `illinois`, `indiana`, `iowa`, `maryland`, `michigan`, `michigan-state`,
  `minnesota`, `nebraska`, `northwestern`, `ohio-state`, `oregon`, `penn-state`, `purdue`,
  `rutgers`, `ucla`, `usc`, `washington`, `wisconsin`
- Big 12: `arizona`, `arizona-state`, `baylor`, `byu`, `cincinnati`, `colorado`, `houston`,
  `iowa-state`, `kansas`, `kansas-state`, `oklahoma-state`, `tcu`, `texas-tech`, `ucf`,
  `utah`, `west-virginia`
- ACC: `boston-college`, `cal`, `clemson`, `duke`, `florida-state`, `georgia-tech`,
  `louisville`, `miami-fl`, `nc-state`, `north-carolina`, `notre-dame` (non-football member),
  `pitt`, `smu`, `stanford`, `syracuse`, `virginia`, `virginia-tech`, `wake-forest`
- Pac-12: `oregon-state`, `washington-state`, `boise-state`, `colorado-state`,
  `fresno-state`, `san-diego-state`, `utah-state`, `texas-state`, `gonzaga` (non-football)
- Mountain West: `air-force`, `hawaii`, `nevada`, `new-mexico`, `san-jose-state`, `unlv`,
  `wyoming`, `utep`, `northern-illinois`, `north-dakota-state`, `grand-canyon` (verify each)
- American: `army`, `charlotte`, `east-carolina`, `fau`, `memphis`, `navy`, `north-texas`,
  `rice`, `south-florida`, `temple`, `tulane`, `tulsa`, `uab`, `utsa`, `wichita-state`
- Conference USA: `delaware`, `fiu`, `jacksonville-state`, `kennesaw-state`, `liberty`,
  `middle-tennessee`, `missouri-state`, `new-mexico-state`, `sam-houston`,
  `western-kentucky`
- Sun Belt: `app-state`, `coastal-carolina`, `georgia-southern`, `georgia-state`,
  `james-madison`, `marshall`, `old-dominion`, `arkansas-state`, `louisiana`, `ulm`,
  `south-alabama`, `southern-miss`, `troy`, `louisiana-tech`
- MAC: `akron`, `ball-state`, `bowling-green`, `buffalo`, `central-michigan`,
  `eastern-michigan`, `kent-state`, `massachusetts`, `miami-oh`, `ohio`, `toledo`,
  `western-michigan`, `sacramento-state`
- FBS independents: `uconn` (Big East otherwise)
- Big East: `butler`, `creighton`, `depaul`, `georgetown`, `marquette`, `providence`,
  `st-johns`, `seton-hall`, `uconn`, `villanova`, `xavier`

(The lists above are the brief's understanding — **verify**; if wrong, fix the data and
note it under "Corrections to the brief".)

### Other IDs
- Broadcasters: `espn` (incl. ABC, ESPN+, SEC Network, ACC Network), `fox` (incl. FS1, BTN
  stake), `cbs` (incl. Paramount+, CBS Sports Network), `nbc` (incl. Peacock), `tnt`
  (TNT Sports / Warner Bros. Discovery / truTV / Max/HBO Max), `cw`, `amazon`, `netflix`,
  `apple`, `youtube`, plus slugs for others (`scripps`, `bein`, `flosports`...).
- Conference networks: `sec-network`, `btn`, `acc-network`, `longhorn-network` (defunct), `pac-12-network` (defunct)…
- People: slug of full name, e.g. `greg-sankey`, `tony-petitti`.

## Record schemas

### `School` (files in `/data/schools/*.json`, each an array)
```jsonc
{
  "id": "ohio-state",
  "name": "The Ohio State University",
  "shortName": "Ohio State",
  "abbr": "OSU",                       // common TV-graphic abbreviation
  "mascot": "Buckeyes",
  "colors": ["#BB0000", "#666666"],    // hex, primary first
  "city": "Columbus", "state": "OH",   // USPS code
  "lat": 40.0017, "lon": -83.0197,      // campus
  "dma": { "name": "Columbus, OH", "rank": 32 },  // Nielsen 2025-26 DMA rank
  "control": "public",                 // "public" | "private"
  "religious": null,                   // e.g. "Catholic (Jesuit)", "Baptist", "LDS", "Methodist"
  "aau": true,
  "enrollment": 66000,                 // total headcount, most recent fall
  "usNewsRank": 41,                    // 2026 US News Best National Universities; null if not national
  "usNewsCategory": "national",        // "national" | "regional" | "liberal-arts" | null
  "endowmentUsd": 8000000000,          // system-level if that's what's reported (say so in note)
  "athletics": {
    "revenueUsd": 280000000,           // most recent reported athletic dept revenue
    "expensesUsd": 270000000,
    "fiscalYear": "FY2024",
    "revShareOptIn": true,             // opted into House settlement revenue sharing (true/false/null)
    "revShareNotes": "Paying full cap ($20.5M) in 2025-26",
    "stadium": { "name": "Ohio Stadium", "capacity": 102780 },
    "arena": { "name": "Value City Arena", "capacity": 18809 }
  },
  "conference": {
    "y2026": { "all": "big-ten", "football": "big-ten", "level": "FBS" },
    "y2010": { "all": "big-ten", "football": "big-ten", "level": "FBS" }  // 2010-11 season; level "FBS"|"FCS"|"D-II"|"none"
  },
  "ratings": {            // 1-100, see anchors below
    "football": 97, "mbb": 60, "wbb": 70, "olympic": 85,
    "brand": 99, "facilities": 95, "fanBase": 98,
    "boosterInfluence": 85, "statePoliticalPressure": 40
  },
  "ratingNotes": "FB: 2024 national champ, 2025 ... MBB: ... Olympic: Directors' Cup #x ...",
  "rivals": ["michigan", "penn-state"],   // school IDs, most important first
  "president": { "name": "Walter \"Ted\" Carter Jr.", "title": "President", "since": 2024 },
  "ad": { "name": "Ross Bjork", "since": 2024 },
  "headFootballCoach": { "name": "Ryan Day", "since": 2019 },   // null if no football
  "headMbbCoach": { "name": "Jake Diebler", "since": 2024 },
  "notes": "State politics / booster / storyline notes useful for events.",
  "sources": ["https://..."]
}
```

**Rating anchors (1–100):**
- `football`: 95+ perennial national-title contender; 85 regular CFP-level; 75 consistent
  Top-25; 60 mid-P4; 45 bottom-P4 / top-G6; 35 solid G6; 25 weak G6; 15 bottom FBS;
  FCS powers ~25–35; average FCS ~10–20.
- `mbb` / `wbb`: 95 blue blood + current title contender; 80 regular NCAA top-4 seed;
  65 regular tournament team; 50 bubble; 35 mid-major average; 20 low-major.
- `olympic`: from recent Learfield Directors' Cup finishes (Top 5 ≈ 95, Top 25 ≈ 75,
  Top 75 ≈ 50, unranked ≈ 20).
- `brand`: national TV draw / viewership & name recognition (Ohio State, Texas, Michigan,
  Alabama, Notre Dame ≈ 98–100; mid-P4 ≈ 55–70; G6 ≈ 20–40).
- `facilities`: stadium/arena/training facilities quality and recent investment.
- `fanBase`: attendance, alumni base, social following, travel.
- `boosterInfluence`: how much big donors/collectives drive decisions (e.g. Phil Knight at
  Oregon, Boone Pickens legacy at OK State, Texas Tech's Cody Campbell ≈ 90+).
- `statePoliticalPressure`: likelihood legislature/governor intervenes in conference
  decisions (Texas/Virginia/Florida/Oklahoma high; private schools usually low).

### `Conference` (`/data/conferences.json` FBS; `/data/conferences_nonfbs.json` others)
```jsonc
{
  "id": "sec", "name": "Southeastern Conference", "shortName": "SEC",
  "founded": 1932, "hq": { "city": "Birmingham", "state": "AL" },
  "division": "FBS",                  // "FBS" | "FCS" | "D1-non-football"
  "cfpTier": "P4",                    // "P4" | "G6" | null
  "commissioner": { "id": "greg-sankey", "name": "Greg Sankey", "since": 2015,
                    "background": "conference-deputy", "contractThrough": null },
  // background enum: former-ad, pro-league-exec, media-exec, attorney, conference-deputy,
  // politician, academic, other
  "members2026": {
    "full": ["alabama", "..."],          // full members (all sports)
    "footballOnly": [],                  // football-only affiliates
    "nonFootball": [],                   // full members that do not play football in this conf
    "affiliates": [{ "school": "x", "sports": ["wrestling"] }]
  },
  "pendingChanges": [{ "school": "x", "change": "join", "effective": "2027-07-01", "notes": "" }],
  "governance": {
    "board": "Board of Presidents and Chancellors",
    "expansionVoteThreshold": "3/4 of members",   // text + numeric below
    "expansionVoteFraction": 0.75,
    "bylawAmendmentThreshold": "2/3", "commissionerRemovalThreshold": null,
    "notes": ""
  },
  "exitTerms": {
    "noticeMonths": 12,
    "feeDescription": "...",
    "feeSchedule": [{ "fiscalYear": 2026, "amountUsd": 165000000 }],
    "grantOfRights": { "through": 2036, "description": "..." },
    "notes": ""
  },
  "distribution": {
    "model": "equal",                    // equal | tiered | performance | hybrid
    "latestFiscalYear": "FY2025", "totalUsd": 0, "perSchoolUsd": 0, "notes": ""
  },
  "football": {
    "conferenceGames": 9, "format": "no divisions, 3 protected rivals",
    "protectedRivalries": [["alabama","auburn"]],
    "championshipGame": { "venue": "Mercedes-Benz Stadium", "city": "Atlanta", "state": "GA", "through": 2031 },
    "schedulingAlliances": []
  },
  "mbbTournament": { "venue": "", "city": "", "state": "", "through": null },
  "wbbTournament": { "venue": "", "city": "", "state": "", "through": null },
  "springMeetings": { "city": "Destin", "state": "FL", "month": 5 },
  "mediaDays": { "city": "", "state": "", "dates2026": "" },
  "sources": []
}
```
Non-FBS conferences may leave football/governance sub-objects sparse but must have id, name,
division, hq, commissioner, members2026.full.

### Other files — free-form but array-of-records with `id` + `sources`
Each owning agent documents its file's shape at the top of its research note.

## File ownership (agents must only write their own files)

| Agent | Files |
|---|---|
| fbs-conferences | `data/conferences.json`, `data/calendar.json`, `research/conferences.md`, `research/legal-exit-fees-gor.md` |
| media-rights | `data/media_deals.json`, `data/broadcasters.json`, `data/conference_networks.json`, `data/sponsors.json`, `research/media-rights.md` |
| money-postseason | `data/distributions.json`, `data/cfp.json`, `data/ncaa_units.json`, `data/bowls.json`, `data/private_capital.json`, `data/house_settlement.json`, `research/revenue-cfp.md`, `research/private-capital.md`, `research/house-settlement.md` |
| career-people | `data/commissioners.json`, `data/commissioner_history.json`, `data/search_firms.json`, `data/career_paths.json`, `data/media_outlets.json`, `research/career.md` |
| governance-politics | `data/governance.json`, `data/external_forces.json`, `data/event_seeds.json`, `research/governance-politics.md`, `research/events.md` |
| history-founding | `data/alignment_2010.json`, `data/realignment_timeline.json`, `data/ncaa_rules.json`, `data/precedents.json`, `research/realignment-history.md`, `research/founding-a-conference.md` |
| schools-sec-b1g | `data/schools/sec.json`, `data/schools/big-ten.json` |
| schools-b12-acc | `data/schools/big-12.json`, `data/schools/acc.json` |
| schools-west | `data/schools/pac-12.json`, `data/schools/mountain-west.json` |
| schools-aac-cusa | `data/schools/american.json`, `data/schools/cusa.json` |
| schools-sbc-mac | `data/schools/sun-belt.json`, `data/schools/mac.json` |
| schools-nonfb | `data/schools/big-east.json` (incl. UConn), `data/schools/other-d1.json` |
| nonfbs-conferences | `data/conferences_nonfbs.json`, `data/schools/fcs.json`, `research/fcs-and-nonfbs.md` |

School agents also write a short `research/schools-<group>.md` (corrections + notable
storylines + sources that apply to many schools).
