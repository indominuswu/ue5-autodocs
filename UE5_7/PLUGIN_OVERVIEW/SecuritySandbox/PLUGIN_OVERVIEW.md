# Security Sandbox Plugin Overview

## 1. What this plugin does

- Provides a framework for reducing the operating system permissions a game client runs with to limit impact from potential exploits.
- Abstracts platform-specific sandbox behavior so clients can drop privileges after startup.
- Exposes configuration for enabling and tuning the sandbox at runtime.

## 2. Key Modules

- **SecuritySandbox** (Runtime, Default)  
  - Role: Declares the sandbox interfaces, settings, and platform implementations (generic + Windows).

## 3. Important Types & APIs

### `ISecuritySandbox` / `ISecuritySandboxModule`

- Role: Interfaces for creating and managing the sandbox instance; module bootstraps platform selection.

### `USecuritySandboxSettings`

- Role: Configurable settings (default config) that control whether the sandbox is enabled and how it behaves.

### `GenericPlatformSecuritySandbox` / `WindowsPlatformSecuritySandbox`

- Role: Platform-specific implementations used by the module to enforce reduced privileges.

## 4. Typical usage patterns

- Enable the plugin and configure `USecuritySandboxSettings` (ini) to turn sandboxing on and set platform-specific options.
- On supported platforms, the module will construct the appropriate platform sandbox implementation during startup to drop privileges.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
