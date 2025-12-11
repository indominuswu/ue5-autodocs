# HttpBlueprint Plugin Overview

## 1. What this plugin does
- Enables authoring and executing HTTP requests directly in Blueprint graphs.
- Supplies Blueprint-friendly types for headers, verbs, and request presets.
- Provides editor graph support for building HTTP nodes.

## 2. Key Modules
- **HttpBlueprint** (Runtime)  
  - Role: Implements HTTP data types (`FHttpHeader`) and Blueprint function library for constructing/manipulating headers.
- **HttpBlueprintGraph** (UncookedOnly)  
  - Role: Editor graph integration for HTTP Blueprint nodes.

## 3. Important Types & APIs

### `UHttpBlueprintFunctionLibrary`
- Role: Blueprint helpers to work with headers and request metadata.
- Key functions: `MakeRequestHeader`, `GetHeaderValue`, `GetAllHeaders` / `GetAllHeaders_Map`, `AddHeader`, `RemoveHeader`.

### Enums and types
- `EHttpVerbs`: HTTP verbs (Post, Put, Delete, Patch, Get).
- `ERequestPresets`: Common request body/header presets (Json, Http, Url, Custom).
- `FHttpHeader`: Blueprint-visible struct storing header key/value pairs.

## 4. Typical usage patterns
- Enable the plugin, then use the provided Blueprint nodes to construct headers and configure requests in HTTP graph nodes.
- Choose verbs via `EHttpVerbs` and presets via `ERequestPresets` to control body formatting.
- Pair with the engine’s HTTP/REST nodes or custom HTTP graph elements supplied by this plugin to send/receive requests.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
