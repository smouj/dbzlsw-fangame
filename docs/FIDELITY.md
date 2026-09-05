# Fidelity Model

The project separates **mechanical**, **temporal**, **physical** and **visible** fidelity. Passing a damage test is not enough to claim that an action reproduces the original GBC game.

## Evidence states

- **CONFIRMED** — directly supported by reproducible ROM/decomp/emulator evidence.
- **STRONG** — multiple consistent observations support the interpretation, but one layer remains unproven.
- **HYPOTHESIS** — plausible working theory; must not be presented as canonical behaviour.
- **PARTIAL** — a route works but a known piece of the physical/presentation contract remains unresolved.
- **NOT_APPLICABLE** — evidence shows that the expected concept does not apply.

## Combat completion contract

A combat action may be called complete only when all applicable layers are demonstrated:

1. legal command and resource rules
2. deterministic engine result
3. EventLog ordering
4. GBC tick boundaries
5. presentation timeline route
6. camera / shot / viewport behaviour
7. actor sequence and physical frames
8. target reaction and contact timing
9. projectile / FX lifecycle
10. damage / defense / KO synchronization
11. HUD / hand timing
12. clean recovery and return to the correct control boundary

If any required layer is unresolved, the action remains PARTIAL even if gameplay results are correct.

## No silent fallback

Fallbacks must be observable and classified. A verifier should fail when a formerly ROM-backed route silently becomes inferred/legacy, or when a new unresolved physical frame appears without an explicit reason.

## Determinism

For deterministic scenarios, the same initial state, seed and command sequence must produce equivalent state, EventLog and presentation timeline outputs.

## Visual evidence

Browser evidence should record enough state to explain *why* a frame is correct: tick, shot, viewport motion, actor/target frame or pose, positions, projectile state and control boundary where applicable.

Screenshots are useful evidence, but screenshots alone do not prove timing. See `docs/SCREENSHOTS.md`.
