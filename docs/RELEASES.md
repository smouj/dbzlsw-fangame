# Release Policy

DBZ LSW Fangame uses releases only for **redistributable public builds**. A Git tag is not permission to redistribute ROM-derived proprietary material.

## Versioning

During public alpha development, releases may use `0.x.y` semantic-style versions:

- patch: fixes/documentation without a new public gameplay capability
- minor: meaningful public feature/fidelity milestone
- major: reserved for a stable project contract later

## Release gates

A public build should not be published until:

1. public-source safety is green;
2. portable build/test checks are green;
3. distributed assets have passed public-source/media review;
4. known fidelity gaps are stated honestly;
5. release notes identify important regressions/limitations;
6. the archive contains no ROM, private research/workspace material or credentials.

## Fidelity language

Avoid blanket claims such as `ROM exact` for the whole game while known presentation/physical gaps remain. Prefer scoped statements such as `mechanically verified`, `ROM-backed route`, `visual sequence confirmed`, or `PARTIAL` as defined in `docs/FIDELITY.md`.

## Pre-release builds

Nightly/preview artifacts may be used later for testing, but they must obey the same redistribution boundary as normal releases.
