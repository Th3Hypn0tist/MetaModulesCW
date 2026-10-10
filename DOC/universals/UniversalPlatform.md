# Universal Platform

Universal Platform contains reusable platform-level capabilities that MetaModule Compositions can depend on.

Current platform family includes:

- IAM
- AccessCore
- DWH
- EXTPeer
- NetworkService
- LibraryMount
- SymbolNamespace

The exact registry is authoritative; file presence alone does not imply membership.

## Direction of dependency

Platform capabilities may be consumed by Business Universals and Compositions.

Platform capabilities do not become business-domain truth simply because business modules use them.

## Web boundary

WebMini and WebEngine are not classified here as Platform Universals in the current model.

They are Expose/control-surface mechanisms with distinct behavior.

Old nanoCMS terminology is not carried forward as a current Platform Universal. Its old role has been superseded by the WebMini/WebEngine distinction.
