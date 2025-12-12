# Netcode Unit Test - Unreal Engine Plugin Overview

## 1. What this plugin does
- Adds exploit-focused unit tests for Unreal Engine networking, built on the Netcode Unit Test framework.
- Provides ready-made tests for packet limits, net bit handling, and crash scenarios for validation.
- Integrates with the NetcodeUnitTest plugin to run uncooked-only test suites on Win64/Linux.

## 2. Editor/Runtime surfaces

- User-facing: No - Uncooked-only module that just registers internal Netcode Unit Test cases; no editor tools or gameplay/runtime APIs are exposed for game teams.

## 3. Key Modules
- **NUTUnrealEngine** (UncookedOnly): Registers Netcode Unit Test cases specific to Unreal Engine behaviors.

## 4. Important Types & APIs
### `INUTUnrealEngine`
- Role: Module interface used to register Unreal Engine-specific test cases with the Netcode Unit Test harness.
### `FUnrealEngineEnvironment` and derived environments
- Role: Provide environment setup for running tests against sample games (`FShooterGameEnvironment`, `FQAGameEnvironment`, `FUTEnvironment`).
### Unit test classes (`FTextCrash`, `NetBitsTest`, `PacketLimitTest`, `PacketLimitTest_Oodle`, `UTT61_DebugReplicateData`)
- Role: Individual test cases covering network serialization limits, packet handling, and crash regression scenarios.

## 5. Typical usage patterns
- Enable alongside the NetcodeUnitTest plugin in an uncooked project build, then run the registered test cases via the framework?s automation entry points.
- Select or extend the provided environment classes to target specific game configurations.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; plugin mirrors current test set in this source tree.

