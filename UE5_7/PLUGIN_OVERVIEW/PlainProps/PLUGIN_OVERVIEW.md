# PlainProps Plugin Overview

## 1. What this plugin does
- Experimental prototype for a new serialization stack (“PlainProps”) targeting Win64.
- Provides utilities to declare/bind property schemas, read/write data, diff, parse, and visualize serialized structures.
- Supplies lightweight type-name/CTTI helpers and string/index utilities for the prototype.

## 2. Editor/Runtime surfaces

- User-facing: Yes - Developer-facing prototype; exposes C++ macros/helpers (`PlainPropsDeclare/Bind/Write/Read/Diff`) for teams experimenting with the PlainProps serialization workflow.

## 3. Key Modules
- **PlainProps** (Runtime)  
  - Role: Core PlainProps runtime with schema construction, read/write/diff/parse helpers and related utilities.

## 4. Important Types & APIs
- Declaration/binding: `PlainPropsDeclare.h`, `PlainPropsBind.h`, `PlainPropsSpecify.h`, `PlainPropsTypename.h`, `PlainPropsCtti.h`.  
  - Role: Macros/helpers to declare PlainProps types and bind members for serialization.
- Schema/build: `PlainPropsBuild.h`, `PlainPropsBuildSchema.h`, `PlainPropsIndex.h`.  
  - Role: Build schemas and indexing for serialized data.
- IO helpers: `PlainPropsWrite.h`, `PlainPropsRead.h`, `PlainPropsSave.h`, `PlainPropsLoad.h`, `PlainPropsSaveMember.h`, `PlainPropsLoadMember.h`.  
  - Role: Serialize/deserialize PlainProps structures.
- Utility/inspection: `PlainPropsPrint.h`, `PlainPropsVisualize.h`, `PlainPropsStringUtil.h`, `PlainPropsDiff.h`, `PlainPropsParse.h`.  
  - Role: String formatting, visualization, diffs, and parsing support for PlainProps data.

## 5. Typical usage patterns
- Enable the plugin (Win64 only).  
- Declare/bind PlainProps-enabled structures using the declaration/binding helpers.  
- Build schemas and serialize data with the write/save APIs; read/load to reconstruct.  
- Use diff/print/visualize helpers to compare or debug serialized data during development.

## 6. Version-specific notes (UE 5.7)
- Marked experimental; Win64-only.  
- No explicit UE 5.7-only changes noted; overview reflects current prototype state.

