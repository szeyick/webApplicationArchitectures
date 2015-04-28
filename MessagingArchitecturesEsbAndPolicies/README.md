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

![alt text][messageQueue]

[messageQueue]: https://github.com/szeyick/webApplicationArchitectures/blob/master/MessagingArchitecturesEsbAndPolicies/resources/storeAndForwardMessaging.png "Message Queue Holds Messages Until Required"

### Publish/Subscribe Messaging

The idea here is that the application that wants to send information "publishes" it, and all other applications that are interested will "subscribe" to it. Again the messages are placed in a queue for the subscriber to retrieve.

### Enterprise Integration Patterns

Are a set of design patterns for use when integrating enterprise applications. It can be used with open source ESB's.

Example Patterns Include -

- Integration Styles
- Messaging Systems
- Messaging Construction
- Message Routing
- Message Transformation
- Messaging Endpoints
- System Management

### Message Routing

A message router can be used when we wish to pass messages to different filters depending on a condition. Rather than publishing directly to the message queue, the router consumes the message and forwards it onto the correct channel depending on a set of conditions.

## WS-Reliable Messaging

Is a protocol that detects unreceived and duplicate SOAP messages and process them in the order they were sent in. It is implemented typically as part of the JMS acknowledgement patterns.

### Message Delivery Assurance

- At Least Once Delivery - Guarantees that messages will be delivered at least once or an error will be raised at the endpoint.
- At Most Once Delivery - Guarantees that messages will be delivered at most once without duplication or an error is raised. In this situation, it is possible for some messages in the sequence to not be delivered (0 or 1 times).
- Exactly Once Delivery - Guarantees that every message will be sent without duplication, and received once. It is a logical "AND" of the At Least Once and At Most Once Delivery.
- InOrder Delivery - Enforces the ordering of messages sent and received being the same. 

## Java Message Service (JMS)

Is a middware API used to send messages between two or more clients, and allows components based on Java EE to create, send, receive and read messages.

This results in a loosely coupled, asychronous and reliable middlware.

It supports **point to point** and **publish/subscribe** communication models.

### JMS Elements 

- JMS Provider/Broker - Implements the JMS Interface for the middleware.
- JMS Client - The application or process that creates/receives messages.
- JMS Producer/Publisher - A JMS client that creates and sends the message.
- JMS Consumer/Subscriber - A JMS client that recieves a message.

### Point to Point Model (Store and Forward Messaging)

Messages are routed to a individual consumer that maintains a **queue** of the incoming messages it needs to process. Because it is a point to point system, the messages can only be consumed by a single consumer as it relies on sending it on a particular channel.

The message queue for the consumer maintains the messages to be processed until they expire or are consumed. If there is no consumer on the other end, the messages will build up into the queue until someone pulls them out.

### Publish/Subscribe Model

Publishes messages to a particular **message topic**. The subscribers will register to that topic and will need to remain active to process the messages.

The message topic functions as a container for messages that are sent by the publisher, and it is up to the receiver to retrieve them. Neither sender nor receiver know about each other.

### JMS Reliability 

- Reliable Message Delivery - The messaging server will deliver the message to the client if no application or network issues. It will deliver it **at most once**
- Guaranteed Message Delivery - The message will be delivered even with application or network issues. The messaging server will store the message then forward to the client, the client needs to send an acknowledgement to verify the message being received.

## Web Service Policies

Encapsulates quality in the web service. This quality must exist even outside of the software and needs to be describable.

Attributes of quality include -

- Reliable Messaging
- Security
- Trust
- Performance
- Transactions
 
### WS* Standards for Quality

There are WS* quality standards that are proposed but not widly accepted unlike some of the core WS* standards.

- WS-Policy Framework - Extending WSDL to express quality aspects
- Security and Trust - WS-Security, WS-Trust, WS-Federation
- Reliability, Transactions and Coordination - WS-Reliable Messaging, WS-Atomic Transaction, WS-Business Activity, WS-Coordination.
- Managing Services - WSDM, WS-Management 

### Service Policies

Policies define how we can interact with a web service. These policies can define the **constraints**, **capabilities** and **preferences** that allow a service to be used. It adds an additional layer of service description for a web service.

It is done so through **policy assertions** that can be split into two categories, **on the wire** or not.

**On the wire** defines such policies as authentication schemes, transport protocol selection, whereas QoS and privacy are considered as assertions that are not on the wire.

### Types of Service Policies

- Versioning Policies - Defines that the same service can exist in the system multiple times. It requires the SOA to support multiple versions of the same service.
- QoS Policies - Defines the functional and non-functional service properties of the service.
- Security Policies - Defines the security requirements of a web service, such as security tokens, digital signatures and encryption.

### WS-Policy Framework

Defines a common framework and language for services to describe their service assurance qualities and requirements. The framework is split into three specifications.

1. **WS-Policy** - A general purpose model and syntax to describe the policies of the service.
2. **WS-Policy Assertions** - Provides a set of common message policy assertions that can be used.
3. **WS-Policy Attachment** - Provides three specific attachment mechanisms for using policy expressions with existing services.

![alt text][wsPolicy]

[wsPolicy]: https://github.com/szeyick/webApplicationArchitectures/blob/master/MessagingArchitecturesEsbAndPolicies/resources/WS-Policy.png "WS-Policy"

### WS-Policy Components

Because a policy is an extension of the WSDL, it utilises the same XML based structure for definining itself. The policy is made up of several components which are defined below -

- Policy - The set of information expressed as a bunch of assertions.
- Policy Assertion - An individual preference, requirement, property.
- Policy Expression - An XML representation of one or more policy assertions.
- Policy Operator - The mechanism to allow for multiple assertions to be logically combined.
- Policy Subject - The endpoint to which the policy is bound to.
- Policy Attachment - Associating expressions with one or more subjects which can be attached to a WSDL document.

An example structure of a WS-Policy is shown below -

```
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy"
...
<wsp:Policy>
  <wsp:ExactlyOne>
    <wsse:SecurityToken>
      <wsse:TokenType>
        wsse:Kerberosv5TGT
      </wsse:TokenType>
    </wsse:SecurityToken>
    <wsse:SecurityToken>
      <wsse:TokenType>
        wsse:X509v3
      </wsse:TokenType>
    </wsse:SecurityToken>
  </wsp:ExactlyOne>
</wsp:Policy>
```

### WS* Security Related Standards

The standards are briefly covered above, however the following section breaks down what each of the standards are responsible for.

1. WS-Security - SOAP extensions focused on implementing **message content integrity and confidentiality**.
2. WS-Security Policy - The policy assertions for WS-Policy that apply to WS-Security, specifies the security requirements for their web services.
3. WS-Trust - Defines XML primitives for requesting and issuing **security tokens** and manaing *trust relationships**
4. WS-Privacy - Uses a combination of the above to communicate **privacy policies** to ensure that incoming SOAP requests adhere to the defined privacy policies.
5. WS-Secure Conversation - Defines extensions of WS-Security to provide **secure communications**.
6. WS-Federation - Defines mechanisms to enable identity, attribute authentication across different places.
7. WS-Authorisation - It describes how **access** policies for a web service are specified and managed.
