# Introduction(why,what) to MCP and its Architecture
##  MCP (Model Context Protocol)
- MCP (Model Context Protocol) is a framework designed to streamline communication between AI tools (such as chatbots) and external systems (servers).
- It solves problems related to context assembly, tool fragmentation, and integration.
- By managing interactions on the server side, MCP reduces the need for extensive client-side coding, simplifies maintenance, and ensures seamless communication
   across various AI-enabled platforms.
- It is expected to become an industry standard in the upcoming years, facilitating more efficient AI tool integration into everyday tasks and workflows.

##  MCP Server
- An MCP server is a system or platform that provides functionalities or resources that an AI tool (host) interacts with through an MCP client.
-  These servers can be local (operating on the same machine as the host) or remote (operating over a network).
-  The server handles requests from the host via the MCP client, executing tasks such as retrieving data, updating resources, or processing operations.
-  MCP servers make it possible for AI tools to connect with and utilize services like GitHub, Slack, or Google Drive without the need for custom code integration.

## MCP Popularity and Motivation
- The motivation behind starting learning is the significant rise in popularity of the term MCP over the past year, which is expected to become an industry standard in the upcoming years.
- This means that every player in the industry will need to integrate MCP into their software.

## MCP Tool Integration
- Make it easy to automate weekly AI-generated newsletters.
- Integrating various MCP tools only requires writing a simple configuration file, where minimal code is needed for each tool, such as Twitter or GitHub.
- This process enables seamless operation of multiple tools without making extensive changes in code, ensuring the MCP framework remains powerful and adaptable to future server updates.
- The ease of integration raises inquiries about the potential applications of MCP.
### Real Life Example
### AI Learning Challenges
The rapid growth of AI leads to an overwhelming challenge for those aiming to master the field, as new products, libraries, and research papers emerge daily. Creating a roadmap for becoming an AI expert can quickly become obsolete due to the fast pace of developments. The uncertainty surrounding how to stay current with advancements poses a significant problem for learners.
### AI Newsletters Strategy
- To stay updated with the rapid pace of AI developments, utilizing various AI newsletters, automate the newsletter creation process using MCP, enabling a regular output of valuable content for learning.
### News Letter Creation Process
The process of creating a newsletter will be divided into three stages: research, editing, and design.
1. **Research**: An AI tool will conduct research based on provided prompts, compiling notes from various sources.
2. **Editing**: These notes will be edited into a final draft.
3. **Design**: The final draft will then be designed into a user-friendly format.

This is done easily using MCP.

---

## Plan for MCP
- Focusing on the **'Why'**, **'What'**, and **'How'** of MCP:
1. **Why** MCP is needed: The necessity of the Model Context Protocol (MCP) by exploring the problems it addresses.
2. **What** MCP entails: The functionality and utility of MCP.
3. **How** MCP will evolve: Expected advancements and its integration into industries.

## WHY MCP
 Beginning from the inception of ChatGPT up to the present.
### ChatGPT's Impact
 - Professional adoption emerged, revealing its utility beyond mere entertainment.
 - Users, including lawyers, coders, and teachers, experienced notable efficiency improvements, realizing the chatbot's potential as a valuable work partner.
 - This collective transition contributed to a productivity boom worldwide, allowing tasks to be completed in half the time.
#### API Revolution and Integration
- The release of ChatGPT and its API by OpenAI marked a pivotal moment in software adaptation, enabling various companies to integrate intelligent chat capabilities into their existing software. Microsoft led the charge by adding AI features to its tools like Word and Excel, while Google followed suit with Gmail and Drive, making AI more accessible beyond just ChatGPT. Consequently, AI became embedded in the software users were already familiar with, significantly enhancing its presence in everyday applications.
### Problem of Fragmentation
- The emergence of multiple AI-enabled tools like Notion and Slack has led to a fragmentation issue, where each tool operates within its own isolated AI environment.
- Users must navigate through these disparate systems to merge information and solve tasks, deviating from the initial vision of a unified AI agent that understands and resolves issues comprehensively. Instead of a single, cohesive solution, users are faced with the challenge of managing several separate AI tools.

#### Understanding Context 
- Creating a unified AI agent poses challenges, particularly the issue of **context**, a fundamental concept in the Model Context Protocol (MCP).
- Context encompasses all information available to the AI when generating a response, including conversation history and external documents.

For example, when discussing a topic like Gen AI, the AI uses previous interaction details to understand and respond appropriately to user inquiries.

### Context Complexity in Professional Use
- In a software development scenario, a developer tasked with implementing two-factor authentication must navigate multiple tools and resources, including Jira for ticket assignments, a code repository for current schemas, security guidelines from a document, and collaboration through Slack.
- The context of this task is complex, requiring the integration of information from various sources to successfully complete the implementation. By leveraging AI tools like ChatGPT, the developer can streamline the process by extracting relevant information from these platforms and asking targeted questions to enhance efficiency.
### Challenges of Context Assembly
- The main challenge lies in **context assembly**, as developers now act as human APIs, spending excessive time collating context for AI systems instead of focusing on product development. 
- The dispersed nature of context across various systems complicates the task of providing AI with relevant information, making it nearly impossible to scale this manual copy-pasting process as projects grow.
- Ideally, an AI like ChatGPT should autonomously gather necessary context, alleviating the burden of manual context assembly.
### Solution
### Function Calling Concept
- OpenAI's function calling allows LLMs to not only chat but also execute tasks by connecting to external functions, transforming them into versatile tools.
-  This innovative approach promotes context assembly, enabling streamlined integration of various APIs to activate different functions across AI chatbots, ultimately addressing challenges in software development and enhancing productivity.
-  However, integrating multiple tools can lead to increased complexity in managing code and maintenance, highlighting the need for a more cohesive solution like the Model Context Protocol (MCP).

## Benefits of MCP
- The Model Context Protocol (MCP) offers significant advantages by handling all the heavy lifting on the server side, requiring no client-side integration work.
- This results in fewer required integrations, reduced maintenance overhead, and lower costs as updates and connection issues are managed by the service providers.
- Additionally, it  simplified management of connections via a single JSON configuration file , enhanceing security .

### MCP's Growing Popularity
MCP is rapidly gaining attraction as renowned AI chatbots like Claude Desktop and Cursor publicly support it, creating pressure on other services  to adapt. The shift towards utilizing AI tools means users will increasingly rely on chatbots to access and manage documents instead of traditional methods, indicating a future where MCP could become the industry standard in upcoming years.

## MCP Servers
- As users increasingly access AI tools, it's crucial to create MCP-compliant servers via APIs to enable seamless connections without requiring custom code.
- The growth of MCP servers across various services enhances the ecosystem, allowing new AI chatbots to easily connect with multiple servers . This interconnectedness benefits both the tools and the MCP framework.

---
# MCP Architecture Overview
- Key topics include MCP architecture, the communication between clients and servers in a step-by-step decoding process, and advanced MCP features.

## Detailed MCP Architecture
The MCP architecture is divided into three parts.
- It begins with a basic version, gradually incorporating more complexities to provide a comprehensive understanding of the framework.

### Basic Architecture Components
The architecture of the Model Context Protocol (MCP) consists of two fundamental components: the **host** and the **server**. Understanding these components is crucial for grasping their functional relationship in processing user interactions.
#### Host and Server Roles
- The host refers to AI chatbots that users interact with for queries.
- while the server is a tool that executes tasks.
- The host can be a standard AI chatbot or a custom-built one, and
- communication occurs between the host and the server, which can be any platform capable of managing tasks like Git, Slack, or Google Drive.
#### Communication Process
- In the MCP architecture, communication primarily occurs between the host and a server, with the host delegating requests to a helper, the **MCP Client**, to retrieve required information.
- For example, when the user queries about new commits in a Git repo, the host directs the MCP Client to check the GitHub server for updates, as the host lacks this specific knowledge.
##### Client's Role in Communication
- The client facilitates communication between the host and server, as direct interactions are not possible.
- By speaking the same MCP language as the server, the client easily converts requests into the appropriate format, enabling efficient communication.
- For instance, when a user queries for recent commits in a git repository, the host generates a higher-level request that the client translates into MCP format for the server.

### Client-Server Relationship
- In the MCP architecture, the client establishes a one-on-one relationship with the server, meaning each client can only connect to one server at a time.
- If communication with additional servers is required, new clients must be created, each forming their own one-on-one connections.
- An analogy is drawn with phone networks where a SIM card represents the MCP client, enabling a phone (host) to communicate through a specific network (server) while potentially needing multiple SIMs for different networks.

## MCP Architecture Benefits
The architecture provides two main benefits: **decoupling** and **scalability**.
- **Decoupling** allows for a separation of concerns, enabling different communication channels to function independently, which promotes safety and reliability in the system.
- **Scalability** permits the addition of multiple servers to a host without compromising functionality, enhancing task execution speed through parallel processing.

---
## Introduction to Primitives
Primitives in MCP Architecture refer to the offerings that the server can provide to the host. This concept involves understanding what functionalities are available through the server. These include tools, resources, and preps.

### Types of Primitives
- **Tools**: Enable interactions with servers. For example, GitHub functionalities include retrieving the number of commits, checking active issues, and listing repositories.
- **Resources**: Provide static data like documents.
- **Preps**: Offer structured templates and instructions to improve AI behavior, ensuring that interactions, such as issue reporting, follow predetermined guidelines.

## Standard Operations in MCP
MCP provides both primitives and standard operations to interact with various servers. Key functions include:
- `tools/list`: To obtain available functionalities.
- `resources/list`: To fetch static documents.
- Subscribe/Unsubscribe operations for change notifications.

Understanding these functions is crucial for effectively utilizing the MCP architecture in AI communication.

## Data Layer of MCP
The **Data Layer** of the Model Context Protocol (MCP) is described as the shared language and grammar that enables communication within the MCP ecosystem. 
- It serves as a foundation for understanding how different components interact, and
- JSON RPC 2.0 is emphasized as its fundamental structure, providing the necessary rules for constructing this language.
A detailed exploration of its grammar and use will enhance comprehension of the MCP architecture.
### Understanding JSON RPC
- JSON RPC stands for **JavaScript Object Notation Remote Procedure Call**, which allows one program to invoke functions on another machine as though they were local, effectively simplifying the development of distributed applications.
-  The protocol uses **JSON** to structure requests and responses, facilitating easier communication and function execution across machines.
-  Additionally, JSON RPC supports features such as **bidirectional communication**, **batching of requests**, and **notifications**, distinguishing it from traditional **REST APIs**.

---
## Transport Layer of MCP
The **Transport Layer** is the crucial mechanism that facilitates the communication of JSON RPC messages between the client and server within MCP architecture. 
- It ensures that both parties can exchange messages effectively, ensuring they communicate in a shared language.
Understanding this layer clarifies how messages are transmitted back and forth, providing a clear pathway for interaction between systems.

### Local vs Remote Servers
MCP identifies two types of servers:
1. **Local Servers**: These operate on the same machine as the host, allowing for direct communication via standard input/output.
2. **Remote Servers**: These operate over a network, using **HTTP** and **Server-Sent Events (SSE)** for communication.

Understanding these distinctions is crucial for effective interaction with different server types in MCP architecture.

---

# Conclusion
- The **Model Context Protocol (MCP)** is a framework that makes it easier for AI tools (like chatbots) to communicate with different systems (like servers).
- It helps solve problems developers face, such as managing multiple tools and keeping things running smoothly as AI systems rapidly evolve.
- MCP is already gaining popularity and is expected to become a standard in the AI industry. As AI tools and chatbots continue to grow, MCP will play key role in connecting these different systems, making AI easier to use and more effective across various fields .
- The **MCP architecture** is designed to simplify how AI chatbots (hosts) and servers work together (interact) . It provides a clear structure for how data is shared and managed, making it easier for developers to create powerful AI systems without worrying about complex ntegration or disconnected systems.

In the future, MCP could become the go-to solution for integrating AI into everyday tasks, whether it's automating newsletters, developing software, or managing documents. i.e could become the standard solution for integrating AI tools into existing workflows  , MCP promises to make the process of integrating AI more efficient and easier to manage.
