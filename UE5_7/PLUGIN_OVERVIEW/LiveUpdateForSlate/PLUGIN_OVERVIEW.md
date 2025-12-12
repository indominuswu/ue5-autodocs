# Live Update for Slate Plugin Overview

## 1. What this plugin does

- Refreshes the editor’s Slate layout and tabs when Live Coding finishes patching modules.
- Helps keep the editor UI in sync with hot-reloaded code during development.
- Provides a simple per-user editor setting to toggle the behavior.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor feature; users toggle `ULiveUpdateSlateSettings` to auto-refresh Slate after Live Coding patches.

## 3. Key Modules

- **LiveUpdateForSlate** (Editor)
  - Role: Hooks Live Coding completion notifications and triggers Slate layout refreshes.
  - Notable types: `ULiveUpdateSlateSettings`, module startup that registers the behavior.

## 4. Important Types & APIs

### `ULiveUpdateSlateSettings`

- Role: EditorPerProjectUserSettings object that toggles automatic Slate refresh after Live Coding patches.
- Key properties: `bEnableLiveUpdateForSlate` (default `true`).

## 5. Typical usage patterns

- Enable the plugin in editor builds.
- Use Project Settings (user settings) to toggle “Refreshes the editor's Slate layout when Live Coding patches are complete.”
- Perform Live Coding; the plugin refreshes open tabs/layouts so hot-reloaded widgets reflect the new code.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

