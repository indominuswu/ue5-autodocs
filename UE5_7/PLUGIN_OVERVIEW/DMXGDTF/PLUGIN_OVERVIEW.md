# DMX GDTF Plugin Overview

## 1. What this plugin does

- Implements the General Device Type Format (GDTF) standard for describing lighting fixtures.
- Provides parsers and data structures to read `.gdtf` files and expose fixture definitions to the DMX Engine.
- Includes a lightweight zip utility for packaged GDTF archives and test coverage for the specification.

## 2. Key Modules

- **DMXGDTF** (Runtime) – GDTF parsing, data models, and protocol mapping (Art-Net, sACN, DMX).
- **DMXGDTFTests** (Editor) – Test harnesses for validating GDTF parsing and data correctness.
- **DMXZip** (Runtime) – Zip helper used to read packaged GDTF files.

## 3. Important Types & APIs

- Core data models: `FDMXGDTFFixtureType`, `FDMXGDTFDMXMode`, `FDMXGDTFAttribute`, `FDMXGDTFDMXChannel`, `FDMXGDTFDMXProfile`, and related geometry/feature structures (e.g., `FDMXGDTFGeometry`, `FDMXGDTFWheel`, `FDMXGDTFEmitter`).
- Protocol mappings: `FDMXGDTFProtocolArtNet`, `FDMXGDTFProtocolSACN`, and `FDMXGDTFProtocolFTRDM` – Capture protocol-specific configuration from GDTF.
- Utility types such as `DMXZipper`/`DMXZipLog` for handling zipped GDTF packages and diagnostics.

## 4. Typical usage patterns

- Enable DMX Engine, DMX Protocol, and DMX GDTF; import a `.gdtf` file via DMX editor workflows (e.g., using the GDTF factory in DMX Engine) to create fixture types from standardized definitions.
- Access parsed fixture data (modes, attributes, geometries) via the DMX Engine and bind them to libraries/patches without manually recreating fixture definitions.
- Use the provided tests as references when extending or validating additional parts of the GDTF spec.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
