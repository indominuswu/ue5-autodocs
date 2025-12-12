# Audio Modulation Plugin Overview

## 1. What this plugin does

- Default implementation of audio modulation (control busses, mix controls, and patching) in the Unreal audio engine.
- Supplies Blueprint utility libraries and editor tools for authoring modulation assets and styles.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides editor asset tools and runtime Blueprint libraries to author and control audio modulation setups.

## 3. Key Modules

- **AudioModulation** (Runtime)  
  - Role: Runtime modulation engine, asset types, and audio routing logic.
- **AudioModulationEditor** (Editor)  
  - Role: Editor panels, asset factories, and visualization for modulation setups.

## 4. Important Types & APIs

### `UAudioModulationSettings` (UDeveloperSettings)

- Role: Project settings controlling default modulation behavior and asset classes.

### `UAudioModulationStatics` (UBlueprintFunctionLibrary)

- Role: Blueprint helpers to activate/deactivate control busses and mixes at runtime.
- Key functions: Functions to update mix values, enable/disable patches, and query modulation state.

### `UAudioModulationStyle` (UBlueprintFunctionLibrary)

- Role: Style helpers for UI/editor tooling around modulation visualization.

## 5. Typical usage patterns

- Enable the plugin; create modulation busses, mixes, and patches in the Content Browser.
- In Blueprints, use `AudioModulationStatics` nodes to push mix values, enable busses, or adjust patch parameters at runtime.
- Configure defaults via Project Settings → Audio → Modulation.
- Use the editor module to visualize modulation graphs and tune control curves.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
