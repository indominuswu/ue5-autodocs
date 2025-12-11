# ZoneGraph Annotations Plugin Overview

## 1. What this plugin does
- Adds annotation support on top of ZoneGraph, allowing lanes to carry dynamic tag overlays and metadata.
- Provides a world subsystem to register annotation components and combine their tag masks with zone data.
- Ships with sample disturbance annotations and Blueprint helpers; can contain content assets.
- Experimental and disabled by default; depends on the ZoneGraph runtime.

## 2. Key Modules
- **ZoneGraphAnnotations** (Runtime): Annotation subsystem, components, tag types, and sample annotations.

## 3. Important Types & APIs
- `UZoneGraphAnnotationSubsystem` (TickableWorldSubsystem): Manages registered annotations, maintains per-`AZoneGraphData` tag masks, and exposes combined annotation tags.
- `UZoneGraphAnnotationComponent`: Component that contributes annotation tag masks to the subsystem for associated zone data.
- `FZoneGraphAnnotationTagContainer`: Aggregates per-data annotation tag masks and combined static tags.
- `UZoneGraphAnnotationTestingActor`: Test actor for exercising annotation behavior.
- Disturbance annotations:
  - `UZoneGraphDisturbanceAnnotation`: Annotation class representing disturbances over lanes.
  - `UZoneGraphDisturbanceAnnotationBPLibrary`: Blueprint helpers to work with disturbance annotations.
- Module interface: `IZoneGraphAnnotationsModule` exposes standard module accessors.

## 4. Typical usage patterns
- Enable ZoneGraph and ZoneGraphAnnotations; place `UZoneGraphAnnotationComponent` on actors associated with `AZoneGraphData` to inject additional tag masks.
- Access `UZoneGraphAnnotationSubsystem` to query combined annotation tags per lane/data handle.
- Use disturbance annotation classes or extend your own to mark temporary influences on lanes (e.g., hazards, reservations).
- For testing, use `UZoneGraphAnnotationTestingActor` and Blueprint library helpers to validate tag application.

## 5. Version-specific notes (UE 5.7)
- Marked experimental; no additional UE 5.7-specific behavior noted in the source.
