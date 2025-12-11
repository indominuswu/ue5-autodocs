# Remote Control Protocol MIDI Plugin Overview

## 1. What this plugin does
- Lets MIDI devices drive Remote Control presets by mapping MIDI messages to exposed entities.
- Provides project-configurable default device selection and editor UI to pick devices and channels.

## 2. Key Modules
- **RemoteControlProtocolMIDI** (Runtime)  
  - Implements the MIDI protocol, discovers devices, resolves device IDs/names, and routes MIDI input to protocol entities.
- **RemoteControlProtocolMIDIEditor** (Editor)  
  - Detail customizations (`FRemoteControlMIDIDeviceCustomization`) and UI for selecting MIDI devices in bindings.

## 3. Important Types & APIs
### `FRemoteControlProtocolMIDI`
- Role: Protocol implementation built on `UMIDIDeviceInputController`; creates protocol entities and processes incoming MIDI events.

### `URemoteControlProtocolMIDISettings` (Config=Engine)
- Role: Stores default MIDI device selection for the project.
- Key property: `DefaultDevice` (`FRemoteControlMIDIDevice`) with selector (`ERemoteControlMIDIDeviceSelector`, device name/id/project settings).

### `FRemoteControlMIDIDevice`
- Role: Identifies and resolves a MIDI device; hashes based on selector/name/id to ensure correct binding.
- Helpers: `ResolveDeviceId`, `SetUseProjectSettings`, `SetDevice`, `ToDisplayName`.

## 4. Typical usage patterns
- Enable Remote Control and MIDI device support, then enable this protocol.
- In the Remote Control Panel, assign the MIDI protocol to exposed entities and pick a device via the editor customization; default comes from project settings.
- Use device ID or name selectors to target specific hardware; incoming MIDI notes/CCs update the bound Remote Control controllers.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.

