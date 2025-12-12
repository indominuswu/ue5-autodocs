# MotionJPEG Decoder for Electra Plugin Overview

## 1. What this plugin does

- Adds MotionJPEG (MJPEG) video decoding support to the Electra media pipeline.
- Registers a decoder module so Electra-based media players can open MJPEG-encoded sources.
- Disabled by default; enable when MJPEG playback is required.

## 2. Editor/Runtime surfaces

- User-facing: No - Backend Electra decoder; users just enable it if they need MJPEG playback, with no direct editor or Blueprint interface.

## 3. Key Modules

- **MJPEGDecoderElectra** (Runtime) — implements the `ElectraMediaMJPEGDecoder` and module glue registering the decoder with Electra.

## 4. Important Types & APIs

- `FElectraMediaMJPEGDecoder` (private) — decodes MJPEG frames for Electra playback.
- Module entry (`FMJPEGDecoderElectraModule`) — installs the decoder into Electra’s codec registry.

## 5. Typical usage patterns

- Enable the plugin alongside an Electra-based media player backend; the decoder becomes available automatically for MJPEG assets/streams.
- No editor UI; behaves transparently when the media source is MJPEG encoded.

## 6. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific changes noted.

