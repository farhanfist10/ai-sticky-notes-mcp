# AI Sticky Notes MCP Server

A custom MCP (Model Context Protocol) server that provides AI-powered sticky notes functionality for Claude Desktop.

## Features

- **Add Notes**: Append new notes to your sticky notes file
- **Read Notes**: View all your saved notes
- **Latest Note Resource**: Access the most recently added note
- **Summary Prompt**: Generate AI prompts to summarize all your notes

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/farhanfist10/ai-sticky-notes-mcp.git
   cd ai-sticky-notes-mcp
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Configuration

Add the following to your Claude Desktop configuration file:

### Windows
`%APPDATA%\Claude\claude_desktop_config.json`

### macOS
`~/Library/Application Support/Claude/claude_desktop_config.json`

### Linux
`~/.config/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "ai-sticky-notes": {
      "command": "python",
      "args": [
        "-m", 
        "mcp.server.fastmcp",
        "/path/to/your/ai-sticky-notes-mcp/main.py"
      ],
      "env": {
        "PYTHONPATH": "/path/to/your/ai-sticky-notes-mcp"
      }
    }
  }
}
```

**Important**: Replace `/path/to/your/ai-sticky-notes-mcp/` with the actual path to your project directory.

## Usage

After configuration, restart Claude Desktop. You'll have access to these tools:

- `add_note(message)`: Add a new note
- `read_notes()`: Read all notes
- Resource `notes://latest`: Access the latest note
- Prompt for summarizing notes

## Example

```python
# The server will create a notes.txt file in the same directory
# All notes are stored persistently in this file
```

## File Structure

```
ai-sticky-notes-mcp/
├── main.py           # Main MCP server implementation
├── requirements.txt  # Python dependencies
├── README.md        # This file
└── notes.txt        # Auto-generated notes storage (created when first used)
```

## How It Works

This MCP server uses the FastMCP framework to expose tools that:

1. **Tools**: Functions that Claude can call to add/read notes
2. **Resources**: Direct access to the latest note
3. **Prompts**: Pre-built prompts for note summarization

The notes are stored in a simple text file (`notes.txt`) that gets created automatically when you first use the server.

## Contributing

Feel free to open issues or submit pull requests to improve this MCP server!

## License

MIT License - feel free to use this project as you wish.
