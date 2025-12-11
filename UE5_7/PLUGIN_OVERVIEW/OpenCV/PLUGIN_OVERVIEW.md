# OpenCV Plugin Overview

## 1. What this plugin does

- Initializes and exposes the bundled OpenCV library for computer-vision utilities inside Unreal Engine.
- Provides Blueprint-callable helpers for reading/writing images, pixel buffer conversion, and direct access to OpenCV headers.
- Intended for runtime scripting/experimentation where OpenCV operations complement engine rendering or media capture.

## 2. Key Modules

- **OpenCVHelper** (Runtime)  
  - Role: Loads the third-party OpenCV distribution and exposes helper functions/headers to projects.

## 3. Important Types & APIs

- `UOpenCVBlueprintFunctionLibrary`  
  - Blueprint nodes for common OpenCV tasks (image loading/saving, buffer conversion).
- `FOpenCVHelper`  
  - C++ utility layer that wraps OpenCV usage and manages initialization.
- `PreOpenCVHeaders.h` / `PostOpenCVHeaders.h`  
  - Include wrappers to safely use OpenCV headers within Unreal build settings.

## 4. Typical usage patterns

- Enable the plugin and include `OpenCVHelper` in module dependencies to get access to OpenCV headers and libraries.
- In Blueprints, call nodes from `OpenCVBlueprintFunctionLibrary` for simple image processing workflows.
- In C++, include `PreOpenCVHeaders.h` / `PostOpenCVHeaders.h` when working directly with OpenCV types to avoid macro conflicts.
- No editor UI is added; usage is via code or Blueprint nodes.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current OpenCV helper integration in the UE 5.7 source tree.
