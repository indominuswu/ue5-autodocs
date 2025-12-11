# Avid DNxHR/DNxMXF Media Plugin Overview

## 1. What this plugin does

- Provides Avid DNxHR/DNxMXF encoding support for Unreal’s media/export pipelines.
- Integrates with Movie Render Queue and Movie Graph to output DNx-formatted video.
- Runtime-only module; no standalone editor panel beyond the added output options.

## 2. Key Modules

- **AvidDNxMedia** (Runtime)  
  - Role: Implements DNx encoders and connects them to Movie Render and Movie Graph nodes.

## 3. Important Types & APIs

- `FAvidDNxEncoder`, `FAvidDNxEncoderProtocol`: Core encoder and protocol helpers for writing DNx streams.
- `UMoviePipelineAvidDNxOutput`: Movie Render Queue output provider that encodes rendered frames to DNx.
- `UMovieGraphAvidDNxHRNode`: Movie Graph node exposing DNxHR output settings for graph-driven renders.

## 4. Typical usage patterns

- Enable the plugin, then select the DNx output option in Movie Render Queue via `UMoviePipelineAvidDNxOutput`.
- In Movie Graph workflows, add `MovieGraphAvidDNxHRNode` to route renders through DNx encoding.
- Configure encoder settings (resolution, bitrate, profile) through the output/provider details panels associated with the Movie Render Queue or Movie Graph node.

## 5. Version-specific notes (UE 5.7)

- Disabled by default; intended for projects needing DNx export.
- No explicit UE 5.7-specific notes found; overview reflects the current plugin state.
