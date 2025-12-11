# Take Recorder Multi-User synchronization Plugin Overview

## 1. What this plugin does
- Adds opt-in synchronization between Multi-User sessions and Take Recorder settings.
- Exposes Blueprint helpers to read/write per-client Take Recorder flags (record on client, synchronize transactions).
- Integrates with Concert/Multi-User messaging to propagate Take Recorder options.

## 2. Key Modules
- **ConcertTakeRecorder** (UncookedOnly)
  - Role: Editor-side integration for Multi-User + Take Recorder synchronization.
  - Notable types: `UMultiUserTakesFunctionLibrary`, Concert message handlers and styles.

## 3. Important Types & APIs

### `UMultiUserTakesFunctionLibrary`
- Role: Blueprint utility library for querying and setting Take Recorder synchronization settings per client.
- Key functions: `GetRecordOnClientLocal`, `SetRecordOnClientLocal`, `GetRecordOnClient`, `SetRecordOnClient`, `GetSynchronizeTakeRecorderTransactions(Local)`, `SetSynchronizeTakeRecorderTransactionsLocal`.
- Uses Multi-User client IDs (`FGuid`) from `UMultiUserSubsystem` to target remote clients.

## 4. Typical usage patterns
- Enable the plugin in projects using Multi-User with Take Recorder.
- Use the provided Blueprint functions to mirror Take Recorder options across clients or to drive UI toggles per connected client.
- Combine with Multi-User session queries (`UMultiUserSubsystem::GetRemoteClientIds`) to address specific participants.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes found; features are labeled opt-in and rely on current Multi-User APIs.
