# Composition runtime

MetaModulesCW must describe not only what a Composition contains, but also the runtime model under which Compositions operate.

This runtime description is necessary so that later `#CTRCT` artifacts can define conformance for Composition hosts.

## Definition versus runtime

```text
Composition definition
!=
running Composition instance
```

The definition contains references, rules, Projections, SiteTree structure and other declarative arrangement.

The runtime host resolves and materializes those definitions in an operational context.

SiteEngine is the primary runtime-host concept for this model.

## Runtime inputs

A running Composition may depend on:

- Business Universals,
- Platform Universals,
- DWH-resolved data,
- Command Surface capabilities,
- AccessCore decisions,
- Projections,
- SiteTree,
- Expose bindings,
- surface-specific renderers.

The runtime host coordinates these dependencies without taking ownership of their canonical semantics.

## Runtime closure

The runtime must be able to determine whether the selected Composition has all required dependencies available.

This is analogous to dependency closure rather than semantic duplication.

If a required capability is unavailable, the runtime should be able to represent that as an explicit runtime/conformance condition instead of silently inventing a substitute.

## Runtime lifecycle

The descriptive model needs to support later contracts for:

```text
resolve
→ mount
→ operate
→ refresh / re-resolve
→ unmount / replace
```

The lifecycle must preserve canonical business truth outside the replaceable Composition/runtime layer.

## Relationship to surfaces

The MetaModules runtime has a canonical UI path: SiteEngine-hosted Composition structure is rendered through WebEngine.

Other control surfaces may consume the same backend capabilities through appropriate Exposes, but that does not make WebEngine incidental to MetaModulesCW.

The runtime contract exists so that Composition behavior remains predictable and WebEngine can interpret the same Composition structure consistently.
