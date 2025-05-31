# MCP Client

A Python client for interacting with MCP servers, featuring a weather tool server as an example. The client uses Anthropic's Claude API for natural language queries and can connect to any compatible MCP server script.

## Features

- Interactive chat client for MCP servers
- Example weather server (`server/weather.py`) with:
  - US state weather alerts
  - Location-based weather forecasts (via NWS API)
- Extensible: connect to any MCP-compatible server script
- Uses Anthropic Claude API for natural language understanding

## Requirements

- Python 3.12+
- [Anthropic API key](https://docs.anthropic.com/claude/docs/access-claude-api)
- MCP Python package (`mcp>=1.9.2`)
- [uv](https://github.com/astral-sh/uv) (for running with isolated environments, optional but recommended)

## Installation

1. **Clone the repository:**
   ```sh
   git clone <your-repo-url>
   cd mcp-client
   ```

2. **Install dependencies:**
   ```sh
   uv pip install -r requirements.txt
   ```
   Or, if you use `uv` and `pyproject.toml`:
   ```sh
   uv pip install
   ```

3. **Set up your Anthropic API key:**
   - Create a `.env` file in the project root:
     ```
     ANTHROPIC_API_KEY=your-anthropic-api-key-here
     ```
   - The `.env` file is in `.gitignore` and will be loaded automatically.

## Usage

### Start the Weather Server

The example weather server is located at `server/weather.py`. It provides two tools: `get_alerts` and `get_forecast`.

### Run the Client

You can connect the client to the weather server using:

```sh
uv run client.py ./server/weather.py
```

Or, if you prefer plain Python:

```sh
python client.py ./server/weather.py
```

You should see output like:

```
Connected to server with tools: ['get_alerts', 'get_forecast']

MCP Client Started!
Type your queries or 'quit' to exit.
```

### Example Queries

- `What is the weather in New York?`
- `Are there any weather alerts for CA?`
- `Give me the forecast for latitude 40.7, longitude -74.0`

### Exiting

Type `quit` to exit the chat loop.

## Project Structure

```
.
├── client.py            # Main MCP client
├── server/
│   └── weather.py       # Example weather MCP server
├── pyproject.toml       # Project metadata and dependencies
├── .env                 # (Not committed) Your API keys
├── .gitignore
└── README.md
```

## Development

- The client loads environment variables from `.env` using `python-dotenv`.
- The weather server uses the US National Weather Service API and requires internet access.

## Troubleshooting

- **Anthropic API errors:**  
  Ensure your API key is valid and has sufficient credits.
- **Python version:**  
  The project requires Python 3.12 or newer.
- **Network issues:**  
  The weather server needs to reach `https://api.weather.gov`.

## License


