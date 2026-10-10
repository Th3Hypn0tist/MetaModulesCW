# MetaModules UI

MetaModules has a canonical UI: **WebEngine**.

The semantic authority for WebEngine is **WebEngineCW**, not MetaModulesCW.

MetaModulesCW specifies how MetaModules uses the exported WebEngine API contract.

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
WebEngine API contract
        ↓
WebEngine
        ↓
MetaModules UI
```

## Contract-based dependency

MetaModules does not require a particular WebEngine release number or knowledge of WebEngine internals.

It requires conformance to the WebEngine API contract.

Therefore:

```text
software version != dependency identity
contract conformance = dependency condition
```

Different WebEngine implementations or releases can satisfy the same MetaModules requirement if they conform to the referenced WebEngine API contract.

## MetaModules-owned UI mapping

MetaModulesCW may define how its own concepts map into WebEngine API inputs, including:

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
