# SurfaceEffects Plugin Overview

## 1. What this plugin does
- Experimental surface-resolution system that maps physical surface context to custom enumerations.
- Uses data-table-driven rules to choose surface enums based on context (e.g., `EPhysicalSurface`).
- Provides a game instance subsystem to query results at runtime.

## 2. Key Modules
- **SurfaceEffects** (Runtime, Experimental) – Developer settings, rule assets, and the game instance subsystem for resolving surface enums.

## 3. Important Types & APIs
- `USurfaceEffectsSettings` (`UDeveloperSettings`) – Points to a data table of `FSurfaceEffectTableRow` entries mapping enum names to rules.
- `USurfaceEffectRule` (`UDataAsset`) – Base asset implementing `GetSurface` to return an enum value based on context.
- `FSurfaceEffectContextBase` – Context struct (primarily wraps `EPhysicalSurface`) passed to rules.
- `USurfaceEffectsSubsystem` (`UGameInstanceSubsystem`) – Provides templated `GetSurface<TEnum>` that looks up rules from the configured data table and returns `TSurfaceEffectResult<TEnum>`.

## 4. Typical usage patterns
- Enable the plugin and assign a data table in project settings; each row name should match the target enum type.
- Create assets derived from `USurfaceEffectRule` to encode surface selection logic (e.g., per physical surface).
- At runtime, retrieve the subsystem from the game instance and call `GetSurface` with your enum type and context; check `bSuccess` before using the result.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; no additional UE 5.7-specific behaviors noted.

