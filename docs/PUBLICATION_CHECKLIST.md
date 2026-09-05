# Public Publication Checklist

Use this checklist whenever code, media, research artefacts or releases move into the public repository.

## Source and privacy

- [ ] No ROM, save state, SRAM, raw dump or proprietary audio dump is tracked.
- [ ] No `.openclaw`, memory/workspace state or agent scratch material is tracked.
- [ ] No local developer paths (`C:\\Users`, `D:\\...`, `/home/<user>`, `/Users/<user>`) appear in public files.
- [ ] No credentials, tokens, private keys or `.env` values are present.
- [ ] No private repository URL or private-only attachment is required to understand the public change.
- [ ] Public-source safety CI is green.

## Technical quality

- [ ] The change has a narrow, reviewable scope.
- [ ] Behavioural changes identify the owning layer (engine/runtime/presentation/UI).
- [ ] Deterministic systems remain deterministic.
- [ ] Tests or verifiers cover the behaviour being changed when practical.
- [ ] Known PARTIAL/HYPOTHESIS states remain explicit.

## ROM / fidelity claims

- [ ] Claims use the evidence vocabulary from `docs/FIDELITY.md`.
- [ ] Evidence is reproducible without redistributing copyrighted ROM data.
- [ ] A visual approximation is not described as confirmed ROM behaviour.
- [ ] Newly resolved physical/timing gaps update the relevant gate/documentation.

## Media

- [ ] Screenshots show the real referenced build.
- [ ] No private/debug/local data is visible.
- [ ] Captions do not overstate fidelity.
- [ ] Media provenance/publication rights have been reviewed.
- [ ] Repository branding uses project-original artwork rather than extracted character/game art.

## Release readiness

- [ ] Portable CI is green.
- [ ] Required `main` checks are green.
- [ ] README/status/roadmap reflect the release accurately.
- [ ] Release notes distinguish completed, partial and known issues.
- [ ] Distributed archives contain only material approved for public redistribution.
