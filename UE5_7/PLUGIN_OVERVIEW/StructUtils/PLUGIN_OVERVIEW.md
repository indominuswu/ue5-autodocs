# Struct Utils Plugin Overview

## 1. What this plugin does
- Experimental utilities around `FInstancedStruct` and related struct-handling helpers.
- Provides runtime modules (`StructUtils`, `StructUtilsEngine`) so engine and Iris networking code can use instanced struct serialization.
- Primarily a module wrapper; functionality lives inside the StructUtils runtime modules.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Exposes `StructUtils`/`StructUtilsEngine` modules (InstancedStruct and serialization helpers) for developers leveraging instanced structs in runtime or networking code.

## 3. Key Modules
- **StructUtils** (Runtime, Experimental) – Core InstancedStruct utilities usable without full engine dependencies.
- **StructUtilsEngine** (Runtime, Experimental) – Engine-facing extensions for InstancedStruct when compiling against the engine.

## 4. Important Types & APIs
- Module interfaces only; InstancedStruct and serialization helpers live in the module sources (the plugin exposes the modules to projects).

## 5. Typical usage patterns
- Enable the plugin to make `StructUtils`/`StructUtilsEngine` modules available to your project or plugin.
- Use `FInstancedStruct` and related serialization/net-serialization helpers in runtime code; engine features such as Iris networking rely on these modules when enabled.

## 6. Version-specific notes (UE 5.7)
- Marked experimental and deprecated for Engine 5.5 in the plugin descriptor; still present in the 5.7 source tree for compatibility.

