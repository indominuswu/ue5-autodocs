# RHI Tests Plugin Overview

## 1. What this plugin does
- Hosts automation tests for low-level RHI functionality (buffers, textures, draw/clear, readback, bindless, reserved resources).
- Provides focused test cases for platform RHI coverage and regression detection.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Automation test suites for RHI validation in test builds.

## 3. Key Modules
- **RHITests** (Runtime/Test)  
  - Collection of RHI test entry points defined in individual headers; loaded post-config-init for test environments.

## 4. Important Types & APIs
- Test suites: `RHIBufferTests`, `RHITextureTests`, `RHIClearTextureTests`, `RHIDrawTests`, `RHIReadbackTests`, `RHIReservedResourceTests`, `RHIGraphicsUAVTests`, `RHIBindlessTests`, `RHIAllocatorTests`.
- Shared utilities: `RHITestsCommon.h` provides helpers and macros used by the suites.
- `FRHITestsModule` registers tests with automation when the plugin loads.

## 5. Typical usage patterns
- Enable in test builds and run the automation tests to validate RHI correctness on a target platform.
- Extend with new test headers following the existing pattern to cover custom RHI features or vendor extensions.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
