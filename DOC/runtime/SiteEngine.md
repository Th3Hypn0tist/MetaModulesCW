# SiteEngine

SiteEngine is the runtime host for Composition-based sites and application structures.

It exists because a Composition definition and a running Composition are different concerns.

A Composition describes **what is assembled**. SiteEngine provides the runtime context in which that structure is mounted, resolved and made operational.

## Core responsibility

Conceptually:

```text
Composition
   ↓
SiteEngine
   ├─ resolve required capabilities
   ├─ resolve data through DWH
   ├─ bind command capabilities through CS
   ├─ apply AccessCore availability
   ├─ materialize SiteTree
   ├─ materialize Projections
   └─ expose runtime structure to WebEngine and other permitted consumers
```

SiteEngine is therefore part of the contract surface that MetaModulesCW must describe.

Without this layer, CW could describe a Composition structurally while leaving undefined how a conforming runtime is expected to host it.

## What SiteEngine does not own

SiteEngine does not become a new semantic authority.

It does not own:

- Business Universal truth,
- Composition semantics,
- authorization policy,
- canonical data,
- Projection truth,
- renderer-specific UI behavior.

Those remain owned by their proper layers.

SiteEngine coordinates them at runtime.

## Runtime boundaries

A conforming SiteEngine runtime needs explicit contracts for at least:

- mounting a Composition,
- resolving its dependency closure,
- resolving referenced Universals and platform capabilities,
- connecting data access through DWH,
- connecting actions through Command Surface,
- applying AccessCore decisions,
- materializing SiteTree and Projection availability,
- exposing the resulting runtime structure to WebEngine as the canonical MetaModules UI, and to other permitted consumers where applicable,
- unmounting / replacing a Composition without transferring canonical truth into the runtime host.

The exact normative rules belong to the later `#CTRCT` pass.

## Replaceability

The runtime host must not make Composition semantics renderer-specific.

A Composition's canonical business semantics must remain independent of the UI layer. Inside MetaModules, WebEngine is the canonical UI consumer of the runtime structure:

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

The same backend capabilities may also be exposed to other control surfaces without changing canonical business semantics.
```

This is part of the broader MetaModules principle:

> canonical meaning remains stable while runtime and surface materializations can change.
