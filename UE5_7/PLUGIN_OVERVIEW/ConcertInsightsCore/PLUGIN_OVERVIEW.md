# ConcertInsightsCore Plugin Overview

## 1. What this plugin does
- Core logic for orchestrating synchronized tracing across Concert endpoints.
- Shared between editor and program targets to request/coordinate trace capture.

## 2. Key Modules
- **ConcertInsightsCore** (EditorAndProgram)  
  - Role: Implements shared tracing request/coordination logic consumed by client and server plugins.

## 3. Important Types & APIs
- Core services are internal (request handling, message routing). No notable `UObject` APIs exposed for gameplay use.

## 4. Typical usage patterns
- Used as a dependency by ConcertInsightsClient and ConcertInsightsServer to share tracing protocol/logic; not directly user-facing.

## 5. Version-specific notes (UE 5.7)
- No explicit UE 5.7-specific notes; overview reflects current module responsibilities.

