# OneSky Localization Service Plugin Overview

## 1. What this plugin does

- Integrates OneSky (Unity VCS localization service) with Unreal’s localization dashboard.
- Provides source control–like operations for localization data (status, update, submit, history) through OneSky APIs.
- Beta and disabled by default.

## 2. Key Modules

- **OneSkyLocalizationService** (Editor, Default)  
  - Role: Implements an `ILocalizationServiceProvider` backed by OneSky.  
  - Notable types: `FOneSkyLocalizationServiceProvider`, `FOneSkyLocalizationServiceModule`, `FOneSkyLocalizationServiceOperations`, `FOneSkyLocalizationServiceState`, `FOneSkyLocalizationServiceRevision`, `FOneSkyLocalizationServiceCommand`, `FOneSkyLocalizationServiceSettings`, `FOneSkyConnection`, `OneSkyLocalizationServiceResponseTypes`.

## 3. Important Types & APIs

- Provider/core: `FOneSkyLocalizationServiceProvider` handles connection, status, check-in/out, update, history, and revision info.  
- Connection: `FOneSkyConnection`/`FOneSkyConnectionInfo` manage REST calls and credentials.  
- Operations/workers: `FOneSkyLocalizationServiceOperations` implements provider operations; `IOneSkyLocalizationServiceWorker` interface.  
- State/revision: `FOneSkyLocalizationServiceState` and `FOneSkyLocalizationServiceRevision` represent file status and versions.  
- Settings: `FOneSkyLocalizationServiceSettings` stores project API keys/ids.  
- Responses: `OneSkyLocalizationServiceResponseTypes` defines DTOs for REST responses.

## 4. Typical usage patterns

- Enable the plugin, enter OneSky project credentials in the localization dashboard settings.  
- Use the localization dashboard/source control UI to check status, pull/push translations, and view history via OneSky.

## 5. Version-specific notes (UE 5.7)

- Beta, off by default. No explicit 5.7-specific changes noted in source.
