# GooglePAD Plugin Overview

## 1. What this plugin does
- Provides Google Play Asset Delivery (PAD) support for Android packaging.
- Exposes Blueprint nodes to request, monitor, and remove on-demand asset packs.
- Adds runtime settings to gate usage to distribution/shipping builds.
- Editor module wires settings into Project/Packaging configuration.

## 2. Key Modules
- **GooglePAD** (Runtime)  
  - Role: Implements PAD JNI integration and Blueprint-accessible asset pack management (downloads, status queries, storage paths).
  - Notable types: `UGooglePADFunctionLibrary`.
- **GooglePADEditor** (Editor)  
  - Role: Registers runtime settings for enabling PAD and build gating.
  - Notable types: `UGooglePADRuntimeSettings`.

## 3. Important Types & APIs

### `UGooglePADFunctionLibrary`
- Role: Blueprint node set for issuing PAD requests and querying download state.
- Key functions: `RequestInfo`, `RequestDownload`, `CancelDownload`, `GetDownloadState`, `GetDownloadStatus`, `GetBytesDownloaded`, `GetTotalBytesToDownload`, `RequestRemoval`, `ShowCellularDataConfirmation`, `GetAssetPackLocation`, `GetAssetsPath`.

### `UGooglePADRuntimeSettings`
- Role: Engine config object gating PAD usage (`bEnablePlugin`, `bOnlyDistribution`, `bOnlyShipping`).
- Location: Project Settings → Packaging when the editor module is loaded.

## 4. Typical usage patterns
- Android-only: enable the plugin (on by default) and configure `GooglePAD Runtime Settings` to restrict to shipping/distribution if desired.
- Add Blueprint PAD nodes to request asset pack downloads at runtime and poll status/progress before mounting content.
- Use `GetAssetPackLocation` / `GetAssetsPath` after completion to access delivered files.
- Remember to release PAD handles (`ReleaseDownloadState`, `ReleaseAssetPackLocation`) when finished.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
