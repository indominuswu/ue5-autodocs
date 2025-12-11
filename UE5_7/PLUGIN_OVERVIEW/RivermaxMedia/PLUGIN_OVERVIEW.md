# NVIDIA Rivermax Media Streaming Plugin Overview

## 1. What this plugin does
- Integrates Rivermax with UE’s Media Framework for SDI/IP-style video IO.
- Provides media sources, outputs, capture, player, custom time step, and timecode provider built on Rivermax streams.
- Editor factories and customizations enable asset creation and configuration within the Content Browser.

## 2. Key Modules
- **RivermaxMedia** (Runtime)  
  - Media capture/output/player implementations using Rivermax; texture sampling/conversion utilities and custom timing sources.
- **RivermaxMediaEditor** (Editor)  
  - Asset factories (`RivermaxMediaSourceFactoryNew`, `RivermaxMediaOutputFactoryNew`), details customizations, and modular initializers.
- **RivermaxMediaFactory** (RuntimeNoCommandlet)  
  - Factory registration for runtime media player/capture creation.

## 3. Important Types & APIs
### Media assets
- `URivermaxMediaSource`: describes an incoming Rivermax stream; includes connection options.
- `URivermaxMediaOutput`: config for Rivermax-backed output; paired with `URivermaxMediaCapture` to send frames.
- `URivermaxMediaCapture`: capture pipeline from UE render targets to Rivermax output.

### Playback and timing
- `URivermaxMediaPlayer`: Rivermax-backed media player with texture sampling (`FRivermaxMediaTextureSample`) and converter.
- `URivermaxCustomTimeStep`: custom engine timestep synced to Rivermax.
- `URivermaxTimecodeProvider`: timecode source derived from Rivermax timing.

### Editor hooks
- Detail customizations (`RivermaxMediaDetailsCustomization`, `RivermaxMediaPropertyCustomization`) expose stream options in the editor.
- Factories create Rivermax media source/output assets from the Content Browser.

## 4. Typical usage patterns
- Enable RivermaxCore and this plugin; ensure Rivermax hardware/drivers are available.
- Create a `RivermaxMediaSource` for input streams or `RivermaxMediaOutput` for output; configure network parameters.
- Use `URivermaxMediaCapture` to send viewport/render target output via Rivermax; set `URivermaxCustomTimeStep`/`URivermaxTimecodeProvider` if synchronization to Rivermax is required.
- Play Rivermax streams through `URivermaxMediaPlayer` in Media Framework components.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

