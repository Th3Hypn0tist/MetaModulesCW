# Derived interfaces

Protocol-facing interfaces should be derived from canonical capabilities rather than designed as independent business models.

REST is a primary example.

## REST over Command Surface

A REST endpoint is a protocol projection of an existing CS capability.

Conceptually:

```text
Business capability
      ↓
Command Surface
      ↓
AccessCore
      ↓
Expose
      ↓
REST mapping
```

The REST layer does not need a second independent definition of business meaning.

## Same principle for other interfaces

The same structure can support:

- WebSocket operations,
- MCP operations,
- Q tools,
- other adapters.

The adapter may transform transport syntax, framing or invocation style while preserving the canonical capability contract.

## Structural derivation

Once capability identity, inputs, outputs, context and effects are structurally explicit, many interface definitions can be generated or validated against that structure.
