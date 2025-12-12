# Common UI Plugin Overview

## 1. What this plugin does
- Provides a reusable, platform-agnostic UI framework with input routing, activatable screens, and common widget patterns.
- Supplies a large library of Slate/UMG widgets (buttons, tabs, carousels, lazy image loading, list/tree views).
- Integrates input abstraction through CommonInput for controller/keyboard/touch support and action routing.
- Includes editor settings and tools for authoring Common UI assets.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides runtime widgets/subsystems and editor settings/tools for building Common UI screens.

## 3. Key Modules
- **CommonUI** (Runtime)  
  - Role: Core widgets, activatable screen stack, input routing, lazy loading, and subsystems for visibility/control.
- **CommonUIEditor** (Editor)  
  - Role: Editor extensions for Common UI assets.
- **CommonInput** (Runtime)  
  - Role: Input mapping/types used by Common UI action routing.

## 4. Important Types & APIs

### Core widgets
- `UCommonActivatableWidget`, `UCommonActivatableWidgetContainer`: Screen/panel units with activation/deactivation lifecycle and animated transitions.
- `UCommonButtonBase`, `UCommonActionWidget`, `UCommonTabListWidgetBase`: Action-aware buttons and tab navigation widgets.
- `UCommonLazyImage`, `UCommonLazyWidget`, `UCommonListView`/`UCommonTileView`/`UCommonTreeView`: Async-loading and list controls adapted for Common UI styling.
- `UCommonWidgetCarousel`, `UCommonVisibilitySwitcher`: Containers for swapping widgets with animations/visibility rules.

### Input and routing
- `UCommonUIActionRouterBase`, `UCommonUIInputSettings`, `UCommonUIInputTypes`, `UIActionBinding`/`UIActionBindingHandle`: Define action bindings and routing across widgets and input devices.
- `UCommonAnalogCursor`, `UCommonBoundActionButton`/`Bar`: Helpers for controller-friendly cursor and bound UI actions.

### Subsystems and settings
- `UCommonUISubsystemBase`, `UCommonUIVisibilitySubsystem`: Engine subsystems that manage global UI state/visibility rules.
- `UCommonUISettings`, `UCommonUIEditorSettings`, `UCommonUIInputSettings`: Project settings for style, input data tables, and platform behavior.
- `UCommonGameViewportClient`: Game viewport client integrating Common UI focus/routing.

### Utilities
- `UCommonUILibrary`, `UCommonUIUtils`, `UCommonUIRichTextData`: Blueprint helpers and styling data for Common UI content.

## 5. Typical usage patterns
- Editor/project setup: Enable CommonUI and CommonInput, configure `UCommonUISettings`/`UCommonUIInputSettings` in project settings (input data tables, platform mappings).
- UI authoring: Build screens from `UCommonActivatableWidget` derivatives, use `UCommonButtonBase` and `UCommonActionWidget` for input-aware controls, and organize flows with activatable containers or carousels.
- Runtime: Register actions through the action router, use lazy widgets for async loading, and manage visibility with `UCommonUIVisibilitySwitcher` or subsystem-driven rules.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific changes called out in the source; overview reflects the current plugin state.
