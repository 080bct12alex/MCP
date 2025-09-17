# Introduction to MCP (Model Context Protocol)

##  MCP (Model Context Protocol)
- MCP (Model Context Protocol) is a framework designed to streamline communication between AI tools (such as chatbots) and external systems (servers).
- It solves problems related to context assembly, tool fragmentation, and integration.
- By managing interactions on the server side, MCP reduces the need for extensive client-side coding, simplifies maintenance, and ensures seamless communication
   across various AI-enabled platforms.
- It is expected to become an industry standard in the upcoming years, facilitating more efficient AI tool integration into everyday tasks and workflows.

## Definition of MCP Server
- An MCP server is a system or platform that provides functionalities or resources that an AI tool (host) interacts with through an MCP client.
-  These servers can be local (operating on the same machine as the host) or remote (operating over a network).
-  The server handles requests from the host via the MCP client, executing tasks such as retrieving data, updating resources, or processing operations.
-  MCP servers make it possible for AI tools to connect with and utilize services like GitHub, Slack, or Google Drive without the need for custom code integration.

## Motivation and Popularity
- MCP is gaining popularity, expected to become an industry standard in upcoming years.
### MCP Tool Integration
- Minimal code needed to integrate various MCP tools like Twitter and GitHub  .
- Simplifies tool integration while ensuring adaptability.
### Real life Example
### AI Learning Challenges
- Rapid AI growth overwhelms learners with new tools, libraries, and research.
- AI expertise roadmap becomes outdated due to fast advancements.
### AI Newsletters Strategy
- Stay updated with AI by using AI newsletters.
- Automate weekly newsletters using MCP.
### Newsletter Creation Process
1. **Research**: AI gathers and compiles information.
2. **Editing**: Notes are edited into a draft.
3. **Design**: Final draft is formatted into a user-friendly design.
- MCP simplifies the process.

# MCP Plan
- **Why**: Solves fragmentation and context assembly problems.
- **What**: Defines MCP’s functionality and utility.
- **How**: Expected advancements in MCP’s integration.

## WHY MCP
### ChatGPT's Impact
- AI adoption boosts productivity for professionals (lawyers, coders, teachers).
  
### API Revolution
- Microsoft, Google integrate AI into tools like Word, Gmail, and Drive.
- AI is embedded in familiar software, enhancing user experience.

## Problem of Fragmentation
- Multiple isolated AI tools cause inefficiency in context integration.
#### Understanding Context 
- **Context**: Information used by AI to generate responses.
- **Professional Use**: Complex tasks require multiple systems for efficient completion.
#### Challenges in Context Assembly
- Developers spend excessive time assembling context across various systems.

## solution
## Function / Tool Calling Concept
- OpenAI’s function calling integrates external APIs, enhancing tool versatility.
- less efficient than MCP 
- Managing multiple tools requires a unified system like MCP.

## Benefits of MCP
- Reduces maintenance overhead by simplifying server-side management.
- Enhances security with a unified connection system.

## MCP's Growing Popularity
- Claude Desktop, Cursor support MCP, pressuring others platforms  to adopt it.

# MCP Servers
- MCP-compliant servers enable seamless AI-tool connections.

# MCP Architecture Overview
- Communication between **host** (AI chatbot) and **server** (task-executing platform).
- **Client** facilitates communication between host and server.

### Client-Server Relationship
- One client connects to one server at a time, similar to a SIM card in a phone.
  
### MCP Architecture Benefits
- **Decoupling**: Independent communication channels ensure safety.
- **Scalability**: Parallel processing for faster task execution.

### Introduction to Primitives
- **Tools**: Enable server interactions (e.g., GitHub functionalities).
- **Resources**: Provide static data like documents.
- **Preps**: Offer templates to structure AI behavior.

### Standard Operations in MCP
- **tools/list**: List available tools.
- **resources/list**: List available documents.
- **Subscribe/Unsubscribe**: Monitor changes in resources.

### Data Layer of MCP
- Uses **JSON RPC 2.0** for communication between client and server.
  #### Understanding JSON RPC
- Facilitates distributed application development with JSON-formatted requests/responses.

### Transport Layer of MCP
- Ensures effective communication of JSON RPC messages between client and server.

### Local vs Remote Servers
- **Local Servers**: Operate on the same machine.
- **Remote Servers**: Communicate over HTTP/SSE.

# Conclusion
- MCP simplifies AI integration, solving tool fragmentation and context assembly challenges.
- Gaining atraction, MCP could become the standard for AI integration in various fields.
