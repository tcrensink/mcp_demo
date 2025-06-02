This repo contains a very simple exploration of MCP, including the high-level architecture of MCP as well as a short working example from the documentation.

# What is MCP?

Model Context Protocol is an network-based protocol for connecting llms and services through apis [as seen here](https://modelcontextprotocol.io/introduction#general-architecture).

**Basic flow:**

- The client sends your question to an llm
- The llm analyzes the available tools and decides which one(s) to use
- The client executes the chosen tool(s) through the MCP server
- The results are sent back to the llm
- The llm formulates a natural language response and is displayed in the client



# Getting started
This demo is based on the official docs: https://modelcontextprotocol.io/quickstart.

## Requirements

- `uv` for managing python installation/environment
- an `ANTHROPIC_API_KEY`
- `npx` (optional) for running service inspector dashboard

## Installation
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv init . --python 3.11
uv venv
uv add "mcp[cli]" httpx anthropic python-dotenv ipython 
```
Create a `.env` file with your anthropic api key:
```
ANTHROPIC_API_KEY=<api key, no quotes>
```

## Run Demo
run the Claude client that connects to the weather api server:
```bash
uv run client.py weather.py
```


# Development & Debug
Use the virtual env and uv when running scripts, e.g.:
```bash
source .venv/bin/activate
uv run my_script.py
```

You can use the Inspector to test server logic (requires `npx` to be installed). View server api, logs, and request history:
```bash
npx @modelcontextprotocol/inspector uv --directory ${PWD} run weather.py
```
