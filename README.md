# ACS VS Code Schema Support

This VS Code extension provides YAML schema support for Agile Certificate Services (ACS) configuration files.
It enables IntelliSense, validation, and autocompletion for the supported configuration files.

## Supported Configuration Files

*Note:* All configuration files must end with exact lower case match and end with .yml.
The structure of a configuration file is `<name>.<type>.yml` and the name must be the same
string value as in the 'name' field in the YAML file.

Name can have the characters 'a-z', 'A-Z', '0-9' and the '-','_' characters.

### Configuration Types

* **Certificate Profile**: `<name>.certprofile.yml`
    - Complete X.509 certificate profile specification
    - Includes subject fields, extensions, validity periods, and cryptographic parameters
    - Example: `my_cert_profile.certprofile.yml`

* **CA Profile**: `<name>.caprofile.yml`
    - Certificate Authority profile configuration
    - Example: `my_ca_profile.caprofile.yml`

* **Keystore**: `<name>.keystore.yml`
    - Keystore configuration settings
    - Example: `my_keystore.keystore.yml`

## Prerequisites

This extension requires
the [YAML extension by Red Hat](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml).
It will be installed automatically when you install this extension.

## Features

- **Schema Validation**: Automatic validation of ACS configuration files against their respective schemas
    - `*.certprofile.yml` - X.509 certificate profile validation
    - `*.caprofile.yml` - Certificate Authority profile validation
    - `*.keystore.yml` - Keystore configuration validation
- **IntelliSense**: Code completion and suggestions for configuration properties
- **Error Highlighting**: Real-time validation with error messages for invalid configurations
- **Documentation**: Hover tooltips with property descriptions and valid values

## Usage

Once installed, the extension automatically provides schema support for all supported configuration file types:

### Certificate Profile (*.certprofile.yml)

Comprehensive validation including:

- Certificate subject fields and constraints
- X.509 certificate extensions (Basic Constraints, Key Usage, etc.)
- Subject Alternative Names with various field types
- Certificate policies and advanced extensions
- Cryptographic parameters and validity periods

### CA Profile (*.caprofile.yml)

Certificate Authority configuration validation

### Keystore (*.keystore.yml)

Keystore configuration validation

## Installing from VSIX

If you have a `.vsix` file (e.g. from a GitHub release), you can install it manually:

### Method 1: Using the Command Line

```bash
code --install-extension acs-vscode-schema-support-<version>.vsix
```

### Method 2: Using VS Code UI

1. Open VS Code
2. Go to the Extensions view (Ctrl+Shift+X / Cmd+Shift+X)
3. Click the three dots menu (`...`) in the Extensions view
4. Select "Install from VSIX..."
5. Browse and select the `.vsix` file

## Development

### Building the Extension

Install the VS Code Extension Manager and package the extension:

```bash
npm install -g @vscode/vsce
npm install
vsce package
```

### Project Structure

- `schemas/certificate-profile.schema.json` - JSON schema for certificate profiles
- `schemas/ca-profile.schema.json` - JSON schema for CA profiles
- `schemas/keystore.schema.json` - JSON schema for keystore configurations
- `package.json` - Extension manifest and configuration

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.