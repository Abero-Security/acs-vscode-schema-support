 # CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a VS Code extension that provides YAML schema support for Agile Certificate Services (ACS) configuration files. The extension automatically applies JSON schema validation to `*.certprofile.yml` files, enabling IntelliSense, validation, and autocompletion for certificate profile configurations.

## Architecture

- **Extension Entry Point**: `src/extension.ts` - Minimal activation function that logs extension startup
- **Schema Configuration**: Defined in `package.json` under `contributes.yamlValidation`
- **JSON Schema**: `schemas/certificate-profile.schema.json` - Comprehensive X.509 certificate profile schema with extensive validation rules for certificate extensions, subject fields, and cryptographic parameters

The extension uses VS Code's built-in YAML validation system through the `yamlValidation` contribution point, requiring users to have the YAML extension by Red Hat installed.

## Development Commands

### Build and Compilation
- `npm run compile` - Compile TypeScript source to JavaScript
- `npm run watch` - Compile in watch mode for development
- `npm run vscode:prepublish` - Prepare extension for publishing (runs compile)

### Code Quality
- `npm run lint` - Run ESLint on source files
- `npm run pretest` - Run compile and lint before testing

### Testing
- `npm run test` - Run extension tests using vscode-test

## Key Files

- `src/extension.ts` - Extension activation/deactivation logic
- `schemas/certificate-profile.schema.json` - JSON schema for certificate profiles (3800+ lines defining complete X.509 certificate structure)
- `package.json` - Extension manifest with YAML validation configuration
- `eslint.config.mjs` - ESLint configuration using flat config format
- `tsconfig.json` - TypeScript configuration targeting ES2022 with Node16 modules

## Schema Details

The JSON schema supports comprehensive X.509 certificate configuration including:
- Subject and Subject Alternative Name fields with validation constraints
- All standard certificate extensions (Basic Constraints, Key Usage, etc.)
- Advanced extensions (CRL Distribution Points, Authority Information Access, etc.)
- Custom extensions with multiple encoding formats
- Cryptographic algorithm specifications
- Certificate validity periods and template inheritance

## Extension Dependencies

This extension requires the YAML extension by Red Hat to be installed for proper functionality, as noted in the README.