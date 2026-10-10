# WebEngine

WebEngine is an AccessCore-aware dynamic renderer.

Its purpose is to compose output from canonical structure, context, permitted capabilities and projections.

## Rendering path

```text
request / context
       ↓
Command Surface + AccessCore
       ↓
allowed data and capabilities
       ↓
Composition + Projection + SiteTree
       ↓
rendered output
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
