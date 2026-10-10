# Composition model

A Composition is a MetaModule that assembles existing capabilities into a domain, role, workflow or application context.

Composition is where contextual arrangement belongs.

## Composition may define

- selected Universals,
- relevant relations,
- contextual rules,
- projections,
- SiteTree,
- page composition,
- role-oriented views,
- domain-specific naming,
- workflow arrangement,
- configuration.

## Composition does not own reusable canonical truth

If a semantic fact already belongs to a Universal, Composition references it.

Examples of avoided duplication:

```text
ERP_Order
CRM_Order
WMS_Order
Strategy_Project
Everyday_Project
```

Preferred model:

```text
BusinessUniversal:Order
BusinessUniversal:Project
```

with context supplied by Composition.

## Replaceability

Composition is designed to be disposable relative to canonical truth.

A broken, obsolete or vendor-specific Composition can be replaced without redefining the underlying business semantics.

This is a major reason why domain products can become much thinner than traditional application silos.
