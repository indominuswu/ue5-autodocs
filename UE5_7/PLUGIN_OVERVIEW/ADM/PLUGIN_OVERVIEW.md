# Audio Definition Model (ADM) Plugin Overview

## 1. What this plugin does
- Adds support for ADM spatialization output using WASAPI aggregate channels.
- Transmits spatial ADM metadata over OSC alongside audio.
- Provides spatialization settings and module hooks for audio devices.

## 2. Editor/Runtime surfaces
- User-facing: Yes - adds `UADMSpatializationSettings` and an ADM spatialization option selectable in project/platform audio settings for Win64; audio teams configure ADM/OSC output in editor audio device settings.

## 3. Key Modules
- **ADMSpatialization** (Runtime)
  - Role: Implements ADM spatialization plugin, settings, and OSC integration.

## 4. Important Types & APIs

### `UADMSpatializationSettings`
- Role: Configures ADM spatialization behavior (e.g., output mapping, OSC endpoints).

### `FADMDirectOutChannel` / `FADMSpatializationModule`
- Role: Channel mapping helpers and module entry for registering the spatialization factory.

## 5. Typical usage patterns
- Enable ADM plugin, select ADM spatialization in the project/platform audio settings.
- Configure `UADMSpatializationSettings` for channel layout and OSC targets.
- Use during playback to emit ADM-formatted spatial audio with accompanying metadata.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
