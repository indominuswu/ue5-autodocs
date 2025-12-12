# IOS TapJoy Advertising Provider Plugin Overview

## 1. What this plugin does

- Supplies a TapJoy advertising provider implementation for iOS builds.
- Integrates with the engine’s advertising interfaces to request/show ads through TapJoy.
- Disabled by default; intended for projects targeting TapJoy on iOS.

## 2. Editor/Runtime surfaces

- User-facing: Yes - iOS projects enable this advertising provider and configure TapJoy credentials so engine ad APIs can serve TapJoy placements.

## 3. Key Modules

- **IOSTapJoy** (Runtime, Default, IOS) — TapJoy platform integration for the advertising subsystem.

## 4. Important Types & APIs

- The plugin implements the provider inside the module code; no public UClass APIs are exposed.

## 5. Typical usage patterns

- Enable the plugin for iOS, configure TapJoy credentials in your project’s advertising settings, and route ad requests through the engine advertising API. The provider is registered at module startup.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific behavior noted; functionality is limited to iOS.

