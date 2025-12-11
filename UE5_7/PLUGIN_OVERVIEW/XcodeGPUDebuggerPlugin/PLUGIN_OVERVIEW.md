# Xcode GPU Debugger Plugin Overview

## 1. What this plugin does

- Integrates with Xcode’s GPU debugger on macOS, providing editor commands and styling hooks to launch GPU debugging.
- Supplies menu/toolbar commands and an editor extension to trigger GPU debugging flows from Unreal.
- Disabled by default; for macOS developer workflows.

## 2. Key Modules

- **XcodeGPUDebuggerPlugin** (DeveloperTool, PostConfigInit, Mac-only)  
  - Role: Registers GPU debugger commands, styles, and editor extension for Xcode integration.  
  - Notable types: `IXcodeGPUDebuggerPlugin`, `FXcodeGPUDebuggerPluginModule`, `FSXcodeGPUDebuggerPluginEditorExtension`, `FXcodeGPUDebuggerPluginCommands`, `FXcodeGPUDebuggerPluginStyle`.

## 3. Important Types & APIs

### `IXcodeGPUDebuggerPlugin`

- Role: Module interface; access via `Get()`/`IsAvailable()` helpers.

### `FXcodeGPUDebuggerPluginModule`

- Role: Registers commands, styles, and the editor extension on startup; cleans up on shutdown.

### `FSXcodeGPUDebuggerPluginEditorExtension`

- Role: Editor-side hooks for invoking Xcode GPU debugging; extends menus/toolbar through command bindings.

### `FXcodeGPUDebuggerPluginCommands` / `FXcodeGPUDebuggerPluginStyle`

- Role: Define Slate commands and style assets used by the plugin UI.

## 4. Typical usage patterns

- On macOS, enable the plugin, then use the provided toolbar/menu command to launch Xcode GPU debugger against the current session.  
- Configure any required project settings in Xcode as needed for GPU capture/debugging.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific changes noted; current implementation reflects the 5.7 source.
