# Electra Codecs Plugin Overview

## 1. What this plugin does
- Supplies codec implementations used by the Electra media player stack.
- Includes decoder modules and factories to register codec support with Electra.
- Disabled by default; enable when using Electra for playback.

## 2. Editor/Runtime surfaces

- User-facing: No - Backend codec modules for Electra; no editor workflows or gameplay APIs beyond enabling them for media playback.

## 3. Key Modules
- **ElectraDecoders** (RuntimeNoCommandlet)  
  - Role: Implements decoder logic for supported codecs.
- **ElectraCodecFactory** (RuntimeNoCommandlet / Editor)  
  - Role: Registers codec factories with Electra runtime and provides editor-time awareness.

## 4. Important Types & APIs
- Codec implementations are internal to the Electra modules; no Blueprint-facing classes are exported.
- Factories register with Electra to make codecs discoverable at runtime.

## 5. Typical usage patterns
- Enable alongside `ElectraPlayer` to allow Electra to instantiate the provided codecs.
- No direct API usage expected; codecs are selected based on media format and platform capabilities.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; behavior follows current Electra codec modules.

