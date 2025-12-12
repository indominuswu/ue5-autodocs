# MsQuic Runtime Plugin Overview

## 1. What this plugin does
- Loads and initializes the MsQuic library for use by networking features that require QUIC.
- Handles locating/shipping the correct platform binaries and exposing a runtime initialization path.

## 2. Editor/Runtime surfaces

- User-facing: No - Acts as a runtime wrapper that loads MsQuic binaries for dependent networking plugins; it exposes no editor tools, settings, or Blueprint/gameplay APIs on its own.

## 3. Key Modules
- **MsQuicRuntime** (Runtime)
  - Role: Module wrapper for the MsQuic DLL/SO; provides initialization/shutdown and versioned binary loading.
  - Notable types: `FMsQuicRuntimeModule`.

## 4. Important Types & APIs

### `FMsQuicRuntimeModule`
- Role: Module entry that loads the MsQuic library (`InitRuntime`) and frees it on shutdown.
- Key properties: version/binary path constants (`MSQUIC_VERSION`, `MSQUIC_BINARIES_PATH`).

## 5. Typical usage patterns
- Enable the plugin to make MsQuic binaries available; call `FMsQuicRuntimeModule::InitRuntime()` from dependent code before issuing QUIC operations.
- Ensure shutdown runs (module unload) to release library handles when the engine exits or the plugin is disabled.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

