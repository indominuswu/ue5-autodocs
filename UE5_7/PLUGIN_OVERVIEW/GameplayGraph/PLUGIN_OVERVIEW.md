# Gameplay Graph Plugin Overview

## 1. What this plugin does
- Supplies a generic graph data model and common graph algorithms for gameplay features.
- Supports graph serialization, handles, vertices, and islands with incremental update helpers.
- Experimental utility module for gameplay systems needing custom graphs.

## 2. Key Modules
- **GameplayGraph** (Runtime) - Provides the graph data structures and algorithms.

## 3. Important Types & APIs
### `FGraph` / `FGraphVertex` / `FGraphHandle`
- Role: Core data structures for representing and referencing graph nodes and elements.

### `FGraphIsland`
- Role: Groups connected subgraphs for processing/partitioning.

### Algorithms (`Connectivity::ConnectedComponents`, `Search`)
- Role: Helpers for traversals and connectivity queries over the graph data.

### `FGraphDefaultSerialization`
- Role: Utilities for serializing graph state and performing incremental updates.

## 4. Typical usage patterns
- Include the module in gameplay systems that need lightweight graph storage (e.g., AI nav, state graphs).
- Construct `FGraph` instances, add vertices/edges, and run provided search/connectivity helpers.
- Serialize graphs using the default/incremental serializers when persisting or diffing data.

## 5. Version-specific notes (UE 5.7)
- Experimental module in 5.7; no explicit version-locked APIs noted.
