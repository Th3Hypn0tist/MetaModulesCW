# AccessCore

AccessCore (AC) is the authorization authority for capabilities and visible data in the active context.

CS provides the functional surface. AC determines which parts of that surface are available to the current identity and context.

## Visibility and execution

The same authorization model affects both:

- what may be shown,
- what may be executed.

Example:

```text
Order capability set
        ↓
        CS
        ↓
        AC
     ↙      ↘
  allowed  denied
     ↓
visible / executable surface
```

A control surface therefore does not independently decide what the user is allowed to do.

## Shared authorization point

The goal is that WebEngine, Studio, Q, REST and other surfaces do not each create independent authorization semantics.

They operate through the same CS + AC path.

This keeps authorization aligned with canonical capabilities rather than UI implementation.
