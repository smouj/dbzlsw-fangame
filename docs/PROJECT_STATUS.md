# Project Status

## Stage

**Public Development Preview / Alpha**

The active project has a mature internal implementation and verification corpus. The public repository is being populated through a clean-source process rather than by exposing the private research repository wholesale.

## What is already structurally established

The active architecture is based on:

- a deterministic battle/runtime authority
- a single Game Boy Color tick model for combat timing
- EventLog-driven presentation
- PixiJS for battle rendering
- ROM-backed descriptors and verification tooling
- automated tests for mechanics, presentation contracts and physical-resource provenance

## Current fidelity gap

Mechanical correctness is substantially ahead of visible fidelity.

Recent battle-level diagnosis showed that ROM-backed presentation cues can exist internally while the production viewport does not yet reproduce all camera/screen motion and choreography visibly. Remaining high-priority work includes actor-target synchronization, camera/shot application, projectile ordering, several partial physical sequences and full-battle E2E coverage.

For that reason this repository does **not** describe the game as visually frame-perfect or fully ROM-exact.

## Completion language

Project documentation should use these terms consistently:

- **PASS** — the claimed contract is demonstrated by the relevant evidence/gate.
- **PARTIAL** — useful implementation exists, but a known portion remains unresolved.
- **BLOCKED** — the required runtime path/evidence is absent or inaccessible.
- **PENDING EVIDENCE** — behaviour must not be invented until the original game is confirmed.
- **N/A** — no applicable original-game behaviour exists.

## Public source availability

The first sanitized application-source snapshot is a public bootstrap milestone. Until that lands, the repository primarily exposes governance, contribution rules, roadmap and research boundaries.
