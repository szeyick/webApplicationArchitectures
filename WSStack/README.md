# WS Stack, XML and WSDL

## Message exchange patterns (RPC)

- One way operations - The operation where you send a message off but do not expect a response (fire and forget)
- Request/Response Operations - As the name suggests, you send a message off and expect a response from the receiver.
- Notification Operations - The opposite of a one way operation, the service/server sends the response to registered clients but does not expect the client to respond back.
- Solicit/Response - The opposite of request/response, where the service/server sends a message and expects a response from the client.

# Message Orientated Middleware (MoM)

MoM provides the following functions
- Queuing
- Event driven processing (publish/subscribe pattern)
- messages are serialised, delivered once.
- Message structures are sent in XML, so the middleware is unconcerned with the message type.

