# Implementation Tasks

## Phase 0 — Project foundation
- [ ] Initialize Vite + JavaScript project
- [ ] Add PlayCanvas Engine
- [ ] Create responsive desktop/mobile shell
- [ ] Initialize WebGL 2 renderer
- [ ] Detect optional WebGPU capability
- [ ] Add 2D fallback shell
**Exit:** App starts on desktop and mobile browsers.

## Phase 1 — 3DGS receipt
- [ ] Produce or acquire roll-only GS asset
- [ ] Confirm asset format loads in target engine
- [ ] Implement GS asset loader
- [ ] Set camera and coordinate conventions
- [ ] Prepare short, medium and full paper states
- [ ] Implement state switching and transitions
- [ ] Measure mobile GPU and memory usage
**Exit:** Roll and extended-paper states render reliably.

## Phase 2 — SVG printing
- [ ] Create receipt SVG template
- [ ] Define paper-plane coordinate mapping
- [ ] Render title, separators, question and choices
- [ ] Render correctness and explanation
- [ ] Implement progressive print timeline
- [ ] Test alignment at multiple camera angles and viewport sizes
**Exit:** Dynamic text appears attached to the receipt and remains legible.

## Phase 3 — Quiz engine
- [ ] Load quiz JSON
- [ ] Validate schema and references
- [ ] Implement question progression and choice input
- [ ] Implement answer evaluation and score
- [ ] Track answer history
- [ ] Implement explanation
- [ ] Implement five-question completion and result receipt
**Exit:** Five-question quiz completes independently of 3D animation.

## Phase 4 — Integration
- [ ] Connect receipt and quiz state machines
- [ ] Synchronize paper extension with print timeline
- [ ] Disable input outside WAIT_ANSWER
- [ ] Add next-question transition and finish state
- [ ] Preserve quiz state during 2D fallback
**Exit:** Complete end-to-end quiz experience.

## Phase 5 — Device QA and optimization
- [ ] Desktop Chrome
- [ ] Android Chrome
- [ ] iOS Safari
- [ ] Touch and pointer behavior
- [ ] Text legibility at narrow widths
- [ ] Asset size, loading time, frame time and memory
- [ ] Context-loss and asset-failure fallback
- [ ] Reduced-motion behavior
**Exit:** Five questions can be completed on representative desktop and mobile devices.

## Phase 6 — WASM evaluation
- [ ] Profile standard asset loading
- [ ] Compare candidate formats
- [ ] Identify measured bottleneck or required decoder
- [ ] Prototype WASM only for that requirement
- [ ] Compare load time, frame time and memory
- [ ] Document adopt/reject decision
**Exit:** WASM is adopted only with evidence of a requirement or measurable benefit.

## First vertical slice
1. Load one roll GS asset.
2. Show one extended-paper state.
3. Align an SVG overlay.
4. Print one question and three choices.
5. Accept an answer.
6. Print correctness and explanation.

Do not begin custom WASM or five-question polish until this slice works.
