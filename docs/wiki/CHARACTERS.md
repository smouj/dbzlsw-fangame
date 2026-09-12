# Characters

Characters are represented by a fighter identity plus a specific **form**. The project treats form identity as gameplay data, not as a cosmetic skin.

## Fighter and form identity

A form can affect:

- card compatibility;
- available LIMITs;
- battle statistics;
- physical fighter graphics;
- animation-resource selection;
- portraits/overworld representation;
- story/encounter context.

For ROM-backed work, the important chain is conceptually:

```text
character / form
→ ROM form identity
→ visual profile
→ graphics / palette
→ animation resource + sequence
→ physical frame
```

The project avoids matching forms only by visual similarity because that can silently associate the correct name with the wrong physical fighter data.

## Teams

The active battle model supports:

- **1v1** battles;
- **2v2** battles;
- active + reserve members;
- manual character switching where legal;
- automatic continuation after KO when a reserve remains.

The exact public setup UI may change during alpha, but team state belongs to the deterministic battle/runtime layer.

## Player loadout vs rival loadout

The intended setup model is asymmetric:

### Player

The player can configure the permitted parts of their battle setup, including fighter/form and their own loadout.

### Rival

The rival can be selected/inspected, but its canonical deck and LIMIT setup should come from the appropriate game/ROM-derived preset rather than becoming a second freely editable player loadout.

This keeps versus setup useful without erasing the identity of original encounters and CPU configurations.

## Physical animation frames

A runtime pose name such as `idle`, `guard`, `beam_charge` or `hurt` is not automatically proof that the original ROM contains a dedicated physical sequence with that semantic label.

The project distinguishes:

- **PHYSICAL** — directly linked to demonstrated physical ROM frames;
- **COMPOSITE** — built from demonstrated parts/sequences;
- **FALLBACK** — runtime substitute when a dedicated physical pose is unavailable;
- **REFERENCE_FX** — visual effect rather than fighter pose;
- **MISSING / UNRESOLVED** — evidence not yet sufficient.

This vocabulary prevents runtime convenience from being mistaken for original-game evidence.

## Character catalogue

The public project currently documents the character/form system at the architectural level. A full per-character catalogue — forms, stats, LIMITs, compatibility and verified physical sequences — should be generated from sanitized public data rather than maintained manually in multiple places.

---

[← Cards](CARDS.md) · [Stage Attacks →](STAGE_ATTACKS.md)
