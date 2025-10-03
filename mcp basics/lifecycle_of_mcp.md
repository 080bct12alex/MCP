# MCP Lifecycle Overview
- The MCP Lifecycle explains how various components like hosts, clients, and servers interact together. 
- It outlines the step-by-step processes necessary for the proper functioning of MCP.

## Session
The MCP lifecycle details the complete steps governing how a host and a server establish and maintain a connection during a session.
- Session   is defined as a continuous connection between a client and server. 
- For instance, when using a Claude desktop that connects to a GitHub server, the connection remains active until the desktop is opened. 
The sequence of steps followed to establish and maintain this connection during the session is what constitutes the MCP lifecycle.

## MCP Lifecycle Stages

The MCP lifecycle consists of three main stages: **Initialization**, **Normal Operation**, and **Shutdown**.

- **Initialization**: The client attempts to connect to the server to start a session.
- **Normal Operation**: Users send questions to the server and receive responses.
- **Shutdown**: The session is terminated, either by the client closing or the server being shut down.


# MCP Lifecycle: Step-by-Step Guide

## 1. Initialization Phase (Step-by-Step)

   1. **Client Sends Initialization Request**  
      - The client initiates the connection by sending an initialization request. This request includes the client's MCP protocol version and capabilities.

   2. **Server Responds with Its Protocol Version and Capabilities**  
      - The server responds with its own MCP protocol version and capabilities, allowing both parties to establish compatibility.

   3. **Client Sends Initialization Confirmation**  
      - After the server responds, the client confirms the successful initialization by sending an "initialized" notification.

   > **Important Note:** During the initialization phase, no other requests (except for pings) can be exchanged between the client and server.

---

## 2. Normal Operation Phase (Step-by-Step)

   1. **Client Sends JSON RPC Requests**  
      - The client sends JSON RPC requests to the server to request information or resources. Example endpoints include:
        - `/tools/list`
        - `/resources/list`
        - `/props/list`

   2. **Server Responds with Available Resources**  
      - The server responds with the list of supported tools, resources, and functionalities based on the client’s request.

   3. **Client Discovers and Invokes Tools**  
      - After receiving the server's list of available tools, the client can request specific tools based on user needs, following the protocol defined during initialization.

---

## 3. Shutdown Phase (Step-by-Step)

   1. **Client Initiates Shutdown**  
      - The client initiates the shutdown process by either closing the server’s input stream or sending a termination signal.

   2. **Server Terminates the Session**  
      - The transport layer (either STDIO for local servers or HTTP for remote servers) handles the termination of the connection. The server typically does not initiate shutdown.

---

## 4. Timeout Mechanism (Step-by-Step)

   1. **Client Sets Timeout Threshold**  
      - When building the client with the MCP SDK, set a timeout period for requests (e.g., 30 seconds).

   2. **Client Sends Request**  
      - The client sends a request to the server and waits for a response within the set timeout period.

   3. **Client Triggers Timeout if No Response**  
      - If the server does not respond within the timeout period, the client triggers the timeout mechanism.

   4. **Client Sends Cancellation Notification**  
      - The client sends a cancellation notification to the server to stop processing the request. The cancellation notification is a JSON RPC method named `notifications/cancelled`.

   5. **Server Stops Processing**  
      - Upon receiving the cancellation notification, the server stops processing and does not return an answer.

---

## Additional Notes

- **Pings:** Periodic ping messages are used to check if the host and server are alive and responsive. They help maintain the connection during long-running tasks to prevent disconnections by proxies or operating systems.
  
- **Error Handling:** Common error scenarios include protocol version mismatches, invalid arguments, timeouts, and server failures. These are handled using JSON RPC error codes like `-32601` (Method Not Found) and `602` (Invalid Parameter).


#### Above is Step-by-Step Summary Guide .Now in detailed explanation

# MCP Lifecycle Overview
- The MCP Lifecycle explains how various components like hosts, clients, and servers interact together. 
- It outlines the step-by-step processes necessary for the proper functioning of MCP.

## Session
The MCP lifecycle details the complete steps governing how a host and a server establish and maintain a connection during a session.
- Sessiob   is defined as a continuous connection between a client and server. 
- For instance, when using a Claude desktop that connects to a GitHub server, the connection remains active until the desktop is opened. 
The sequence of steps followed to establish and maintain this connection during the session is what constitutes the MCP lifecycle.

## MCP Lifecycle Stages

The MCP lifecycle consists of three main stages: **Initialization**, **Normal Operation**, and **Shutdown**.

- **Initialization**: The client attempts to connect to the server to start a session.
- **Normal Operation**: Users send questions to the server and receive responses.
- **Shutdown**: The session is terminated, either by the client closing or the server being shut down.

### Initialization Phase

The **Initialization Phase** is the first interaction between the client and server, during which they check the compatibility of their MCP protocol versions and exchange capabilities. This phase can be broken down into three steps:
1. The client sends an initialization request with its protocol version and capabilities.
2. The server responds with its own version and capabilities.
3. The client sends an initialization notification confirming the successful connection.

Two important rules to remember:
- Neither party can exchange requests other than pings until the initialization is complete.

#### Capability Negotiation

**Capability negotiation** is a critical process during the client-server initialization phase, where both parties establish their capabilities, setting expectations for communication. Clients offer three main capabilities: access to root directories, sampling, and elicitation. Servers provide tools, resources, prompts, and login functionalities. Additionally, sub-capabilities such as list change notifications and subscriptions enhance communication by alerting clients to new resources or modifications.

### Operation Phase

During the **operation phase**, the client and server exchange messages based on previously negotiated capabilities from the initialization phase, adhering to the established protocol version. The client discovers available tools and resources by sending JSON RPC requests to endpoints like `/tools/list`, `/resources/list`, and `/props/list`, which prompts the server to respond with supported functionalities. The capability discovery occurs automatically after initialization, enabling the client to subsequently call specific tools based on user requests.

### Shutdown Phase

The **shutdown phase** of the MCP lifecycle is where the session between the client and server is terminated, typically initiated by the client. Unlike other phases, no JSON RPC messages are exchanged during shutdown, and the responsibility for termination lies with the transport layer, either STDIO for local servers or HTTP for remote servers. Clients generally control the shutdown process, either by closing the server's input stream or sending termination signals, while servers rarely initiate the shutdown.

## Special Cases in MCP

Special cases arise throughout the MCP lifecycle, including the **ping** method, which is a lightweight request-response mechanism designed to check if the host and server are alive and responsive. Pings can be sent periodically between client and server to maintain connection integrity during long-running tasks, preventing inadvertent disconnections by operating systems or proxies. The utility of pings is emphasized during connection initialization and when there is prolonged inactivity between communications.

## Error Handling in MCP

Error handling in MCP addresses how hosts and servers indicate issues with requests, mirroring JSON RPC error handling standards. 

- Common scenarios for errors include protocol version mismatches, calling undefined methods, sending invalid arguments, server failures, timeouts, and syntax problems in JSON RPC messages.
- The standard error object structure includes an error code, message, and optional debugging information.

### Error Codes Overview

- Error code **-32601** indicates "Method Not Found."
- Code **602** represents that an invalid parameter was sent.
- Code **600** indicates an invalid request for a non-existent method.
- Codes above 32,000 typically relate to authentication failures, rate limits exceeded, quota errors, or internal issues, providing a general idea of common error scenarios.

## Timeout Explanation

The concept of **timeout** ensures that client requests do not hang indefinitely due to a slow or unresponsive server. By defining a threshold, requests can be canceled after a specified time, freeing up resources and providing feedback to the user about potential issues. This mechanism protects users from waiting unnecessarily and optimizes server resource management.

### Timeout Mechanism

When building a client with the MCP SDK, you can set a timeout for requests, such as 30 seconds. If the server does not respond within this period, the client triggers a timeout and sends a cancellation notification to the server, which stops processing the request and does not return an answer. This mechanism ensures that clients avoid waiting indefinitely for responses from the server.

### Cancellation Notification

When a server takes too long to respond to a query and the timeout threshold is crossed, the client can send a cancellation notification. This notification is structured as a JSON RPC method named **'notifications/cancelled'** with the request ID set to the server, corresponding to the ID of the earlier request made by the client.

### Progress Notification

**Progress notifications** allow clients to receive periodic updates about long-running tasks, helping them understand the status of their requests. When a client requests a lengthy operation, a progress token is included in the metadata, enabling the server to send notifications detailing the percentage of completion. This approach keeps users informed about ongoing processes, enhancing their experience and managing their expectations.

## User Experience Improvement

Real-time notifications will provide users with feedback on their progress, enhancing the user experience. Similar to features seen in research assistants like ChatGPT, a progress bar indicates how much work has been done and how much is left, allowing users to better gauge waiting times. Although the underlying work continues behind the scenes, this notification system helps keep users informed.
