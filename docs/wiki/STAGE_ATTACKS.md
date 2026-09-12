# Stage Attacks

Stage Attacks are a dedicated command family with preparation, a timed input sequence and a ROM-defined cinematic/gameplay resolution. They are not normal Beam cards and should not be documented as a generic QTE overlay.

## The four Stage cards

The ROM card table contains four Stage command cards:

| Card | Commands | Maximum CC from successful inputs |
|---|---:|---:|
| 3 Stage Attack | 3 | 3 |
| 4 Stage Attack | 4 | 4 |
| 5 Stage Attack | 5 | 5 |
| 6 Stage Attack | 6 | 6 |

The selected card determines the number of expected commands. The ROM has larger working buffers, but that does **not** mean every Stage action uses 10 or 16 inputs.

## Stage flow

The project targets this structure:

```text
ATTACK PHASE
→ BASIC / Stage selection
→ Stage preparation
→ QTE/input window opens
→ exactly 3/4/5/6 expected commands
→ result / correction branch where applicable
→ Stage command choreography
→ target reaction / impact
→ damage + tactical consequences
→ cleanup
→ FIELD
→ next player-control boundary
```

The input UI must not appear before the Stage input state actually begins.

## Accepted commands

The Stage command set uses:

```text
RIGHT
UP
DOWN
A
B
```

For the main sequence, the ROM stores the expected commands and a result for each command index.

A correct input:

```text
result[index] = success
index++
```

A wrong input:

```text
result[index] = failure
index++
```

The wrong button is therefore not ignored while the game waits for the originally expected button.

## One global timer

The Stage sequence uses a **single global input window**, not a fresh timer for every command.

The position-dependent ROM matrix is:

| Attacker | Defender | Window |
|---|---|---:|
| FRONT | FRONT | **150 GBC ticks** |
| FRONT | BACK | **120 GBC ticks** |
| BACK | FRONT | **80 GBC ticks** |
| BACK | BACK | **50 GBC ticks** |

At the GBC cadence these are approximately:

```text
150t ≈ 2.511 s
120t ≈ 2.009 s
 80t ≈ 1.339 s
 50t ≈ 0.837 s
```

These values supersede older provisional timings such as `1.2 / 1.7 / 2.4 / 2.9` seconds.

Correct and incorrect commands advance the command index while this original global deadline continues.

## Error correction / cash-out subwindow

After a Stage input error, the original game exposes an additional A/B decision window with ROM thresholds at **10, 25 and 30 ticks**.

The currently established behaviour is:

- **B / FIX** — the strict branch, associated with attempting to repair the error and continue;
- **A / BANK** — the wider branch, associated with ending the chain while keeping the CC earned so far;
- **timeout** — failure when the correction window expires.

The numeric thresholds are ROM-derived. The human labels are retained because they match documented original-game behaviour, but research notes should still distinguish literal ROM state from descriptive naming.

Critically, a repair attempt does **not** restart the original Stage global deadline.

## Stage scoring and damage

Successful commands feed the Stage result/CC accumulation, but Stage damage is not simply “number of correct buttons.”

The ROM also derives a base combat component and reduces it according to horizontal position:

```text
FRONT / FRONT → base
BACK  / FRONT → base / 2
FRONT / BACK  → base / 2
BACK  / BACK  → base / 4
```

So FRONT/BACK influences both Stage input difficulty and the numerical Stage result.

## Powered directional repositioning

When the relevant powered Stage state is active, successful directional commands can persistently change the defender's tactical position:

```text
RIGHT → force BACK
UP    → force AIR
DOWN  → force GROUND
A/B   → no tactical-position change
```

This tactical change must remain distinct from ordinary visual knockback.

## ROM physical command choreography

Stage actor commands use physical resources from Stage animation Bank `$61`.

| Command | Resource | Sequence selection | Actor duration |
|---|---:|---|---:|
| A | 1 | by actor visual profile | 4 frames / 13t |
| B | 2 | by actor visual profile | 6 frames / 32t |
| RIGHT | 3 | by actor visual profile | 7 frames / 41t |
| UP | 4 | by actor visual profile | 7 frames / 41t |
| DOWN | 4 | fixed sequence 9 | 9 frames / 53t |

The target reaction is also synchronized to specific actor frames and uses dedicated target sequences. The remake should therefore not reduce all Stage commands to one shared `attack → hurt → fixed delay` movie.

Some Stage physical-texture/corpus work can still be pending even when the ROM sequence/timing contract itself is known. The project must preserve that distinction honestly.

## Fidelity requirements

A Stage implementation is only complete when the applicable evidence reaches production end-to-end:

- 3/4/5/6 command count;
- global 150/120/80/50-tick timer;
- wrong-input progression;
- A/B correction semantics without timer reset;
- partial CC/result handling;
- ROM-selected command variant/sequence;
- actor/target physical timing;
- Stage damage/position rules;
- impact/reaction/cleanup;
- return to the correct next player-choice boundary.

---

[← Characters](CHARACTERS.md) · [Story Mode →](STORY_MODE.md)
