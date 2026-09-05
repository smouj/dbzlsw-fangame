# Development Guide

## Current public-source stage

The public repository is being populated from a sanitized source snapshot tracked in issue #1. Until that issue closes, do not assume that the root contains the complete runnable application.

The public history intentionally does not inherit the private research/workspace history.

## Supported development model

Once the application snapshot is present, the contributor baseline is expected to be:

```bash
git clone https://github.com/<your-user>/dbzlsw-fangame.git
cd dbzlsw-fangame
npm ci
npm run dev
```

Portable contributor commands will expose a small stable surface such as typecheck, test, build and verify. Specialist ROM-local commands remain separate because CI does not receive a game ROM.

## Branch naming

Prefer focused names:

- `fix/camera-screen-motion`
- `fix/energy-bomb-projectile-order`
- `feat/full-battle-e2e`
- `research/cont-punch-sequence`
- `docs/fidelity-evidence`

## Architecture rule

Gameplay authority belongs to the deterministic runtime/engine. UI components must not independently calculate legality, damage, RNG, QTE resolution or combat outcomes.

Visible combat presentation should derive from the GBC-timed presentation timeline rather than independent React/CSS timers.

## Local ROM research

ROM-dependent workflows are optional for general contribution. When used:

1. provide your own legally obtained game image locally;
2. keep it outside tracked source paths;
3. verify the expected game revision/hash using project tooling when available;
4. commit only reviewed, redistributable derived findings;
5. never attach a ROM or raw dump to an issue or pull request.

## Before opening a pull request

- rebase/update against current `main` as appropriate;
- run the portable checks relevant to your change;
- confirm `Public source safety` is satisfied;
- remove local paths, temporary screenshots and debug data;
- attach reproducible evidence for behavioural claims;
- explain any remaining PARTIAL/HYPOTHESIS state explicitly.

See `CONTRIBUTING.md` for the full acceptance policy.
