# Chaos Outfit Asset Plugin Overview

## 1. What this plugin does

- Provides authoring tools for assembling outfit assets composed of Chaos cloth parts.
- Supplies dataflow nodes to query, merge, size, and configure outfit collections and cloth assets.
- Includes editor factories/definitions to create outfit assets and related schemas.

## 2. Key Modules

- **ChaosOutfitAssetDataflowNodes** (Runtime)  
  - Role: Dataflow nodes for manipulating outfit data (querying body parts, merging outfits, generating sized outfits).
- **ChaosOutfitAssetEngine** (Runtime)  
  - Role: Core runtime support for outfit assets and dataflow evaluation.
- **ChaosOutfitAssetEditor** (Editor)  
  - Role: Editor UI, asset definitions, commands, and factories for creating and editing outfit assets.

## 3. Important Types & APIs

### Dataflow nodes (runtime)
- `FMakeOutfitNode`, `FMakeSizedOutfitNode`, `FMergeOutfitsNode`, `FGetOutfitBodyPartsNode`, `FGetOutfitClothCollectionsNode`, `FSetOutfitClothCollectionNode`: build or query outfit compositions and cloth collections.
- `FGetOrMakeOutfitFromAssetNode`, `FGetOutfitAssetNode`, `FOutfitAssetTerminalNode`: access or produce outfit assets within a dataflow graph.
- `FFilterSizedOutfitNode`, `FSizedOutfitSourceAnyType`: helper nodes for handling sized variants.

### Editor-facing types
- `UOutfitAssetFactory`: creates outfit assets from the editor.
- `UAssetDefinition_OutfitAsset`: asset type registration for content browser integration.
- `FOutfitAssetEditorStyle`, `FOutfitEditorCommands`: styling and command bindings for the outfit editor experience.

## 4. Typical usage patterns

- Enable the plugin and create a new Outfit Asset via the factory/asset definition.
- Build outfit assembly graphs using the provided dataflow nodes to combine cloth assets, define body parts, and manage sized variants.
- Use editor tooling (styles/commands) to visualize and adjust outfit composition; integrate cloth collections through the dataflow nodes.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
