# Identity families

MetaModulesCW uses the CW identity families without collapsing their responsibilities.

## #ABS

`#ABS` describes what a semantic thing **is**.

It is the abstraction layer.

Examples:

```text
#ABS:BusinessUniversal:Order.cw
#ABS:BusinessUniversal:Project.cw
#ABS:MMDemo:Company.cw
```

Concrete modeled organizations such as MMDemo Industries Oy belong here, not in DOC.

## #FILE

`#FILE` describes practical implementation semantics: what happens in implementation.

It does not mean that the CW artifact is source code, nor that its identity is merely a physical filename.

Example:

```text
#FILE:BusinessUniversal:Order.cw
```

A PHP, Python, Rust or other implementation may materialize that semantics.

## #DOC

`#DOC` explains and specifies the model in descriptive form.

This directory is the first DOC pass for MetaModulesCW.

DOC exists so the model can be reviewed and corrected before normative contracts are extracted.

## #CTRCT

`#CTRCT` defines the normative operating model that conforming implementations, compositions and surfaces follow.

CTRCT is intentionally derived after the DOC model is stable.

## Identity preservation

Canonical identities retain their complete form, including `.cw` where it is part of the identity.

For example:

```text
#FILE:BusinessUniversal:Order.cw
```

is not silently normalized to:

```text
#FILE:BusinessUniversal:Order
```

The identity family is semantic, not decorative.
