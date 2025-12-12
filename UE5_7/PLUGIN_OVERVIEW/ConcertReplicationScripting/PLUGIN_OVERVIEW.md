# Concert Replication Scripting Plugin Overview

## 1. What this plugin does
- Exposes Concert Replication types to scripting (Blueprint) so automation can configure replication sessions and property lists.
- Provides editor UI and styles for scripting tools.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Supplies Blueprint nodes and editor UI/styles for configuring Concert replication scripting workflows.

## 3. Key Modules
- **ConcertReplicationScripting** (Runtime)  
  - Role: Blueprint library and helpers for working with Concert replication property chains and scripting interfaces.
- **ConcertReplicationScriptingEditor** (Editor)  
  - Role: Editor module with customizations, widgets, and styles for the scripting UI.

## 4. Important Types & APIs

### `UConcertReplicationBlueprintFunctionLibrary`
- Role: Blueprint-callable helper functions to work with Concert replication scripting (build property chains, configure replication).

### `FConcertPropertyChainWrapper` / `FConcertPropertyChainWrapperContainer`
- Role: Utility structs for representing property access chains when scripting replication.

## 5. Typical usage patterns
- Editor/automation: Use Blueprint nodes from `UConcertReplicationBlueprintFunctionLibrary` to build property lists and configure replication sessions programmatically. Editor widgets/styles from this plugin provide the scripting UI.

## 6. Version-specific notes (UE 5.7)
- No UE 5.7-specific notes called out; plugin is currently marked for scripting support only.
