# Stylus & Tablet Plugin Overview

## 1. What this plugin does
- Adds advanced stylus/tablet input support (pressure, tilt, buttons) for editor use.
- Provides platform-specific backends for Windows (Wintab, RealTimeStylus) and Mac.
- Includes a debug paint widget to visualize stylus data.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor stylus integration with backend selection and debug widgets that tooling teams use to read pressure/tilt/button data from tablets.

## 3. Key Modules
- **StylusInput** (Editor)  
  - Role: Core stylus interfaces, packet structures, tablet context management, and utilities.  
  - Notable types: `FStylusInputInterface`, `FStylusInputPacket`, `FStylusInputTabletContext`, `FStylusInputUtils`.
- **StylusInputDebugWidget** (EditorNoCommandlet)  
  - Role: Debug widgets for visualizing stylus input in the editor.  
  - Notable types: `SStylusInputDebugWidget`, `SStylusInputDebugPaintWidget`.
- **StylusInputMac** (EditorNoCommandlet, Mac)  
  - Role: Mac-specific tablet context and event handling.  
  - Notable types: `FMacTabletContext`, `FMacInterface`, `FNSEventHandler`.
- **StylusInputRealTimeStylus** (EditorNoCommandlet, Win64)  
  - Role: Windows RealTimeStylus backend and COM plugin wrappers.  
  - Notable types: `FRealTimeStylusInstance`, `FRealTimeStylusTabletContext`, `FRealTimeStylusPluginBase/Async/Sync`.
- **StylusInputWintab** (EditorNoCommandlet, Win64)  
  - Role: Wintab backend for Win64 tablets.  
  - Notable types: `FWintabInstance`, `FWintabTabletContext`, `FWintabStylus`, `FWintabMessageHandler`.

## 4. Important Types & APIs
### `FStylusInputInterface` and `FStylusInputPacket`
- Role: Abstraction and data structure for stylus input (position, pressure, tilt, buttons).
- Key functions: converting platform packets to engine-friendly data, handling tablet context creation/destruction.

### Platform backends
- Role: Each backend translates OS-level stylus events into `FStylusInputPacket` streams and manages device contexts (`FRealTimeStylusTabletContext`, `FWintabTabletContext`, `FMacTabletContext`).

### Debug widgets
- Role: Slate widgets (`SStylusInputDebugWidget`, `SStylusInputDebugPaintWidget`) to visualize strokes, pressure, and tablet state.

## 5. Typical usage patterns
- Enable the plugin (disabled by default). On Win64 choose between Wintab and RealTimeStylus backends; on Mac the Mac backend loads automatically.
- Consume stylus events via the `IStylusInputModule` interfaces in editor tools, or use the debug widget tab to verify pressure/tilt data.
- Configure backend selection and options through module settings (where exposed) or backend-specific code paths.

## 6. Version-specific notes (UE 5.7)
- Marked beta and editor-only; no explicit UE 5.7-specific notes found in the current source.

