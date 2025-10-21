# kc - Keychain Environment Variable Manager

`kc` is a secure command-line tool for managing environment variables using macOS Keychain. It allows you to store sensitive environment variables (like API keys, tokens, and secrets) in the system keychain rather than in plain text files or environment variables.

## Features

- Securely store environment variables in macOS Keychain
- Add, delete, list, and show environment variable values
- Export variables directly to your shell environment
- Dedicated keychain storage to keep environment variables separate
- Interactive keychain creation and management

## Installation

Simply download `kc` to somewhere in your `$PATH`, and make sure it's executable. For example:

```
sudo curl -o /usr/local/bin/kc https://raw.githubusercontent.com/mattias-lidman/kc/refs/heads/main/kc
sudo chmod +x /usr/local/bin/kc
```

To uninstall, simply remove the `kc` file:

```
sudo rm /usr/local/bin/kc
```

## Usage

### Basic Commands

```bash
kc                   # Show help message
kc add VAR_NAME      # Add a new environment variable
kc delete VAR_NAME   # Delete an environment variable
kc list              # List all stored variables
kc export VAR_NAME   # Export variable(s) to shell environment
kc show VAR_NAME     # Display the value of variable(s)
kc delete-keychain   # Delete the entire keychain
```

### Examples

Add a new variable:
```bash
kc add API_KEY
# You'll be prompted to enter the secret value
```

List all stored variables:
```bash
kc list
```

Export variables to your shell:
```bash
. kc export API_KEY
# Note: The dot (.) or source command is required for exporting
```

Show variable values:
```bash
kc show API_KEY
# Displays: API_KEY=your_secret_value
```

### Configuration

By default, `kc` uses a keychain named `kcEnvironmentVariables.keychain`, which is automatically created the first time you run `kc`.
You can customize this by setting the `KC_KEYCHAIN_NAME` environment variable in your `.zshrc`:

```bash
export KC_KEYCHAIN_NAME="my-custom-keychain"
```

## Security

- All secrets are stored in the macOS Keychain, which provides encryption at rest
- Variables are stored in a dedicated keychain for better organization
- Sensitive values are never displayed in command history
- Password input is hidden when adding new variables

## Requirements

- macOS (uses the `security` command-line tool)
- Zsh shell

## License

MIT License. See `LICENSE` file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
