# Windows Movie Player Plugin Overview

## 1. What this plugin does

- Provides a Media Foundation-based movie player for Windows startup/loading movies.
- Registers during `PreLoadingScreen` to play WMV/MP4 (Media Foundation) content on Win64.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Startup/loading movie player for Win64 using Media Foundation; projects rely on it to play configured startup movies.

## 3. Key Modules

- **WindowsMoviePlayer** (RuntimeNoCommandlet)
  - Role: Integrates Windows Media Foundation with the engine movie player pipeline; Win64-only.

## 4. Important Types & APIs

- Public surface is minimal (`WindowsMoviePlayer.h`); the module hooks into the engine movie player without exposing additional UObject APIs.

## 5. Typical usage patterns

- Enabled by default on Win64. Place movie files in the project Movies directory and configure startup movies in project settings; playback uses this plugin?s Media Foundation path.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; behavior aligns with existing Media Foundation integration.

