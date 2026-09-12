# Game Overview

## What is DBZ LSW Fangame?

**DBZ LSW Fangame** is an independent, open-source, community-driven recreation of _Dragon Ball Z: Legendary Super Warriors_ (Game Boy Color).

The project is not trying to create a generic Dragon Ball battle game. Its primary target is the distinctive combat identity of _Legendary Super Warriors_: card-driven decisions, separate Attack and Defense phases, fighter/form compatibility, tactical position, CC/Ki/resource management, Stage commands, Support/Defense responses and GBC-style battle choreography.

## Two kinds of canon

The project deliberately distinguishes:

### Original-game canon

Behaviour established from the GBC ROM/data, reproducible traces or reliable supporting sources.

### Fangame canon

Intentional project decisions about architecture, UI, presentation and adaptation where a modern recreation does not reproduce the original shell one-for-one.

A fangame design choice must never be documented as though the original ROM did it.

## Project goals

The project aims to preserve the systems that define the original game while making the recreation maintainable on modern systems:

- the original card-driven combat grammar;
- Attack/Defense decision boundaries;
- fighter/form compatibility and loadout structure;
- ROM-backed timing/mechanics where demonstrated;
- physical action/FX provenance where public-safe;
- faithful character/action sequencing where evidence exists;
- reproducible reverse-engineering evidence;
- deterministic modern runtime/testing;
- modern rendering and application structure;
- an open contribution surface that does not distribute a ROM.

## What is modernized?

The recreation is **not** a ROM emulator frontend. It reimplements the game systems in a modern application stack and uses ROM research as the reference/evidence source.

The architecture is broadly:

```text
player / AI decision
        ↓
BattleRuntime / Engine
        ↓
authoritative events
        ↓
GBC-timed presentation timeline
        ↓
PixiJS battle presentation
        ↓
modern React application shell
```

This gives the project a modern renderer, scalable viewport, tooling and accessible UI while still allowing ROM-backed timing and choreography to drive the battle presentation.

## Determinism is a project property

The fangame uses deterministic state/RNG plumbing for reproducible tests and debugging.

That is an implementation choice of this project. It is **not**, by itself, proof that every internal randomness source matches the original GBC algorithm byte-for-byte. Exact ROM randomness/timing parity is tracked separately when relevant.

## What is not a project goal?

The project does not aim to:

- redistribute the original ROM;
- call the whole game "ROM exact" while scoped gaps remain;
- let React/UI timers become a second gameplay engine;
- replace evidence-backed behaviour with plausible visual guesses;
- force every runtime semantic pose to masquerade as a dedicated ROM physical sequence;
- reproduce every original Story/navigation interaction when the fangame intentionally uses a streamlined scene-driven Story format.

That final point is an adaptation choice of this project, not a claim that the original GBC game lacked exploration/navigation systems.

## Current maturity

The combat architecture and data model are substantially developed. The main challenge is **end-to-end fidelity**: getting already-known ROM mechanics, sequence selection, frame timing, screen motion, FX and cleanup all the way into the production BattleScreen without legacy approximations taking over.

For the changing public baseline, see:

- [Project Status](../PROJECT_STATUS.md)
- [Roadmap](../ROADMAP.md)
- [Open issues](https://github.com/smouj/dbzlsw-fangame/issues)

## Technology

The active implementation uses:

- **TypeScript** — gameplay/runtime and research tooling;
- **React** — application shell and UI;
- **PixiJS** — battle rendering/presentation;
- **Vite** — development/build;
- **Vitest** — unit and contract verification;
- **Playwright** — browser/E2E checks;
- a **Game Boy Color-oriented tick model** — deterministic battle/presentation timing.

---

[← Wiki Home](README.md) · [Gameplay →](GAMEPLAY.md)
