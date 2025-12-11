# EOS Voice Chat Plugin Overview

## 1. What this plugin does
- Implements `IVoiceChat` integration for the EOS Voice service.
- Provides client-side voice chat using EOS SDK, including connection, capture, and playback.
- Disabled by default; enable when using EOS-backed voice chat.

## 2. Key Modules
- **EOSVoiceChat** (ClientOnlyNoCommandlet)  
  - Role: Voice chat implementation that bridges engine voice APIs to EOS.

## 3. Important Types & APIs

### `UpdateVoiceChatSettings`
- Role: Helper/settings type referenced by the module to configure voice chat behavior.
- Public Blueprint surface is minimal; voice features are accessed through the engine `IVoiceChat` interface.

## 4. Typical usage patterns
- Enable alongside other EOS plugins. Acquire the voice chat interface via `IVoiceChat::Get()` (EOS implementation becomes active).
- Configure EOS credentials and product IDs in online subsystem settings; join channels/sessions through standard voice chat APIs.
- Module is client-only; not used in dedicated server commandlets.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; overview reflects current source.
