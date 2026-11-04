# Wheel Racer — Squeek Grand Prix

A pixel kart race powered by the **real** Squeekchain hamster wheel.

**▶ Race it live: <https://kuhugn.github.io/wheel-racer/>**

> Your engine is Squeektoshi. When he runs, you fly. When he naps, you pedal.
> Your rival is the ghost of the last settled round — a recording that never sleeps.

Built for the **Squeekchain Genesis** builder program
(<https://squeekchain.com/genesis/code>).

## How it plays

- 500 m sprint on a garden dirt track, 3 lanes (W/S or ↑/↓, touch buttons on mobile).
- **Your top speed follows the live wheel RPM** from the Squeekchain public API,
  polled every 3 seconds. The giant wheel in the background spins at the real
  RPM and powers the track through a glowing cable.
- **The ghost never naps.** Its pace profile (18–25 m/s, surging in 6-second
  segments) is seeded by the settlement anchor — `settledThroughRound × 1,000,003
  + blockHeight` — so every player races the same ghost in the same round, and
  the results screen links the settlement transaction on Sepolia Etherscan.
- **When Squeektoshi naps mid-race, your engine dies** while the ghost keeps
  going. Hold SPACE (or the PEDAL button) to pedal at ~7.5 m/s until he wakes.
- Dodge rocks, Syrup slugs and surfacing Garden moles (they telegraph with a
  “!” before popping up). A crash costs 1 of 3 hearts and most of your speed.
- Pearl seeds: +10 pts and a small boost. Score = seeds + win bonus 300 +
  50 per remaining heart.
- A **Simulate nap** button kills the engine for 12 s so reviewers can test
  the nap/pedal mechanic on demand.
- Pre-race setup: name + language (English / Tiếng Việt). Optional wallet
  connect (👛 top-right) only names leaderboard entries; racing never needs
  a transaction or gas.

## Squeekchain integration

| Use | Source |
| --- | --- |
| Engine power (RPM → top speed), wheel status, rim speed, distance | `GET https://api.squeekchain.com/v1/status` → `measurement` |
| Ghost pace seed (settled round + Squeek block height) | `GET /v1/status` → `builder.anchor` |
| Settlement proof link | `builder.anchor.transactionHash` → Sepolia Etherscan |

## Run it

No build step, no dependencies. Serve the folder statically:

```sh
python3 -m http.server 8099
# open http://127.0.0.1:8099/
```

## Project layout

- `index.html` — the whole game (Canvas 2D) in one static file; the hamster,
  mole, slug and pearl-seed sprites are embedded as data URIs. Artwork adapted
  from Exsqueektion (squeek.win) pixel assets, the same source as Burrow Raid.
- `index-template.html` — the same source with sprite placeholders, kept for
  provenance/rebuilds.
- `SUBMIT.md` — the Genesis submission checklist for this project.
