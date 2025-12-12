# nDisplay Launch Plugin Overview

## 1. What this plugin does

- Provides editor tooling to launch local nDisplay nodes easily (virtual production).  
- Integrates with Console Variables and Multi-User/Concert for coordinating launches.  
- Beta, disabled by default; supports Win64/Linux.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Editor launch tooling lets users start nDisplay nodes locally for VP testing and integrates with Console Variables/Multi-User coordination.

## 3. Key Modules

- **DisplayClusterLaunchEditor** (Editor, Default, Win64/Linux)  
  - Role: Editor UI/logic for launching nDisplay nodes; ties into existing nDisplay and messaging systems.

## 3. Typical usage patterns

- Enable the plugin alongside nDisplay and ConsoleVariables/MultiUser plugins.  
- Use the nDisplay Launch tools to start local nodes from the editor for testing/iteration.

## 6. Version-specific notes (UE 5.7)

- Beta/off by default; no explicit 5.7-specific changes noted.

