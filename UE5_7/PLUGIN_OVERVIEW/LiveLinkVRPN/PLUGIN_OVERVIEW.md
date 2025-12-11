# LiveLinkVRPN Plugin Overview

## 1. What this plugin does

- Provides a Live Link source that consumes VRPN tracking devices (e.g., trackers/rigids) over the VRPN protocol.
- Streams positional data into Live Link for use in virtual production or tracking-driven workflows.
- Runtime-only plugin enabled on Win64.

## 2. Key Modules

- **LiveLinkVRPN** (Runtime)
  - Role: Implements the VRPN Live Link source and factory.
  - Notable types: `ULiveLinkVRPNSourceSettings`, `FLiveLinkVRPNSource`, `ULiveLinkVRPNSourceFactory`.

## 3. Important Types & APIs

### `ULiveLinkVRPNSourceSettings`

- Role: Minimal Live Link source settings class for VRPN sources (inherits `ULiveLinkSourceSettings`).

### `FLiveLinkVRPNSource`

- Role: Live Link source implementation that connects to a VRPN server, receives tracker updates, and publishes Live Link subjects.
- Key behaviors: Handles connection settings (server/device names) and mapping incoming transforms to Live Link frames.

## 4. Typical usage patterns

- Enable the plugin and add a new Live Link source of type VRPN in the Live Link panel.
- Provide the VRPN server/address and tracker name; the source publishes subject data that can be consumed by cameras, pawns, or Control Rig.
- Combine with Live Link role remapping/blueprints to drive actors with external trackers.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
