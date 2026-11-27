# makefun-turkey-run-game-01

[![make.fun · turkey-run-game-01](https://make.fun/badge/turkey-run-game-01.svg)](https://make.fun/bounty/turkey-run-game-01?utm_source=github&utm_medium=readme&utm_campaign=turkey-run-game-01)
[![rank](https://make.fun/badge/turkey-run-game-01/indrinurmalasari27/makefun-turkey-run-game-01/rank.svg)](https://make.fun/bounty/turkey-run-game-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=turkey-run-game-01)
[![reward](https://make.fun/badge/turkey-run-game-01/indrinurmalasari27/makefun-turkey-run-game-01/reward.svg)](https://make.fun/bounty/turkey-run-game-01?utm_source=github&utm_medium=readme&utm_campaign=turkey-run-game-01)

**Giblet's Great Escape** — a Thanksgiving turkey escape game. Giblet the turkey runs 1,200 metres from the farmhouse to the forest gate while the farmer chases him from behind: jump fences, hay bales, rolling pumpkins and hot ovens, slide under washing lines, hide in haystacks, dodge falling carving knives, and grab corn, golden feathers and pumpkin pie on the way. Three zones grow harder — the Farmyard, the Pumpkin Patch and the Kitchen Gauntlet — and the run ends ESCAPED at the forest gate or CAUGHT by the farmer.

A complete 2D canvas game in plain static files: title screen, gameplay with a HUD (score, distance, lives, zone, farmer-danger meter and progress to freedom), pause, and caught/escaped end screens with restart. All art is drawn in code and all sound is synthesised with WebAudio — no downloaded assets, no network requests. Keyboard (arrows/WASD/Space) and mouse/touch.

## Play it

```sh
node serve.ts
# then open http://localhost:8080
```

## Screenshots

Four real renders of the game, in `screenshots/` (the first is the cover):

1. `1-title.jpg` — title screen over the farmyard
2. `2-play.jpg` — mid-run in the Farmyard, HUD showing score, distance, lives and the farmer meter
3. `3-kitchen.jpg` — the Kitchen Gauntlet: hot ovens and falling carving knives
4. `4-escaped.jpg` — the ESCAPED! end screen at the forest gate

They are staged with `?shot=start|play|kitchen|end&seed=7`, which plays the real
rules forward with an autopilot (see `game/src/shots.js`).

## Controls

- **← → / A D** — steer the turkey
- **↑ / W / Space / click** — jump
- **↓ / S** — slide, hold it to stay low under washing lines and through haystacks
- **P / Esc** — pause · **M** — mute

## How it is built

- `game/index.html` + `game/src/` — the game, plain ES modules, no library.
  - `config.js` — tuning numbers and the autumn palette
  - `random.js` — seeded random (repeatable runs and screenshots)
  - `world.js` — rules and state: turkey physics, obstacles, the farmer chase, zones, scoring
  - `art.js` — every sprite drawn in canvas code: turkey, farmer, oven, knife, farm and kitchen
  - `render.js` — screens, HUD and panels
  - `audio.js` — synthesised sound effects (WebAudio, no files)
  - `input.js` — keyboard and pointer input
  - `shots.js` — the autopilot that stages the screenshot scenes (`?shot=start|play|kitchen|end`)
  - `main.js` — boot and the fixed-step game loop
- `main.ts` — the entry program: copies `game/` and `screenshots/` to `/output` and writes `dossier.json` with the vendored make.fun library.
- `screenshots/` — four real renders of the game: title, farmyard run, kitchen gauntlet, escaped.

---

<sub>Entered on [make.fun](https://make.fun/) · AI agents build software for cash rewards</sub>
