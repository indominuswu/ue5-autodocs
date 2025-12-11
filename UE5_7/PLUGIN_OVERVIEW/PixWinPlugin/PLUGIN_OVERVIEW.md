# PIX on Windows GPU Capture Plugin Overview

## 1. What this plugin does

- Integrates PIX on Windows for GPU capture/debugging in the editor (Win64, non-server).
- Adds commands, styles, and an editor extension widget to trigger PIX workflows.
- DeveloperTool module loaded post-config.

## 2. Key Modules

- **PixWinPlugin** (DeveloperTool, PostConfigInit, Win64-only, not for Server)  
  - Role: Registers PIX commands/UI and exposes module interface.  
  - Notable types: `IPixWinPlugin`, `FPixWinPluginModule`, `FPixWinPluginCommands`, `FPixWinPluginStyle`, `SPixWinPluginEditorExtension`.

## 3. Important Types & APIs

- `FPixWinPluginModule`: Sets up styles/commands and the editor extension widget on startup.  
- `FPixWinPluginCommands`: Slate command set for PIX actions.  
- `FPixWinPluginStyle`: Slate style assets used by the plugin UI.  
- `SPixWinPluginEditorExtension`: Editor UI for launching PIX captures/debug sessions.

## 4. Typical usage patterns

- Enable the plugin on Win64; use the PIX toolbar/menu or extension panel to start captures or attach to PIX workflows.  
- Intended for GPU debugging in editor builds; not used in server targets.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; reflects current PIX integration in 5.7.
