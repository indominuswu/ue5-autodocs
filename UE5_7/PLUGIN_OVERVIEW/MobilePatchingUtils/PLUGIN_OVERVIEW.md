# Mobile Patching Utilities Plugin Overview

## 1. What this plugin does

- Exposes Blueprint utilities for downloading, installing, and mounting mobile content updates.
- Wraps build manifest handling and patch installer APIs for over-the-air content delivery.
- Enabled by default for mobile platform projects.

## 2. Key Modules

- **MobilePatchingUtils** (Runtime) — Blueprint libraries and content state objects that manage downloads, disk usage, and mounting.

## 3. Important Types & APIs

- `UMobilePatchingLibrary` — Blueprint callable functions to request remote content, start downloads, and query platform support.
- `UMobilePendingContent` — represents a download in progress; exposes progress stats (`GetDownloadSize`, `GetInstallProgress`, `GetDownloadSpeed`) and completion callbacks (`OnSucceeded`, `OnFailed` delegates).
- `UMobileInstalledContent` — handles already-downloaded content, disk usage queries, and `Mount` operations with configurable pak order and mount point.

## 4. Typical usage patterns

- Enable the plugin, then in Blueprint call `RequestContent`/`StartInstall` via `UMobilePatchingLibrary` to begin downloading an update manifest.
- Bind success/failure delegates to drive UI and mount installed content (`UMobilePendingContent::Mount` via inherited API) after download completes.
- Query disk space and download size to present progress bars and guard against insufficient storage on mobile devices.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes; APIs match the current runtime headers.
