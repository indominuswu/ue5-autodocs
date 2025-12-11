# Voice Chat Interface Plugin Overview

## 1. What this plugin does

- Declares the engine’s modular voice chat interfaces used by platform-specific implementations (e.g., EOS voice chat).
- Defines channel configuration, positional voice settings, and result/error handling shared across providers.
- Client-only module; intended to be consumed by other voice chat providers or game code via the modular feature system.

## 2. Key Modules

- **VoiceChat** (ClientOnly)  
  - Role: Exposes `IVoiceChat`/`IVoiceChatUser` interfaces and shared result/error types (`FVoiceChatResult`, `EVoiceChatChannelType`, attenuation models).

## 3. Important Types & APIs

### `IVoiceChat` / `IVoiceChatUser`

- Role: Modular feature interfaces for connecting, logging in, and managing voice chat users/channels.
- Key operations: Initialize/uninitialize the voice system, login/logout users, join/leave channels (positional or non-positional), set 3D channel properties (`FVoiceChatChannel3dProperties`), mute/unmute, volume control, and device selection.
- Access: Usually via `IVoiceChat::Get()` / `IVoiceChat::GetVoiceChat()` using the modular feature name.

### Result/error helpers

- `FVoiceChatResult`/`EVoiceChatResult::Type` encapsulate provider-specific error codes and categories (see `VoiceChatResult.h`/`VoiceChatErrors.h`).

### Channel/attenuation enums

- `EVoiceChatChannelType` (NonPositional, Positional, Echo) and `EVoiceChatAttenuationModel` (None, InverseByDistance, LinearByDistance, ExponentialByDistance) drive how providers configure spatialization.

## 4. Typical usage patterns

- Enable this plugin plus a concrete provider (e.g., EOSVoiceChat). On client startup, obtain `IVoiceChat`, call `Initialize()`, then login users and join channels as needed.
- Configure positional channels using `FVoiceChatChannel3dProperties` to set attenuation and distance ranges.
- Handle `FVoiceChatResult` values from API calls for error reporting and recovery (device changes, reconnects, etc.).

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
