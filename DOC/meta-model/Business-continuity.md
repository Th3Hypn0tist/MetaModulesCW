# Business continuity

Business continuity belongs below the Composition layer.

The purpose of the Universal model is that business operations and canonical truth remain valid even if a particular Composition becomes unusable.

## Failure separation

```text
Composition failure != canonical business failure
```

An ERP Composition may become tangled, be removed or be replaced while Orders, Invoices, Projects, Contracts, StockMovements and accounting truth remain valid.

## Replaceable layers

The architecture allows replacement of:

- Composition,
- vendor,
- Projection,
- SiteTree,
- control surface,
- presentation library,

without requiring migration into a new vendor-owned semantic model.

## Competitive boundary

Vendors therefore compete primarily on:

- Composition quality,
- workflow,
- projections,
- UX,
- tooling,
- conformance,
- operational specialization,

rather than ownership of canonical business truth.
