# Motion Design For nDisplay Plugin Overview

## 1. What this plugin does

- Extends Motion Design (Avalanche) for nDisplay clustering synchronization.
- Provides runtime hooks so Motion Design sequences and state can replicate across nDisplay nodes.

## 2. Key Modules

- **AvalancheDisplayCluster** (Runtime)  
  - Role: Runtime synchronization layer between Motion Design and nDisplay clusters.

## 3. Important Types & APIs

- No public subsystems or components are declared in headers; integration occurs inside the module to bridge Motion Design systems to nDisplay.

## 4. Typical usage patterns

- Enable when running Motion Design content on nDisplay clusters.
- Configure alongside standard nDisplay setup; Motion Design synchronization happens through the plugin’s runtime hooks.

## 5. Version-specific notes (UE 5.7)

- Marked experimental in the `.uplugin`.
- No additional UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
