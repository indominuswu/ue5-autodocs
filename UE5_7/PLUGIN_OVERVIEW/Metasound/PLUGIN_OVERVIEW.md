# MetaSound Plugin Overview

## 1. What this plugin does
- High-performance audio system providing graph-based DSP for sound sources with sample-accurate control and modulation.
- Supplies runtime graph core, generators, standard node library, engine integration, and editor tooling for building MetaSound assets.
- Includes editor-only testing and node registration utilities.
- Enabled by default in UE 5.7.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime MetaSound graph/audio assets plus editor graph UI and node tools.

## 3. Key Modules
- **MetasoundGraphCore** (Runtime, PreDefault)
  - Role: Core graph representation, literals, and data types for MetaSound documents.
- **MetasoundGenerator** (Runtime, PreDefault)
  - Role: Audio generator implementation that renders MetaSound graphs.
- **MetasoundFrontend** (Runtime, PreDefault)
  - Role: Frontend document model, node registration, and serialization.
- **MetasoundStandardNodes** (Runtime, PreDefault)
  - Role: Built-in DSP and utility node library.
- **MetasoundEngine** (Runtime, PreDefault)
  - Role: Engine integration (asset types, output system, settings, builder subsystems).
  - Notable types: `UMetaSoundSource`, `UMetaSoundPatch`, `UMetaSoundWave`, `UMetaSoundBuilderSubsystem`, `UMetaSoundAssetSubsystem`, `UMetasoundOutputSubsystem`, `UMetasoundOperatorCacheSubsystem`, `FMetasoundGeneratorHandle`, `UMetasoundSettings`.
- **MetasoundEngineTest** (UncookedOnly, PreDefault)
  - Role: Test harness for engine integration.
- **MetasoundEditor** (UncookedOnly, PreDefault)
  - Role: Editor asset editors, graph UI, and node registration tools.

## 4. Important Types & APIs
### `UMetaSoundSource` / `UMetaSoundPatch` / `UMetaSoundWave`
- Role: Asset types representing MetaSound graphs used as sources, reusable patches, or baked waves.
- Key properties: referenced frontend document, graph inputs/outputs, and referenced standard/custom nodes.

### `UMetaSoundBuilderSubsystem`
- Role: Blueprint-accessible subsystem to build or modify MetaSound documents at runtime or in editor scripts.
- Key functions: add nodes/edges, set inputs, generate outputs, and register document builders (`FMetasoundDocumentBuilderRegistry`).

### `UMetaSoundAssetSubsystem` / `UMetasoundOutputSubsystem` / `UMetasoundOperatorCacheSubsystem`
- Role: Manage asset lifecycle, audio output routing, and operator caching for efficient playback.

### `UMetasoundSettings`
- Role: Project settings controlling enabling/disabling MetaSound, performance options, and experimental features.

## 5. Typical usage patterns
- Create MetaSound Source or Patch assets and edit them in the MetaSound editor (graph UI from `MetasoundEditor`).
- Reference MetaSound Sources in sound cues or directly on audio components to drive sample-accurate DSP graphs.
- Use Blueprint or C++ via `UMetaSoundBuilderSubsystem` to programmatically assemble graphs or modify parameters at runtime.
- Register custom nodes through the frontend APIs and include them in assets alongside `MetasoundStandardNodes`.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin is enabled by default and corresponds to the UE 5.7 implementation.
