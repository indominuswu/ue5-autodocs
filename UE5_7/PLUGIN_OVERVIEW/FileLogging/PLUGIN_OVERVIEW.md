# File Logging Analytics Provider Plugin Overview

## 1. What this plugin does
- Implements an analytics provider that writes analytics events to local disk for debugging or offline analysis.
- Useful for inspecting analytics traffic without sending data to a remote backend.

## 2. Key Modules
- **FileLogging** (Runtime) - Registers the file-based analytics provider and module startup.

## 3. Important Types & APIs
### `FFileLoggingProvider`
- Role: Analytics provider implementation that serializes events to file output.
- Key functions: overrides analytics provider APIs to append events/attributes to logs on disk.

## 4. Typical usage patterns
- Enable the plugin and select the FileLogging provider when configuring the analytics system in your project.
- Run the game/editor to produce analytics logs locally; inspect generated files for validation.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific behaviors; functionality matches the provider shipped in this source tree.
