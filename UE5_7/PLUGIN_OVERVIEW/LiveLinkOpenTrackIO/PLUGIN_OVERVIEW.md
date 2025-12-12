# LiveLinkOpenTrackIO Plugin Overview

## 1. What this plugin does
- Adds LiveLink source support for OpenTrackIO devices/streams (including Live Link Hub).
- Offers configuration for multicast/unicast endpoints and optional transform subjects.

## 2. Editor/Runtime surfaces

- User-facing: Yes - LiveLink source factory/UI lets users configure OpenTrackIO endpoints and publish camera/transform subjects into LiveLink.

## 3. Key Modules
- **LiveLinkOpenTrackIO** (Runtime)  
  - Role: Implements the OpenTrackIO LiveLink source and source settings.
  - Notable types: `ULiveLinkOpenTrackIOSourceFactory`, `ULiveLinkOpenTrackIOSourceSettings`, `ULiveLinkOpenTrackIOConnectionSettings`, `SLiveLinkOpenTrackIOSourceFactory`.

## 4. Important Types & APIs

### Source and settings
- `ULiveLinkOpenTrackIOSourceFactory`: Builds creation panels and creates sources from connection strings; UI backed by `SLiveLinkOpenTrackIOSourceFactory`.
- `ULiveLinkOpenTrackIOSourceSettings`: Stores protocol (`Multicast`/`Unicast`), `MulticastEndpoint`, `UnicastEndpoint`, and `SubjectsPerTransform` options to emit per-transform subjects and optionally apply transforms back to camera data.
- `ULiveLinkOpenTrackIOConnectionSettings`: Captures network connection parameters for the source.

## 5. Typical usage patterns
- LiveLink panel: Add a new OpenTrackIO source, choose multicast/unicast endpoints, and decide whether to generate subjects per transform.
- Runtime/editor: Consume the produced LiveLink subjects (camera plus optional transform subjects) to drive tracking inside UE or Live Link Hub.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is experimental and disabled by default.

