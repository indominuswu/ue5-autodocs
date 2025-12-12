# Field System Plugin Overview

## 1. What this plugin does
- Editor support for creating and managing Field System assets used by Chaos field simulations.
- Adds asset type actions, factories, and actor factories for Field System assets.
- Provides editor styling and commands for Field System tooling.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Field System asset and actor factories plus editor commands let users create and place Field System assets for Chaos simulations.

## 3. Key Modules
- **FieldSystemEditor** (Editor)
  - Role: Registers Field System asset factories, actor factories, and editor commands/styles.
  - Notable types: `FAssetTypeActions_FieldSystem`, `UFieldSystemFactory`, `UActorFactoryFieldSystem`, `FFieldSystemEditorModule`, `FFieldSystemEditorStyle`.

## 4. Important Types & APIs

### `FAssetTypeActions_FieldSystem`
- Role: Asset action handler enabling Field System asset creation and editing in the content browser.

### `UFieldSystemFactory`
- Role: Factory for creating new Field System assets.

### `UActorFactoryFieldSystem`
- Role: Allows placing Field System actors into levels from the editor.

### `FFieldSystemEditorModule` / `FFieldSystemEditorCommands`
- Role: Module and command definitions that bind Field System editor tools and menu entries.

## 5. Typical usage patterns
- Enable the plugin (Geometry category) to author Field System assets for Chaos simulations.
- Create Field System assets via the content browser using the provided factory; place them in levels with the actor factory.
- Use editor commands and styles registered by the module to work with Field System-specific tooling.

## 6. Version-specific notes (UE 5.7)
- Marked beta in 5.7; no additional version-specific behaviors were identified in the current source.

