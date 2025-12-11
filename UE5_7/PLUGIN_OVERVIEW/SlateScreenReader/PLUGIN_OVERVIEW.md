# SlateScreenReader Plugin Overview

## 1. What this plugin does
- Provides a screen reader framework for Slate to deliver vision accessibility (text-to-speech, announcements, accessible input).
- Wraps the base ScreenReader plugin with a Slate-focused engine subsystem and lifecycle management.
- Supports desktop platforms (Win64, Mac, Linux) and is disabled on server targets.

## 2. Key Modules
- **SlateScreenReader** (Runtime)
  - Role: Implements the Slate-facing screen reader runtime, registers with the ScreenReader plugin, and exposes activation/user management APIs.
  - Notable types: `USlateScreenReaderEngineSubsystem`, `FSlateScreenReaderModule`, `FSlateScreenReaderBuilder`.

## 3. Important Types & APIs
- `USlateScreenReaderEngineSubsystem` (UEngineSubsystem)
  - Role: Primary entry point for activating/deactivating the screen reader and registering users.
  - Key functions: `ActivateScreenReader()`, `DeactivateScreenReader()`, `RegisterUser(int32)`, `UnregisterUser(int32)`, `ActivateUser(int32)`, `DeactivateUser(int32)`, `IsScreenReaderActive()`, `IsUserRegistered(int32)`.
  - Usage: Provides BlueprintCallable access so gameplay or tooling code can drive accessibility workflows.
- `FSlateScreenReaderModule`
  - Role: Module bootstrap for the plugin, wiring Slate to the underlying ScreenReader implementation.
- `FSlateScreenReaderBuilder`
  - Role: Helper constructing the screen reader instance used by the subsystem.

## 4. Typical usage patterns
- Enable both `SlateScreenReader` and the base `ScreenReader` plugin in the project.
- From code or Blueprint, get `USlateScreenReaderEngineSubsystem::Get()` and call `ActivateScreenReader()` before registering users.
- Register one or more users (typically matching Slate user IDs), then `ActivateUser` to allow announcements.
- Request spoken feedback via `FScreenReaderAnnouncement` through the registered user objects (see subsystem header example comments for usage).
- Intended for accessibility features; not used on server builds.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
