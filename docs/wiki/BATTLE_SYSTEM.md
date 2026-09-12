# Battle System

The battle system is the core of DBZ LSW Fangame. It combines the original game's phase structure, card grammar, resources, tactical position and action resolution with a deterministic modern runtime.

This page separates two things deliberately:

- **ROM/game contract** — behaviour demonstrated from the original game;
- **fangame architecture** — how this project reproduces that behaviour safely and deterministically.

## 1. Round structure

A normal player-controlled round is built around two distinct decision phases:

```text
ATTACK PHASE
→ player chooses an attack-side command
→ the accepted action resolves
→ control stops at the next decision boundary

DEFENSE PHASE
→ player chooses a response to the incoming enemy action
→ the enemy action resolves with that defense context
→ the round completes
→ the next ATTACK decision begins
```

The fangame runtime owns those boundaries. Presentation may finish an already accepted action, but it may not invent the next command or advance the battle by itself.

## 2. Top-level command menus

The original battle command grammar is phase-dependent.

### Attack Phase

```text
ATTACK
├─ LIMIT
├─ JOINT
├─ BASIC
└─ CHARA
```

### Defense Phase

```text
DEFENSE
├─ LIMIT
├─ JOINT
└─ BASIC
```

`CHARA` is therefore an Attack-side top-level command, not a universal command shown identically in both phases.

`BASIC` expands into phase-appropriate basic actions. In the fangame this includes the original families represented by Stage/Gather on the Attack side and Guard/Move-style responses on the Defense side, subject to runtime legality.

## 3. Core resources

### HP

Health. Reaching the terminal KO condition ends a 1v1 battle or advances team resolution when a reserve fighter remains.

### Ki

Energy used by actions whose rules require it. Ki is authoritative gameplay state, never presentation state.

### CC

Command/card currency. The battle authority validates and pays CC costs before an action is committed.

### Deck and hand

Each side has a battle deck plus physical hand slots. JOINT uses the normal hand flow: the chosen card is paid for, removed from the hand and the hand is compacted according to the battle rules.

## 4. LIMIT and JOINT are different storage systems

### LIMIT

The active member has **five equipped LIMIT slots**.

A legal LIMIT action:

- selects one of those equipped cards;
- requires the active power-window state;
- validates CC, compatibility and phase legality;
- pays CC;
- does **not** discard the equipped LIMIT card.

LIMIT is therefore a reusable equipped-card source, not a second hand.

### JOINT

JOINT selects from the physical hand.

A legal JOINT action:

- validates the selected hand card;
- pays its cost;
- consumes/removes that card from the hand;
- compacts/advances the hand state as required.

## 5. Attack-side and Defense-side LIMIT legality

The same equipped LIMIT mechanism is used in both phases, but card-type legality differs by phase.

- **Attack:** Defense-category cards are rejected.
- **Defense:** cards below Support/Defense categories are rejected; legal Support and Defense LIMIT cards can therefore be used when their own restrictions pass.

This is important: Defense LIMIT is not a mysterious separate engine and is not restricted to Defense cards only.

## 6. Tactical position vs cinematic coordinates

The game tracks tactical position separately from visual coordinates used during an action movie.

```text
tactical state
≠
cinematic X/Y
```

The relevant tactical state includes horizontal FRONT/BACK and vertical states where applicable. A rush, camera pan or knockback can move a sprite without changing authoritative position unless the resolved action explicitly changes it.

Stage is a clear example: horizontal position affects its timing/damage rules, while powered directional Stage results can also cause persistent tactical repositioning.

## 7. CHARA and team state

`CHARA` switches the active member when team state and command legality allow it.

The project keeps two boundaries separate:

```text
logical team switch
≠
visible exit/entry choreography
```

The runtime commits the team state at the authoritative point; Presentation reproduces the ROM-derived exit/entry motion around that state change.

## 8. Defense is an active decision

Defense is not a passive animation after the enemy has already resolved its attack. The player chooses a legal response first. Depending on state and available cards, that response can come from:

- LIMIT;
- JOINT;
- BASIC defensive actions such as Guard/Move;
- Support or Defense cards when legal for the selected source.

The battle authority resolves the mechanical result. Presentation then renders the corresponding guard, avoid, support/defense effect, impact branch and cleanup.

## 9. Deterministic fangame authority

The remake uses deterministic state/RNG plumbing so the same initial state, seed and command sequence can be reproduced for testing.

That is an implementation property of this project. It should not be confused with a claim that every original GBC randomness source is literally identical to the remake's internal RNG implementation.

## 10. Gameplay vs presentation authority

The Engine/runtime owns:

- command legality;
- costs;
- gameplay RNG/result inputs;
- hit/miss and defense outcome;
- damage;
- HP/Ki/CC;
- phase/exchange progression;
- Stage/QTE gameplay result;
- KO;
- authoritative tactical state.

The presentation layer owns:

- shot/background;
- fighter visibility;
- physical frame/sequence playback;
- cinematic motion;
- FX/projectiles/BG effects;
- camera/screen motion;
- impact timing and cleanup;
- audio requests.

For the formal implementation boundary, see [Architecture](../ARCHITECTURE.md).

---

[← Gameplay](GAMEPLAY.md) · [Cards →](CARDS.md)
