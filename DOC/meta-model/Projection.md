# Projection model

A Projection is a view of existing canonical truth.

Projection changes what is selected, arranged, labeled or presented. It does not create a second authoritative copy of the underlying data.

Examples:

- WMS inventory view,
- ERP operational view,
- CFO role view,
- CEO dashboard,
- Strategy War Room,
- customer-facing view,
- mobile view.

The same canonical object may participate in many projections simultaneously.

## Projection and truth

```text
canonical truth
   ├─ Projection A
   ├─ Projection B
   └─ Projection C
```

A Projection may cache or materialize derived information for performance, but that derived representation remains rebuildable from canonical sources.

## Role projections

Executive and job-specific views are Projections, not separate canonical Strategy modules.

For example:

- CEO
- CFO
- COO
- CTO/CIO
- CHRO
- CSO

are role-oriented views over existing data and capabilities.

Studio can configure which Projections appear on which WebEngine pages.
