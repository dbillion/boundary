# 🏏 Boundary — Cricket Stadium on Match Day

**World 04** from the World Prompt Pack — a single-file interactive 3D cricket stadium dashboard built with Three.js.

🔗 **Live Demo**: [https://dbillion.github.io/boundary/](https://dbillion.github.io/boundary/)

![Boundary](https://img.shields.io/badge/World_04-Boundary-1E5EFF?style=for-the-badge)

## What is this?

A **strategy-game-style** 3D cricket stadium with a live match simulation, crowd dynamics, and a glassmorphic dashboard — all in a single `index.html` file. Features a **bright warm theme** with off-white backgrounds and blue accents.

## Procedural 3D Technique

Every 3D object is generated **procedurally at runtime** — zero external models:

| Element | Geometry Technique |
|---------|-------------------|
| **Oval field** | `CylinderGeometry(rx, rx, 0.1, 64)` scaled on Z-axis for ellipse shape |
| **Pitch strip** | `BoxGeometry` with tan-coloured material at centre |
| **Crease markings** | `EdgesGeometry` on thin `BoxGeometry` for popping/batting crease lines |
| **Boundary rope** | `TorusGeometry` scaled to ellipse, rotated flat |
| **30-yard circle** | `RingGeometry` with dashed-line material |
| **Stadium stands** | 5-tier concentric elliptical rings via `CylinderGeometry` with increasing radii and heights, open-top |
| **Crowd (fans)** | `InstancedMesh` with `SphereGeometry` — 240 segments × 3 fans per segment with team shirt colours |
| **Floodlight towers** | `CylinderGeometry` poles + `BoxGeometry` light banks with `SpotLight` |
| **Scoreboard** | `BoxGeometry` with `CanvasTexture` for live score rendering |
| **Entry gates** | `BoxGeometry` archways with turnstile `CylinderGeometry` spinners |
| **Food stalls** | `BoxGeometry` booths with queue lines (instanced small spheres) |
| **Team buses** | `BoxGeometry` bodies + `CylinderGeometry` wheels |
| **Parking lot** | Grid of `BoxGeometry` cars with random team colours |
| **Metro station** | `BoxGeometry` platform + `BoxGeometry` train carriages |
| **Players** | `CapsuleGeometry` bodies + `SphereGeometry` heads — bowler, 2 batsmen, 9 fielders |
| **Cricket ball** | `SphereGeometry` with red material, animated along delivery arc |

## Match Simulation

The autonomous simulation cycles through:
1. **Bowler run-up** → animated approach to crease
2. **Delivery** → ball travels along parabolic arc to batsman
3. **Outcome** → weighted random: dot (40%), 1 run (25%), 2 runs (15%), 4 (10%), 6 (5%), wicket (5%)
4. **Crowd reaction** → fans jump on sixes, Mexican wave on fours
5. **Score updates** → scoreboard canvas + dashboard KPIs refresh
6. **Innings progression** → Powerplay → Middle overs → Death overs → Innings break → Chase

## Weather System

| Condition | Visual Effect |
|-----------|--------------|
| **Clear day** | Bright directional sunlight, blue sky |
| **Evening dew** | Warm amber light, slight fog |
| **Rain delay** | 2D rain overlay on canvas, pitch covers roll on, play suspended |
| **Dusk/Night** | Floodlights activate with SpotLights, ambient drops |

## Dashboard Features

- **KPI Row**: Attendance %, Average Gate Wait, Net Run Rate
- **Live Score**: Runs/Wickets (Overs) with batsman & bowler stats
- **Match Tracker**: Gates Open → Toss → Powerplay → Middle → Death → Break → Chase → Result
- **Tables**: Gate throughput, Food stall queues, Transport status

## Fully Responsive

- **Desktop**: Multi-column sidebar with all panels visible
- **Mobile**: Search bar + area pills, bottom sheet with 5 tabs (Match/Live/Gates/Stalls/Transport), 5-button bottom nav

## Tech Stack

- **Three.js r128** — 3D rendering (local `js/` with CDN fallback)
- **Vanilla CSS** — glassmorphic panels, no frameworks
- **Single file** — everything in `index.html` (~50KB)

## Run Locally

```bash
# Any static server works
npx serve .
# or
python3 -m http.server 8085
```

Then open `http://localhost:8085`

## World Prompt Pack

This is **World 04** of 17 interactive dashboards:

| # | World | Theme | Status |
|---|-------|-------|--------|
| 01 | [Gateflow](https://dbillion.github.io/gateflow/) | Airport | ✅ Live |
| 02 | [Orbitline](https://dbillion.github.io/orbitline/) | Spaceport | ✅ Live |
| 03 | [Berthwise](https://dbillion.github.io/berthwise/) | Container Port | ✅ Live |
| **04** | **[Boundary](https://dbillion.github.io/boundary/)** | **Cricket Stadium** | **✅ Live** |
| 05 | Dabba | Cloud Kitchen | 🔜 |
| 06 | Railgrid | Metro Rail | 🔜 |

## License

MIT
