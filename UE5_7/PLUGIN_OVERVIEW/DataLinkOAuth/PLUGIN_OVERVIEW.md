# Motion Design Data Link OAuth Plugin Overview

## 1. What this plugin does

- Adds OAuth 2.0 authentication support to Motion Design Data Link connections.
- Manages tokens and local HTTP listeners used during OAuth authorization flows.
- Provides editor tooling to author OAuth settings assets.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Users create OAuth settings assets via the editor factory and call `UDataLinkOAuthSubsystem` to register listeners and retrieve tokens for Data Link connections.

## 3. Key Modules

- **DataLinkOAuth** (Runtime)  
  - Role: Runtime OAuth token management and request handling.
  - Notable types: `UDataLinkOAuthSubsystem`, `FDataLinkOAuthToken`, `FDataLinkOAuthHandle`.
- **DataLinkOAuthEditor** (Editor)  
  - Role: Factories and asset definitions for OAuth settings.
  - Notable types: `UDataLinkOAuthSettings` factory classes, asset definitions for OAuth settings assets.

## 4. Important Types & APIs

### `UDataLinkOAuthSubsystem`
- Role: Engine subsystem that tracks OAuth listening instances and issued tokens.
- Key functions: `RegisterListenInstance`, `UnregisterListenInstance`, `FindToken`, `RegisterToken`, `CleanExpiredTokens`.
- Key properties: Maps of active listeners and stored tokens keyed by handles.

### OAuth settings assets
- Role: Editor-created assets that describe OAuth endpoints and credentials, instantiated via editor factories.

## 5. Typical usage patterns

- Enable alongside `DataLink` to secure Data Link connections with OAuth.
- Create OAuth settings assets in the editor; the editor module provides factories and asset definitions.
- At runtime, use `UDataLinkOAuthSubsystem::RegisterListenInstance` to start a local listener and obtain tokens, then look up tokens via `FindToken` when establishing connections.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific notes discovered; plugin ships as an optional OAuth extension in this branch.

