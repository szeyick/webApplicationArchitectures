# WS Stack, XML and WSDL

From previous topics, we know that WS* approaches refer to RPC, Message Orientated and Event Orientated architectural styles. It can sit on top of existing application protocols to send messages through a network (HTTP, HTTPS, SMTP).

## Message Exchange Patterns (RPC - Remote Procedure Calls)

RPC's are synchronous operations that follow the request/response pattern. The code is generally the same between the client and server, so the client essentially calls the same function on the server. This results in **tightly coupled code** since changes in either can stop the RPC from functioning correctly.

## Message Orientated API's

Can be both synchronous and asynchronous messsage types. The client and server communicate through messages, meaning that if we change the message, it will not break the interface. Either the client and server can choose to ignore the newer or unused parts of the message without affecting the behaviour.

The messages that are exchanged between client and server are constructed through an XML schema.

### Request/Response Messaging

![alt text][requestResponse]

[requestResponse]: https://github.com/szeyick/webApplicationArchitectures/blob/master/WSStack/resources/messageRequestResponse.png "Request/Response Example"

As the name stipulates, it is a messaging operation where a message is received and a response is returned. The addition of the **output** element means that the web service is expected to respond.

```
<wsdl:operation name="DispatchOrder">
  <wsdl:input message="tns:DispatchOrder_Message"/>
  <wsdl:output message="tns:TrackingNumber_Message"/>
</wsdl:operation>
```

### One Way Messaging

Is a messaging operation where the message is sent by the client, but a response is not expected. An example of a one way message in a programming language would be a trigger of a `void doSomething()` method call.

A one way message is defined in the schema as a **input** element without a corresponding **output**. This illustrates that no response is expected to be sent.

```
<wsdl:operation name="SubmitOrder">
  <wsdl:input name="order" message="tns:SubmitOrder_Message"/>
</wsdl:operation>
```
 
### Notification Messaging

Is a messaging operation where the message is sent by the service/server to registered clients, but does not expect a response. It is similar to the one way message, but from the server side. 

As such, the message schema will contain a **output** element and no **input** element.

```
<wsdl:operation name="SendInvoice">
  <wsdl:output name="invoice" message="tns:SubmitInvoice_Message"/>
</wsdl:operation>
```

### Solicit Response 

A message operation that would be the opposite of request/response. In this instance, the service/server sends the request to the client expecting a result. As this is the opposite, the message schema for the order of **input** and **output** elements are the opposite of the request/response schema.

```
<wsdl:operation name="VerifyDelivery">
  <wsdl:output message="tns:VerifyDelivery_Message"/>
  <wsdl:input message="tns:DeliveryReceived_Message"/>
</wsdl:operation>
```

## Message Orientated Middleware (MoM)

Middleware functions as a sort of broker/mediator of messages, where it manages and directs where the messages go.

MoM provides the following functions
- Queuing
- Event driven processing (publish/subscribe pattern)
- Messages are serialised, delivered once.
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

## WSDL - Web Service Description Language

Describing the interface, the contract between the develper and user. It is the users job to find the description and interact with the web service through that interface.

It is an XML based description language, where the user interacts with the web service through the interface without having to interact with the concrete implementation of the service itself. This allows the implementation to be done in basically any language irrespective of what the user can understand.

### Web Services in Context
The following is described by WSDL 

- what the service can do : **functionality**
- how good the service can do it
- how to use the service 

### WSDL Structure
- the interface definition  describes the general structure of the service. It contains the operations supported by the service and other things.

- the port type is otherwise known as the interface.

