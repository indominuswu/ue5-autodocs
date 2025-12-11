# Engine Asset Definitions Plugin Overview

## 1. What this plugin does

- Registers engine-provided asset definitions for use in the Content Browser/asset tools.
- Enabled by default; supplies definitions for core asset types.

## 2. Key Modules

- **EngineAssetDefinitions** (Editor, PostEngineInit)  
  - Role: Provides engine-level `UAssetDefinition` classes and registers them with asset tooling.

## 3. Typical usage patterns

- Keep enabled to ensure engine asset types have proper actions/metadata in the Content Browser.

## 5. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted.
