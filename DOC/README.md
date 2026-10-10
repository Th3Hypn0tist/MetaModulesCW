# MetaModulesCW — DOC pass

This directory is the descriptive specification layer for the complete MetaModules framework.

The purpose of the DOC pass is to make the entire operating framework explicit before normative `#CTRCT` artifacts are distilled from it. Independently owned components remain external semantic authorities and are inherited by contract rather than copied into MetaModulesCW.

## Layer boundaries

- `#ABS` — what a semantic thing is.
- `#FILE` — what happens in practical implementation semantics.
- `#DOC` — explanatory and descriptive specification.
- `#CTRCT` — normative operating model and conformance requirements.

This pass intentionally does **not** create `#CTRCT`, `#ABS` or `#FILE` artifacts.

MMDemo Industries Oy may be discussed in DOC as part of the design process: why it exists, what architectural questions it is intended to test, and which parts of MetaModules it should exercise.

The concrete MMDemo business model itself — its actual company structure, roles, processes, pipeline, configured Compositions and other modeled facts — belongs later to `#ABS`.

## DOC index

### Foundation
- [CW baseline](foundation/CW-baseline.md)
- [Identity families](foundation/Identity-families.md)
- [Contract inheritance](foundation/Contract-inheritance.md)

### Meta model
- [MetaModule model](meta-model/MetaModule.md)
- [Universal model](meta-model/Universal.md)
- [Composition model](meta-model/Composition.md)
- [Projection model](meta-model/Projection.md)
- [Business continuity](meta-model/Business-continuity.md)

### Universals
- [Business Universals](universals/BusinessUniversals.md)
- [Universal Platform](universals/UniversalPlatform.md)

### Data
- [DWH substrate](data/DWH.md)

### Runtime
- [Composition runtime](runtime/Composition-runtime.md)
- [SiteEngine](runtime/SiteEngine.md)

### Execution
- [Command Surface](execution/CommandSurface.md)
- [AccessCore](execution/AccessCore.md)
- [Functional path](execution/Functional-path.md)

### Expose and derived interfaces
- [Expose](expose/Expose.md)
- [Derived interfaces](expose/Derived-interfaces.md)

### UI and surfaces
- [MetaModules UI](ui/MetaModules-UI.md)
- [WebEngine integration](surfaces/WebEngine.md) — MetaModules use of WebEngineCW contracts
- [WebMini](surfaces/WebMini.md)
- [Studio](surfaces/Studio.md)

### Composition families
- [Business Domain](compositions/BusinessDomain.md)
- [Strategy](compositions/Strategy.md)
- [Everyday](compositions/Everyday.md)

### Design process
- [MMDemo Industries Oy — design role](design/MMDemo-design-role.md)

### Contract preparation
- [CTRCT derivation](contract-prep/CTRCT-derivation.md)

## Core model

```text
Canonical semantics
    ↓
Universals
    ↓
DWH
    ↓
Composition / MetaModule
    ↓
SiteEngine / composition runtime
    ↓
SiteTree + Projection
    ↓
Command Surface + AccessCore
    ↓
Expose
    ↓
required WebEngineCW contracts
    ↓
WebEngine
    ↓
MetaModules UI
```

The model is designed so that semantic meaning is defined once and reused structurally.

> One truth. Many topologies. No duplicate truth.
