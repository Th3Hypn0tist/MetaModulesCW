# CW baseline

MetaModulesCW is built on AIGM Canonical Wireframe (CW), not beside it.

Current baseline:

- CW Core 1.2.0
- Canonical Contract Format 2.5.0
- CanonicalWireframe NodeTypes 1.18.0
- CanonicalWireframe Dependency Rules 4.0.0

MetaModules adds domain-specific semantics through a MetaModules specification set, NodeTypes and Rulesets while leaving CW Core generic.

## Relevant CW semantics

The current baseline establishes several important identity and addressing rules:

- Entity identity is model-global.
- Property identity is owner-local.
- Cross-Entity Property addressing is explicit and includes both Entity and Property identity.
- Function input/output/logic references are owner-local.
- Specification provenance is immutable.
- StructureTree is hierarchical navigation, not a second source of semantic truth.
- Links provide relational navigation through canonical Property semantics.
- Renderer concerns how canonical structure is shown, not what it means.

## Validation model

CW provides two separate validation concerns:

- specification-set integrity,
- canonical-model validity under the selected specification set.

The result classes distinguish at least:

- INVALID_SPECIFICATION
- INVALID_MODEL
- UNREADY
- READY
- IMPLEMENTATION_FAILURE

`UNREADY` and `INVALID_MODEL` are intentionally different states.

## MetaModules relationship to CW

```text
CW Core
  ↓
MetaModules NodeTypes / Rulesets
  ↓
MetaModules specification set
  ↓
MetaModules canonical models
```

MetaModules does not introduce a parallel canonical format, edge store, relation system, identity system or semantic authority.
