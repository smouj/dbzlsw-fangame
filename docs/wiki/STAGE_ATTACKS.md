# Stage Attacks

Stage Attacks are command-input actions built around a short preparation phase followed by a timed input window and a cinematic resolution.

They are one of the most distinctive systems in _Legendary Super Warriors_ and are treated as a dedicated gameplay family rather than as normal Beam cards.

## The four Stage cards

The game has four Stage command cards:

| Card | Required inputs |
|---|---:|
| 3 Stage Attack | 3 |
| 4 Stage Attack | 4 |
| 5 Stage Attack | 5 |
| 6 Stage Attack | 6 |

The input count is part of the selected Stage card. The runtime must not generate a fixed 10- or 16-input sequence for every Stage action.

## Stage flow

A Stage action is expected to follow this structure:

```text
ATTACK PHASE
→ choose BASIC / Stage route
→ preparation movie
→ input window opens
→ timed command sequence
→ Stage result
→ resolution choreography
→ impact / counter / repositioning as applicable
→ cleanup
→ FIELD
→ next control boundary
```

The input UI must not appear before preparation is complete.

## Input semantics

The input window uses a **single global deadline** for the Stage attempt. It is not a fresh timer for every individual button.

For each expected command:

- a correct input records success and advances to the next command;
- a wrong input records failure for that command **and still advances**;
- repair/correction behaviour, where supported by the active runtime contract, must preserve the original global deadline rather than restarting the timer.

This distinction is important because a UI that resets time after every button makes Stage substantially easier than the original system.

## Position and timing

Stage timing depends on battle context, including attacker/defender positional state. The project stores and verifies this in **GBC ticks** rather than generic browser milliseconds.

Exact currently verified timing matrices belong to generated/runtime verification data and may evolve as evidence is promoted. The wiki therefore documents the stable rule:

> Stage uses a position-dependent, single global GBC-tick input window.

## Success, failure and counterplay

A Stage action is not merely a visual QTE overlay. Its result feeds the normal battle authority and can affect the final resolution, including failed-input/counter behaviour and position changes associated with the action.

Presentation then reproduces the appropriate preparation, rush, impact and cleanup without independently deciding the gameplay result.

## Power interaction

Power-state Stage inputs can interact with defender positioning for directional commands. These changes are resolved as battle state, then reflected visually.

## Fidelity requirements

A Stage implementation is not considered complete simply because the input buttons work. The project tracks:

- correct input count;
- global deadline;
- wrong-input progression;
- result/counter semantics;
- physical Stage animation resources;
- actor/target sequencing;
- movement and impact timings;
- repositioning;
- cleanup;
- return to the next player-choice boundary.

---

[← Characters](CHARACTERS.md) · [Story Mode →](STORY_MODE.md)
