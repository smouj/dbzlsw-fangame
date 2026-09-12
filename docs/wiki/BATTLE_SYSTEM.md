# Battle System

The battle system is the core of DBZ LSW Fangame. It combines turn structure, cards, character state, resources, tactical position and cinematic resolution.

## 1. Attack and Defense are separate phases

The game does not treat a round as one uninterrupted autoplay sequence.

```text
ATTACK PHASE
→ player chooses and resolves an action
→ stop at the next decision boundary

DEFENSE PHASE
→ player chooses how to answer the enemy attack
→ enemy action resolves
→ stop before the next round decision
```

The runtime owns those boundaries. Presentation may continue the movie of an already-accepted action, but it may not choose the next command.

## 2. Core resources

### HP

Health. Reaching the terminal KO condition ends a 1v1 battle or advances team resolution in a multi-fighter battle.

### Ki

Energy used by relevant attacks/actions. Ki changes are part of gameplay state, never presentation state.

### CC

Command/card currency. Actions and cards can require CC; payment is validated and applied by the battle authority.

### Hand and deck

The battle model tracks the playable hand and deck progression. JOINT/card actions consume cards according to their rules; permanent/equipped LIMIT behaviour is modeled separately.

## 3. Position

Fighters can occupy tactical states that affect battle behaviour and presentation. The project tracks horizontal front/back state and relevant vertical state rather than treating every cinematic coordinate as gameplay position.

This distinction matters:

```text
tactical position
≠
visual X/Y used during a cinematic
```

A rush, knockback or camera pan may move sprites visually without changing the authoritative tactical state unless the resolved action explicitly says so.

## 4. Command groups

### LIMIT

Uses a fighter's equipped Limit options. Availability depends on battle context and the required power/legality gates. LIMIT is not the same as playing a disposable hand card.

### JOINT

Uses a card from the physical hand/deck flow. Validity, CC cost, compatibility and phase restrictions are resolved by the Engine.

### BASIC

Opens context-sensitive basic actions such as movement/guard/power-related actions and Stage behaviour depending on phase and state.

### CHARA

Switches the active team member when the team state allows it. The logical switch and its visible entry/exit choreography are separate concerns: the runtime changes authority at the correct boundary while the presenter reproduces the transition.

## 5. Defense responses

Defense is not a passive animation. The player can select a legal response before the enemy action resolves. Depending on available state/cards this can include defensive cards, Support/LIMIT options, Guard or movement/evasion behaviour.

The exact result is resolved mechanically first and then presented visually.

## 6. Determinism

Given the same battle state, RNG state and command sequence, gameplay results and event ordering should be reproducible. Determinism is a project requirement because it enables:

- regression tests;
- ROM comparison;
- reliable replays/fixtures;
- debugging of presentation without changing gameplay outcomes.

## 7. Gameplay vs presentation authority

The Engine/runtime owns:

- legality;
- costs;
- RNG;
- hit/miss;
- damage;
- HP/Ki/CC;
- phase/exchange progression;
- QTE result;
- KO;
- authoritative tactical state.

The presentation layer owns:

- shot/background;
- sprite visibility;
- physical frame/pose;
- movement shown on screen;
- FX/projectiles;
- camera/screen motion;
- impact timing and cleanup;
- audio requests.

For the formal architecture, see [Architecture](../ARCHITECTURE.md).

---

[← Gameplay](GAMEPLAY.md) · [Cards →](CARDS.md)
