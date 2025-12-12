# Variant Manager Content Plugin Overview

## 1. What this plugin does
- Supplies runtime and editor asset types that store variant data for the Variant Manager tool.
- Defines Level Variant Sets, Variants, bindings, property value types, and a Switch Actor.
- Provides factories, customizations, and asset definitions for creating and editing variant assets in the editor.
- Beta and enabled by default when installed.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime variant assets and Switch Actor plus editor factories/customizations for variant editing.

## 3. Key Modules
- **VariantManagerContent** (Runtime)
  - Role: Core asset classes (`LevelVariantSets`, `VariantSet`, `Variant`, `VariantObjectBinding`, `PropertyValue*`, `SwitchActor`), runtime activation helpers, module bootstrap.
- **VariantManagerContentEditor** (Editor)
  - Role: Asset factories and customizations (`VariantManagerFactoryNew`, `LevelVariantSetsActorFactory`, `SwitchActorFactory`), asset definitions, editor logging and integration.

## 4. Important Types & APIs
### `ULevelVariantSets` / `AVariantManagerContent` assets
- Role: Container asset for variant sets and variants; owns variant bindings and director logic (`LevelVariantSetsFunctionDirector`).

### `UVariantSet`, `UVariant`, `UVariantObjectBinding`
- Role: Organize variants and bind them to scene actors/components with captured properties or function calls.
- Key properties: display text, thumbnail handling (`ThumbnailGenerator`), captured bindings list.

### `UPropertyValue` and subclasses (`PropertyValueColor`, `PropertyValueMaterial`, `PropertyValueOption`, `PropertyValueSoftObject`)
- Role: Store captured property data for playback when activating variants.

### `ALevelVariantSetsActor`
- Role: Actor that references a `ULevelVariantSets` asset and exposes activation controls at runtime/Blueprint.

### `ASwitchActor`
- Role: Actor that switches between child options, commonly driven by variants.

## 5. Typical usage patterns
- Enable the plugin (automatically enabled with Variant Manager).
- Create a `LevelVariantSets` asset; place an `ALevelVariantSetsActor` in the level pointing to it.
- Add `UVariantSet`/`UVariant` entries, capture property values or function calls for target actors/components.
- Use the Variant Manager editor to author data; at runtime call into `ALevelVariantSetsActor` or Blueprint to switch variants, optionally using `ASwitchActor` for mesh swaps.

## 6. Version-specific notes (UE 5.7)
- Marked beta in the `.uplugin`.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
