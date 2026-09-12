# Characters

Characters are represented by a fighter identity plus a specific **form**. In both the ROM research and the fangame, form identity is gameplay data, not a cosmetic skin.

## Fighter and form identity

A form can affect:

- card compatibility;
- equipped/available LIMITs;
- battle statistics;
- graphics/palette identity;
- animation-resource selection;
- portraits/overworld representation;
- story/encounter context.

For ROM-backed work, the physical chain is treated explicitly:

```text
character / form
→ ROM form identity
→ actor visual profile key
→ graphics bank + palette
→ AnimationResource
→ sequence selector
→ frame index / visual frame
→ metasprite / graphics blocks
→ physical fighter image
```

The project does not identify forms by visual similarity alone. A renderer that shows the wrong fighter with internally consistent bank/palette math is still wrong.

## ROM identity vs runtime semantic pose

A runtime pose name such as:

```text
idle
guard
hurt
beam_charge
beam_fire
knockback_down
```

is a semantic runtime convenience. It does **not** prove that the original ROM contains a dedicated physical sequence with that same human-readable meaning.

The project therefore distinguishes:

- **PHYSICAL** — directly linked to demonstrated ROM physical frames;
- **COMPOSITE** — assembled from demonstrated physical material;
- **FALLBACK** — runtime substitute when no dedicated physical equivalent is demonstrated;
- **REFERENCE_FX** — visual effect rather than fighter pose;
- **MISSING / UNRESOLVED** — evidence is not sufficient yet.

A 100% runtime pose-resolution rate is not the same as 100% physical-pose coverage.

## Teams

The battle model supports:

- **1v1**;
- **2v2**;
- one active fighter plus reserve state;
- legal manual switching through `CHARA`;
- automatic continuation when a KO occurs and a reserve remains.

Team state belongs to the battle/runtime authority. Visible exit/entry choreography belongs to Presentation.

## LIMIT loadout

Each battle member has **five LIMIT slots** in the battle data model used by the ROM research.

LIMIT cards are equipped/reusable options rather than cards drawn from the physical hand. Their legality still depends on phase, compatibility, CC and the active power-window state.

See [Battle System](BATTLE_SYSTEM.md) and [Cards](CARDS.md).

## Player setup vs rival setup

The project intentionally keeps player and rival setup asymmetric.

### Player

The player may configure the permitted parts of their own setup, including fighter/form and their own loadout where the selected game mode allows it.

### Rival

The rival can be selected and inspected, but its default deck/LIMIT configuration is intended to come from the appropriate **ROM-derived/canonical enemy preset** rather than behaving like a second freely editable player.

Until a specific rival preset is publicly derived and verified, the project should label that preset as unresolved rather than inventing a plausible deck.

## Physical fighter fidelity

For a fighter frame to be considered physically linked, the project should be able to trace its identity through the ROM-backed chain rather than merely find a PNG that looks correct.

Relevant evidence can include:

- ROM form record;
- actor visual profile key;
- graphics bank;
- physical palette;
- AnimationResource;
- resolved sequence;
- visual frame/metasprite;
- graphics blocks/tiles;
- runtime consumption.

This is why sprite extraction, semantic pose mapping and production animation are tracked as related but separate problems.

## Character catalogue

A complete public catalogue should ultimately be generated from sanitized canonical data and include, per fighter/form:

- ROM identity;
- stats;
- compatibility;
- LIMIT loadout/preset data where public-safe;
- physical animation coverage;
- runtime fallback/composite status;
- story/encounter usage.

That catalogue should not be manually duplicated across documentation files.

---

[← Cards](CARDS.md) · [Stage Attacks →](STAGE_ATTACKS.md)
