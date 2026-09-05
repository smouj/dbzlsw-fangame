# Maintainer Repository Setup

This file defines the intended GitHub settings for `smouj/dbzlsw-fangame`. These settings live partly outside Git and should match this version-controlled baseline.

## Repository identity

**Name:** `dbzlsw-fangame`

**Description:**

> Open-source, research-driven fangame recreation of Dragon Ball Z: Legendary Super Warriors (GBC), focused on deterministic combat and ROM-backed fidelity.

**Topics:**

`dragon-ball-z`, `legendary-super-warriors`, `game-boy-color`, `gbc`, `fangame`, `reverse-engineering`, `typescript`, `react`, `pixijs`, `game-development`, `turn-based`, `card-game`

See `docs/BRANDING.md` for the canonical public copy.

## Social preview

Use the approved 1280×640 social-preview design from `docs/media/social-preview.svg` (exported to PNG/JPG for GitHub's Social preview uploader). Do not use extracted character art as repository branding.

## Community links

- Reddit: https://www.reddit.com/r/DBZ_LSW_FANGAME/
- X/Twitter: do not configure until the exact official handle is explicitly verified by the maintainer.

## Features

Recommended:

- Issues: enabled
- Discussions: enabled for questions/community conversation once moderation is ready
- Projects: enabled when the public execution board is created
- Wiki: disabled; versioned technical documentation belongs in `docs/`
- Releases: enabled when redistributable public builds exist
- Private vulnerability reporting: enabled if available

## Merge policy

- prefer **squash merge** for public contributions
- delete head branches after merge
- avoid direct pushes to `main`
- block force pushes

## `main` ruleset

Configure a ruleset with:

- pull request required
- at least 1 approving review
- conversation resolution required
- force pushes blocked
- branch deletion blocked
- administrators normally follow the same rules

Required checks initially:

- `Public source safety / safety`
- `Repository health / community-files`

After issue #1 publishes application source, add stable portable core/fidelity/browser checks.

## Issue taxonomy

### Priority

`P0`, `P1`, `P2`, `P3`

### Domain

`engine`, `gameplay`, `renderer`, `camera`, `animation`, `rom-fidelity`, `visual-fidelity`, `research`, `ui`, `documentation`, `tooling`

### State / contribution

`confirmed`, `needs-evidence`, `blocked`, `ready`, `good first issue`, `help wanted`

Avoid duplicate labels with equivalent meanings.

## Public project board

Recommended workflow:

1. Backlog
2. Ready
3. In progress
4. Review
5. Blocked
6. Done

Only actionable public work belongs on the public board. Unprocessed local research is promoted after it has a reproducible public description.

## Repository boundary

Do not turn the public repository into a mirror of a private workspace or import private Git object history. Public code/media enters through a reviewed sanitized snapshot/change satisfying `docs/PUBLIC_SOURCE_POLICY.md` and `docs/SCREENSHOTS.md`.
