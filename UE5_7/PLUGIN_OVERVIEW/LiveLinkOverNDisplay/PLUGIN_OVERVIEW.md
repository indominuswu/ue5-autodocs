# Live Link Over nDisplay Plugin Overview

## 1. What this plugin does
- Synchronizes LiveLink subjects across nDisplay clusters.
- Provides configuration to enable/disable LiveLink-over-nDisplay handling from project settings or command line.

## 2. Editor/Runtime surfaces

- User-facing: Yes - nDisplay users enable `ULiveLinkOverNDisplaySettings` (or command-line switch) to sync LiveLink subjects across cluster nodes.

## 3. Key Modules
- **LiveLinkOverNDisplay** (Runtime)  
  - Role: Manages LiveLink subject synchronization for nDisplay deployments and exposes settings.
  - Notable types: `ULiveLinkOverNDisplaySettings`.

## 4. Important Types & APIs

### `ULiveLinkOverNDisplaySettings`
- Role: Engine config object that controls whether LiveLink-over-nDisplay is active.
- Key properties: `bIsEnabled` (configurable), command-line override (`-EnableLiveLinkOverNDisplay=false/true`), helper `IsLiveLinkOverNDisplayEnabled` combining config and command line.

### Supporting classes
- Internal agent/connection classes (`NDisplayLiveLinkProxy`, `NDisplayAgentViz`) handle synchronization inside the module.

## 5. Typical usage patterns
- Project setup: Enable the plugin and set `bIsEnabled` in project settings; optionally override via command line when launching nDisplay nodes.
- Runtime: With the feature enabled, LiveLink subjects are shared/synchronized across the nDisplay cluster without additional user code.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is disabled by default and intended for nDisplay-based productions.

