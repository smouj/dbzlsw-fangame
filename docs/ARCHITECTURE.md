# Architecture Direction

## Core rule

The project should have one gameplay authority and one time authority.

```text
UI / AI
   ↓ commands
BattleRuntime / Engine
   ↓ deterministic events
EventLog
   ↓
GBC-timed Presentation Timeline
   ↓
Pixi Presenter / Camera / Actors / FX / HUD-linked presentation
```

## Gameplay authority

React components and AI controllers may request legal commands, but must not independently calculate combat outcomes such as damage, RNG, QTE result, KO, card cost or defense semantics.

## Presentation authority

Gameplay-significant visuals should be functions of the timeline and GBC tick. Independent timers that can drift from combat state are architectural debt.

PixiJS is the intended authority for the battle framebuffer: fighters, camera, projectiles, FX, impacts and other synchronized combat presentation.

## Fidelity layering

A static descriptor being ROM-backed does not prove that production gameplay displays it correctly. The project therefore verifies multiple layers:

1. source/evidence descriptor
2. engine/runtime resolution
3. EventLog
4. presentation compilation/timeline
5. cue consumption
6. physical frame/resource mapping
7. browser-visible choreography

## Determinism

Given the same initial state, seed and command sequence, the engine-side result and event stream should be reproducible. Rendering may interpolate for display, but it must not become a gameplay authority.
