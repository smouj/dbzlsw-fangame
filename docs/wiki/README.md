# DBZ LSW Fangame Wiki

Welcome to the canonical public wiki for **DBZ LSW Fangame**, an independent, non-commercial recreation of _Dragon Ball Z: Legendary Super Warriors_ for modern systems.

This wiki explains both:

- the **original-game behaviour** we have actually established from ROM/data or reliable supporting evidence;
- the **fangame contract** that intentionally modernizes or adapts parts of that experience.

Those two categories must never be silently merged.

> **Development status:** this project is in active public alpha development. For volatile implementation metrics, open issues and current P0 work, use [Project Status](../PROJECT_STATUS.md) and the [Roadmap](../ROADMAP.md). The wiki intentionally avoids duplicating completion numbers that can become stale.

## Start here

### For players

| Page | What it explains |
|---|---|
| [Game Overview](GAME_OVERVIEW.md) | What the project is, what it preserves and what it modernizes |
| [Gameplay](GAMEPLAY.md) | The overall match loop and original command grammar |
| [Battle System](BATTLE_SYSTEM.md) | Attack/Defense phases, resources, position, LIMIT/JOINT and authority |
| [Cards](CARDS.md) | The 125-card ROM table, card families and card-source rules |
| [Characters](CHARACTERS.md) | Fighters, forms, teams, LIMIT slots and ROM physical identity |
| [Stage Attacks](STAGE_ATTACKS.md) | 3/4/5/6 Stage, exact ROM timing and correction behaviour |
| [Story Mode](STORY_MODE.md) | Original campaign facts vs this project's scene-driven adaptation |
| [FAQ](FAQ.md) | Common questions about the game and project |

### For contributors and researchers

| Page | What it explains |
|---|---|
| [Fidelity & ROM Research](FIDELITY_AND_RESEARCH.md) | Evidence layers, static/dynamic ROM claims and public-safe research |
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

The public wiki follows these rules:

1. **Original-game fact and fangame adaptation are different labels.** A project design decision must not be rewritten as something the GBC ROM did.
2. **Gameplay rules and presentation are separate.** A correct damage result does not automatically mean the visible choreography is faithful.
3. **ROM-backed does not mean globally ROM-exact.** Claims are scoped to the exact mechanic, handler, timing, resource or presentation path actually demonstrated.
4. **Static and dynamic evidence are different.** A byte layout can be statically closed while actor/target semantics still require live traces.
5. **Runtime convenience is not physical provenance.** A pose/fallback name does not prove that the ROM contains a dedicated frame sequence with that semantic label.
6. **Unknown behaviour stays unknown.** The project does not invent a GBC rule merely to complete a table or make a test pass.
7. **Current implementation status lives in status documents.** Stable rules belong here; changing completion percentages do not.

## Source priority

When two documents disagree, the project should prefer the newest demonstrated canonical source in this order:

```text
reproducible ROM/data evidence
→ current canonical project data / verifier
→ reviewed project documentation
→ external guide/reference
→ visual inference / hypothesis
```

External guides can clarify human-facing behaviour, but they do not override contradictory ROM evidence.

## Legal note

No ROM is distributed by this repository. The project is unofficial and is not affiliated with or endorsed by the rights holders of _Dragon Ball_, _Dragon Ball Z_ or _Dragon Ball Z: Legendary Super Warriors_. See [NOTICE.md](../../NOTICE.md), [Public Source Policy](../PUBLIC_SOURCE_POLICY.md) and [ROM Research Policy](../ROM_RESEARCH_POLICY.md).

---

**Previous:** — · **Next:** [Game Overview →](GAME_OVERVIEW.md)
