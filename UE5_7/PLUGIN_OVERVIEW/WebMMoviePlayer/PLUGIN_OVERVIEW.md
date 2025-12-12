# Movie Player for WebM files Plugin Overview

## 1. What this plugin does

- Integrates WebM playback with the startup movie pipeline (PreLoadingScreen phase).
- Uses the `WebMMedia` decoder to render WebM videos during loading screens on desktop platforms.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Registers a WebM-capable startup movie player so projects can play WebM files during loading screens via standard movie settings.

## 3. Key Modules

- **WebMMoviePlayer** (RuntimeNoCommandlet)
  - Role: Registers a movie player that leverages WebM decoding for startup/transition movies on Win64/Linux/Mac.

## 4. Important Types & APIs

- The module is entirely private; it hooks into the engine movie player. No public UObject or Blueprint APIs are exported.

## 5. Typical usage patterns

- Enable the plugin alongside `WebMMedia`. Place your WebM startup movies in the usual Movies directory; the plugin registers a WebM-capable movie player during `PreLoadingScreen`.
- Configure loading screen movie playback via project settings (`Start-up Movie Settings`) as normal; WebM files will be handled by this plugin.

## 6. Version-specific notes (UE 5.7)

- Enabled by default. No explicit UE 5.7-specific notes found.

