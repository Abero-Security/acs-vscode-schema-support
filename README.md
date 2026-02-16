# ACS Schema Support

This VS Code extension provides YAML schema support for Agile Certificate Services (ACS) configuration files.
It enables IntelliSense, validation, and autocompletion for the supported configuration files.

## Features

- **Schema Validation**: Automatic validation of ACS configuration files against their respective schemas
    - `*.certprofile.yml` - X.509 certificate profile validation
    - `*.caprofile.yml` - Certificate Authority profile validation
    - `*.keystore.yml` - Keystore configuration validation
- **IntelliSense**: Code completion and suggestions for configuration properties
- **Error Highlighting**: Real-time validation with error messages for invalid configurations
- **Documentation**: Hover tooltips with property descriptions and valid values

## Supported Configuration Files

All configuration files must:

- Use the naming pattern: `<name>.<type>.yml`
- End with `.yml` (lowercase)
- Have a `name` field matching the filename prefix
- Use only these characters in names: `a-z`, `A-Z`, `0-9`, `-`, `_`

### Configuration Types

| Type                    | Filename Pattern         | Description                                                                 |
|-------------------------|--------------------------|-----------------------------------------------------------------------------|
| **Certificate Profile** | `<name>.certprofile.yml` | X.509 certificate profile with subject fields, extensions, validity periods |
| **CA Profile**          | `<name>.caprofile.yml`   | Certificate Authority profile configuration                                 |
| **Keystore**            | `<name>.keystore.yml`    | Keystore configuration settings                                             |

**Examples:**

- `my-cert.certprofile.yml`
- `root_ca.caprofile.yml`
- `production_keystore.keystore.yml`

## Prerequisites

This extension requires
the [YAML extension by Red Hat](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml), which will be
installed automatically as a dependency.

## Usage

Once installed, schema support is automatically activated for files matching the supported patterns. Just create or open
a `.certprofile.yml`, `.caprofile.yml`, or `.keystore.yml` file and start editing!

### Certificate Profile Features

- Certificate subject fields and constraints
- X.509 extensions (Basic Constraints, Key Usage, Extended Key Usage, etc.)
- Subject Alternative Names (DNS, IP, Email, URI, etc.)
- Certificate policies and custom extensions
- Cryptographic parameters and validity periods

### CA Profile (*.caprofile.yml)

Certificate Authority configuration validation

### Keystore (*.keystore.yml)

Keystore configuration validation

## Installation

### From VS Code Marketplace

1. Open VS Code
2. Go to Extensions view (`Ctrl+Shift+X` / `Cmd+Shift+X`)
3. Search for "ACS Schema Support"
4. Click Install

### From VSIX File

**Command Line:**

```bash
code --install-extension acs-schema-support-<version>.vsix
```

**VS Code UI:**

1. Open Extensions view (`Ctrl+Shift+X` / `Cmd+Shift+X`)
2. Click the `...` menu → "Install from VSIX..."
3. Select the `.vsix` file

## Contributing

### Building from Source

```bash
# Install the VS Code Extension Manager
npm install -g @vscode/vsce

# Package the extension
vsce package
```

This creates a `.vsix` file you can install locally.

### Project Structure

```
├── schemas/
│   ├── certificate-profile.schema.json
│   ├── ca-profile.schema.json
│   └── keystore.schema.json
├── images/
│   └── logo-v3-black-text-white-bg.png
└── package.json
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Copyright (c) 2026 Abero Security AB**