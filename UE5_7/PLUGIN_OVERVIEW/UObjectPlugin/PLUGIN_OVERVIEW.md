# UObject Example Plugin Overview

## 1. What this plugin does

- Demonstrates declaring a custom `UObject` and `UStruct` inside a plugin module.
- Serves as a lightweight template for creating object types without modifying engine code.
- Enabled by default as an example module.

## 2. Key Modules

- **UObjectPlugin** (Runtime, Default)  
  - Role: Provides example object/struct types and standard module interface helpers.  
  - Notable types: `IUObjectPlugin`, `UMyPluginObject`, `FMyPluginStruct`.

## 3. Important Types & APIs

### `IUObjectPlugin`

- Role: Public module interface; `Get()`/`IsAvailable()` for module access.

### `UMyPluginObject`

- Role: Example `UObject` defined in the plugin.  
- Key data: Contains `FMyPluginStruct MyStruct` as a private property.

### `FMyPluginStruct`

- Role: Simple struct with a `FString TestString` property, illustrating UStruct usage in a plugin module.

## 4. Typical usage patterns

- Use as a starting point for defining custom `UObject`/`UStruct` types within your own plugin module.
- Duplicate/rename the module and extend the object/struct with project-specific properties and functions.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific behavior; example content reflects the current 5.7 source.
