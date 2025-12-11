# Level Sequence Navigator Bridge Plugin Overview

## 1. What this plugin does
- Bridges Level Sequence assets into the Sequence Navigator tooling.
- Provides a tool provider that exposes Level Sequence navigation within the Sequence Navigator UI.
- Experimental editor-only integration enabled by default.

## 2. Key Modules
- **LevelSequenceNavigatorBridge** (Editor) - Registers navigation tool provider for Level Sequences.

## 3. Important Types & APIs
### `FLevelSequenceNavigationToolProvider`
- Role: Supplies Sequence Navigator with Level Sequence-specific navigation and filtering logic.

### `FLevelSequenceNavigatorBridgeModule`
- Role: Module startup that registers the provider with Sequence Navigator on load.

## 4. Typical usage patterns
- Enable alongside `LevelSequenceEditor` and `SequenceNavigator`.
- Open the Sequence Navigator panel; Level Sequence entries become navigable via the bridge provider.

## 5. Version-specific notes (UE 5.7)
- Experimental plugin in 5.7; no additional version-specific notes found.
