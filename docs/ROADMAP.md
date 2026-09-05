# Public Roadmap

This roadmap reflects technical priority, not release dates.

## P0 — Public source bootstrap

- Publish a sanitized source snapshot without ROM/private-workspace history.
- Preserve deterministic engine/runtime authority.
- Provide `npm ci`, development server and portable verification commands.
- Keep local ROM-dependent workflows explicitly separate.

## P0 — Battle choreography fidelity

- Make the BattleRuntime/GBC tick the single presentation-time authority.
- Apply ROM timeline `SHOT` / `SCREEN_MOTION` to the production Pixi viewport.
- Synchronize actor and target physical sequences at contact boundaries.
- Close projectile spawn/travel/contact/cleanup ordering.
- Synchronize HUD/hand changes with the visible action film.

## P0 — Physical sequence closure

Known priorities include the remaining incomplete physical sequences in the Golden Combat set, including continuous physical attacks and projectile-based actions whose physical frame/order evidence is not yet complete.

## P0 — Full battle E2E

- deterministic 1v1 battle from initialization to KO/results
- deterministic 2v2 battle including reserves, automatic entry and character switching
- no illegal AI commands
- no orphaned QTE/projectile/presentation state after terminal boundaries

## P1 — Renderer consolidation

- remove gameplay-significant duplicate DOM/CSS presentation paths
- establish Pixi as the single battle-framebuffer authority
- retain React for navigation, controls, accessibility and non-gameplay UI

## P1 — Public contributor ergonomics

- focused contributor commands
- browser CI
- good-first-issue backlog
- documented fixtures for work that does not require a ROM

## P2 — Story / metagame / polish

Story progression, broader metagame work and non-critical visual polish remain secondary to closing the core combat loop and public contributor experience.
