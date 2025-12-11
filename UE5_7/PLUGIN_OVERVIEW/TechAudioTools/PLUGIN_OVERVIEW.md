# TechAudioTools Plugin Overview

## 1. What this plugin does
- Experimental collection of audio tooling utilities, focused on MVVM viewmodels for audio components and MetaSound data inspection.
- Provides runtime and MetaSound-specific modules plus editor viewmodels for MetaSound editing workflows.
- Depends on MetaSound and ModelViewViewModel modules.

## 2. Key Modules
- **TechAudioTools** (Runtime, Experimental) – Core audio utilities and MVVM viewmodels (e.g., for `UAudioComponent`).
- **TechAudioToolsMetaSound** (Runtime, Experimental) – MetaSound-specific viewmodels and literal interfaces.
- **TechAudioToolsMetaSoundEditor** (Editor, Experimental) – Editor viewmodels and conversion helpers for MetaSound tooling.

## 3. Important Types & APIs
- `UAudioComponentViewModel` (MVVM viewmodel) – Wraps an `UAudioComponent`, exposes properties/actions to UI bindings; uses conversion helpers in `TechAudioToolsConversionFunctions`.
- MetaSound viewmodels: `UMetaSoundViewModel`, `UMetaSoundLiteralViewModel`, and conversion helpers (`MetaSoundViewModelConversionFunctions`) for binding MetaSound data to UI.
- Interfaces: `IMetaSoundLiteralInterface` for working with MetaSound literal values.

## 4. Typical usage patterns
- Enable alongside MetaSound to experiment with MVVM-driven audio/MetaSound editor tooling.
- Bind UI (UMG/MVVM) to `UAudioComponentViewModel` to inspect/control audio components in tools.
- Use MetaSound viewmodels in custom editor panels to surface graph data or literal parameters for debugging.

## 5. Version-specific notes (UE 5.7)
- Marked beta/experimental; no explicit UE 5.7-specific behavior beyond current interfaces.

