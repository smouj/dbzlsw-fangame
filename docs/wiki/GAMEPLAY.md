# Gameplay

DBZ LSW Fangame is built around **decision → resolution → next decision**. The player must regain control at the same class of boundaries where the original game expects a choice; presentation is not allowed to silently continue the match on its own.

## Core round flow

A normal player-controlled round is structured around two distinct phases:

```text
ROUND
│
├─ ATTACK PHASE
│  ├─ choose LIMIT / JOINT / BASIC / CHARA
│  ├─ resolve the accepted action
│  └─ stop at the next decision boundary
│
├─ DEFENSE PHASE
│  ├─ choose LIMIT / JOINT / BASIC response
│  ├─ resolve the incoming enemy action
│  └─ complete the round
│
└─ NEXT ROUND
```

When the runtime reaches a player-choice boundary, the game can wait indefinitely. A UI timer, cinematic callback or React effect must never invent the next gameplay command.

## What the player manages

During battle, the player manages connected systems including:

- **HP** — fighter health;
- **Ki** — energy used by applicable actions;
- **CC** — command/card currency;
- **hand/deck** — JOINT card flow;
- **five equipped LIMIT slots per member**;
- **tactical position** — FRONT/BACK and relevant vertical state;
- **power-window state** — required for LIMIT and used by other power-related rules;
- **active member/reserve** — in team battles;
- **Attack vs Defense phase** — changes command/card legality.

## Command grammar

The original top-level menus are phase-specific.

### Attack

```text
LIMIT
JOINT
BASIC
CHARA
```

### Defense

```text
LIMIT
JOINT
BASIC
```

`BASIC` contains phase-appropriate basic actions rather than being one universal attack button. The fangame maps these into the original action families, including Stage/Gather-style Attack actions and Guard/Move-style Defense responses where legal.

## Cards are selected from two different sources

### LIMIT

LIMIT uses one of the active member's equipped reusable cards and requires the power-window state.

### JOINT

JOINT uses the physical hand. The selected card is consumed/removed from that hand after a valid committed use.

This distinction is part of gameplay, not merely UI organization.

## Stage gameplay

Stage is a dedicated command-input family. The selected 3/4/5/6 Stage card determines the exact number of expected commands, and the input sequence runs under one position-dependent global GBC-tick deadline.

See [Stage Attacks](STAGE_ATTACKS.md) for the ROM-verified timing matrix and correction behaviour.

## Cinematic flow

Gameplay and cinematography are deliberately separated.

A resolved action may move through visual states such as:

```text
FIELD / tactical view
→ transition/preparation
→ ACTION shot
→ actor sequence
→ motion / projectile / FX
→ target reaction / impact
→ cleanup
→ FIELD
→ next control boundary
```

The visible movie follows the authoritative result; it does not decide hit/miss, damage, resources, tactical state, KO or the next phase.

## Match formats

The active battle model supports:

- **1v1**;
- **2v2**;
- active/reserve switching;
- reserve continuation after KO;
- deterministic rematches/testing.

The public setup UI can evolve during alpha without changing these battle-state contracts.

## Determinism and ROM fidelity

The fangame uses deterministic runtime/RNG plumbing so tests and reproductions are stable.

That should not be read as “the remake's internal RNG algorithm is automatically identical to every original GBC randomness source.” When exact ROM random/timing provenance is relevant, it is tracked as a separate fidelity question.

## Where to go next

- [Battle System](BATTLE_SYSTEM.md) — command legality, resources, position and authority.
- [Cards](CARDS.md) — the 125-card ROM data model.
- [Stage Attacks](STAGE_ATTACKS.md) — exact Stage command/timing contract.
- [Fidelity & ROM Research](FIDELITY_AND_RESEARCH.md) — what counts as demonstrated.

---

[← Game Overview](GAME_OVERVIEW.md) · [Battle System →](BATTLE_SYSTEM.md)
