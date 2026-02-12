# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a declarative VS Code extension that provides YAML schema support for Agile Certificate Services (ACS)
configuration files. The extension automatically applies JSON schema validation to ACS configuration files (
`*.certprofile.yml`, `*.caprofile.yml`, `*.keystore.yml`), enabling IntelliSense, validation, and autocompletion.

There is no TypeScript code — the extension is purely declarative, relying on `package.json` contribution points and
JSON schema files.

## Architecture

- **Schema Configuration**: Defined in `package.json` under `contributes.yamlValidation`
- **JSON Schemas**: Located in `schemas/` directory

The extension uses VS Code's YAML validation system through the `yamlValidation` contribution point. The YAML extension
by Red Hat is declared as an `extensionDependency` and is installed automatically.

## Development Commands

### Packaging

- `npm install -g @vscode/vsce` - Install the VS Code Extension Manager
- `npm install` - Install dependencies
- `vsce package` - Build the `.vsix` extension package

## Key Files

- `schemas/certificate-profile.schema.json` - JSON schema for certificate profiles
- `schemas/ca-profile.schema.json` - JSON schema for CA profiles
- `schemas/keystore.schema.json` - JSON schema for keystore configurations
- `package.json` - Extension manifest with YAML validation configuration
- `.github/workflows/release.yml` - GitHub Actions workflow for building and uploading release assets

## Schema Details

The JSON schemas support comprehensive configuration including:

- Subject and Subject Alternative Name fields with validation constraints
- All standard certificate extensions (Basic Constraints, Key Usage, etc.)
- Advanced extensions (CRL Distribution Points, Authority Information Access, etc.)
- Custom extensions with multiple encoding formats
- Cryptographic algorithm specifications
- Certificate validity periods and template inheritance
