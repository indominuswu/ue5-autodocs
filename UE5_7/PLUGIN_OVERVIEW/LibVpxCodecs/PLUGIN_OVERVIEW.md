# LibVpxCodecs Plugin Overview

## 1. What this plugin does
- Adds VPX-based codecs (e.g., VP8/VP9) from LibVpx into the AVCodecs stack.
- Enables playback/encoding support for media formats backed by the LibVpx implementation.

## 2. Key Modules
- **LibVpxCodecs** (Runtime)  
  - Role: Registers LibVpx codecs with the engine’s AV codecs registry.  
  - Notable types: none exposed; functionality is internal codec registration.

## 3. Important Types & APIs
- No public-facing classes or Blueprint APIs; the module registers codecs at startup for the media framework.

## 4. Typical usage patterns
- Enable the plugin to allow media players to load VPX streams through the AVCodecs layer; no direct code changes are required.
- Use engine media players as usual—VPX formats will be available if the plugin is enabled.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; the plugin is experimental and disabled by default.

