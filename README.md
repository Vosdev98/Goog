# 🟢 Wiggle Goog 3D

A wacky, googly-eyed jelly game that grows into a two-act adventure — a 3D arcade
romp that detonates into a first-person shooter. Built from the prompt
*"wiggle goog biisss pooor ssaccekl toscccet lickes…"* — interpreted as:
**you are Goog, a wiggly googly blob — gobble the snackles, dodge the wobbles, then go tactical.**

## How to play

- **Just double-click `index.html`** — one self-contained file (no install, server, or internet).
- Or serve it: `python -m http.server 8137` then open `http://localhost:8137`.
- `index-2d.html` is the original 2D prototype, kept as a backup.

## Controls

| Action | Input |
|--------|-------|
| Move | **WASD** / **Arrow keys** / **drag** (touch) |
| Aim & shoot (Act 2) | **Mouse** look + **click/hold** to fire (pointer-lock) |
| Reload | **R** |
| Start / Restart | Press any key / tap / click |
| Pause (Act 2) | **Esc** (releases mouse) |
| Mute | **M**, or the 🔊 button (bottom-left) |
| Settings | ⚙ button (title, bottom-right) — sensitivity, volume, invert-Y, music |

## Act 1 — Wiggle (3D arcade)

- 🍬 **Snackles** — donuts, cupcakes, and candy gems; gobble them for points and grow.
- ⭐ **Golden stars** — rare, worth 5× with a juicy burst.
- 🔴 **Wobbles** — spiky googly-eyed sea-mines that bounce around. Touch one, lose a life (3 total).
- 🔥 **Combos** — eat quickly in a row to stack a score multiplier.
- **Power-ups** — ⚡ Turbo · 🛡 Shield (invincible + bounces wobbles) · 🧲 Magnet.
- Difficulty ramps the longer you survive. Best score saved locally.

## Act 2 — GOOG GOES TACTICAL 🔫 (unlocks at 2500, first-person)

Cross **2500 points** and the game detonates into a Counter-Strike-inspired FPS on a
de_dust2-style desert map (palms, archways, a distant mosque dome + minaret, mountains,
crates, a sandy sun-lit skybox). Goog grabs an **AK-47** and fights a **4-wave mission**:

- **Wave 1–3:** escalating squads of three enemy types —
  **grunts** (shooters), **rushers** (fast melee chargers), **heavies** (tanky, double-shot).
- **Wave 4:** the **boss** — *the Goog-Crusher* — a giant with a 5-round spread that enrages at half health.
- **Between waves:** grab dropped **health** and **ammo** pickups.
- **Shoot down incoming projectiles**, take cover (walls block bullets & sightlines), clear all waves, then reach the **exit archway** for **MISSION COMPLETE** (with kills + accuracy stats).
- 100 HP, 3 lives (respawn on death). A **🔫 TACTICAL TEST** button on the title jumps straight in.
- **Touch:** drag to look, hold to advance + auto-fire.

## Tech

Pure **WebGL** + JavaScript, **zero dependencies** (no Three.js, no CDN, no asset files).
A compact hand-written engine:

- mat4/mat3 math, lit shaders (diffuse + specular + rim + distance fog), and a
  **per-vertex-colour model builder** that merges procedural primitives
  (sphere, cube, cylinder, cone, torus) into single multi-material meshes —
  so Goog, the enemies, the detailed AK viewmodel, snackles, the mine, palms and
  the archway are all real 3D models.
- A **directional desert skybox** (sun, gradient, heat-shimmer) that tracks your view.
- Two cameras: an angled chase cam (Act 1) and a true first-person eye cam with
  pointer-lock mouse-look, recoil, weapon bob, and a depth-cleared viewmodel (Act 2).
- **Procedural generative music** (menu / arcade / combat moods) + procedural Web Audio SFX.
- Fixed-timestep physics, AABB/grid collision, camera shake, particles, settings persistence.
