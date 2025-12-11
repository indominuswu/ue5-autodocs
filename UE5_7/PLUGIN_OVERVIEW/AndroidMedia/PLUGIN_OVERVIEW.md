# Android Media Player Plugin Overview

## 1. What this plugin does
- Implements a Media Framework player using the Android Media library.
- Provides runtime playback, texture sampling, and platform integration for Android media sources.
- Supplies editor and factory support for creating Android media players/media sources.

## 2. Key Modules
- **AndroidMedia** (RuntimeNoCommandlet, PreLoadingScreen)
  - Role: Core media player implementation and platform codecs.
- **AndroidMediaEditor** (Editor)
  - Role: Editor-side asset factories (`AndroidFileMediaSourceFactory`) and settings exposure.
- **AndroidMediaFactory** (Editor, RuntimeNoCommandlet)
  - Role: Media player factory registration for Android targets.

## 3. Important Types & APIs
- `FAndroidMediaPlayer`
  - Role: Platform media player handling playback, tracks, and synchronization.
- `FAndroidMediaTextureSample`
  - Role: Texture sample implementation used by the renderer for decoded frames.
- `IAndroidMediaModule`
  - Role: Public interface for the media module used by factory registration.
- `UAndroidMediaSettings`
  - Role: Project settings for media playback behavior on Android.
- `UAndroidFileMediaSourceFactory`
  - Role: Editor factory for Android file-based media sources.

## 4. Typical usage patterns
- Enable the plugin (on by default) for Android projects needing media playback.
- Create media players/sources in the editor; Android-specific factory registers the player so existing Media Framework assets work on device.
- Adjust `AndroidMedia` settings in Project Settings for platform-specific playback tuning.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
