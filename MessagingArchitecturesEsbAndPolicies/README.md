# Messaging Architectures, ESB's and Policies

## Message Orientated Middleware (MoM)

Middleware handles the connections between the clients and servers. This results in a slightly less complex system as the communication channels are managed by the middlware. By delegating the handling of communications, the message sender and receiver are decoupled.

MoM also handles different types of communication requests other than just request/response and provides the capability to reliabily support one-way messaging, notification and solicit/response messages. 

An **MoM Integration Broker** or **ESB** provides the middleware with the following functions, message transformation, business rules processing, adapter services, repository services, events & alerts.

### MoM Providers

- Java Messaging Service (JMS)
- Apache Active MQ
- WSO2 Message Broker
- WebSphere MQ

## Enterprise Service Bus (ESB)

It is a standard that leaverages MoM across independant (heterogeneous) systems. It is a new way of building and deploying web services by combining different pieces of middleware into a single package. It manages the deployment of web services and helps solve some of the **integration** problems that may exist when combining different systems together.

### Key Features of ESB

- Web Service Support - SOAP, WSDL, UDDI (Universal Description, Discovery and Integration)
- Asynchronous Message Sending
- Transformation
- Message Routing - Publication/Subscribe, content-based, itinerary
- Platform Neutral - Connects to any enterprise system, WS*, Java, .NET

The ESB infrastructure provides a framework that orchestrates the behaviour between services in a distributed system.

## Enterprise Messaging

Messaging provides the basic communication models that **store and forward** messages along through the **publish and subscribe** pattern.

### Store and Forwarding Messaging

Is a queueing mechanism where messages are placed on a virtual channel (message queue) by the message sender which are retrieved by the receiving application when needed.

The message queue functions as a container that holds the message until it is required.
