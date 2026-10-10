# MMDemo Industries Oy — design role

MMDemo Industries Oy is the reference business used during MetaModules design to test whether the model actually closes over a realistic company.

This document explains **why the demo exists and what it is intended to prove**.

It does not define the final canonical MMDemo company instance. The concrete company model belongs to the later `#ABS` pass.

## Why MMDemo exists

A generic architecture can look correct while still hiding missing semantics.

MMDemo is used as a deliberate pressure test against a complete business lifecycle so gaps can be found before contracts are frozen.

The demo should force the model to cover, together:

- sales,
- CRM,
- procurement,
- inventory / WMS,
- projects,
- delivery,
- installation,
- field service,
- billing,
- accounting,
- HR,
- payroll / expenses,
- management,
- Strategy,
- role-oriented projections.

The purpose is not to create another monolithic ERP example.

The purpose is to demonstrate that these areas can be composed from shared Universals without creating duplicate domain truth.

## Reference company shape

For design purposes, MMDemo is conceived as a small Finnish B2B company with a few dozen employees.

It is broad enough to:

- sell components,
- assemble solutions,
- install at customer sites,
- service and maintain delivered systems.

That business shape was chosen because it creates useful cross-domain pressure:

```text
CRM
→ Sales
→ Procurement / Inventory
→ Project / Delivery
→ Installation
→ Service
→ Billing
→ Accounting
→ Strategy
```

Cross-cutting areas such as Identity, HR, contracts, measurements and role views must work over the same underlying truth.

## What MMDemo must prove

### 1. Universal reuse

The same canonical Business Universals must participate in multiple domain Compositions.

For example, one Order semantic can be relevant to several operational views without becoming separate ERP_Order, CRM_Order or WMS_Order truth.

### 2. Composition replaceability

Operational domain modules must remain Compositions.

Changing or replacing an ERP, CRM or Strategy Composition must not require migration of the canonical business truth into a new application-owned model.

### 3. Projection reuse

The same canonical data must support different projections:

- operational,
- warehouse,
- accounting,
- management,
- role-specific,
- Strategy / War Room.

A new view must not require a new authoritative copy of the underlying data.

### 4. DWH resolution

The demo must make it possible to test the principle:

> Data moves. Surface materializes locally.

A local surface may resolve the required canonical data through DWH without transporting the original UI across environments.

### 5. Command Surface consistency

Every action exposed through the demo must ultimately be command-addressable through CS.

WebEngine, WebMini applications, Studio, REST, Q tools and other surfaces must converge on the same canonical capability rather than introducing UI-specific business logic.

### 6. AccessCore authority

The demo must be able to show that role differences are caused by AccessCore decisions and Projections, not separate implementations of the business process.

### 7. End-to-end business continuity

The reference business flow should remain understandable and operable from canonical Universals even if one Composition is replaced or removed.

## Reference lifecycle used during design

A representative customer lifecycle is:

```text
Opportunity
→ Quote
→ Order
→ Customer Delivery Project
→ Shipment
→ Invoice
→ Settlement / Payment
→ Accounting
→ Management / Strategy projections
```

Supporting lifecycle examples include:

```text
Procurement Order
→ Receipt
→ StockMovement
→ Inventory projection
→ Supplier Invoice
```

and:

```text
Customer Case
→ Service Project
→ Resolution / Return handling
```

These are design scenarios.

Their final canonical identities, relations, properties and concrete company configuration are defined in the `#ABS` model, not here.

## Master pipeline

The MMDemo master pipeline is intended as a structural demonstration surface for the whole business.

It should eventually allow a user to inspect a process stage and see:

- participating Universals,
- participating Compositions,
- relevant capabilities,
- available Projections,
- role views,
- command surface actions,
- related Strategy views.

The same structural graph can later support animation of data flow through the business.

This makes the architecture visible:

```text
one canonical truth
→ many domain contexts
→ many projections
→ many surfaces
```

without duplicating the underlying semantics.

## DOC / ABS boundary

This DOC owns the **design rationale and test intent** of MMDemo.

The later `#ABS` layer owns concrete statements such as:

- the actual MMDemo organization,
- exact roles and identities,
- actual process graph,
- exact Composition membership,
- exact pipeline topology,
- concrete demo data,
- concrete configured role projections.

This distinction is intentional:

```text
DOC:
why the reference business exists
what the architecture must demonstrate with it

ABS:
what MMDemo Industries Oy actually is in the canonical model
```
