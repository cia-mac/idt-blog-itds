---
workflow_step: itd_020_shipped_and_itd_008_v3_ball_scene
agent_type: execute
token_budget: deep
last_updated: 2026-04-19
---

# SESSION_STATE: idt-blog-itds

**Last Updated:** 2026-04-19 (autopilot continuation)
**Session:** ITD-020 slow-motion lever with bullet-through-apple + ITD-008 scene swapped from cityscape to moving ball
**Last committed:** `75d9d9b` — "Ship v4 Ciamac-gold ITD baseline, split into idt-specific and generic" (2026-04-14)
**Branch:** main (no remote configured)

## Current State

Fifteen ITDs shipped prior to this session. This session added one new shippable ITD (ITD-020), three abandoned concept prototypes (ITD-017, 018, 019), and updated ITD-008 scene to a moving ball (v3). Gallery now at `index_v11.html` featuring ITD-020 as the hero, 10 generic + 6 IDT-specific = 16 total live entries. None of the new files are committed yet.

### ITD-020: What Slow Motion Actually Is · `generic/itd-020-slow-motion_v8.html`

- **Concept:** single canvas, single physical lever, watch a fast event slow down as the lever swings to higher frame rates.
- **Scene:** procedural bullet-through-apple. 5 ms physical event. Apple renders as a solid red ellipse with stem, leaf, and highlight. Bullet is a gold oblong with a motion-blur streak whose length is inversely tied to capture fps. On impact, 190 particles release outward with analytic landing times on a floor plane (y=392 scene-space), then fade out on the ground.
- **Lever:** dedicated canvas panel below the stage. Pivot at bottom-center, shaft swings through ±55° arc, gold-rimmed rubber knob at the tip, gold-bolt pivot cap, rivets on the base plate, arc groove with eight tick marks at the preset rates. Drag the knob or tap anywhere on the lever canvas. Log-scale fps mapping across [60, 20,000].
- **Presets:** 4×2 card grid below the stats strip. Cards are the hero, each at 1.45em fps with a context label (`phone camera / action cam / broadcast / industrial / science lab / ballistics / impact research / the ceiling`). Active preset = gold border + gold faint fill + gold text. Active state only triggers when fps within 3% of a preset value.
- **Stats strip:** `Capture | Slow-Motion Factor (hero gold) | 5 ms stretches to`. Persistent readout outside the scene.
- **Loop behavior:** scene runs t=0 to t=1 then pauses for 1.6 s on the intact apple (t=0). Scene-end fade ramp from t=0.82 to t=1.0 wipes all transient elements so the transition to pause is clean.

### Abandoned concepts (files preserved, NOT in gallery)

- **ITD-017** `generic/itd-017-highspeed-tradeoff_v1.html`, `_v2.html` — three-slider tradeoff interactive (fps/resolution/memory with record-time readout). User rejected concept after v2. "This concept is not working."
- **ITD-018** `generic/itd-018-time-magnification_v1.html`, `_v2.html` — dual-scale timeline showing real-time vs viewer-time. Started with balloon pop (v1), then electric arc (v2). Superseded by ITD-020 pure slow-mo pattern.
- **ITD-019** `generic/itd-019-filmstrip_v1.html`, `_v2.html` — Muybridge-style contact sheet of captured frames. User rejected. "I don't want frames like that, doesn't do anything for me."

### Design tokens preserved

- v4 Ciamac-gold palette intact across ITD-020: `#ffd94d` accent, DM Sans + JetBrains Mono, noise overlay, fadeUp, `#09090b` bg. New ITD-020 uses the same grammar.

## What Was Done This Session

1. **Onboarded on ITD concept** (first message) — read Notion pages for ITD business concept, pattern/pipeline, and series buildout. Confirmed ITD = Interactive Technical Diagrams. Existing 14 ITDs split into generic + idt-specific.
2. **ITD-017 Tradeoff** (v1 → v2) — built a fps/resolution/memory tradeoff interactive with accumulating memory bar. Rejected by user.
3. **ITD-018 Time Magnification** (v1 → v2) — dual-scale timeline, balloon pop (v1), then switched to electric arc after user accepted that subject. 20,000 fps cap applied.
4. **ITD-019 Frame Filmstrip** (v1 → v2) — contact-sheet grid, same arc subject. Rejected.
5. **Pivot to pure slow-mo playback.** User prescription: "show a fast event then slow it down to 20000."
6. **ITD-020 build and iterate** (v1 → v8):
   - v1/v2: mousetrap scene (user said "try something else" eventually)
   - v3: cleaned up HUD, added stats strip, fixed scene layout bugs
   - v4: upgraded preset chips to prominent card grid ("all about the frame rates")
   - v5: continuous log-scale slider, bullet-through-apple scene
   - v6: replaced horizontal slider with pivoting arc lever (user: "the frame rate should be a lever")
   - v7: strengthened gravity, reduced rightward velocity, intact-apple pause state
   - v8: particle count 340→190, analytic landing times + floor settle, scene-end fade
7. **Gallery rewrites**: index_v7 (ITD-017 featured), v8 (018/019 featured, dropped 017), v9 (ITD-020 featured, dropped 017/018/019), v10 (ITD-020 v8 pointer).
8. **All files opened in browser** after each write per memory rule.

## File Inventory (new this session)

### `generic/` additions

| File | Status |
|---|---|
| `itd-017-highspeed-tradeoff_v1.html` | abandoned concept (not in gallery) |
| `itd-017-highspeed-tradeoff_v2.html` | abandoned concept (not in gallery) |
| `itd-018-time-magnification_v1.html` | abandoned concept (not in gallery) |
| `itd-018-time-magnification_v2.html` | abandoned concept (not in gallery) |
| `itd-019-filmstrip_v1.html` | abandoned concept (not in gallery) |
| `itd-019-filmstrip_v2.html` | abandoned concept (not in gallery) |
| `itd-020-slow-motion_v1.html` | abandoned (mousetrap) |
| `itd-020-slow-motion_v2.html` | abandoned (mousetrap) |
| `itd-020-slow-motion_v3.html` | abandoned (mousetrap, stats strip pass) |
| `itd-020-slow-motion_v4.html` | abandoned (mousetrap, preset cards pass) |
| `itd-020-slow-motion_v5.html` | abandoned (bullet+apple, log slider, pre-lever) |
| `itd-020-slow-motion_v6.html` | abandoned (arc lever, pre-physics-tune) |
| `itd-020-slow-motion_v7.html` | prior baseline |
| `itd-020-slow-motion_v8.html` | **SHIPPABLE. Featured in gallery.** |

### Root

| File | Status |
|---|---|
| `index_v7.html` | superseded |
| `index_v8.html` | superseded |
| `index_v9.html` | superseded |
| `index_v10.html` | superseded |
| `index_v11.html` | superseded |
| `index_v12.html` | **current live gallery (ITD-020 featured, ITD-008 bumped to v4)** |
| `generic/itd-008-bit-depth_v3.html` | superseded (first ball pass) |
| `generic/itd-008-bit-depth_v4.html` | **live. Bigger ball, ground band, scene default view, relocated label.** |
| `SESSION_STATE_v5.md` | pre-overwrite snapshot of the prior SESSION_STATE |

## Next Actions

1. **Commit.** Every file in this session is untracked. Needs a clean commit per project discipline. Suggested:
   - `git add SESSION_STATE.md SESSION_STATE_v5.md generic/itd-020-* index_v10.html`
   - `git commit -m "Ship ITD-020 slow-motion lever with bullet-through-apple; v10 gallery"`
   - Decide separately whether to commit or `/archive` the ITD-017/018/019 abandoned attempts.
2. **Decide hosting.** No git remote on this repo. When ready to share ITD-020, push to `cia-mac` on GitHub and enable GitHub Pages.
3. **Write blog post for ITD-020** (if/when IDT blog pipeline resumes). Currently on ice per locked read on Luiz.
4. **Possible ITD-021: crash test**. User mentioned this mid-session; parked when direction pivoted to slow-motion. Concept proposed: side-view impact with airbag deploy timing + head excursion trajectory + measurement uncertainty band that shrinks as fps rises. Physical duration ~100-150 ms.
5. **Consider archiving abandoned attempts** (017/018/019 v1+v2) to `/archive/abandoned-concepts/` so they stop cluttering the `generic/` directory without being deleted.

## Blockers

- **No git remote configured.** Repo is local-only. Can't share via URL until remote + Pages configured.
- **IDT work is on ice** per Luiz locked read (2026-04-14). `idt-specific/` bucket continues to be dormant. `generic/` is safe to continue developing — ITD-020 went in there.

## Fragile Areas

- **Preset active-state tolerance** (ratio 0.97-1.03) means continuous-slider drags near a preset will show it active, then inactive once you pass. Intentional; don't tighten or loosen without confirming the feel.
- **Analytic landing time** (`landingTime` per particle) depends on `vy*vy + 2*GRAVITY*dy >= 0`. If future tuning pushes vy strongly negative (upward) with small dy to floor, the discriminant could go negative — code falls back to `99` (never lands), which means that particle just fades out mid-air. Fine for now but fragile under further velocity tuning.
- **Lever hit area** is the entire lever canvas. Clicking anywhere maps to an angle. No radius check on the knob itself. User said this was fine but if it gets changed, preserve the "click anywhere on canvas to set angle" behavior.
- **Bullet motion-blur streak** at low fps extends beyond the scene-space SCN_W bounds before being clipped by the ctx.scale scope. If the streak math changes, verify it doesn't paint outside the stage canvas.
- **Scene-end fade (0.82-1.0)** is applied in two places: inside `drawParticles` and around `drawImpactFlash`/`drawBullet` via `globalAlpha`. If another scene element is added to `drawScene`, remember to wrap it in the same fade so it doesn't pop.

## Context for Next Session

- **ITD-020 v8 is the shipped version.** `generic/itd-020-slow-motion_v8.html`. Opens cleanly, loop feels complete, fall settles on floor before reset.
- **The lever is literally a lever** — pivoting arc with gold knob. User specifically requested this form factor after rejecting horizontal sliders.
- **Apple visibility during pause state** was the last fix: pause gap now rests on t=0 (intact apple) not t=1.0 (exploded). If you see the exploded-state lingering, check `inPauseGap ? sceneT = 0.0`.
- **Subject pipeline:** rejected subjects so far were droplet, mousetrap (as the rejected v1-v4 scene), hummingbird (dismissed as too hard to render procedurally). Accepted: electric arc, bullet-through-apple. If you need another subject, avoid naturalistic organic forms and favor geometric/procedural.
- **Preset labels are the user's touch:** `phone camera / action cam / broadcast / industrial / science lab / ballistics / impact research / the ceiling`. Keep this tone — concrete + slightly cheeky — for any future preset contexts.
- **Continuous lever + discrete presets** is the pattern. Lever drags freely in log fps space, presets snap and highlight only when within 3% of the preset value.
- **20,000 fps is the cap.** User explicitly capped this. Don't go higher.
- **5 ms is the canonical physical event duration** for slow-mo demos in this series. Gives 2× magnification at 60 fps (a blink) and 666× at 20k (3.3 s viewer). If you pick a different subject, target a physical duration that works across that range.
