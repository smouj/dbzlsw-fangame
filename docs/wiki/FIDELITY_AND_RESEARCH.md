# Fidelity & ROM Research

DBZ LSW Fangame treats fidelity as an **evidence chain**, not as a marketing label.

A mechanic can be mechanically correct while its visible choreography is still incomplete. A physical frame can be reconstructed correctly without proving when the original game uses it. A ROM descriptor can be decoded correctly while production still renders a legacy approximation.

Those are different completion states and must stay separate.

## Evidence chain

The project tracks several layers that are easy to confuse:

1. **ROM data located** — table, handler, resource, pointer or byte sequence identified;
2. **mechanical meaning demonstrated** — the gameplay rule and its consumers are understood;
3. **presentation program decoded** — waits, branches, motion, sequence selection, FX or screen operations understood;
4. **physical resource linked** — fighter frame, metasprite, FX or palette identity demonstrated;
5. **runtime consumes it** — production uses the ROM-backed mechanic/presentation path;
6. **browser-visible output validated** — final BattleScreen behaviour matches the scoped evidence.

A claim must not jump directly from layer 1 to layer 6.

## Public completion vocabulary

The canonical public status terms are defined in [Fidelity](../FIDELITY.md):

- **PASS** — the scoped claim is demonstrated by the required evidence/gate;
- **PARTIAL** — useful implementation/evidence exists, but a known part remains unresolved;
- **BLOCKED** — a required path or evidence source is unavailable;
- **PENDING EVIDENCE** — behaviour is deliberately left unresolved rather than invented;
- **N/A** — the original behaviour does not apply.

These are project-facing completion terms.

## Research evidence labels

ROM research can additionally use more precise provenance labels when useful:

- **ROM_STATIC_VERIFIED** — demonstrated from static ROM/code/data analysis;
- **ROM_HANDLER_VERIFIED** — demonstrated from a specific handler/worker/control-flow path;
- **ROM_DYNAMIC_VERIFIED** — demonstrated by reproducible live execution/trace evidence;
- **PENDING_ROM_TRACE** — static evidence is insufficient and dynamic capture is required;
- **INFERRED / HYPOTHESIS** — useful working interpretation that must not be presented as established ROM fact.

A human-readable interpretation can be useful while still carrying a weaker provenance label than the underlying numeric/byte fact.

## Static vs dynamic ROM research

### Static research can establish

Examples include:

- the 125-card table and card fields;
- category + handler dispatch;
- AnimationResource descriptors;
- sequence/frame tables;
- duration ticks and encoded offsets;
- graphics/palette pointers;
- literal presentation VM programs;
- state-machine branches;
- resource/sequence selection tables;
- many Support/Defense/Stage rules.

### Dynamic research is still needed for some questions

Examples include:

- semantic actor/target binding in special multi-object cases;
- universal spatial anchors such as actor/target/contact positions when static code does not prove their semantic role;
- absolute multi-actor geometry;
- execution-dependent ownership/branch meaning that cannot be closed statically.

Those items stay pending until a reproducible trace exists.

## Physical fighter provenance

The project does not equate a runtime pose label with an original physical frame.

The ROM-side chain is conceptually:

```text
ROM form identity
→ actor visual profile
→ graphics bank + palette
→ AnimationResource
→ selected sequence
→ frame index / visual frame
→ metasprite
→ graphics blocks / tiles
→ physical fighter image
```

The runtime may then map that physical image into a semantic pose/action.

Therefore:

```text
runtime pose coverage = 100%
```

would still **not** prove:

```text
physical ROM pose coverage = 100%
```

if fallbacks/composites remain.

## Gameplay fidelity vs implementation determinism

The fangame uses deterministic state and RNG plumbing for reproducible tests.

That is a project architecture choice. It is not automatically evidence that every original GBC randomness source is implemented with the same internal algorithm. Where the ROM uses a specific counter/sample or timing source, exact parity must be demonstrated separately.

## ROM → runtime → screen

The desired end-to-end chain is:

```text
ROM evidence
→ sanitized canonical descriptor/data
→ BattleRuntime / Engine
→ EventLog
→ ROM-derived presentation profile/compiler
→ BattleTimeline
→ Pixi cue consumption
→ physical frame / FX / camera / screen motion
→ browser-visible battle
```

The active fidelity problem is often not “we know nothing about the ROM,” but “the evidence exists and production has not consumed all of it yet.”

## Project adaptation vs original-game fact

Documentation must explicitly distinguish:

- what the original game demonstrably does;
- what the fangame deliberately modernizes/adapts;
- what remains unresolved.

Story mode is an example: the project intentionally streamlines the original campaign into a scene-driven flow, but that must not be rewritten as a claim that the GBC game never contained exploration/navigation systems.

## Public-source boundary

This repository does not distribute a ROM, save state, SRAM dump or raw proprietary asset corpus.

Public research should prefer:

- derived metadata;
- scoped addresses/identifiers where appropriate;
- reproducible tooling;
- hashes/checksums;
- tests/verifiers;
- diagrams;
- public-safe evidence summaries.

See:

- [ROM Research Policy](../ROM_RESEARCH_POLICY.md)
- [Public Source Policy](../PUBLIC_SOURCE_POLICY.md)
- [Publication Checklist](../PUBLICATION_CHECKLIST.md)

## Reporting a fidelity discrepancy

A useful report identifies:

- action/card;
- player/enemy side;
- original expected behaviour and evidence source;
- observed fangame behaviour;
- deterministic reproduction steps when possible;
- discrepancy type: mechanic, timing, physical frame, actor/target choreography, camera/screen, FX, HUD or cleanup;
- whether the claim is static, dynamic or still inferred.

“Feels wrong” is a useful starting observation, but a reproducible scoped difference is what makes the issue actionable.

---

[← Story Mode](STORY_MODE.md) · [FAQ →](FAQ.md)
