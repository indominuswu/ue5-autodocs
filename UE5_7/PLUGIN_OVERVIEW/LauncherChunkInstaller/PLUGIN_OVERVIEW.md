# Launcher Chunk Installer Plugin Overview

## 1. What this plugin does

- Provides a chunk installer implementation that hooks into the Epic Launcher-based installation flow.
- Resolves chunk locations and availability for platform installers on desktop platforms.
- Enabled by default for Win64, Linux, and Mac.

## 2. Key Modules

- **LauncherChunkInstaller** (Runtime, PostConfigInit, Win64/Linux/Mac) — Implements the platform chunk installer interface.

## 3. Important Types & APIs

### `FLauncherChunkInstaller` (FGenericPlatformChunkInstall)

- Role: Platform chunk installer implementation that overrides `GetChunkLocation` to report where chunks are installed/available through the launcher.
- Registered by the module at startup; used internally by the engine’s chunk download/install systems.

## 4. Typical usage patterns

- Leave the plugin enabled when distributing builds through the launcher; chunk installation queries route through `FLauncherChunkInstaller` automatically.
- No direct Blueprint or gameplay API is exposed; it operates as backend infrastructure.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes; behavior matches the current module implementation.

