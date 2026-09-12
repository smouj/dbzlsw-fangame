# DBZ LSW Fangame Wiki

Welcome to the canonical public wiki for **DBZ LSW Fangame**, an independent, non-commercial recreation of _Dragon Ball Z: Legendary Super Warriors_ for modern systems.

This wiki explains the game itself: how battles work, how cards and characters interact, how Stage Attacks behave, what the Story mode is intended to be, and how the project distinguishes verified GBC behaviour from approximations still under investigation.

> **Development status:** this project is in active public alpha development. For volatile implementation metrics, open issues and current P0 work, use [Project Status](../PROJECT_STATUS.md) and the [Roadmap](../ROADMAP.md). The wiki intentionally avoids duplicating numbers that can become stale.

## Start here

### For players

| Page | What it explains |
|---|---|
| [Game Overview](GAME_OVERVIEW.md) | What the project is, its goals and scope |
| [Gameplay](GAMEPLAY.md) | The overall match loop and player experience |
| [Battle System](BATTLE_SYSTEM.md) | Attack/Defense phases, resources, positions and commands |
| [Cards](CARDS.md) | The 125-card system, card families, LIMIT and JOINT |
| [Characters](CHARACTERS.md) | Fighters, forms, teams and loadouts |
| [Stage Attacks](STAGE_ATTACKS.md) | 3/4/5/6 Stage, input windows and resolution |
| [Story Mode](STORY_MODE.md) | The project's scene → dialogue → battle story structure |
| [FAQ](FAQ.md) | Common questions about the game and project |

### For contributors and researchers

| Page | What it explains |
|---|---|
| [Fidelity & ROM Research](FIDELITY_AND_RESEARCH.md) | Evidence levels, ROM-backed claims and public-safe research |
| [Architecture](../ARCHITECTURE.md) | Gameplay/runtime/presentation authority |
| [Fidelity Model](../FIDELITY.md) | Formal PASS/PARTIAL/evidence vocabulary |
| [Development](../DEVELOPMENT.md) | Contributor workflow |
| [Contributing](../../CONTRIBUTING.md) | Pull request and contribution rules |

## Wiki map

```text
HOME
├─ Game Overview
├─ Gameplay
│  ├─ Battle System
│  ├─ Cards
│  ├─ Characters
│  └─ Stage Attacks
├─ Story Mode
├─ Fidelity & ROM Research
└─ FAQ
```

## Canon and terminology

The public wiki follows four rules:

1. **Gameplay rules and presentation are separate.** A correct damage result does not automatically mean the visible choreography is faithful.
2. **ROM-backed does not mean globally ROM-exact.** Claims are scoped to the behaviour or resource actually demonstrated.
3. **Unknown behaviour stays unknown.** The project does not invent a GBC rule merely to complete a table or make a test pass.
4. **Current implementation status lives in status documents.** Stable game rules belong here; rapidly changing completion percentages do not.

## Legal note

No ROM is distributed by this repository. The project is unofficial and is not affiliated with or endorsed by the rights holders of _Dragon Ball_, _Dragon Ball Z_ or _Dragon Ball Z: Legendary Super Warriors_. See [NOTICE.md](../../NOTICE.md), [Public Source Policy](../PUBLIC_SOURCE_POLICY.md) and [ROM Research Policy](../ROM_RESEARCH_POLICY.md).

---

**Previous:** — · **Next:** [Game Overview →](GAME_OVERVIEW.md)
