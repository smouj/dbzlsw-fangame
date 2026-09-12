# Cards

Cards are one of the defining systems of _Dragon Ball Z: Legendary Super Warriors_. The project models the complete **125-card ROM table** as structured gameplay data rather than as hard-coded UI actions.

## ROM card families

The 125 entries are divided into these broad categories:

| Family | Count | Role |
|---|---:|---|
| Command / Stage | 4 | 3/4/5/6 Stage command cards |
| Damage | 24 | Physical/direct-damage actions, including special handlers |
| Beam | 38 | Energy/projectile attack families |
| Support | 48 | Buffs, state changes and support effects |
| Defense | 11 | Defensive responses |
| **Total** | **125** | |

These are card-table categories. They are not the same thing as runtime presentation families: two cards can share a category while using different handlers, animation resources or visual programs.

## ROM card record

The project treats each card as a structured record that can contain, among other fields:

```text
category
power
accuracy
internal card id
CC cost
execution handler
actor AnimationResource
FX resource
palette
fighter/form compatibility mask
metadata
```

The execution handler must always be interpreted in its proper category/context. Handler byte values are not assumed to have one universal meaning across all card categories.

## Playing a card

A card is not legal merely because it exists in a hand or equipped LIMIT slot. The battle authority validates the applicable rules, including:

- current Attack/Defense phase;
- fighter/form compatibility;
- CC/resource cost;
- card category;
- active temporary state;
- action-specific restrictions.

If legal, the Engine/runtime commits gameplay first and emits deterministic events. Presentation then renders the ROM-backed action path available for that card.

## LIMIT vs JOINT

The original game uses two distinct card sources.

### LIMIT

Each active fighter has **five equipped LIMIT slots**.

LIMIT:

- selects an equipped card;
- requires the power-window state;
- pays CC;
- validates normal compatibility/phase restrictions;
- does **not** consume the equipped card after use.

### JOINT

JOINT selects a card from the **physical hand**.

JOINT:

- pays the card cost;
- consumes/removes the selected hand card;
- compacts the hand/deck flow afterward.

So LIMIT is reusable equipped access; JOINT is consumable hand access.

## Phase legality

Card category legality is phase-dependent.

### Attack

Defense-category cards are not legal Attack selections.

### Defense

Defense-side LIMIT/JOINT legality accepts the appropriate **Support** and **Defense** categories when their individual restrictions pass. Defense LIMIT is therefore not equivalent to “Defense cards only.”

## Support and Defense

Support and Defense are gameplay categories, not visual-only effects. They can alter state, legal responses and the resolution of an incoming action.

The project preserves this separation:

```text
card selection
→ mechanical resolution
→ EventLog/result
→ ROM presentation branch
→ visible response
```

Visual code must not invent the mechanical meaning of a Support/Defense result.

## Execution and presentation fidelity

For every card, the project may need to reconcile several layers:

1. ROM card record;
2. category + execution handler;
3. legality and mechanical result;
4. actor AnimationResource / selected sequence;
5. FX resource and palette;
6. result branch;
7. presentation program/timing;
8. physical frame/FX linkage;
9. production renderer consumption.

A card is not considered fully faithful simply because its final damage is correct.

## Important distinction: category vs handler vs visual family

Do not reduce the card system to labels such as “Beam = one animation.” The ROM can route cards through shared execution skeletons, specialized workers, category-specific handlers and card-specific resources.

For public documentation, claims should therefore identify the scope precisely: data, mechanic, handler, physical sequence, presentation or browser-visible output.

See [Fidelity & ROM Research](FIDELITY_AND_RESEARCH.md).

## Card catalogue

A full card-by-card public catalogue should be generated from sanitized canonical data so counts, handlers, compatibility and evidence state cannot drift from the implementation. Until that dataset is published, this page documents the stable ROM/project contract rather than duplicating private/raw extraction tables manually.

---

[← Battle System](BATTLE_SYSTEM.md) · [Characters →](CHARACTERS.md)
