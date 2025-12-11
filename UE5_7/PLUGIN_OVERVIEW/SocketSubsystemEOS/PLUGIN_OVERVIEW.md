# Socket Subsystem EOS Plugin Overview

## 1. What this plugin does
- Implements an EOS-based socket subsystem for peer-to-peer networking.
- Provides EOS-backed net driver and connection classes that integrate with UE networking.
- Intended for platforms listed in the allowlist (Win64, Mac, Android) and relies on EOS shared utilities.

## 2. Key Modules
- **SocketSubsystemEOS** (RuntimeNoCommandlet)
  - Role: Registers the EOS socket subsystem during PostConfigInit and supplies EOS-specific net driver/connection implementations.
  - Notable types: `UNetDriverEOS`, `UNetConnectionEOS`, `UNetDriverEOSBase` (deprecated).

## 3. Important Types & APIs
- `UNetDriverEOS`
  - Role: Net driver that routes socket operations through EOS P2P.
  - Notes: Replaces the deprecated `UNetDriverEOSBase`.
- `UNetConnectionEOS`
  - Role: Connection object used by the EOS net driver for remote/local endpoints.
- `UNetDriverEOSBase` (deprecated)
  - Role: Legacy base retained for migration; new projects should use `UNetDriverEOS`.

## 4. Typical usage patterns
- Enable the plugin alongside `OnlineSubsystemUtils` and `EOSShared`.
- Configure sessions/net drivers to use `UNetDriverEOS` for P2P transport when using EOS.
- Ensure target platforms match the allowlist (Win64/Mac/Android); servers are not explicitly denied but the module type excludes commandlets.

## 5. Version-specific notes (UE 5.7)
- `UNetDriverEOSBase` is marked deprecated in favor of `UNetDriverEOS`; no additional 5.7-specific changes noted.
