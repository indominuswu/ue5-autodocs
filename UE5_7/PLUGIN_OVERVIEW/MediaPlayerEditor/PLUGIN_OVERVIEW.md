# Media Player Editor Plugin Overview

## 1. What this plugin does
- Editor tooling for creating and editing `UMediaPlayer`, `UMediaPlaylist`, `UMediaTexture`, and Media Source assets.
- Provides dedicated asset editors with preview viewport, playlist timeline, playback controls, and media stats.
- Supplies Content Browser integration: factories for new media assets, asset type actions, and thumbnail renderers for sources.
- Adds details customizations and visualizers (e.g., `FMediaSoundComponentVisualizer`) tailored to media workflows.

## 2. Key Modules
- **MediaPlayerEditor** (Editor)
  - Role: Hosts the asset editors, details customizations, thumbnail/viewport widgets, and asset type actions for media assets.
  - Notable types: `FMediaPlayerEditorToolkit`, `FMediaPlaylistEditorToolkit`, `FMediaSourceEditorToolkit`, `FMediaSourceActions`, `FMediaTextureActions`, `UMediaPlayerEditorSettings`, `FMediaSoundComponentVisualizer`.

## 3. Important Types & APIs
### `FMediaPlayerEditorToolkit`
- Role: Main asset editor for `UMediaPlayer`; provides tabs for media preview, cache/status, overlay, output routing, and playlist inspection.
- Key functions: `Initialize` to open a player asset; tab registration for viewer, playlist, details, and stats panes.

### `FMediaPlaylistEditorToolkit`
- Role: Asset editor for `UMediaPlaylist` with track list, item details, and playback testing directly in-editor.
- Notes: Integrates with media player viewport and exposes playlist editing commands.

### `FMediaSourceEditorToolkit` / `FFileMediaSourceActions` / `FStreamMediaSourceActions`
- Role: Editors and asset type actions for source assets; expose media URI/path settings and validation.
- Key pieces: Custom detail panels (`FFileMediaSourceCustomization`, `FPlatformMediaSourceCustomization`) and thumbnail rendering (`FMediaSourceThumbnailRenderer`).

### `UMediaPlayerEditorSettings`
- Role: Stores editor preferences such as default media player to use for previews and playback behavior inside the editor.

### Slate widgets (prefixed `SMedia*`)
- Role: Viewer, timeline, overlay, stats, and details panels that make up the Media Player Editor UI (e.g., `SMediaPlayerEditorViewport`, `SMediaPlayerEditorPlaylist`, `SMediaPlayerSlider`).

## 4. Typical usage patterns
- Enable the plugin (Editor category) – it is on by default. Media assets in the Content Browser will use the custom editors.
- Create assets via Add/Import: Media Player, Media Playlist, Media Texture, File/Stream/Platform Media Sources.
- Double-click a Media Player to open the editor; use the viewport to preview playback, inspect media info, and manage playlists.
- Use asset actions to set thumbnail renders for sources and to open source/playlist editors directly.
- For audio visualization, the media sound component visualizer helps debug channel routing and levels in the editor viewport.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
