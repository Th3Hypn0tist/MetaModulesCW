# WebMini

WebMini is a local-first raw static HTTP server.

`Mini` describes the server-side responsibility, not the complexity of the served application.

A WebMini-served application can be extremely large and capable.

Structure is the canonical example of the intended class of application.

## Typical shape

```text
browser
  ↓ localhost/raw HTTP
WebMini
  ↓ serves static HTML/JS/assets
heavy local application
  ↓
REST / WebSocket / other Exposes
  ↓
CS / backend
```

The served application may contain:

- large client-side logic,
- graph editing,
- S3D,
- realtime visualization,
- undo/redo,
- extensive local state,
- complex interaction.

## Local-first boundary

WebMini is intended primarily for local tools.

The local raw HTTP leg is not treated as the remote transport boundary.

When work occurs in another environment, the architecture opens/materializes a suitable local surface there and moves/resolves the data instead of transporting the original UI across the network.

This is why DWH is central to the WebMini model.
