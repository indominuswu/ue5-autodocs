# Serialization Utils Plugin Overview

## 1. What this plugin does

- Provides extended serialization helpers for JSON and XML formats.
- Supplies formatter/back-end implementations that plug into UE’s structured archive system for reading/writing data.

## 2. Key Modules

- **JsonSerialization** (Runtime, Default)  
  - Role: JSON-specific structured archive formatters with extended functionality.
- **XmlSerialization** (Runtime, Default)  
  - Role: XML structured archive formatters and utilities.

## 3. Important Types & APIs

### JSON

- `FJsonArchiveInputFormatterEx`, `FJsonArchiveOutputFormatterEx`: Extended structured archive formatters for JSON.
- `FJsonSerializationModule`: Module owning formatter registration.

### XML

- `FXmlArchiveInputFormatter`, `FXmlArchiveOutputFormatter`: Structured archive formatters for XML.
- `FXmlStructSerializerBackend`: Backend adapter for struct serialization to XML.
- Utilities: `FXmlWriter`, `FXmlFormatterHelper`, `FXmlUtils` for low-level XML writing and helper routines.

## 4. Typical usage patterns

- Enable the plugin, then use the provided formatters when serializing data via structured archives to JSON or XML.
- Leverage the XML utilities/backends when building custom exporters that need direct XML output.

## 5. Version-specific notes (UE 5.7)

- No explicit UE 5.7-specific notes found; this overview is based on the current plugin state in the UE 5.7 source tree.
