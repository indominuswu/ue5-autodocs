# Windows Device Profile Selector Plugin Overview

## 1. What this plugin does

- Selects appropriate device profiles for Windows platforms at startup.
- Adjusts system settings based on detected hardware to choose a matching DeviceProfile.

## 2. Key Modules

- **WindowsDeviceProfileSelector** (RuntimeNoCommandlet)
  - Role: Runs during `PostConfigInit` on Win64 to pick the best DeviceProfile before other systems initialize.

## 3. Important Types & APIs

- The module exposes minimal public API (`WindowsDeviceProfileSelector.h`); selection logic executes internally during startup.

## 4. Typical usage patterns

- Enabled by default on Win64. Provide Windows-specific DeviceProfile entries in `DefaultDeviceProfiles.ini`; the selector picks the best match automatically.
- No direct Blueprint/API interaction is required?selection happens during early engine startup.

## 5. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes noted; plugin remains a default startup helper for Windows.
