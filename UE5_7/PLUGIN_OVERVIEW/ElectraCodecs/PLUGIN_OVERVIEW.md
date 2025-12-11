# Electra Codecs Plugin Overview

## 1. What this plugin does
- Supplies codec implementations used by the Electra media player stack.
- Includes decoder modules and factories to register codec support with Electra.
- Disabled by default; enable when using Electra for playback.

## 2. Key Modules
- **ElectraDecoders** (RuntimeNoCommandlet)  
  - Role: Implements decoder logic for supported codecs.
- **ElectraCodecFactory** (RuntimeNoCommandlet / Editor)  
  - Role: Registers codec factories with Electra runtime and provides editor-time awareness.

## 3. Important Types & APIs
- Codec implementations are internal to the Electra modules; no Blueprint-facing classes are exported.
- Factories register with Electra to make codecs discoverable at runtime.

## 4. Typical usage patterns
- Enable alongside `ElectraPlayer` to allow Electra to instantiate the provided codecs.
- No direct API usage expected; codecs are selected based on media format and platform capabilities.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; behavior follows current Electra codec modules.
