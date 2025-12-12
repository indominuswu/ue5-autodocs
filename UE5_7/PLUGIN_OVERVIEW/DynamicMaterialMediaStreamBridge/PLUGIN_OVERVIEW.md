# Material Designer Media Stream Bridge Plugin Overview

## 1. What this plugin does
- Bridges the Media Stream plugin into Material Designer so live media streams can be used as dynamic material inputs.
- Adds dynamic and static material value nodes that reference media streams.
- Provides editor integration to expose media stream sources inside the Material Designer UI.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Material Designer users add media stream value nodes (including dynamic variants) and pick streams in the editor UI to feed live media into materials.

## 3. Key Modules
- **DynamicMaterialMediaStreamBridge** (Runtime)  
  - Role: Runtime material value nodes for media streams.
- **DynamicMaterialMediaStreamBridgeEditor** (Editor)  
  - Role: Editor menus/property rows that let users pick media streams when authoring materials.

## 4. Important Types & APIs

### `UDMMaterialValueMediaStream` / `UDMMaterialValueMediaStreamDynamic`
- Role: Material value nodes that wrap a media stream and feed it into dynamic material graphs.
- Behavior: Dynamic variant supports runtime-updatable bindings.

### Editor helpers
- `FDMMaterialValueMediaStreamPropertyRowGenerator`, `FDMMediaStreamStageSourceMenuExtender`: Extend Material Designer UI with stream pickers and stage source menus.

## 5. Typical usage patterns
- Enable both Material Designer and Media Stream plugins, plus this bridge.
- In the Material Designer editor, add a media stream value node to a material graph to sample a stream as a texture input.
- Use the dynamic value to swap or drive streams at runtime via Blueprint/C++.

## 6. Version-specific notes (UE 5.7)
- Marked experimental; no explicit UE 5.7-only changes noted.

