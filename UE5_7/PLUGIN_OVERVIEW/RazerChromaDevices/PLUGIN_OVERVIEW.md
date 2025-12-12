# Razer Chroma Devices Plugin Overview

## 1. What this plugin does
- Provides runtime control over Razer Chroma lighting effects for supported devices.
- Supplies developer settings, animation assets, and Blueprint/API access for triggering effects.
- Includes editor integration for creating Chroma animation assets and factories.
- Beta, disabled by default; client-only runtime with editor support.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developer-facing device integration with settings, Chroma animation assets, and Blueprint functions (`URazerChromaFunctionLibrary`) to drive Razer lighting.

## 3. Key Modules
- **RazerChromaDevices** (ClientOnlyNoCommandlet)
  - Role: Core device interface, dynamic SDK loading, input device support, developer settings, Blueprint function library.
  - Notable types: `RazerChromaDynamicAPI`, `RazerChromaInputDevice`, `RazerChromaDeveloperSettings`, `RazerChromaFunctionLibrary`, `RazerChromaAnimationAsset`.
- **RazerChromaEditor** (Editor)
  - Role: Asset factory/actions for Chroma animation assets.

## 4. Important Types & APIs
### `URazerChromaDeveloperSettings`
- Role: Project settings for SDK paths, device support toggles, and default behavior.

### `URazerChromaFunctionLibrary`
- Role: Blueprint-callable functions to play/stop Chroma animations, set device colors, and manage effects.

### `URazerChromaAnimationAsset`
- Role: Asset representing a Chroma lighting animation; editable in editor and playable at runtime.

### `FRazerChromaDynamicAPI`
- Role: Wraps dynamic loading/binding to the Razer Chroma SDK (`RzChromaSDK*` headers).

## 5. Typical usage patterns
- Enable the plugin and configure developer settings for SDK availability.
- Create Chroma Animation assets via the provided factory; edit them in the editor.
- At runtime (client), call `URazerChromaFunctionLibrary` to play animations or set device colors on connected Razer hardware.
- Use alongside input devices if needed via `RazerChromaInputDevice`.

## 6. Version-specific notes (UE 5.7)
- Marked beta in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

