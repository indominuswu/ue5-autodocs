# Blueprint File Utilities Plugin Overview

## 1. What this plugin does

- Exposes low-level file system operations to Blueprints (find, copy, move, delete, create directories).
- Targets absolute paths for interacting with user/system file locations outside packaged content.
- Useful for tooling, debug utilities, or lightweight file management without writing C++.
- Disabled by default; enable the plugin to access its Blueprint nodes.

## 2. Editor/Runtime surfaces
- User-facing: Yes - Provides `UBlueprintFileUtilsBPLibrary` Blueprint nodes (FindFiles, Copy/Move/Delete, MakeDirectory, GetUserDirectory) for editor and runtime scripting.

## 3. Key Modules

- **BlueprintFileUtils** (Runtime, Default)  
  - Role: Provides the Blueprint function library backing all file operations via `IFileManager`/`FPlatformProcess`.
  - Notable types: `UBlueprintFileUtilsBPLibrary`, module shim `FBlueprintFileUtilsModule`.

## 4. Important Types & APIs

### `UBlueprintFileUtilsBPLibrary` (Blueprint function library)

- Role: Blueprint-facing wrapper over `IFileManager` and `FPlatformProcess::UserDir()` for file system access.
- Key functions (Category `FileUtils`, all static):  
  - `FindFiles(Directory, FoundFiles, FileExtension="")` – non-recursive search with optional extension filter (`.ext` or `ext`).  
  - `FindRecursive(StartDirectory, FoundPaths, Wildcard="", bFindFiles=true, bFindDirectories=false)` – recursive search supporting wildcards.  
  - `FileExists(Filename)`, `DirectoryExists(Directory)`.  
  - `MakeDirectory(Path, bCreateTree=false)`.  
  - `DeleteDirectory(Directory, bMustExist=false, bDeleteRecursively=false)`, `DeleteFile(Filename, bMustExist=false, bEvenIfReadOnly=false)`.  
  - `CopyFile(DestFilename, SrcFilename, bReplace=true, bEvenIfReadOnly=false)`, `MoveFile(DestFilename, SrcFilename, bReplace=true, bEvenIfReadOnly=false)`.  
  - `GetUserDirectory()` – returns the platform user/home directory.

### `FBlueprintFileUtilsModule`

- Role: Module entry point; no additional runtime APIs beyond standard module lifetime.

## 5. Typical usage patterns

- Enable the plugin, then use the `FileUtils` Blueprint nodes in editor or at runtime to perform file operations with absolute paths (e.g., user documents, temp folders).
- Use `FindFiles`/`FindRecursive` to gather file lists, `FileExists`/`DirectoryExists` for guards, and `CopyFile`/`MoveFile`/`DeleteFile` for maintenance tasks.
- `MakeDirectory` can set up target folders before writing; `DeleteDirectory` supports recursive removal when `bDeleteRecursively` is true.
- `GetUserDirectory` is convenient for locating a writable user area on each platform.

## 6. Version-specific notes (UE 5.7)

- No UE 5.7-specific changes or deprecations are noted; behavior matches the current source implementation.

