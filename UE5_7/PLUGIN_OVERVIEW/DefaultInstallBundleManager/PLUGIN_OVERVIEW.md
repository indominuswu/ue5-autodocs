# Default Install Bundle Manager Plugin Overview

## 1. What this plugin does

- Provides the default engine implementation for downloading, patching, and mounting install bundles at runtime.
- Supplies platform-aware bundle sources (chunk install, bulk download) and utility helpers for install management.
- Intended as a reference/engine-level bundle manager that game-specific managers can override.

## 2. Key Modules

- **DefaultInstallBundleManager** (Runtime) – Bundle manager implementation with platform chunk support and helper utilities.

## 3. Important Types & APIs

- `FDefaultInstallBundleManager` – Core manager that orchestrates bundle downloads, patching, and mounting.
- `FInstallBundleSourcePlatformChunkInstall` / `FInstallBundleSourcePlatformBase` – Platform-specific providers for fetching bundles via platform chunk systems.
- `FInstallBundleSourceBulk` – Bulk download provider for non-chunked bundle delivery.
- `FInstallBundleManagerUtil` – Common helper functions shared across sources and the manager.

## 4. Typical usage patterns

- Enable the plugin to rely on the engine-supplied install bundle management; bundles can be fetched during runtime based on manifest data.
- Choose platform-specific sources (chunk install vs. bulk) depending on target platform capabilities.
- Integrate with game logic by querying the bundle manager for download progress, completion, and mounting status.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
