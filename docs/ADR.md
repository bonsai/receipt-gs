# Architecture Decision Records

## ADR-001: Rendering engine
**Decision:** Use PlayCanvas Engine for the MVP.

**Reasoning:** It provides browser rendering infrastructure and Gaussian Splatting support, avoiding a custom renderer. WebGL 2 is the baseline; WebGPU is an optional capability, not a requirement.

**Alternatives:** Three.js with a compatible splat renderer; custom WebGL/WebGPU renderer.

**Revisit when:** required mobile browser support or asset formats prove incompatible.

## ADR-002: Separate 3D appearance from dynamic text
**Decision:** 3DGS renders the roll, paper curvature, shading and appearance. SVG renders all dynamic text and crisp UI.

**Reasoning:** Text embedded in a trained splat asset would be expensive to update for each quiz. SVG preserves legibility and content independence.

**Constraint:** Define a stable paper-plane coordinate system and map SVG coordinates to the projected paper surface. A simple screen-space overlay is acceptable only while camera motion is constrained; perspective-correct placement must be tested.

## ADR-003: Unrolling representation
**Decision:** MVP uses discrete GS states, not continuous physical deformation.

Initial asset states:
- roll-only
- paper-short
- paper-medium
- paper-full

Use transitions/crossfades and synchronized SVG reveal. Keep coordinate frame, scale, orientation and camera framing consistent across assets.

**Reasoning:** This reduces implementation and mobile performance risk.

**Future options:** mesh-coupled Gaussian deformation, deformable 3DGS, or pre-rendered flipbook sequence.

## ADR-004: WASM scope
**Decision:** Do not build custom WASM before profiling.

Start with the engine's supported asset loading path. Add a WASM decoder or processor only if a selected format or measured bottleneck requires it. Keep quiz state, SVG, and orchestration in JavaScript.

**Reasoning:** WASM is not inherently faster for all browser tasks and adds build/debug complexity.

## ADR-005: Content format
**Decision:** Use versioned JSON files for quiz content. No database or backend in MVP.

**Reasoning:** Static content is sufficient for a five-question demonstration and is easy to version-control.

## ADR-006: Progressive enhancement
**Decision:** 3D rendering is an enhancement, not a prerequisite for quiz completion. Provide a 2D receipt fallback.

**Reasoning:** Mobile GPU limits, browser differences and context loss must not make the quiz unusable.
