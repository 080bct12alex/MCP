# Fast API Integration

## Scenario

- Existing Expense Tracker  powered by Fast API backend that serves web, Android, iOS clients.
- Goal: Integrate with MCP clients like Claude Desktop without rewriting logic.
- The Problem Avoided: Rewriting all the existing add_expense, list_expense, and summarize logic into new MCP-specific tools.

## Solution: FastMCP.from_fastapi()

- A separate file (server.py) is created to bridge/Convert the existing Fast API app to an MCP Server. This requires minimal code.

Code: server.py (The Bridge)

```bash
from mcp.server.fastmcp import FastMCP
 
from main import app # Assuming the existing Fast API app  named 'app' 

mcp = FastMCP.from_fastapi(
    app=app,
    name="FastAPI Expense Tracker"
)

if __name__ == "__main__":
    mcp.run()



```

## Benefit

- Saves development time by exposing existing Fast API endpoints as MCP tools automatically.

