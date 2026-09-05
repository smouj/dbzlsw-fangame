<div align="center">

# DBZ LSW Fangame

**Community-driven, research-based recreation of _Dragon Ball Z: Legendary Super Warriors_ for modern systems.**

[![Status](https://img.shields.io/badge/status-public%20development%20preview-f59e0b)](#project-status)
[![License: MIT](https://img.shields.io/badge/code%20license-MIT-2563eb)](LICENSE)
[![Fan Project](https://img.shields.io/badge/project-non--commercial%20fan%20project-6b7280)](#legal-and-project-scope)

Mechanical fidelity · GBC-timed combat · ROM research · deterministic engine · PixiJS presentation · community contributions

</div>

---

## What this project is

**DBZ LSW Fangame** is an independent, non-commercial fan project focused on understanding and faithfully recreating the systems, timing, combat flow and presentation grammar of _Dragon Ball Z: Legendary Super Warriors_ (Game Boy Color).

The project is being developed as a modern TypeScript application with a deterministic combat engine and a presentation layer designed around the original Game Boy Color timing model. Reverse-engineering findings are used as technical evidence; unverified behaviour is tracked as such rather than silently approximated.

This repository is the **public collaboration surface** for the project: source code that is safe to redistribute, documentation, tests, tooling, issues and pull requests live here. Private/raw ROM research and non-redistributable material remain outside this repository.

## Project status

**Public Development Preview / Alpha.**

The underlying project is already substantial, but public-source publication is being staged deliberately so that the public history starts clean and does not accidentally contain ROM files, raw extracted proprietary data, private research material or workspace artefacts.

Current development priorities are:

1. **Visible battle fidelity** — camera/shot choreography, actor-target synchronization, projectile lifecycle and HUD timing.
2. **Physical animation closure** — resolve remaining incomplete physical sequences and frame provenance.
3. **Full-battle E2E validation** — deterministic 1v1 and 2v2 battles from initialization through KO/results.
4. **Public-source hardening** — contributor setup, portable CI and strict separation between redistributable source and local ROM-derived outputs.

See [`docs/ROADMAP.md`](docs/ROADMAP.md) for the public roadmap and [`docs/PROJECT_STATUS.md`](docs/PROJECT_STATUS.md) for the current fidelity model.

## Fidelity model

A feature is not considered "ROM-faithful" just because its gameplay result is correct. Mechanical and visible fidelity are tracked independently.

A combat action is considered complete only when the relevant evidence supports the full chain:

```text
input / legality
→ engine resolution
→ deterministic EventLog
→ GBC-timed presentation timeline
→ camera / shot
→ actor + target frames and motion
→ projectile / FX lifecycle
→ impact / damage / reaction
→ HUD / hand timing
→ return to the correct control boundary
```

When evidence is incomplete, the project uses explicit states such as **partial**, **pending evidence** or **not applicable** instead of inventing behaviour.

## Technology

The active implementation is built around:

- TypeScript
- React
- Vite
- PixiJS
- Vitest
- Playwright
- deterministic GBC-tick combat/runtime tooling

The public repository will expose a small set of contributor-facing commands while retaining detailed specialist verifiers underneath.

## Development model

The intended public workflow is:

```text
fork
  ↓
feature branch
  ↓
small, evidence-backed change
  ↓
portable checks
  ↓
pull request
  ↓
review
  ↓
squash merge
```

Before contributing, read:

- [`CONTRIBUTING.md`](CONTRIBUTING.md)
- [`docs/PUBLIC_SOURCE_POLICY.md`](docs/PUBLIC_SOURCE_POLICY.md)
- [`docs/ROM_RESEARCH_POLICY.md`](docs/ROM_RESEARCH_POLICY.md)
- [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md)

## ROM and asset policy

**This repository does not distribute the game ROM.** Contributors must not commit ROM images, save states, raw ROM dumps, proprietary audio dumps or other non-redistributable extracted material.

Where local verification against an original game image is required, contributors provide their own legally obtained copy locally. Local extraction outputs must remain ignored/untracked unless a specific derived artefact has been reviewed and approved for public distribution.

The public CI includes guardrails intended to catch common accidental publication paths.

## Areas where help is useful

Contributions are particularly valuable in:

- GBC reverse engineering and emulator-assisted research
- deterministic gameplay systems
- PixiJS rendering and camera choreography
- animation/frame provenance
- projectile and FX synchronization
- browser E2E testing
- TypeScript architecture
- technical documentation
- reproducible ROM-fidelity evidence

Good contributions do not need to be large. A small, well-evidenced correction is preferable to a broad speculative rewrite.

## Repository roles

This public repository and the private research workspace intentionally serve different purposes:

```text
private research workspace
raw evidence · local ROM work · internal audits
                │
                │ verified, redistributable knowledge
                ▼
         dbzlsw-fangame
source · tests · docs · tooling · issues · pull requests
```

See [`docs/PUBLIC_SOURCE_POLICY.md`](docs/PUBLIC_SOURCE_POLICY.md) for the boundary in detail.

## Legal and project scope

This is an **unofficial, non-commercial fan project**. It is not affiliated with, endorsed by, sponsored by or approved by the rights holders of _Dragon Ball_, _Dragon Ball Z_ or _Dragon Ball Z: Legendary Super Warriors_.

The **MIT License applies only to original source code and documentation contributed under that license**. It does not grant rights to third-party trademarks, characters, artwork, music, ROM data or other copyrighted game assets.

No game ROM is provided or required to browse this repository.

## License

Original project source code and documentation in this repository are licensed under the [MIT License](LICENSE), unless a file explicitly states otherwise.

Third-party intellectual property remains the property of its respective owners.
