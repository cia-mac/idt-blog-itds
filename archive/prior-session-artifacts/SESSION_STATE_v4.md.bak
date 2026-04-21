---
workflow_step: v4_baseline_committed_split_done
agent_type: execute
token_budget: deep
last_updated: 2026-04-14
---

# SESSION_STATE: idt-blog-itds

**Last Updated:** 2026-04-14 (evening, post-commit)
**Session:** v3 redesign + v4 Ciamac retint + IDT/generic bucket split + index_v6 + git commit
**Last commit:** `75d9d9b` — "Ship v4 Ciamac-gold ITD baseline, split into idt-specific and generic"

## Current State

All 14 ITDs shipped at v4 (ITD-004 at v5). Files now physically split into two buckets:

- `idt-specific/` — 6 ITDs tied to IDT products or IDT-proprietary features. These cannot ship under ciamac.com as pure portfolio pieces without IDT context.
- `generic/` — 9 ITDs covering high-speed imaging concepts that stand alone as educational content. Safe to host under ciamac.com or syndicate anywhere.

Gallery indexes (`index_v1` through `index_v5`) still live at the repo root and reference the old flat paths. They need updating to point into the new buckets.

## What Was Done This Session

1. **v2 -> v3 design-system upgrade (14 files).** Dispatched 7 parallel agents. Each redesigned a batch to DM Sans + JetBrains Mono, CSS variables, `.itd-tag` gold display label, noise overlay, `fadeUp` animation, `.panel` hover lift, `.itd-footer` with ciamac.com link. Stripped every IDT / idtcameras.com reference in body copy. Specs strip "Source" relabeled to "Author" = `ciamac.com`. JavaScript preserved byte-identical across every file.

2. **Course correction.** Ciamac asked: "what are my colors for ciamac.com? should we think of its own art direction? should all my ITDs look the same?" The v3 pass used IDT's olive gold `#E8B600` under a ciamac.com label.

3. **Design direction locked.** Hybrid: one typographic system, one substrate, one structural grammar, flexible accent per ITD. Baseline accent `#ffd94d` (Ciamac warm gold). Per-ITD bespoke art direction deferred.

4. **v3 -> v4 retint (14 files).** Dispatched 4 parallel agents. Mechanical swap of every `#E8B600`, `#f0d060`, and `rgba(232,182,0,*)` literal across CSS AND inline JS canvas colors. 165 total substitutions.

5. **IDT vs generic split (2026-04-14 evening).** Grep audit of all v4 files for IDT product/feature references (IDT, Phoenix, Galileo, XSM, CCM, CrashCam, XSLink, XStream, Helios, SugarCube, OS II, XS II, RT V/IV/III, Viper, XDR). Moved all versions (v1 through latest) of each ITD into `idt-specific/` or `generic/` subdirectories. Blog-post drafts moved with their ITDs.

6. **Memory updated.** Added `reference_ciamac_brand_colors.md` and `project_itd_design_system.md`.

## File Inventory

### `idt-specific/` (6 ITDs)

| ITD | Latest | Topic | Why IDT-specific |
|---|---|---|---|
| 004 | v5 | FPS vs Resolution | References IDT camera models |
| 005 | v4 | Camera Placement | References IDT product configurations |
| 010 | v4 | Pixel Size | Preset names reference Helios, XS II, etc. |
| 012 | v4 | Connection Topology | Full IDT product palette in interactive |
| 015 | v4 | XDR | XDR is IDT proprietary feature name |
| 016 | v4 | XSLink Hub | XSLink Hub is the subject itself |

### `generic/` (9 ITDs)

| ITD | Latest | Topic |
|---|---|---|
| 002 | v4 | SDI Signal Path |
| 003 | v4 | State Machine |
| 006 | v4 | Stereo PIV |
| 007 | v4 | Sensor Readout |
| 008 | v2 (unchanged, per user) | Bit Depth |
| 009 | v4 | Exposure vs Motion Blur |
| 011 | v4 | Temporal Resolution |
| 013 | v4 | Trigger Modes |
| 014 | v4 | High Dynamic Range |

### Root (untouched)

- `index_v1` through `index_v5` — gallery pages, still reference flat paths
- `SESSION_STATE.md`, `SESSION_STATE_v3.md`, `SESSION_STATE_v4.md`
- `SDI_HighSpeed_Cameras_Preview.pdf`, `console-workflow_v1.html` — untracked from prior sessions, leave alone

## Design System (v4 tokens)

- Background `#09090b`, surface `#0f0f12`, surface-raised `#131318`
- Accent gold `#ffd94d` (Ciamac warm), gradient pair `#fff1a5`
- Borders `rgba(255,255,255,0.06)` default, `0.1` hover
- Text `#c8c8d0` body, `#6a6a78` dim, `#3e3e4a` muted
- Red `#ef4444`, green `#22c55e`, cable blue `#4080D0` (ITD-012 semantic)
- Radius `14px` large, `8px` small
- Fonts: DM Sans (display/body), JetBrains Mono (data/labels)
- Noise overlay: SVG feTurbulence, opacity 0.03, z-index 9999
- Animation: `fadeUp 0.6s cubic-bezier(0.22, 1, 0.36, 1)` with staggered delays

## Next Actions

1. Ciamac eyeballs `index_v6.html` in browser. Confirm featured pick (ITD-014 HDR), section labels, and the two-bucket hierarchy read right.
2. Decide hosting strategy: `generic/` set likely lives under ciamac.com portfolio; `idt-specific/` set stays with IDT blog pipeline (currently on ice).
3. Push to GitHub. No remote configured yet on this repo. Decide if it lives under cia-mac private.
4. Pick pilot ITD for per-ITD art direction pass. Candidates from `generic/`: ITD-014 HDR (luminance gradient accent), ITD-006 Stereo PIV (anaglyph cyan/magenta). From `idt-specific/`: ITD-012 Connection Topology (already semantic).
5. If per-ITD pass happens, establish a playbook doc so the method is repeatable.

## Blockers

- No git remote. Repo is local-only. Push target undecided.
- Older `index_v1` through `index_v5` still reference flat root paths. They are preserved as snapshots but their links 404 now. Treat them as read-only history.
- Per-ITD art direction deferred. No pilot picked.

## Fragile Areas

- ITD-012 drag-and-drop depends on exact class names / JS-hardcoded `CONN_COLORS` hex values. Retint swapped `CONN_COLORS.fiber` and `rtv` to `#ffd94d`. Red/blue/green cable colors preserved.
- ITD-013 ring-buffer animation uses `requestAnimationFrame` timing; retint only touched color string literals.
- ITD-014 HDR scene canvas uses tone-mapped literals that do NOT include IDT gold, so the retint there only hit UI chrome.
- ITD-004 has two em dashes inside preserved JS comments (byte-identical source). The em-dash ban applies to authored text, not protected script.
- File paths changed this session. Any external link, docs reference, or gallery page pointing to `itd-XXX-*_v4.html` at the repo root is now broken. Update to `idt-specific/` or `generic/` subdir.

## Context for Next Session

- v3 files are kept as the IDT-gold snapshot. v4 is the Ciamac-gold baseline.
- The `/tmp/itd_v3_design_system.md` and `/tmp/itd_v4_retint_spec.md` specs exist and were used this session. Keep as playbook drafts.
- Design direction decision is in memory as `project_itd_design_system.md`. Any future ITD starts from `#ffd94d` baseline, not IDT olive.
- Split decision: if a future ITD depends on IDT product names or IDT-proprietary features, it belongs in `idt-specific/`. If it teaches a concept that stands alone, `generic/`.
- Preview server from earlier this session (bash id `boq9e7aa8`) was running on 127.0.0.1:8090. Paths it was serving are now stale post-split; restart if needed.
- IDT work is on ice as of 2026-04-14 per standing memory. The `idt-specific/` bucket is therefore on ice too until lifted. `generic/` is safe to continue developing.
