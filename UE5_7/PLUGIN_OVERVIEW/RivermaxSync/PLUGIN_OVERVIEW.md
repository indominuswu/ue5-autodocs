# NVIDIA Rivermax Media synchronization for nDisplay Plugin Overview

## 1. What this plugin does

- Adds a Rivermax-backed display cluster media output synchronization policy that aligns capture with Precision Time Protocol (PTP) for nDisplay clusters.
- Provides logic to detect and report PTP drift between nodes during synchronized capture.
- Supplies an editor factory to expose the Rivermax synchronization policy as an asset choice in media output settings.

## 2. Editor/Runtime surfaces

- User-facing: Yes - nDisplay users select the Rivermax PTP sync policy asset (`UMediaOutputSynchronizationPolicyRivermax`) to align media capture across nodes and monitor PTP drift events.

## 3. Key Modules

- **RivermaxSync** (Runtime)  
  - Role: Implements the Rivermax-specific media output synchronization policy and PTP barrier handling for DisplayCluster capture.
- **RivermaxSyncEditor** (Editor)  
  - Role: Registers the Rivermax synchronization policy asset/factory for use in the editor UI.

## 4. Important Types & APIs

### `UMediaOutputSynchronizationPolicyRivermax`

- Role: DisplayCluster media output synchronization policy that aligns Rivermax capture using PTP-aware barrier data.
- Key properties: `MarginMs` (tunable synchronization window).
- Key functions: Overrides `GetHandler()` to supply the Rivermax-specific handler.

### `FMediaOutputSynchronizationPolicyRivermaxHandler`

- Role: Runtime handler that joins the DisplayCluster barrier, measures per-node frame boundaries, and applies Rivermax-aligned sync decisions.
- Key behaviors: Overrides barrier initialization, `Synchronize()`, and capture-type validation to gate supported media capture types.

### `FRivermaxClusterPtpUnsyncEvent`

- Role: Stage Monitor event struct that reports PTP deltas per node when a desync is detected.
- Key fields: `NodePtpFrameDeltas`, `PtpBaseNodeId`.

### `UMediaOutputSynchronizationPolicyRivermaxFactory`

- Role: Editor factory for creating Rivermax synchronization policy assets.

## 5. Typical usage patterns

- Enable the plugin, then select the Rivermax (PTP) synchronization policy on DisplayCluster media outputs when using NVIDIA Rivermax hardware.
- Configure the `MarginMs` setting on the policy asset to control the allowed timing window around the sync point.
- In clustered sessions, monitor Stage Monitor events (`FRivermaxClusterPtpUnsyncEvent`) for PTP drift diagnostics.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

