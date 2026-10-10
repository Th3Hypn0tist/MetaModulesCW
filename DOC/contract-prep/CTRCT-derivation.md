# CTRCT derivation

The DOC pass is descriptive.

The next pass distills normative `#CTRCT` artifacts from the stable descriptive model.

CTRCT will define the operating model that conforming implementations, Compositions and surfaces follow.

## Derivation rule

Each contract statement should be traceable to an explicit DOC concept.

The contract layer should not invent new architecture during extraction.

Typical transformation:

```text
DOC concept:
"All functionality goes through Command Surface and AccessCore decides availability."

        ↓ distill

CTRCT:
normative requirements for command addressability,
authorization, visibility and bypass prevention.
```

## Expected contract families

The DOC set suggests at least these future contract areas:

- CW baseline / specification provenance
- identity-family responsibility
- Universal reuse
- Composition ownership boundaries
- Composition runtime / SiteEngine hosting
- Projection non-authority
- business-continuity separation
- DWH substrate and resolution
- Command Surface addressability
- AccessCore authorization
- Expose publication boundaries
- derived interface conformance
- WebMini boundary
- WebEngine rendering boundary
- Studio editing boundary
- runtime mounting, dependency resolution and lifecycle boundaries
- no-duplication rules.

## Contract quality test

A good CTRCT rule should be:

- normative,
- machine-checkable where possible,
- implementation-independent,
- traceable to DOC,
- free of duplicate semantic authority.

The contract pass is where principles become conformance rules.
