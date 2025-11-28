## Server Setup (local)

1. Install `uv` 
- Recommended Package Manager for FastMCP

```bash
pip install uv

```

2. Create project folder and initialized:
  
  ```bash
  uv init .
  ```

3. Install FastMCP:
```bash
  uv add fast-mcp
  ```

4.  Create **main.py** server code using **@server.tool** decorator to define  tool  within a FastMCP server instance .

```bash
from fastmcp import FastMCP

# FastMCP server instance  
server = FastMCP("server instance  ")

@server.tool()
def tool_name( ):

# This command allows the server to be run as an MCP serve
if __name__ == "__main__":
    server.run()


```
  

5. Test server locally using MCP Inspector tool:
  ```
  uv run fastmcp dev main.py  
  ```

6. Claude Desktop integration:
  ```
  uv run fastmcp install claude-desktop main.py
  ```

If interrupted to solve the issue with the uv command not being recognized by Claude Desktop's configuration file.

#### Fixing Claude Desktop Integration Path Issue

- Claude config file needs the absolute path to the uv executable, not just the word uv, especially if it's running within a virtual environment.

- Find the absolute path of uv:
  ```bash
  which uv
  ```
      
- Edit Claude Desktop Config:
  - Navigate to **Settings → Developers → Edit Config**.
  - Replace "**uv**" in the command section with the absolute path found.

- Restart Claude Desktop to apply changes.



##  Fast API Integration

 ### Scenario

- Existing Expense Tracker  powered by Fast API backend that serves web, Android, iOS clients.
- Goal: Integrate with MCP clients like Claude Desktop without rewriting logic.
- The Problem Avoided: Rewriting all the existing add_expense, list_expense, and summarize logic into new MCP-specific tools.

### Solution: FastMCP.from_fastapi()
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

### Benefit

- Saves development time by exposing existing Fast API endpoints as MCP tools automatically.

