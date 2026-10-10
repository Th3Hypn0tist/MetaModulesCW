# Universal model

A Universal is a reusable semantic primitive.

The Universal layer carries the stable meaning that many different Compositions can reuse.

A Universal can be understood as:

```text
canonical meaning
+ basic capabilities
+ canonical relations
+ semantic boundaries
+ invariants
```

The Universal remains deliberately domain-neutral where possible.

## Reuse principle

If multiple domain applications need the same semantic thing, the preferred model is one Universal reused in multiple Compositions.

Example:

```text
BusinessUniversal:Order
├─ ERP Composition
├─ CRM Composition
├─ procurement context
└─ sales context
```

The contexts differ. The canonical primitive does not need to fragment into separate ERP_Order, CRM_Order, PurchaseOrder or SalesOrder entities merely because different Compositions use it differently.

## Universal neutrality

Domain-specific details belong in Composition unless they are genuinely universal.

This keeps the Universal layer stable enough to survive replacement of:

- applications,
- vendors,
- presentation models,
- control surfaces,
- workflow arrangements.
