# Online Subsystem Amazon Plugin Overview

## 1. What this plugin does
- Provides an Online Subsystem (OSSv1) implementation for Amazon platform identity/access.
- Integrates Amazon-specific identity handling via `OnlineIdentityAmazon`.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Platform OSS provider exposing Amazon identity via `IOnlineSubsystem::Get(\"AMAZON\")` for games that integrate Amazon logins.

## 3. Key Modules
- **OnlineSubsystemAmazon** (Runtime): Amazon OSS provider for Win64/Linux.

## 4. Important Types & APIs
### `FOnlineSubsystemAmazon` / `FOnlineSubsystemAmazonModule`
- Role: Provider registration and lifecycle for the Amazon subsystem.
### `FOnlineIdentityAmazon`
- Role: Handles Amazon user authentication/identity for OSS features.
### `OnlineSubsystemAmazonPackage`
- Role: Module/package definitions for export/import.

## 5. Typical usage patterns
- Enable plugin and configure Amazon credentials; obtain subsystem via `IOnlineSubsystem::Get("AMAZON")`.
- Use identity interface for login and integrate with OSS features supported by the provider.

## 6. Version-specific notes (UE 5.7)
- No explicit 5.7 notes; platform allow list limited to Win64/Linux per metadata.

