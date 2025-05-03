[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/isaacwasserman-mcp-vegalite-server-badge.png)](https://mseep.ai/app/isaacwasserman-mcp-vegalite-server)

# Data Visualization MCP Server
[![smithery badge](https://smithery.ai/badge/mcp-server-vegalite)](https://smithery.ai/server/mcp-server-vegalite)

## Overview
A Model Context Protocol (MCP) server implementation that provides the LLM an interface for visualizing data using Vega-Lite syntax.

## Components

### Tools
The server offers two core tools:

- `save_data`
   - Save a table of data agregations to the server for later visualization
   - Input:
     - `name` (string): Name of the data table to be saved
     - `data` (array): Array of objects representing the data table
   - Returns: success message
- `visualize_data`
   - Visualize a table of data using Vega-Lite syntax
   - Input:
     - `data_name` (string): Name of the data table to be visualized
     - `vegalite_specification` (string): JSON string representing the Vega-Lite specification
   - Returns: If the `--output_type` is set to `text`, returns a success message with an additional `artifact` key containing the complete Vega-Lite specification with data. If the `--output_type` is set to `png`, returns a base64 encoded PNG image of the visualization using the MPC `ImageContent` container.

## Usage with Claude Desktop

```python
# Add the server to your claude_desktop_config.json
{
  "mcpServers": {
    "datavis": {
        "command": "uv",
        "args": [
            "--directory",
            "/absolute/path/to/mcp-datavis-server",
            "run",
            "mcp_server_datavis",
            "--output_type",
            "png" # or "text"
        ]
    }
  }
}
```
