# OpenXRMsftHandInteraction Plugin Overview

## 1. What this plugin does

- Implements the `XR_MSFT_hand_interaction` OpenXR extension, allowing tracked hands to behave like motion controllers.
- Provides OpenXR action bindings and profile support specific to Microsoft’s hand interaction profile.

## 2. Key Modules

- **OpenXRMsftHandInteraction** (Runtime)  
  - Role: Registers the MSFT hand interaction profile, binds actions, and exposes hand-derived controller poses to the engine.

## 3. Important Types & APIs

- `FOpenXRMsftHandInteraction` (`OpenXRMsftHandInteraction.h`)  
  - Runtime extension handler configuring OpenXR interaction profiles and translating hand states to controller-like inputs.

## 4. Typical usage patterns

- Enable alongside the core OpenXR plugin when targeting runtimes that support `XR_MSFT_hand_interaction`.
- Use standard motion-controller input paths; this extension maps hand tracking into controller actions so existing input bindings work.
- No dedicated editor UI; configuration is through OpenXR project settings and controller mappings.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview reflects the Microsoft hand interaction support present in the UE 5.7 source tree.
