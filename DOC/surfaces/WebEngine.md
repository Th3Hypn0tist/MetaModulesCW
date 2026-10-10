# WebEngine integration

WebEngine is the canonical MetaModules UI.

**WebEngineCW is the single source of truth for WebEngine itself.**

MetaModulesCW does not redefine WebEngine rendering semantics, SiteTree interpretation rules, navigation behavior, lifecycle semantics or other WebEngine-owned behavior.

Instead, MetaModulesCW references the exported WebEngine API contract and defines only the MetaModules-side binding to that contract.

## API contract dependency

MetaModulesCW does not depend on a WebEngine software version or on WebEngine internal contracts.

The relevant question is:

> Does WebEngine satisfy the WebEngine API contract referenced by MetaModulesCW?

Conceptually:

```text
WebEngineCW
    ↓ defines and exports
WebEngine API contract
    ↑ referenced by
MetaModulesCW

WebEngine implementation
    ↓ must satisfy
WebEngine API contract
```

The implementation behind that boundary is irrelevant to MetaModules.

## Ownership boundary

WebEngineCW owns:

- WebEngine semantics,
- WebEngine runtime behavior,
- UI interpretation rules,
- rendering behavior,
- WebEngine-specific lifecycle,
- WebEngine conformance rules.

MetaModulesCW owns:

- the reference to the WebEngine API contract,
- the MetaModules-side mapping into that API,
- the MetaModules-side expectations for data/context supplied to the API,
- MetaModules-specific integration constraints that do not redefine WebEngine behavior.

## No duplicate truth

MetaModulesCW must not copy WebEngine contract definitions locally.

```text
WRONG:
MetaModulesCW
└─ duplicated WebEngine rule

RIGHT:
WebEngineCW
└─ exports WebEngine API contract

MetaModulesCW
└─ references WebEngine API contract
```

This keeps WebEngine independently evolvable while preserving deterministic MetaModules UI behavior.

## Canonical MetaModules path

```text
Business Universals
        ↓
Composition
        ↓
SiteEngine
        ↓
DWH + CS + AC
        ↓
MetaModules UI structure
        ↓
WebEngine API contract
        ↓
WebEngine
        ↓
MetaModules UI
```
