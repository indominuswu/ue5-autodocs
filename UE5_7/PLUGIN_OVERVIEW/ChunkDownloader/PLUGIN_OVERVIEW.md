# Chunk Downloader Plugin Overview

## 1. What this plugin does

- Implements a streaming install client for downloading and mounting content chunks (paks) at runtime.
- Manages CDN build manifests, chunk status tracking, and background downloads.
- Provides delegates for chunk install progress and lifecycle.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Runtime API (`FChunkDownloader`, status/delegate hooks) is used directly in games to stream and mount downloadable paks.

## 3. Key Modules

- **ChunkDownloader** (Runtime)  
  - Role: Runtime chunk download/mount manager with platform-specific download implementations.
  - Notable types: `FChunkDownloader`, `FPakFileEntry`, `FPlatformChunkInstallMultiDelegate`, `EChunkStatus`.

## 4. Important Types & APIs

### `FChunkDownloader`
- Role: Singleton-style manager for chunk downloads and mounting.
- Key functions:  
  - `Initialize(PlatformName, TargetDownloadsInFlight)` / `Finalize()` to start/stop the manager.  
  - `LoadCachedBuild` and `UpdateBuild` to sync against deployment/build IDs and fetch manifests.  
  - Accessors for current `ContentBuildId` and `DeploymentName`.  
  - Status tracking via `EChunkStatus` (Mounted, Cached, Downloading, Partial, Remote, Unknown).

### `FPakFileEntry`
- Role: Describes a pak file within a chunk (file name, size, version/ID, chunk ID, relative URL).

### `FPlatformChunkInstallMultiDelegate`
- Role: Delegate for reporting chunk install state changes.

## 5. Typical usage patterns

- Enable the plugin and call `FChunkDownloader::GetOrCreate()` to obtain the manager.
- Initialize with platform name/desired parallel downloads, load cached builds, then call `UpdateBuild` with deployment/build IDs to pull manifests and begin downloads.
- Track chunk states via `EChunkStatus` and delegates; mount downloaded chunks when they reach Cached/Mounted states.
- Call `Finalize` during shutdown to cancel downloads and unmount as needed.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

