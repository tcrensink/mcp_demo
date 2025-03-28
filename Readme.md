# What is MCP?

Model Context Protocol is an network-based protocol for connecting llms and services through apis [as seen here](https://modelcontextprotocol.io/introduction#general-architecture).

**Basic flow:**

- The client sends your question to an llm
- The llm analyzes the available tools and decides which one(s) to use
- The client executes the chosen tool(s) through the MCP server
- The results are sent back to the llm
- The llm formulates a natural language response and is displayed in the client



# Getting started
This demo is based on the official docs: https://modelcontextprotocol.io/quickstart

# installation & environment setup
curl -LsSf https://astral.sh/uv/install.sh | sh
uv init . --python 3.11
uv venv
uv add "mcp[cli]" httpx anthropic python-dotenv ipython 

# development
```bash
# activate the python environment
source .venv/bin/activate

# run inspector to debug services (requires npx)
npx @modelcontextprotocol/inspector uv --directory ${PWD} run weather.py
```
