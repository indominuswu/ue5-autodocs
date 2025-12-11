# WebAPI Plugin Overview

## 1. What this plugin does

- Provides tooling to generate Unreal-friendly APIs from web specifications (OpenAPI) and to call them at runtime.
- Includes editor subsystems, providers, and settings for code generation plus optional LiquidJS templating.
- Supplies runtime types for HTTP requests/responses and a subsystem to execute operations.

## 2. Key Modules

- **WebAPI** (Runtime)
  - Role: Runtime plumbing for web API operations (`UWebAPISubsystem`, HTTP handlers, developer settings, operation objects).
- **WebAPIEditor** (Editor)
  - Role: Editor integration, providers, settings, and message logging for generating API assets.
- **WebAPIBlueprintGraph** (UncookedOnly)
  - Role: Blueprint graph support for generated API operations.
- **WebAPIOpenAPI** (Editor)
  - Role: OpenAPI provider for parsing OpenAPI specs into WebAPI definitions.
- **WebAPILiquidJS** (Editor)
  - Role: LiquidJS templating support for codegen output.

## 3. Important Types & APIs

### `UWebAPISubsystem` (Subsystem)
- Role: Central runtime entry point to send web requests defined by generated operations and handle responses.
- Key types: Works with `FWebAPIHttpRequest`, `FWebAPIMessageResponse`, and `UWebAPIOperationObject` instances produced by codegen.

### `UWebAPIDeveloperSettings`
- Role: Configures default options for runtime behavior and codegen (paths, providers, message handling).

### `UWebAPIEditorSubsystem`
- Role: Editor subsystem coordinating API generation, error reporting, and provider selection.

### `UWebAPIProvider` / `UWebAPIProviderSettings`
- Role: Abstract provider interface and settings used by specific inputs like OpenAPI; supply parsed definitions to the generator.

### `WebAPI Http handlers`
- Role: Pluggable message handler structs for HTTP requests/responses (`WebAPIHttpMessageHandlers.h`) used by operation objects at runtime.

### Blueprint graph support
- Role: `WebAPIBlueprintGraph` module exposes Blueprint nodes for generated operations, enabling visual scripting against the generated APIs.

## 4. Typical usage patterns

- Enable the plugin (and dependencies `PluginBrowser`, `WebSocketNetworking`). In the editor, import an OpenAPI spec using the WebAPI tools; choose an OpenAPI provider and generation template (LiquidJS or defaults) in the settings.
- Generated definitions create `UWebAPIOperationObject`-based assets and supporting C++/Blueprint types. Use `UWebAPIEditorSubsystem` to regenerate when specs change.
- At runtime, access `UWebAPISubsystem` to dispatch operations; configure `UWebAPIDeveloperSettings` for handler defaults and message processing.
- Blueprint users can call generated nodes provided by `WebAPIBlueprintGraph` to send requests and process responses.

## 5. Version-specific notes (UE 5.7)

- Marked experimental. No explicit UE 5.7-only behaviors were noted; overview reflects current source.
