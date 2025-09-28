## Server Setup (local)

1. Install `uv` 
- Recommended Package Manager for FastMCP

```
pip install uv

```

2. Create project folder and initialized:
  
  ```
  uv init .
  ```

3. Install FastMCP:
```
  uv add fast-mcp
  ```

4.  Create **main.py** server code using **@server.tool** decorator to define  tool  within a FastMCP server instance .

```
from fastmcp import FastMCP

# FastMCP server instance  
server = FastMCP("server instance  ")

@server.tool()
def tool_name( ):


if __name__ == "__main__":
    server.run()





```
  

5. Test server locally using MCP Inspector tool:
  ```
  uv run fast-mcp debug main.py
  ```

6. Claude Desktop integration:
  ```
  uv run fast-mcp install claude-desktop main.py
  ```

If interrupted to solve the issue with the uv command not being recognized by Claude Desktop's configuration file.

#### Fixing Claude Desktop Integration Path Issue

- Claude config file needs the absolute path to the uv executable, not just the word uv, especially if it's running within a virtual environment.

- Find the absolute path of uv:
  ```
  which uv
  ```
      
- Edit Claude Desktop Config:
  - Navigate to Settings → Developers → Edit Config.
  - Replace "uv" in the command section with the absolute path found.

- Restart Claude Desktop to apply changes.