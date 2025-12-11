# EOS Shared Plugin Overview

## 1. What this plugin does
- Initializes and shuts down the Epic Online Services (EOS) SDK runtime for other EOS plugins.
- Centralizes EOS SDK lifecycle management so subsystems can safely use the SDK.
- Disabled by default; enable when using EOS-based online services.

## 2. Key Modules
- **EOSShared** (Runtime)  
  - Role: Boots and tears down the EOS SDK; exposes shared utilities for other EOS plugins.

## 3. Important Types & APIs

### `UI_OnDisplaySettings`
- Role: Utility/helper tied to EOS display configuration; used internally.
- Public Blueprint surface is minimal; other EOS plugins consume the shared initialization.

## 4. Typical usage patterns
- Enable `EOSShared` along with other EOS plugins (overlay, voice chat, online subsystem EOS).
- The module handles EOS SDK startup/shutdown automatically during engine module load/unload.
- No direct gameplay code changes required unless customizing EOS init parameters.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific changes noted; behavior mirrors current source.
