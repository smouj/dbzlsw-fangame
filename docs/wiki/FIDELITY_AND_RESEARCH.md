# Fidelity & ROM Research

DBZ LSW Fangame treats fidelity as an evidence problem, not as a marketing label.

A mechanic can be mechanically correct while its visible choreography is still incomplete. Likewise, a physical frame can be extracted correctly without proving when the original game uses it.

## Evidence layers

The project separates several layers that are easy to confuse:

1. **ROM data exists** — a table, handler, resource or byte sequence has been located.
2. **Mechanical meaning is understood** — the gameplay rule has been demonstrated.
3. **Presentation program is understood** — timing, branches, movement or FX are decoded.
4. **Physical resource is linked** — frame/FX/palette identity is demonstrated.
5. **Runtime consumes it** — production uses the ROM-backed path.
6. **Browser-visible output matches** — the final battle view reproduces the intended result.

A claim should never jump directly from layer 1 to layer 6.

## Public evidence vocabulary

The canonical status language is defined in [Fidelity](../FIDELITY.md). In short:

- **PASS** — the scoped claim is demonstrated by its required gate/evidence;
- **PARTIAL** — useful implementation/evidence exists, but a known part remains unresolved;
- **BLOCKED** — the required path or evidence is unavailable;
- **PENDING EVIDENCE** — the project deliberately refuses to invent the missing behaviour;
- **N/A** — the original behaviour does not apply.

Research-specific notes can additionally distinguish static vs dynamic evidence where useful.

## Static vs dynamic ROM research

### Static research

Static research can establish things such as:

- card records;
- handler dispatch;
- animation-resource descriptors;
- sequence/frame tables;
- durations and offsets encoded in data;
- palette/graphics pointers;
- literal presentation programs;
- known state-machine branches.

### Dynamic research

Some questions require observing the game while it runs, for example:

- semantic actor/target binding for special multi-object cases;
- runtime-selected branches that cannot be proven from static data alone;
- spatial anchors/coordinates whose meaning depends on live context;
- exact multi-actor ownership in special handlers.

Those items stay pending until a reproducible trace exists.

## Physical frame provenance

The project does not equate a runtime pose label with an original physical frame.

A useful mental model is:

```text
ROM AnimationResource
→ sequence
→ frame index
→ visual frame
→ metasprite / graphics / palette
→ physical image

runtime semantic pose
→ may reference that physical image
→ or a composite/fallback when no direct physical equivalent is demonstrated
```

This is why a 100% runtime pose-resolution metric is not the same as 100% physical-pose coverage.

## ROM → runtime → screen

The target fidelity chain is:

```text
ROM evidence
→ sanitized public descriptor
→ BattleRuntime / EventLog
→ presentation compiler
→ BattleTimeline
→ Pixi cue consumption
→ physical frame / FX / camera
→ browser-visible battle
```

The main fidelity work in alpha is closing gaps in this chain, not merely increasing the amount of reverse-engineering documentation.

## Public-source boundary

This repository does not distribute a ROM, save state, SRAM dump or raw proprietary asset corpus.

Public research should prefer:

- addresses/identifiers where appropriate;
- derived metadata;
- reproducible tooling;
- hashes/checksums;
- tests;
- diagrams;
- small public-safe evidence summaries.

See:

- [ROM Research Policy](../ROM_RESEARCH_POLICY.md)
- [Public Source Policy](../PUBLIC_SOURCE_POLICY.md)
- [Publication Checklist](../PUBLICATION_CHECKLIST.md)

## How to report a fidelity discrepancy

A useful report should identify:

- action/card;
- player/enemy side;
- expected original behaviour;
- observed fangame behaviour;
- deterministic reproduction steps if possible;
- whether the discrepancy is mechanical, visual, timing, physical-frame, camera/shot, FX or cleanup related.

Avoid opening an issue that only says “it feels wrong.” Precise evidence makes the issue actionable.

---

[← Story Mode](STORY_MODE.md) · [FAQ →](FAQ.md)
