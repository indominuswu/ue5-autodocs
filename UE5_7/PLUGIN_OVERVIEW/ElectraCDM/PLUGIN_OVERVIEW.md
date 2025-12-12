# Electra Player Content Decryption Module Plugin Overview

## 1. What this plugin does
- Provides Content Decryption Module (CDM) support for Electra media playback.
- Handles DRM-related decryption for protected streams used by the Electra player stack.
- Disabled by default; enable when integrating encrypted media pipelines.

## 2. Editor/Runtime surfaces

- User-facing: No - Backend DRM/CDM integration for Electra with no editor tools or Blueprint/runtime APIs beyond optional enablement.

## 3. Key Modules
- **ElectraCDM** (RuntimeNoCommandlet)  
  - Role: Implements CDM hooks and decryptors for Electra playback.

## 4. Important Types & APIs
- The module supplies internal CDM integration for Electra; no public subsystems/components are exposed directly to Blueprints.
- Integrates with Electra player runtime to negotiate licenses and decrypt media segments.

## 5. Typical usage patterns
- Enable alongside `ElectraPlayer` when playing protected streams; configure CDM/license handling per platform.
- Used programmatically by Electra; typically no direct user-facing API calls are needed beyond enabling the plugin and configuring playback options.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific changes noted; behavior reflects current Electra CDM implementation.

