# SignalR
SignalR using Asp.net Core

## Introduction on 2 way communication
Polling <br/>
Periodic call server if there is an update. Every HTTP request is sent to the server and server return a new status or 204 status NoContent.
<br/>
Adds lot of load on the server.
<br/>
<br/>
Long Polling <br/>
The client sents out a request to the server and the server does not close the request until it has new content. When there is no update within a certain timeframe the request timesout.
<br/>
Better than Polling, but still uses HTTP request to do stuff its not ment to.
<br/>
<br/>
Server Sent Events <br/>
Its a HTML5 feature. The server connects to the browser to sent events. Browser does not close until a data is recieved as a stream. Browser uses EventSource to handle active messages.
<br/>
Server side uses asyn/await wih response type to be 'text/event-stream'.
On Client use EventSource event and check onMessage event handler.
<br/>
Simple HTTP request
Auto Connect of timeout
Not all browser support it
Easily pollyfilled
Max HTTP connection issue (6 cuncurrent request)
One way connection
<br/>
<br/>
Web Socket <br/>
A standardized way to use one TCP socket through which message can be sent from Server to Client or vise-versa.<br>
Full Duplex message
No limit on HTTP concurrent HTTP request
Has 50 connection for web socket
Supports text/binary
TCP socket upgrade, HTTP sockets use TCP socket hence need to upgrade to pure TCP socket mechanism
WS Protocol
<br/>
Web Socket lifetime
<br/>
TCP Socket
    HTTP Handshake - Message - Closure
<br/>
Web Socket handshake
<br/>
Client asks for socket upgrade with server response code 101 (Switching Protocol).
If not returns failure, that browsers does not support it.
The key for communication is sent from cient as string, the server hashes the key with socket constant and converts to base64 string. This done for cache busting.
<br/>
Message is composed of frames. Frames have header bits to indicate end of message, mask, length of payload and what kind of message it is.

# SignalR Introduction
SignalR is an open source framework that wraps the complexity of real-time web transport.
<br/>
Benefits:
Cross Platform, Fast, Light Weight
<br/>
SignalR is on top of Transport layer composing of WebSocket, Server side events and Long polling
The transport mechanism is chosen by signalR based on support and falls back to transport in the hierarchy mentioned above.
<br/>
<br/>
RPC - Remote Procedure calls<br/>
Hubs - Component in SignalR, residing in Asp Net core. Server side class used to recieve or send messages from client. <br/>
Support - Json or MessagePack

# SignalR chat app
- Create a new webapp for SignalRChat app<br/>
dotnet new webapp -o SignalRChat
<br>
- Install SignalR<br/>
npm install @aspnet/signalR
- Setup SignalR Client<br/>
Move signalr.js file located in node_modules/@aspnet/signalr/dist/browser
to wwwroot/js/signalr folder<br/>
- Setup SignalR Hub<br/>
- Run the app<br/>
dotnet run













