# FAQ

## Is this an official Dragon Ball game?

No. DBZ LSW Fangame is an **unofficial, independent, non-commercial fan project**. It is not affiliated with or endorsed by the relevant rights holders.

## Is this a ROM hack?

No. The project is a modern recreation built with TypeScript, React and PixiJS. ROM research is used as evidence for mechanics, timing, resources, animation/presentation programs and physical graphics provenance.

## Is the fangame running the original ROM underneath?

No. The active project reimplements the game systems in its own runtime rather than using the ROM as the live gameplay engine.

That is why reverse engineering matters: ROM evidence has to be translated into canonical data, Engine/runtime behaviour and Presentation, then verified all the way to the browser-visible result.

## Does the repository include the original ROM?

No. The repository does not distribute `.gb`/`.gbc` ROMs, save states, SRAM dumps or raw proprietary asset corpora.

## Do I need the original ROM to contribute?

Not for every contribution.

Documentation, UI, architecture, tests and public-source work can be contributed without ROM access. ROM-dependent research must follow the project's public research policy and use a contributor's own legally obtained copy.

## Is the game finished?

No. It is in active public alpha development.

The battle/runtime architecture is substantial, while end-to-end visible fidelity remains active work. Check [Project Status](../PROJECT_STATUS.md) for the current baseline.

## Can I download and play a public build right now?

Public application source/build availability is controlled through the project's public-source and release process. Check [Releases](https://github.com/smouj/dbzlsw-fangame/releases), [Project Status](../PROJECT_STATUS.md) and open issues for the current situation.

## How faithful is it to the GBC game?

Fidelity is tracked **per mechanic, resource and presentation path**, not claimed globally.

For example, the project may have ROM-verified card data and Stage timing while a specific physical texture, multi-actor spatial binding or production Pixi path is still partial. Those states are documented separately rather than being collapsed into one “ROM exact” label.

See [Fidelity & ROM Research](FIDELITY_AND_RESEARCH.md).

## How many cards are in the original battle table?

**125**.

The project models the complete table as:

- 4 Command/Stage;
- 24 Damage;
- 38 Beam;
- 48 Support;
- 11 Defense.

See [Cards](CARDS.md).

## What is the difference between LIMIT and JOINT?

**LIMIT** uses one of the active member's five equipped, reusable LIMIT cards and requires the power-window state.

**JOINT** uses the physical hand and consumes/removes the selected hand card after a legal committed use.

See [Battle System](BATTLE_SYSTEM.md).

## How do Stage Attacks work?

There are 3/4/5/6 Stage command cards requiring exactly 3/4/5/6 expected commands.

The main sequence uses one global position-dependent window:

- FRONT / FRONT: 150 ticks;
- FRONT / BACK: 120 ticks;
- BACK / FRONT: 80 ticks;
- BACK / BACK: 50 ticks.

Wrong input advances the command index, and the original game has a separate A/B correction/cash-out window after errors.

See [Stage Attacks](STAGE_ATTACKS.md).

## Does the game support teams?

The active battle model supports **1v1** and **2v2**, including active/reserve handling and legal character switching.

## Is Story mode the same as the original GBC exploration layer?

No. This is an intentional project adaptation.

The original game contains navigation/exploration systems. The fangame currently chooses a streamlined Story structure:

```text
scene → dialogue → transition → battle → resolution → next chapter
```

So “no free-roaming Story layer in the fangame” must not be interpreted as “the original game never had one.”

See [Story Mode](STORY_MODE.md).

## Why does the project use GBC ticks?

Because timing is part of the original behaviour and must not drift with browser/UI timers. A Game Boy Color-oriented logical clock gives the remake one reproducible time domain for runtime and presentation.

## Does deterministic mean the RNG is automatically identical to the ROM?

No.

Determinism means the fangame can reproduce its own result from the same state/seed/commands. Exact parity with a specific original GBC random/timing source is a separate ROM-fidelity claim that must be demonstrated.

## Why not just copy what looks right from gameplay videos?

Videos are useful visual evidence, but they cannot always reveal the mechanical state, handler, resource selection or hidden result branch. The preferred workflow combines ROM/static research, dynamic traces where needed, deterministic tests and visual comparison.

## How can I help?

Start with [CONTRIBUTING.md](../../CONTRIBUTING.md) and check [open issues](https://github.com/smouj/dbzlsw-fangame/issues).

Useful areas include:

- battle/runtime;
- PixiJS presentation;
- camera/shot choreography;
- physical-frame mapping;
- deterministic browser testing;
- documentation;
- accessibility/UI;
- reproducible ROM research.

## Where is the community?

- GitHub Issues and Pull Requests for actionable development work;
- [r/DBZ_LSW_FANGAME](https://www.reddit.com/r/DBZ_LSW_FANGAME/) for broader community discussion and progress posts.

See [Community](../COMMUNITY.md).

---

[← Fidelity & ROM Research](FIDELITY_AND_RESEARCH.md) · [Wiki Home →](README.md)
