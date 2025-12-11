# Blueprint Material and Texture Nodes Plugin Overview

## 1. What this plugin does

- Adds editor-only Blueprint nodes to read textures/render targets and to create/modify Material Instance Constants.
- Useful for tooling and editor automation that needs access to texture data or dynamic MIC creation without C++.

## 2. Key Modules

- **BlueprintMaterialTextureNodes** (UncookedOnly, PreLoadingScreen)  
  - Role: Blueprint function library providing material/texture utility nodes.  
  - Notable types: `UBlueprintMaterialTextureNodesBPLibrary`, module entry `FBlueprintMaterialTextureNodesModule`.

## 3. Important Types & APIs

- `UBlueprintMaterialTextureNodesBPLibrary`: Blueprint functions for reading textures/render targets and manipulating Material Instance Constants (e.g., create/edit parameters). (All functions are editor-only.)  
- Module setup is minimal beyond registering the library.

## 4. Typical usage patterns

- Enable the plugin in editor builds.  
- Use the provided Blueprint nodes to sample texture data or create/modify MIC assets as part of editor tools or automation scripts.

## 5. Version-specific notes (UE 5.7)

- No explicit 5.7-specific changes noted; functionality reflects current source.
