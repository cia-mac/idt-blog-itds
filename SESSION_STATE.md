---
workflow_step: gallery_complete_blog_posts_pending
agent_type: execute
token_budget: deep
last_updated: 2026-04-04
---

# SESSION_STATE: idt-blog-itds
**Last Updated:** 2026-04-04 (late PM)
**Session:** ITD Series Buildout: 7 New Diagrams + Gallery

## What Was In Progress
Nothing in progress. All 13 ITDs complete. Gallery updated.

## Completed This Session
- ITD-007: Sensor Readout (itd-007-sensor-readout_v1.html + blog post)
- ITD-008: Bit Depth (itd-008-bit-depth_v1.html)
- ITD-009: Exposure vs Blur (itd-009-exposure-blur_v1.html)
- ITD-010: Pixel Size (itd-010-pixel-size_v1.html)
- ITD-011: Temporal Resolution (itd-011-temporal-resolution_v1.html)
- ITD-012: Connection Topology (itd-012-connection-topology_v1.html)
- ITD-013: Trigger Modes (itd-013-trigger-modes_v1.html)
- ITD-016: XSLink Hub (itd-016-xslink-hub_v1.html)
- Gallery: index_v4.html (all 13 ITDs, ITD-012 featured)

## Previously Completed (prior session)
- ITD-002: SDI Signal Path (itd-002-sdi-signal-path_v1.html + blog post)
- ITD-003: State Machine (itd-003-state-machine_v1.html + blog post)
- ITD-004: FPS vs Resolution (itd-004-fps-resolution_v2.html + blog post)
- ITD-005: Camera Placement (itd-005-camera-placement_v1.html + blog post)
- ITD-006: Stereo PIV (itd-006-stereo-piv_v1.html + blog post)

## Design System
- Background: #0c0c0c, Gold accent: #E8B600, Red/CCM: #D94040, Blue/Fiber: #4080D0, Green: #40B060
- Fonts: JetBrains Mono (labels/data), DM Sans (body) via Google Fonts CDN
- Self-contained HTML, inline CSS/JS, zero external dependencies
- Canvas-based with requestAnimationFrame, IntersectionObserver, DPR handling

## Next Actions
1. Write blog posts for ITD-008 through ITD-013 and ITD-016 (only 002-007 have posts)
2. Deploy all ITD files to idtcameras.com /itd/ path
3. Remaining concepts: ITD-014 (Weight vs Capability), ITD-015 (Processor Channel Allocation)

## Blockers
None.

## Key Decisions
- ITDs dual-use: IDT blog content + Ciamac personal LinkedIn (2-4/month)
- Posted from Ciamac's account to build his audience, not from IDT
- No content production business. Taste + speed as competitive edge.
- Fixed container aspect-ratio (1.15) for ITD-004 sensor window
- ITD-005 accuracy audit: removed fabricated 200G CCM spec, FOV is lens-dependent
- ITD-004 v1 (scatter plot) superseded by v2 (camera selector grid)
