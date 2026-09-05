# Maintainer Repository Setup

This file defines the intended GitHub repository settings for `smouj/dbzlsw-fangame`. Some settings live outside Git and must be configured in the GitHub repository UI/API by an administrator.

## Repository identity

**Name**

`dbzlsw-fangame`

**Recommended description**

> Research-driven community fangame recreation of Dragon Ball Z: Legendary Super Warriors (GBC), focused on deterministic combat and ROM-backed fidelity.

**Recommended topics**

- `dragon-ball-z`
- `legendary-super-warriors`
- `game-boy-color`
- `gbc`
- `fangame`
- `reverse-engineering`
- `typescript`
- `react`
- `pixijs`
- `game-development`

## Features

Recommended:

- Issues: enabled
- Projects: enabled when the first public execution board is created
- Discussions: enabled for community questions and non-actionable conversation
- Wiki: disabled; versioned documentation belongs in `docs/`
- Releases: enabled when distributable public builds exist
- Private vulnerability reporting: enabled if available

## Merge policy

Preferred public contribution path:

- allow **squash merge**
- use squash merge for external PRs
- delete head branches after merge
- avoid direct pushes to `main`
- avoid force pushes

## `main` ruleset

Once the public source snapshot is present, configure a ruleset for `main` with:

- pull request required
- at least 1 approving review
- conversation resolution required
- required status checks
- force pushes blocked
- branch deletion blocked
- administrators should normally follow the same rules

Initial required checks:

- `Public source safety / safety`
- `Repository health / community-files`

After application source publication, add the portable core/fidelity/browser checks as they become stable.

## Issue taxonomy

Recommended labels:

### Priority

- `P0`
- `P1`
- `P2`
- `P3`

### Domain

- `engine`
- `gameplay`
- `renderer`
- `camera`
- `animation`
- `rom-fidelity`
- `visual-fidelity`
- `research`
- `ui`
- `documentation`
- `tooling`

### State / contribution

- `confirmed`
- `needs-evidence`
- `blocked`
- `ready`
- `good first issue`
- `help wanted`

Avoid creating labels that duplicate the same concept under slightly different wording.

## Public project board

Recommended columns:

1. Backlog
2. Ready
3. In progress
4. Review
5. Blocked
6. Done

The board should contain public, actionable work only. Raw research notes and private-agent tasks remain outside it until promoted into a reproducible public task.

## Repository boundary

Do not change the public repository into a mirror of the private development repository. The public repository has its own clean history and receives sanitized source snapshots/changes that satisfy `docs/PUBLIC_SOURCE_POLICY.md`.
