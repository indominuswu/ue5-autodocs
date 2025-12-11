# Interchange OpenVDB Plugin Overview

## 1. What this plugin does

- Adds an Interchange translator for OpenVDB volume files.
- Editor-only module that plugs into Interchange import flows to parse volume data.
- Experimental, hidden, and disabled by default.

## 2. Key Modules

- **InterchangeOpenVDBImport** (Editor, Default) — Implements the OpenVDB translator and hooks into Interchange pipelines.
- Dependency: `Interchange` runtime framework.

## 3. Important Types & APIs

### `UInterchangeOpenVDBTranslator`

- Role: Interchange translator for `.vdb` sources; implements `CanImportSourceData`, `Translate`, and settings plumbed through `UInterchangeVolumeTranslatorSettings`.
- Uses an internal implementation helper to parse VDB content and populate node containers.

### `UInterchangeVolumeTranslatorSettings`

- Role: Shared volume translator settings object (defined in the Interchange runtime) used here to configure import options for VDB data.

## 4. Typical usage patterns

- Enable the plugin in editor builds alongside Interchange. Choose the OpenVDB translator when importing volume data; adjust volume translator settings as needed.
- Imported volumes are translated into Interchange node containers for downstream pipelines to convert into engine assets.

## 5. Version-specific notes (UE 5.7)

- Marked experimental/hidden; no additional UE 5.7-specific changes are called out in the source.

