# Command Surface

Command Surface (CS) is the common functional surface of the system.

The central principle is:

> If it can be done, it can be commanded.

All executable capabilities are exposed through the same command-addressable model rather than being owned privately by one UI.

## Functional convergence

A single canonical capability can be used by:

- direct CS command,
- WebEngine action,
- WebMini application,
- Studio action,
- REST adapter,
- WebSocket adapter,
- MCP adapter,

These are different surfaces over the same capability.

## Why this matters

Without a common Command Surface, each UI or protocol tends to reimplement business behavior.

With CS, the architecture can derive interfaces from structure instead of maintaining parallel APIs.

Conceptually:

```text
canonical capability
       ↓
      CS
       ↓
authorized execution path
```

The normative requirements for CS are intentionally deferred to the CTRCT pass.
