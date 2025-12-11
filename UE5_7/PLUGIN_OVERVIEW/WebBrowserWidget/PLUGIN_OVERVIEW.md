# Web Browser Plugin Overview

## 1. What this plugin does

- Adds a UMG widget (`UWebBrowser`) for embedding a web browser in UI.
- Supports loading URLs or raw HTML strings and exposes delegate events for navigation, popups, and console messages.
- Ships with asset management helpers for browser materials/resources.

## 2. Key Modules

- **WebBrowserWidget** (Runtime)
  - Role: Browser widget implementation and module setup; loads early (`PreDefault`).

## 3. Important Types & APIs

### `UWebBrowser` (Widget)
- Role: UMG widget wrapping a web browser view.
- Key functions: `LoadURL`, `LoadString` for navigation/content; delegates `OnUrlChanged`, `OnBeforePopup`, `OnConsoleMessage` for UI reactions.

### `UWebBrowserAssetManager`
- Role: Helper for loading browser-related assets/materials used by the widget.

### `IWebBrowserWidgetModule`
- Role: Module interface (header) providing module availability and initialization helpers.

## 4. Typical usage patterns

- Enable the plugin (Win64/Mac/Linux/Android/iOS). Add a `Web Browser` widget to a UMG layout and call `LoadURL` or `LoadString` to display content.
- Bind to the delegates to react to navigation changes, block popups, or capture console logs.
- For platform/browser configuration, adjust settings via project configuration (uses underlying WebBrowser subsystem).

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes; behavior reflects the current runtime widget implementation.
