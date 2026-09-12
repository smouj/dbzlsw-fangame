# Story Mode

The project's Story mode is designed as a **scene-driven battle campaign**, not as a free-roaming RPG layer.

## Canonical story structure

The intended loop is:

```text
scene / panel
→ dialogue
→ transition
→ battle
→ resolution
→ next scene / chapter
```

The original game's guides and ROM research are useful for determining what happens, who participates, the order of events and the battle context. They are **not** a requirement to reproduce every exploration or object-interaction layer as a modern RPG system.

## What Story mode includes

The project can use:

- scene backgrounds;
- character portraits;
- dialogue;
- chapter transitions;
- battle setup derived from the story context;
- post-battle resolution;
- story-significant objects/events where they matter narratively.

## What Story mode does not require

The current design does not depend on:

- a freely navigable RPG overworld;
- exploration hotspots;
- loot containers or field pickups;
- cards placed as collectible map objects;
- route-choice systems that are not part of the intended remake flow;
- unrelated RPG mechanics added simply because they existed in a walkthrough context.

This keeps the campaign focused on the narrative and battle system that define the project.

## Story and battle are separate systems

Story prepares a battle configuration; it does not become a second battle engine.

```text
Story chapter
→ battle config
→ BattleRuntime / Engine
→ battle result
→ Story progression
```

The Story layer may choose participants, context and presentation around a fight, but combat legality, damage, resources, Stage outcomes and KO remain owned by the battle system.

## Current priority

Story is part of the project, but active development prioritizes **playable, repeatable, ROM-faithful battles** before broad story-content completion.

For the latest priority order, see [Roadmap](../ROADMAP.md) and [Project Status](../PROJECT_STATUS.md).

## Future wiki expansion

As public-safe chapter data is stabilized, this wiki can expand into:

- chapter index;
- battle-by-battle roster;
- story scene summaries;
- unlock/progression notes;
- verified differences between the original game and the fangame presentation.

Those pages should be generated or reviewed against the canonical story data rather than copied from old walkthrough assumptions.

---

[← Stage Attacks](STAGE_ATTACKS.md) · [Fidelity & ROM Research →](FIDELITY_AND_RESEARCH.md)
