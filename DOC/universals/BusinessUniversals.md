# Business Universals

The current authoritative Business Universal target set contains 32 reusable business primitives.

1. Identity
2. Project
3. Location
4. Asset
5. CatalogItem
6. Specification
7. Opportunity
8. LineItem
9. Quote
10. Order
11. Invoice
12. BalanceAccount
13. BalanceTransaction
14. Settlement
15. Account
16. JournalEntry
17. LedgerEntry
18. StockMovement
19. Lot
20. Shipment
21. HandlingUnit
22. Case
23. Assessment
24. Reservation
25. Entitlement
26. Contract
27. Plan
28. Filing
29. Measurement
30. RuleSet
31. Text
32. FileResource

## Explicit non-members

The following are not Business Universals in the current model:

- Relation
- Event
- State
- Period
- ResourcePool

## Important semantic locks

### Project

Project is recursive.

```text
Project
└─ Project
   └─ Project
      └─ ...
```

Tasks, subtasks, phases, work packages, milestones and programs can be contextual projections or labels of Project hierarchy rather than separate canonical primitives.

### StockMovement

There is no standalone canonical Stock entity.

Physical stock is derived from movements. Reservations are modeled separately.

A typical interpretation is:

```text
physical = SUM(relevant StockMovements)
reserved = active Reservations
available = physical - reserved
```

### RuleSet

RuleSet represents business/domain rule data semantics. It is not the generic execution or automation engine.

### Text

Text is intentionally generic.

Communication-specific semantics such as sender, recipient, thread, delivery or read state belong in Composition.

### Asset

Asset remains domain-neutral.

An apartment, machine, vehicle or other owned/managed object can be an Asset while domain-specific semantics are composed around it.
