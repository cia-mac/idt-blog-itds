---
workflow_step: remote_and_pages_live_gallery_v17
agent_type: execute
token_budget: deep
last_updated: 2026-04-22
---

# SESSION_STATE: idt-blog-itds

**Last Updated:** 2026-04-22 (exit ritual)
**Session:** Multi-day autopilot + manual iteration. ITD-020 shipped, abandoned concepts archived, ITD-021 prototyped and rejected, ITD-008 / ITD-011 / ITD-014 iterated to v5/v6, gallery advanced index_v12 → v13 (prepared) → v14 → v15 → v16 → v17 (live), remote + Pages provisioned.
**Last committed:** `a405d8a` — "ITD-014 v6: upgrade HDR scene from flat rectangles to gradient+glow render"
**Branch:** main → `origin` at https://github.com/cia-mac/idt-blog-itds (public). GitHub Pages live at https://cia-mac.github.io/idt-blog-itds/ serving root `index.html` meta-refresh to `index_v17.html`.

## Current State

Working tree clean. Local and origin/main aligned at `a405d8a`. Repo has 12 commits ahead of the pre-session baseline `75d9d9b`.

### Live gallery

`index_v17.html` is current. `index.html` at the repo root is a meta-refresh redirect to v17 so the bare Pages URL serves the gallery. Every prior gallery version (v1 through v16) is preserved in repo root.

### Shipped ITDs this session arc

| ITD | Current file | What shipped |
|---|---|---|
| ITD-020 | `generic/itd-020-slow-motion_v8.html` | Slow-motion lever + bullet-through-apple. First lever-pattern ITD; canonical template for the rest. |
| ITD-008 | `generic/itd-008-bit-depth_v5.html` | Bit-depth demo with moving-ball scene, ground band, scene-aware histogram, unified light direction, gold retint. v3/v4 iterations also preserved. |
| ITD-011 | `generic/itd-011-temporal-resolution_v5.html` | Fps cap bumped 15k → 20k to match ITD-020/021 ceiling. Preset context labels + copy alignment. |
| ITD-014 | `generic/itd-014-hdr_v6.html` | HDR scene upgraded from flat rectangles to gradient + glow render. v5 fixed hidden olive-gold leak in histogram bars. |

### ITD-021: not in gallery

`generic/itd-021-crash-test_v1.html` was rebaselined by the owner to a new framing ("How Crash Tests Are Actually Measured", 50 ms crash, impact + airbag deploy + dummy kinematics). The three Claude prototypes (v1 pre-rebaseline, v2, v3 measurement-ruler angle) remain in the repo but are not linked from any gallery. An alternate v4 draft using ITD-020's playback-slowdown angle lives at `archive/abandoned-concepts/itd-021-crash-test_v4-draft-playback-angle.html`. `index_v13.html` was prepared to add ITD-021 to the Generic grid but was never promoted.

### Archive structure

- `archive/abandoned-concepts/` — ITD-017/018/019 (rejected concepts) + ITD-021 v4 draft. README documents each.
- `archive/prior-session-artifacts/` — stale untracked root files moved here on 2026-04-19: `SDI_HighSpeed_Cameras_Preview.pdf`, `SESSION_STATE_v4.md.bak`, `console-workflow_v1.html`. README documents each.

## Commit log (this session arc, on top of `75d9d9b`)

```
a405d8a  ITD-014 v6: upgrade HDR scene from flat rectangles to gradient+glow render
3e7a83a  SESSION_STATE: remote + Pages provisioned
58232a3  Add root index.html redirecting to current live gallery
e0ce8f3  ITD-014 v5: fix hidden olive-gold leak in histogram bars
016a3b2  ITD-011 v5: fps cap 15k -> 20k, preset context labels, copy alignment
7701a7b  Housekeeping: archive prior-session untracked artifacts
52e923a  ITD-008 v5: gold retint fixes, scene-aware histogram, unified light direction
19a939e  Housekeeping: ITD-008 moving-ball scene + gallery v11/v12 + ITD-021 rejection note
1173d75  Update SESSION_STATE for index_v13 commit
3494ba3  Gallery index_v13: add ITD-021 crash-test as New
e5289f2  Prototype ITD-021 crash-test: temporal resolution lever
da8b192  Archive abandoned ITD-017/018/019 concepts
caa1b39  Ship ITD-020 slow-motion lever with bullet-through-apple; v10 gallery
```

## Key Decisions

1. **Lever is the canonical interaction pattern.** One canvas, one pivoting arc lever, continuous log-fps mapping [60, 20000] with eight preset ticks. Established in ITD-020; carried to ITD-021 prototypes and back-propagated to ITD-011 (fps cap bump).
2. **Preset labels are shared across lever-based ITDs.** `phone camera / action cam / broadcast / industrial / science lab / ballistics / impact research / the ceiling`.
3. **20,000 fps is the hard cap.** Do not exceed.
4. **ITD-020 and ITD-021 teach different lessons with the same lever.** ITD-020: slow-motion = capture/playback ratio. The rejected ITD-021 prototypes tried "temporal measurement ruler"; the owner's rebaseline direction is "how crash tests are actually measured" over a 50 ms event.
5. **Remote provisioned public.** Pages on free tier requires public. Consistent with `overcrank`, `splat-desktop`, `idt-content-plan` which are also public for sharing intent. Global rule prefers private; override here was explicit for URL-sharing.
6. **Root URL strategy:** thin meta-refresh `index.html` points to the current gallery version. Bump the href each time a new `index_vN.html` becomes live. Preserves versioning discipline without forcing viewers to know the version number.

## Next Actions

1. **ITD-021 direction.** Owner-owned. v1 is being iterated with the new framing. Claude should stay out unless asked.
2. **Batch ITD v3→v5+ redesign for remaining files** (ITD-002/003/006/007/009/013 still at v4). The new bar is v5/v6 with scene-aware rendering, gradient+glow, unified light direction. Tracks with existing Notion task "Batch ITD v3 redesign (14 remaining files)" but scope has moved to "v5+".
3. **Custom domain on Pages** (optional). Currently `cia-mac.github.io/idt-blog-itds`. If ciamac.com/blog-itds or similar is desired, add a CNAME file and configure DNS.
4. **IDT-specific bucket is still dormant** per Luiz locked read. Six IDT-specific ITDs sit at v4/v5; not safe to share externally; not urgent.

## Blockers

- **IDT work on ice** per Luiz locked read (2026-04-14). `idt-specific/` bucket is dormant. `generic/` is portfolio-safe under ciamac.com.

## Fragile Areas

### Lever-pattern ITDs (ITD-020, ITD-021 prototypes)

- Preset active-state tolerance ratio 0.97-1.03.
- Log-scale fps mapping assumes FPS_MIN=60, FPS_MAX=20000 constants. Do not change these without updating TICK_FPS and subtitle copy.
- Lever hit area = entire lever canvas (click anywhere maps to angle). Preserve if refactoring.

### ITD-020 specific

- Analytic particle landing depends on `vy² + 2·GRAVITY·dy ≥ 0`. Falls back to 99 sentinel if negative.
- Bullet motion-blur streak at low fps extends beyond SCN_W before clip.
- Scene-end fade applied in two places (drawParticles + drawImpactFlash/drawBullet). New scene elements need the same fade.

### ITD-021 prototypes (v2/v3)

- Sampling quantization epsilon `+1e-6` in `floor(trueT * N + 1e-6)` avoids boundary bug. Don't remove.
- `lastSampledIdx` reset to -1 on lever change AND loop restart. Both resets must stay.
- Head rest Y = 176 is tuned to sit below roof polygon top (148).
- Airbag growth direction assumes WHEEL_CX=235, WHEEL_CY=258.

### Gallery / deployment

- `index.html` meta-refresh hardcodes the current gallery version. Bump the href when promoting a new `index_vN.html`.
- Pages rebuilds automatically on push to `main`. Usually green within 30-60 seconds.
- Repo is public; do not commit secrets.

## Context for Next Session

- **URL lives at** https://cia-mac.github.io/idt-blog-itds/. Gallery is v17. Ten generic diagrams visible. Six IDT-specific diagrams still on ice.
- **Lever template is established.** Copy ITD-020 v8 as the starting point for any new lever-based ITD.
- **Preset labels, 20k cap, log-fps mapping are invariants.** Do not change.
- **Gold is for measurement/emphasis, not the subject.** Heads, dummies, subjects render in muted tones. Gold carries the accent.
- **Version discipline is enforced.** Every file bumps version suffix. Previous versions stay in place. Deletions go to `archive/`.
