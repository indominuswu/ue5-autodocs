# ZoneGraph Plugin Overview

## 1. What this plugin does
- Experimental AI navigation system built around “zone graphs” composed of lanes, tags, and zone shapes.
- Provides runtime storage, queries, and pathfinding over authored zone data instead of navmeshes.
- Includes an editor module for building zone graph data from `UZoneShapeComponent` geometry and a debug module for visualization.
- Supplies query/path utilities for locating lanes, advancing along lanes, and resolving links by tag filters.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Ships editor authoring/build/debug tools for zone graphs alongside runtime query and pathfinding APIs used by AI/navigation systems.

## 3. Key Modules
- **ZoneGraph** (Runtime): Core data types, storage, queries, pathfinding, and subsystem management.
- **ZoneGraphDebug** (Runtime): Rendering/visualization support for zone graph data.
- **ZoneGraphEditor** (Editor): Authoring tools, builders, and editor hooks for zone graph assets.
- **ZoneGraphTestSuite** (UncookedOnly): Automated tests for lane building and querying.

## 4. Important Types & APIs
- `UZoneGraphSubsystem` (TickableWorldSubsystem): Registers `AZoneGraphData` actors, builds storage via `FZoneGraphBuilder`, and exposes queries (`FindNearestLane`, `FindLaneOverlaps`, `GetLinkedLanes`, `AdvanceLaneLocation`, `GetLaneLength/Width/Tags`, tag lookups).
- `AZoneGraphData`: Actor holding `FZoneGraphStorage` (lanes, boundaries, tags) plus a `UZoneGraphRenderingComponent` for debug draw; receives `OnRegistered` callbacks when added to the subsystem.
- `UZoneShapeComponent`: Base component for authored shapes; feeds the builder to generate lanes with tag masks and connection restrictions.
- Data & query structs: `FZoneGraphLaneHandle`, `FZoneGraphLaneLocation`, `FZoneGraphLaneSection`, `FZoneGraphLinkedLane`, `FZoneGraphTagMask`, `FZoneGraphBuildSettings`.
- Pathfinding: `FZoneGraphAStarWrapper`, `FZoneGraphAStarNode`, and `FZoneGraphPathFilter` for A* over lanes; `ZoneGraphBVTree` for spatial queries.
- Delegates: `UE::ZoneGraphDelegates::OnZoneGraphDataBuildDone`, `OnZoneGraphTagsChanged`, `OnZoneGraphRequestRebuild`, and lane profile change notifications.

## 5. Typical usage patterns
- Author zone shapes in the editor using `UZoneShapeComponent`-derived actors; build data via the ZoneGraph editor tools to create `AZoneGraphData`.
- At runtime, acquire `UZoneGraphSubsystem` and query for lanes by bounds/tag filters, advance along lanes for movement, or run A* using lane handles.
- Use tag masks to constrain pathing and lane connections; listen to delegates for rebuilds or tag changes.
- Enable `ZoneGraphDebug` to visualize lanes and tags in the viewport for debugging.

## 6. Version-specific notes (UE 5.7)
- Plugin is marked experimental; no additional UE 5.7-specific notes beyond current source.
