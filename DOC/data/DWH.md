# DWH substrate

DWH is the canonical data substrate used by MetaModules.

Its architectural purpose is to resolve canonical data independently of where the data physically resides.

The key operating idea is:

> Data moves. Surface materializes locally.

## Resolution model

```text
surface / composition
       ↓
      DWH
   ↙       ↘
local     remote
 data      data
   ↘       ↙
 resolved canonical view
```

A surface does not need to become the transport mechanism for the whole UI.

Instead, the surface is opened locally and the required canonical data is resolved through DWH-compatible contracts.

## Contract-level concerns

DWH-related MetaModule semantics may describe:

- data ownership,
- readable members,
- writable members,
- field projection,
- local/remote resolution,
- relation access,
- file/data payload,
- authorization intersection,
- external peer boundaries.

They do not need to prescribe:

- SQL engine,
- ORM,
- storage vendor,
- programming language,
- serialization implementation.

## Surface independence

The same canonical data may be used by:

- WebMini applications,
- WebEngine pages,
- native applications,
- Unity surfaces,
- Q tools,
- other future control surfaces.

The data model remains canonical while the local surface changes.
