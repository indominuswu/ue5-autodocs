# Image Sequence Media Player Plugin Overview

## 1. What this plugin does

- Provides a media player for image sequences (EXR and other formats) with caching tuned for large frame sets.
- Supplies runtime playback support plus editor factories to author `ImgMediaSource` assets.
- Includes GPU-accelerated EXR reading on Win64 and platform-wrapped OpenEXR support.
- Marked beta; the legacy playback component is deprecated in favor of Media Plate.

## 2. Key Modules

- **ImgMedia** (RuntimeNoCommandlet, Default) — Core image-sequence reader, caching, scheduling.
- **ImgMediaEngine** (RuntimeNoCommandlet, PreDefault) — Playback helpers, deprecated component bridge to actors.
- **ImgMediaFactory** (RuntimeNoCommandlet & Editor, PostEngineInit) — Asset factories and settings exposure.
- **ImgMediaEditor** (Editor, PostEngineInit) — Editor widgets and details customization for media sources.
- **OpenExrWrapper** (RuntimeNoCommandlet, PostEngineInit, Mac/Win64) — Platform OpenEXR wrapper.
- **ExrReaderGpu** (Runtime, PostConfigInit, Win64) — GPU decoding path for EXR sequences.

## 3. Important Types & APIs

### `UImgMediaSource`

- Role: Media source asset describing an image-sequence path, filename patterns, proxy/LOD schemes, and frame rate controls.
- Key properties: sequence path/proxies, frame rate override, mip-mapping and cache hints.

### `UImgMediaSettings`

- Role: Project-wide settings driving global cache sizes, thread counts, throttling, and path resolution for the Img Media pipeline.
- Notable members: cache size controls, tick timing, proxy discovery flags.

### `UDEPRECATED_ImgMediaPlaybackComponent`

- Role: Legacy actor component that bound image sequence playback to scene components; kept for backward compatibility and marked deprecated in favor of Media Plate.

### Factories & editor helpers

- `UImgMediaSourceFactory` / `UImgMediaSourceFactoryNew`: Editor factories that create `UImgMediaSource` assets and wire default options.
- `UImgMediaProcessEXROptions`: Options object used by EXR import/processing tools in the editor module.

## 4. Typical usage patterns

- Editor: Create an **Img Media Source** asset, point it at a numbered EXR/PNG sequence, and reference it from a **Media Player** or **Media Plate**. Configure proxies and frame rates in the asset or via project settings.
- Runtime: Play the source through a `UMediaPlayer` (or Media Plate) to drive a `UMediaTexture`. Global playback/cache tuning comes from `UImgMediaSettings`.
- GPU EXR path: On Win64, enabling GPU decoding (`ExrReaderGpu`) improves throughput for large frames.

## 5. Version-specific notes (UE 5.7)

- `UDEPRECATED_ImgMediaPlaybackComponent` is still present but flagged deprecated (message references 5.3); Media Plate is recommended.
- No other explicit UE 5.7-only notes found; overview reflects the current plugin state in this source tree.

