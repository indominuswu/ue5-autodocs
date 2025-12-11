# Paper2D Plugin Overview

## 1. What this plugin does

- Provides core 2D asset types (sprites, flipbooks, tile sets, tile maps, spline-based terrain) and runtime components to render and animate them.
- Ships editor tooling for creating/editing sprites, flipbooks, tile sets/maps, and grouped sprites, plus content browser integrations and asset factories.
- Includes importers for sprite sheets and Tiled (.tmx/.json) tile maps to quickly bring external 2D content into UE.
- Offers optional editor snapping helpers for planar 2D workflows (SmartSnapping module).

## 2. Key Modules

- **Paper2D** (Runtime, PreDefault)  
  - Role: Core 2D asset definitions and runtime components for sprites, flipbooks, tile maps, grouped sprites, and 2D terrain; exposes Blueprint utilities and plugin runtime settings.  
  - Notable types: `UPaperSprite`, `UPaperFlipbook`, `UPaperTileMap`, `UPaperTileSet`, `UPaperSpriteComponent`, `UPaperFlipbookComponent`, `UPaperTileMapComponent`, `UPaperTerrainComponent`, `UPaperRuntimeSettings`, `UPaperSpriteBlueprintLibrary`, `UTileMapBlueprintLibrary`, `APaperCharacter` and related actor shells.

- **Paper2DEditor** (Editor, Default)  
  - Role: Asset editors, factories, asset type actions, content browser extensions, viewport/editor UI for sprites, flipbooks, tile sets/maps, grouped sprites, terrain, and atlas tools.  
  - Notable types: `FPaper2DEditorModule`, asset factories (`PaperSpriteFactory`, `PaperFlipbookFactory`, `PaperTileMapFactory`, `PaperTileSetFactory`, `PaperSpriteActorFactory`, `PaperFlipbookActorFactory`), editor panels/viewports, importer settings (`PaperImporterSettings`), style/commands setup.

- **PaperSpriteSheetImporter** (Editor, Default)  
  - Role: Imports sprite sheets into Paper2D sprites/flipbooks using built-in factories.

- **PaperTiledImporter** (Editor, Default)  
  - Role: Imports Tiled map exports; parses tile sets/layers/objects and creates `UPaperTileMap`, tile sets, and textures; supports reimporting.

- **SmartSnapping** (Editor, PostEngineInit)  
  - Role: Adds planar constraint snapping policy (`FPlanarConstraintSnapPolicy`) to editor transform snapping for 2D workflows.

## 3. Important Types & APIs

### `UPaperSprite`

- Role: Core sprite asset storing texture regions, collision domain, sockets, per-pixel geometry, materials, and atlas membership.
- Key properties: `SourceTexture`/`AdditionalSourceTextures`, `DefaultMaterial`/`AlternateMaterial`, `SpriteCollisionDomain`, `PixelsPerUnrealUnit`, `Sockets`.
- Key functions: geometry and collision rebuild helpers (`RebuildData`, `RebuildCollisionData`, `RebuildRenderData`), socket queries (`FindSocket`, `QuerySupportedSockets`), texture-to-pivot conversion helpers, material accessors (`GetMaterial`, `GetNumMaterials`).

### `UPaperFlipbook`

- Role: Flipbook (2D animation) composed of ordered sprite keyframes with per-frame durations.
- Key properties: `FramesPerSecond`, `KeyFrames`, `DefaultMaterial`, `CollisionSource`.
- Key functions (BlueprintCallable): `GetNumFrames`, `GetTotalDuration`, `GetSpriteAtTime`, `GetSpriteAtFrame`, `GetKeyFrameIndexAtTime`, socket queries (`FindSocket`, `HasAnySockets`, `DoesSocketExist`, `QuerySupportedSockets`).

### `UPaperFlipbookComponent`

- Role: Scene component that plays flipbooks at runtime; handles rendering, collision, and replication.
- Key properties: `SourceFlipbook`, `PlayRate`, `bLooping`, `SpriteColor`.
- Key functions/events (Blueprint): `SetFlipbook`, `Play`/`PlayFromStart`, `Reverse`/`ReverseFromEnd`, `Stop`, `SetPlaybackPosition`/`SetPlaybackPositionInFrames`, `SetLooping`, `SetPlayRate`, `GetFlipbookLength`/`GetFlipbookLengthInFrames`, `GetFlipbookFramerate`, `SetSpriteColor`; multicast `OnFinishedPlaying`.

### `UPaperSpriteComponent`

- Role: Scene component for rendering a single sprite with collision support.
- Key properties: `SourceSprite`, `SpriteColor`.
- Key functions (Blueprint): `SetSprite`, `GetSprite`, `SetSpriteColor`; socket queries through overridden `HasAnySockets`/`GetSocketTransform`.

### `UPaperTileMapComponent`

- Role: Scene component for rendering/editing tile maps (EarlyAccessPreview); owns or references a `UPaperTileMap`.
- Key functions (Blueprint): `CreateNewTileMap`, `SetTileMap`, `GetMapSize`, `GetTile`, `SetTile`, `ResizeMap`, `AddNewLayer`, `SetTileMapColor`, `SetLayerColor`, `SetDefaultCollisionThickness`, `SetLayerCollision`, `RebuildCollision`, `GetTileCornerPosition`/`GetTileCenterPosition`/`GetTilePolygon`; `OwnsTileMap`/`MakeTileMapEditable`.

### `UPaperTerrainComponent` and `UPaperTerrainSplineComponent`

- Role: Experimental spline-based 2D terrain renderer; instances sprite geometry along a spline using `UPaperTerrainMaterial` rules.
- Key properties: `TerrainMaterial`, `RandomSeed`, `SegmentOverlapAmount`, `SpriteCollisionDomain`, `CollisionThickness`.
- Key functions: `SetTerrainColor`; internal spline hooks (`OnSplineEdited`, segment generation/rebuild).

### `APaperCharacter`

- Role: `ACharacter` variant that uses a `UPaperFlipbookComponent` for visuals; `GetSprite()` exposes the flipbook component.

### `UTileMapBlueprintLibrary`

- Role: Blueprint utility library for tile info; functions: `GetTileUserData`, `GetTileTransform`, `BreakTile`, `MakeTile`.

### `UPaperSpriteBlueprintLibrary`

- Role: UI helper to convert a sprite to a `FSlateBrush` (`MakeBrushFromSprite`) for UMG/Slate widgets.

### `UPaperRuntimeSettings` (config `Engine`)

- Role: Plugin-wide toggles. Properties: `bEnableSpriteAtlasGroups` (experimental atlasing), `bEnableTerrainSplineEditing` (experimental terrain authoring; editor restart required), `bResizeSpriteDataToMatchTextures` (auto-rescale sprite-authored data when source textures change).

### Editor-facing factories & tooling (Paper2DEditor)

- Asset factories: `PaperSpriteFactory`, `PaperFlipbookFactory`, `PaperTileMapFactory`, `PaperTileSetFactory`, plus actor factories/brokers for sprite/flipbook actors.
- Asset editors/viewports: sprite, flipbook, tile set, tile map, grouped sprite, and terrain editors; custom viewport/client code (`SPaperEditorViewport`, `PaperEditorViewportClient`).
- Importers: `PaperImporterSettings` governs slicing/extraction; PaperSpriteSheetImporter handles sprite sheets; PaperTiledImporter handles Tiled JSON/TMX (tile sets, layers, object layers, collision, properties, reimport support).
- Asset type actions and thumbnails for sprites/flipbooks/tile sets; content browser and level editor menu extensions.

### `FPlanarConstraintSnapPolicy` (SmartSnapping)

- Role: Editor snapping policy that constrains translation/rotation/scale to a plane; toggleable via the snapping system to aid 2D layout.

## 4. Typical usage patterns

- **Editor workflows**  
  - Enable Paper2D (enabled by default). Create sprites from textures or sprite sheets via the Paper2D sprite/sheet importers.  
  - Build flipbooks from sprite sequences; edit via the Flipbook Editor.  
  - Create tile sets and tile maps; edit maps with the tile map editor (early access). Import Tiled exports through the Paper Tiled Importer to generate maps/tile sets/textures with reimport support.  
  - Author spline-based 2D terrain (experimental) when `bEnableTerrainSplineEditing` is enabled in `PaperRuntimeSettings`.  
  - Use SmartSnapping to constrain transforms to a plane for 2D scene editing.

- **Runtime usage**  
  - Add `UPaperSpriteComponent` for static sprites, or `UPaperFlipbookComponent` for animated sprites; drive playback with Blueprint nodes (`Play`, `SetFlipbook`, `SetPlaybackPosition`, `SetLooping`, etc.).  
  - Use `APaperCharacter` as a 2D-friendly character base with a built-in flipbook component.  
  - Place `APaperTileMapActor`/`UPaperTileMapComponent` for tile map rendering; modify tiles at runtime with `SetTile`, `ResizeMap`, `AddNewLayer`, and rebuild collision when needed.  
  - Apply `UPaperTerrainComponent` with an associated spline for 2D terrain rendering; adjust colors and collision settings per component.  
  - Use Blueprint libraries for utility (`UTileMapBlueprintLibrary::BreakTile`/`MakeTile`, `GetTileUserData`, `UPaperSpriteBlueprintLibrary::MakeBrushFromSprite` for UI brushes).

## 5. Version-specific notes (UE 5.7)

- Tile map component is marked `EarlyAccessPreview`; terrain components are marked `Experimental`, consistent with prior versions.  
- `UPaperRuntimeSettings` exposes experimental toggles for atlas groups and terrain spline editing.  
- No explicit UE 5.7-only changes or deprecations are called out in code comments; this overview reflects the current 5.7 source state.
