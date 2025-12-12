# Bink Media Plugin Overview

## 1. What this plugin does

- Integrates Bink as a media player for video playback inside Unreal.
- Supplies Bink-backed media textures, players, and Blueprint helpers plus editor factories for creating assets.
- Adds project settings for configuring Bink playback behavior.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides Bink media player/texture assets, Blueprint helpers, and editor factories/settings for video playback.

## 3. Key Modules

- **BinkMediaPlayer** (Runtime)  
  - Role: Core Bink player, media textures, streaming logic, and Blueprint helper library.
- **BinkMediaPlayerEditor** (Editor)  
  - Role: Editor toolkit, asset factories, and customization for Bink media players/textures.

## 4. Important Types & APIs

- `FBinkMediaPlayer`: Core runtime player implementation for Bink streams.
- `UBinkMediaTexture`, `FBinkMediaTextureResource`: Render Bink video frames to textures.
- `UBinkFunctionLibrary`: Blueprint-callable helpers for Bink playback.
- `UBinkMoviePlayerSettings`: Project settings controlling playback and decoding behavior.
- Factories and editor UI: `UBinkMediaPlayerFactory`, `UBinkMediaPlayerFactoryNew`, `UBinkMediaTextureFactoryNew`, `FBinkMediaPlayerEditorToolkit`, `FBinkMediaPlayerEditorCommands`.

## 5. Typical usage patterns

- Enable the plugin to register Bink as a media backend.
- Create Bink media player/texture assets via the Content Browser factories or convert existing media sources to Bink.
- In Blueprints or code, use `UBinkFunctionLibrary` and `FBinkMediaPlayer` to open and control Bink movie playback, binding textures to UI or materials.
- Configure defaults under Project Settings -> Plugins -> Bink Movie Player (`UBinkMoviePlayerSettings`).

## 6. Version-specific notes (UE 5.7)

- Disabled by default; intended for projects licensed to use Bink.
- No explicit UE 5.7-specific notes found.
