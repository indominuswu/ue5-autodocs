# Enhanced Input Plugin Overview

## 1. What this plugin does
- Modern input handling system with contextual mapping contexts and gameplay/input subsystems.
- Supports dynamic rebinding, player-mappable keys, and input actions with modifiers/triggers.
- Provides editor tooling for visualization and Blueprint nodes for runtime setup.
- Enabled by default in UE 5.7 projects.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Runtime subsystems/components/Blueprint nodes for enhanced input plus editor visualization/settings support.

## 3. Key Modules
- **EnhancedInput** (Runtime) — Core runtime system (subsystems, mappings, actions).
- **InputBlueprintNodes** (UncookedOnly) — Blueprint nodes for input workflows.
- **InputEditor** (Editor) — Editor visualization, settings, and asset support.

## 4. Important Types & APIs

### Runtime subsystems and components
- `UEnhancedInputLocalPlayerSubsystem` / `UEnhancedInputWorldSubsystem` / `UEnhancedInputSubsystem`: Manage active mapping contexts per player or world and route input to actions.
- `UEnhancedInputComponent`: Drop-in replacement for `UInputComponent` that binds `UInputAction` objects to gameplay functions.
- `UEnhancedInputUserSettings`: Stores user preferences/rebindings; works with `UPlayerMappableKeySettings`.
- `UEnhancedInputPlatformSettings`: Platform-specific input settings; `UEnhancedInputDeveloperSettings` configures defaults at project level.
- `UPlayerMappableKeySettings` / `UPlayerMappableInputConfig`: Declare which keys can be remapped and expose metadata for UI.

### Blueprint/utility APIs
- `UEnhancedInputLibrary` and companion Blueprint nodes: Add/remove mapping contexts, query action values, and apply player mappable key changes.
- Tests/mock classes (`UMockedEnhancedInputSubsystem`, etc.) exist for validation.

### Editor tools
- `UEnhancedInputEditorSubsystem`, `UEnhancedInputEditorSettings`, and project settings for editor visualization.
- Input Editor module registers factories, visualization, and property customization for mapping contexts and actions.

## 5. Typical usage patterns
- Create `UInputAction` and `UInputMappingContext` assets in the editor; configure triggers/modifiers and optionally mark mappings as player-mappable with `UPlayerMappableKeySettings`.
- In runtime code/Blueprints, add mapping contexts to `UEnhancedInputLocalPlayerSubsystem` (e.g., in `BeginPlay`) and bind actions on an `UEnhancedInputComponent`.
- Use `UEnhancedInputUserSettings` to save/load remappings and expose UI for key rebinding.
- For editor tooling, adjust defaults in Enhanced Input project settings; use visualization tools from the Input Editor module.

## 6. Version-specific notes (UE 5.7)
- Enabled by default in UE 5.7 projects; no additional 5.7-specific notes surfaced from source.
