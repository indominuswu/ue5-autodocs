# Playlists Plugin Overview

## 1. What this plugin does

- Adds Sequencer Playlists for preparing, queuing, and triggering level sequences on the fly during virtual production sessions.
- Provides playlist assets, items, and a player/subsystem to manage playback and transitions.
- Integrates with Sequencer UI to browse playlist items and trigger them during on-set workflows.

## 2. Key Modules

- **SequencerPlaylists** (Editor, Default)  
  - Role: Defines playlist assets/items, the runtime player/subsystem, and editor widgets for managing playlists.

## 3. Important Types & APIs

### Playlist assets and items

- `USequencerPlaylist`: Asset that holds an ordered list of playlist items.
- `USequencerPlaylistItem` / `USequencerPlaylistItem_Sequence`: Items referencing level sequences (and their movie scene sub-tracks/sections).

### Playback

- `USequencerPlaylistPlayer`: Drives playback of playlist items.
- `USequencerPlaylistsSubsystem`: Editor subsystem coordinating playlist execution and integration with Sequencer.

### Module access

- `ISequencerPlaylistsModule`: Entry point for registering/extending playlist features.

## 4. Typical usage patterns

- Enable the plugin and create a Sequencer Playlist asset; add `Sequence` items that point to `ULevelSequence` assets.
- Use the playlist player or subsystem to queue and trigger items during a virtual production session; items can be reordered or activated interactively.
- Leverage the editor widgets (tabs/panels provided by the module) to manage playlists while working in Sequencer.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
