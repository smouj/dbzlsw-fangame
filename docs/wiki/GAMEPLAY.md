# Gameplay

DBZ LSW Fangame is built around **decision → resolution → next decision**. The player is expected to remain in control at the boundaries where the original game asks for a choice; presentation must never silently advance the match on its own.

## Core round flow

A normal round is structured around two distinct phases:

```text
ROUND
│
├─ ATTACK PHASE
│  ├─ choose an offensive/action command
│  ├─ resolve preparation and action
│  └─ finish the player's action
│
├─ DEFENSE PHASE
│  ├─ choose a defensive response
│  ├─ resolve the enemy action with that response
│  └─ finish the enemy action
│
└─ NEXT ROUND
```

When the runtime reaches a player-choice boundary, the game must be able to wait indefinitely. No UI timeout, cinematic completion callback or React effect is allowed to invent the next gameplay command.

## What the player manages

During battle, the player manages several connected systems:

- **HP** — fighter health;
- **Ki** — energy used by relevant actions;
- **CC** — card/command resource;
- **hand/deck** — playable cards and draw state;
- **position** — front/back and vertical tactical state where applicable;
- **power window** — temporary state that can enable or alter certain actions;
- **active member / reserve** — in team battles;
- **Attack vs Defense context** — which commands are currently legal.

## Main action families

The battle UI exposes the original game's command grammar rather than one generic "attack" button. Depending on phase and context, actions include:

- **LIMIT**
- **JOINT**
- **BASIC**
- **CHARA**
- **GUARD**
- **MOVE**
- **GATHER**
- **STAGE**
- **POWER**
- card-based attacks, Beam, Support and Defense actions

Not every option is legal in every phase. The Engine/runtime is the authority for legality and cost.

## Cinematic flow

Gameplay and cinematography are deliberately separated.

A resolved action can move through several visual states:

```text
FIELD
→ action preparation
→ ACTION shot
→ actor animation
→ projectile / movement / FX
→ impact / defense reaction
→ cleanup
→ FIELD
→ next control boundary
```

The visible movie must follow the authoritative battle result; it does not decide hit/miss, damage, resources, KO or the next phase.

## Match formats

The project supports the battle architecture needed for:

- **1v1** fights;
- **2v2** team fights;
- active/reserve character switching;
- KO-driven team progression;
- deterministic rematches and repeated testing.

The exact public UI surface may evolve during alpha, but these formats are part of the active battle model.

## Where to go next

- Learn the detailed rules in [Battle System](BATTLE_SYSTEM.md).
- Learn how the 125-card system is organized in [Cards](CARDS.md).
- Learn Stage input behaviour in [Stage Attacks](STAGE_ATTACKS.md).

---

[← Game Overview](GAME_OVERVIEW.md) · [Battle System →](BATTLE_SYSTEM.md)
