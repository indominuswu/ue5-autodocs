# PlainPropsEngine Plugin Overview

## 1. What this plugin does
- Experimental engine-level bindings for the PlainProps serialization prototype.
- Adds commandlets and integration points to exercise PlainProps within engine code paths.
- Depends on the core PlainProps and PlainPropsUObject plugins.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Experimental but exposes engine commandlets/bindings for teams testing PlainProps serialization inside engine workflows.

## 3. Key Modules
- **PlainPropsEngine** (Runtime, PreLoadingScreen)  
  - Role: Engine bindings and commandlets that connect PlainProps to engine systems; Win64 only.

## 4. Important Types & APIs
- `FPlainPropsEngineModule`  
  - Role: Module entry for engine-level PlainProps support.
- `PlainPropsCommandlets.h`  
  - Role: Defines commandlets for running PlainProps workflows from the command line (e.g., testing or generating data).
- `PlainPropsEngineBindings` (private)  
  - Role: Internal bindings glue PlainProps into engine-specific types/utilities.

## 5. Typical usage patterns
- Enable along with `PlainProps` and `PlainPropsUObject` on Win64.  
- Run the provided PlainProps commandlets to validate or process PlainProps data in an engine context.  
- Use this module when engine-level serialization experiments with PlainProps are required.

## 6. Version-specific notes (UE 5.7)
- Marked experimental and Win64-only; loads early (PreLoadingScreen).  
- No explicit UE 5.7-specific behaviors beyond current source.

