# UBA Controller Plugin Overview

## 1. What this plugin does

- Adds support for distributing shader compilation using UnrealBuildAccelerator (UBA).
- Provides an editor-time module to communicate with UBA and process jobs.
- Enabled by default in the Build Distribution category.

## 2. Key Modules

- **UbaController** (Editor)
  - Role: Earliest-load editor module that initializes UBA communication and job processing utilities.

## 3. Important Types & APIs

### `FUbaControllerModule`

- Role: Module entry responsible for setting up UBA controller services during editor startup.

### `FUbaJobProcessor`

- Role: Handles job submission and processing logic for shader compile distribution through UBA.

### `UbaStringConversion`

- Role: String conversion helpers used by the controller and job processor.

## 4. Typical usage patterns

- Enable the plugin (on by default) and configure UBA as the shader compilation distribution backend.
- The module loads early to hook into the shader compile pipeline; usage is transparent once UBA endpoints are configured.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
