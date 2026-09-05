# Contributing to DBZ LSW Fangame

Thank you for considering a contribution. This project values **reproducible evidence, deterministic behaviour and small reviewable changes** over speculative rewrites.

## Before you start

Read:

1. `docs/PUBLIC_SOURCE_POLICY.md`
2. `docs/ROM_RESEARCH_POLICY.md` when the change claims GBC fidelity
3. `CODE_OF_CONDUCT.md`

Never commit a ROM, save state, raw ROM dump, proprietary audio dump, private workspace material or unreviewed extracted asset corpus.

## Contribution types

Useful contributions include:

- gameplay/engine corrections
- PixiJS rendering and camera choreography
- animation/frame provenance
- projectile and FX synchronization
- browser E2E coverage
- ROM research expressed as reproducible derived findings
- documentation and contributor tooling

## Evidence standard

If a PR changes behaviour because "the original game does X", include evidence that another contributor can independently understand.

Good evidence may include:

- ROM address/bank and relevant derived interpretation
- emulator trace summarized without embedding copyrighted ROM data
- reproducible test case
- frame/tick observations from legally obtained local material
- a link to an already accepted public project finding

Do not label guesses as confirmed behaviour. Use `hypothesis`, `partial`, `pending evidence` or similar wording where appropriate.

## Workflow

1. Fork the repository.
2. Create a focused branch (`fix/...`, `feat/...`, `research/...`, `docs/...`).
3. Keep the change small enough to review coherently.
4. Run the public checks available in the source snapshot.
5. Open a pull request using the template.
6. Resolve review comments and keep evidence attached to the change.

Prefer squash-ready commits and descriptive messages, for example:

```text
fix(camera): apply ROM screen motion to cinematic viewport
test(combat): lock projectile contact order
docs(rom): document verified stage timing
```

## Behavioural authority

Gameplay rules belong in the deterministic battle/runtime layer. React/UI code should not become a second authority for damage, legality, RNG, QTE resolution or combat outcomes.

Presentation should derive from the battle timeline rather than independent UI timers.

## Pull request acceptance

A PR should normally satisfy all of the following that apply:

- portable CI is green
- no public-source policy violations
- deterministic behaviour remains deterministic
- new behavioural claims have evidence
- no silent fallback is introduced
- tests/gates are updated when a previously known partial becomes complete
- user-facing changes are checked at supported viewports

## Scope discipline

Do not mix unrelated refactors into a fidelity fix. A 30-line correction with strong evidence is generally more valuable than a 1,000-line rewrite whose behavioural differences cannot be audited.
