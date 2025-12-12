# SlateIM Plugin Overview

## 1. What this plugin does

- Provides an immediate mode wrapper around Slate, aimed at quickly building debugging and tooling UIs.
- Offers a set of lightweight `SIm*` widgets (buttons, tables, tabs, graphs, containers) for immediate-mode rendering.
- Includes viewport/window roots and in-game overlay support for rendering SlateIM UIs in editor or runtime contexts.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Supplies immediate-mode Slate widgets and in-game/editor overlays for building debugging and tooling UIs.

## 3. Key Modules

- **SlateIM** (Runtime, Default)  
  - Role: Core immediate-mode Slate API, widget scopes, containers, roots, and manager.
- **SlateIMInGame** (Runtime, Default)  
  - Role: In-game entry points, widget bases, and cheat manager hooks for rendering SlateIM content during play.

## 4. Important Types & APIs

### Core API and management

- `FSlateIMManager`, `FSlateIMWidgetScope`, `FSlateIMSlotData`: Manage immediate-mode widget lifetimes and layout data.
- Roots: `FSlateIMViewportRoot`, `FSlateIMWindowRoot`, `FSlateIMExposedRoot` for hosting IM content.
- Logging/type helpers: `SlateIMLogging.h`, `SlateIMTypeChecking.h`.

### Widgets and containers

- Immediate-mode widgets and containers such as `SImButton`, `SImCheckBox`, `SImGraph`, `SImTableView`, `SImTabGroup`, `SImScrollBox`, and stack/wrap/compound containers.
- Context/utility widgets: `SImContextMenuAnchor`, `SImPopUp`, `SImWrapper`, and modular table/column helpers.

### In-game support

- `USlateIMInGameWidgetBase`, `USlateIMInGameWidgetModularFeature`, `USlateIMInGameWidgetCheatManager`: Hooks to display SlateIM overlays while the game is running.

## 5. Typical usage patterns

- Enable the plugin, include `SlateIM.h`, and build UI using the provided immediate-mode API and `SIm*` widgets.
- Create a SlateIM root (viewport or window) and populate it each frame with widget calls guarded by `FSlateIMWidgetScope`.
- For runtime overlays, use the in-game module to register a SlateIM widget and toggle it via the cheat manager or modular feature.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
