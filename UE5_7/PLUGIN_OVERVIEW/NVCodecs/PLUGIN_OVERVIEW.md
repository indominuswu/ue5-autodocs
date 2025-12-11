# NVCodecs Plugin Overview

## 1. What this plugin does
- Adds NVIDIA Media Codec SDK-based encoders/decoders to the AVCodecs stack.
- Provides CUDA-backed video resources plus NVENC and NVDEC implementations for Win64/Linux.
- Extends AVCodecsCore with GPU-accelerated encode/decode paths.

## 2. Key Modules
- **NVCodecs** (Runtime): Core integration glue for NVIDIA codecs within AVCodecs.
- **NVCodecsRHI** (Runtime): RHI-facing helpers for interop with GPU resources.
- **NVDEC** (Runtime): NVIDIA hardware video decoder implementation.
- **NVENC** (Runtime): NVIDIA hardware video encoder implementation.

## 3. Important Types & APIs
### `FVideoContextCUDA` / `FVideoResourceCUDA`
- Role: CUDA-backed video context/resource used to interop with D3D11/D3D12/Vulkan surfaces.
- Key functions: resource transform helpers from platform-specific video resources into CUDA.
### `FVideoDecoderNVDEC` / `FVideoDecoderConfigNVDEC`
- Role: NVDEC decoder and configuration describing supported bitstreams and session setup.
- Key properties: codec config structs, output resource wiring to CUDA surfaces.
### `FVideoEncoderNVENCCUDA` and other `FVideoEncoderNVENC*`
- Role: NVENC encoder variants for CUDA, D3D11, and D3D12 backends sharing core `FEncoderNVENC` logic.
- Key properties: encoder configuration (`FVideoEncoderConfigNVENC`), rate control/setup parameters.

## 4. Typical usage patterns
- Enable NVCodecs on supported Windows/Linux targets to expose NVENC/NVDEC to AVCodecs.
- Create video encoder/decoder instances via AVCodecs factory; use CUDA-backed resources for zero-copy transfers.
- Configure encoder/decoder settings through the provided NVENC/NVDEC config structs when initializing sessions.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; no other 5.7-specific notes beyond the experimental flag and platform allow list.
