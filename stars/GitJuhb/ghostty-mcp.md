---
project: ghostty-mcp
stars: 1
description: |-
    null
url: https://github.com/GitJuhb/ghostty-mcp
---

# Ghostty MCP Server

A Model Context Protocol (MCP) server for [Ghostty](https://ghostty.org), the fast, native, feature-rich terminal emulator. This server enables AI assistants like Claude to interact with and control Ghostty through a standardized interface.

## Features

- **Configuration Management**: Get and set Ghostty configuration values
- **Theme Control**: Switch between themes and manage light/dark modes
- **Keybinding Management**: Add, modify, or remove custom keybindings
- **Command Execution**: Run commands directly in Ghostty
- **Window Management**: Create, split, and manage Ghostty windows
- **Live Reload**: Reload configuration without restarting
- **Discovery**: List available themes, keybindings, and configurations

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/ghostty-mcp.git
cd ghostty-mcp
```

2. Install dependencies:
```bash
npm install
```

3. Build the project:
```bash
npm run build
```

## Configuration

### Claude Desktop Configuration

Add the following to your Claude Desktop configuration file:

**macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
**Linux**: `~/.config/claude/claude_desktop_config.json`
**Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "ghostty": {
      "command": "node",
      "args": ["/path/to/ghostty-mcp/dist/index.js"],
      "env": {}
    }
  }
}
```

Replace `/path/to/ghostty-mcp` with the actual path to your cloned repository.

## Available Tools

### `ghostty_config`
Get or set Ghostty configuration values.

**Parameters:**
- `key` (string, required): Configuration key (e.g., "font-size", "theme", "window-decoration")
- `value` (string, optional): Configuration value. If not provided, returns current value

**Examples:**
```
// Get current font size
ghostty_config(key: "font-size")

// Set font size to 14
ghostty_config(key: "font-size", value: "14")
```

### `ghostty_theme`
Change Ghostty theme.

**Parameters:**
- `theme` (string, required): Theme name to apply
- `mode` (string, optional): Theme mode - "light", "dark", or "auto"

**Examples:**
```
// Apply dracula theme
ghostty_theme(theme: "dracula")

// Set github_light for light mode
ghostty_theme(theme: "github_light", mode: "light")
```

### `ghostty_keybind`
Manage Ghostty keybindings.

**Parameters:**
- `action` (string, required): Action to bind (e.g., "copy", "paste", "new_tab")
- `key` (string, required): Key combination (e.g., "cmd+c", "ctrl+shift+t")
- `remove` (boolean, optional): If true, removes the keybinding

**Examples:**
```
// Add keybinding for new tab
ghostty_keybind(action: "new_tab", key: "cmd+t")

// Remove keybinding
ghostty_keybind(action: "new_tab", remove: true)
```

### `ghostty_command`
Execute commands in Ghostty.

**Parameters:**
- `command` (string, required): Command to execute
- `wait` (boolean, optional): Whether to wait for command completion

**Examples:**
```
// Run a command
ghostty_command(command: "ls -la")

// Run and wait for completion
ghostty_command(command: "npm install", wait: true)
```

### `ghostty_window`
Manage Ghostty windows and splits.

**Parameters:**
- `action` (string, required): One of:
  - "new": Create new window
  - "close": Close current window
  - "split-horizontal": Split horizontally
  - "split-vertical": Split vertically
  - "focus-next": Focus next pane
  - "focus-previous": Focus previous pane
- `config` (object, optional): Additional window configuration

**Examples:**
```
// Create new window
ghostty_window(action: "new")

// Split vertically
ghostty_window(action: "split-vertical")
```

### `ghostty_reload`
Reload Ghostty configuration.

**Parameters:**
- `scope` (string, optional): What to reload - "config", "theme", or "all" (default: "all")

**Examples:**
```
// Reload all configuration
ghostty_reload()

// Reload only theme
ghostty_reload(scope: "theme")
```

### `ghostty_list`
List available themes, keybindings, or configuration.

**Parameters:**
- `type` (string, required): What to list - "themes", "keybindings", or "config"
- `filter` (string, optional): Optional filter for results

**Examples:**
```
// List all themes
ghostty_list(type: "themes")

// List keybindings containing "tab"
ghostty_list(type: "keybindings", filter: "tab")
```

## Development

### Running in Development Mode

```bash
npm run dev
```

### Building

```bash
npm run build
```

### Testing with MCP Inspector

You can test this server using the [MCP Inspector](https://github.com/modelcontextprotocol/inspector):

```bash
npx @modelcontextprotocol/inspector node dist/index.js
```

## Requirements

- Node.js 18 or later
- Ghostty terminal emulator installed
- Access to Ghostty CLI commands

## Platform Support

This MCP server supports:
- macOS
- Linux
- Windows (with appropriate path adjustments)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - see LICENSE file for details

## Acknowledgments

- [Ghostty](https://ghostty.org) by Mitchell Hashimoto
- [Model Context Protocol](https://modelcontextprotocol.io) by Anthropic
