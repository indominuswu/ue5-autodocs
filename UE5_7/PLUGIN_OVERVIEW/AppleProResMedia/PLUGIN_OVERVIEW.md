# Apple ProRes Media Plugin Overview

## 1. What this plugin does
- Implements video playback and export support for the Apple ProRes codec.
- Provides encoder and decoder integration, Movie Render Pipeline nodes, and media settings for ProRes workflows.
- Supplies third-party ProRes toolbox headers for encoding/decoding.

## 2. Key Modules
- **AppleProResMedia** (Runtime, PostEngineInit)
  - Role: Core ProRes media integration, encoder/decoder registration, and pipeline nodes.

## 3. Important Types & APIs
- `UAppleProResMediaSettings`
  - Role: Project settings for ProRes usage.
- `FAppleProResEncoder`
  - Role: Encoder implementation wrapping the ProRes toolbox.
- `FAppleProResEncoderProtocol`
  - Role: Protocol definitions for encoder operations.
- `WmfMediaAppleProResDecoder`
  - Role: Windows decoder integration for ProRes playback.
- Movie pipeline nodes: `UMoviePipelineAppleProResOutput`, `UMovieGraphAppleProResNode`
  - Role: Output nodes for Movie Render Pipeline supporting ProRes.
- Third-party headers (`ProResFileReader`, `ProResFileWriter`, etc.)
  - Role: Low-level codec support shipped with the plugin.

## 4. Typical usage patterns
- Enable the plugin on platforms where ProRes ingest/export is needed.
- Configure `AppleProResMedia` settings; use Movie Render Pipeline ProRes output nodes for rendering sequences.
- Play ProRes media through the Media Framework; the plugin registers ProRes codec support for playback and encoding.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
