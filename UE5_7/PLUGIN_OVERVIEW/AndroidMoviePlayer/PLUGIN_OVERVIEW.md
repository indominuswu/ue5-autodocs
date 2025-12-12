# Android Movie Player Plugin Overview

## 1. What this plugin does
- Provides Android platform startup movie playback using the Android Media library.
- Integrates with the engine movie player interface to show movies before the game fully loads.

## 2. Editor/Runtime surfaces
- User-facing: Yes - supplies the platform movie streamer (`FAndroidMovieStreamer`) used when developers configure startup/loading movies for Android builds.

## 3. Key Modules
- **AndroidMoviePlayer** (RuntimeNoCommandlet, PreLoadingScreen)
  - Role: Implements platform movie streaming for Android boot/loading movies.

## 4. Important Types & APIs
- `FAndroidMovieStreamer`
  - Role: Platform-specific movie streamer used by the movie player system.
- `AndroidMoviePlayer.h`
  - Role: Public entry point exposing the module implementation.

## 5. Typical usage patterns
- Enable the plugin (on by default) to allow startup/loading movies on Android.
- Place movie files in the expected project movie directory; engine movie player will route playback through `FAndroidMovieStreamer`.
- Configure startup movie lists in project settings; no additional Blueprint/API usage typically required.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
