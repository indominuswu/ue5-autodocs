# MemoryUsageQueries Plugin Overview

## 1. What this plugin does
- Runtime helper for querying package/class memory usage and dependency sizes, originally contributed by The Coalition.
- Provides a pluggable `IMemoryUsageInfoProvider` interface with Low-Level Memory Tracker (LLM) backed implementation.
- Exposes static query functions to gather exclusive/inclusive memory, dependency graphs, and filtered size reports.
- Disabled by default; intended for profiling and tooling scenarios.

## 2. Key Modules
- **MemoryUsageQueries** (Runtime)
  - Role: Implements the query API, default provider, and optional LLM-backed provider selection via config.
  - Notable types: `FMemoryUsageQueriesModule`, `UMemoryUsageQueriesConfig`, `IMemoryUsageInfoProvider`, `FMemoryUsageInfoProviderLLM`, namespace `MemoryUsageQueries` helpers.

## 3. Important Types & APIs
### `UMemoryUsageQueriesConfig`
- Role: Config object that selects the active `IMemoryUsageInfoProvider` and related options.
- Key properties: provider name, flags controlling dependency traversal and filtering.

### `IMemoryUsageInfoProvider`
- Role: Interface returning package size data (exclusive, inclusive, shared/unique) and dependency mappings.
- Implementations: `FMemoryUsageInfoProviderLLM` uses LLM data; custom providers can be registered.

### `MemoryUsageQueries` namespace functions
- Role: Static API for querying memory (`GetMemoryUsage*`) and dependencies (`GetDependenciesWithSize*`), plus LLM-backed filtered queries.
- Notes: Several overloads using `FName` replace deprecated string-based variants (5.6/5.7 deprecation warnings are present).

## 4. Typical usage patterns
- Enable the plugin when profiling. Configure provider via `UMemoryUsageQueriesConfig`.
- Call `MemoryUsageQueries::GetMemoryUsage*` or `GetDependenciesWithSize*` from tooling code to retrieve size data per package or combined sets.
- With LLM enabled, use filtered queries (group/class filters) to produce categorized memory reports for debugging or command-line tools.

## 5. Version-specific notes (UE 5.7)
- Deprecated string-based query overloads are marked as of 5.6; `FName` versions should be used in UE 5.7.
