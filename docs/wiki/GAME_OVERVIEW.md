# Game Overview

## What is DBZ LSW Fangame?

**DBZ LSW Fangame** is an independent, open-source, community-driven recreation of _Dragon Ball Z: Legendary Super Warriors_ (Game Boy Color).

The project is not trying to create a generic Dragon Ball battle game. Its primary target is the distinctive structure of _Legendary Super Warriors_: card-driven decisions, Attack and Defense phases, character positioning, resource management, Stage inputs, support/defense responses and GBC-style battle choreography.

## Project goals

The project aims to preserve the parts that define the original game while making the implementation maintainable on modern systems:

- deterministic combat;
- GBC-timed battle logic and presentation;
- the original card-driven combat grammar;
- reproducible ROM-backed research;
- faithful character/action sequencing where evidence exists;
- modern rendering and application structure;
- portable tests and verification tooling;
- an open contribution surface that does not distribute a ROM.

## What is being modernized?

The recreation uses a modern application stack and presentation layer rather than emulating the original Game Boy Color screen directly.

The active architecture is broadly:

```text
player / AI decision
        ↓
BattleRuntime / Engine
        ↓
deterministic events
        ↓
GBC-timed presentation timeline
        ↓
PixiJS battle presentation
        ↓
modern application UI
```

This lets the project reproduce original mechanics and timing while still using a modern renderer, scalable viewport, tooling and accessibility-oriented UI.

## What is not a project goal?

The project does not aim to:

- redistribute the original ROM;
- hide unverified behaviour behind "ROM exact" claims;
- turn Story mode into a free-roaming RPG if that is not part of the project's intended design;
- let React/UI timers become a second gameplay engine;
- replace evidence-backed behaviour with visual guesses simply because they look plausible.

## Current maturity

The combat architecture and data model are substantially developed. The main remaining challenge is not basic game existence but **end-to-end fidelity**: ensuring that ROM-backed timing, scenes, actors, projectiles, camera motion, physical frames and cleanup are actually consumed by the production battle view.

For the current public baseline, see:

- [Project Status](../PROJECT_STATUS.md)
- [Roadmap](../ROADMAP.md)
- [Open issues](https://github.com/smouj/dbzlsw-fangame/issues)

## Technology

The active implementation uses:

- **TypeScript** for gameplay/runtime and tooling;
- **React** for the application shell and UI;
- **PixiJS** for battle rendering;
- **Vite** for development/build;
- **Vitest** for unit and contract verification;
- **Playwright** for browser/E2E checks;
- a **Game Boy Color tick model** for deterministic timing.

---

[← Wiki Home](README.md) · [Gameplay →](GAMEPLAY.md)
