# Contract inheritance

MetaModulesCW composes independently owned semantic systems by **contract inheritance/reference**, not by copying their definitions.

This is essential to the no-duplicate-truth rule.

## Core rule

If another CW repository is the semantic authority for a component, MetaModulesCW does not become a second authority for that component.

Instead:

```text
component CW
   ↓ owns contracts
MetaModulesCW
   ↓ requires / inherits selected contracts
MetaModules integration
```

## Contract set, not software version

A dependency is expressed in terms of the contracts that must be satisfied.

The implementation's product version is not the semantic dependency.

For example:

```text
WebEngine implementation A
WebEngine implementation B
WebEngine implementation C
        ↓
all may satisfy the same
WebEngineCW contract set
        ↓
MetaModulesCW requirement is satisfied
```

This allows implementation releases to evolve independently from the MetaModules semantic model.

## Provenance still matters

Contract identity and provenance remain explicit.

MetaModulesCW must be able to identify exactly which contract definitions it requires. It must not rely on vague concepts such as "latest WebEngine" or infer compatibility from a software version string.

The rule is:

> require explicit contracts; do not require a product version as a substitute for contracts.

## WebEngine example

WebEngineCW owns WebEngine semantics.

MetaModulesCW owns only the integration:

```text
WebEngineCW
├─ WebEngine contracts
└─ WebEngine conformance

MetaModulesCW
├─ requires selected WebEngine contracts
├─ maps Composition structure to them
└─ adds MetaModules-specific integration constraints
```

No WebEngine contract text should be duplicated into MetaModulesCW merely for convenience.
