# MIDI Device Support Plugin Overview

## 1. What this plugin does

- Exposes MIDI device input/output to UE through C++ and Blueprint-friendly APIs.
- Lets projects enumerate MIDI hardware, listen for MIDI events, and send messages.
- Targets gameplay and tooling scenarios that need external controllers or DAW integration.
- Disabled by default to avoid unnecessary dependencies when MIDI is not required.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users enumerate devices and use `UMIDIDeviceInputController`/`UMIDIDeviceOutputController` Blueprint/C++ APIs to receive and send MIDI messages.

## 3. Key Modules

- **MIDIDevice** (Runtime) — runtime device discovery, input polling, and output dispatch; provides Blueprint controllers.

## 4. Important Types & APIs

- `UMIDIDeviceManager` — discovers devices, manages lifecycle, and ticks controllers.
- `UMIDIDeviceInputController` — Blueprint-assignable delegates for Note On/Off, Pitch Bend, Aftertouch, Control Change, Program Change, Channel Aftertouch, and a raw event multicast; handles startup/shutdown per device and polls input.
- `UMIDIDeviceOutputController` — sends MIDI messages to hardware (notes, control changes, etc.).
- `UMIDIDeviceControllerBase` — shared base for input/output controllers.

## 5. Typical usage patterns

- Enable the plugin, then use `UMIDIDeviceManager` to list devices and create input/output controllers.
- In Blueprint, bind to `OnMIDINoteOn`, `OnMIDINoteOff`, `OnMIDIControlChange`, etc., on an input controller to react to hardware events.
- Use an output controller to send messages (e.g., trigger notes or control changes) back to the connected device.
- Add controllers to an actor or subsystem and tick/cleanup via the manager to keep device sessions healthy.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes called out in code; functionality matches the current runtime implementation.

