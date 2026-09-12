# Cards

Cards are one of the defining systems of _Legendary Super Warriors_. The project models the complete **125-card** set as gameplay data rather than treating card names as hard-coded UI actions.

## Card families

The ROM card table divides the 125 entries into the following broad gameplay groups:

| Family | Count | Role |
|---|---:|---|
| Command / Stage | 4 | 3/4/5/6 Stage command cards |
| Damage | 24 | Physical/direct-damage actions |
| Beam | 38 | Energy/projectile attacks |
| Support | 48 | Buffs, state changes and support effects |
| Defense | 11 | Defensive responses |
| **Total** | **125** | |

The project keeps the original card record semantics separate from presentation. A Beam card, for example, can have:

```text
card data
├─ power / accuracy / CC cost
├─ compatibility
├─ execution handler
├─ actor animation resource
├─ FX resource
└─ palette / presentation dependencies
```

## Playing cards

A card is not legal merely because it exists in the hand. The runtime validates the relevant context, including:

- current phase;
- fighter/form compatibility;
- resource cost;
- command family;
- temporary battle state;
- any action-specific restrictions.

If the command is legal, the Engine applies gameplay state changes and emits events. Presentation then turns those events and ROM-backed descriptors into the visible action.

## LIMIT vs JOINT

These two systems are intentionally distinct.

### LIMIT

LIMIT actions come from the active fighter's equipped Limit loadout. They are persistent options rather than cards discarded from the current hand after use.

Availability is controlled by the relevant power/context gates and normal legality checks.

### JOINT

JOINT uses the normal hand/deck flow. When a playable card is consumed, the hand/deck state advances according to the battle rules.

## Support and Defense

Support and Defense are not visual-only categories. Their effects can influence battle state, legal responses and the way an incoming action resolves.

The project therefore keeps two layers explicit:

```text
mechanical effect
        ↓
BattleEventLog
        ↓
visual response / ROM presentation
```

This prevents a visual branch from becoming an accidental source of gameplay truth.

## Card fidelity

The project tracks cards at more than one level:

1. data/compatibility;
2. mechanical execution;
3. result branch;
4. animation resource;
5. physical frame sequence;
6. FX/palette;
7. presentation timeline;
8. production renderer consumption.

A card is not called fully faithful merely because damage is correct. See [Fidelity & ROM Research](FIDELITY_AND_RESEARCH.md).

## Card catalogue

A complete public card-by-card catalogue is intended to live under this wiki once the public-source snapshot exposes the relevant sanitized data directly. Until then, this page documents the stable system contract rather than duplicating private/raw research tables.

---

[← Battle System](BATTLE_SYSTEM.md) · [Characters →](CHARACTERS.md)
