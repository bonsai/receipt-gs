# PRD — ReceiptGS MVP

**Version:** 0.1.0  
**Status:** MVP scope confirmed  
**Target:** PC + Smartphone Web Browser

## 1. Product
ReceiptGS is an interactive quiz experience in which a thermal receipt unrolls from a paper roll, prints a question and choices, accepts an answer, and prints the result.

3D Gaussian Splatting (3DGS) provides the volumetric appearance of the roll and paper. SVG provides crisp, dynamic text and UI.

## 2. Problem
Conventional quiz interfaces look like forms. ReceiptGS makes the receipt itself the interface, adding a tangible reveal and print sequence while keeping text readable.

## 3. MVP users and journey
1. Open the web page and see a receipt roll.
2. Start the experience.
3. The receipt unrolls.
4. The question and choices print progressively.
5. The user selects one answer by touch or pointer.
6. Correctness and explanation print.
7. The next question is presented.
8. After five questions, a result receipt is printed.

## 4. Scope
### P0
- PC and smartphone browser support
- 3DGS receipt roll and unrolling states
- SVG text overlay
- Progressive print animation
- JSON quiz loading and validation
- Single-choice answers
- Correctness, explanation, score
- Five-question session and final receipt
- Touch and pointer input
- 2D fallback if 3D initialization fails

### Out of scope
- Accounts, cloud persistence, leaderboards
- Quiz authoring CMS
- Multiplayer
- Real-time paper physics
- Continuous Gaussian deformation
- Custom 3DGS training or rendering engine

## 5. Functional requirements
| ID | Requirement | Priority |
|---|---|---|
| FR-01 | Load and display roll GS asset | P0 |
| FR-02 | Show roll-to-paper unfolding sequence | P0 |
| FR-03 | Render crisp SVG text on paper | P0 |
| FR-04 | Animate question and choice printing | P0 |
| FR-05 | Load quiz from JSON | P0 |
| FR-06 | Accept one choice by touch/pointer | P0 |
| FR-07 | Evaluate answer and update score | P0 |
| FR-08 | Print explanation and correctness | P0 |
| FR-09 | Run five questions and print final result | P0 |
| FR-10 | Adapt layout and controls to mobile | P0 |
| FR-11 | Fall back to 2D when 3D fails | P0 |
| FR-12 | Low-performance mode | P1 |
| FR-13 | Sound effects | P2 |

## 6. Non-functional targets
- WebGL 2 baseline; WebGPU optional when supported and stable.
- Performance target: 60fps desktop, 30fps mobile; validate on real devices.
- Initial GS asset budget target: 8 MB total, subject to visual testing.
- No backend required for the MVP.
- Quiz content and renderer must remain independent.
- Text remains readable at common mobile viewport sizes.
- Asset loading failure must not block quiz play.

These are targets, not verified results.

## 7. Acceptance criteria
- A user can complete five questions.
- Receipt visibly unrolls from a roll.
- Question, choices, correctness and explanation appear as print output.
- Text remains legible on desktop and mobile.
- Answer controls work with touch and pointer.
- Quiz remains playable in 2D fallback mode.
- Performance and memory are measured on representative devices.

## 8. First vertical slice
Roll visible → paper extends → one question prints → three choices → answer → result and explanation print. Complete this before expanding to five questions.
