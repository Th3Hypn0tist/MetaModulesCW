# MetaModules UI

MetaModules has a canonical UI: **WebEngine**.

The semantic authority for WebEngine is **WebEngineCW**, not MetaModulesCW.

MetaModulesCW specifies how MetaModules uses the WebEngine contract surface.

## Canonical path

```text
Business Universals
        ↓
Composition
        ↓
SiteEngine
        ↓
DWH + Command Surface + AccessCore
        ↓
SiteTree + Projections + permitted capabilities
        ↓
required WebEngineCW contracts
        ↓
WebEngine
        ↓
MetaModules UI
```

## Contract-based dependency

MetaModules does not require a particular WebEngine release number.

It requires a set of WebEngineCW contracts.

Therefore:

```text
software version != dependency identity
contract conformance = dependency condition
```

Different WebEngine implementations or releases can satisfy the same MetaModules requirement if they conform to the required contracts.

## MetaModules-owned UI mapping

MetaModulesCW may define how its own concepts map into WebEngine contract inputs, including:

- Composition-provided structure,
- SiteTree references,
- Projection availability,
- capability references,
- AccessCore-filtered visibility,
- DWH-resolved data context.

Those mappings do not redefine WebEngine behavior.

## WebMini distinction

WebMini is not the MetaModules UI.

WebMini is a local-first raw static HTTP server intended to serve local applications, including heavy tools such as Structure.

A WebMini application may consume the same backend capabilities, but it is a separate local application surface.
