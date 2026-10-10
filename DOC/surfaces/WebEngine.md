# WebEngine integration

WebEngine is the canonical MetaModules UI.

**WebEngineCW is the single source of truth for WebEngine itself.**

MetaModulesCW does not redefine WebEngine rendering semantics, SiteTree interpretation rules, navigation behavior, lifecycle semantics or other WebEngine-owned behavior.

Instead, MetaModulesCW declares which WebEngine contracts its Compositions require and defines the integration between MetaModules structure and those contract surfaces.

## Contract inheritance, not product-version dependency

MetaModulesCW does not depend on a WebEngine software version.

The relevant question is:

> Which WebEngineCW contracts does this MetaModules model require?

A WebEngine implementation may have any release/build/version identifier as long as it conforms to the required contracts.

Conceptually:

```text
WebEngine implementation
        ↓ conforms to
WebEngineCW contracts
        ↑ required by
MetaModulesCW
```

The contract identities and provenance are what matter to conformance. Product/release version is not the semantic dependency.

## Ownership boundary

WebEngineCW owns:

- WebEngine semantics,
- WebEngine runtime behavior,
- UI interpretation rules,
- rendering behavior,
- WebEngine-specific lifecycle,
- WebEngine conformance rules.

MetaModulesCW owns:

- which WebEngine contracts MetaModules requires,
- how Composition structure is supplied to those contracts,
- how MetaModules SiteTree and Projections bind into the WebEngine contract surface,
- how MetaModules CS / AC / DWH semantics intersect with that surface,
- MetaModules-specific integration constraints.

## No duplicate truth

MetaModulesCW must not copy WebEngine contract definitions locally.

```text
WRONG:
MetaModulesCW
└─ duplicated WebEngine rule

RIGHT:
WebEngineCW
└─ WebEngine contract

MetaModulesCW
└─ reference / requirement to that contract
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
required WebEngineCW contracts
        ↓
WebEngine
        ↓
MetaModules UI
```
