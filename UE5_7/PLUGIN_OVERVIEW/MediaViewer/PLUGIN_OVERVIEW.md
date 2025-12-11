# Media Viewer Plugin Overview

## 1. What this plugin does
- Editor-only media viewer for inspecting and comparing media assets (textures, render targets, media sources, viewports).
- Provides a library-style browser with grouping, drag/drop, and quick access to media items from the Content Browser.
- Offers image viewers with overlays, status bars, and multiple viewer factories for different media types.
- Adds toolbar/commands to open dedicated Media Viewer tabs inside the editor.

## 2. Key Modules
- **MediaViewer** (Editor)
  - Role: Implements the Media Viewer tab, library management, image viewer implementations, and Content Browser integration.
  - Notable types: `FMediaViewerModule`, `IMediaViewerModule`, `IMediaViewerLibrary`, `FMediaViewerLibrary`, `IMediaImageViewerFactory`, `FMediaImageViewer`, `SMediaViewer`.

## 3. Important Types & APIs
### `IMediaViewerLibrary` / `FMediaViewerLibrary`
- Role: Manages collections of `FMediaViewerLibraryItem`/`Group` entries, persisting and querying items to display.
- Key features: supports dynamic groups, asset-backed entries, and cached texture data for quick preview.

### `FMediaImageViewer` and factories (`IMediaImageViewerFactory`)
- Role: Viewer implementations for different media kinds (media textures, render targets, level viewports, color swatches).
- Key properties: overlay/status support (`SMediaImageViewerOverlay`, `SMediaImageViewerStatusBar`) and texture sample caches for efficient refresh.

### `SMediaViewer` / `SMediaViewerToolbar`
- Role: Main Slate UI that hosts the library panel, viewer viewport, drop targets, and toolbar commands.

### `FMediaViewerCommands` / `FMediaViewerStyle`
- Role: Command definitions and styling used to register the Media Viewer window and bind keyboard shortcuts.

## 4. Typical usage patterns
- Enable the plugin (Editor category). Open the Media Viewer tab from the Window/Media menu or toolbar.
- Drag media assets (textures, media sources, render targets) into the library; organize via groups and compare items side by side.
- Use viewer-specific overlays to inspect metadata, playback state, and color sampling; switch viewer implementations via toolbar commands.
- Content Browser integration allows right-click or drag/drop to send assets directly to the Media Viewer.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview reflects the plugin state in UE 5.7.
