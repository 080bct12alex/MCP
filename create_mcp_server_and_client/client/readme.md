# MCP Client Development: 
Building MCP clients to connect custom chatbots to MCP servers, moving beyond the built-in client within Claude Desktop that handles normal chatting and interacts with multiple attached MCP servers .

# Choosing the Client Library
Multiple libraries exist for client creation, including the official MCP library, langchain-mcp, and langchain-mcp-adapters .
- The langchain-mcp-adapters library provides a lightweight wrapper that makes MCP tools compatible with LangChain and LangGraph .
    - This wrapper is chosen because it is the simplest method and is closely integrated with the LangChain/LangGraph ecosystem, which  is already familiar with  .

# Client Architecture and Servers
The  client connects to servers of various types to provide comprehensive functionality:

- Two main servers are attached to the chatbot behind the scenes: a Math MCP Server for calculations and an Expense Tracking MCP Server for expense management  .
   - The Math Server is set up as a Local MCP Server, while the Expense Tracking Server is a Remote MCP Server s .
- The entire application is converted into a Streamlit based Graphical User Interface (GUI) .

| **Server Type** | **Server** | **Transport Protocol** | **Purpose**                                      |
| --------------- | ------------------ | ---------------------- | ------------------------------------------------ |
| **Local**       | Math Server        | stdio                  | Arithmetic calculations (e.g., multiply, divide) |
| **Remote**      | Expense Tracking   | streamable_http        | Add, list, and summarize expenses                |
| **Third-Party** | Manim Server       | stdio                  | Generate animation videos                        |
		
## Step-by-Step Implementation: Connecting Local Servers
The process of connecting the client to a local MCP server (Math Server) involves several steps:

- **Setup and Initialization**: Install necessary dependencies (LangChain, Streamlit, etc.) and initialize the working directory using uv init .

- **Server Configuration**: Define the server configuration, specifying the name (e.g., Math), the transport (stdio), and the command/arguments needed for the client to start the local server .

   When communicating with local servers over stdio, the client is responsible for starting the server. 

- **Client Instantiation**: Create an instance of MultiServerMCPClient using the server configuration dictionary.

- Tool Fetching: Fetch all available tools from the connected server using await client.get_tools()  . These tools are typically stored in a dictionary keyed by the tool name for easy lookup  .

### LLM Tool Invocation Flow
The core logic involves the LLM identifying and invoking the correct MCP tool:



![MCP Client Tool Invocation Process](/create_mcp_server_and_client/client/images/MCP%20Client%20Tool%20Invocation%20Process.png)


















