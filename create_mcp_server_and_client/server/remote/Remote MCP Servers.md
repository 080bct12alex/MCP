### Building and Deploying a remote MCP server .

### **1\. Local vs Remote MCP Servers**

* **Local MCP Server**

  * Runs on the same machine as host and client.

  * Faster (communication stays on the same machine).

* **Remote MCP Server**

  * Runs on a different machine (usually over the internet).

  * Advantages:

    * Supports multiple clients simultaneously.

    * Runs on powerful machines → can handle compute-intensive tasks.

  * Disadvantages:

    * Slower than local servers (network latency).

---

### **2\. Steps to Create a Remote MCP Server**

1. **Install dependencies**

   * `pip install uv`

   * `uv add mcp`

2. **Setup project**

   * Create a folder → open in VS Code.

   * Initialize with `uv init .`

3. **Write server code** (main.py)
   * Both local and remte server can be made using fast_mcp library ; So identical code
   * Key difference from local server:

     * Local → `mcp.run()` (default: stdio transport).

     * Remote → use `transport = HTTP` with host `0.0.0.0` and a defined port.

4. **Run server**

   * `fastmcp run main.py --transport http --host 0.0.0.0 --port <number>`

   * `uv run main.py`

5. **Debug with MCP Inspector**

   * `uv run fastmcp dev main.py`

   * Select transport: `streamable http`.

   * Check tools & resources.

---

### **3\. Deployment with Fast MCP Cloud**

1. Push code to GitHub.

   * `git init`, `git add.`, `git commit -m "initial commit"`.

   * Add remote & push: `git remote add origin <url>` → `git push origin main`.

2. Go to fastmcp.cloud.

   * Connect GitHub account.

   * Select repository → Deploy.

   * Set entry point (`main.py`).

   * Optional: change server name, discoverability.

3. Once deployed → server URL generated → shareable.

---

### **4\. Using Remote MCP Server with Claude Desktop**

*For paid plan:*
* Go to ***Settings → Connectors → Add Custom Connector***.

* Provide server name \+ URL.

* Works only with **Pro plan** currently.

*For Free plan :*
- *using ***Proxy Server*** between claude desktop and our remote mcp* 
![Proxy Server Architecture](https://i.ibb.co/FbgjSVNC/Proxy-Server-Architecture.png)

- To set up the proxy:

    - A new file proxy server code is added that uses fast_mcp.as_proxy() to connect to the remote server's URL and define the proxy's name .
The proxy runs as a local server using mcp.run(), implying STDIO transport to confirm connectivity to the remote server.
It's tested in MCP Inspector (uv run fast_mcp dev main.py) using STDIO transport.
The proxy is then installed into Claude Desktop using uv run fast_mcp install-cloud-desktop main.py 
- *Run proxy server* in claude desktop ***same way of running local server***. 
---

**5\. Converting Local Expense Tracker into Remote MCP**

* Copy Expense Tracker  code (from local) into main.py.

* Copy  `categories.json` file.

* Run locally → test with MCP Inspector.

* If working → push to GitHub → deploy with Fast MCP Cloud .

- Problem Solved:
   
   *Using same main.py code from local*
   - *Database Read-Only Mode*
       - *After deploying , claude desktop saying " unable to  add expenses because the database is set to read-only mode in deployment server"* . 
   - *Synchronous/Blocking Server*
       - The server is identified to have some limitations like synchronous operation; only process one user's request at a time, blocking other users until the current operation completes 
            - The server is converted to an asynchronous architecture using Python's async/await features and database operations are made parallel using the aio_sqlite library .
                - *This change allows the MCP server to handle multiple concurrent users efficiently*                         
 


- Improvement Needed:

  - *Authentication Issues*

     - Absence of a user_id column and user authentication in the current setup, leading to potential data visibility issues among multiple users, indicating a need for implementing an authentication mechanism.
         - Implementing authentication to verify user identities before logging expenses 
 
  - Building custom MCP clients (to avoid reliance on Claude Desktop)
---

 **Conclusion**
- From a coding perspective, local and remote MCP servers appear almost similar as both can be made by using fast_mcp library, but need to implement some changes  with the primary difference being the transport configure ( \= transport → HTTP) to set up the remote server .

* Fast MCP Cloud simplifies deployment.

* Once deployed, servers can be shared globally via a URL.