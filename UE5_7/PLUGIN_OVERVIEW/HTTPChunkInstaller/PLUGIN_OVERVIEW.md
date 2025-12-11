# HTTP Chunk Installer Plugin Overview

## 1. What this plugin does
- Implements a streaming install client that downloads and installs chunks over HTTP.
- Integrates with the engine’s chunk install abstraction to report progress and manage priorities.
- Provides helper interfaces for cloud title files and installer state management.

## 2. Key Modules
- **HTTPChunkInstaller** (Runtime)  
  - Role: Supplies `FHTTPChunkInstall`, cloud title file utilities, and tick-based management of HTTP chunk download/installation.

## 3. Important Types & APIs

### `FHTTPChunkInstall`
- Role: `FGenericPlatformChunkInstall` implementation using HTTP plus `FTSTickerObjectBase` for ticking.
- Key functions: `GetChunkProgress`, `SetInstallSpeed`, `PrioritizeChunk`, `DebugStartNextChunk`, `EndInstall`, and internal helpers for manifest parsing and cache management.

### Supporting types
- `FChunkInstall`, `FChunkSetup`, `FCloudTitleFileInterface`: Helper interfaces for manifest reading, local caching, and cloud storage interaction.

## 4. Typical usage patterns
- Enable the plugin for titles that download game content chunks at runtime; the platform chunk installer will route through `FHTTPChunkInstall`.
- Configure chunk manifests and cloud storage; monitor progress via the chunk install APIs (percentage complete, speed).
- Use `SetInstallSpeed`/`PrioritizeChunk` to manage foreground vs. background installs.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
