# MetaModulesCW

> **Build the semantics once. Derive everything else from structure.**

MetaModulesCW defines the canonical MetaModules framework on top of AIGM Canonical Wireframe (CW). It includes the semantic model, Composition runtime contracts, data/access boundaries and the canonical MetaModules UI contract.

The core idea is deliberately strict:

> If something can be referenced, composed, projected, inherited, resolved or reused, it must not be duplicated.

MetaModules is not an application suite and it is not an ERP implementation. It defines the reusable semantic primitives, contracts, composition rules and operating framework from which ERP, CRM, WMS, HRM, Strategy, Everyday and other systems can be composed and run.

The business goal is equally strict:

> Canonical business truth must survive replacement of applications, compositions, vendors and control surfaces.

---

## 1. Canonical foundation

MetaModulesCW is defined using the current CW specification family.

Current target baseline:

- **CW Core:** 1.2.0
- **Canonical Contract Format:** 2.5.0
- **CW NodeTypes:** 1.18.0
- **CW Dependency Rules:** 4.0.0

MetaModules must follow CW format and identity rules exactly. It must not invent a parallel storage, graph, relation or specification format.

Important CW 1.2 / CCF 2.5 semantics include:

- Entity identity is model-global.
- Property identity is local to its owning Entity.
- Cross-Entity Property addresses are explicit.
- Canonical references are explicit and must not be guessed from paths, filenames, rendering or naming conventions.
- StructureTree is navigation, not a second semantic authority.
- Links are canonical Property semantics, not a parallel edge store.
- The selected specification set defines interpretation and validation context.

MetaModules adds its own NodeTypes / Rulesets / specification set **on top of CW Core**. It does not modify CW Core.

AIGMos Ruleset is a separate concern and is **not part of this repository scope at this stage**.

---

## 2. CW identity families must retain their exact roles

The repository follows CW canonical identity families.

### `#ABS`

Abstractions: what a semantic thing **is**.

Examples:

```text
#ABS:BusinessUniversal:Order.cw
#ABS:BusinessUniversal:Project.cw
#ABS:Composition:BusinessDomain:ERP.cw
```

### `#FILE`

Practical implementation semantics: what **happens in implementation**.

`#FILE` does **not** mean that the CW Node contains source code or that the Node simply represents a physical source file.

Example:

```text
#FILE:BusinessUniversal:Order.cw
```

describes the practical semantics of Order operations and behavior. A PHP, Python, Rust or other implementation may materialize that meaning, but the source code itself is not the canonical semantic authority.

### `#DOC`

Specifications, explanations and human-readable semantic documentation.

Example:

```text
#DOC:BusinessUniversal:Order.cw
```

### `#CTRCT`

Normative contracts, membership, boundaries, requirements and conformance claims.

Example:

```text
#CTRCT:BusinessUniversal:Order.cw
```

The full canonical identity is significant. Do not silently shorten:

```text
#FILE:BusinessUniversal:Order.cw
```

to:

```text
#FILE:BusinessUniversal:Order
```

---

## 3. MetaModule principle

A MetaModule Composition means, in practice:

> **Take these existing capabilities, connect them this way, and present/use them this way.**

A Composition does not copy the canonical truth owned by Universals.

A Composition may define:

- membership / references to Universals,
- composition-specific relations,
- composition-specific rules,
- projections,
- SiteTree structure,
- presentation defaults,
- workflow / arrangement,
- allowed combinations and constraints.

A Composition must not redefine a Universal merely because a domain uses it differently.

Examples:

```text
ERP
CRM
HRM
WMS
Projects
Service
Finance
Strategy
Everyday
```

are all Composition definitions over the same reusable foundation.

There must not be separate canonical entities such as:

```text
ERP_Order
CRM_Order
WMS_Order
Strategy_Project
Everyday_Project
```

when the meaning is already provided by:

```text
BusinessUniversal:Order
BusinessUniversal:Project
```

Domain meaning belongs in Composition where it is genuinely domain-specific.

---

## 4. Business Universal invariant

The Business Universal layer owns the reusable business primitives and their canonical semantics.

A Business Universal consists of:

```text
canonical meaning
+ basic operations
+ canonical relations
+ contract boundaries
+ invariants
```

The current authoritative Business Universal target set contains 32 primitives:

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

Explicitly **not** Business Universals:

- Relation
- Event
- State
- Period
- ResourcePool

### Important semantic locks

#### Project is recursive

A task does not require a separate canonical Task primitive.

```text
Project
└─ Project
   └─ Project
      └─ ...
```

A child Project may be projected as:

- task,
- subtask,
- phase,
- work package,
- milestone,
- program,
- or another contextual name.

The canonical primitive remains Project.

#### Stock is derived

There is no standalone canonical Stock primitive.

Stock truth is derived from StockMovement.

Examples:

```text
physical stock = sum(relevant StockMovements)
reserved stock = active Reservations
available stock = physical - reserved
```

A balance may be cached as a projection, but the cache must remain rebuildable from canonical truth.

#### RuleSet is domain/business data

BusinessUniversal:RuleSet must not silently become a generic execution or workflow engine.

#### Text replaces Message

Message is too communication-domain-specific for the Universal layer.

`Text` is the reusable primitive. Sender, recipient, thread, delivery, read-state and similar communication semantics belong in Composition.

#### Asset is domain-neutral

A real-estate apartment is an Asset.

Real-estate-specific meaning such as property listing, lease context or building-specific semantics is composed around the Asset rather than creating a new universal primitive.

---

## 5. Business continuity belongs below Composition

A major invariant of MetaModules is:

> **Composition failure must not invalidate Universal operation.**

Business operations must remain functional even if a Composition becomes badly designed, tangled or unusable.

A broken ERP Composition must not corrupt or invalidate:

- Orders,
- Invoices,
- StockMovements,
- Projects,
- Contracts,
- accounting truth,
- or other canonical Universal data.

Therefore Composition is intentionally replaceable.

A company may:

- remove one ERP Composition,
- mount another ERP Composition,
- replace a vendor,
- rebuild SiteTree,
- replace projections,
- replace an entire control surface,

without migrating the canonical business truth into a new vendor-specific model.

This keeps the ecosystem open to tool builders.

> **Vendors compete on Composition quality, projections, workflow and UX — not ownership of canonical business truth.**

---

## 6. DWH is the canonical data substrate

MetaModules operates over DWH contracts.

DWH is responsible for resolving data independently of where that data physically resides.

The MetaModule contract defines semantic ownership and allowed interaction, not SQL, ORM or storage-engine implementation.

A typical contract may define:

```text
owns
reads
writes
relations
required contracts
allowed projections
constraints
```

but it does not need to define:

```text
SQL schema
database engine
ORM
transport implementation
programming language
```

The important system rule is:

> **Data moves. Surface materializes locally.**

A remote UI surface is not transported as the system model. Instead:

```text
remote canonical data
        ↓
       DWH
        ↓
local resolution / projection
        ↓
local control surface
```

This allows the same canonical business truth to appear through completely different local surfaces.

---

## 7. Universal Platform

The MetaModules model also includes reusable Platform Universals.

The current Platform family includes the canonical platform capabilities required by MetaModule compositions, including:

- IAM
- AccessCore
- DWH
- EXTPeer
- NetworkService
- LibraryMount
- SymbolNamespace

Platform Universals must stay semantically separate from Business Universals.

The exact Platform registry is authoritative; file presence alone must not imply membership.

Old `nanoCMS` terminology must not be reintroduced as a Platform Universal. That concept belonged to an older web-surface model and has been superseded by the current WebMini / WebEngine split.

---

## 8. Command Surface is the functional spine

One of the strongest invariants is:

> **If it can be done, it can be commanded.**

More precisely:

> **All functional operations go through Command Surface (CS).**

No UI may own a private business action that bypasses CS.

The canonical execution shape is:

```text
capability / command
        ↓
Command Surface
        ↓
AccessCore
        ↓
allowed / denied
        ↓
canonical operation
```

AccessCore decides what may be shown and what may be executed in the current context.

This means that control surfaces do not invent capabilities. They ask for the available command surface and render the authorized result.

Hard invariants:

```text
NO_UI_ONLY_ACTIONS
NO_AC_BYPASS
```

If a function exists only behind one GUI button, the architecture is leaking implementation into functionality.

### REST follows from the same structure

REST is effectively an Expose over CS.

The business API does not need a second independent semantic definition.

For example, one canonical capability can be surfaced as:

```text
CS command
REST endpoint
WebSocket operation
MCP operation
WebEngine action
Studio action
```

while preserving the same underlying operation and authorization path.

---

## 9. Expose and control surfaces

Expose is the backend boundary through which a surface or protocol is served.

Backend semantics must remain independent of the chosen control surface.

MetaModulesCW defines WebEngine as the canonical MetaModules UI. Other control surfaces may consume the same canonical backend capabilities, but they do not replace WebEngine's role inside the MetaModules framework specification.

Other surfaces may include:

- WebMini-hosted local applications
- Unity-based control surfaces
- native applications
- other future control surfaces

Replacing the surface must not redefine backend semantics or canonical business truth.

### WebMini

WebMini is a **raw static HTTP server**.

Its defining property is the minimal server-side web layer, not a small client application.

A WebMini-served application may be very large.

Structure is a canonical example of the intended pattern:

```text
WebMini
  ↓ serves static HTML/JS/assets
Structure
  ↓
REST / WebSocket / other Exposes
  ↓
CS / backend
```

A WebMini client may use:

- large JavaScript applications,
- S3D,
- realtime WebSocket data,
- graph editing,
- local state,
- undo/redo,
- complex visualization.

`Mini` refers to the web server / backend footprint.

WebMini is local-first. The raw HTTP connection is intended for the local trusted environment.

The surface is not moved across an untrusted network. When the working context moves, a new local surface is materialized there and DWH resolves the required data.

### WebEngine

WebEngine is the canonical MetaModules UI. It is the AC-aware dynamic UI layer that materializes Composition, SiteTree and Projection structure into the user-facing MetaModules web surface.

Its fundamental path is:

```text
request
→ identity / context
→ Command Surface / AccessCore
→ allowed capabilities and data
→ Composition / Projection / SiteTree
→ render output
```

Two users may request the same logical page and receive different outputs because AccessCore permits different data, capabilities or projections.

A core WebEngine design principle is:

> **The surface should feel lightweight even when the system behind it is large.**

System complexity must not automatically become interface complexity.

### Shared presentation capabilities

WebMini and WebEngine may both use shared presentation technologies such as:

- WebGUI
- S3D
- Style

These are presentation capabilities. They are not canonical business truth and they are not the same thing as WebMini or WebEngine.

---

## 10. Studio

Studio is not a general business semantic editor.

Studio is primarily the WYSIWYG editor for WebEngine Composition presentation.

Studio edits:

- WebEngine SiteTree,
- pages,
- which Projections appear on a page,
- Projection placement,
- page layout,
- Composition configuration exposed for editing,
- domain Composition arrangement.

Studio does not redefine the canonical semantics of Business Universals.

All domain modules are, in practice, Compositions that can be edited through Studio where the Composition exposes those editable surfaces.

Example:

```text
Business Universals
        ↓
     Composition
        ↓
        CRM
        ↓
      Studio
  ├─ SiteTree
  ├─ pages
  ├─ projections
  └─ composition configuration
        ↓
    WebEngine
```

---

## 11. Domain modules are Composition MetaModules

The first domain examples must demonstrate reuse, not create parallel domain truth.

### ERP

ERP is not required to own its own business model.

It is essentially a Composition definition:

> Take these existing capabilities and show/use them this way.

A typical ERP Composition may select from:

- Identity
- Project
- CatalogItem
- Order
- Invoice
- Account
- JournalEntry
- LedgerEntry
- StockMovement
- Shipment
- Contract
- Measurement
- etc.

The difficult reusable semantics already exist in the Universal layer.

ERP adds arrangement, workflow, projections, SiteTree, defaults and domain-specific rules.

### CRM

Example composition:

```text
Identity
+ Opportunity
+ Quote
+ Order
+ Contract
+ Text
+ domain relations
+ projections
```

### WMS

Example composition:

```text
CatalogItem
+ Location
+ StockMovement
+ Lot
+ Reservation
+ Shipment
+ HandlingUnit
+ domain relations
+ projections
```

### Other initial Business Domain compositions

- HRM
- Projects
- Service
- Finance

The goal is breadth and structural proof, not production-grade domain nuance in every example.

---

## 12. Strategy

Strategy uses the same Composition / Projection model.

Strategy does not need a separate duplicate business data model.

Example Strategy methods:

- SWOT
- PESTEL
- OKR
- Balanced Scorecard
- Business Model Canvas
- Porter Five Forces
- Scenario Planning
- Decision Matrix
- Risk Matrix
- Roadmap

Example Strategy capabilities:

- Board
- Portfolio
- Decision
- Due Diligence / M&A
- Governance / GRC
- Vendor
- Tender / RFP
- Benefits
- War Room
- Investor / Management Reporting
- Management System

C-suite views are **custom Projections**, not canonical Strategy modules.

For example:

```text
CEO view
CFO view
COO view
CTO/CIO view
CHRO view
CSO view
...```

A small company may still demonstrate all of these projections because the purpose is to show role-oriented views over the same truth, not to claim that the company literally has a large executive organization.

---

## 13. Everyday

Everyday is also a Composition family over the same reusable primitives.

Current example profiles include:

- Shopping
- Pantry
- Meals
- Tasks
- Habits
- Budget
- Subscriptions
- Warranty
- Inventory
- Packing
- Travel
- Events
- Family
- Medication
- Workout
- Reading
- Watchlist
- Wishlist
- Gifts
- Maintenance
- Logbook

These remain compositions/projections, not new canonical primitive families unless a genuinely reusable missing primitive is discovered.

---

## 14. MMdemo Industries Oy

MMdemo exists to demonstrate that the same canonical truth can support many business and role views without duplicating data.

The fictitious example company:

**MMDemo Industries Oy**

is a small Finnish B2B company with roughly a few dozen employees.

It:

- sells components,
- assembles solutions,
- installs at customer sites,
- services and maintains them.

This naturally exercises:

- CRM,
- Sales,
- Procurement,
- WMS / inventory,
- Projects,
- Field Service,
- Billing / Accounting,
- HR / payroll,
- Strategy.

MMdemo may expose more organizational projections than a company of its size would normally formalize. That is intentional: the demo proves that custom role projections are cheap because they are views, not duplicate systems.

### Main example flow

```text
Opportunity
→ Quote
→ Sales Order
→ Customer Delivery Project
→ Shipment
→ Invoice
→ Payment
→ Accounting
→ Strategy / War Room
```

Supporting flows include:

```text
Purchase Order
→ Receipt
→ Inventory
→ Supplier Invoice
```

and:

```text
Customer Case
→ Service Project
→ return / resolution
```

---

## 15. MMdemo master pipeline visualization

The complete MMdemo business pipeline must be modeled so it can be rendered as an interactive master diagram.

The diagram is not merely decoration. It is a navigation and explanation surface.

The user should be able to select a part of the process and immediately see:

- which Business Universals participate,
- which Composition MetaModules use them,
- which Strategy tools relate to that stage,
- which Projections are available,
- which role views include that stage,
- which commands / capabilities manage it.

The same graph also enables animated explanations of data flow.

Example animation:

```text
Opportunity
→ Quote
→ Order
→ Project
→ Shipment
→ Invoice
→ Payment
→ Ledger
→ Reporting
→ War Room
```

Another animation can show the same canonical data through multiple views:

```text
StockMovement
├─ WMS projection
├─ ERP projection
├─ operational dashboard
└─ Strategy / War Room projection
```

This visualization should make the core principle visible:

> **One truth. Many topologies. No duplicate truth.**

---

## 16. Structural derivation is the goal

Once the semantic structure is correct, the rest should follow from it.

```text
Business Universals
+ Platform Universals
+ Relations
+ Contracts
+ DWH
+ Command Surface
+ AccessCore
+ Composition rules
+ Projection rules
        ↓
Domain modules
        ↓
Studio
        ↓
SiteTree + projections
        ↓
WebEngine (MetaModules UI)
        ↓
REST / WebSocket / MCP and other Expose mappings where required
        ↓
REST / WebSocket / MCP
```

The objective is not to generate arbitrary software from prose.

The objective is to make repeated definitions unnecessary because the semantic structure is already explicit.

---

## 17. Hard invariants

The implementation and CW model should be reviewed against these invariants.

### No duplicate truth

```text
NO_DUPLICATE_SEMANTICS
NO_DUPLICATE_DATA
NO_DUPLICATE_RELATIONS
NO_DUPLICATE_PROJECTIONS
NO_DUPLICATE_UI_STRUCTURE
```

If an existing canonical structure can be referenced, composed or projected, do that instead of copying it.

### Composition is replaceable

```text
bad Composition != broken business substrate
```

Business continuity belongs to the Universal layer.

### UI is not functionality authority

```text
NO_UI_ONLY_ACTIONS
NO_AC_BYPASS
```

All functionality goes through Command Surface and AccessCore.

### Surface is replaceable

```text
backend semantics stay
data crosses boundaries
surface materializes locally
```

### Projection is not truth

A Projection is derived from canonical data and must not become an independent authoritative copy.

### Domain nuance belongs in Composition

A Universal remains minimal and reusable. Domain-specific additions must not contaminate the Universal base unless they are genuinely universal.

---

## 18. Repository implementation target

The first complete MetaModulesCW milestone should contain:

```text
CW Core dependency / pinned specification provenance
        ↓
MetaModules NodeTypes
        ↓
MetaModules Rulesets
        ↓
MetaModules specification set
        ↓
Universal Platform registry
        ↓
Business Universal registry (32)
        ↓
Business Universal ABS / FILE / DOC / CTRCT semantics
        ↓
Composition semantics
        ↓
Business Domain examples
        ↓
Strategy examples
        ↓
Everyday examples
        ↓
Studio / SiteTree / Projection relationships
        ↓
DWH contract closure
        ↓
CW specification lint
        ↓
CW model validation
```

The repository must remain valid against the selected immutable CW specification closure.

---

## 19. Review test

When reviewing any addition, ask:

1. Is this meaning already represented by an existing Universal?
2. Can this be a relation instead of a new Entity?
3. Can this be a Composition instead of a new Universal?
4. Can this be a Projection instead of duplicated data?
5. Can this be referenced instead of copied?
6. Does this action go through Command Surface?
7. Does AccessCore remain the authorization authority?
8. Is DWH handling data location rather than the UI?
9. Is the control surface replaceable?
10. Would business operations still work if this Composition were deleted?

If the answer to the last question is **no**, Composition has probably taken ownership of something that belongs lower in the stack.

---

## Core statement

> **Create the playground and its rules. Let applications be compositions of the structure.**

Or operationally:

> **Build the structure correctly once. Remove all unnecessary repetition. Derive the rest from structure.**
