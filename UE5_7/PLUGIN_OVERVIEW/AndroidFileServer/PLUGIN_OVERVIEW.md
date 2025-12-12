# AndroidFileServer Plugin Overview

## 1. What this plugin does
- Adds remote file management support for Android projects via a platform file server (USB and/or network).
- Exposes Blueprint APIs to start/stop the file server and query its status.
- Provides editor settings to control manifest flags and runtime behavior.

## 2. Editor/Runtime surfaces
- User-facing: Yes - offers Blueprint control library (`UAndroidFileServerBPLibrary`) and project settings for developers to start/stop the Android file server.

## 3. Key Modules
- **AndroidFileServer** (Runtime, PreLoadingScreen)
  - Role: Hosts the runtime file server and Blueprint control library.
- **AndroidFileServerEditor** (Editor)
  - Role: Editor settings integration and manifest configuration support.

## 4. Important Types & APIs
- `UAndroidFileServerBPLibrary`
  - Role: BlueprintFunctionLibrary to control the file server.
  - Key functions: `StartFileServer(bUSB, bNetwork, Port)`, `StopFileServer`, `IsFileServerRunning`.
- `UAndroidFileServerRuntimeSettings`
  - Role: Project settings for enabling services, permissions, and startup behavior.

## 5. Typical usage patterns
- Enable the plugin (on by default for Android). Configure runtime settings in Project Settings to allow USB/network access and desired port.
- In Blueprint or code, call `StartFileServer` to expose project files for remote access during development or profiling; stop when finished.
- Combine with Android platform deployment workflows that rely on live file access.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
