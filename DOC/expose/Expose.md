# Expose

Expose defines how canonical capabilities, data and projections are made available across a boundary.

Expose is a semantic publication mechanism, not one specific protocol.

Conceptually:

```text
canonical capability / data / projection
                   ↓
                Expose
          ↙        ↓        ↘
       REST    WebSocket    MCP
          ↘        ↓        ↙
             target surface
```

The backend semantic contract remains stable even when the target transport or control surface changes.

## Publication boundary

Expose determines what is available outward and in what semantic shape.

New internal data does not automatically become externally visible.

## Surface replacement

A control surface can be replaced without redefining the underlying Expose semantics.

For example, the same backend capability may be consumed by:

- WebEngine,
- WebMini application,
- native UI,
- Unity UI,
- Q through its Tool Layer.
