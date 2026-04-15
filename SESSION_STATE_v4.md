---
workflow_step: v4_baseline_shipped_awaiting_review
agent_type: execute
token_budget: deep
last_updated: 2026-04-14
---

# SESSION_STATE: idt-blog-itds

**Last Updated:** 2026-04-14 (evening)
**Session:** v3 redesign + v4 Ciamac retint across all 14 ITDs

## Current State

All 14 ITDs shipped at v4 (ITD-004 at v5). These are the new series baseline, structurally unified and retinted to Ciamac's warm gold `#ffd94d`. Source v2/v3 files preserved. No git commits yet. Preview server running at 127.0.0.1:8090.

## What Was Done This Session

1. **v2 -> v3 design-system upgrade (14 files).** Dispatched 7 parallel agents. Each redesigned a batch to a new design token system: DM Sans + JetBrains Mono, CSS variables (`--gold`, `--bg`, `--surface`, `--border`, etc.), `.itd-tag` gold display label, noise overlay (SVG feTurbulence), `fadeUp` animation on entry, `.panel` with hover lift, `.itd-footer` with ciamac.com link. Stripped every IDT / idtcameras.com reference in body copy. Specs strip "Source" relabeled to "Author" with value `ciamac.com`. JavaScript preserved byte-identical across every file.

2. **Course correction.** Ciamac asked: "what are my colors for ciamac.com? should we think of its own art direction? should all my ITDs look the same?" The v3 pass used IDT's olive gold `#E8B600` under a ciamac.com label. That tension exposed a missed decision.

3. **Design direction locked.** Hybrid method: one typographic system, one substrate, one structural grammar, flexible accent per ITD. Series baseline accent is Ciamac warm gold `#ffd94d` (matches the main site's accent). Per-ITD bespoke art direction deferred to a later pass.

4. **v3 -> v4 retint (14 files).** Dispatched 4 parallel agents. Mechanical color swap of every `#E8B600`, `#f0d060`, and `rgba(232,182,0,*)` literal across CSS AND inline JS canvas colors. 165 total substitutions. Every v4 file verified to contain `#ffd94d` and zero olive-gold remnants.

5. **Memory updated.** Added `reference_ciamac_brand_colors.md` (site palette reference) and `project_itd_design_system.md` (hybrid direction decision).

## File Inventory (ITDs)

| ITD | Latest | Topic |
|---|---|---|
| 002 | v4 | SDI Signal Path |
| 003 | v4 | State Machine |
| 004 | v5 | FPS vs Resolution |
| 005 | v4 | Camera Placement |
| 006 | v4 | Stereo PIV |
| 007 | v4 | Sensor Readout |
| 008 | v2 (unchanged, per user) | Bit Depth |
| 009 | v4 | Exposure vs Motion Blur |
| 010 | v4 | Pixel Size |
| 011 | v4 | Temporal Resolution |
| 012 | v4 | Connection Topology |
| 013 | v4 | Trigger Modes |
| 014 | v4 | High Dynamic Range |
| 015 | v4 | XDR |
| 016 | v4 | XSLink Hub |

## Design System (v4 tokens)

- Background `#09090b`, surface `#0f0f12`, surface-raised `#131318`
- Accent gold `#ffd94d` (Ciamac warm), gradient pair to `#fff1a5`
- Borders `rgba(255,255,255,0.06)` default, `0.1` hover
- Text `#c8c8d0` body, `#6a6a78` dim, `#3e3e4a` muted
- Red `#ef4444`, green `#22c55e`, cable blue `#4080D0` (ITD-012 semantic)
- Radius `14px` large, `8px` small
- Fonts: DM Sans (display/body), JetBrains Mono (data/labels)
- Noise overlay: SVG feTurbulence, opacity 0.03, z-index 9999
- Animation: `fadeUp 0.6s cubic-bezier(0.22, 1, 0.36, 1)` with staggered delays on panels

## Next Actions

1. Ciamac reviews v4 baseline in browser (ITD-014 and ITD-012 already open at 127.0.0.1:8090).
2. If baseline lands: pick a pilot ITD for per-ITD art direction pass. Candidates: ITD-014 HDR (luminance gradient accent), ITD-006 Stereo PIV (anaglyph cyan/magenta), ITD-012 Connection Topology (already semantic).
3. Update gallery (`index_v5.html` or new `index_v6.html`) to point to v4 files instead of v2/v3.
4. Commit the v3 + v4 batch to git when Ciamac confirms.
5. If the per-ITD pass happens, establish a playbook doc so the method is repeatable.

## Blockers

- No git commits yet. Ciamac should eyeball v4 before we commit the pile.
- Per-ITD art direction deferred. No pilot picked yet.
- `SDI_HighSpeed_Cameras_Preview.pdf` and `console-workflow_v1.html` are untracked files from a prior session, unrelated to this work. Leave alone.

## Fragile Areas

- ITD-012 drag-and-drop depends on exact class names / JS-hardcoded `CONN_COLORS` hex values. Retint swapped `CONN_COLORS.fiber` and `rtv` color to `#ffd94d`. Red/blue/green cable colors preserved.
- ITD-013 ring-buffer animation uses `requestAnimationFrame` timing; retint only touched color string literals.
- ITD-014 HDR scene canvas uses tone-mapped literals that do NOT include IDT gold, so the retint there only hit UI chrome (gradient headers, tags, footer).
- ITD-004 has two em dashes inside preserved JS comments (byte-identical source). The em-dash ban applies to authored text, not protected script.

## Context for Next Session

- The v3 files are kept as a snapshot of the IDT-gold version. v4 is the Ciamac-gold baseline.
- The `/tmp/itd_v3_design_system.md` and `/tmp/itd_v4_retint_spec.md` specs exist and were used this session. They can be deleted or kept as playbook drafts.
- Design direction decision is now in memory as `project_itd_design_system.md`. Any future ITD should start from `#ffd94d` baseline, not IDT olive.
- Preview server is running in background (bash id boq9e7aa8) on 127.0.0.1:8090. Kill it when done with review.
