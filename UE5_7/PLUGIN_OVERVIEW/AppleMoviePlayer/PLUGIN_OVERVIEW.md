# Apple Movie Player Plugin Overview

## 1. What this plugin does
- Implements AVPlayer-based startup/loading movie playback for Apple platforms.
- Integrates with the engine movie player to show movies before the game finishes loading.

## 2. Key Modules
- **AppleMoviePlayer** (RuntimeNoCommandlet, PreLoadingScreen)
  - Role: Platform movie streaming implementation for iOS/macOS/tvOS.

## 3. Important Types & APIs
- `AppleMoviePlayer` module interface
  - Role: Exposes the platform movie streamer implementation.
- `FAppleMovieStreamer`
  - Role: Handles movie playback via AVPlayer for startup screens.

## 4. Typical usage patterns
- Enable the plugin (on by default) for Apple targets that need startup or loading movies.
- Configure startup movies in project settings; the engine routes playback through the Apple movie streamer with no additional setup.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
