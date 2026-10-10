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

The runtime does not imply one renderer.

WebEngine can render SiteEngine-hosted structure dynamically.

A local application can consume the same canonical capabilities through appropriate Exposes.

The runtime contract exists so that Composition behavior remains predictable independently of the concrete surface.
