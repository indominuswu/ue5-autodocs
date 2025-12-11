# Subtitles and Closed Captions Plugin Overview

## 1. What this plugin does
- Experimental runtime for displaying subtitles and closed captions as standalone content.
- Provides world/audio subsystems, developer settings, and Blueprint utilities for queuing subtitle assets.
- Includes uncooked editor support for authoring/testing subtitle assets and widgets.

## 2. Key Modules
- **SubtitlesAndClosedCaptions** (Runtime, Win64) – Core subtitle playback, subsystems, and Blueprint API.
- **SubtitlesAndClosedCaptionsEditor** (UncookedOnly) – Editor-facing helpers for testing and asset support.

## 3. Important Types & APIs
- `USubtitlesSettings` (`UDeveloperSettings`) – Selects the subtitle widget class (`SubtitleWidgetToUse`) with a stored default fallback.
- `USubtitlesSubsystem` (`UWorldSubsystem`) – Manages subtitle state per world.
- `USubtitlesAudioSubsystem` (`UAudioEngineSubsystem`) – Handles audio-layer integration separate from world lifetime.
- `USubtitlesBlueprintFunctionLibrary` – Blueprint-callable helpers to queue/stop subtitles from assets or struct data (`QueueSubtitlesFromAsset`, `QueueSubtitle`, `StopAllSubtitles`, `ReplaceSubtitleWidget`, etc.).

## 4. Typical usage patterns
- Enable the plugin and choose a subtitle widget in project settings.
- In Blueprints, call `QueueSubtitlesFromAsset` or `QueueSubtitle` to trigger playback; use `StopSubtitle`/`StopAllSubtitles` to clear.
- Swap the active widget at runtime with `ReplaceSubtitleWidget` to change presentation.
- Use uncooked editor support to preview widgets and subtitle assets.

## 5. Version-specific notes (UE 5.7)
- Plugin is marked experimental; no explicit UE 5.7-specific notes beyond current APIs.

