# Public Source Policy

This document defines what may cross from local/private research into the public `dbzlsw-fangame` repository.

## Principle

The public repository contains **redistributable source, tooling and derived technical knowledge**. It is not a ROM archive, extracted-asset archive or mirror of a private workspace.

## Classification

Every new family of material should fit one of these categories:

| Class | Public? | Examples |
|---|---:|---|
| `PUBLIC_ORIGINAL` | Yes | original TypeScript, tests, docs, build tooling |
| `PUBLIC_DERIVED_DATA` | Review required | compact tables/timings/identifiers derived from research |
| `LOCAL_ROM_REQUIRED` | No output by default | local generated sprites, raw traces, disassembly-dependent exports |
| `PRIVATE_RESEARCH` | No | internal audits, agent state, working notes, unfiltered captures |
| `DO_NOT_DISTRIBUTE` | No | ROM images, proprietary dumps, save states, extracted audio archives |

## Never commit

- `.gb`, `.gbc` or other ROM images
- emulator save states or SRAM saves
- raw memory/bank dumps
- large copied disassembly blocks that reproduce copyrighted source material
- proprietary audio dumps
- private workspace/agent state (`.openclaw`, `memory/`, temporary audits)
- bulk ROM-extracted asset corpora unless distribution rights have been established and maintainer review explicitly approves them

## Derived research

A technical fact can often be public even when the source material used to discover it cannot. Prefer concise derived statements such as:

```text
handler: $0A
animation resource: $2C
contact offset: 17 ticks
```

over embedding the underlying ROM bytes.

## Public release gate

`Public source safety` CI checks common prohibited paths and unexpectedly large tracked files. Passing that workflow is necessary but not sufficient: contributors and reviewers remain responsible for the nature and provenance of submitted material.

## History

The public repository intentionally starts from a clean history rather than exposing the private research repository's historical object database. This reduces the chance that previously deleted private or proprietary artefacts remain recoverable from Git history.
