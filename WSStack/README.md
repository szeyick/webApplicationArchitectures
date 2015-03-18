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

# XML Schema

- The template functions as a template to construct a message (document) that is compatible for web services.
- It defines they **structure** and **datatype** of the document.

# Namespaces

- The namespace is the collection of names, identified by a URI a reference which is used by the XML documents to define the element types and attribute names. 
- The schema defines how the data is structured, the data to conform to the structure is the document.
- www.corefilling.com provides a XML validation to ensure that the XSD and XML conform.

# Element Declaration

Describes how to declare an element in XML, it must have


1. A name
2. A type - either simple or complex types. A complex type is a data type that can include other elements or attributes. A simple type is a string, integer, etc.
3. Cardinality (minOccurs, maxOccurs)
