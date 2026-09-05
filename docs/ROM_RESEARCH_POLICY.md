# ROM Research and Evidence Policy

The project separates **evidence quality** from implementation confidence.

## Evidence levels

### Confirmed

Reproducible from the original game through a stable method such as disassembly analysis, deterministic emulator trace, repeatable frame/tick observation or an already-reviewed project oracle.

### Strong / incomplete

Multiple observations agree but one part of the chain is still unresolved—for example the command path is known but a physical animation sequence is not fully mapped.

### Hypothesis

A plausible interpretation that still requires verification. Hypotheses may guide research but must not be presented as canonical behaviour.

### Not applicable

The source game intentionally has no corresponding behaviour/resource, or the concept is outside the original game's domain.

## Research record

A useful research note answers:

- What exact question was investigated?
- Which game revision/region was observed?
- What method was used?
- What addresses, handlers, ticks or observable transitions matter?
- What remains uncertain?
- Which public test or implementation should change as a result?

## Copyright-safe reporting

Report **derived facts**, not ROM redistribution. Do not attach the ROM, save states, complete bank dumps or copied proprietary source data.

Short identifiers, addresses, interpreted control flow, hashes and independently written descriptions are preferred.

## From evidence to code

A ROM-fidelity PR should make the evidence-to-behaviour mapping inspectable:

```text
evidence
  ↓
ROM/domain descriptor
  ↓
deterministic runtime behaviour
  ↓
presentation timeline
  ↓
renderer
  ↓
regression gate
```

If a link is still missing, keep the feature explicitly partial rather than filling the gap with an undocumented approximation.
