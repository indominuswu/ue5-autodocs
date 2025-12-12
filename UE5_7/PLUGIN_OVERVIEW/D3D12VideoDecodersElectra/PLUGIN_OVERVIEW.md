# D3D12 Hardware accelerated video decoding plugin for the Electra media player Plugin Overview

## 1. What this plugin does

- Integrates Direct3D 12 hardware video decoding into the Electra media player pipeline.
- Uses vendor-provided GPU decoders for formats like H.264/H.265 to offload video decode to hardware.
- Targeted at Windows platforms using D3D12; disabled by default.

## 2. Editor/Runtime surfaces

- User-facing: No - Platform backend for Electra (Win64 `D3D12VideoDecodersElectra` runtime only) enabling GPU video decode; no editor workflows or gameplay APIs.

## 3. Key Modules

- **D3D12VideoDecodersElectra** (Runtime)  
  - Role: Implements codec-specific decoder paths and module glue for Electra.
  - Notable types: `FVideoDecoder_D3D12_H264`, `FVideoDecoder_D3D12_H265`, common helpers in `VideoDecoder_D3D12_Common`.

## 4. Important Types & APIs

### `FVideoDecoder_D3D12_*`
- Role: Codec-specific decoders that interface with D3D12 video acceleration for Electra streams.
- Key behavior: Create decode contexts, handle error reporting via `DecoderErrors_D3D12`, and feed frames into Electra.

### `FD3D12VideoDecodersElectraModule`
- Role: Module startup/shutdown and registration with the media player factory.

## 5. Typical usage patterns

- Enable the plugin on Windows builds using Electra when GPU decode is desired.
- Electra will select the D3D12 decoder when available; no direct Blueprint/API surface is exposed.
- Ensure the target GPU/driver supports D3D12 video decode for the chosen codec.

## 6. Version-specific notes (UE 5.7)

- Plugin remains optional and off by default; no UE 5.7-specific changes noted in source comments.

