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

WebEngineCW owns the complete internal WebEngine contract model and exports the WebEngine API contract.

MetaModulesCW references only that exported API contract:

```text
WebEngineCW
├─ internal WebEngine semantics
├─ internal WebEngine contracts
├─ conformance rules
└─ exports: WebEngine API contract

MetaModulesCW
└─ references: WebEngine API contract
```

MetaModulesCW does not need to know which internal WebEngine contracts, modules, functions or implementation strategies satisfy the API contract.

No WebEngine contract text should be duplicated into MetaModulesCW merely for convenience.


## Black-box conformance boundary

For MetaModules, WebEngine is a contract boundary.

```text
MetaModulesCW
     ↓
WebEngine API contract
     ↓
WebEngine
```

Everything below the API contract is WebEngineCW territory.

MetaModules conformance asks only:

> Does the connected WebEngine satisfy the referenced API contract?

It does not ask:

- which internal WebEngine architecture is used,
- which language is used,
- which modules implement the behavior,
- which internal contracts are composed,
- which WebEngine release number is running.

Those concerns are irrelevant to MetaModules as long as the API contract is satisfied.
