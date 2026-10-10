# WebEngine

WebEngine is the canonical MetaModules UI layer.

It is an AccessCore-aware dynamic UI engine that materializes MetaModules Composition structure into the user-facing web surface.

Its purpose is to turn canonical MetaModules structure — Composition, SiteTree, Projections and authorized capabilities — into the operative MetaModules user interface.

## Rendering path

```text
request / context
       ↓
SiteEngine
       ↓
Composition + Projection + SiteTree
       ↓
Command Surface + AccessCore
       ↓
allowed data and capabilities
       ↓
WebEngine render
```

The same logical page may render differently for different identities because the available capabilities and data can differ.

## Lightweight surface principle

WebEngine is intended to keep the visible surface lightweight even when the backend system is large.

System complexity does not automatically become interface complexity.

## Difference from WebMini

WebMini:

- raw static HTTP server,
- typically local-first,
- heavy client applications are allowed,
- no AccessCore-dependent server-side rendering requirement.

WebEngine:

- dynamic renderer,
- AccessCore-aware,
- Composition/Projection/SiteTree-aware output construction.

The difference is where and how the output is composed, not application size.


## Relation to SiteEngine

WebEngine is the MetaModules UI, while SiteEngine is the Composition runtime host.

SiteEngine hosts/materializes the active Composition and its runtime structure. WebEngine consumes that structure and turns the permitted result into the MetaModules UI.

The separation keeps semantic ownership clear:

```text
Composition
   ↓
SiteEngine
   ↓
runtime structure
       ↓
   WebEngine
       ↓
MetaModules UI
```


## Canonical UI role

WebEngine is not merely one optional renderer among peers inside MetaModulesCW.

It is the UI contract for MetaModules.

That means MetaModulesCW must define enough of WebEngine behavior for a Composition to have a deterministic UI interpretation:

- SiteTree interpretation,
- page composition,
- Projection placement,
- capability presentation,
- AccessCore-filtered visibility,
- navigation behavior,
- refresh/re-resolution behavior,
- Composition-to-UI mapping.

Other control surfaces can exist against the same backend contracts, but they are external alternatives to the MetaModules UI rather than substitutes for defining it.

Conceptually:

```text
Business Universals
      ↓
Composition
      ↓
SiteEngine
      ↓
CS + AC + DWH
      ↓
WebEngine
      ↓
MetaModules UI
```
