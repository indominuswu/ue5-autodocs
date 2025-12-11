# Niagara MRQ Support Plugin Overview

## 1. What this plugin does

- Provides a Niagara data interface that exposes Movie Render Queue (MRQ) information to Niagara simulations.
- Allows Niagara systems to read temporal sample counts, frame indices, and sequence frame rate during MRQ renders.

## 2. Key Modules

- **NiagaraMRQ** (Runtime) – Data interface and shader parameter plumbing for MRQ integration.

## 3. Important Types & APIs

### `UNiagaraDataInterfaceMRQ`

- Niagara data interface (`UNiagaraDataInterface`) tagged as “MovieRenderQueue”.
- Exposes shader parameters such as `Active`, `TemporalSampleCount`, `TemporalSampleIndex`, and `SequenceFPS`.
- Implements per-instance data, HLSL generation (`GetFunctionHLSL`, `GetParameterDefinitionHLSL`), and provides GPU parameters for use in Niagara scripts.

## 4. Typical usage patterns

- Enable the plugin, add the “MovieRenderQueue” data interface to Niagara systems used in MRQ renders, and read its parameters inside Niagara scripts to branch or adjust simulation based on MRQ temporal sampling.
- Suitable for effects that need to align with MRQ temporal sampling (motion blur, accumulation) when rendering sequences.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes found; overview reflects the current runtime implementation.

