# Functional path

MetaModules uses a single conceptual functional path for actions.

```text
canonical capability
        ↓
Command Surface
        ↓
AccessCore
        ↓
allowed execution
        ↓
canonical data / DWH effects
        ↓
result
```

A presentation surface can initiate an action, but it is not the owner of the action.

Examples:

```text
WebEngine button ─┐
Studio action ────┤
REST request ─────┤
WebMini app ──────┤
                  ↓
             same CS capability
```

## Scope boundary

This DOC does not introduce AIGMos Trigger → Event → Runner automation semantics.

Those belong to a later AIGMos Ruleset and are not required for ordinary MetaModule business behavior.

Direct business logic remains direct unless an automation layer is intentionally composed later.
