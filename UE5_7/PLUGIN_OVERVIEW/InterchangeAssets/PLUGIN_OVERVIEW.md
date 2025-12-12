# Interchange Framework Assets Plugin Overview

## 1. What this plugin does

- Supplies content/assets (base materials, shaders, and supporting data) used by the Interchange import framework.
- Supports runtime loading of those shared assets during import/export operations.
- Enabled by default because Interchange depends on its packaged assets.

## 2. Editor/Runtime surfaces

- User-facing: No - Content/dependency plugin providing base materials for Interchange; no direct editor workflow or API surface.

## 3. Key Modules

- **InterchangeAssets** (Runtime, PostConfigInit) — Loads and exposes shared assets packaged with the plugin.
- Dependency: `BaseMaterial` plugin is enabled to provide material assets referenced by Interchange pipelines.

## 4. Important Types & APIs

- The module primarily loads packaged content; no public UClass APIs are declared in the plugin source.

## 5. Typical usage patterns

- This plugin is consumed automatically by Interchange import workflows; ensure it stays enabled when using Interchange pipelines that rely on provided base materials/shaders.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific behavior noted; the plugin simply packages shared assets for the Interchange system.

