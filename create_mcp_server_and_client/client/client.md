# Building MCP Clients
MCP clients is essential for connecting chatbots to MCP servers. Until now, accessing to the servers  using of the Claude Desktop client; however, NOW exploring how to create a custom client for better integration.

# Using MCP Libraries
You can create clients using official MCP libraries or explore the Langchain MCP adapters, which offer a lightweight wrapper to make MCP tools compatible with Langchain and Langraft ;  This approach is preferred for its simplicity and strong connection to the Langchain and Langraph ecosystem, which is beneficial since  already working with these technologies.

# Chatbot Development
Creating a chatbot that can engage in normal conversation while also connecting to two MCP servers—one for mathematical calculations and the other for expense tracking. Connect with a local math server and a remote expense tracking server, eventually integrating everything into a user-friendly GUI.  connect additional MCP servers for enhanced functionality.

## Connecting to Local Server
A local MCP server for basic arithmetic calculations has been set up and tested to ensure functionality before building a client. The client will establish a connection to this server by following a series of steps that include installing necessary dependencies, creating a new folder, initializing UV, and writing the client code. The process involves using async functionality in Python to connect the client to the server, fetch its tools, and utilize them through an LLM.

## Integrating Multiple Servers
The process of connecting multiple MCP servers has been updated to allow for flexibility in handling multiple tool calls. Previously limited to a single tool call, the code now utilizes a loop to manage execution based on the number of tool call items in the response, thus accommodating suggestions from the LLM for executing multiple tools at once.

## Connecting to Remote Server
Additional flexibility is gained by connecting a remote MCP server for expense tracking, which has been previously deployed. This involves adding its configuration to the existing code, enabling the client to utilize additional expense tracking tools alongside mathematical operations. Furthermore, a new server, 'Manim', will be connected to the client, allowing for the creation of animation videos, demonstrating the capability to leverage remote servers for diverse functionality.

## Streamlit GUI Implementation
The content discusses the conversion of existing logic into a Streamlit-based GUI application for building an MCP client. The code has been written in a new file, client2.py, retaining the same logic while incorporating some descriptive elements with the help of ChatGPT. The demonstration includes how to run the application, view expenses, and add more MCP servers.