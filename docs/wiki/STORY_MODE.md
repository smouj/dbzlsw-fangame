# Story Mode

Story mode in DBZ LSW Fangame is a **deliberate project adaptation** of the original game's campaign structure.

It is important not to confuse two statements:

1. the original GBC game contains exploration/system layers beyond battles;
2. this fangame intentionally presents Story as a streamlined scene-driven campaign rather than reproducing every RPG/navigation interaction one-for-one.

The wiki should never imply that the original ROM lacked those systems simply because this project does not reproduce them directly.

## Fangame story contract

The intended project loop is:

```text
scene / panel
→ dialogue
→ transition
→ battle
→ battle result
→ next scene / chapter
```

This is the canonical **fangame** Story flow.

## What is taken from the original game

ROM research, original-game data and reliable guides are used to establish things such as:

- story ordering;
- participating characters/forms;
- battle matchups;
- important dialogue/events;
- chapter context;
- unlock/progression facts when verified;
- story-significant objects or events.

Those sources determine **what happens** in the original campaign.

## What the fangame intentionally changes

The current project does not require a one-for-one recreation of the original exploration layer.

The modern Story presentation may omit or abstract:

- freely navigable RPG maps;
- exploration hotspots;
- field pickups/containers;
- cards represented as map collectibles;
- navigation interactions that do not contribute to the project's scene-driven flow.

That is a **design choice of this fangame**, not a claim about what existed in _Legendary Super Warriors_.

## What Story mode includes

The project can use:

- scene backgrounds/panels;
- character portraits and expressions;
- dialogue;
- chapter transitions;
- story-derived battle setup;
- post-battle resolution;
- story-significant items/events when narratively relevant.

A story object such as a Dragon Ball, the Time Machine or the Z Sword may still appear because it matters to the narrative even if it is not implemented as a free-roaming pickup mechanic.

## Story and Battle remain separate authorities

Story creates context and battle configuration; it does not become a second combat engine.

```text
Story chapter
→ participants / encounter context
→ BattleConfig
→ BattleRuntime / Engine
→ battle outcome
→ Story progression
```

Story may choose who fights, why the fight occurs and what scene follows. It must not independently calculate card legality, damage, Stage results, CC/Ki, defense semantics or KO.

## Fidelity policy for Story

Story documentation should distinguish three categories explicitly:

- **ORIGINAL-GAME FACT** — demonstrated by ROM/data or a reliable source;
- **FANGAME ADAPTATION** — intentional presentation/design choice of this project;
- **UNRESOLVED** — not yet sufficiently verified.

This prevents an adaptation decision from being accidentally documented as original GBC behaviour.

## Current project priority

Story remains part of the project, but current development prioritizes **playable, repeatable and visually faithful battles** before broad Story content completion.

For changing priorities, see:

- [Project Status](../PROJECT_STATUS.md)
- [Roadmap](../ROADMAP.md)

## Future wiki expansion

Once the public-safe chapter dataset is ready, Story documentation should expand into generated/reviewed pages covering:

- chapter index;
- scene summaries;
- battle-by-battle participants;
- unlock/progression data;
- original-game facts vs fangame adaptations;
- known unresolved points.

Those pages should be sourced from canonical project data and evidence, not copied blindly from walkthrough assumptions.

---

[← Stage Attacks](STAGE_ATTACKS.md) · [Fidelity & ROM Research →](FIDELITY_AND_RESEARCH.md)
