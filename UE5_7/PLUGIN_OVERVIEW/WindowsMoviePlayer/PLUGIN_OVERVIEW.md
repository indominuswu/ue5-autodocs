# Windows Movie Player Plugin Overview

## 1. What this plugin does

- Provides a Media Foundation-based movie player for Windows startup/loading movies.
- Registers during `PreLoadingScreen` to play WMV/MP4 (Media Foundation) content on Win64.

## 2. Key Modules

- **WindowsMoviePlayer** (RuntimeNoCommandlet)
  - Role: Integrates Windows Media Foundation with the engine movie player pipeline; Win64-only.

## 3. Important Types & APIs

- Public surface is minimal (`WindowsMoviePlayer.h`); the module hooks into the engine movie player without exposing additional UObject APIs.

## 4. Typical usage patterns

- Enabled by default on Win64. Place movie files in the project Movies directory and configure startup movies in project settings; playback uses this plugin?s Media Foundation path.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; behavior aligns with existing Media Foundation integration.
