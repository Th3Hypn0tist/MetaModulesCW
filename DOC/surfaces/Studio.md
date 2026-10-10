# Studio

Studio is the editing surface for Composition-oriented presentation and arrangement.

Its primary role is WYSIWYG editing of WebEngine SiteTree and page composition, while also allowing editable Composition configuration where that Composition exposes it.

## Studio edits

- SiteTree,
- pages,
- Projection selection,
- Projection placement,
- layout,
- Composition configuration,
- domain Composition arrangement.

## Studio does not own Universal semantics

Studio edits how canonical capabilities are assembled and presented.

It does not redefine what Order, Project, Identity or another Universal means.

## Composition relation

All domain modules can be treated as Compositions that Studio can edit at the appropriate level.

Conceptually:

```text
Universals
   ↓
Composition
   ↓
Studio
├─ SiteTree
├─ pages
├─ projections
└─ editable composition configuration
   ↓
WebEngine
```

Studio actions themselves use the same canonical functional path through CS and AC.


## Relation to SiteEngine

Studio edits Composition structure and presentation configuration.

SiteEngine is responsible for running/materializing the resulting Composition. Studio is therefore an editor of runtime input, not the runtime host itself.

```text
Studio
  ↓ edits
Composition
  ↓ mount/materialize
SiteEngine
  ↓
active runtime structure
```
