# ImageWidgets Plugin Overview

## 1. What this plugin does
- Supplies generic Slate widgets and interfaces for displaying images and image-like content.
- Provides reusable viewers and catalogs for image browsing inside Slate tools.
- Editor-focused utility; no runtime gameplay components.

## 2. Key Modules
- **ImageWidgets** (Editor)  
  - Role: Registers Slate widgets for image viewing/cataloging and an image viewer interface.

## 3. Important Types & APIs

### Slate widgets and interfaces
- `IImageViewer`: Interface for consumers that need to display image content.
- `SImageViewport`: Viewport widget for rendering an image with pan/zoom controls.
- `SImageCatalog`: Widget for browsing/selecting images from a collection.

## 4. Typical usage patterns
- Enable the plugin to reuse the image viewing widgets within custom editor tools or content browsers.
- Compose `SImageViewport` and `SImageCatalog` in Slate UI to preview textures or external images; implement `IImageViewer` to feed image data.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
