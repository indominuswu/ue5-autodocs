# RivermaxCore Plugin Overview

## 1. What this plugin does
- Exposes NVIDIA Rivermax networking to UE for high-bandwidth video/ancillary streaming.
- Provides core Rivermax device management, stream setup, frame allocation, and PTP-aware scheduling utilities.
- Includes editor customizations and rendering helpers for Rivermax-based workflows.

## 2. Key Modules
- **RivermaxCore** (Runtime)  
  - Core Rivermax manager, device discovery, frame management, stream interfaces (input/output/ancillary), wrappers, and tracing utilities.
- **RivermaxEditor** (Editor)  
  - Settings/detail customizations and widgets for selecting Rivermax interfaces/devices in editor.
- **RivermaxRendering** (Runtime)  
  - Shader support and rendering-side hooks for Rivermax output.

## 3. Important Types & APIs
### Interfaces
- `IRivermaxCoreModule`, `IRivermaxManager`: access to Rivermax initialization, device queries, and stream creation.
- `IRivermaxInputStream`, `IRivermaxOutputStream`: abstract APIs for receiving/sending Rivermax video/ancillary data.
- `IRivermaxBoundaryMonitor`: monitors network boundaries/limits during streaming.

### Core utilities
- `FRivermaxManager`, `FRivermaxDeviceFinder`: manage available NICs and Rivermax startup/shutdown.
- `FRivermaxFrameManager` / `FRivermaxFrameAllocator`: handle frame buffers and synchronization.
- Stream implementations: `RivermaxOutStream`, `RivermaxOutVideoStream`, `RivermaxOutAncStream`, `RivermaxInputStream`.
- Helpers: `RivermaxFormats`, `RivermaxTypes`, `RivermaxPTPUtils`, `RivermaxTracingUtils`.

### Settings
- `URivermaxSettings` (Developer Settings, config=Engine): select time source (`PTP`, `Engine`, `System`) and PTP interface address when using PTP.

### Editor widgets
- `SRivermaxInterfaceComboBox`, customizations (`RivermaxSettingsDetailsCustomization`, `RivermaxDeviceSelectionCustomization`) assist in picking NICs/interfaces.

## 4. Typical usage patterns
- Enable the plugin and configure `URivermaxSettings` (choose time source and PTP interface).
- Use `IRivermaxManager` to enumerate interfaces and create input/output streams; implement boundary monitoring if needed.
- For editor workflows, use provided customizations to select Rivermax-capable NICs in asset or project settings.
- Streams can be coupled with media pipelines (via RivermaxMedia) or custom rendering paths (RivermaxRendering).

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

