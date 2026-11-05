# Animation State Model

## States
| State | Visual behavior | Exit |
|---|---|---|
| IDLE | Roll waits in view | Start |
| UNROLL | Paper extends from roll | Paper reaches target length |
| PRINT_QUESTION | Question prints progressively | Text complete |
| PRINT_CHOICES | Choices print progressively | Text complete |
| WAIT_ANSWER | Choice controls enabled | User selects |
| REVEAL | Correctness and explanation print | Reveal complete |
| NEXT | Paper advances / next segment prepared | Next question available |
| FINISH | Final score receipt prints | Session ends |
| ERROR_FALLBACK | 2D receipt mode | Continue quiz |

## Transition rules
- Only WAIT_ANSWER accepts input.
- Disable duplicate input immediately after a selection.
- Correctness is computed by quiz engine, not animation code.
- Animation completion events advance the state machine.
- A rendering failure switches presentation to ERROR_FALLBACK without resetting quiz progress.
- After the last question, transition to FINISH instead of NEXT.

## Ownership
- Quiz engine: question index, selected choice, correctness, score, answers.
- Receipt controller: paper state and GS asset transitions.
- Print timeline: timed SVG reveal.
- App controller: coordinates state transitions.

## Timing
Use a centralized timeline/clock abstraction. Avoid independent timers in each UI component. Timing values come from defaults and optional per-question JSON overrides.

## Input and accessibility
- Touch and pointer supported.
- Keyboard selection should be supported where practical.
- Respect reduced-motion preference by shortening or skipping non-essential transitions.
- Never require a timed response.
