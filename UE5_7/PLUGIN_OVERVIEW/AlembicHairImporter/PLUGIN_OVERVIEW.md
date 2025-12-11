# Alembic Groom Importer Plugin Overview

## 1. What this plugin does
- Imports Alembic hair strands (groom) data into Unreal as groom assets.
- Provides a translator module used by the grooming pipeline.

## 2. Key Modules
- **AlembicHairTranslatorModule** (Editor)
  - Role: Registers the Alembic hair translator with the import pipeline.

## 3. Important Types & APIs

### `FAlembicHairTranslator`
- Role: Translator that reads Alembic groom data and produces Unreal groom assets.

## 4. Typical usage patterns
- Enable the plugin, then import Alembic hair (`.abc`) files through the Content Browser; the translator converts them to groom assets.
- Configure import options during the import dialog as provided by the translator.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.