# LiveLinkFreeD Plugin Overview

## 1. What this plugin does
- Adds LiveLink source support for the FreeD protocol commonly used in virtual production tracking.
- Provides UI and settings to configure FreeD connections and source behavior.

## 2. Key Modules
- **LiveLinkFreeD** (Runtime)  
  - Role: Implements the FreeD LiveLink source.
  - Notable types: `ULiveLinkFreeDSourceFactory`, `ULiveLinkFreeDSourceSettings`, `ULiveLinkFreeDConnectionSettings`, `SLiveLinkFreeDSourceFactory`.

## 3. Important Types & APIs

### Source setup
- `ULiveLinkFreeDSourceFactory`: LiveLink source factory with UI panel (`SLiveLinkFreeDSourceFactory`) to configure connections.
- `ULiveLinkFreeDConnectionSettings`: Stores connection details for the FreeD stream.
- `ULiveLinkFreeDSourceSettings`: Per-source settings for LiveLink subjects produced by the FreeD source.

## 4. Typical usage patterns
- LiveLink panel: Add a new source and choose FreeD; configure IP/port and source settings via the provided UI panel.
- Runtime: With the source active, LiveLink subjects stream FreeD tracking data for cameras or tracked objects and can be consumed by controllers/components.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is disabled by default and intended for virtual production tracking.

