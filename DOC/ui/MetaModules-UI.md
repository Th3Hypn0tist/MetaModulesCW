# MetaModules UI

MetaModules has a canonical UI layer: **WebEngine**.

This is a framework-level relationship, not an incidental implementation choice.

MetaModulesCW therefore covers both the canonical semantic structure and the contracts required to turn that structure into an operative user interface.

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
WebEngine
        ↓
MetaModules UI
```

## What the UI derives from structure

The MetaModules UI should derive as much as possible from canonical structure rather than duplicating application logic.

This includes:

- navigation from SiteTree,
- pages from Composition structure,
- visible Projections,
- available capabilities,
- role/context-specific visibility through AccessCore,
- links between related canonical objects,
- refresh/re-resolution behavior.

## Ownership boundary

WebEngine owns UI interpretation and rendering behavior.

It does not own:

- Business Universal semantics,
- canonical business data,
- AccessCore policy,
- DWH ownership,
- Command Surface capability semantics,
- Composition truth.

The UI is therefore strong inside the framework while still being downstream of canonical semantics.

## WebMini distinction

WebMini is not the MetaModules UI.

WebMini is a local-first raw static HTTP server intended to serve local applications, including heavy tools such as Structure.

A WebMini application may consume the same backend capabilities, but it is a separate local application surface.

## Why this belongs in MetaModulesCW

A Composition that defines SiteTree, Projections and presentation arrangement is incomplete if the framework does not define how those structures become UI.

For that reason, WebEngine behavior belongs in the same CW framework and its contracts are derived alongside Composition runtime contracts.
