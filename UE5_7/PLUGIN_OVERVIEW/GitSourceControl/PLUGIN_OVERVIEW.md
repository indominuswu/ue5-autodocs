# Git Source Control Plugin Overview

## 1. What this plugin does

- Provides Git integration for Unreal Editor: status, diff, submit (commit), history, branching operations via the source control panel.
- Implements Git workers for standard operations and a settings UI for repository configuration.
- Beta-marked, enabled by default.

## 2. Key Modules

- **GitSourceControl** (Editor, Default)  
  - Role: Source control provider implementation for Git.  
  - Notable types: `FGitSourceControlProvider`, `FGitSourceControlModule`, `FGitSourceControlState`, `FGitSourceControlRevision`, `FGitSourceControlSettings`, `FGitSourceControlOperations`, `FGitSourceControlUtils`, `SGitSourceControlSettings`, `IGitSourceControlWorker`.

## 3. Important Types & APIs

- `FGitSourceControlProvider`: Source control provider entry point; routes operations to workers, caches state, registers with editor.  
- `FGitSourceControlOperations`: Defines Git worker classes for common operations (check-out/commit/update/revert/history/etc.).  
- `FGitSourceControlState`/`FGitSourceControlRevision`: Represent file state and revisions.  
- `FGitSourceControlSettings`: Stores repo path, binary/executable preferences; `SGitSourceControlSettings` Slate widget for configuration.  
- `FGitSourceControlUtils`: Utility helpers for invoking Git, parsing output, and managing file lists.

## 4. Typical usage patterns

- Enable the plugin; configure repository path and Git binary via the Git settings panel.  
- Use the Source Control menu to connect, check out, commit, revert, view history, and diff files.  
- Works with standard editor source control workflows (Content Browser, File menu).

## 5. Version-specific notes (UE 5.7)

- Marked Beta in 5.7; otherwise matches standard Git provider functionality in this source tree.
