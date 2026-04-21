---
workflow_step: itd_021_rejected_v12_remains_live_gallery
agent_type: execute
token_budget: deep
last_updated: 2026-04-19
---

# SESSION_STATE: idt-blog-itds

**Last Updated:** 2026-04-19 (post-autopilot)
**Session:** ITD-020 shipped + abandoned concepts archived + ITD-021 crash-test prototyped (v1 → v3). ITD-008 v3/v4 moving-ball scene updated in parallel by another session.
**Last committed:** `3494ba3` — "Gallery index_v13: add ITD-021 crash-test as New" (2026-04-19)
**Branch:** main → `origin` at https://github.com/cia-mac/idt-blog-itds (public). GitHub Pages live at https://cia-mac.github.io/idt-blog-itds/ serving via root `index.html` meta-refresh to `index_v12.html`.

## Current State

Three new commits this session on top of the previous baseline `75d9d9b`:

- `caa1b39` — Ship ITD-020 slow-motion lever with bullet-through-apple; v10 gallery (14 files)
- `da8b192` — Archive abandoned ITD-017/018/019 concepts (7 files)
- `e5289f2` — Prototype ITD-021 crash-test: temporal resolution lever (3 files)
- `3494ba3` — Gallery index_v13: add ITD-021 crash-test as New (1 file, based on parallel-session v12)

Parallel work on ITD-008 (v3 → v4 moving-ball scene) and the gallery (`index_v11.html` → `index_v12.html`) was done outside this Claude session and remains uncommitted.

### ITD-020: What Slow Motion Actually Is · `generic/itd-020-slow-motion_v8.html`

Shipped, committed, featured in the live gallery. Pivoting arc lever, continuous log-scale fps 60 to 20,000, bullet-through-apple scene, analytic particle landing, scene-end fade, intact-apple pause state. See prior SESSION_STATE_v5 for scene internals.

### ITD-021: The Camera Is A Ruler · `generic/itd-021-crash-test_v3.html` (prototype)

- **Concept:** crash-test as measurement instrument. 120 ms side-view frontal crash, airbag fires at 15 ms, peak head excursion at ~87 ms. Lever controls **sampling rate**, not playback slowdown. Playback duration fixed at 3.2 s.
- **Pedagogical distinction from ITD-020:** ITD-020 teaches "slow motion = capture/playback ratio." ITD-021 teaches "higher fps = finer temporal measurement." Same lever, different lesson.
- **Scene:** concrete wall on left (with horizontal slab lines), car cross-section (hood → windshield → roof → rear window → rear deck → wheels), dashboard, steering wheel (narrow ellipse for side view), seat with headrest, dummy torso (seatbelt diagonal in gold webbing), muted-gray head, airbag inflating from wheel hub up-right toward driver with fabric seam overlay.
- **Stats strip:** `Capture | Frames During Impact (hero, 7 → 2,400) | Between Samples (16.7 ms → 50 μs)`.
- **Trajectory visualization:** dotted gold ghost of true curve + gold sample dots at `i/N` positions + solid gold reconstructed line through dots up to current sampledT. Dot size scales down with N for dense readability.
- **Shutter flash:** gold-border vignette for 90 ms after each new captured frame OR after a lever change. At 60 fps reads as distinct "click, click" cadence. At 20 k reads as continuous glow.
- **Head quantization:** `sampledT = Math.min(1, floor(trueT * N + 1e-6) / N)`. Head freezes on each sample for `PLAYBACK_DURATION / N` wall seconds. At 60 fps that's ~457 ms per freeze (visibly stutters). At 5 k it reads smooth.
- **v1 → v3 iteration:**
  - v1: first pass. Scene composition weak (detached airbag, invisible torso, head floating). Peak-excursion error stat was a dud (≤ 0.2 mm at 60 fps) because the chosen peak time 0.72 coincided with the 5/7 sample.
  - v2: redrew scene as car cabin cross-section, added wall + wheels + windshield tint, recolored head to muted gray so gold reads as measurement overlay only, swapped stat to "Between Samples," added shutter-flash vignette.
  - v3: lowered `HEAD_REST_Y` from 162 → 176 so head no longer clips roof (148), brightened torso fill `#2c2c34` → `#3a3a44` for legibility against cabin window tint.
- **REJECTED after live review (2026-04-19).** The measurement-ruler framing did not land. Files (v1, v2, v3) remain in the repo and remain committed. `index_v13.html` was prepared to add ITD-021 to the Generic grid but was not promoted. **Live gallery is `index_v12.html`** (no ITD-021 card). A future session could either iterate to v4 with a different angle or leave the prototype as a reference.

### ITD-008 parallel work (outside this Claude session)

`generic/itd-008-bit-depth_v3.html` (first ball pass), `generic/itd-008-bit-depth_v4.html` (bigger ball, ground band, default view, relocated label). Gallery at `index_v11.html` (superseded) and `index_v12.html` (live, featuring ITD-020 hero + ITD-008 v4 link). These files are untracked and not included in any commit from this autopilot.

### Abandoned concepts (archived)

`archive/abandoned-concepts/` contains ITD-017 v1/v2 (tradeoff sliders, rejected), ITD-018 v1/v2 (dual timeline, superseded by ITD-020), ITD-019 v1/v2 (filmstrip, rejected). README in that folder captures the reasoning.

## What Was Done This Autopilot

1. Committed ITD-020 shipped artifacts + v10 gallery (`caa1b39`)
2. Moved abandoned ITD-017/018/019 files into `archive/abandoned-concepts/` with README, committed (`da8b192`)
3. Built ITD-021 v1 prototype (single canvas crash-test with lever-controlled sampling)
4. Audited v1 against the screenshot, identified: detached airbag, invisible torso, dud peak-error stat, gold-on-gold head
5. Built ITD-021 v2 addressing all four audit points (redrawn scene, muted-gray head, "Between Samples" stat, shutter-flash)
6. Tuned v2 → v3 (head below roof, torso brightness bump)
7. Committed ITD-021 v1/v2/v3 together with iteration narrative in commit body (`e5289f2`)
8. Added `idt-blog-itds` server to `~/.claude/launch.json` (python http.server on port 8090) for preview verification
9. Opened every version in preview and verified via screenshots + preview_eval state probes

## Next Actions

1. **Live-review ITD-021 v3.** Pull the lever across the range. Confirm peak excursion renders visibly around the 0.72 mark of each loop, that airbag covers head at peak, that stutter cadence feels instructive at 60 fps without reading as broken.
2. **Activate `index_v13.html`** if ITD-021 passes review. v13 adds the ITD-021 card to the Generic grid right after ITD-020, bumps hero count 16 → 17 and Generic count 10 → 11. Featured hero stays on ITD-020. **Caveat:** v13 is based on the parallel-session `index_v12.html` so it inherits the link to `itd-008-bit-depth_v4.html` which is still untracked. Fresh clones would 404 on that card until the parallel work is committed.
3. **Commit parallel-session ITD-008/gallery work.** `itd-008-bit-depth_v3/v4.html` and `index_v11/v12.html` are untracked. Separate commit, not this session's scope.
4. **Configure `cia-mac` GitHub remote + Pages.** Still blocked. Nothing shareable by URL yet.
5. **Housekeeping:** `SDI_HighSpeed_Cameras_Preview.pdf`, `SESSION_STATE_v4.md.bak`, `console-workflow_v1.html` are stale untracked files from prior sessions. Probably archive candidates.

## Blockers

- ~~No git remote~~ **Remote + Pages provisioned 2026-04-20.** `origin` = https://github.com/cia-mac/idt-blog-itds (public). Pages live at https://cia-mac.github.io/idt-blog-itds/. Root serves `index.html` which meta-refreshes to `index_v12.html` (the live gallery); bump that href when the gallery version advances. Repo is public to enable Pages on the free tier; switch to private only if a Pro/Team plan is active.
- **IDT work on ice** per Luiz locked read (2026-04-14). `idt-specific/` bucket dormant. `generic/` is safe to keep developing.

## Fragile Areas

### Shared with ITD-020

- Preset active-state tolerance (ratio 0.97-1.03), analytic particle landing, bullet motion-blur clipping, scene-end fade coupling. See SESSION_STATE_v5 for detail.

### ITD-021 specific

- **Sampling quantization epsilon.** `Math.floor(trueT * N + 1e-6)` deliberately avoids a boundary bug when `trueT === i/N` exactly. Do not remove the epsilon.
- **Shutter flash resets.** `lastSampledIdx` is reset to -1 both on lever change (`setFps`) and on loop restart (`animateScene` pause-gap exit). Any new trigger condition needs both resets to stay consistent.
- **Head rest Y = 176** is tuned to sit below the roof polygon top edge at y=148. If the car roof repositions, re-verify the head doesn't clip.
- **Airbag growth direction** assumes WHEEL_CX=235, WHEEL_CY=258, and inflates toward (cx + r·0.75, cy − r·0.55). Moving the wheel without rechecking this will push the airbag into the wrong scene element.
- **Playback duration is constant 3.2 s** in ITD-021 (vs fps-scaled in ITD-020). The two ITDs use the same lever for different mental models. Do not unify the playback math.
- **Timeline dot density:** at N > 400 the tick alpha drops to 0.22 and lineWidth to 0.5 so the bar reads as a progress fill rather than individual ticks. Below that threshold ticks are discrete. The threshold is visual not semantic; tune if it doesn't feel right.

## Context for Next Session

- **ITD-020 v8 is the canonical slow-motion demo.** ITD-021 v3 is the temporal-resolution companion. Two ITDs, one lever grammar, two lessons.
- **Head is muted gray in ITD-021 by design.** Gold is reserved for the measurement overlay (trajectory + sample dots + reconstructed line + timeline + shutter flash). Do not recolor the head gold.
- **Preset labels are verbatim shared** across ITD-020 and ITD-021: `phone camera / action cam / broadcast / industrial / science lab / ballistics / impact research / the ceiling`. Keep this across any new ITD in the series.
- **20,000 fps is still the cap.** Do not exceed.
- **120 ms is the canonical crash physical duration.** 5 ms for slow-mo. Subject determines duration; duration determines N at each fps.
- **Gallery is currently at `index_v12.html`** (parallel-session output). Not yet committed. If you start a new session, check whether the parallel work has been consolidated before writing `index_v13.html`.
