# UMG Viewmodel for UMG Preview Plugin Overview

## 1. What this plugin does

- Extends the UMG Widget Preview tooling to understand MVVM viewmodels.
- Provides styling and widget extensions so previewed widgets can display MVVM data in the designer.
- Disabled by default; used in conjunction with the main MVVM plugin for design-time preview.

## 2. Key Modules

- **ModelViewViewModelPreview** (Editor) — UMG preview integration, styling, and panels for MVVM sources.

## 3. Important Types & APIs

- `FMVVMWidgetPreviewExtension` — hooks MVVM data into the UMG preview pipeline.
- `SMVVMPreviewSourcePanel` — editor panel for inspecting preview data sources.
- `FMVVMWidgetPreviewStyle` — style definitions for the preview UI.

## 4. Typical usage patterns

- Enable alongside ModelViewViewModel when working in the UMG designer; open Widget Blueprint preview to visualize bindings.
- Use the preview source panel to inspect which viewmodels and bindings are active in the preview session.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes; functionality is limited to editor preview support.
