# Subversion Plugin Overview

## 1. What this plugin does
- Adds Subversion (SVN) source control support to the Unreal Editor.
- Implements provider, state, and revision handling for SVN checkouts, commits, labels, and history.
- Exposes an editor settings panel for repository configuration and credentials.

## 2. Key Modules
- **SubversionSourceControl** (UncookedOnly)  
  - Role: Source control provider implementation, workers for SVN operations, UI settings, and integration hooks.  
  - Notable types: `FSubversionSourceControlProvider`, `FSubversionSourceControlState`, `FSubversionSourceControlRevision`, `FSubversionSourceControlOperations`, `USubversionSourceControlSettings`, `SSubversionSourceControlSettings`.

## 3. Important Types & APIs
### `FSubversionSourceControlProvider`
- Role: Main provider exposing SVN capabilities to the editor.
- Key functions: connect/disconnect, status refresh, check-in/checkout, revert, get history/labels.

### `FSubversionSourceControlOperations` / workers
- Role: Concrete worker classes for SVN commands (update, commit, add, delete, revert, copy, mark for add).

### `USubversionSourceControlSettings`
- Role: Config object storing repository URL, user credentials, binary path, and connection preferences.

## 4. Typical usage patterns
- In Editor -> Source Control, choose Subversion and enter repository URL/credentials in the settings panel provided by `SSubversionSourceControlSettings`.
- Use standard source control commands (check out, submit, sync) through the Content Browser or File menu; operations are executed via SVN command-line wrappers.
- Retrieve history, revisions, and labels for assets through the provider’s revision classes.

## 5. Version-specific notes (UE 5.7)
- No UE 5.7-specific changes noted; plugin is stable and non-beta in this source tree.
