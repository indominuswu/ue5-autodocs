# Chaos Caching USD Plugin Overview

## 1. What this plugin does

- Extends Chaos Cache support to use USD files for recording or playing back flesh simulations.
- Provides editor utilities for importing/exporting USD caches for Chaos Flesh.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor integration lets users import/export Chaos Flesh caches as USD and configure caches to read/write USD files.

## 3. Key Modules

- **ChaosCachingUSD** (Editor)  
  - Role: Editor integration for USD-based Chaos cache workflows tied to Chaos Flesh simulations.

## 4. Important Types & APIs

- USD cache handlers within the module manage reading/writing USD files for Chaos Flesh data; exposed through editor tooling.

## 5. Typical usage patterns

- Enable alongside ChaosCaching and ChaosFlesh to import or export caches as USD.
- Use editor tools provided by the module to point Chaos Flesh caches at USD files for playback or recording.

## 6. Version-specific notes (UE 5.7)

- Experimental, editor-only, disabled by default in this UE 5.7 tree.
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

