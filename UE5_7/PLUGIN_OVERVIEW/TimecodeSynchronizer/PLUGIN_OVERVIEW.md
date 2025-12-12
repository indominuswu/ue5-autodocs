# Timecode Synchronizer (Deprecated) Plugin Overview

## 1. What this plugin does

- Provides an asset-driven timecode synchronizer that becomes the engine TimecodeProvider once inputs align.
- Supports multiple synchronization modes (user offset, auto, auto-oldest) and sources (default provider, external provider, or input-derived).
- Marked deprecated; the uplugin description recommends migrating to TimedDataMonitor.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Editor asset/toolkit for configuring synchronizers that can drive the engine timecode provider at runtime.

## 3. Key Modules

- **TimecodeSynchronizer** (Runtime)
  - Role: Defines the synchronizer asset, sync modes, timecode/framerate enums, and runtime logic to become the active provider when inputs match.
- **TimecodeSynchronizerEditor** (Editor)
  - Role: Asset factory, editor toolkit, toolbar commands, and widgets for configuring and monitoring synchronizers.

## 4. Important Types & APIs

### `UTimecodeSynchronizer`

- Role: Asset representing inputs, offsets, and sync configuration; can drive the engine timecode provider when synchronized.
- Key enums: `ETimecodeSynchronizationSyncMode`, `ETimecodeSynchronizationTimecodeType`, `ETimecodeSynchronizationFrameRateSources` (all deprecated annotations).

### `UTimecodeSynchronizerProjectSettings`

- Role: Project-wide defaults for the synchronizer feature.

### Editor toolkit and widgets

- Role: `FTimecodeSynchronizerEditorToolkit` and Slate widgets (`STimecodeSynchronizerWidget`, `STimecodeSynchronizerSourceViewer/Viewport`) visualize inputs and allow editing.

## 5. Typical usage patterns

- Create a Timecode Synchronizer asset in the editor, add input sources, and set sync mode/offsets.
- Use the editor toolkit to monitor input readiness; when synchronized, the asset can set itself as the engine TimecodeProvider.
- New projects should prefer TimedDataMonitor; this plugin is kept for legacy content.

## 6. Version-specific notes (UE 5.7)

- Deprecated status is explicitly documented in code comments and the plugin description; no other UE 5.7-specific changes noted.
