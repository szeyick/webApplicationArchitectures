# Event Driven Architectures

## Organisms Sense and Response: EDA

The idea here is to imitate real life by sensing the surroundings to make a decision on what to do next. This is the concept behind event driven architectures where you react to a particular event.

Biologically these events are triggered from an external source such as the senses (sight, sound, touch, taste, etc).

In this scenario, the central nervous system detects the event and processes it.

## Internet of Things (IoT)

In the modern age of the internet, devices are now even more interconnected. This means that we are able to know the exact sate of the environment that they are in, which can in turn provide a more responsive system that can get updates in real-time. 

With more devices now connected to the internet, the PC is no longer the only access point. Now, lights, plants, fridges and even more devices can get real-time updates from the internet. It allows for devices to attain situational awareness throught the internet.

## Events and Complex Events

An event is classified as something that the system senses or is of interest to the system.

Furthermore a complex event is defined as an event that involves more than a single event. This means that it could be event that depends on several other events to occur at the same time for it to be triggered. An example of this would be the sending of an item, which depends on the purchase order and payment events before the sending event is triggered.

### Time, Causality and Aggregation

Three most common and important relation between events are

- Time - The relationship that orders the events.
- Cause - The dependancy of activites in the system
- Aggregation - The combined relationship of activities that create an event.

## Event Driven Architectures (EDA)

EDA's follow the Event-Orientated architecture used the WS* standards.

EDA processes communicate by accessing shared events in something called an **event cloud**. Each part of the system (or process) communicates with other parts of the system through the **publish/subscribe** pattern.

It is a purely asynchronous architecture that connects the subscribers with the publishers. Furthermore, we can also bind a set of rules to allow it to react differently to certain events.

An EDA senses and processes events to subscribers. Because it is decoupled, the publishers don't care who consumes the events and multiple processes can consume the events. 

### Features

- Captures asynchronous events occuring in parallel.
- Senses real time events and conditions.
- Initiates the appropriate response, action or process.
- It modifies processes in real-time to respond to changing conditions.

## Publish Subscribe Architectures

Is a type of architecture pattern for subscribing to events. The internal network within the system connects the publishers and subscribers together.

### Basic Architecture

- Event Publisher - Is the component that generates the events.
- Event Subscriber - Is the component that subscribes to events.
- Event Processing Engine - The component that pushes events from publisher to subscriber.
 
### Event Processing Styles

There are two types of processing styles, simple and complex events.

For **simple events**, the event is triggered and a the subscriber responds immediately.

**Complex events** can be comprised of a group of simple events. For example, an event of loud nosies, cars, and smell of tires can form a complex event of a race car.

**Complex Event Processing (CEP)** includes a set of techniques and tools to help undersatnd and control event driven information systems.

In addition, there is also a **stream event processing**. In this style, events are streaming in and it is up to the architecture to filter them and make sense of it to create additional events. 

Traditional application development isn't designed to handle high volumes of traffic or complex queries. Also the data is usually static and database access being quite slow, with complex event processing, the data is stored and processed on the fly.

### Event Driven Architectures and SOA

EDA's promote the decoupling of business processes through the publish/subscribe model. A publisher can trigger an event which can be consumed by multiple processes without them even knowing about each other. As a result SOA and EDA's are complimentary architectures.

Service Orientated Architectures (SOA), requires knowledge of where the service is. However with EDA, you can generate the event but you don't care who responds to it. 

SOA creates a one-to-one connection, since the end points need to be mapped, but with EDA, many services can respond/react to events as there is no direct relationship between the publisher and subscriber. 

SOA primarily uses a request-response message exchange whereas EDA's process messages through asynchronous calls.

### Implementing EDA

EDA's can be implemented through -

- Enterprise Service Buses (ESB's)
- Event Driven Processing and rule engines.

## WS* support for Publish/Subscribe EDA

- Standard SOAP messages and WSDL configurations are not enough to support EDA's and highly decoupled architectures as they are not detailed enough to support it.
- WS-Notification (OASIS) supports subscribe-notification pattern for EDA and peer-peer architectures.
- WS-Eventing (W3C) is simpler implementation than WS-Notification
- WS-Addressing is the standard for adding extra **addresses and message** information in the SOAP header.

### WS-Addressing

It allows developers to add processing and delivery instructions within a SOAP message header.

- Destination - Contains a **Internationalised Resource Identier (IRI)** that represents the address of the intended receiver.
- Source/Reply/Fault Endpoints - Contains details of where the message originated, receiver of replies and faults to be sent.
- Action - Contains an IRI that identifies the intent of the message.
- Message ID - An absolute IRI that identifies the message, can be used to track messages.
- Relationship - A pair of values indicating how the message relates to another message.
- Reference Parameters - Extend an address with parameters relevant to the web service.

### Rule Engines 

Executes When-Then rules. Essentially, when an event happens, then it does something. Similar to an if statement.


