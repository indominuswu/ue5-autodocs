# Windows Virtual Keyboard Plugin Overview

## 1. What this plugin does

- Adds support for invoking the Windows 11 virtual keyboard from Unreal applications.
- Targets Win64 platforms with compatible Windows builds (26100.5061+ per plugin description).

## 2. Key Modules

- **WinVirtualKeyboard** (RuntimeNoCommandlet)
  - Role: Registers virtual keyboard integration during startup on Win64.

## 3. Important Types & APIs

- Module code is private (no public headers). Behavior is automatic once enabled; it bridges to the OS virtual keyboard APIs.

## 4. Typical usage patterns

- Enable the plugin on Win64 builds that need on-screen keyboard support (e.g., touchscreen kiosks). No Blueprint/API surface is exposed; activation is handled internally via platform hooks.

## 5. Version-specific notes (UE 5.7)

- Plugin is beta and disabled by default; requires Windows 11 version noted in the description. No other UE 5.7-specific notes found.
