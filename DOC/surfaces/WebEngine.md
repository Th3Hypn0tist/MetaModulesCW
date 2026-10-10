# WebEngine

WebEngine is an AccessCore-aware dynamic renderer.

Its purpose is to compose output from canonical structure, context, permitted capabilities and projections.

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

WebEngine is a renderer, not the Composition runtime authority.

SiteEngine hosts/materializes the active Composition and its runtime structure. WebEngine consumes that structure and renders the permitted result.

This keeps rendering replaceable:

```text
Composition
   ↓
SiteEngine
   ↓
runtime structure
   ├─ WebEngine
   ├─ another renderer
   └─ another control surface
```
