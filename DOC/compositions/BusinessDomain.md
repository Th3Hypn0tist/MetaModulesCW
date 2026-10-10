# Business Domain compositions

Traditional business applications are modeled as Compositions over Business Universals rather than independent canonical data models.

Initial examples include:

- ERP
- CRM
- HRM
- WMS
- Projects
- Service
- Finance

## ERP

ERP can be expressed as a Composition of existing capabilities such as:

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

ERP adds arrangement, workflow context, projections, SiteTree and domain-specific rules.

## CRM

A CRM Composition may combine:

- Identity
- Opportunity
- Quote
- Order
- Contract
- Text
- relevant relations
- role projections.

## WMS

A WMS Composition may combine:

- CatalogItem
- Location
- StockMovement
- Lot
- Reservation
- Shipment
- HandlingUnit.

## Shared truth

The point of these examples is not exhaustive product design.

They demonstrate that multiple domains can operate over the same canonical primitives without creating separate copies of the same business truth.
