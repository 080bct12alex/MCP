# Building the Expense Tracker MCP Server with FastMCP and Fast API Integration

A  MCP server  for an expense tracker chatbot that allows users to manage their expenses through natural language like 'I bought milk for ₹20', and the server will log this information, enabling them to later inquire about their total expenses or specific categories. 

## MCP Server Features
 - Adding expenses, listing expenses, and summarizing monthly spending. 
 - Additional features such as editing and deleting expenses, as well as adding credit, can be implemented to enhance functionality. 

- In the MCP server development, a SQLite database is used for storing transactions and expenses due to its simplicity. 

 ## MCP Server Core (main.py)
- Uses FastMCP,  SQLite for storage.


## MCP Server : Expense Tracker

  Create **main.py** 

```bash
from fastmcp import FastMCP

mcp = FastMCP("ExpenseTracker")




if __name__ == "__main__":
    server.run()


```

### 1.  Database Initialization 
- Use SQLite database file named expenses.db.

- **Database initialization code**
       
    - database.py or integrated into (main.py):
```bash
import os
import sqlite3

DB_PATH = os.path.join(os.path.dirname(__file__), "expenses.db")

def init_db():
    with sqlite3.connect(DB_PATH) as c:
        c.execute("""
            CREATE TABLE IF NOT EXISTS expenses(
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                date TEXT NOT NULL,
                amount REAL NOT NULL,
                category TEXT NOT NULL,
                subcategory TEXT DEFAULT '',
                note TEXT DEFAULT ''
            )
        """)

# Call once at server startup
init_db()   

```

 
 
###  2. Add and List All Expenses

```bash
@mcp.tool()
def add_expense(date, amount, category, subcategory="", note=""):

@mcp.tool()
def list_expenses(date):


```


### 3. Filtering and Summarizing
-  Updated List Expenses:
        
       List Expenses by Date Range

```bash
@mcp.tool()
def list_expenses(start_date, end_date):

```

#### Summarize Expenses
```bash
@mcp.tool()
def summarize(start_date, end_date, category=None):

```
- Testing

  - Test summarize:
    - "Total expense on Education in the last 10 days."
  - Confirm Claude calls summarize with proper parameters and receives correct totals.

### 4. Consistent Categories with Resources

4.1 Create Categories JSON File (categories.json):
```bash
{
  "Transportation": ["Cab Ride"],
  "Entertainment": ["Movies"],
  "Health": ["Medicine"]
}
```

4.2 Add Resource to MCP Server
```bash
import os

CATEGORIES_PATH = os.path.join(os.path.dirname(__file__), "categories.json")
  # Ensure file exists

@mcp.resource("expense://categories", mime_type="application/json")
def categories():
    # Read fresh each time so you can edit the file without restarting
    with open(CATEGORIES_PATH, "r", encoding="utf-8") as f:
        return f.read()

# This provides Claude access to structured categories

```

4.3 Testing 

- Restart Claude Desktop.
- Access resource through UI (+ button → Expense Tracker → categories resource).
- Test "Add expense" asking Claude to scrutinize category using the resource.
- Claude now consistently chooses from approved categories and sub-categories.

## 5. Fast API Integration

5.1 Scenario

- Existing Expense Tracker  powered by Fast API backend that serves web, Android, iOS clients.
- Goal: Integrate with MCP clients like Claude Desktop without rewriting logic.
- The Problem Avoided: Rewriting all the existing add_expense, list_expense, and summarize logic into new MCP-specific tools.

5.2 Solution: FastMCP.from_fastapi()
- A separate file (server.py) is created to bridge/Convert the existing Fast API app to an MCP Server. This requires minimal code.

Code: server.py (The Bridge / FastMCP)

```bash
from mcp.server.fastmcp import FastMCP
 
from main import app 

mcp = FastMCP.from_fastapi(
    app=app,
    name="FastAPI Expense Tracker"
)

if __name__ == "__main__":
    mcp.run()



```

Code: main.py (FastAPI)

```bash




```



5.3 Benefit

- Saves development time by exposing existing Fast API endpoints as MCP tools automatically.
    -  The existing (add, list, summarize) exposed via the Fast API endpoints is automatically converted into accessible MCP tools, making the application immediately compatible with MCP clients like Claude Desktop.

5.4 Conclusion 
- Fast-MCP is compatible with Fast API. This allows existing Fast API applications  to be easily converted into an MCP server without rewriting the core logic.