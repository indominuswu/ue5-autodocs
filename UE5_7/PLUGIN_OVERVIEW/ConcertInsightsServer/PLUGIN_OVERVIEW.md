# ConcertInsightsServer Plugin Overview

## 1. What this plugin does
- Runs on the Concert server side to listen for synchronized trace requests from clients and start capture.
- Works with ConcertInsightsClient to coordinate traces across endpoints.

## 2. Key Modules
- **ConcertInsightsServer** (Program)  
  - Role: Server-side handler for synchronized tracing requests and orchestration.

## 3. Important Types & APIs
- Program-focused module; logic centers on handling incoming requests and starting traces. No public gameplay-facing `UObject` APIs.

## 4. Typical usage patterns
- Deployed with Concert server; automatically participates in tracing when clients request synchronized captures via the Insights client UI.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific behavior noted; reflects current code.

