# WebEngine API boundary

WebEngineCW is the sole semantic authority for WebEngine.

MetaModulesCW depends on WebEngine through one external contract boundary:

> **WebEngine API contract**

The word API here means the canonical contract surface between MetaModules and WebEngine. It is not limited to REST or any particular transport.

## Boundary

```text
MetaModulesCW
      ↓ references
WebEngine API contract
      ↓ implemented by
WebEngine
```

MetaModulesCW does not inherit WebEngine internals.

It does not need to know:

- WebEngine internal module structure,
- rendering implementation,
- internal dependency graph,
- programming language,
- storage choices,
- internal contract decomposition,
- release/build/version number.

## Conformance rule

From MetaModules' perspective, WebEngine is conformant when it satisfies the referenced WebEngine API contract.

```text
internal implementation A ─┐
internal implementation B ─┼─> WebEngine API contract ─> MetaModules compatible
internal implementation C ─┘
```

This creates a strict black-box boundary.

## Ownership

WebEngineCW owns:

- API contract definition,
- API semantics,
- input/output meaning,
- error semantics,
- WebEngine behavior behind the API,
- WebEngine conformance.

MetaModulesCW owns:

- the reference to the API contract,
- MetaModules-side inputs supplied to it,
- MetaModules-side use of outputs,
- integration constraints that belong specifically to MetaModules.

## No duplicated API truth

MetaModulesCW must not copy the WebEngine API definition.

It references its canonical identity in WebEngineCW.

Therefore:

```text
WebEngineCW = API truth
MetaModulesCW = API consumer
```

Changes to WebEngine internals are irrelevant to MetaModules unless they change conformance to the referenced API contract.
