# PlainPropsUObject Plugin Overview

## 1. What this plugin does
- Experimental CoreUObject bindings for the PlainProps serialization prototype.
- Provides runtime helpers to exercise PlainProps round-tripping with UObject types.
- Serves as a bridge between PlainProps core and engine-level integrations.

## 2. Key Modules
- **PlainPropsUObject** (Runtime, PreLoadingScreen)  
  - Role: CoreUObject bindings and runtime helpers for PlainProps; Win64 only.

## 3. Important Types & APIs
- `FPlainPropsUObjectModule`  
  - Role: Module entry for UObject bindings.
- `PlainPropsUObjectRuntime.h`  
  - Role: Runtime utilities for using PlainProps with UObject data.
- `PlainPropsRoundtripTest.h`  
  - Role: Helpers/tests for round-tripping PlainProps data through UObject serialization paths.

## 4. Typical usage patterns
- Enable alongside `PlainProps` (required) and optionally `PlainPropsEngine`.  
- Use the runtime helpers to serialize/deserialize UObject-related data via PlainProps and validate round-trips.  
- Useful as a dependency when experimenting with PlainProps in engine code that touches UObject serialization.

## 5. Version-specific notes (UE 5.7)
- Marked experimental and Win64-only; loads early (PreLoadingScreen).  
- No explicit UE 5.7-specific behaviors noted; overview reflects current source.
