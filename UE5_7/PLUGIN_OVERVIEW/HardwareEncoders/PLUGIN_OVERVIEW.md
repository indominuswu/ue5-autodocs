# HardwareEncoders Plugin Overview

## 1. What this plugin does
- Adds GPU hardware encoder backends (AMD AMF, NVIDIA NVENC) to the AVEncoder framework.
- Provides higher-performance H.264 encoding paths for capture/streaming workflows.
- Operates under existing AVEncoder/MediaCapture clients; no direct editor UI.

## 2. Key Modules
- **EncoderAMF** (Runtime)  
  - Role: AMD AMF-based H.264 encoder integration (`Amf_EncoderH264`).
- **EncoderNVENC** (Runtime)  
  - Role: NVIDIA NVENC-based H.264 encoder integration (`NVENC_EncoderH264`, `NVENCStats` helpers).

## 3. Important Types & APIs
- Encoders are internal classes wired into AVEncoder; no public UObject APIs are exposed. Module headers include `Amf_Common.h`, `NVENC_Common.h`, `NVENC_EncoderH264.h`.

## 4. Typical usage patterns
- Enable the plugin on supported hardware platforms; AVEncoder clients (e.g., Pixel Streaming, MediaCapture) can select hardware encoder backends when available.
- Choose encoder type through AVEncoder configuration or command-line switches used by the consuming system; no Blueprint nodes are provided.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
