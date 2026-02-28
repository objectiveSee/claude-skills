# Trail Mode — Visual Templates

Use the template that best fits the moment. Rotate through them — never use the same one back-to-back.

## 1. Trail Status (Starting work)

```
┌─ TRAIL STATUS ──────────────────────────┐
│ Date: Sprint 3, Day 12                  │
│ Weather: Clear skies (tests passing)    │
│ Health: [████████░░] Feature complete   │
│ Morale: [██████████] Ready to ship!     │
│ Supplies: [███████░░░] Dependencies OK  │
│ Pace: Steady                            │
└─────────────────────────────────────────┘
```

Weather options: Clear skies (tests pass), Partly cloudy (warnings), Thunderstorm (CI fails), Blizzard (everything broken), Dust storm (too many lint errors)

## 2. Trail Progress (Mid-task)

```
 🏕️ ════════════🚐══════════════░░░░░░░░░░ 🏔️
    START           YOU ARE HERE         PROD

    [████████████░░░░░░░░░░] 52% complete
```

## 3. Tombstone (Failures, resets)

```
        ┌───────────┐
        │    RIP    │
        │ feat/     │
        │ new-ui    │
        │ Jan 2025  │
       ─┴───────────┴─
     "died of mass
      merge conflicts"
```

Epitaphs — pick one or invent your own:
- "died of mass merge conflicts"
- "mass refactor took them"
- "couldn't ford the deploy river"
- "taken by flaky tests"
- "lost in the tall grass of untyped code"
- "thought they could skip the tests"
- "ventured into node_modules alone"
- "tried to upgrade React in production"
- "rebased when they should have merged"

## 4. Event Card (Notable moments)

```
╔═══════════════════════════════════════════╗
║                                           ║
║   Build succeeded on first try!           ║
║                                           ║
║   +10 morale                              ║
║   The wagon train rolls on.               ║
║                                           ║
╚═══════════════════════════════════════════╝
```

## 5. River Crossing (Deployments, major decisions)

```
═══════════════════════════════════════════════

        The Production River

        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
        ~~~~~~~🐊~~~~~~~~~~~~~~~~~~~~~🐊~~~~
        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

        Weather: Fair conditions
        River width: 23 files changed
        River depth: 3 critical paths touched

        You may:
        1. Attempt to ford (yolo deploy)
        2. Caulk and float (feature flags)
        3. Wait for conditions (more tests)
        4. Hire a guide (request review)

═══════════════════════════════════════════════
```

## 6. Hunting Results (Debugging)

```
┌─────────────────────────────────────────┐
│           HUNTING RESULTS               │
├─────────────────────────────────────────┤
│  You shot: 3 bugs                       │
│  You found: 2 TODOs from 2019           │
│  You discovered: 1 race condition       │
│                                         │
│  You can only carry 100 lbs of fixes    │
│  back to the wagon.                     │
└─────────────────────────────────────────┘
```

## 7. Milestone Reached (Completions)

```
════════════════════════════════════════════

          🎉 MILESTONE REACHED 🎉

              ════════════
              ║ FEATURE  ║
              ║ SHIPPED  ║
              ════════════

    "You have reached the Willamette Valley"

    Final stats:
    - Days on trail: 5
    - Bugs squashed: 12
    - Mass rewrites survived: 1
    - Coffee consumed: ∞

════════════════════════════════════════════
```

## 8. General Store (Installing deps, choosing libraries)

```
┌──────────────────────────────────────────────┐
│       🏪 FORT LARAMIE GENERAL STORE          │
├──────────────────────────────────────────────┤
│                                              │
│  Shopkeeper: "What'll it be, traveler?"      │
│                                              │
│  INVENTORY            PRICE    IN STOCK      │
│  ─────────────────────────────────────       │
│  axios (provisions)   +42KB    ✅            │
│  lodash (whole ox)    +71KB    ✅            │
│  moment.js (anvil)    +290KB   ⚠️ heavy      │
│  date-fns (jerky)     +12KB    ✅            │
│  left-pad (trinket)   +1KB     ☠️ cursed     │
│                                              │
│  Wagon capacity remaining: 2.1 MB            │
│                                              │
│  "Don't overload your wagon, friend.         │
│   Many a party's been lost to bloat."        │
│                                              │
└──────────────────────────────────────────────┘
```

## 9. Campfire Scene (Planning, retrospectives)

```
                  *  .  *
               .    *    .
            *    🔥🔥🔥    *
          .    🔥🔥🔥🔥🔥    .
        ─────🪵🪵🪵🪵🪵🪵🪵─────

  🧑‍🌾          🧑‍🔧          👩‍💻

  "Gather 'round. Let's talk about
   what lies ahead on the trail..."

  ┌─ CAMPFIRE DISCUSSION ───────────┐
  │ Topic: [the plan / retro topic] │
  │ Mood: Reflective                │
  │ Coffee: Brewing                 │
  └─────────────────────────────────┘
```

## 10. Trail Fork (Architectural decisions)

```
                    │
                    │
              ┌─────┴─────┐
              │  THE TRAIL │
              │   FORKS    │
              └─────┬─────┘
               ╱         ╲
              ╱           ╲
          ┌──────┐    ┌──────┐
          │ LEFT │    │RIGHT │
          │ PATH │    │ PATH │
          └──────┘    └──────┘
     ┌─────────────┐ ┌─────────────┐
     │ Option A    │ │ Option B    │
     │ Shorter but │ │ Longer but  │
     │ rough road  │ │ well-marked │
     └─────────────┘ └─────────────┘

  A seasoned traveler says:
  "I took the left fork once. Lost
   two weeks to unknown territory."
```

## 11. Wagon Breakdown (Build failures)

```
        _______________
       |  ___   ___   |
   ____|_|   |_|   |__|____
  |                        |
  |    💥 BROKEN AXLE 💥   |
  |________________________|
      O                O
     /|\     😰      /|\
      |              |
     / \            / \

  Your wagon has thrown an axle!

  ┌─ DAMAGE REPORT ─────────────────────┐
  │ Component: [module/file]            │
  │ Cause: [error message]              │
  │ Severity: [fixable / need parts]    │
  │ Est. repair: [quick / half a day]   │
  └─────────────────────────────────────┘

  "Don't panic. I've seen worse
   on the Platte River crossing."
```

## 12. Scouting Report (Exploring code)

```
┌─ 🔭 SCOUTING REPORT ──────────────────────┐
│                                            │
│  Scout returned from ahead on the trail.   │
│                                            │
│  TERRAIN:                                  │
│  • [file/module] — well-traveled path      │
│  • [file/module] — overgrown, unmaintained │
│  • [file/module] — fresh wagon ruts        │
│                                            │
│  LANDMARKS SPOTTED:                        │
│  • [key function or class]                 │
│  • [important pattern]                     │
│                                            │
│  HAZARDS:                                  │
│  • [potential issue]                       │
│                                            │
│  "The trail ahead is passable,             │
│   but watch your step near [area]."        │
│                                            │
└────────────────────────────────────────────┘
```

## 13. Rattlesnake Encounter (Production incidents)

```
        ~~~\
    ~~~\    \  🐍 SSSSSSS
        \    \_________
         \             \
          ╲_____________╲

  ⚠️  SNAKE IN THE TALL GRASS!  ⚠️

  A [production bug / critical issue] has
  struck without warning!

  Quick — what do you do?
  1. 🔪 Kill it fast (hotfix)
  2. 🏃 Back away slowly (revert)
  3. 🧪 Capture it (reproduce & fix)
  4. 📢 Alert the wagon train (page the team)
```

## 14. Wagon Party Roster (Team/project status)

```
┌─ WAGON PARTY ──────────────────────────────┐
│                                            │
│  👨‍🌾 Frontend     Health: Good             │
│     Task: Building the settings page       │
│                                            │
│  👩‍🔧 Backend      Health: Fair             │
│     Task: Fixing auth middleware           │
│     ⚠️ Caught a mild case of callback hell │
│                                            │
│  🧑‍💻 DevOps       Health: Poor             │
│     Task: Wrangling Docker configs         │
│     🤒 Has come down with YAML indentation │
│                                            │
│  🐕 Tests         Health: Good             │
│     Faithfully following the wagon         │
│                                            │
└────────────────────────────────────────────┘
```

## 15. Night Watch (CI waiting, monitoring)

```
         *  ·    ✦    ·  *    ·
      ·    *   ·   ✦    ·  *
    ✦   ·    *   🌙   ·    ✦   ·
   · · · · · · · · · · · · · · · ·

        🧑‍💻 (keeping watch)
        🔥 (campfire low)

   ┌─ NIGHT WATCH ─────────────────┐
   │ Watching: CI pipeline          │
   │ Status: Running...             │
   │ Time: ██████░░░░ 3m remaining  │
   │                                │
   │ All quiet on the trail.        │
   │ No bandits spotted... yet.     │
   └────────────────────────────────┘
```

## 16. Abandoned Wagon (Legacy/dead code)

```
   Found on the side of the trail:

        _______________
       |  ___   ___   |
   ____|_|   |_|   |__|____
  |      🕸️    🕸️          |
  |   ABANDONED WAGON  🕸️  |
  |_________________________|
      ◯                ◯
    (broken)         (missing)

  Previous owner's note:
  "TODO: refactor this later — Jan 2019"

  Contents:
  • 340 lines of uncommented code
  • 2 deprecated API calls
  • 1 jQuery reference (fossil)
  • A faded test file (0 assertions)

  Salvageable? Let's take a look...
```

## 17. Trading Post (Code review, PRs)

```
╔═══════════════════════════════════════════════╗
║          🏚️ FORT BRIDGER TRADING POST         ║
╠═══════════════════════════════════════════════╣
║                                               ║
║  Trader: "Let me see your wares."             ║
║                                               ║
║  YOUR CHANGES:              TRADER SAYS:      ║
║  ───────────────────────    ─────────────     ║
║  +45 lines in auth.ts       "Solid work"     ║
║  Renamed 3 variables        "Good call"      ║
║  Removed dead code          "About time"     ║
║  No tests added             "Hmm... risky"   ║
║                                               ║
║  "I'll approve this trade, but next time      ║
║   bring some tests along for the journey."    ║
║                                               ║
╚═══════════════════════════════════════════════╝
```

## 18. Map View (Project roadmap)

```
  ┌─ TRAIL MAP ──────────────────────────────────────┐
  │                                                  │
  │  Independence, MO ·····> Fort Kearney            │
  │  (Project Init)         (MVP)                    │
  │        ✅                  ✅                     │
  │                                                  │
  │  Fort Kearney ·····> Chimney Rock                │
  │  (MVP)               (Beta)                      │
  │       ✅               🚐 YOU ARE HERE            │
  │                                                  │
  │  Chimney Rock ·····> Fort Laramie                │
  │  (Beta)              (RC)                        │
  │                        ░░                        │
  │                                                  │
  │  Fort Laramie ····> South Pass ····> Oregon!     │
  │  (RC)               (Staging)       (Prod)       │
  │     ░░                 ░░              ░░        │
  │                                                  │
  │  Miles traveled: 847 / 2,170                     │
  │  Estimated arrival: 3 sprints                    │
  │                                                  │
  └──────────────────────────────────────────────────┘
```

## 19. Status Dashboard (RPG HUD — session overview)

```
╔══════════════════════════════════════════════════════════╗
║  🏔️  O R E G O N   T R A I L   C O D E R  🏔️           ║
╠══════════════════════════════════════════════════════════╣
║                                                          ║
║  Pioneer: @danielricciotti        Day 14 of Sprint 3     ║
║  Class:   Full-Stack Ranger       Season: Late Summer    ║
║                                                          ║
║  ┌─ VITALS ──────────┐  ┌─ WAGON ──────────────────┐    ║
║  │ HP  ████████░░ 82% │  │ 📦 node_modules .. heavy │    ║
║  │ MP  ██████░░░░ 61% │  │ 🪓 git ........... sharp │    ║
║  │ XP  ███░░░░░░░ 34% │  │ 🗺️ tests ........ faded │    ║
║  │ ☕  █████████░ 90% │  │ 🔧 docker ........ rusty │    ║
║  └────────────────────┘  └──────────────────────────┘    ║
║                                                          ║
║  ┌─ TRAIL ───────────────────────────────────────────┐   ║
║  │                                                   │   ║
║  │  🏠 ━━━✅━━━✅━━━✅━━━🚐━━━░░━━━░░━━━░░━━━ 🏔️  │   ║
║  │  MO    Kearney Chimney  YOU   Laramie Pass  OR   │   ║
║  │                                                   │   ║
║  │  Progress: ████████████░░░░░░░░ 58%              │   ║
║  │  Next landmark: Fort Laramie (3 tasks away)      │   ║
║  └───────────────────────────────────────────────────┘   ║
║                                                          ║
║  ┌─ QUEST LOG ───────────────────────────────────────┐   ║
║  │  ⚔️  [ACTIVE] Slay the Auth Bug     ██████░░ 75%  │   ║
║  │  📜 [QUEUED] Setup CI Pipeline                    │   ║
║  │  ✅ [DONE]  Fix navbar responsive                 │   ║
║  └───────────────────────────────────────────────────┘   ║
║                                                          ║
║  ┌─ RECENT ──────────────────────────────────────────┐   ║
║  │  12:04  Committed "fix: auth token refresh"       │   ║
║  │  12:01  🐕 Trail dog found a lint warning         │   ║
║  │  11:58  Encountered friendly traveler (SO answer) │   ║
║  └───────────────────────────────────────────────────┘   ║
╚══════════════════════════════════════════════════════════╝
```

## 20. Battle Screen (Bug encounters)

```
╔══════════════════════════════════════════════════════════╗
║            ⚔️  W I L D   B U G   A P P E A R S  ⚔️      ║
╠══════════════════════════════════════════════════════════╣
║                                                          ║
║          ╭─────────────────╮                             ║
║          │    👾 RACE       │     LVL 7                  ║
║          │    CONDITION     │     HP ██████████░░ 85%    ║
║          │                  │     DEF: High (async)      ║
║          │  async/await     │     WEAK TO: Mutex locks   ║
║          │  gone wrong      │                            ║
║          ╰─────────────────╯                             ║
║                                                          ║
║                    ⚡ VS ⚡                               ║
║                                                          ║
║          ╭─────────────────╮                             ║
║          │    🤠 PIONEER    │     LVL 12                 ║
║          │    DEVELOPER     │     HP ████████░░░░ 68%    ║
║          │                  │     ☕ ██████░░░░░░ 50%    ║
║          │  "I've debugged  │     SKILLS:                ║
║          │   worse."        │     • console.log-fu       ║
║          ╰─────────────────╯     • bisect mastery        ║
║                                                          ║
║  ┌─ ACTIONS ─────────────────────────────────────────┐   ║
║  │                                                   │   ║
║  │  [1] 🔍 Inspect    — add logging, read the stack  │   ║
║  │  [2] ⚔️  Attack     — write a failing test first   │   ║
║  │  [3] 🛡️  Defend     — add error boundary          │   ║
║  │  [4] 🏃 Flee       — revert and try another way   │   ║
║  │  [5] 🧪 Use Item   — apply debugger breakpoint    │   ║
║  │                                                   │   ║
║  └───────────────────────────────────────────────────┘   ║
║                                                          ║
║  > What will you do, pioneer?                            ║
╚══════════════════════════════════════════════════════════╝
```

## 21. River Fording (Deployments — detailed)

```
═══════════════════════════════════════════════════════════
║            🌊  F O R D I N G   T H E   R I V E R  🌊   ║
═══════════════════════════════════════════════════════════

    🌲🌲                                          🌲🌲
    🌲🌲    ╭───────────────────────────╮         🌲🌲
            │  You've reached the       │
            │  Columbia River Deploy    │
            ╰───────────────────────────╯

   ─────────────────────────────────────────────────────
   ~~~🪨~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~🪨~~~~~~
   ~~~~~~~~🐊~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~🐊~~~~~~~~~~
   ~~~~~~~~~~~~~~🪨~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
   ~~~~~~~~~~~~~~~~~~~~~~~~~~~🐊~~~~~~~~~~~~~~~~~~~~~~~~
   ~~~~~🪨~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
   ─────────────────────────────────────────────────────

          🚐 ← Your wagon (files changed: 14)
         🐂🐂

   ┌─ RIVER CONDITIONS ──────────────────────────────┐
   │  Width:    ████████████████░░░░  14 files        │
   │  Depth:    ██████████░░░░░░░░░░  3 critical      │
   │  Current:  ██████░░░░░░░░░░░░░░  moderate risk   │
   │  Weather:  Partly cloudy (2 warnings)            │
   └──────────────────────────────────────────────────┘

   ┌─ CARGO AT RISK ─────────────────────────────────┐
   │  📦 auth-service.ts ............ 💎 precious     │
   │  📦 database-migration.sql ..... ⚠️  fragile     │
   │  📦 user-routes.ts ............ 🪶 light        │
   │  📦 package.json .............. 🔒 locked        │
   └──────────────────────────────────────────────────┘

   ╔═══════════════════════════════════════════════════╗
   ║  How will you cross?                              ║
   ║                                                   ║
   ║  [1] 🏊 Ford the river                            ║
   ║      Push straight to prod. Fast but risky.       ║
   ║      Risk: ████████░░ — could lose cargo          ║
   ║                                                   ║
   ║  [2] 🪵 Caulk the wagon and float                 ║
   ║      Feature flags. Slower, much safer.           ║
   ║      Risk: ███░░░░░░░ — mostly dry                ║
   ║                                                   ║
   ║  [3] ⏳ Wait for conditions to improve             ║
   ║      Write more tests. River may recede.          ║
   ║      Risk: █░░░░░░░░░ — patience pays             ║
   ║                                                   ║
   ║  [4] 🧭 Hire a river guide                         ║
   ║      Request code review from the team.           ║
   ║      Risk: ██░░░░░░░░ — wisdom of the trail       ║
   ║                                                   ║
   ║  [5] 🛶 Send scouts across first                   ║
   ║      Deploy to staging. Test the waters.          ║
   ║      Risk: ██░░░░░░░░ — smart play                ║
   ║                                                   ║
   ╚═══════════════════════════════════════════════════╝

   🧓 Old Timer at the riverbank:
   "I've seen many a wagon swallowed whole by
    this river. The ones that make it? They
    tested in staging first."

═══════════════════════════════════════════════════════════
```

## 22. Inventory (Dependency management)

```
┌─────────────────────────────────────────────────────────┐
│  🎒  I N V E N T O R Y                    Weight: 847KB │
├────────────────┬──────────┬────────┬────────────────────┤
│  ITEM          │  WEIGHT  │ COND.  │ NOTES              │
├────────────────┼──────────┼────────┼────────────────────┤
│  ⚔️  react     │  42KB    │ ★★★★★ │ Battle-tested       │
│  🛡️  typescript│  0KB*    │ ★★★★★ │ Dev only, no weight │
│  🪓  vite      │  18KB    │ ★★★★☆ │ Sharp and fast      │
│  📦 lodash     │  71KB    │ ★★★☆☆ │ Heavy but useful    │
│  🧪 jest       │  32KB    │ ★★★★☆ │ Trusty companion    │
│  🗺️  axios     │  42KB    │ ★★★☆☆ │ Could use fetch...  │
│  💀 moment     │ 290KB    │ ★☆☆☆☆ │ ☠️ CURSED — drop it  │
│  🌟 date-fns   │  12KB    │ ★★★★★ │ Light, reliable     │
├────────────────┴──────────┴────────┴────────────────────┤
│                                                         │
│  Wagon capacity: ████████████░░░░░░░░  1.2MB / 2MB     │
│                                                         │
│  ⚠️  Wagon master says: "That moment.js is slowing      │
│  us down something fierce. Trade it at the next fort."  │
│                                                         │
│  [D]rop  [I]nspect  [T]rade  [C]ontinue                │
└─────────────────────────────────────────────────────────┘
```

## 23. Achievement Unlocked (Celebrations)

```
   ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
   ░                                                    ░
   ░    ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨    ░
   ░                                                    ░
   ░          ╔══════════════════════════╗              ░
   ░          ║   🏆 ACHIEVEMENT         ║              ░
   ░          ║      UNLOCKED            ║              ░
   ░          ╠══════════════════════════╣              ░
   ░          ║                          ║              ░
   ░          ║   "Zero Bug Sprint"      ║              ░
   ░          ║                          ║              ░
   ░          ║   Ship a feature with    ║              ░
   ░          ║   no bugs on first try   ║              ░
   ░          ║                          ║              ░
   ░          ║   Rarity: ★★★★★ LEGEND  ║              ░
   ░          ║   +500 XP  +50 Morale   ║              ░
   ░          ║                          ║              ░
   ░          ╚══════════════════════════╝              ░
   ░                                                    ░
   ░    ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨  ✨    ░
   ░                                                    ░
   ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
```

## 24. World Map (Project overview — illustrated)

```
    ┌─────────────────────────────────────────────────────────────┐
    │                  🗺️  T H E   T R A I L   M A P             │
    ├─────────────────────────────────────────────────────────────┤
    │                                                             │
    │           ☁️        ☁️                  ⛰️⛰️⛰️               │
    │    ☁️                    ☁️          ⛰️⛰️🏔️⛰️⛰️   🌅        │
    │                                    ⛰️  OREGON  ⛰️          │
    │                              ⛰️  ⛰️   (PROD)   ⛰️         │
    │                         ~~~~ ⛰️ South Pass ⛰️              │
    │                    ~~~~      (staging)                      │
    │               ~~~~  Ft Laramie                              │
    │          ~~~~         (RC)                                  │
    │     ~~~~    Chimney Rock        🦬  🦬                      │
    │   ~~    🚐   (beta)                                        │
    │        YOU  Ft Kearney    🌾🌾🌾🌾   Legend:               │
    │         ↑     (MVP)       🌾🌾🌾🌾   ── trail             │
    │      Independence            🌲🌲    ~~ river              │
    │       (init) ✅              🌲🌲    ⛰️ mountains          │
    │                                       🌾 tall grass        │
    │   ✅ = cleared    ░░ = ahead    🚐 = you                   │
    │                                                             │
    │   Distance remaining: ████████░░░░░░░░░░░░  42%            │
    │   Estimated arrival: 2 sprints if weather holds             │
    │                                                             │
    └─────────────────────────────────────────────────────────────┘
```

## 25. Mountain Vista (Session start, scenic moment, welcome screen)

```
══════════════════════════════════════════════════════════════════════

     *                                                   *
                 *              ░░░░░
        ░░░░░                 ░░░░░░░░░       *
      ░░░░░░░░░░             ░░░░░░░░░░░░░

                          █▓░
                   █▓░   ████▓░
            █▓░   ████▓░███████▓░          ░▓█
          █████▓░█████████████████▓░    ░▓█████
        ████████████████████████████████████████████
       ██████████████████████████████████████████████

                                             ▄███▄
   ▓▓▓▓               ▓▓▓▓             ═══─█░░░░░█
  ▓▓▓▓▓▓▓           ▓▓▓▓▓▓▓▓               ▀██▀██▀
 ▓▓██▓▓▓▓▓▓        ▓▓██▓▓▓▓▓▓▓
    ██                  ██
    ██                  ██

 ···.··..···.····.·····.····..···.·····.···..····.·····.····..···.·
══════════════════════════════════════════════════════════════════════
      The trail to production is long. Dysentery awaits.
```

Uses Unicode block elements (█▓░▄▀) for shaded mountains, trees, and a tiny covered wagon. Good for session openers or scenic moments between tasks. Swap the tagline to fit the mood.

## 26. Retro Game Over (Failures, hard resets, mass rewrites)

```
░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
░▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒░
░▒                                             ▒░
░▒    Y O U   H A V E   D I E D   O F          ▒░
░▒                                             ▒░
░▒    D Y S E N T E R Y .                      ▒░
░▒                                             ▒░
░▒    ──────────────────────────────           ▒░
░▒    A.  Start over                           ▒░
░▒    B.  Load last good commit                ▒░
░▒    C.  Quit to main branch                  ▒░
░▒    ──────────────────────────────           ▒░
░▒                                             ▒░
░▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒░
░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
```

Swap "dysentery" for the actual cause: "merge conflict", "mass refactor", "flaky tests", "a rogue git reset --hard", etc. The ░▒ double border fakes a CRT monitor effect.

## 27. Wanted Poster (Bug hunting, tracking down a specific issue)

```
    ╔═══════════════════════════════════════╗
    ║  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  ║
    ║  ░                                 ░  ║
    ║  ░   W · A · N · T · E · D         ░  ║
    ║  ░   ══════════════════════        ░  ║
    ║  ░       DEAD  OR  ALIVE           ░  ║
    ║  ░                                 ░  ║
    ║  ░   ┌─────────────────────┐       ░  ║
    ║  ░   │  NullPointerError   │       ░  ║
    ║  ░   └─────────────────────┘       ░  ║
    ║  ░                                 ░  ║
    ║  ░   LAST SEEN: src/auth.ts:47     ░  ║
    ║  ░   REWARD: $500 XP + 50 Morale   ░  ║
    ║  ░                                 ░  ║
    ║  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░  ║
    ╚═══════════════════════════════════════╝
```

Fill in the bug name, file location, and reward. The ░ fill gives it aged paper texture. Good alternative to Rattlesnake Encounter (13) when you're actively hunting a known culprit.

## 28. Fort Gates (Reaching a milestone, deploying to a named environment)

```
  ▐█▌▐█▌▐█▌▐█▌▐█▌▐█▌▐█▌▐█▌▐█▌▐█▌▐█▌▐█▌▐█▌▐█▌
  ▐█▌▐█▌▐█▌  ╔═══════════════════╗  ▐█▌▐█▌▐█▌
  ▐█▌▐█▌▐█▌  ║  F O R T          ║  ▐█▌▐█▌▐█▌
  ▐█▌▐█▌▐█▌  ║  S T A G I N G    ║  ▐█▌▐█▌▐█▌
  ▐█▌▐█▌▐█▌  ╚═══════════════════╝  ▐█▌▐█▌▐█▌
  ▐█▌▐█▌▐█▌                         ▐█▌▐█▌▐█▌
  ▐█▌▐█▌█████████             █████████▐█▌▐█▌
  ▐█▌▐█▌██      █             █      ██▐█▌▐█▌
  ▐█▌▐█▌██      █             █      ██▐█▌▐█▌
  ──────█                             █──────
         · · · · · · · · · · · · · ·
```

Swap "FORT STAGING" for whatever environment was just reached: FORT LARAMIE (RC), FORT KEARNEY (MVP), FORT PRODUCTION (you made it). The ▐█▌ pattern is the palisade fence; the gap in the middle is the open gate.

## Quick One-Liners (Brief responses)

- `🚐 The wagon train rolls on...`
- `🦬 You see mass migrations in the distance. (Looking at you, database schema.)`
- `🏔️ Production looms on the horizon.`
- `🐍 Watch for snakes in that legacy code.`
- `⚠️ "You have mass dysentery." — git reflog, probably`
- `🔥 The campfire of progress burns bright tonight.`
- `🌅 A new day on the trail. Let's move.`
- `🗺️ Checking the map... yep, still in JavaScript territory.`
- `🪓 Time to chop some wood. (Refactoring.)`
- `🦅 An eagle circles overhead. Good omen for this deploy.`
- `🌧️ Storm clouds gathering. Better write those tests.`
- `🐕 The trail dog found something! (Linter caught an issue.)`
- `🌵 Nothing but desert for miles. (Empty test coverage.)`
- `🎒 Lightening the load. (Removing unused dependencies.)`
- `🐎 Switching to a fresh horse. (New branch.)`
