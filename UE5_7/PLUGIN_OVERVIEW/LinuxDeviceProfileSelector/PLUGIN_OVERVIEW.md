# Linux Device Profile Selector Plugin Overview

## 1. What this plugin does
- Chooses an appropriate device profile at startup on Linux platforms.
- Integrates with the engine’s device profile system to select profiles without commandlets.

## 2. Editor/Runtime surfaces

- User-facing: No - Platform helper that auto-selects Linux device profiles; no direct editor or gameplay-facing interface.

## 3. Key Modules
- **LinuxDeviceProfileSelector** (RuntimeNoCommandlet)  
  - Role: Runtime hook that applies platform-specific device profiles for Linux builds.
  - Notable types: none exposed; logic lives inside the module startup.

## 4. Important Types & APIs
- No public classes or Blueprint APIs; selection happens during module initialization against device profiles.

## 5. Typical usage patterns
- Enable the plugin in Linux builds to automatically pick the best device profile; no additional setup is required.
- Combine with custom Linux device profiles in project settings to tune scalability defaults.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; the plugin remains a small runtime helper enabled by default.

