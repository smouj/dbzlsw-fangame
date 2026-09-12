# FAQ

## Is this an official Dragon Ball game?

No. DBZ LSW Fangame is an **unofficial, independent, non-commercial fan project**. It is not affiliated with or endorsed by the relevant rights holders.

## Is this a ROM hack?

No. The project is a modern recreation built with TypeScript, React and PixiJS. ROM research is used to understand the original game's mechanics, timing, resources and presentation grammar.

## Does the repository include the original ROM?

No. The repository does not distribute `.gb`/`.gbc` ROMs, save states, SRAM dumps or raw proprietary asset corpora.

## Do I need the original ROM to contribute?

Not for every type of contribution.

You can contribute to documentation, UI, architecture, tests and public-source work without ROM access. ROM-dependent research must follow the project's public research policy and use a contributor's own legally obtained copy.

## Is the game finished?

No. It is in active public alpha development.

The battle/runtime architecture is already substantial, while visible choreography and end-to-end fidelity remain active work. Check [Project Status](../PROJECT_STATUS.md) for the current baseline.

## Can I download and play a public build right now?

Public application source and builds are being staged through the project's public-source/release process. Check the repository [Releases](https://github.com/smouj/dbzlsw-fangame/releases), [Project Status](../PROJECT_STATUS.md) and open issues for the latest availability.

## How faithful is it to the GBC game?

Fidelity is tracked per system/action rather than claimed globally.

Some mechanics and resources are strongly ROM-backed; other visual sequences remain partial or pending evidence. The project deliberately distinguishes mechanical correctness from final browser-visible choreography.

See [Fidelity & ROM Research](FIDELITY_AND_RESEARCH.md).

## How many cards are in the game?

The original battle data contains **125 cards**, and the project models that complete set.

See [Cards](CARDS.md).

## How do Stage Attacks work?

There are 3/4/5/6 Stage command cards, requiring the corresponding number of timed inputs. Stage uses a global input window whose timing depends on battle context.

See [Stage Attacks](STAGE_ATTACKS.md).

## Does the game support teams?

The active battle model supports both **1v1** and **2v2**, including active/reserve member handling and character switching where legal.

## Is Story mode an overworld RPG?

The intended fangame Story structure is scene/dialogue driven:

```text
scene → dialogue → battle → resolution → next chapter
```

It does not depend on recreating a free-roaming RPG exploration layer.

See [Story Mode](STORY_MODE.md).

## Why does the project use GBC ticks?

Because timing is part of the original game's behaviour. A single Game Boy Color-oriented logical clock makes action sequencing deterministic and avoids browser timers becoming gameplay authority.

## Why not just copy what looks right from gameplay videos?

Videos are valuable visual evidence, but they do not replace mechanical/ROM evidence when the project can obtain it. The preferred workflow is to combine static/dynamic research, deterministic tests and visual comparison.

## How can I help?

Start with [CONTRIBUTING.md](../../CONTRIBUTING.md) and look at [open issues](https://github.com/smouj/dbzlsw-fangame/issues).

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
