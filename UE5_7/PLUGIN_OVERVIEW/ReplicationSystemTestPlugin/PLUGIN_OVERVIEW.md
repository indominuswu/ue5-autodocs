# Replication System Test Plugin Overview

## 1. What this plugin does
- Contains unit and functional tests for the network replication system (Iris), covering serializers, prioritizers, filtering, RPCs, and data streams.
- Provides mock objects, test fixtures, and automation helpers for replication feature validation.

## 2. Editor/Runtime surfaces
- User-facing: No - Test-only plugin with automation fixtures/mocks; no editor tools or runtime gameplay APIs exposed.

## 3. Key Modules
- **ReplicationSystemTestPlugin** (UncookedOnly)  
  - All test assets, fixtures, and mock implementations for replication/Iris live here; runs in editor/test environments only.

## 4. Important Types & APIs
- Network automation helpers: `NetworkAutomationTest.h` / `NetworkAutomationTestMacros.h` define fixtures and assertions for Iris tests.
- Mock types: `MockDataStream`, `MockNetObjectFilter`, `MockNetObjectPrioritizer`, `MockNetSerializer`, `MockNetBlob`, `MockNetObjectAttachment` support targeted test scenarios.
- Test objects/structs: `ReplicatedTestObject`, `ReplicatedTestObjectWithRPC`, `TestFastArrayReplicationState`, `TestReplicationStateDescriptorBuilder`, `TestPrioritizationObject`, etc., exercise serialization, prioritization, and replication state building.
- Fixtures: `ReplicationSystemTestFixture`, `ReplicationSystemServerClientTestFixture`, `MultiReplicationSystemsTestFixture`, `NetBlobTestFixture`, `TestNetSerializerFixture` scaffold server/client flows.

## 5. Typical usage patterns
- Enable for developer/test builds to run replication automation tests.
- Derive new fixtures from provided bases to add coverage for custom serializers or prioritizers.
- Use the mock objects to validate Iris integration without game-specific actors.

## 6. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
