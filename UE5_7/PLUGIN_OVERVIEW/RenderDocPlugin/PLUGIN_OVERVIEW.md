# RenderDoc Plugin Overview

## 1. What this plugin does
- Integrates the RenderDoc graphics debugger into the Unreal Editor for frame capture and inspection.
- Provides menu/toolbar commands to launch captures, set capture options, and open RenderDoc sessions.
- Manages RenderDoc binaries loading/unloading and notifies users of capture status.

## 2. Key Modules
- **RenderDocPlugin** (DeveloperTool)  
  - Role: Core integration, UI commands, settings, and loader for RenderDoc.  
  - Notable types: `FRenderDocPluginModule`, `URenderDocPluginSettings`, `FRenderDocPluginCommands`, `FRenderDocPluginLoader`, UI widgets (`SRenderDocPluginEditorExtension`, `SRenderDocPluginHelpWindow`).

## 3. Important Types & APIs
### `URenderDocPluginSettings`
- Role: Configurable settings for RenderDoc integration (path to RenderDoc, capture options).
- Key properties: RenderDoc executable path, overlay settings, capture hotkeys.

### `FRenderDocPluginModule`
- Role: Registers editor commands, menu extensions, and handles capture requests.
- Key functions: start/stop capture, open existing capture in RenderDoc, manage loader lifecycle.

## 4. Typical usage patterns
- Enable the plugin (on by default for Win64/Linux), configure RenderDoc install path in project/editor settings if not autodetected.
- Use the RenderDoc toolbar/menu commands to capture a frame from the editor viewport or PIE session, then inspect it in RenderDoc.
- Optionally adjust capture options in `URenderDocPluginSettings` for overlays, capture triggers, or multi-frame captures.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific changes are called out; integration targets Win64 and Linux per the descriptor.
